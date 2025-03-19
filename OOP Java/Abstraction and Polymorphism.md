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