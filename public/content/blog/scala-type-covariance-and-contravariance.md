+++
date = "2016-07-19T18:16:24+02:00"
draft = false
title = "Scala Type covariance and contravariance"
categories = ["scala"]
+++

## Type Covariance and Contravariance

Quoting from [wikipedia](<http://en.wikipedia.org/wiki/Covariance_and_contravariance_%28computer_science%29>)

> Within the type system of a programming language, covariance and contravariance refers to the ordering of types from narrower to wider and their interchangeability or equivalence in certain situations (such as parameters, generics, and return types).

* covariant: converting from wider (double) to narrower (float).
* contravariant: converting from narrower (float) to wider (double).
* invariant: Not able to convert.

The ability to send a collection of subclass instances to a collection of base class is called covariance

The ability to send a collection of superclass instances to a collection of subclass is called contravariance

By default scala does not allow covariance and contravariance, but there are some good use cases where you might want to use a derived type as a super type.

Lets prepare some base code:

    class Person(val name: String) {
     override def toString = name
    }

    class Employee(override val name: String) extends Person(name)

    val empList = List(new Employee("Joao"), new Employee("Andre"))
    
    val peopleList = List(new Person("Martin"), new Person("Jonas"))
 
    def sayHi(people:List[Employee]) = people.map { println _ }

    sayHi(empList)
    
    sayHi(peopleList) // compilation ERROR

The error is pretty obvious we can’t send a List[Person] as the sayHi function expects a List[Employee] as it’s formal parameter, and here is where covariancecomes into place.

### Covariance

To solve the above compilation error we have to let scala compiler know that it’s ok to treat a Person as an Employee, we 
do that as follows:

    def sayHi[T <: Person](people: List[T]) = people.map { println _ }

sayHi has now a special syntax [T <: Person]. This syntax indicates that T sould be of Type Person or any class that derives from Person, which means that know we can have something like:

    sayHi(empList) sayHi(peopleList)

You can also indicate covariance at the class level by making the parameterized type+T instead off T.
    
    class SomeCollection[+T]

    var lst1 = new SomeCollection[Employee]
    
    var lst2: SomeCollection[Person] = lst1

The above snippet is possible since Employee is a subclass of Person

### Contravariance

Contravariance is the literally the opposite of Covariance, Lets imagine we want to add Employee to Person, as you can see the relationship is from subclass to superclass.

    def appendToPerson[T, D <: T](employees: List[T], people: List[D]) = people ++ employees

With the syntax [T, D <: T], we have constrained the parameterized type D to be of the type T or a super type of T, so basically T sets the lower level in the Type hierarchy for type D. In our example the type D (Person) can be of type T (Employee) or its superclass.

Scala also has class level support for setting contravariance and as you might guess the parameterized type is -T

### Summary

* A class C[T], when a method accepts only C[T] is invariant
* A class C[+T], when a method accepts C[T] i can also get any of it’s dervatives
* A class C[+-T], when a method accepts C[T] i can also get any of it’s super classes

Function Type bounds:

    def fun[T <: A](arg:T) // covariant, arg must be of type T or any of it's subclasses
  
    def fun[T >: A](arg:T) // Contravariant, arg must be of type T or any of it's super class

