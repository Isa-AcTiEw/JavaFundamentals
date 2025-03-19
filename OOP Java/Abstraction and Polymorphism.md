# Abstraction 
- Abstraction is a OOP concept that enables the hiding of non-relevant methods and implementation details from
other classes, basically it abstracts the functionalities of a class.
	- This allow the subclasses to extend the functionailities through overriding abstract 
	- methods or implementing methods defined in interfaces 

## Ways abstraction is achieved in java 
1. Abstact classes 
2. Interfaces 

### Abstract class 
- An abstract class is a class that cannot be instantiated which means that there can be no objects being 
instantiated from the abstract class, it contains both concrete and abstract methods and can have class 
attributes 

- To create an abstract class the keyword `abstract` is used 

Example of an abstract class 
``` Java
package com.example.java; 
 
import java.lang.Math;

abstract class Shape3D(){
	public double volume;
	public double abstract findSurfaceArea();
	public double abstract calculateVolume();
	@Override 
	public String toString(){
		System.out.println("This is the length: " + length + " this is the height: " + height);
	}
} 

class Cube extends Shape3D {
	private int numSides;
	private double length;

	Cube(int l, int h, int b, int numS){
		this.length = l;
		this.height = h;
		this.numSides = numS;
	}
	
	@Override 
	public double findSurfaceArea(){
		double oneSurfaceArea = length * length;
		return oneSurfaceArea * numSides;
	}

	@Override 
	public double calculateVolume(){
		return Math.pow(length,3);
	}
}

class Cylinder extends Shape3D {
	private double slantHeight;
	private double radius;
	
	@Override 
	public double findArea(){
		return 2 * Math.pi * Math.pow(radius,2) + 2 * Math.pi * height;
	}

	@Override 
	public double calculateVolume(){
		return Math.pi * Math.pow(radius,2) * height;
	}

}


```

- The class Shape3D is an abstract class, the classes Cylinder and Cube both extend the abstract class Shape3D and hence 
it inherits all attributes and methods (concrete or abstract). In this case both classes will override the abstract 
method `calculateVolume` and `calculateArea` based on their mathematical properties and forumulae.

- For a subclass to implement an abstract method the annotation `@Override` is being 
utilised enabling the sub classes to override and implement the abstracts method defined in the abstract class 


## Interface
- An interface refers to contract or blueprint that defines a set of methods that a class must implement 
> Note! : That an interface cannot have any attributes or any concrete methods, it is a pure blueprint for subclasses
concrete classes to extend its functionalities 

- To define an interface in Java the keyword `interface` is being utilised 

``` Java
// In the context of strategy design pattern 

// Conversion Strategy
interface conversionStrategy {
	void convert();
}
// in the concrete strategies (implement the fly method)

class pdfConversionStrategy implements conversionStrategy{
	@Override 
	void convert(){
		System.out.println("Converting document to pdf");
	}
}

class wordConversionStrategy implements conversionStrategy{
	@Override 
	void convert(){
		System.out.println("Converting document to word");
	}
}
```
- In this example we used the strategy design pattern to encapsulate what changes, the common interface conversionStrategy is used to abstract
away the implementation details of convert() method, delegating the implementaiton of the behaviour of the class to the subclasses
. This allows for the current code to be easily extended without modifying other classes

> classes would just need to implement the interface and can extend based on their own specific behaviour 
 