# Overview
- The following data structures introduced in this section is meant to facilitate the understanding of the use of these data structures (ADT abstract-datTypes)
- As such the Java collections class is used where the implementation of the data structures are abstracted away from the programmer 

## ArrayList 
- An arrayList in Java is a list data structure that enables the dynamic resizing of elements after the list has been initialised, this means that the size of the list is not fixed at compile time unlike the array data structure 


ArrayList instantiation 

- Based on the java documentation we are given three ways to instantiate a new ArrayList object, using the following default and parameterized constructors 
  
- `ArrayList()` initialises a new ArrayList with the capacity of storing 10 of the elements of the specified dataType
  
- `ArrayList(size)` initialises a new ArrayList with the capacity of size, so it stores size elements of the dataType initially
  
- `ArrayList(Collection<? extends E> c)` initialises an ArrayList with another collection that belongs to the same type or is a subtype of E
  - Stated thru the bounding type operator ` <? extends E> `

``` Java 
import Java.util.ArrayList;
ArrayList<dataType> listName = new ArrayList<dataType>(); // default constructor method
S
// Example of using the parameterized constructor method by passing the initial capacity of the ArrayList 

// initialise an ArrayList of 10 elements initially
ArrayList<dataType> listName = new ArrayList<dataType>(10); 

// Example of initialising an ArrayList 
// Example initialising an arrayList of strings 

ArrayList<String> foodNames = new ArrayList<String>();

// Initialising an ArrayList with any collection

// Initialise a list of strings
List<String> existingList = Arrays.asList("Apple", "Banana", "Cherry");
ArrayList<String> fruits = new ArrayList<String>(existingList);

HashMap<Integer,String> studentList = new HashMap<Integer,String>();
students.put(121421,'Isaac');
students.put(51951,'John');
students.put(25219,'Jacob');

// initialising the ArrayList using hashMap values or keys (extract the values or keys)

ArrayList<String> studNames = new ArrayList<string>(studentList.value())

``` 

## Operations of an ArrayList 

- add() operation which runs in O(n) time adding n elements take n time basically (Armotized time)
  - Takes in the specified element according to the primitive or non-primitive data type specified to store the items in the collection

- clear() operation which basically removes all elements in the ArrayList, returns an empty ArrayList 

- get(index) which takes in a valid integer that is within the size of the array, where this integer represents an index in the ArrayList 
  - Returns the element at that index 
  
- set(index,element) also takes in a valid integer (index) in the ArrayList and modifies the value stored at that index with the second argument (new element)
  
- size() operator which returns the total number of elements in the ArrayList as an integer 

- remove(index) which removes the element at the specified index 
  
- remove(Object o) which removes the first occurence of the object found in the ArrayList 

- isEmpty() which checks if the ArrayList is empty returning true if it is and false if its not 


## iterating over elements in an ArrayList 

``` Java 
import Java.util.ArrayList;

ArrayList <String> fastFoodRest = new ArrayList<string>();
fastFoodRest.add("Burger King");
fastFoodRest.add("Mcdonald\'s");
fastFoodRest.add("Wendy\'s");
fastFoodRest.add("KFC");
fastFoodRest.add("Long John Silver");
fastFoodRest.add("Mos Burger");

for (int i = 0; i < fastFoodRest.size(); i++){
  String str = fastFoodRest.get(i);
  System.out.println(str + "/n");
}

int currentInd = 0;
while(currentInd < fastFoodRest.size()){
  System.out.println(fastFoodRest.get(currentInd) + "/n");
  currentInd ++;
}
```
- string elements are being added into the ArrayList 
- The for loop iterates over each element and retrives the element at the current index using the get operator
- The while loop utilises a condition which states that as long as currentIndex is within the size of the list, i will retrive the element at the currentIndex and then print the element out. Breaks when it exceeds it.



# Stack 
- A stack is a LIFO (Last-In-First Out ) data structure, which elements that are being added to the stack last appears at the top of the stack, while previous elements appear at the bottom of the stack
  
Applications of the data structure 
- Program stackFrame in compilers 
- Callstack for functions important in recursive algorithms 
- Palindrome algorithm 
- Valid Prefixes 


How is a stack being implemented in java 

- We see that based on this class definition for the stack class ` public class Stack<E> extends Vector<E> `
  - We can see that a Stack class in java extends it inherits the Vector class and adds on new methods to support the stack data structure 
  - In doing so since Stack extends Vector it implements all its interfaces which includes collections, List and Iterable 
  
![diagram of stack class heirachy](/Understanding%20Java%20Collections/stackDiagramGeeksForGeeks.png)


## Instantiating a new Stack
- Stack \<dataType> nameOfStack = new Stack \<dataType>();
``` Java
Stack<Integer> nums = new Stack<Integer>();
Stack<String> names = new Stack<String>();
Stack<ArrayList<String>> arrayListStack = new Stack<ArrayList<String>>();
Stack<Object> objects = new Stack<Object>();
```


## Stack methods 
``` Java 
import Java.util.Stack;

Stack<Integer> nums = new Stack<Integer>();

nums.push(1);
nums.push(2);
nums.push(3);
nums.push(4);
nums.push(5);

// How the stack looks 5 4 3 2 1

// printing the stack 

System.out.println(nums); 

// what if i wanted to print the stack in order of insertion without modifying the original stack 

// 5 , 4 , 3 , 2 , 1 
// DisplayOrder: 1 , 2 , 3 , 4 , 5
Stack<Integer> displayOrder = new Stack<Integer>();

for(int i = 0; i < nums.size(); i++){
  String currentItem = nums.peek();
  nums.pop();
  displayOrder.push(currentItem);


}

// use the displayOrder stack to print 
System.out.println(displayOrder);
```
- peek() method returns the element at the top of the stack 
- size() method from the vector class -> implements the List interface : returns the number of elements in the stack 
- pop() removes the top element from the stack and returns the top element 
- push() method, adds a new element at the top of the stack. Prev element are pushed to bottom 
  - 1 (added)
  - 2,1 (2 added) ... ... 5,4,3,2,1 (after adding 3,4,5)


Time Complexity analysis 
- Peek() is O(1) constant time complexity
- Pop() is O(1) constant time 
- Push() is O(1) constant time
- displayStackInOrder() is O(n) operation
- reverseStack is O(n) operation

# Queue 
- A queue is a first in first (FIFO) data structure which means that elements that arrive first in the queue, would be processed first. Elements in the queue are being dequeued based on the order they are inserted (arrive)
- First element to be inserted is the First element to be out (dequeued) similar to how a real life queue is being formed when queueing for food at restaurants 

Applications of a queue 
- CPU process scheduling and management 
- Long polling at regular intervals 
- Message queue (rabitMQ, Kafka)
- Read Write buffer


Implementation of Queue in java 
- In java, the queue data structure is implemented as an interface that extends (inherits) from the collections interface 
  - Which means it inherits all the methods of the collection interface and must implement them, additionally it is able to extend its own functionalities by adding new methods 
- The deque interface (deque) double ended queue extends the queue interface, deque is a double ended queue where insertion and deletion can happen from both the front and rear of the queue 
  - Concrete classes LinkedList and ArrayDeque implements the Deque interface

![Hierarchy of Queue in Java](/Understanding%20Java%20Collections/queueHierarchy.png)


Initialising a queue 
- ` Queue <dataType> queueName = new ConcreteClass();`
- Since queue is an interface it needs a concrete class to be initialised, this concrete class has to implement the Queue interface, for instance LinkedList and 
  
Queue Methods

- add(E e): inserts an element into the queue if the capcity of the queue has not been reached. Returns true if suzessful and throws an `IllegalStateException` if the capacity is exceeded 
- element() retrieves the element at the front of the queue 
- offer(E e): similar to the add method it inserts an element at the head of the queue if its possible (capacity is not exceeded), if the queue capacity is reached it will just return false instead of throwing an exception 
  - Used this when a queue is bounded and adding beyond its capacity would result in an error / failure not an unhandled exception

- peek() : element or NULL 
  - Retrieves but does not remove the element at the head of the queue, or return null if the queue is empty

- poll() : element or NULL
  - Retrieves and removes the head of the queue, return null if queue is empty

- remove() 
  - Retrieves and removes the head of the queue 


Since queue implements the collection interface it will have all the methods from the collection interface to be used 


Example of utilising the methods in the queue 
``` Java 
// initialse a queue of strings 

import Java.util.Queue;
import Java.util.LinkedList;

Queue<String> names = new LinkedList<String>();

names.add("Isaac");
names.add("John");
names.add("Matthew");
names.add("Johnathan");
names.add("Jacob");
names.add("Ruth");

for(int i = 0; i <names.size(); i++){
  String currentName = names.peek();
  System.out.println(currentName);
}

// Now what if i wanted to simulate an ordering system 
int timeTake = 0;
// use RandInt
for (int j = 0; j <names.size(); j++){
     Random random = new Random();
     int randomInt = random.nextInt(10) + 1; // generate a random int between 1 - 10
     String currentCust = names.poll(); // retrieves the current element at the head of the queue and removes them from the queue 
     timeTake += randomInt
     System.out.println("Processed " + currentCust " in " + randomInt);
}

```

# Map (Seperate from Collections interface)
- In java map replaces the Dictionary classes that can be seen in other programming languages like C# and Python, the map interface provides extensibility as it is implemented by other Map classes and its functionality can be extended 
  - For instance the HashMap iterator iterate over each entry in the HashMap in no particular method
  - However i can have other classes like TreeMap that returns an iterator based on a specific order 
  - Map is a Key Value pair collection where each value is exactly map to no more than 1 key














# Hashmap

- A hashmap is a collection of key - value pair items, each key in a hashMap is unique and generated from a hashing algorithm hashCode of the value that is being stored 


## Key details to take note for HashMap
1. A hashMap cannot contain duplicate keys, hence if two objects have the same hash code (ie. Has the same hash with different values).
    > A collision occurs, the more collisions in the hashMap the less efficient in terms of time complexity the adding or deleting of kvp in the hashMap (Loadfactor increases and the hashMap is not sparsely distributed)

  - Hence the Hashmap in java resolves collision using seperate chaining, so if an object that is different and have a same value, a linked List is being initialised to append colliding objects at that hash bucket 

2. Objects that are the same, (same objects or instances of the same object)
   - the hashCode() method in the class will always generate the same hash for the object 
   - Hence, they will always have the same hash value 

3. Keys in hashMap must be primitive dataTypes and are immutable
   - Given the characteristics of keys in HashMap mainly immutability and primitive dataTypes (numerical) this allows us to be sure that the hash values are constant throughout and one object produces exactly one hash value in which we are able to index it according to the hash generated. If hashes are mutable the consistency and accuracy of the hashTable is loss (degraded performance)
- 
   - If you are using an object as the key it must have a hashCode() that will hash the object based on the hashing algorithm, and equal to comapre if two objects are equal based on their hash value

How is a Hashmap implemented in Java
- Hashmap is a class that is implemented in the java.utils package, the hashMap class extends the Abstract Map class and implements the Map interface, clonable and serializable interface 

  > Benefit: Allowing HashMap class to extend the functionalities of Abstract Map to suit the needs of the application (Open-Closed Principle)



## Initialising of HashMap
- To intialise the Hashmap the following syntax is used ` HashMap<K,V> hashMapName = new HashMap<K,V>();`
- Besides instantiating with a default constructor there are three more methods that uses parameterized constructor to instantiate the HashMap with a specified capcitjy, specified capacity and load factor or from another Map<K,V>
  - a) Specifying an intial cap `Hashmap<K,V> hashMapName = new HashMap<K,V>(int cap)`
  - b) Specifying an initial capacity and load factor`HashMap<K,V> hashMapName = new HashMap<K,V>(int cap, int loadFactor);` 
  - c) Initialising a HashMap from a Map `HashMap<K,V> hashMapName = new HashMap<K,V>(Map map)`


Example of a program using HashMap
``` Java 
import java.util.HashMap;
class Main{         
  static void main(String[] args){
    HashMap<Integer,String> contactList = new HashMap<Integer,String>();
    contactList.put(913101,"Johnathan Tan");
    contactList.put(941490,"Jacob Goh");
    contactList.put(985104,"Kane Tan");
    contactList.put(902501,"John Foo");
    contactList.put(849101,"John Low");

    // Iterating over each entry in the HashMap
    for (Entry<Integer,String> entry: contactList.entrySet()){
      System.out.println("This is the current key: " + entry.getKey() " and this is the current object: " + entry.getValue())
    }

    // printing the entire hashMap
    System.out.println(contactList);

    // priinting the value of a specific key e.g. 913101 in the hashMap
    System.out.println(contactList.get(913101));

    // remove a specified object in the HashMap at the corresponding key
    contactList.remove(913101);

    System.out.println(contactList);
    
    String name = contactList.get(913101);
    // What will be the following output ? ans: NULL as the key and object has been removed 

    // Scenario: Remove the contact of John Low, user keys in name only 

    Scanner myObj = new Scanner(System.in);  // Create a Scanner object
    System.out.println("Enter a name to remove from the contact List: ");
    String contactName = myObj.nextLine();

    // Use iterator to iterate over the Hash Map entries
    for(Entry<Integer,String> entry: contactList.entrySet()){
      if(entry.getValue == contactName){
        Integer objKey = entry.getKey();
        // delete the corresponding object in the set 
        contactList.remove(objeKey);
      }
    }

    // Print the hashMap again to verify sucessful deletion
    for(Entry<Integer, String> entry: contactList.entrySet()){
      System.out.println("This is the key: " + entry.getKey() + " this is the current object: " + entry.getValue());
    }

    // update the new contact number of the corresponding person 
    System.out.println("Enter the name of the person in the contactList to update: ");
    String newContactName = myObj.nextLine();
    System.out.println("Enter the new contact no of the person to update: ");
    Integer contactNum = myObj.nextLine();

    for(Entry<Integer,String> entry: contactList.entrySet()){
      if(entry.getValue() == newContactName){
        // remove the current object and add a new one 
        Integer remKey = entry.getKey();
        contactList.remove(remKey);
        contactList.add(contactNum,newContactName);
      }
    }

  }
}


```

Explanation of the methods used in Java Hashmap
- add(Key,Value) , adds a new key value pair to the HashMap
- remove(Key) removes an object at the corresponding key in the HashMap, return null if there is no corresponding object mapped to the key specified
- remove(Key,Value) , remove the entry of the specified key only if it is mapped to the specified value 
- replace(Key,newValue) : Replaces the key at the specified value only if the key specified is present else it will return null
- entrySet() : Returns a reference to the Map objects as instances of Map.Entry<K,V> allowing us to immediately access the key or value of the current entry


