Generics and Collections
===

Arrays are very useful, but sometimes we want other kinds of *collections* of objects. Some of the limitations of arrays are:
* they are of fixed size
+ the indices can only be integers

Java provides two main interfaces for collections; the [List](http://docs.oracle.com/javase/8/docs/api/java/util/List.html), which is like an array, but can grow (and shrink), and [Map](http://docs.oracle.com/javase/8/docs/api/java/util/Map.html), which is somewhat like an array, but the 'index' can be of any type (so we don't really have iteration, but can put and retrieve data by any kind of key).

## Generics

Arrays are special in that we have an extra type parameters; we have arrays *of ints* or arrays *of strings*; Java provides for a generic mechanism for this kind of polymorphism (not quite the same as arrays, since this was added much later than arrays), called *generics*.

In Java we can define generic structures (for those that have been defined as generic) by putting the type(s) within angle brackets; so, for example, to define a list of Strings we would use: `List<String>`.

## Lists

Lists are probably the most useful collection; the intrface is called `List` and the most common implementation is `ArrayList`. Its more important operations are:
+ `add` - takes the element as parameter; used to add an element to the list
+ `get(int index)` - get the element at the corresponding place (index starts at 0)
+ `set(int index, ... element)` - sets the element at that index
+ `size` - returns the number of elements in the list
+ `isEmpty` - returns true if the list is empty
+ `remove(int index)` -removes the element at that index (and 'slides' the following ones one space down; use carefully or, better yet, don't use at all :)
+ iteration - we can iterate on lists as if they were an array
### Example 1
```java
	Point lowestXY(List<Point> points) {
		if(points.isEmpty())
			return null;
		Point low=points.get(0);
		for(Point p : points) {
			if(p.x < low.x)
				p.x=low.x;
			if(p.y<low.y)
				p.y=low.y;
		}
		return low;
	}
```

Although java doesn't provide a nice syntax for initializing lists, it does provide a class, Arrays with a static method, asList, which takes a variable number of arguments and returns a list; for example:
```java
		List<Integer> numbers=Arrays.asList(1,2,3,4);
		for(int n : numbers) {
			System.out.println(n);
		}
```

## Maps

Maps are like arrays, but we can use any kind of objects as the key. To use a Map we need to provide two type parameters, the type for the key and the type for the value.

For example, to represent a map from Strings to ints (well, Integer; we need to use the boxed version) we would declare it as `Map<String,Integer>`. The main implementation class is HashMap.

### Example

```java
		Map<String, Integer> digitValues=new HashMap<String,Integer>();
		digitValues.put("Zero",0);
		digitValues.put("One",1);
		digitValues.put("Two",2);

		System.out.println(digitValues.get("One"));
```

Some of the map operations are:
+ get(key) - to retrieve the value stored at a given key
+ containsKey(key) - returns true if the map has a value  for the given key
+ put(key,value) -sets the value for the given key
+ remove(key) - removes the value for the given key
+ size(), isEmpty() - as in collections
+ keySet(), entrySet(), values() - return collections of keys, values or entries

## Other collections

Besides these collections, Java supports [Set](http://docs.oracle.com/javase/7/docs/api/java/util/Set.html), [Queue](http://docs.oracle.com/javase/7/docs/api/java/util/Queue.html), [Stack](http://docs.oracle.com/javase/7/docs/api/java/util/Queue.html), [Dequeue](http://docs.oracle.com/javase/7/docs/api/java/util/Deque.html) and many others. 
