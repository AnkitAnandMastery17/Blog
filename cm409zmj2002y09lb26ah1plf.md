---
title: "Demystifying Object-Oriented Programming: Fundamental Ideas and Key Principles (Part 1)"
seoTitle: "Intro to Object-Oriented Programming Fundamentals"
seoDescription: "Discover OOP fundamentals: classes, objects, and association types in this comprehensive guide"
datePublished: Wed Nov 27 2024 19:25:18 GMT+0000 (Coordinated Universal Time)
cuid: cm409zmj2002y09lb26ah1plf
slug: demystifying-object-oriented-programming-fundamental-ideas-and-key-principles-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1732716996226/32d40b24-5900-4e84-a998-cef3a7457780.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1732734269427/862eb01f-8d75-47eb-8978-317b33c8ccd5.jpeg
tags: programming-blogs, java, programming-languages, object-oriented-programming, classes-and-objects

---

Hello! I'm Ankit, and I'm thrilled to connect with you. In this blog, I'll delve into some foundational concepts that will enhance your understanding of OOP principles. I'm eager to share my insights with you.

# What does the term OOP mean?

The full form of OOP is object-oriented programming. It is an paradigm or a methodology to design a program using classes and objects. It simplifies software development by providing some concepts→

1. Object
    
2. Class
    
3. Abstraction
    
4. Polymorphism
    
5. Inheritance
    
6. Encapsulation
    

Apart from these concepts there are some other terms which are used in object oriented design.

1. **Cohesion**→ Cohesion defines how effectively elements within a module or object work together to fulfill a single well defined task. High level of cohesion means elements are tightly integrated and working together to achieve the desired functionality.
    
2. **Coupling**→ Coupling defines the degree interdependence of software modules. Tight coupling means that modules are closely connected and changes made in one module will effect the other. Loose coupling means modules are independent and changes made in one module will have minimal impact on other.
    
3. **Association**→ Association represents the relationship between the objects. There are 4 types of association:
    
    * one to one
        
    * one to many
        
    * many to one
        
    * many to many
        
4. **Aggregation**→ Aggregation is a way to achieve Association. Aggregation represents the relationship where one object contains other objects as a part of its state. It represents the weak relationship between objects. It is also termed as a *has-a* relationship in Java. Like, inheritance represents the *is-a* relationship. It is another way to reuse objects.
    
5. **Composition**→ The composition is also a way to achieve Association. The composition represents the relationship where one object contains other objects as a part of its state. There is a strong relationship between the containing object and the dependent object. It is the state where containing objects do not have an independent existence. If you delete the parent object, all the child objects will be deleted automatically.
    

## Class

A class is a user defined blueprint or prototype from which objects are created. It represents a set of properties and methods. It is a logical entity i.e. it doesn’t occupy space in the memory. Using class you can create multiple objects with the same behavior instead of writing their code multiple number of times.

# Object

Any entity which has states and properties is known as object. State or data means the information of the object and properties means the methods which use state to perform an operation. It is a physical entity which means it occupy space in the memory. It is also known as instance of a class. Here Pen is an object which contains states and properties.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1732727580571/35263cb9-ccdd-49b4-a7a5-357c0a0805a3.png align="center")

### Syntax of class

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1732732024564/c0500640-3757-48ea-be22-1c4a92cdcfc8.png align="center")

Member variables and member methods combinedly called member of the class. Member of a class can be divided into two parts→

* Static member
    
* Non-static member
    

Example→

```java
Class Demo{
  static int x=200;   //Static variable
  int y=100;          // Non static variable

//static method
public static void method1{
 System.out.println("Running static method");
  int a=200;   //local varaible
}
//Non static method 
 public void method2{
System.out.println("Running non-static method");
int b=12;  // local variable
}
```

### Dot Operator

The dot operator is used to access the members of any class. The member can be static or non-static.

## Accessing Static member of a class

syntax→

```java
classname.membername;
```

Example→

```java
public class dotOperator {
    public static void main(String[] args) {
        System.out.println("x value :"+ demo1.x ); // accessing the static variable
        demo1.test();   // accessing the static method
    }
}
 class demo1{
     static int x=200;
     static void test(){
         System.out.println("Running static method test");
     }
}
```

Result→

```plaintext
x value :200
Running static method test
```

* NOTE→ A static variable of any class can be re-initialized in any part of the program.
    

```java
public class reInitializationOfStaticVariable {
    public static void main(String[] args) {
        System.out.println("x value:"+ demo2.x);
        demo2.test();

        System.out.println("After reinitialization");
        demo2.x=200;
        System.out.println("x value after reinitialization :" +demo2.x);
    }

}

class demo2{
    static int  x=100;
    static void test()
    {
        System.out.println("Hello");
    }

}
```

Result→

```plaintext
x value:100
Hello
After re-initailization
x value after re-initailization :200
```

# Accessing the non-static member of a class

To access the non-static member of a class first we need to create an object of that class, without object it is not possible to access the non-static member of a class.

syntax for object creation→

```plaintext
new classname();
```

Example→

```java
public class accessingNonStaticMember {
    public static void main(String[] args) {

        System.out.println("y value: "+ new demo3().y);
        System.out.println("x value: "+ new demo3().x);

        new demo3().test();
    }
}
class demo3{
    int y=12;
    int x=20;
    void test()
    {
        System.out.println("Running");
    }
}
```

Result→

```plaintext
y value: 12
x value: 20
Running
```

### This is where we end today, but your learning journey continues!

I’d love to hear your thoughts! Share your feedback or experiences in the comments below.

Let’s connect! Follow me here or on LinkedIn/Instagram/Twitter for more insights.

Stay tuned for my next post, where I’ll dive into more deep into the topic. Don’t miss it.

### Thank you for reading! 😊