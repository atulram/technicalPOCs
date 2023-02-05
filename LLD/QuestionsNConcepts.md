**Important Interview Questions**
- LRU
- Elevator
- Rate Limitor
- Distributed Scheduler
- Distributed Crawler





**Concepts**

A good code should be
- Readable : Meaning understandable with proper namings and conventions
- Testable
- Mintanable: Meaning the code should keep on working with no or minimum changes required when the library version change or gets depricated, in case of any bugs or security issue, when the platform changes(eg android version change)
- Extensible: Ability of adding new feature with ease
- Reusable: One behaviour should be written only once

**OOPs**

The principle of object oriented programming is abstraction. Abstraction means working in terms of ideas. A software system is broken into various ideas and each idea represents an entity or a class

The three pillars are implementing abstraction

- Encapsulation: Idea is to hold things together and protect it  from outside.  This is done by using a class which holds the data and the methods together and also protects the data and methods by giving proper access modifiers. We control what other could see

- Inheritance: When multiple entities/class have similar things in them. We club those things and inherit from them.

- Polymorphism: It means we don't need to know the exact concrete class of an object. As long as there is an is-a relationship we can accept any object

The problem with inheritance, Let's say we have an animal class and we have dogs, birds,  etc inherited from the animal class,  if we implement a function called run in all of these classes there may be cases where the bird cannot run.  We may be tempted to inherit a class called running animal from animal. Then all those animals who can run will inherit the running animal class and the ones who cannot run will inherit the nonrunning animal class, but this is not a good solution as tomorrow there can be a sleeping animal and a nonsleeping animal. We would need to inherit the concrete classes from these classes.  The approach would be to use interfaces for behaviors.

Interfaces are blueprints of a behavior.

In the above example, we will have interfaces like running sleepable, walkable,  eatable. We will make the animal class inherit walkable and eatable whereas the child classes who can sleep well implement the sleepable interface and those who can run will implement the runnable interface.

So unless there is a guarantee that all the sub-classes of the class will have that behavior represent that behavior as an interface. 
We will only add a behavior to a class when that behavior is an inherent property of  that entity

