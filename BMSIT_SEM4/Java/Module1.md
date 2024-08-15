# Module1 Paper

## Accessing a Collection via an Iterator

- To cycle through the elements in a collection.
- For example, you might want to display each element. One way to do this is to employ an *iterator*, which is an object that implements either the `Iterator` or the `ListIterator` interface.
- **Iterator** enables you to cycle through a collection, obtaining or removing elements.
- **ListIterator** extends `Iterator` to allow bidirectional traversal of a list, and the modification of elements.
- `Iterator` and `ListIterator` are generic interfaces which are declared as shown here:
  - `interface Iterator<E>`
  - `interface ListIterator<E>`


## HashSet

Constructors

- HashSet( )
- HashSet(Collection<? extends E> c)
- HashSet(int capacity)
- HashSet(int capacity, float fillRatio)

Methods:

- .add(Collection e)
- .remove(object o)
- .contains(object o)
- .size()
- .iterator()

```java
import java.util.*;
public class hset{
    public static void main(String[] args){
        HashSet<String> hs = new HashSet<String>();
        hs.add("A");
        hs.add("B");
        hs.remove(0);
        sout(hs.contains("A"));
        sout(hs.size());
        hs.add("C");
        hs.add("D");
        Iterator<String> = hs.Iterator();

    }
}
```
