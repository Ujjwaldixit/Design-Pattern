# Java Design Pattern
## What are Software Design patterns?
Software Design Pattern can be defined as a blueprint to solve common recurring 
problems in Software.

## Advantages
Some advantages of Design Patterns are:-
- Reusability
- Robust and highly maintainable code
- Easy to understand the code
- Easy to debug
- Faster Development

## Types of Design Patterns
 There are generally 3 types of Design Patterns, which are further categorised into 23 design patterns.
 Types of Design Patterns are:-
1. Creational design pattern
2. Structural design patterns
3. Behavioral design pattern
 <br>
 <br>
 ![Types of Design Patterns](https://i0.wp.com/techvidvan.com/tutorials/wp-content/uploads/sites/2/2020/06/Types-of-Design-Pattern-in-Java.jpg?resize=771%2C476&ssl=1)

Here, we will discuss 5 design patterns.

## 1. Template Design Pattern
Template Method is a behavioral design pattern and its used in the scenarios where the **order of execution of program in fixed and same**.
<br>

 Let's understand this method with the help of one scenario, suppose we are working in the car factory and we want build cars. To build a car there are certain steps we have to follow:
First, we will build the frame of a car, then we will assemble the other parts like engine, seats etc,then finally we will paint the  car.
<br>

The point here is that, we have to follow the sequential order to build the car and is same of all the cars.

 ### **Points to remember**
 - Template method must be **Final**, so that subclass can't overrride them.
 - Since we want some of the methods to be implemented by subclasses, we have to make our base class as **abstract class.**

  ```Java
  public abstract class CarTemplate {

	public final void buildCar(){
		buildFrame();
		installEngineandInterior();
		buildOuterBody();
		Paint();
		System.out.println("Car is built.");
	}
    private void buildFrame() {
		System.out.println("Building frame");
	}

	private abstract void installEngineandInterior();
	public abstract void buildOuterBody();
	public abstract void Paint();

	
}
```
 
Now every car class have to extend above class,whether it is SUV or Sedan or any other.
<br>

```Java
public class SUV extends CarTemplate {

	@Override
	public void installEngineandInterior();{
		System.out.println("Installing SUV engine and interiors");
	}

	@Override
	public void buildOuterBody() {
		System.out.println("Building outer body of SUV");
	}

    public void Paint {
		System.out.println("Paint Red");
	}


}
```


```java
public class Sedan extends CarTemplate {

	@Override
	public void installEngineandInterior();{
		System.out.println("Installing Sedan engine and interiors");
	}

	@Override
	public void buildOuterBody() {
		System.out.println("Building outer body of Sedan");
	}

    public void Paint {
		System.out.println("Paint Black");
	}


}
```
Main Class
```java
public class Main {

	public static void main(String[] args) {
		
		carTemplate carT = new SUV();
    //building Suv
		carT.buildCar();
		
		carT = new Sedan();
	//building Sedan
		carT.buildcar();
	}

}
```
In above code, every class implements there own methods but they followed the same sequence of execution.

## 2. Strategy Pattern
Strategy pattern is used when we have multiple meythods to do  specific task, so we define all methods and let user decide to choose the specific method.

Like to start a bike we have two methods ,either use self start button or use kick start.Rider can choose any of the method.

```java
public interface bikeStart {
   public int start();
}
```

```java
public class selfStart implements Start{
   @Override
   public string Start() {
      return "selfStart";
   }
}
```
```java
public class kickStart implements Start{
   @Override
   public string Start() {
      return "kickStart";
   }
}
```
```java
public class Methods {
   private Methods methods;

   public Methods(Methods methods){
      this.methods = methods;
   }

   public String executeMethods(){
      return strategy.Start();
   }
}
```
```java
public class Main {
   public static void main(String[] args) {
      Methods methods = new Methods(new SelfStart());		
      System.out.println(methods.executeMethods());

      
   }
}
```

## 3. Proxy pattern
Proxy is a structural design pattern that lets you provide a substitute or placeholder for another object.
<br>
Example:-
A credit card is a proxy for a bank account, which is a proxy for a bundle of cash. 
<br>


![proxy image](https://refactoring.guru/images/patterns/diagrams/proxy/live-example.png?id=a268c57fdaf073ee81cf)

## 4. Singleton Pattern
 First we will see , what is a singleton class? Singleton class is a class that can have only one object (an instance of the class) at a time. So singleton pattern is to create a class which can create only one object.
 <br>
 We can make the class singleton by making its constructor private.
First we will create a object then ,by making its constructor private we ensure that no other object can be created by any other class.

```java
public class SingletonClass {

   private static SingletonClass obj = new SingletonClass();
   private SingletonClass(){}
   public static SingletonClass getInstance(){
      return obj;
   }

   public void Message(){
      System.out.println("Hello World?hOW ARE YOU");
   }
}
```

```java
public class SingletonPatternDemo {
   public static void main(String[] args) {
      SingletonClass obj = SingletonClass.getInstance();
      obj.Message();
   }
}
```
## 5. Facade Pattern
This method is used to hide the complexities of the system, this means we hide the internal details of code and show the abstract part to the user.

```java
interface MyInterface
{
   public void method1();
   public void method2();
}
```
```java
class Demo implements MyInterface
{
   public void method1()
   {
	System.out.println("implementation of method1");
   }
   public void method2()
   {
	System.out.println("implementation of method2");
   }
}
```
```java
class Main
{
public static void main(String arg[])
   {
	MyInterface obj = new Demo();
	obj.method1();
    obj.method2();
   }
}
```

## References
- Geeksforgeeks- https://www.geeksforgeeks.org/
- journalDev -https://www.journaldev.com/
- JavatPoint -https://www.javatpoint.com/











    

    


