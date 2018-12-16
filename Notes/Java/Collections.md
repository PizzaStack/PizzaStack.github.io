# [Return to Index](/README.md)
# Collections API
Java provides the **Collection** interface which provides a framework for several diffrent containers which will be disscussed below. All interfaces except **Map** share **Collection** as their superinterface.  
  
- **List** is an ordered collection of elements. A user has the ability to place an element anywhere in the list. The elements are accessable by their index. Unlike **Set**, **List** typically allows for duplicate elements such that element1.equals(element2). In addition to duplicates, **List** allow for multiple null elements to be stored.  
  
- **Set** is a collection of non duplicate elements meaning there will never exist a situation where element1.equals(element2). In addition to this, it is implied that there can only exist one null element due to the no duplicates rule.  

- **Queue** is a collection of elements who in essence cannot be iterated, instead the **Queue** follows the **FIFO** (First In First Out) rule. When an element is added to the **Queue** it is placed at the back and when an element is pulled it is pulled from the from the front (index :0).  
  
- **Deque** extends **Queue** but augments the ability to insert and remove elements at either end. The name is short for "Double Ended Queue" and is pronounced "Deck".  
  
- **Map** is an interface which stores data with a key. A map cannot contain duplicate keys; each key can map to at most one value. **Map** can be visualized like a dictionary where only one word is paired with one definition.  

## Example Implementations
  
**ArrayList** extends **AbstractList** and implements **List** (among others). **ArrayList** provides a dynamic array implementation. **ArrayList** has a dynimic capacity which is resized when the user fills the container. At all times the **ArrayList** capacity will be either larger or the same size as the number of elements it contians.  
  
**HashSet** extends **AbstractSet** and implements **Set** (among others). **HashSet** implements the **Set** interface which organizes elemts based on a hash map. Due to the hash map, there is no guananteed order of iteration.  
  
**TreeSet** extends **AbstractSet** and implements **NavigableSet**. Elements in the set are ordered using natural ordering (sorted and ascending order). **TreeSet** does not preserve the insertion order of elements but elements are sorted by keys. Alternatively, a Comparator can be passed in the constructor to achieve other orderings. Elements in a **TreeSet** must be homogenous and comparable with the default sorting or else a runtime *ClassCastException* will occur. **TreeSet** is essentially an implementation of a self-balancing binary search tree.  
  
**LinkedList** extends **AbstractSequentialList** and implements **List** and **Deque** (among others). **LinkedList** is implemented using a doubly-linked list (meaning it is iterable both forward and backwards).  
  
**HashMap** is an implementation of the **Map** interface. This container allows for both null keys and elements. Unlike the **Map** keys are generated using a hashing algorithm.  
  
**Hashtable** maps keys to values. Any non-null object can be used as a key or as a value. To successfully store and retrieve objects from a hashtable, the objects used as keys must implement the hashCode method and the equals method. The HashMap class is roughly equivalent to Hashtable, except that it is non synchronized and permits nulls. (HashMap allows null values as key and value whereas Hashtable doesn't allow nulls).  
  
![alt text](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/java-collection.jpg "Collections Tree")

