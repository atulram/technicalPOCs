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

The three pillars of implementing abstraction

- Encapsulation: Idea is to _hold things together_ and _protect_ it  from outside.  
    - This is done by using a **class** which holds the data and the methods together 
    - and also protects the data and methods by giving proper access modifiers(public, private, protected, default) We control what other could see
    - We can hide the details and only expose the things that we want to support in future because others will be using it

- Inheritance: When multiple entities/class have similar things in them. We club those things and inherit from them.
is-a relation

- Polymorphism: It means we don't need to know the exact concrete class of an object. As long as there is an is-a relationship we can accept any object. So a function/variable etc that accepts an animal will be able to accept any sub-class of animal as well 
eg. 
    - Animal a = createAnimal() -> can retrun a dog as well
    - function feed(Animal a) -> can take a husky as well
    - Upcasting is not allowed, dog d = new Animal() X

The problem with inheritance, Let's say we have an animal class and we have dogs, birds,  etc inherited from the animal class,  if we implement a function called run in all of these classes there may be cases where the bird cannot run.  We may be tempted to inherit a class called running animal from animal. Then all those animals who can run will inherit the running animal class and the ones who cannot run will inherit the nonrunning animal class, but this is not a good solution as tomorrow there can be a sleeping animal and a nonsleeping animal. We would need to inherit the concrete classes from these classes.  The approach would be to use interfaces for behaviors.

**Interfaces are blueprints of a behavior.**

In the above example, we will have interfaces like runnable, sleepable, walkable,  eatable. We will make the animal class inherit walkable and eatable(because we know that eevry animal will be able to eat and walk, as these are the inherent behaviours of an animal) whereas the child classes who can sleep well implement the sleepable interface and the child classes those who can run will implement the runnable interface.

So unless there is a guarantee that all the sub-classes of the class will have a certain behavior its always better to represent that behavior as an interface. So that we will only add a behavior to a class when that behavior is an inherent property of that entity or else child class can always implement as many interfaces they want. Making our code extensible

Runnable r = new Dog(), then take alist of runnable objects -> dog class has implemented runnable function

**SOLID**
- Single responsibility principle 

    Every code unit should have only one well-defined responsibility.  A code unit can be a package, class, or a function

    eg consider a  bird class

    It can have attributes like species, type, color, etc.

    - We can consider a method fly.  How a bird flies depends on the species of the bird.  An Eagle can fly high a sparrow can fly low and so on.  We can see that each type of bird will implement the fly function differently one way is to **have multiple if-else conditions** in the fly method based on the type of the bird.  This is wrong one indication of a violation of the single responsibility principle is,  multiple if else conditions
    
    - Another way to look at it is in **how many ways we will have to open the class**. One is when a new attribute or behavior needs to be added to a bird class,  and the second is when any of the birds change the way it flies.  We should definitely have the first one but the second one is not necessary

    - Another way to identify the violation of SRP is if there is a Monster function.  It is a function that performs more tasks than the name suggests. eg.  Consider a log function it connects to a database, executes the query, and then logs the output.  A better way is to have a connect to database function and a create query function and then delegate please responsibilities to the respective functions. Basically, delegate the responsibility of a monster functions to other smaller functions.

    - Another way to identify the violation of SRP is if the utility package has multiple functions which are unrelated. A better way is to segregate everything.  Have a utils folder inside the utils folder has different folders let one of the folders inside is a date,  then inside the date folder have multiple classes.  Each of these classes will be solely responsible for one thing.  This helps when in the future if you want to completely take out this component, then we will not have to worry about multiple places to look for

        Pros:
        - Reusability
        - Bloated code reduction, Readability
        - Testinng

        Cons:
        - Lot of files

- Open/Close: Any code unit should be open for extension but closed for modificaion when adding a new feature. (like a new class/function)

    Solving the fly method of bird class, we can think of making a parent bird class and then each bird will inherit the bird class and implement a flyable interface to add its own implementation in the fly method, but that way if some birds have similar flying behavior we can't reuse the code. So a better way is to have an interface flyable implemented by each bird and a flying behavior interface implemented by a class that gives the implementation of the fly method and every bird must compose this class and call its fly method in its fly method. Favor composition over inheritance (has-a over is-a). Also if some birds can't fly they won't implement the flyable interface

- Liskov's Substitution principle: Any variable of a parent class should be AS-IS substitutable by an instance of any child class without the client needing to do any code change

    Bird b = new Parrot,  Any line below this should not need to worry if we replace Bird b = new Kiwi(). 

    So this stops the developer from poorly implementing the kiwi fly metthod to through an error when called

    Another thing that Liskovs substitution says is that child classes shouldn't give any special or other defination to the methods of parent class
    (**Minimize surprises**)

- Interface Segregation principle: Keep the interfaces as light as possible. Have very less numbers of methods in the interfaces. Interfaces should be for a specific purpose

- Dependency inversion: No two concrete classes(any class that can be instantiated) should be directly connected to each other.  They should be connected via an interface

    It promotes loose coupling

    let's say flipkart client class depends on razorpay for payment, if flipkart class is directly using razorpay then if in future flipkart wants to move to payu then it will have to change its client. Rather the right way would be for the flipkart client to use an interface and there should be a adapter which implement that interface for razorpay, payu etc
    
    eg.

    PaymentApi api = new RazorPayAdapter()
    
    PaymentApi api = new PayUAdapter()

    and not RazorPay razorPay = new RazorPay()

    But still we are creating a object of the Adapter in the flipkart class. Dpendency injection makes it more loosely coupled by making the Flipkart constructor accept the adapter

    Payment api;
    Flipkart(Payment api) {
        this.api = api
    }

    code can run for different adapters, whatever the client wants
    Inevrsion of control is another concept that tells that even the caller of the flipkart class need not pass the adapter object, the framework will handle it. 