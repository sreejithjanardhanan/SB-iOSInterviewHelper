# SB-iOSInterviewCheatsheat

This cheat sheet to crack interview for iOS

# Important questions :

Q.What is the Swift and its advantages?
A.Swift is a general-purpose, multi-paradigm, compiled time programming language developed by Apple Inc. for iOS, macOS,         watchOS, tvOS, and Linux.
  Readability — Clean syntax, which makes it easier to read and write.
  Maintenance — Less Code & Less Legacy — one file .swift.
  Safer Platform — You can compile, and fix the errors while writing the code.
  High Speed — The incredibly quick and high-performing LLVM compiler transforms the Swift code into optimized native code to   get the most out of its devices. The syntax and standard library have also been tuned to make the code perform optimally.
  Swift Supports Dynamic Libraries
  Open Source
  
Q.Explain difference between class and structure.
A.There are mainly four difference between class and struct in swift. 
  Classes have below additional capabilities that structures do not:
  Type Casting : Type casting enables you to check and interpret the type of a class instance at runtime.
  Reference counting allows more than one reference to a class instance. (Structs are value types and Classes are reference     types.)
  Inheritance enables one class to inherit the characteristics of another.
  Deinitializers enable an instance of a class to free up any resources it has assigned.
  
  Structures are always copied when they are passed around in your code, and do not use reference counting. Structure       
  instances are always passed by value, and class instances are always passed by reference.
  
Q.When to use class and when to use struct?
A.As a general guideline, consider creating a structure when one or more of these conditions apply:
  The structure’s primary purpose is to encapsulate a few relatively simple data values.
  It is reasonable to expect that the encapsulated values will be copied rather than referenced when you assign or pass around   an instance of that structure.
  Any properties stored by the structure are themselves value types, which would also be expected to be copied rather than       referenced.
  The structure does not need to inherit properties or behavior from another existing type.
  In all other cases, define a class, and create instances of that class to be managed and passed by reference.

Q.How to pass a variable as a reference?
A.We can pass variable as a reference using inout parameter. inout means that modifying the local variable will also modify     the passed-in parameters.

    var value: String = “Apple”
    func changeString(newValue:inout String) {
    newValue = “Samsung”
    print(newValue) // Output:Samsung
    print(value) // Output:Samsung
     }
    changeString(newValue:&value)
        
Q.What is swift module?
A.A module is a single unit of code distribution.
  A framework or application that is built and shipped as a single unit and that can be imported by another module with
  Swift’s import keyword.
  Each build target (such as an app bundle or framework) in Xcode is treated as a separate module in Swift.
  
Q.What are the different Access Levels in swift?
A.Swift provides five different access levels for entities within your code.
  Open access: Classes with open access can be subclassed or overridden by subclasses within the module where they’re defined   and within any module that imports the module where they’re defined.
  Public access: Classes with public access can be subclassed or overridden by subclasses only within the module where they’re   defined.
  Internal access: enables entities to be used within any source file from their defining module, but not in any source file     outside of that module.
  File-private access: restricts the use of an entity to its own defining source file.
  Private access: restricts the use of an entity to the enclosing declaration, and to extensions of that declaration that are   in the same file.
  Open access is the highest (least restrictive) access level and private access is the lowest (most restrictive) access         level.
  All entities in your code (with a few specific exceptions) have a default access level of internal.
  
Q.Explain lazy in Swift ?
A.Lazy initialization — technique for delaying the creation of an object or some other expensive process until it’s needed.     These properties can only use with class and struct member.Lazy properties are not thread safe because of not initialized     automatically .
  You must always declare a lazy property as a variable (with the var keyword).
  Constant properties must always have a value before initialization completes, and therefore cannot be declared as lazy.

Q.What is tuple in swift ?
A.A tuple is a group of zero or more values represented as one value. They are commonly used to return multiple values from a   function call.
  Tuple = Dictionary(can be created on the fly) + Struct (hold very specific types of data)
  There are two types of Tuple in swift
  1.Named Tuple
         
    let nameAndAge = (name:”Midhun”, age:7)
    Access the values like:
    nameAndAge.name //Output: Midhun
    nameAndAge.age //Output: 7
    
  2. Unnamed Tuple
  In unnamed tuple we don’t specify the name for it’s elements.

    let nameAndAge = (“Midhun”, 7)
    Access the values like:
    nameAndAge.0 //Output: Midhun
    nameAndAge.1 //Output: 7

Q.What is Enumeration ?
A.An enumeration defines a common type for a group of related values and enables you to work with those values in a type-safe   way within your code.
  Unlike C and Objective-C, Swift enumeration cases are not assigned a default integer value when they are created.

Q.What is Associated Values?
A.Associated values are more like variables, associated with one of the enumeration cases.

     enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
    }
    
 “Define an enumeration type called Barcode, which can take either a value of upc with an associated value of type (Int, Int,   Int, Int), or a value of qrCode with an associated value of type String.”
 It is sometimes useful to be able to store associated values of other types alongside case values.
 This enables you to store additional custom information along with the case value, and permits this information to vary each   time you use that case in your code.
 
Q.Explain generics in Swift ?
A.Generics enables you to write flexible, reusable functions and types that can work with any type. You can write code that     avoids duplication and expresses its intent in a clear, abstracted manner.
  Swift’s Array and Dictionary types are both generic collections.
  In below code,generic function for swap two value is used for string and integer. It is the example of reusable code.
     
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
    
Q.What is optional in swift & when to use optional?
A.An optional in Swift is a type that can hold either a value or no value. Optional are written by appending a “?” to any       type.
  Use cases of optional:
  1. Things that can fail (I was expecting something but I got nothing)
  2. Things that are nothing now but might be something later (and vice-versa)
  Good example of optional:
  1.A property which can be there or not there, like middleName or spouse in a Person class.
  2.A method which can return a value or nothing, like searching for a match in an array.
  3.A method which can return either a result or get an error and return nothing, like trying to read a file’s contents (which     normally returns the file’s data) but the file doesn’t exist.
  4.Delegate properties, which don’t always have to be set and are generally set after initialization.
  5.For weak properties in classes. The thing they point to can be set to nil at any time.
    When you need a way to know when a value has been set (data not yet loaded > the data) instead of using a separate 
    dataLoaded Boolean.

Q.What is optional chaining in swift?
A.The process of querying, calling properties, subscripts and methods on an optional that may be ‘nil’ is defined as optional   chaining. Optional chaining return two values −
  if the optional contains a ‘value’ then calling its related property, methods and subscripts returns values
  if the optional contains a ‘nil’ value all its its related property, methods and subscripts returns nil
  Optional chaining is the alternative of forced unwrapping.
  
Q.What is forced unwrapping?
A.Forced Unwrapping : It’s the way of extracting the value contained inside an Optional. This operation is dangerous because     you are telling the compiler: I am sure this Optional value does contain a real value, extract it!

    let value: Int? = 1
    let newValue: Int = value! // Now newValue contains 1
    let anotherOptionalInt: Int? = nil
    let anotherInt = anotherOptionalInt! // Output:fatal error: unexpectedly found nil while unwrapping an optional value.
    
Q.What is implicit unwrapping?
A.Implicit Unwrapping : When we define an Implicitly unwrapped optional, we define a container that will automatically         
  perform a force unwrap each time we read it.

    var name: String! = “Virat”
    let student = name // If now we read text
    name = nil
    let player = name //fatal error: unexpectedly found nil while unwrapping an Optional value
    
If an implicitly unwrapped optional is nil and you try to access its wrapped value, you’ll trigger a runtime error. The result is exactly the same as if you place an exclamation mark after a normal optional that doesn’t contain a value.

Q.What is Optional binding ?
A.You can unwrap an optional in both a “safe” and “unsafe” way. The safe way is to use Optional Binding.
Optional binding used to find out whether an optional contains a value, and if so, to make that value available as a temporary constant or variable. There’s no need to use the ! suffix to access its value.

    let possibleString: String? = "Hello"
    if let actualString = possibleString {
    // actualString is a normal (non-optional) String value
    // equal to the value stored in possibleString
    print(actualString)
    }
    else {
    // possibleString did not hold a value, handle that
    // situation
    }
    
Q.What is Guard statement and its benefits?
A.Guard statement is simple and powerful. It checks for some condition and if it evaluates to be false, then the else       
  statement executes which normally will exit a method.

    func addStudent(student: [String: String]) {
    guard let name = student["name"] else {
    return
    }
    print("Added \(name)!")
    guard let rollNo = student ["rollNo"] else {
    print("roll No not assigned")
    return
    }
    print("Assigned roll no is \(rollNo).")
    }
    addStudent(student: ["name": "Ravi"])
    // Prints "Added Ravi!"
    // Prints "roll No not assigned"
    addStudent(student: ["name": "Ravi", "rollNo": "1"])
    // Prints "Added Ravi!"
    // Prints "Assigned roll no is 1"
  Benefit of guard statement is faster execution. A guard block only runs if the condition is false, and it will exit out of     the code block through a control transfer statement like return, break, continue, or thrown. It provides an early exit and     fewer brackets. Early exit means faster execution.
  
Q.When to use guard let and if let?
A.Use guard when we want to eliminate unexpected/incorrect input and focus on purpose and use if when we have alternative ways   to handle input.
  Use guard if else block is relatively short to reduce nesting and indentation.
  
Q.What is defer ?
A.Defer statement to execute a set of statements just before code execution leaves the current block of code.
The defer statement inside the if code block will be executed first. Then it follows a LIFO pattern to execute the rest of the defer statements.
      
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
    
Q.List out what are the control transfer statements used in Swift?
A.break — The break statement ends execution of an entire control flow statement immediately
  continue — The continue statement tells a loop to stop what it is doing and start again at the beginning of the next    
  iteration through the loop.
  return — returns values from functions.
  throw —used in propagating errors Using Throwing Functions
  fallthrough — fallthrough statement is used in switch case to execute case statements which is next to the matched case       statements based on our requirements.
  In swift, fallthrough statement is used to execute next switch case statement event if it is not matching.
  
    let integerToDescribe = 5
    var description = “The number \(integerToDescribe) is”
    switch integerToDescribe {
    case 2, 3, 5, 7, 11, 13, 17, 19:
    description += “ a prime number, and also”
    fallthrough
    case 10:
    description += “ case 10.”
    default:
    description += “ an integer.”
    }
    print(description)// Output:The number 5 is a prime number, and also case 10.
    
Q.What is closure, where can we use it ?
A.They are self contained chunks of code that can be passed around and used in your code.
  Closures in Swift are similar to blocks in C and Objective-C and to lambdas in other programming languages.
  They are almost the same as functions but don’t necessarily have a name.
  No need to declare the type of each parameter, if you do so you don’t need to state the return type of the closure.
  
Q.What are escaping/ nonescaping closures?
A.@nonescaping closures: (default closure)
  When you are passing a closure in function’s arguments, using it before the function’s body gets execute and returns the       compiler back.When the function ends, the passed closure goes out of scope and have no more existence in memory.
  @escaping closures:
  When are passing the closure in function’s arguments, using it after the function’s body gets execute and returns the         compiler back.When the function ends, the scope of the passed closure exist and have existence in memory, till the closure     gets executed. 
  
Q.Mention what are the collection types available in Swift?
A.Arrays — are used to store same type of multiple values in ordered manner.
  Sets — are used to store same type of distinct values in unordered manner.
  Dictionaries — are used to store values with key-value pair association in unordered manner.
  
Q.How base-class is defined in Swift?
A.In Swift the classes are not inherited from the base class and the classes that you define without specifying its super       class, automatically becomes the base-class.

Q.What is de-initializer and how it is written in Swift?
A.A de-initializer is declared immediately before a class instance is de-allocated. You write de-initializer with the deinit     keyword. Use it if you need to do some action or cleanup before deallocating the object.
  For example, if you create a custom class to open a file and write some data to it, you might need to close the file before   the class instance is deallocated.
  De-initializer is written without any parenthesis, and it does not take any parameters.
    
    deinit {
    // perform the deinitialization
    }
    
Q.What is the use of double question marks ‘??’ ?
A.This operator is called as nil coalescing operator.We used it to give a default value when an optional is nil.

    let a: String? = nil
    let b = "nil coalescing operator"
    let result = a ?? b
    print(result) //output:"nil coalescing operator"
    a ?? b unwraps an optional a if it contains a value, or returns a default value b if a is nil.
    The expression a is always of an optional type. The expression b must match the type that is stored inside a.
    
Q.What is the difference between ‘?’ and ‘!’ ?
A.“?” mark
  1. When working with optional values, you can write ‘?’ before operations like methods, properties, and subscript.
  2. If the value before the ‘?’ is nil, everything after the ‘?’ is ignored and the value of the whole expression is nil.
  3. Otherwise, the optional value is unwrapped, and everything after the ‘?’ acts on the unwrapped value.
  4. In both cases, the value of the whole expression is an optional value.
  “!” Mark
  1. Once you’re sure that the optional does contain a value, you can access its underlying value by adding an exclamation 
  mark (!) to the end of the optional’s name.
  2. The exclamation mark effectively says, “I know that this optional definitely has a value; please use it.”
  3. Only use in case when you are absolutely certain that the implicitly unwrapped optional has a value when it is first 
  accessed.
  
Q.What is type aliasing in Swift?
A.A type alias declaration introduces a named alias of an existing type into your program. Type alias declarations are           declared using the keyword typealias.

    typealias name = existing type
    typealias StudentName = String
    let name:StudentName = "Jack"
    
In Swift, you can use typealias for most types. They can be either: 
1.Built-in types (for.eg: String, Int)
2.User-defined types (for.e.g: class, struct, enum)
3.Complex types (for e.g: closures)

Q.What is the difference between functions and methods in Swift?
A.Method — is a function that’s associated with a class, struct, or enum. This goes for both instance and type methods.
  Function — is declared in the global scope and doesn’t belong to any type.
  Functions could be defined outside of classes or inside of classes/structs/enums, while Methods have to be defined inside of   and part of classes/structs/enums.
  
Q.What’s the syntax for external parameters?
A.Extenal Parameter — allow us to name a function parameters to make their purpose more clear.
        
        func power(base a: Int, exponent b: Int) -> Int
        
  Sometimes it’s useful to name each parameter when you call a function, to indicate the purpose of each argument you pass to   the function.If you want users of your function to provide parameter names when they call your function, define an external   parameter name for each parameter, in addition to the local parameter name.
  
Q.Can you override structs and enums in Swift?
A.We Can’t subclass struct / enum, not possible to override. Because, struct is value type and compiler need to know exact size of struct at compile time which is not possible.
  
# Interview Preparation:

1) Objective C
2) Memory management
3) iPhone Development
4) iOS webview and its delegate methods
5) categories, protocols, local and distribution notifications- Design Patterns
6) Push Notifications
7) Threads and Operations queues
8) JSON Parsing
9) Auto layout and its debugging
10) Core data
11) Thread and operation queues
12) NSURL session
13) Blocks
14) iBeacon, Core bluetooth, Augmented reality.

Interview:

Introduction
Resume

Interview usual question:
Properties
ARC
Escaping and Non escaping closure.
Dependency injection and Frameworks
Higher order function
Core data
Jenkins
Jira
Inn app purchase
Ns url session
Autolayout
Unit test case
Bluetooth - normal and classic
Architecture pattern
Stack/heap
Memory management
Oops concept
Rx swift.
Android update + certification
Javascript basics


Career Development :

App development - iOS and Android

