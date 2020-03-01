# Answers:

1.Bounds vs frames

Bounds - relative to its own coordinate system.
Frame - relative to superview it is contained within.

2. Operator overloading vs method overloading vs method overriding:

Operator overloading - existing operators(-, +, /, *) behave with types.

Method Overloading -  same method name but different parameters. Compile time.

Method Overriding - same method name and parameters. Parent class - child class. Run time. 
Polymorphism applies overriding not overloading.

3. Advantages of swift:

Compile time programming language
Open source
Safer platform/Type-safe language - fix errors in compile time
Readability - clean syntax
Maintenance - less code, one file  
Built in Error handling
Closures
Tuples
Optional Types - crash resistant
Fast/High speed - LLVM compiler transforms swift code into optimised native code.

4. Difference between class and structure when to use:

Type casting
Reference counting 
Inheritance
Deinitializers
Structs are value types and pass by value, Classes are reference types 
and pass by reference. 
Structures are always copied when they are passed around, no 
reference counting.

Structure :

Primary purpose is to encapsulate simple data values.
Encapsulated values will be copied rather than referenced.
Any properties stored are themselves value types.
No inheritance

Class:

Pass by reference

5. Design patterns:

Reusable solution to common problems in software design. Templates - easy to understand - reuse.

Creational - Singleton
Structural - Decorator, Adaptor, Facade
Behavioural - Observer and Memento

Singleton - Single instance, global access point, lazy loading.
Decorator - Extensions and delegation, adds behaviour and responsibilities without modifying code.
Adaptor - Standard interface, incompatible interface to work together.
Facade - Single interface to complex subsystem.
Observer - Notifications and KVO, notifies other object of any state changes.
Memento - externalised state restored without violating encapsulation; private data remains private, Apple - Archiving and state restoration.

6. How to pass variable as reference:

inout -  Modifying the local variable will also modify the passed-in parameters. Point original data in memory.
    var value: String = “Apple”
    func changeString(newValue:inout String) {
         newValue = “Samsung”
         print(newValue) // Output:Samsung
         print(value) // Output:Samsung
    }
    changeString(newValue:&value)

7. Generics - example

Write flexible, reusable functions and types that can work with any type. Avoid duplication and expresses its intent in a clear, abstracted manner.

Swift’s Array and Dictionary types are both generic collections.
eg:
    func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
         let temporaryA = a
         a = b
         b = temporaryA
    }
    var num1 = 4
    var num2 = 5
    var str1 = “a”
    var str2 = “b”
    swapTwoValues(&num1,&num2)
    swapTwoValues(&str1,&str2)
    print (“num1:”, num1) //output: 5
    print (“num2:”, num2) //output: 4
    print (“str1:”, str1) //output: b
    print (“str2:”, str2) //output: a

8. Lazy

- Delaying the creation of an object or some other expensive process until it’s needed. 
- Use only with Class and struct member. 
- Not thread safe because of not initialised automatically .
- With the var.
- Constant properties must always have a value before initialisation completes, and therefore cannot be declared as lazy.

9. Defer
- Execute a set of statements just before code execution leaves the current block of code.
- The defer statement inside the if code block will be executed first. Then it follows a LIFO pattern to execute the rest of the defer statements.
    func doSomething() {
        defer { print(“1”)}
        defer { print(“2”)}
        defer { print(“3”)}
        if 1<2 {
        defer { print("1<2")}
    }
    defer { print(“4”)}
    defer { print(“5”)}
    defer { print(“6”)}
    }
    Output 1<2 6 5 4 3 2 1

10. Guard vs if else
- Early exit/Faster execution - Runs if condition is false, exit out though control transfer statement - return, break, continue or thrown.
- Safely unwrap optionals
- Avoid pyramid of doom 

Use guard to eliminate incorrect/ unexpected input, Use if alternate ways to handle input.
Else case is too short to handle.

11. Closure - example
- Self contained chunks of code that can be passed around and used in your code.
- Blocks in C and Objective-C and lambdas in other programming 
languages. Link : https://fuckingclosuresyntax.com

Escaping closure:
        
- Passing the closure in function’s arguments, using it after the 
function’s body gets execute and returns the compiler back.
- When the function ends, the scope of the passed closure exist and have existence in 
memory, till the closure gets executed.

- Storage 
- Asynchronous execution

Non escaping closure:
        
- Passing a closure in function’s arguments, using it before the function’s 
body gets execute and returns the compiler back.
- When the function ends, the passed closure goes out of scope and have no more 
existence in memory. 
Link: https://medium.com/@bestiosdevelope/what-do-mean-escaping-and-nonescaping-closures-in-swift-d404d721f39d
        
Auto closure: 
- Automatically created to wrap an expression that’s being passed as an 
        argument.
        
Trailing closure: 
- Long closure expression to pass trailing closure. 
        
Capturing values : 
- Capture contents and variables from surrounding context.
        
Capture List : 
- To break strong reference cycle.
        
12. ARC :
- Compile time
- Frees up memory when zero strong references.
- Memory management based on retain count.
- Retain cycle - A -> B & B-> A, Weak used to break retain cycle.
- Closure - capture list ( Strong(default), weak, unowned) to break retain cycle.
- Define variables that will be used in closure.Thus avoiding retain cycle.
        
self.action = { [ selfView = self.view ] in 
    selfView.alpha = 0.5 
}
        
or 
        
self.action = { [view] in 
    view.alpha = 0.5 
}
        
13. Strong, weak vs unowned
Strong - reference count increases, reference maintain life of the object.
Weak - no reference count increases, optionals , var, automatically changes to nil.
Unowned -   no reference count increases, non-optionals , let , it cannot be nil.
        
14. Optionals, optional binding, Optional chaining.
- type can hold either value or no value - Optionals
- Safe way of unwrapping optionals - Optional binding
- Process of querying, calling properties, subscripts, methods on optionals - Optional     
chaining
        
15. Forced unwrapping/ Implicit unwrapping
- Way of extracting the value contained inside optional - Forced
- Automatically perform force unwrap - Implicit
        
16. Access level in swift.
- Five different access levels for entities within your code.
        
Open access: Classes with open access - subclassed or overridden by 
subclasses within the module where they’re defined and within any module that 
imports the module where they’re defined.
        
Public access: Classes with public access can be subclassed or overridden by 
subclasses only within the module where they’re defined.
        
Internal access: enables entities to be used within any source file from their defining 
module, but not in any source file outside of that module.
        
File-private access: restricts the use of an entity to its own defining source file.
        
Private access: restricts the use of an entity to the enclosing declaration, and to 
extensions of that declaration that are in the same file.
        
Open access is the highest (least restrictive) access level and private access is the lowest (most restrictive) access level.
All entities in your code (with a few specific exceptions) have a default access level of internal.
        
17. Application life cycle
- ApplicationWillFinishLaunchingWithOptions
- ApplicationDidFinishLaunchingWithOptions
- ApplicationDidBecomeActive
- ApplicationWillResignActive
- ApplicationDidEnterBackground
- ApplicatonWillEnterForeground
- ApplicationWillTerminate
        
18. Application states
- notRunning
- InActive
- Active
- Background
- Suspended
        
19. View controller life cycle 
- loadView
- viewDidLoad
- viewWillAppear
- viewWillLayoutSubviews
- viewDidLayoutSubviews
- viewDidAppear
- viewWillDisappear
- viewDidDisappear
- viewWillTransitionTo
        
20. Tuple
- Group of 1 or more value represent one value.
- Return multiple values from function
- Tuple - Dictionary(Can be created on fly) + Struct(Holds data)
- Named tuple and UnnamedTuple.
        
21. Stack and Heap
Stack - Static memory allocation, Compile time, Fast, LIFO order. Execution remains suspended until last function returns value, Easy to track, Value types, Thread specific:each thread have separate stack but share heap.
Heap - Dynamic memory allocation, Run time, Slower, Difficult to track - allocate memory anytime, free anytime. Reference types.Application specific.
Value type - Int, double, String, Array, Dictionary, Set, Struct, enum, Tuple.
        
Reference types - Functions, classes, Closures.
        
22. App store submission
- Assemble Appstore Information
- Create Bundle ID
- Create a Certificate Signing Request
- Create Distribution certificate and profile.
- Create app store listing.
- Create a Release build Fill in version info
- Submit version for review
- Release
        
23. Store - kit
- Consumable : Buy more than once (Pay every time)
- Non Consumable : Buy only once. Permanently it will be there. (one time payment)
- Non renewing : Content available fixed period of time.(Renew manually)
- Auto renewing : Repeating subscription like Monthly.(will deduct money on cycle complete).
        
        
24. Final vs Static:
- Static means there is only one copy of the variable in memory shared by all instances of the class. The final keyword just means the value can't be changed. Without final , any object can change the value of the variable. Link: https://stackoverflow.com/questions/13772827/difference-between-static-and-final
        
25. Push notification
- App registers for push notification - OS asks APNS for device token - App receives device token - App sends device token to server - Something happens send push notification to APNS 
- APNS send push notification to app. Link: https://stackoverflow.com/questions/32775132/what-is-push-notification-and-how-to-get-chat-notification-in-ios
       
26. Core data
- Link: https://medium.com/xcblog/core-data-with-swift-4-for-beginners-1fc067cca707
        
        
        
        
        


