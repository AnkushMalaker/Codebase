# Method overriding

Rules:

1. The method must have the same name as in the parent class
2. The method must have the same parameter as in the parent class.
3. There must be an IS-A relationship (inheritance).

Example:

```
class Vehicle{  
  //defining a method  
  void run(){System.out.println("Vehicle is running");}  
}  
//Creating a child class  
class Bike2 extends Vehicle{  
  //defining the same method as in the parent class  
  void run(){System.out.println("Bike is running safely");}  
  
  public static void main(String args[]){  
  Bike2 obj = new Bike2();//creating object  
  obj.run();//calling method  
  }  
}  
```

Note:
`Static` methods can't be overridden and `main` cant be either.

## Covariant Return Type

Method overriding by changing return type.

```
class A{  
A get(){return this;}  
}  
  
class B1 extends A{  
B1 get(){return this;}  
void message(){System.out.println("welcome to covariant return type");}  
  
public static void main(String args[]){  
new B1().get().message();  
}  
}  
```

This will output: "welcome to .. ."
