# .NET Interview Questions - Explained

## Q1. What is C#? What Is the difference between C# and .NET?

**Explanation:**
C# is a modern, type-safe, object-oriented programming language developed by Microsoft. It is designed for building secure and robust applications on the .NET platform.  
**.NET** is a comprehensive software development framework that provides a runtime environment, libraries, and tools. C# is a language; .NET is the platform.

**Example:**
```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, World!"); // C# program running on .NET
    }
}
```

---

## Q2. What is OOPS? What are the main concepts of OOPS?

**Explanation:**
OOPS stands for Object-Oriented Programming System. It organizes software using objects and four main pillars:
- **Encapsulation**: Bundles data and methods.
- **Abstraction**: Shows only relevant details.
- **Inheritance**: Enables code reuse via parent-child relationships.
- **Polymorphism**: Allows the same action to behave differently.

**Example:**
```csharp
public abstract class Animal // Abstraction
{
    public abstract void Speak();
}
public class Dog : Animal // Inheritance
{
    public override void Speak() // Polymorphism
    {
        Console.WriteLine("Dog barks");
    }
}
```

---

## Q3. What are the advantages of OOPS?

**Explanation:**
- **Modularity**: Code is organized into objects/classes.
- **Reusability**: Inheritance lets you reuse code.
- **Security**: Encapsulation protects data.
- **Maintainability**: Code is easier to update and extend.

**Example:**
```csharp
public class Vehicle { public void Start() { Console.WriteLine("Vehicle starts"); } }
public class Car : Vehicle { public void Drive() { Console.WriteLine("Car drives"); } }
```

---

## Q4. What are the limitations of OOPS?

**Explanation:**
- Can be overkill for small scripts.
- More complex than procedural programming for simple tasks.
- Sometimes leads to unnecessary abstraction and indirection.

---

## Q5. What are Classes and Objects?

**Explanation:**
A class is a blueprint for creating objects (instances). An object is an instance of a class.

**Example:**
```csharp
public class Person
{
    public string Name { get; set; }
}
Person person = new Person { Name = "Alice" };
```

---

## Q6. What are the types of classes in C#?

**Explanation:**
- **Static Class**: Only contains static members, cannot be instantiated.
- **Abstract Class**: Cannot be instantiated, contains abstract methods.
- **Sealed Class**: Cannot be inherited.
- **Partial Class**: Defined across multiple files.
- **Concrete Class**: Regular instantiable class.

**Example:**
```csharp
public static class Utilities { }
public abstract class Animal { public abstract void Speak(); }
public sealed class Logger { }
public partial class Customer { }
public class Employee { }
```

---

## Q7. Is it possible to prevent object creation of a class in C#?

**Explanation:**
Yes, by making the constructor private, or making the class static or abstract.

**Example:**
```csharp
public class Singleton
{
    private Singleton() { }
    private static Singleton instance;
    public static Singleton Instance => instance ??= new Singleton();
}
```

---

## Q8. What is Property?

**Explanation:**
A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field. Properties use accessors (`get`, `set`).

**Example:**
```csharp
public class Person
{
    private string name;
    public string Name
    {
        get { return name; }
        set { name = value; }
    }
}
```

---

## Q9. What is the difference between Property and Function?

**Explanation:**
- **Property**: Used to get or set data, accessed like a field.
- **Function (Method)**: Performs an operation, called with parentheses and can take parameters.

**Example:**
```csharp
public class Box
{
    public int Height { get; set; } // Property

    public int CalculateVolume(int width, int length) // Function
    {
        return Height * width * length;
    }
}
```

---

## Q10. What are Namespaces?

**Explanation:**
Namespaces organize code and prevent naming conflicts. They provide a way to group related classes.

**Example:**
```csharp
namespace MyApp.Models
{
    public class User { }
}
namespace MyApp.Services
{
    public class UserService { }
}
```

---

## Q11. What is Inheritance? When to use Inheritance?

**Explanation:**
Inheritance allows a class (child) to acquire members (fields, methods, properties) from another class (parent). Use for code reuse and logical hierarchy.

**Example:**
```csharp
public class Animal { public void Eat() { Console.WriteLine("Eating"); } }
public class Dog : Animal { public void Bark() { Console.WriteLine("Bark"); } }
```

---

## Q12. What are the different types of Inheritance?

**Explanation:**
- **Single Inheritance**: One class inherits from another.
- **Multilevel Inheritance**: Class derives from a derived class.
- **Hierarchical Inheritance**: Multiple classes inherit from one.
- **Multiple Inheritance**: Not supported in C#, but can use interfaces.

**Example:**
```csharp
public class Animal { }
public class Dog : Animal { }
public class Cat : Animal { }
```

---

## Q13. Does C# support Multiple Inheritance?

**Explanation:**
No, C# does not support multiple inheritance for classes, but does via interfaces.

**Example:**
```csharp
public interface IRunner { void Run(); }
public interface ISwimmer { void Swim(); }
public class Athlete : IRunner, ISwimmer
{
    public void Run() { }
    public void Swim() { }
}
```

---

## Q14. How to prevent a class from being Inherited?

**Explanation:**
Use the `sealed` keyword.

**Example:**
```csharp
public sealed class FinalClass { }
```

---

## Q15. Are private class members inherited to the derived class?

**Explanation:**
Yes, private members are inherited but not accessible directly. They can be accessed via public/protected methods.

**Example:**
```csharp
public class Base { private int x; }
public class Derived : Base { /* x is inherited, but not accessible */ }
```

---

## Q16. What is Abstraction? How to implement abstraction?

**Explanation:**
Abstraction hides implementation details and exposes only the functionality. Implemented via abstract classes and interfaces.

**Example:**
```csharp
public abstract class Shape
{
    public abstract double Area();
}
public class Circle : Shape
{
    public double Radius { get; set; }
    public override double Area() => Math.PI * Radius * Radius;
}
```

---

## Q17. What is Encapsulation? How to implement encapsulation?

**Explanation:**
Encapsulation bundles data and methods operating on the data within a class and restricts direct access to some of the object's components.

**Example:**
```csharp
public class Account
{
    private double balance;
    public void Deposit(double amount) { balance += amount; }
    public double GetBalance() => balance;
}
```

---

## Q18. What is the difference between Abstraction and Encapsulation?

**Explanation:**
- **Abstraction**: Hides complexity by exposing only relevant parts.
- **Encapsulation**: Protects data by restricting access via access modifiers.

---

## Q19. What is Polymorphism and what are its types? When to use polymorphism?

**Explanation:**
Polymorphism allows objects to be treated as instances of their parent class.  
Types:
- **Compile-time (method overloading)**
- **Run-time (method overriding)**

Use when you want flexible and reusable code.

**Example:**
```csharp
public class Animal { public virtual void Speak() { Console.WriteLine("Animal"); } }
public class Dog : Animal { public override void Speak() { Console.WriteLine("Dog"); } }
Animal a = new Dog();
a.Speak(); // Output: Dog
```

---

## Q20. What is Method Overloading? In how many ways a method can be overloaded?

**Explanation:**
Method overloading is defining multiple methods with the same name but different parameter lists (type, number, or order of parameters).

**Example:**
```csharp
public class MathUtil
{
    public int Sum(int a, int b) => a + b;
    public double Sum(double a, double b) => a + b;
    public int Sum(int a, int b, int c) => a + b + c;
}
```

---

## Q21. When should you use method overloading in real applications?

**Explanation:**
Use method overloading when you want to perform similar operations with different types, numbers, or orders of parameters. It improves readability and reduces code duplication.

**Example:**
```csharp
public void Log(string message) { }
public void Log(string message, Exception ex) { }
```

---

## Q22. If two methods are same except return type, then methods are overloaded or what will happen?

**Explanation:**
Methods cannot be overloaded solely by differing return types. The compiler will throw an error because return type is not considered for overload resolution.

**Example:**
```csharp
// Not allowed:
// int Foo() { ... }
// string Foo() { ... }
```

---

## Q23. What is the difference between Overloading and Overriding?

**Explanation:**
- **Overloading:** Same method name, different parameter list, within the same class.
- **Overriding:** Redefining a base class method in a derived class using the `override` keyword.

**Example:**
```csharp
public class A { public virtual void Print() { } }
public class B : A { public override void Print() { } }
public class C {
    public void Print(int x) { }
    public void Print(string y) { } // Overloading
}
```

---

## Q24. What is the use of Overriding?

**Explanation:**
Overriding allows a derived class to provide a specific implementation for a method defined in its base class. Use it to change or extend base class behavior.

**Example:**
```csharp
public class Animal { public virtual void Speak() { Console.WriteLine("Animal"); } }
public class Cat : Animal { public override void Speak() { Console.WriteLine("Meow"); } }
```

---

## Q25. If a method is marked as virtual, do we must have to "override" it from the child class?

**Explanation:**
No, it’s optional. If not overridden, the child class inherits the base implementation.

**Example:**
```csharp
public class Parent { public virtual void Show() { Console.WriteLine("Parent"); } }
public class Child : Parent { }
```

---

## Q26. What is the difference between Method Overriding and Method Hiding?

**Explanation:**
- **Overriding:** Uses `override` keyword; the base method must be `virtual`, `abstract`, or `override`.
- **Hiding:** Uses `new` keyword; creates a new method with the same name in the derived class.

**Example:**
```csharp
public class Base { public virtual void Print() { } }
public class Derived : Base { public new void Print() { } }
```

---

## Q27. What is the difference between Abstract class and an Interface?

**Explanation:**
- **Abstract class:** Can have implementations, fields, and constructors. Supports single inheritance.
- **Interface:** Can only have signatures (and default implementations in C# 8+). Supports multiple inheritance.

**Example:**
```csharp
public interface IRun { void Run(); }
public abstract class Animal { public abstract void Speak(); }
```

---

## Q28. When to use Interface and when Abstract class in real applications?

**Explanation:**
Use interfaces to define contracts for unrelated classes and for multiple inheritance. Use abstract classes for shared implementation and common base behavior.

**Example:**
```csharp
public interface IDrawable { void Draw(); }
public abstract class Shape { public abstract double Area(); }
```

---

## Q29. Why to create Interfaces in real applications?

**Explanation:**
Interfaces enforce contracts, enable dependency injection, allow for flexible architecture, and support multiple inheritance.

**Example:**
```csharp
public interface ILogger { void Log(string message); }
```

---

## Q30. Can we define body of Interfaces methods? When to define methods in Interfaces?

**Explanation:**
Before C# 8, interface members could not have bodies. In C# 8+, default implementations are allowed.

**Example:**
```csharp
public interface IDefault
{
    void Foo() { Console.WriteLine("Default"); } // C# 8+ only
}
```

---

## Q31. Can you create an instance of an Abstract class or an Interface?

**Explanation:**
No, you must inherit and instantiate the derived/concrete class.

**Example:**
```csharp
// Not allowed: var a = new AbstractClass();
```

---

## Q32. Do Interface can have a Constructor?

**Explanation:**
No, interfaces cannot have constructors.

---

## Q33. Do abstract class have Constructors in C#?

**Explanation:**
Yes, abstract classes can have constructors for base initialization. They are called during object creation of derived classes.

**Example:**
```csharp
public abstract class Base
{
    public Base() { Console.WriteLine("Base constructor"); }
}
public class Derived : Base { }
```

---

## Q34. What is the difference between abstraction and abstract class?

**Explanation:**
- **Abstraction:** Concept for exposing only essential features.
- **Abstract class:** A tool for implementing abstraction.

---

## Q35. Can Abstract class be Sealed or Static in C#?

**Explanation:**
No, abstract classes cannot be sealed (cannot be inherited) or static (cannot be instantiated at all).

---

## Q36. Can you declare abstract methods as private in C#?

**Explanation:**
No, abstract methods must be public or protected. Private abstract methods are not allowed.

---

## Q37. Does Abstract class support multiple Inheritance?

**Explanation:**
No, a class (including abstract) can inherit from only one class, but can implement multiple interfaces.

---

## Q38. What are Access Specifiers?

**Explanation:**
Access specifiers (modifiers) control the accessibility of classes and their members:
- `private`, `protected`, `internal`, `protected internal`, `public`, `private protected`.

**Example:**
```csharp
public class MyClass
{
    private int id;
    protected string name;
    public void Print() { }
}
```

---

## Q39. What is internal access modifier? Show example?

**Explanation:**
`internal` restricts access to the current assembly.

**Example:**
```csharp
internal class InternalClass { }
```

---

## Q40. What is the default access modifier in a class?

**Explanation:**
Class members are `private` by default. Top-level classes are `internal` by default.

**Example:**
```csharp
class MyClass // internal by default
{
    int number; // private by default
}
```
## Q41. What is Boxing and Unboxing?

**Explanation:**
Boxing is the process of converting a value type (like `int`) to an object type. Unboxing is the reverse, extracting the value type from the object. Boxing wraps the value in an object on the heap, unboxing retrieves it.

**Example:**
```csharp
int number = 5;
object boxed = number; // Boxing
int unboxed = (int)boxed; // Unboxing
```

---

## Q42. Which one is explicit: Boxing or Unboxing?

**Explanation:**
Unboxing is explicit (requires a cast), while boxing is implicit.

**Example:**
```csharp
int x = 10;
object obj = x; // Boxing (implicit)
int y = (int)obj; // Unboxing (explicit)
```

---

## Q43. Is Boxing and Unboxing good for performance?

**Explanation:**
No, both involve heap allocation and can be expensive if done repeatedly. Avoid in performance-critical code.

**Example:**
```csharp
for (int i = 0; i < 100000; i++) {
    object o = i; // Boxing in a loop is slow
}
```

---

## Q44. What are the basic string operations in C#?

**Explanation:**
Common operations include concatenation, comparison, searching, substring, splitting, and replacement.

**Example:**
```csharp
string name = "DotNet";
string greeting = "Hello, " + name; // Concatenation
bool hasD = name.Contains("D"); // Search
string upper = name.ToUpper(); // Case conversion
```

---

## Q45. What is the difference between “String” and “StringBuilder”?

**Explanation:**
- `String` is immutable—modifying it creates a new string object each time.
- `StringBuilder` is mutable—can change the contents without allocating a new object each time; efficient for many modifications.

**Example:**
```csharp
string s = "Hello";
s += " World"; // Creates new string

var sb = new StringBuilder("Hello");
sb.Append(" World"); // Modifies the same object
```

---

## Q46. When to use String and when StringBuilder in real applications?

**Explanation:**
Use `String` for few, simple changes. Use `StringBuilder` for many or frequent modifications (e.g., in loops or concatenating large text).

**Example:**
```csharp
// Use StringBuilder in a loop
var sb = new StringBuilder();
for (int i = 0; i < 1000; i++) sb.Append(i);
string result = sb.ToString();
```

---

## Q47. What is String Interpolation in C#?

**Explanation:**
String interpolation allows embedding expressions inside string literals using the `$` symbol.

**Example:**
```csharp
string name = "Alice";
string greeting = $"Hello, {name}!";
```

---

## Q48. What are the Loop types in C#? When to use what in real applications?

**Explanation:**
- `for` loop: Known number of iterations.
- `while` loop: Unknown number, test before.
- `do-while` loop: Unknown number, test after.
- `foreach` loop: Iterates collections.

**Example:**
```csharp
for (int i = 0; i < 5; i++) { }
while (true) { break; }
do { } while(false);
foreach (var ch in "abc") { }
```

---

## Q49. What is the difference between “continue” and “break” statement?

**Explanation:**
- `continue`: Skips to next iteration.
- `break`: Exits the loop entirely.

**Example:**
```csharp
for (int i = 0; i < 5; i++) {
    if (i == 2) continue;
    if (i == 4) break;
    Console.WriteLine(i);
}
```

---

## Q50. What are the alternative ways of writing if-else conditions? When to use what?

**Explanation:**
- Ternary operator for simple conditions.
- Switch statement for multiple choices.
- Pattern matching (C# 7+).

**Example:**
```csharp
// Ternary
int a = 5;
string result = (a > 0) ? "Positive" : "Non-positive";

// Switch
switch (a) {
    case 1: break;
    default: break;
}
```

---

## Q51. How to implement Exception Handling in C#?

**Explanation:**
Use `try`, `catch`, and `finally` blocks to handle exceptions and clean up resources.

**Example:**
```csharp
try {
    int x = int.Parse("not a number");
} catch (FormatException ex) {
    Console.WriteLine("Error: " + ex.Message);
} finally {
    Console.WriteLine("Cleanup code here.");
}
```

---

## Q52. Can we execute multiple Catch blocks?

**Explanation:**
Yes, multiple `catch` blocks can be used to handle different exception types.

**Example:**
```csharp
try { }
catch (FormatException) { }
catch (NullReferenceException) { }
```

---

## Q53. When to use Finally in real applications?

**Explanation:**
Use `finally` to release resources (files, DB connections) regardless of exception occurrence.

**Example:**
```csharp
FileStream fs = null;
try {
    fs = File.Open("test.txt", FileMode.Open);
}
finally {
    if (fs != null) fs.Close();
}
```

---

## Q54. Can we have only “Try” block without “Catch” block in real applications?

**Explanation:**
No, a `try` must be paired with at least one `catch` or a `finally` block.

**Example:**
```csharp
try {
    // code
} finally {
    // cleanup
}
```

---

## Q55. What is the difference between Finally and Finalize?

**Explanation:**
- `finally`: Code block after try/catch that always executes.
- `Finalize`: Destructor method called by the garbage collector before object removal.

**Example:**
```csharp
// Finally
try { } finally { }

// Finalize
class Demo {
    ~Demo() { /* cleanup code */ }
}
```

---

## Q56. What is the difference between “throw ex” and “throw”? Which one to use in real applications?

**Explanation:**
- `throw ex`: Resets the call stack information.
- `throw`: Preserves the original stack trace. Prefer just `throw` when rethrowing.

**Example:**
```csharp
try { }
catch (Exception ex) {
    throw; // Best practice
}
```

---

## Q57. Explain Generics in C#? When and why to use?

**Explanation:**
Generics allow type-safe data structures and methods. Use for reusable code and type safety.

**Example:**
```csharp
List<int> numbers = new List<int>(); // Only ints allowed
public T Identity<T>(T value) { return value; }
```

---

## Q58. What are Collections in C# and what are their types?

**Explanation:**
Collections are classes for storing and managing groups of related objects. Types: Arrays, ArrayList, List<T>, Dictionary<K,V>, Stack, Queue, HashSet, etc.

**Example:**
```csharp
List<string> names = new List<string>();
Dictionary<int, string> dict = new Dictionary<int, string>();
```

---

## Q59. What is the difference between Array and ArrayList (atleast 2)?

**Explanation:**
- Array: Fixed size, type-safe.
- ArrayList: Grows dynamically, stores objects (boxing/unboxing for value types).

**Example:**
```csharp
int[] arr = new int[2];
ArrayList al = new ArrayList();
al.Add(1);
al.Add("abc");
```

---

## Q60. What is the difference between ArrayList and Hashtable?

**Explanation:**
- ArrayList: Stores values indexed by integer position.
- Hashtable: Stores key-value pairs, keys can be any object.

**Example:**
```csharp
ArrayList al = new ArrayList() { 1, 2, 3 };
Hashtable ht = new Hashtable() { { "a", 1 }, { "b", 2 } };
```

---
## Q61. What is the difference between List and Dictionary Collections?

**Explanation:**
- `List<T>` is a collection of items of the same type, accessed via an integer index.
- `Dictionary<TKey, TValue>` stores key-value pairs, allowing fast lookups by key.

**Example:**
```csharp
List<string> names = new List<string> { "Alice", "Bob" };
Dictionary<int, string> idToName = new Dictionary<int, string> { { 1, "Alice" }, { 2, "Bob" } };
```

---

## Q62. What is IEnumerable in C#?

**Explanation:**
`IEnumerable` is an interface for collections that can be iterated using `foreach`. It exposes an enumerator to traverse the collection.

**Example:**
```csharp
IEnumerable<int> numbers = new List<int> { 1, 2, 3 };
foreach (var num in numbers) { Console.WriteLine(num); }
```

---

## Q63. What is the difference between IEnumerable and IEnumerator in C#?

**Explanation:**
- `IEnumerable` provides an enumerator.
- `IEnumerator` provides the ability to iterate through the collection (with `MoveNext`, `Current`, `Reset`).

**Example:**
```csharp
IEnumerable<int> nums = new List<int> { 1, 2 };
IEnumerator<int> enumerator = nums.GetEnumerator();
while (enumerator.MoveNext()) {
    Console.WriteLine(enumerator.Current);
}
```

---

## Q64. What is the difference between IEnumerable and IQueryable in C#?

**Explanation:**
- `IEnumerable` executes queries in-memory (LINQ to objects).
- `IQueryable` can execute queries on remote data sources (like a database), supports query composition and deferred execution.

**Example:**
```csharp
List<int> list = new List<int> { 1, 2, 3 };
IEnumerable<int> en = list.Where(x => x > 1);

// IQueryable is used with Entity Framework for DB queries
```

---

## Q65. What is a Constructor? When to use constructor in real applications?

**Explanation:**
A constructor is a special method invoked when an object is created. Use it to initialize object state.

**Example:**
```csharp
public class Person
{
    public string Name;
    public Person(string name) { Name = name; }
}
Person p = new Person("Bob");
```

---

## Q66. What are the types of constructor?

**Explanation:**
- Default (parameterless)
- Parameterized
- Copy constructor (by convention)
- Static constructor
- Private constructor

**Example:**
```csharp
public class Demo
{
    public Demo() { } // Default
    public Demo(int x) { } // Parameterized
    static Demo() { } // Static
    private Demo(string secret) { } // Private
}
```

---

## Q67. What is Default constructor?

**Explanation:**
A constructor with no parameters. It is provided by default if no other constructors exist.

**Example:**
```csharp
public class Box
{
    public Box() { /* default constructor */ }
}
```

---

## Q68. What is Parameterized constructor?

**Explanation:**
A constructor that takes arguments to initialize fields or properties.

**Example:**
```csharp
public class Point
{
    public int X, Y;
    public Point(int x, int y) { X = x; Y = y; }
}
```

---

## Q69. What is Static constructor? What is the use in real applications?

**Explanation:**
A static constructor initializes static members of a class and is called only once, before any static member is accessed.

**Example:**
```csharp
public class Settings
{
    public static readonly string Config;
    static Settings()
    {
        Config = "Loaded";
    }
}
```

---

## Q70. Can we have parameters or access modifier in static constructor?

**Explanation:**
No, static constructors cannot have parameters or access modifiers; they are always parameterless and private by default.

**Example:**
```csharp
public class Demo
{
    static Demo() { /* OK */ }
    // static Demo(int x) { } // Error
}
```

---

## Q71. What is Copy constructor?

**Explanation:**
A constructor that creates a new object as a copy of an existing object.

**Example:**
```csharp
public class Person
{
    public string Name;
    public Person(Person other) { Name = other.Name; }
}
```

---

## Q72. What is Private constructor? What is the use?

**Explanation:**
A constructor marked `private`. Used to prevent instantiation from outside (Singleton pattern, static classes).

**Example:**
```csharp
public class OnlyStatic
{
    private OnlyStatic() { }
    public static void Print() { }
}
```

---

## Q73. What is Constructor overloading?

**Explanation:**
Defining multiple constructors with different parameter lists.

**Example:**
```csharp
public class Rectangle
{
    public Rectangle() { }
    public Rectangle(int width, int height) { }
}
```

---

## Q74. What is Destructor?

**Explanation:**
A method called when an object is garbage collected. Used for cleanup.

**Example:**
```csharp
public class Demo
{
    ~Demo() { /* cleanup code */ }
}
```

---

## Q75. Can you create object of class with private constructor in C#?

**Explanation:**
No, unless using a static method within the same class (e.g., Singleton pattern).

**Example:**
```csharp
public class Singleton
{
    private Singleton() { }
    public static Singleton Instance { get; } = new Singleton();
}
```

---

## Q76. If base class and child class both have constructor which one will be called first, when derived class object is created?

**Explanation:**
The base class constructor executes first, then the derived class constructor.

**Example:**
```csharp
public class Base { public Base() { Console.WriteLine("Base"); } }
public class Child : Base { public Child() { Console.WriteLine("Child"); } }
```

---

## Q77. What is a Method in C#?

**Explanation:**
A method is a block of code that performs a task, can take parameters, and may return a value.

**Example:**
```csharp
public int Add(int x, int y) { return x + y; }
```

---

## Q78. What is the difference between Pass by Value and Pass by Reference Parameters?

**Explanation:**
- Pass by value (`int x`): Method gets a copy of the argument.
- Pass by reference (`ref int x`): Method operates on the original variable.

**Example:**
```csharp
void Increment(ref int x) { x++; }
int a = 5;
Increment(ref a); // a is now 6
```

---

## Q79. How to return more than one value from a method in C#?

**Explanation:**
Use `out` parameters, tuples, or custom types.

**Example:**
```csharp
void GetValues(out int x, out int y) { x = 1; y = 2; }
// Or
(int, int) GetTuple() => (1, 2);
```

---

## Q80. What is the difference between “out” and “ref” parameters?

**Explanation:**
- `ref`: Must be initialized before passing.
- `out`: Must be assigned in the method before returning; does not need to be initialized beforehand.

**Example:**
```csharp
void SetValue(out int x) { x = 10; }
void Add(ref int x) { x++; }
```

## Q81. What is “params” keyword? When to use params keyword in real applications?

**Explanation:**
The `params` keyword lets you pass a variable number of arguments as an array to a method. Use it when you don't know how many values will be passed.

**Example:**
```csharp
public void PrintNumbers(params int[] numbers)
{
    foreach (var number in numbers)
        Console.WriteLine(number);
}

PrintNumbers(1, 2, 3, 4);
```

---

## Q82. What are optional parameters in a method?

**Explanation:**
Optional parameters allow a method to be called with fewer arguments than defined. They have default values assigned in the method signature.

**Example:**
```csharp
public void Greet(string name = "Guest")
{
    Console.WriteLine($"Hello, {name}");
}
Greet(); // Output: Hello, Guest
```

---

## Q83. What are named parameters in a method?

**Explanation:**
Named parameters allow you to specify arguments by parameter name, regardless of position. This improves code readability.

**Example:**
```csharp
public void Display(string firstName, string lastName)
{
    Console.WriteLine($"{firstName} {lastName}");
}
Display(lastName: "Doe", firstName: "John");
```

---

## Q84. What are Extension Methods in C#? When to use extension methods?

**Explanation:**
Extension methods let you add new methods to existing types without modifying them. Useful for adding utility methods to .NET or third-party types.

**Example:**
```csharp
public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str)
    {
        return string.IsNullOrEmpty(str);
    }
}
string s = null;
bool empty = s.IsNullOrEmpty();
```

---

## Q85. What are Delegates in C#? When to use delegates in real applications?

**Explanation:**
A delegate is a type-safe function pointer, allowing methods to be passed as parameters. Use delegates for event handling and callback methods.

**Example:**
```csharp
public delegate int Operation(int a, int b);
public class Calc
{
    public int Add(int a, int b) => a + b;
}
Calc calc = new Calc();
Operation op = calc.Add;
int result = op(2, 3); // 5
```

---

## Q86. What are Multicast Delegates?

**Explanation:**
A multicast delegate can reference multiple methods. When invoked, all methods are called in order.

**Example:**
```csharp
public delegate void Notify();
Notify notify = () => Console.WriteLine("First");
notify += () => Console.WriteLine("Second");
notify(); // Output: First \n Second
```

---

## Q87. What are Anonymous Delegates in C#?

**Explanation:**
Anonymous delegates are inline delegate implementations (no named method). Used for short, simple callback logic.

**Example:**
```csharp
Action print = delegate { Console.WriteLine("Hello World"); };
print();
```

---

## Q88. What are the differences between Events and Delegates?

**Explanation:**
- Delegates can be called directly, events cannot (outside the declaring class).
- Events are a way to provide notifications, delegates are like function pointers.
- Events restrict delegate invocation to the class that declares them.

**Example:**
```csharp
public delegate void Notify();
public class Publisher
{
    public event Notify OnPublish;
}
```

---

## Q89. What is ‘this’ keyword in C#? When to use it in real applications?

**Explanation:**
`this` refers to the current instance of the class. Use it to resolve naming conflicts, pass the current object, or in extension methods.

**Example:**
```csharp
public class Person
{
    private string name;
    public void SetName(string name)
    {
        this.name = name; // Disambiguates field and parameter
    }
}
```

---

## Q90. What is the purpose of “using” keyword in C#?

**Explanation:**
- To include namespaces.
- To define a scope for objects to be disposed (resource cleanup).

**Example:**
```csharp
using System.IO; // Namespace

using (StreamReader sr = new StreamReader("file.txt"))
{
    Console.WriteLine(sr.ReadToEnd());
}
```

---

## Q91. Can we use Using keyword with other classes apart from DBConnection?

**Explanation:**
Yes, any class implementing `IDisposable` can be used in a `using` statement.

**Example:**
```csharp
using (FileStream fs = new FileStream("a.txt", FileMode.Open)) { }
```

---

## Q92. What is the difference between “is” and “as” operators?

**Explanation:**
- `is`: Checks if an object is a given type (returns bool).
- `as`: Attempts to cast, returns null if it fails (no exception).

**Example:**
```csharp
object obj = "string";
if (obj is string) { }
string s = obj as string;
```

---

## Q93. What is the difference between “Readonly” and “Constant” variables?

**Explanation:**
- `const`: Value is set at compile time, must be initialized at declaration, static by default.
- `readonly`: Value is set at runtime (in constructor), instance or static.

**Example:**
```csharp
public class Demo
{
    public const int Max = 10;
    public readonly int Id;
    public Demo(int id) { Id = id; }
}
```

---

## Q94. What is “Static" class? When to use static class in real application?

**Explanation:**
A static class cannot be instantiated and can only contain static members. Use for utility/helper classes with no instance data.

**Example:**
```csharp
public static class MathHelper
{
    public static int Square(int x) => x * x;
}
```

---

## Q95. What is the difference between “var” and “dynamic” in C#?

**Explanation:**
- `var`: Statically typed (type decided at compile time).
- `dynamic`: Dynamically typed (type decided at runtime).

**Example:**
```csharp
var x = 5; // int
dynamic y = 5; // can change type at runtime
y = "now a string";
```

---

## Q96. What is Enum keyword used for?

**Explanation:**
`enum` defines a set of named integral constants for grouping related values.

**Example:**
```csharp
enum Day { Sun, Mon, Tue, Wed, Thu, Fri, Sat }
Day today = Day.Fri;
```

---

## Q97. Is it possible to inherit Enum in C#?

**Explanation:**
No, enums cannot be inherited.

---

## Q98. What is the use of Yield keyword in C#?

**Explanation:**
`yield` simplifies iterator implementation by pausing and resuming method execution.

**Example:**
```csharp
public IEnumerable<int> GetNumbers()
{
    yield return 1;
    yield return 2;
}
```

---

## Q99. What is LINQ? When to use LINQ in real applications?

**Explanation:**
LINQ (Language Integrated Query) allows querying collections in C# with SQL-like syntax. Use for querying/filtering/manipulating data in memory or from data sources.

**Example:**
```csharp
var evens = from n in Enumerable.Range(1, 10) where n % 2 == 0 select n;
```

---

## Q100. What are the advantages & disadvantages of LINQ?

**Explanation:**
- **Advantages:** Readable, type-safe queries; integrates with C#, reusable logic.
- **Disadvantages:** Sometimes less efficient than raw queries; debugging can be harder; not all LINQ providers support all query features.

**Example:**
```csharp
List<int> nums = new List<int> { 1, 2, 3, 4 };
var even = nums.Where(n => n % 2 == 0).ToList();
```
## Q101. What is Lambda Expressions? What is the use in real applications?

**Explanation:**
A lambda expression is an anonymous function that can contain expressions and statements. It is used to create delegates or expression tree types. Lambdas are often used in LINQ, event handling, and functional-style programming for concise syntax.

**Example:**
```csharp
Func<int, int, int> add = (a, b) => a + b;
int result = add(2, 3); // result = 5

var squares = Enumerable.Range(1,5).Select(x => x * x); // LINQ with lambda
```

---

## Q102. What is the difference between First and FirstOrDefault methods in LINQ?

**Explanation:**
- `First` throws an exception if no element is found.
- `FirstOrDefault` returns the default value for the type (e.g., `null` for reference types, `0` for value types) if no element is found.

**Example:**
```csharp
var list = new List<int>();
// int n = list.First(); // Throws InvalidOperationException
int n = list.FirstOrDefault(); // Returns 0
```

---

## Q103. What are the important components of .NET framework?

**Explanation:**
- **CLR (Common Language Runtime):** Manages execution, memory, security, etc.
- **FCL (Framework Class Library):** Predefined classes and APIs.
- **CTS (Common Type System):** Defines data types and programming constructs.
- **CLS (Common Language Specification):** Language interoperability.
- **Assemblies:** Compiled code units (DLL, EXE).

---

## Q104. What is an Assembly? What are the different types of assembly?

**Explanation:**
An assembly is a compiled code library used by .NET applications.  
- **Private Assembly:** Used by a single application.
- **Shared Assembly:** Can be used by multiple applications (often in GAC).
- **Satellite Assembly:** Contains resources for localization.

**Example:**
- `MyApp.dll` (private)
- `System.Data.dll` (shared)

---

## Q105. What is GAC?

**Explanation:**
GAC (Global Assembly Cache) is a machine-wide store for shared assemblies. Assemblies in GAC can be used by multiple applications and must have a strong name.

---

## Q106. What is Reflection?

**Explanation:**
Reflection enables inspection of metadata, type information, and runtime behavior of assemblies, types, and members. Used for dynamic type discovery, late binding, and frameworks like serialization.

**Example:**
```csharp
Type t = typeof(string);
var methods = t.GetMethods();
```

---

## Q107. What are Serialization and Deserialization?

**Explanation:**
- **Serialization:** Converting an object into a format (e.g., XML, JSON, binary) for storage or transmission.
- **Deserialization:** Reconstructing object from that format.

**Example:**
```csharp
using System.Text.Json;
var json = JsonSerializer.Serialize(new { Name = "Alice" });
var obj = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
```

---

## Q108. What is meant by Globalization and Localization?

**Explanation:**
- **Globalization:** Designing applications to support multiple cultures (languages, formats, etc.).
- **Localization:** Customizing application for a specific culture/region.

**Example:**
```csharp
using System.Globalization;
var ci = new CultureInfo("fr-FR");
double value = 12345.67;
Console.WriteLine(value.ToString("N", ci)); // "12 345,67"
```

---

## Q109. What are Window Services?

**Explanation:**
Windows Services are long-running executable applications that run in the background and can start automatically on system boot. Used for background tasks (monitoring, scheduling, etc.).

---

## Q110. What is Garbage Collection(GC)?

**Explanation:**
GC is the automatic memory management feature in .NET. It reclaims memory occupied by objects that are no longer reachable, thus preventing memory leaks.

**Example:**
```csharp
GC.Collect(); // Forces a garbage collection (not recommended in general)
```

---

## Q111. What are Generations in garbage collection?

**Explanation:**
.NET GC divides managed heap into three generations:
- **Gen 0:** Short-lived objects.
- **Gen 1:** Surviving Gen 0 objects.
- **Gen 2:** Long-lived objects.
This improves performance by collecting short-lived objects more frequently.

---

## Q112. What is the difference between “Dispose” and “Finalize”?

**Explanation:**
- `Dispose()`: Explicitly called to release unmanaged resources.
- `Finalize()`: (Destructor) Called by GC before object is reclaimed; can be overridden using `~ClassName()`.

**Example:**
```csharp
public void Dispose() { /* free resources */ }
~MyClass() { /* cleanup before GC */ }
```

---

## Q113. What is the difference between “Finalize” and “Finally” methods?

**Explanation:**
- `Finalize`: Destructor, called by GC to clean up resources before object destruction.
- `finally`: Code block in exception handling, always executes after try/catch.

**Example:**
```csharp
try { } finally { /* always runs */ }
~Demo() { /* runs when GC collects */ }
```

---

## Q114. Can we force Garbage Collector to run?

**Explanation:**
Yes, by calling `GC.Collect()`, but it is discouraged in production as GC is optimized to handle memory efficiently.

**Example:**
```csharp
GC.Collect();
```

---

## Q115. What is the difference between Process and Thread?

**Explanation:**
- **Process:** An independent, self-contained unit of execution with its own memory space.
- **Thread:** A lightweight unit of execution within a process; threads in the same process share memory.

**Example:**
```csharp
using System.Threading;
Thread t = new Thread(() => Console.WriteLine("Running in thread")); t.Start();
```

---

## Q116. Explain Multithreading?

**Explanation:**
Multithreading allows concurrent execution of two or more threads, improving application responsiveness and performance, especially on multi-core CPUs.

**Example:**
```csharp
Thread t1 = new Thread(() => Console.WriteLine("Thread 1"));
Thread t2 = new Thread(() => Console.WriteLine("Thread 2"));
t1.Start(); t2.Start();
```

---

## Q117. What is the difference between synchronous and asynchronous programming? What is the role of Task?

**Explanation:**
- **Synchronous:** Code runs sequentially, blocking until completion.
- **Asynchronous:** Code can run without blocking; allows other work while waiting.
- `Task` represents an asynchronous operation in .NET.

**Example:**
```csharp
public async Task<int> CalculateAsync() { await Task.Delay(1000); return 42; }
```

---

## Q118. What is the difference between Threads and Tasks? What are the advantages of Tasks over Threads?

**Explanation:**
- **Thread:** OS-level, manual scheduling, more overhead.
- **Task:** Higher-level abstraction, managed by .NET Task Scheduler, supports cancellation, continuation, and exception handling.

**Example:**
```csharp
Task.Run(() => Console.WriteLine("Task")); // Preferred for async operations
```

---

## Q119. What is the role of Async and Await?

**Explanation:**
`async` enables a method to be asynchronous; `await` pauses execution until the awaited asynchronous operation completes.

**Example:**
```csharp
public async Task<int> GetResultAsync()
{
    await Task.Delay(1000);
    return 7;
}
```

---

## Q120. What is the difference between DBMS and RDBMS?

**Explanation:**
- **DBMS** (Database Management System): Stores data as files or collections (no relationships).
- **RDBMS** (Relational DBMS): Stores data in tables with relationships (primary/foreign keys), supports SQL and constraints.
Examples: SQL Server, Oracle, MySQL.

---
## Q121. What is a Constraint in SQL? What are the types of constraints?

**Explanation:**
A constraint is a rule applied to a column or table to enforce data integrity. Types include:
- **Primary Key:** Uniquely identifies each row.
- **Foreign Key:** Ensures referential integrity between tables.
- **Unique:** Ensures all values in a column are unique.
- **Check:** Ensures values meet a specific condition.
- **Default:** Sets a default value if none is provided.
- **Not Null:** Disallows null values in a column.

**Example:**
```sql
CREATE TABLE Employee (
    EmpID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Salary INT CHECK (Salary > 0),
    ManagerID INT FOREIGN KEY REFERENCES Employee(EmpID)
);
```

---

## Q122. What is the difference between Primary key and Unique key?

**Explanation:**
- **Primary Key:** Uniquely identifies each row, cannot have NULL values, only one per table.
- **Unique Key:** Ensures all values are unique, can have NULLs, multiple unique keys allowed per table.

---

## Q123. What are Triggers and types of triggers?

**Explanation:**
A trigger is a special kind of stored procedure that automatically executes when an event occurs in the database (INSERT, UPDATE, DELETE).
Types:
- **AFTER Trigger:** Executes after the operation.
- **INSTEAD OF Trigger:** Executes instead of the operation.
- **BEFORE Trigger:** (Not supported in SQL Server, but is in some other DBMS.)

**Example:**
```sql
CREATE TRIGGER trgAfterInsert
ON Employee
AFTER INSERT
AS
BEGIN
    PRINT 'Inserted new employee'
END
```

---

## Q124. What is a View?

**Explanation:**
A view is a virtual table based on the result set of a SQL query. It does not store data itself.

**Example:**
```sql
CREATE VIEW ActiveEmployees AS
SELECT * FROM Employee WHERE IsActive = 1;
```

---

## Q125. What is the difference between Having clause and Where clause?

**Explanation:**
- **WHERE:** Filters rows before grouping.
- **HAVING:** Filters groups after `GROUP BY`.

**Example:**
```sql
SELECT Dept, COUNT(*) FROM Employee WHERE Salary > 5000 GROUP BY Dept HAVING COUNT(*) > 3;
```

---

## Q126. What is Sub query or Nested query or Inner query in SQL?

**Explanation:**
A subquery is a query inside another query, often used to filter results or calculate values.

**Example:**
```sql
SELECT Name FROM Employee WHERE DeptID IN (SELECT DeptID FROM Department WHERE Location = 'NY');
```

---

## Q127. What is Auto Increment/ Identity column in SQL Server?

**Explanation:**
An identity column automatically generates a unique value for each new row.

**Example:**
```sql
CREATE TABLE Employee (
    EmpID INT IDENTITY(1,1) PRIMARY KEY,
    Name VARCHAR(100)
);
```

---

## Q128. What are Joins in SQL?

**Explanation:**
Joins combine rows from two or more tables based on a related column.

---

## Q129. What are the types of Joins in SQL Server?

**Explanation:**
- **INNER JOIN:** Returns matching rows.
- **LEFT (OUTER) JOIN:** All left rows + matched right rows.
- **RIGHT (OUTER) JOIN:** All right rows + matched left rows.
- **FULL (OUTER) JOIN:** All rows when there is a match in one of the tables.
- **CROSS JOIN:** Cartesian product.

**Example:**
```sql
SELECT * FROM A INNER JOIN B ON A.Id = B.AId;
```

---

## Q130. What is Self-Join?

**Explanation:**
A self-join joins a table to itself as if it were two tables, using aliases.

**Example:**
```sql
SELECT e1.Name, e2.Name AS Manager
FROM Employee e1
LEFT JOIN Employee e2 ON e1.ManagerID = e2.EmpID;
```

---

## Q131. What are Indexes in SQL Server?

**Explanation:**
Indexes speed up data retrieval but may slow down insert/update/delete. They are similar to the index in a book.

---

## Q132. What is Clustered index?

**Explanation:**
A clustered index determines the physical order of data in a table. Each table can have only one clustered index.

**Example:**
```sql
CREATE CLUSTERED INDEX idx_EmpID ON Employee(EmpID);
```

---

## Q133. What is Non-Clustered index?

**Explanation:**
A non-clustered index is a separate structure from the data rows. A table can have multiple non-clustered indexes.

**Example:**
```sql
CREATE NONCLUSTERED INDEX idx_Name ON Employee(Name);
```

---

## Q134. What is the difference between Clustered and Non-Clustered index?

**Explanation:**
- **Clustered:** Sorts and stores data rows; one per table.
- **Non-Clustered:** Separate structure, holds pointers to data; many per table.

---

## Q135. How to create Clustered and Non-Clustered index in a table?

**Example:**
```sql
-- Clustered
CREATE CLUSTERED INDEX idx_EmpID ON Employee(EmpID);

-- Non-Clustered
CREATE NONCLUSTERED INDEX idx_Name ON Employee(Name);
```

---

## Q136. In which column you will apply the indexing to optimize this query?

**Explanation:**
Apply indexing to columns used in WHERE, JOIN, or ORDER BY clauses to improve query performance.

**Example:**
```sql
SELECT * FROM Employee WHERE Email = 'a@b.com';
-- Index on Email column is beneficial
```

---

## Q137. What is the difference between Stored Procedure and Functions?

**Explanation:**
- **Stored Procedure:** Can return multiple values, execute SQL statements, use output parameters, support transactions.
- **Function:** Returns a single value or table, can be used in SELECT, cannot use output parameters or transactions.

---

## Q138. How to optimize a Stored Procedure or SQL Query?

**Explanation:**
- Use indexes, avoid SELECT *, use proper joins, avoid cursors, use appropriate WHERE clauses, update statistics, and use SET NOCOUNT ON.

---

## Q139. What is a Cursor? Why to avoid them?

**Explanation:**
A cursor allows row-by-row processing of result sets. They are slow and use more resources, so set-based operations are preferred.

---

## Q140. What is the difference between scope_identity and @@identity?

**Explanation:**
- **@@IDENTITY:** Returns last identity value generated in current session, any table/trigger.
- **SCOPE_IDENTITY():** Returns last identity value in current scope, recommended to avoid unexpected values.

**Example:**
```sql
INSERT INTO Employee (Name) VALUES ('Bob');
SELECT SCOPE_IDENTITY();
```

---
## Q141. What is CTE in SQL Server?

**Explanation:**
A CTE (Common Table Expression) is a temporary named result set that you can reference within a SELECT, INSERT, UPDATE, or DELETE statement. It improves readability and enables recursive queries.

**Example:**
```sql
WITH EmployeeCTE AS (
    SELECT EmpID, Name, ManagerID FROM Employee WHERE ManagerID IS NULL
    UNION ALL
    SELECT e.EmpID, e.Name, e.ManagerID
    FROM Employee e
    INNER JOIN EmployeeCTE cte ON e.ManagerID = cte.EmpID
)
SELECT * FROM EmployeeCTE;
```

---

## Q142. What is the difference between Delete, Truncate and Drop commands?

**Explanation:**
- **DELETE:** Removes rows based on condition, can be rolled back (transactional), keeps table structure.
- **TRUNCATE:** Removes all rows, cannot use WHERE, resets identity, cannot be rolled back in some DBMS.
- **DROP:** Deletes entire table structure and data, cannot be rolled back.

**Example:**
```sql
DELETE FROM Employee WHERE EmpID = 1;
TRUNCATE TABLE Employee;
DROP TABLE Employee;
```

---

## Q143. How to get the Nth highest salary of an employee?

**Explanation:**
Use the `ROW_NUMBER()` or `DENSE_RANK()` window function for this purpose.

**Example:**
```sql
SELECT TOP 1 Salary
FROM (
    SELECT Salary, DENSE_RANK() OVER (ORDER BY Salary DESC) AS Rank
    FROM Employee
) AS Temp
WHERE Rank = N;
-- Replace N with desired rank (e.g., 2 for second highest)
```

---

## Q144. What are ACID properties?

**Explanation:**
- **Atomicity:** All operations in a transaction are completed or none are.
- **Consistency:** The database remains in a valid state before and after the transaction.
- **Isolation:** Transactions do not affect each other.
- **Durability:** Once committed, changes persist even after a system failure.

---

## Q145. What are Magic Tables in SQL Server?

**Explanation:**
Magic tables are the special tables `INSERTED` and `DELETED` used internally by triggers to hold the rows affected by DML operations.

**Example:**
```sql
CREATE TRIGGER trgAfterInsert
ON Employee
AFTER INSERT
AS
BEGIN
    SELECT * FROM INSERTED
END
```

---

## Q146. What is MVC? Explain MVC Life cycle.

**Explanation:**
MVC (Model-View-Controller) is a design pattern for separating concerns:
- **Model:** Data and business logic.
- **View:** UI.
- **Controller:** Handles user input and interactions.

**MVC Life Cycle:** Request → Routing → Controller Initialization → Action Execution → Result Execution → View Rendering → Response.

---

## Q147. What are the advantages of MVC over Web Forms?

**Explanation:**
- Separation of concerns.
- Easier testing and maintainability.
- Fine-grained control over HTML, CSS, and JavaScript.
- Better support for TDD and RESTful applications.

---

## Q148. What are the different return types of a controller Action method?

**Explanation:**
- `ViewResult`, `PartialViewResult`, `JsonResult`, `RedirectResult`, `ContentResult`, `FileResult`, `EmptyResult`, `ActionResult`, `Task<ActionResult>`, etc.

**Example:**
```csharp
public ActionResult Index() { return View(); }
public JsonResult Data() { return Json(new { Name = "Alice" }); }
```

---

## Q149. What are Filters and their types in MVC?

**Explanation:**
Filters are attributes for executing code before or after controller actions:
- **Authorization Filter**
- **Action Filter**
- **Result Filter**
- **Exception Filter**

**Example:**
```csharp
[Authorize]
public ActionResult Index() { ... }
```

---

## Q150. What is Authentication and Authorization in ASP.NET MVC?

**Explanation:**
- **Authentication:** Verifies user identity.
- **Authorization:** Checks if authenticated user has permission for an action/resource.

---

## Q151. What are the types of Authentication in ASP.NET MVC?

**Explanation:**
- Forms Authentication
- Windows Authentication
- OAuth/OpenID Connect
- Token-based Authentication (JWT, etc.)
- Custom Authentication

---

## Q152. What is Output Caching in MVC? How to implement it?

**Explanation:**
Output caching stores the output of a controller action for reuse, reducing server processing time.

**Example:**
```csharp
[OutputCache(Duration = 60, VaryByParam = "none")]
public ActionResult Index() { ... }
```

---

## Q153. What is Routing in MVC?

**Explanation:**
Routing maps incoming URLs to controller actions. It defines how URLs are interpreted by the application.

**Example:**
```csharp
routes.MapRoute(
    name: "Default",
    url: "{controller}/{action}/{id}",
    defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
);
```

---

## Q154. Explain Attribute Based Routing in MVC?

**Explanation:**
Attribute routing allows defining routes directly on controller actions using attributes.

**Example:**
```csharp
[Route("products/{id}")]
public ActionResult Details(int id) { ... }
```

---

## Q155. What is the difference between ViewData, ViewBag & TempData?

**Explanation:**
- **ViewData:** Dictionary object, used to pass data from controller to view (per request).
- **ViewBag:** Dynamic property on ViewData, also per request.
- **TempData:** Dictionary for passing data between actions (persists until read).

---

## Q156. How can we pass the data from controller to view in MVC?

**Explanation:**
- Using model objects.
- Using ViewData, ViewBag, or TempData.

**Example:**
```csharp
ViewData["Message"] = "Hello";
ViewBag.Message = "Hello";
return View(model);
```

---

## Q157. What is Partial View?

**Explanation:**
A partial view is a reusable component or view fragment that can be rendered inside another view.

**Example:**
```csharp
@Html.Partial("_LoginPartial")
```

---

## Q158. What are Areas in MVC?

**Explanation:**
Areas allow dividing a large MVC application into smaller functional sections, each with its own controllers, views, and models.

---

## Q159. How Validation works in MVC? What is Data Annotation?

**Explanation:**
Validation is achieved through model validation and data annotation attributes (`[Required]`, `[StringLength]`, etc.) on model properties.

**Example:**
```csharp
public class User
{
    [Required]
    public string Name { get; set; }
}
```

---

## Q160. Explain the concept of MVC Scaffolding?

**Explanation:**
Scaffolding auto-generates code for CRUD operations based on the model, reducing development time.

---
## Q161. What is Razor View Engine in MVC?

**Explanation:**
Razor is a markup syntax used for embedding server-based code (C#) into web pages. It's the default view engine for ASP.NET MVC and provides a clean, easy-to-read way to generate dynamic HTML.

**Example:**
```csharp
@model MyApp.Models.User
<h1>Hello, @Model.Name!</h1>
```

---

## Q162. What is Layout in Razor View Engine?

**Explanation:**
A layout is a shared template for consistent page structure (like a master page). It defines common UI (header, footer, etc.) for multiple views.

**Example:**
```csharp
// _Layout.cshtml
<html>
  <body>
    @RenderBody()
  </body>
</html>
```

---

## Q163. How to use Partial Views in MVC?

**Explanation:**
Partial views are reusable view fragments rendered inside other views.

**Example:**
```csharp
@Html.Partial("_LoginPartial")
```

---

## Q164. What is HTML Helper in MVC?

**Explanation:**
HTML Helpers are methods that generate HTML elements in Razor views, making it easier to render form elements, links, etc.

**Example:**
```csharp
@Html.TextBoxFor(model => model.Name)
@Html.ActionLink("Home", "Index")
```

---

## Q165. What is strongly typed View in MVC?

**Explanation:**
A strongly typed view is bound to a specific model class, enabling IntelliSense and compile-time checking.

**Example:**
```csharp
@model MyApp.Models.User
<p>@Model.Name</p>
```

---

## Q166. What are Bundling and Minification in MVC?

**Explanation:**
Bundling combines multiple files (CSS/JS) into one, Minification removes whitespace/comments. Together, they reduce HTTP requests and file sizes, improving performance.

**Example:**
```csharp
// In BundleConfig.cs
bundles.Add(new ScriptBundle("~/bundles/jquery").Include("~/Scripts/jquery-{version}.js"));
```

---

## Q167. What is the difference between TempData, ViewData, and ViewBag?

**Explanation:**
- `ViewBag` and `ViewData`: Used to pass data from controller to view; valid only for the current request.
- `TempData`: Used to pass data between actions; persists until read.

---

## Q168. What is Model Binding in MVC?

**Explanation:**
Model binding automates mapping of HTTP request data (form, query string, etc.) to action parameters or model properties.

**Example:**
```csharp
public ActionResult Edit(User user) { /* user properties are automatically bound */ }
```

---

## Q169. What is Data Annotation in MVC?

**Explanation:**
Data Annotations are attributes used to validate model properties (e.g., `[Required]`, `[StringLength]`, `[Range]`).

**Example:**
```csharp
public class Product
{
    [Required]
    public string Name { get; set; }
}
```

---

## Q170. How to perform client-side validation in MVC?

**Explanation:**
Enable unobtrusive JavaScript and use Data Annotations. MVC emits the necessary validation attributes, and libraries like jQuery Validate perform client-side checks.

**Example:**
```csharp
@model Product
@using (Html.BeginForm()) {
    @Html.EditorFor(m => m.Name)
    @Html.ValidationMessageFor(m => m.Name)
}
```

---

## Q171. What is AntiForgeryToken in MVC?

**Explanation:**
AntiForgeryToken prevents CSRF (Cross-Site Request Forgery) attacks by generating a unique token for forms and validating it on submission.

**Example:**
```csharp
@Html.AntiForgeryToken()
[ValidateAntiForgeryToken]
public ActionResult Save(Model model) { ... }
```

---

## Q172. What is Dependency Injection (DI)? How is it implemented in .NET?

**Explanation:**
DI is a design pattern where dependencies are provided to a class rather than created inside it. .NET Core has built-in DI via constructor injection and service configuration.

**Example:**
```csharp
public class HomeController
{
    private readonly IService _service;
    public HomeController(IService service) { _service = service; }
}
```

---

## Q173. What is Inversion of Control (IoC)?

**Explanation:**
IoC is a design principle where control of object creation and dependency management is shifted from the class itself to an external entity (IoC container).

---

## Q174. What are Action Filters in MVC?

**Explanation:**
Action Filters are attributes that execute code before or after controller actions (e.g., logging, authorization, error handling).

**Example:**
```csharp
public class LogActionFilter : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext filterContext)
    {
        // Logging logic here
    }
}
```

---

## Q175. How to handle errors in MVC?

**Explanation:**
- Use `try-catch` in actions.
- Use custom error pages (`web.config`).
- Implement `HandleErrorAttribute` or custom exception filters.

**Example:**
```csharp
[HandleError]
public ActionResult Index() { throw new Exception(); }
```

---

## Q176. What is Web API?

**Explanation:**
ASP.NET Web API is a framework for building HTTP-based RESTful services, returning data (JSON/XML) for clients (web, mobile, etc.).

---

## Q177. What is the difference between MVC and Web API?

**Explanation:**
- MVC is mainly for returning views (HTML UI).
- Web API is for returning data (JSON/XML) to clients.

---

## Q178. What is RESTful service?

**Explanation:**
A RESTful service follows REST principles: stateless, client-server, uses standard HTTP methods (GET, POST, PUT, DELETE), and resource-based URLs.

---

## Q179. What is Attribute Routing in Web API?

**Explanation:**
Attribute routing lets you define routes directly on controller actions with attributes.

**Example:**
```csharp
[Route("api/products/{id}")]
public IHttpActionResult GetProduct(int id) { ... }
```

---

## Q180. How to secure Web API?

**Explanation:**
- Use HTTPS.
- Implement authentication (JWT, OAuth).
- Authorize requests with roles/claims.
- Validate input data.

**Example:**
```csharp
[Authorize(Roles = "Admin")]
public IHttpActionResult GetSecret() { ... }
```

---
## Q181. What is the difference between IHttpActionResult and HttpResponseMessage in Web API?

**Explanation:**
- `IHttpActionResult` is a higher-level, more testable abstraction for HTTP responses (introduced in Web API 2).
- `HttpResponseMessage` is a lower-level class representing the HTTP response.

**Example:**
```csharp
public IHttpActionResult Get() => Ok("Success");
public HttpResponseMessage GetMsg() => Request.CreateResponse(HttpStatusCode.OK, "Success");
```

---

## Q182. What is CORS? How to enable CORS in Web API?

**Explanation:**
CORS (Cross-Origin Resource Sharing) allows web applications from one domain to access resources from another. In Web API, enable CORS globally or per controller/action using the `[EnableCors]` attribute or middleware.

**Example:**
```csharp
[EnableCors(origins: "*", headers: "*", methods: "*")]
public class MyApiController : ApiController { }
```

---

## Q183. What is Swagger? Why is it used?

**Explanation:**
Swagger (now part of OpenAPI) is a framework for documenting and testing RESTful APIs. It generates interactive API documentation and client SDKs.

---

## Q184. How to version Web API?

**Explanation:**
- URI versioning: `/api/v1/products`
- Query string/version header
- Namespace-based versioning
- Use libraries like Microsoft.AspNet.WebApi.Versioning

---

## Q185. What is OWIN?

**Explanation:**
OWIN (Open Web Interface for .NET) defines a standard interface between .NET web servers and web applications, decoupling server and application code.

---

## Q186. What is Katana?

**Explanation:**
Katana is Microsoft's implementation of the OWIN specification, providing components for building OWIN-based applications.

---

## Q187. What is Middleware in ASP.NET Core?

**Explanation:**
Middleware are components in the request pipeline that process HTTP requests and responses, such as authentication, logging, or error handling.

**Example:**
```csharp
app.Use(async (context, next) =>
{
    // Custom logic before
    await next.Invoke();
    // Custom logic after
});
```

---

## Q188. What is Dependency Injection in ASP.NET Core and why is it important?

**Explanation:**
Dependency Injection (DI) in ASP.NET Core allows services to be injected into classes, improving modularity and testability. It's built-in via the IServiceCollection and constructor injection.

---

## Q189. What are the service lifetimes in ASP.NET Core DI?

**Explanation:**
- **Transient:** New instance every time requested.
- **Scoped:** One instance per request.
- **Singleton:** One instance for the application's lifetime.

**Example:**
```csharp
services.AddTransient<IMyService, MyService>();
services.AddScoped<IMyService, MyService>();
services.AddSingleton<IMyService, MyService>();
```

---

## Q190. What is Entity Framework?

**Explanation:**
Entity Framework (EF) is an ORM (Object-Relational Mapper) for .NET. It lets you work with databases using .NET objects, supporting LINQ queries, change tracking, and migrations.

---

## Q191. What is Code First, Database First, and Model First in Entity Framework?

**Explanation:**
- **Code First:** Define models in code; EF creates/migrates DB.
- **Database First:** Start from existing DB; generate models.
- **Model First:** Create a model visually; generate DB and code.

---

## Q192. What are migrations in Entity Framework?

**Explanation:**
Migrations are a way to incrementally update the database schema when your data model changes, using commands like `Add-Migration` and `Update-Database`.

---

## Q193. What is DbContext in EF?

**Explanation:**
`DbContext` is the primary class for interacting with the database using EF. It manages entity objects, queries, and saves changes.

**Example:**
```csharp
public class MyDbContext : DbContext
{
    public DbSet<User> Users { get; set; }
}
```

---

## Q194. What is a DbSet in EF?

**Explanation:**
A `DbSet` represents a collection of all entities in the context, or that can be queried from the database.

---

## Q195. How to query data using LINQ in EF?

**Example:**
```csharp
var users = context.Users.Where(u => u.IsActive).ToList();
```

---

## Q196. What is Lazy Loading, Eager Loading, and Explicit Loading in EF?

**Explanation:**
- **Lazy Loading:** Related data is loaded automatically when accessed.
- **Eager Loading:** Related data is loaded up front using `.Include()`.
- **Explicit Loading:** Load related data on demand using `.Load()`.

**Example:**
```csharp
var user = context.Users.Include(u => u.Orders).First();
```

---

## Q197. What is the difference between First, FirstOrDefault, Single, and SingleOrDefault in LINQ?

**Explanation:**
- `First`: Returns first element, or throws if none.
- `FirstOrDefault`: Returns first or default (null/0).
- `Single`: Returns only element, or throws if not exactly one.
- `SingleOrDefault`: Returns only element or default, throws if more than one.

---

## Q198. How to handle concurrency in EF?

**Explanation:**
Use concurrency tokens (like `RowVersion` column), handle `DbUpdateConcurrencyException`, and resolve conflicts as needed.

---

## Q199. How to execute raw SQL queries in EF?

**Example:**
```csharp
var products = context.Products.FromSqlRaw("SELECT * FROM Products").ToList();
```

---

## Q200. What is Dapper?

**Explanation:**
Dapper is a lightweight, high-performance micro ORM for .NET, providing fast database access using extension methods for IDbConnection.

**Example:**
```csharp
using (var conn = new SqlConnection(connStr))
{
    var users = conn.Query<User>("SELECT * FROM Users").ToList();
}
```

---
## Q201. What is Microservices architecture?

**Explanation:**
Microservices architecture is an approach where an application is structured as a collection of loosely coupled, independently deployable services. Each service focuses on a specific business capability and communicates with others via APIs.

---

## Q202. What are the benefits of Microservices?

**Explanation:**
- Independent development and deployment
- Scalability and flexibility
- Technology diversity
- Improved fault isolation
- Easier maintenance and evolution

---

## Q203. What are some challenges in Microservices?

**Explanation:**
- Complex distributed systems
- Data consistency and transactions
- Service coordination
- Deployment and monitoring
- Network latency and security

---

## Q204. What is API Gateway?

**Explanation:**
An API Gateway is a server that acts as a single entry point for a set of microservices. It handles routing, authentication, rate limiting, and response aggregation.

---

## Q205. What is Service Discovery in Microservices?

**Explanation:**
Service Discovery is the process by which microservices find and communicate with each other dynamically, typically through a service registry (e.g., Consul, Eureka).

---

## Q206. What is Docker? How is it used with .NET?

**Explanation:**
Docker is a platform for packaging, distributing, and running applications in containers. .NET applications can be containerized for consistent deployment and isolation.

**Example:**
```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:6.0
COPY . /app
WORKDIR /app
ENTRYPOINT ["dotnet", "MyApp.dll"]
```

---

## Q207. What is Kubernetes?

**Explanation:**
Kubernetes is a container orchestration system for automating deployment, scaling, and management of containerized applications.

---

## Q208. What is the difference between Monolithic and Microservices architectures?

**Explanation:**
- **Monolithic:** Single, unified codebase, easier to develop at first, harder to scale and maintain as it grows.
- **Microservices:** Multiple independent services, easier to scale and modify, but more complex to manage.

---

## Q209. What is SignalR?

**Explanation:**
SignalR is a library for ASP.NET that enables real-time web functionality, allowing server code to push updates to connected clients (e.g., chat apps, live dashboards).

---

## Q210. What is gRPC?

**Explanation:**
gRPC is a high-performance, open-source RPC framework that uses Protocol Buffers for serialization and supports cross-language communication. It is commonly used for efficient service-to-service communication.

---

## Q211. What is Blazor?

**Explanation:**
Blazor is a framework for building interactive web UIs using C# instead of JavaScript. It runs in the browser via WebAssembly or on the server.

---

## Q212. What is .NET MAUI?

**Explanation:**
.NET MAUI (Multi-platform App UI) is a cross-platform framework for building native mobile and desktop apps using C# and .NET.

---

## Q213. What is Minimal API in .NET?

**Explanation:**
Minimal API is a lightweight approach introduced in .NET 6 for building small, fast HTTP APIs with minimal configuration and boilerplate.

**Example:**
```csharp
var app = WebApplication.CreateBuilder().Build();
app.MapGet("/", () => "Hello World!");
app.Run();
```

---

## Q214. What is Health Check in ASP.NET Core?

**Explanation:**
Health Checks are endpoints that allow you to monitor the health and readiness of your application and its dependencies (e.g., database, external services).

**Example:**
```csharp
services.AddHealthChecks();
app.MapHealthChecks("/health");
```

---

## Q215. What are Middlewares in ASP.NET Core?

**Explanation:**
Middlewares are software components that process HTTP requests and responses in the app's pipeline. Examples: Authentication, logging, error handling.

---

## Q216. What are Tag Helpers in ASP.NET Core?

**Explanation:**
Tag Helpers are server-side components that help create and render HTML elements in Razor views using C# code.

**Example:**
```csharp
<input asp-for="Name" />
```

---

## Q217. What is the difference between Razor Pages and MVC?

**Explanation:**
- **Razor Pages:** Page-centric, each page handles its own model and actions, simpler for page-focused scenarios.
- **MVC:** Controller-centric, better for large, complex applications with many views.

---

## Q218. What is Identity in ASP.NET Core?

**Explanation:**
Identity is a membership system for authentication and user management (registration, login, roles, claims) in ASP.NET Core applications.

---

## Q219. How to implement JWT Authentication in ASP.NET Core?

**Explanation:**
- Add JWT middleware and configure authentication in `Startup.cs`.
- Validate JWT tokens on incoming requests.

**Example:**
```csharp
services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options => { /* config */ });
```

---

## Q220. What are Claims in ASP.NET Core Identity?

**Explanation:**
Claims are key-value pairs that represent user data (like roles, permissions, email) and are used for authorization decisions.

**Example:**
```csharp
var claims = new List<Claim> { new Claim(ClaimTypes.Role, "Admin") };
```

---
## Q221. What is Policy-based Authorization in ASP.NET Core?

**Explanation:**
Policy-based authorization allows you to define complex access control rules (policies) using requirements and handlers. Policies are registered during startup and applied with the `[Authorize(Policy = "PolicyName")]` attribute.

**Example:**
```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdminOnly", policy => policy.RequireRole("Admin"));
});

// Usage in controller
[Authorize(Policy = "AdminOnly")]
public IActionResult AdminAction() { ... }
```

---

## Q222. What is Middleware Pipeline in .NET Core?

**Explanation:**
The middleware pipeline is the ordered sequence of middleware components that process HTTP requests and responses in ASP.NET Core. Each middleware can pass control to the next or short-circuit the pipeline.

**Example:**
```csharp
app.UseMiddleware<LoggingMiddleware>();
app.UseRouting();
app.UseEndpoints(endpoints => { endpoints.MapControllers(); });
```

---

## Q223. What is Kestrel?

**Explanation:**
Kestrel is a cross-platform web server for ASP.NET Core, used as the default web server to process HTTP requests.

---

## Q224. What is Hosting in ASP.NET Core?

**Explanation:**
Hosting refers to the environment where the ASP.NET Core app runs. The host manages app startup, configuration, dependency injection, and the request pipeline.

---

## Q225. What is the difference between IHost and IWebHost in ASP.NET Core?

**Explanation:**
- `IHost`: Used for generic hosting (web, background, etc.), supports services like logging, DI, configuration.
- `IWebHost`: Legacy/older, specific to web applications. `IHost` is preferred in ASP.NET Core 3.0+.

---

## Q226. What is strongly typed configuration in .NET Core?

**Explanation:**
Strongly typed configuration binds configuration settings (from appsettings.json, etc.) to C# classes, providing IntelliSense and compile-time checking.

**Example:**
```csharp
public class MySettings { public string Key { get; set; } }
services.Configure<MySettings>(Configuration.GetSection("MySettings"));
```

---

## Q227. How do you read environment variables in .NET Core?

**Explanation:**
Use `Environment.GetEnvironmentVariable("VAR_NAME")`, or bind them through `IConfiguration` for app settings.

**Example:**
```csharp
string value = Environment.GetEnvironmentVariable("ASPNETCORE_ENVIRONMENT");
```

---

## Q228. What is appsettings.json? How do you use it?

**Explanation:**
`appsettings.json` is the default configuration file in .NET Core for storing app settings, connection strings, etc. Access via `IConfiguration`.

**Example:**
```json
{
  "ConnectionStrings": { "Default": "..." }
}
```
```csharp
var connStr = Configuration.GetConnectionString("Default");
```

---

## Q229. How do you send emails in .NET?

**Explanation:**
Use `System.Net.Mail.SmtpClient` and `MailMessage`. In .NET Core, use third-party libraries (e.g., MailKit) as SmtpClient is obsolete.

**Example:**
```csharp
using (var client = new SmtpClient("smtp.server.com"))
{
    var mail = new MailMessage("from@a.com", "to@b.com", "Subject", "Body");
    client.Send(mail);
}
```

---

## Q230. What is async/await? Give an example.

**Explanation:**
`async` and `await` are used for asynchronous programming, allowing non-blocking operations.

**Example:**
```csharp
public async Task<string> DownloadAsync(string url)
{
    using var client = new HttpClient();
    return await client.GetStringAsync(url);
}
```

---

## Q231. What is a ValueTuple in C#?

**Explanation:**
A `ValueTuple` is a lightweight data structure for grouping multiple values without creating a class.

**Example:**
```csharp
public (int Id, string Name) GetUser() => (1, "Alice");
```

---

## Q232. What is pattern matching in C#?

**Explanation:**
Pattern matching simplifies control flow based on object types, properties, or values with `is`, `switch`, and newer C# enhancements.

**Example:**
```csharp
if (obj is string s && s.Length > 0) { ... }
```

---

## Q233. What is the difference between public, private, protected, and internal in C#?

**Explanation:**
- `public`: Accessible everywhere.
- `private`: Accessible only within the declaring class.
- `protected`: Accessible in declaring class and derived classes.
- `internal`: Accessible within the same assembly.

---

## Q234. What is the difference between abstract class and interface (C# 8 and newer)?

**Explanation:**
- Abstract class: Can include implementation, fields, constructors, and access modifiers.
- Interface: Can have default implementations, but no fields/constructors; multiple interfaces can be implemented.

---

## Q235. What is the difference between struct and class in C#?

**Explanation:**
- `class`: Reference type, stored on heap, supports inheritance.
- `struct`: Value type, stored on stack, no inheritance.

**Example:**
```csharp
struct Point { public int X, Y; }
class Person { public string Name; }
```

---

## Q236. What is IDisposable and the Dispose Pattern?

**Explanation:**
`IDisposable` defines a `Dispose()` method for releasing unmanaged resources. The Dispose Pattern ensures proper cleanup, often used with `using`.

**Example:**
```csharp
public class MyResource : IDisposable
{
    public void Dispose() { /* Cleanup */ }
}
```

---

## Q237. How do you implement logging in .NET Core?

**Explanation:**
Use built-in logging via `ILogger<T>`, configure providers (Console, Debug, etc.), and inject `ILogger` into classes.

**Example:**
```csharp
public class HomeController
{
    private readonly ILogger<HomeController> _logger;
    public HomeController(ILogger<HomeController> logger) => _logger = logger;
}
```

---

## Q238. What is Serilog?

**Explanation:**
Serilog is a popular, flexible logging library for .NET that allows structured logging and supports many sinks (console, files, ElasticSearch, etc.).

**Example:**
```csharp
Log.Logger = new LoggerConfiguration().WriteTo.Console().CreateLogger();
```

---

## Q239. What is MediatR?

**Explanation:**
MediatR is a library for implementing the Mediator pattern in .NET. It decouples request handling (commands, queries, notifications) from their implementation.

---

## Q240. What is CQRS?

**Explanation:**
CQRS (Command Query Responsibility Segregation) is a design pattern that separates reading (query) and writing (command) operations into different models, improving scalability and maintainability.

---
## Q241. What is SOLID in object-oriented design?

**Explanation:**
SOLID is an acronym for five design principles for writing maintainable and scalable object-oriented code:
- **S**ingle Responsibility Principle
- **O**pen/Closed Principle
- **L**iskov Substitution Principle
- **I**nterface Segregation Principle
- **D**ependency Inversion Principle

---

## Q242. What is the Single Responsibility Principle?

**Explanation:**
A class should have only one reason to change, meaning it should have only one job or responsibility.

**Example:**
```csharp
// BAD: Handles data and logging
class UserService { void Save() { /* save & log */ } }

// GOOD: Separate responsibilities
class UserService { void Save() { /* save */ } }
class Logger { void Log(string msg) { /* log */ } }
```

---

## Q243. What is the Open/Closed Principle?

**Explanation:**
Software entities (classes, modules, functions) should be open for extension, but closed for modification.

**Example:**
```csharp
// Use interfaces/abstraction so new functionality can be added without changing existing code
interface IShape { double Area(); }
class Rectangle : IShape { ... }
class Circle : IShape { ... }
```

---

## Q244. What is the Liskov Substitution Principle?

**Explanation:**
Objects of a superclass should be replaceable with objects of a subclass without altering the correctness of the program.

**Example:**
```csharp
// Derived classes should honor the behavior of base classes
class Bird { virtual void Fly() { } }
class Sparrow : Bird { override void Fly() { } }
// Don't create a Penguin : Bird if Penguin can't Fly()
```

---

## Q245. What is the Interface Segregation Principle?

**Explanation:**
Clients should not be forced to depend on interfaces they do not use; create smaller, more specific interfaces.

**Example:**
```csharp
interface IPrint { void Print(); }
interface IScan { void Scan(); }
class Printer : IPrint { ... }
class Scanner : IScan { ... }
```

---

## Q246. What is the Dependency Inversion Principle?

**Explanation:**
High-level modules should not depend on low-level modules; both should depend on abstractions.

**Example:**
```csharp
interface IMessageSender { void Send(string msg); }
class EmailSender : IMessageSender { ... }
class Notification { IMessageSender sender; }
```

---

## Q247. What is TDD (Test Driven Development)?

**Explanation:**
TDD is a development process where you write tests before writing production code, following the cycle: Red (fail) → Green (pass) → Refactor.

---

## Q248. What is mocking? Why is it used in unit testing?

**Explanation:**
Mocking is the practice of creating fake objects that mimic real dependencies, allowing you to isolate and test units of code.

**Example:**
```csharp
var mockService = new Mock<IMyService>();
mockService.Setup(s => s.DoSomething()).Returns(42);
```

---

## Q249. What is xUnit, NUnit, and MSTest?

**Explanation:**
They are popular .NET unit testing frameworks:
- **xUnit:** Modern, extensible, open-source.
- **NUnit:** Feature-rich, attribute-based.
- **MSTest:** Microsoft's official test framework.

---

## Q250. What is Continuous Integration (CI) and Continuous Deployment (CD)?

**Explanation:**
- **CI:** Automates building and testing code every time a team member commits changes.
- **CD:** Automates deploying applications to production after passing CI, ensuring frequent, reliable releases.

---
	