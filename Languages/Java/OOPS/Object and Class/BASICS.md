# Basics

## To create object

There are many ways to create an object in java. They are:

- By new keyword
- By newInstance() method
- By clone() method
- By deserialization
- By factory method etc.

## Initializing object

3 ways:

1. Initializing through reference:  
   `s1.id = 101`
   `s1.name = "abc"`
2. Through method:
   `s1.insertRecord(111, "abc")`
3. Through constructor:
   Discused below.

### Constructor

Rules for constructor:

1. Constructor name same as class name
2. No return type
3. Cannot be abstract, static, final and synchronized.

Two types of constructors:

1. Default  
   `<class_name>(){}`
2. Parametrized  
   `<class name>(parameters){}`

Constructor overloading - Can use many constructors for same class and overload.

There is no copy constructor in java, so we can copy values of one obj to another via a constructor, assignment or `clone()`

## Static keyword

Static can be applied to:

1. Variable
2. Method
3. Block
4. Nested Calss

### Static Variable

If we add static to a variable, it's only allocated to memory once and all objects share that memory. (For example, a student class has the college name same for all students in a college. )

### Static method

Static method belongs to class rather than object.  
Class methods can be invoked without creating instances.  
Static method can access static data member and change its value.

Restrictions on static methods:

- Cannot call non-static data members or call non-static methods directly.
- `This` and `super` cannot be used in static context.

Java main method static because the object is not required to call a static method. If it were a non-static method, JVM creates an object first then call main() method that will lead the problem of extra memory allocation.

### Static block

Initialize static data member and executed before the main method at the time of class loading.

```
class A2{
  static{System.out.println("static block is invoked");}  // <- This gets run first before main
  public static void main(String args[]){
   System.out.println("Hello main");
  }
}
```

## This Keyword

`this` refers to the current object.  
Usages:

- this can be used to refer current class instance variable.
- this can be used to invoke current class method (implicitly)
- this() can be used to invoke current class constructor.
  Rule: Call to this() must be the first statement in constructor.
- this can be passed as an argument in the method call.
- this can be passed as argument in the constructor call.
- this can be used to return the current class instance from the method.
