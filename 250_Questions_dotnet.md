# .NET Interview Questions – Professional, Modern, and Practical Guide

---

### Q1. What is C#? What is the difference between C# and .NET?

**Explanation:**

C# (C-sharp) is a modern, strongly-typed, object-oriented programming language created by Microsoft, primarily for building applications on the .NET platform. It is used for developing web, desktop, cloud, mobile, IoT, and gaming solutions.

.NET is a comprehensive development platform and runtime that provides services like memory management, type safety, garbage collection, and a vast set of libraries (APIs) for building and running applications.

**Differences:**

| Aspect    | C# (Language)         | .NET (Platform/Framework)              |
|-----------|----------------------|----------------------------------------|
| Type      | Programming Language | Runtime & Libraries                    |
| Usage     | Author application logic | Hosts, compiles, and manages code   |
| Examples  | Classes, interfaces, lambdas | CLR, ASP.NET Core, EF Core        |

**Example:**

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, World using C# on .NET!");
    }
}
```

---

### Q2. What is OOP? What are the main concepts of OOP?

**Explanation:**

Object-Oriented Programming (OOP) is a methodology that structures software as a collection of objects, which encapsulate data and behavior. The four core OOP pillars are:

- **Encapsulation**: Hides internal state and requires all interaction to be performed through an object's methods.
- **Abstraction**: Exposes only relevant features; hides unnecessary details.
- **Inheritance**: Allows a new class to acquire properties and behavior of an existing class.
- **Polymorphism**: Enables objects to be treated as instances of their parent class, with behavior specific to their derived type.

**Example:**

```csharp
public abstract class Animal // Abstraction
{
    public abstract void Speak();
}

public class Dog : Animal // Inheritance
{
    public override void Speak() // Polymorphism
        => Console.WriteLine("Dog barks");
}
```

---

### Q3. What are the advantages of OOP?

**Explanation:**

- **Modularity**: Code is organized into reusable objects and classes.
- **Reusability**: Inheritance and composition promote code reuse across applications.
- **Maintainability**: Encapsulation and abstraction make code easier to modify and extend.
- **Testability**: Modular units are easier to test independently.
- **Scalability**: OOP naturally models complex, scalable systems.

**Example:**

```csharp
public class Vehicle
{
    public virtual void Start() => Console.WriteLine("Vehicle started");
}

public class Car : Vehicle
{
    public void Drive() => Console.WriteLine("Car driving");
}
```

---

### Q4. What are the limitations of OOP?

**Explanation:**

- Overhead: OOP can introduce complexity and performance overhead, especially for small or performance-critical scripts.
- Steep learning curve: Understanding abstraction, polymorphism, and inheritance can be challenging for beginners.
- Over-design: Excessive use of patterns or abstraction can make code harder to follow (over-engineering).

---

### Q5. What are Classes and Objects?

**Explanation:**

A **class** is a blueprint that defines the structure and behavior (methods, properties) of objects. An **object** is an instance of a class, representing a concrete entity with state and behavior.

**Example:**

```csharp
public class Person
{
    public string Name { get; set; }
}

var person = new Person { Name = "Alice" };
```

---

### Q6. What are the types of classes in C#?

**Explanation:**

- **Static Class**: Cannot be instantiated; contains only static members.
- **Abstract Class**: Cannot be instantiated; may contain abstract members to be implemented by derived classes.
- **Sealed Class**: Cannot be inherited.
- **Partial Class**: Defined across multiple files (combined at compile time).
- **Concrete Class**: Regular class that can be instantiated.

**Example:**

```csharp
public static class Utilities { }
public abstract class Animal { public abstract void Speak(); }
public sealed class Logger { }
public partial class Customer { }
public class Employee { }
```

---

### Q7. Is it possible to prevent object creation of a class in C#?

**Explanation:**

Yes, by:
- Making the constructor private (commonly used in singleton patterns).
- Declaring the class as `static` (for utility/helper classes).
- Declaring the class as `abstract` (cannot be directly instantiated).

**Example:**

```csharp
public class Singleton
{
    private Singleton() { }
    public static Singleton Instance { get; } = new Singleton();
}
```

---

### Q8. What is a Property?

**Explanation:**

A property in C# provides a flexible mechanism to expose private fields. Properties use `get` and `set` accessors for controlled access, supporting validation, encapsulation, and computed values.

**Example:**

```csharp
public class Person
{
    private string _name;
    public string Name
    {
        get => _name;
        set => _name = value;
    }
}
```

---

### Q9. What is the difference between a Property and a Method?

**Explanation:**

- **Property**: Used to read, write, or compute a value. Accessed like a field, but with logic.
- **Method**: Performs operations or actions. Invoked with parentheses; can take parameters.

**Example:**

```csharp
public class Box
{
    public int Height { get; set; } // Property

    public int CalculateVolume(int width, int length) // Method
        => Height * width * length;
}
```

---

### Q10. What are Namespaces?

**Explanation:**

Namespaces organize code into logical groups and help prevent name collisions by qualifying class names. They are essential in large projects and when using third-party libraries.

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

### Q11. What is Inheritance? When should it be used?

**Explanation:**

Inheritance allows a class to inherit fields, properties, and methods from another class. Use inheritance when you have a clear "is-a" relationship and want to enable code reuse and polymorphism.

**Example:**

```csharp
public class Animal { public void Eat() => Console.WriteLine("Eating"); }

public class Dog : Animal { public void Bark() => Console.WriteLine("Bark"); }
```

---

### Q12. What are the types of Inheritance in C#?

**Explanation:**

- **Single Inheritance**: A class inherits from one base class.
- **Multilevel Inheritance**: A class inherits from a derived class.
- **Hierarchical Inheritance**: Multiple classes inherit from a single base class.
- **Multiple Inheritance**: Not supported for classes in C#, but supported via interfaces.

**Example:**

```csharp
public class Animal { }
public class Dog : Animal { }
public class Cat : Animal { }
```

---

### Q13. Does C# support Multiple Inheritance?

**Explanation:**

C# does not support multiple inheritance for classes (to avoid ambiguity), but supports it for interfaces. A class can implement multiple interfaces.

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

### Q14. How do you prevent a class from being inherited?

**Explanation:**

Use the `sealed` keyword to prevent other classes from inheriting from it.

**Example:**

```csharp
public sealed class FinalClass { }
```

---

### Q15. Are private class members inherited by derived classes?

**Explanation:**

Private members are inherited, but not directly accessible in derived classes. They can only be accessed via protected or public members in the base class.

**Example:**

```csharp
public class Base { private int _x; }
public class Derived : Base { /* _x is inherited, but not accessible */ }
```

---

### Q16. What is Abstraction? How do you implement it in C#?

**Explanation:**

Abstraction exposes only essential features and hides implementation details. In C#, abstraction is implemented using abstract classes and interfaces.

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

### Q17. What is Encapsulation? How do you implement it?

**Explanation:**

Encapsulation bundles data and behavior together and restricts direct access to internal state. It is implemented using access modifiers (private, protected, public) and properties.

**Example:**

```csharp
public class Account
{
    private double _balance;
    public void Deposit(double amount) => _balance += amount;
    public double GetBalance() => _balance;
}
```

---

### Q18. What is the difference between Abstraction and Encapsulation?

**Explanation:**

- **Abstraction**: Focuses on exposing only relevant features (what an object does).
- **Encapsulation**: Focuses on restricting access to internal state (how it does it).

---

### Q19. What is Polymorphism? What are its types, and when is it used?

**Explanation:**

Polymorphism allows different types to be treated as a base type, enabling a single interface for entities of different types. Types:
- **Compile-time (static) polymorphism**: Method overloading.
- **Run-time (dynamic) polymorphism**: Method overriding.

Use polymorphism when you want code flexibility and extensibility.

**Example:**

```csharp
public class Animal { public virtual void Speak() => Console.WriteLine("Animal"); }
public class Dog : Animal { public override void Speak() => Console.WriteLine("Dog"); }

Animal animal = new Dog();
animal.Speak(); // Output: Dog
```

---

### Q20. What is Method Overloading? How can a method be overloaded?

**Explanation:**

Method overloading allows multiple methods with the same name but different parameter lists (type, number, or order). Overloading improves code readability and usability.

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

### Q21. When should you use method overloading in real applications?

**Explanation:**

Use method overloading for similar operations requiring different types or numbers of parameters. It simplifies APIs and reduces code duplication.

**Example:**

```csharp
public void Log(string message) { }
public void Log(string message, Exception ex) { }
```

---

### Q22. Can two methods be overloaded by return type alone?

**Explanation:**

No, methods cannot be overloaded by only differing return types. The compiler requires different parameter lists for overload resolution.

**Example:**

```csharp
// Not allowed:
// int Foo() { ... }
// string Foo() { ... }
```

---

### Q23. What is the difference between Overloading and Overriding?

**Explanation:**

- **Overloading**: Same method name, different parameters, in the same class.
- **Overriding**: Redefining a base class virtual/abstract method in a derived class.

**Example:**

```csharp
public class A { public virtual void Print() { } }
public class B : A { public override void Print() { } }
public class C
{
    public void Print(int x) { }
    public void Print(string y) { } // Overloading
}
```

---

### Q24. What is the use of Overriding?

**Explanation:**

Overriding allows derived classes to provide a specific implementation of a method defined in the base class, enabling polymorphic behavior.

**Example:**

```csharp
public class Animal { public virtual void Speak() => Console.WriteLine("Animal"); }
public class Cat : Animal { public override void Speak() => Console.WriteLine("Meow"); }
```

---

### Q25. If a method is marked as virtual, must it be overridden in the child class?

**Explanation:**

No. Overriding is optional. If not overridden, the child class inherits the base implementation.

**Example:**

```csharp
public class Parent { public virtual void Show() => Console.WriteLine("Parent"); }
public class Child : Parent { }
```

---

### Q26. What is the difference between Method Overriding and Method Hiding?

**Explanation:**

- **Method Overriding**: Uses `override` keyword; method must be `virtual`, `abstract`, or `override` in the base class.
- **Method Hiding**: Uses `new` keyword; hides the base method with a new implementation.

**Example:**

```csharp
public class Base { public virtual void Print() { } }
public class Derived : Base { public new void Print() { } }
```

---

### Q27. What is the difference between an Abstract class and an Interface?

**Explanation:**

| Feature         | Abstract Class                           | Interface                        |
|-----------------|-----------------------------------------|----------------------------------|
| Implementation  | Can provide some implementation         | Only method/property signatures (C# 8+ allows default implementation) |
| Fields          | Can have fields                         | Cannot have fields (except static in C# 8+) |
| Constructors    | Can have constructors                   | Cannot have constructors         |
| Inheritance     | Single inheritance                      | Multiple inheritance supported   |

**Example:**

```csharp
public interface IRun { void Run(); }
public abstract class Animal { public abstract void Speak(); }
```

---

### Q28. When should you use an Interface and when an Abstract class?

**Explanation:**

- Use **interface** to define contracts for unrelated classes and when multiple inheritance is needed.
- Use **abstract class** to provide a common base and shared implementation for related classes.

**Example:**

```csharp
public interface IDrawable { void Draw(); }
public abstract class Shape { public abstract double Area(); }
```

---

### Q29. Why create interfaces in real applications?

**Explanation:**

Interfaces enable loose coupling, facilitate dependency injection, enforce contracts, and allow for flexible, testable, and maintainable code.

**Example:**

```csharp
public interface ILogger { void Log(string message); }
```

---

### Q30. Can you define method bodies in interfaces? When is this allowed?

**Explanation:**

Before C# 8, interfaces could not have method bodies. C# 8+ allows default interface method implementations.

**Example:**

```csharp
public interface IDefault
{
    void Foo() => Console.WriteLine("Default"); // C# 8+ only
}
```

---

### Q31. Can you create an instance of an Abstract class or Interface?

**Explanation:**

No. You must inherit and instantiate a derived/concrete class.

**Example:**

```csharp
// Not allowed:
// var a = new AbstractClass();
```

---

### Q32. Can interfaces have constructors?

**Explanation:**

No. Interfaces cannot have constructors.

---

### Q33. Can abstract classes have constructors in C#?

**Explanation:**

Yes. Abstract classes can have constructors for base initialization, which are invoked when a derived class is instantiated.

**Example:**

```csharp
public abstract class Base
{
    public Base() => Console.WriteLine("Base constructor");
}
public class Derived : Base { }
```

---

### Q34. What is the difference between abstraction and abstract class?

**Explanation:**

- **Abstraction**: Concept for exposing only essential features and hiding implementation details.
- **Abstract class**: Tool in C# to implement abstraction.

---

### Q35. Can an Abstract class be Sealed or Static in C#?

**Explanation:**

No. An abstract class cannot be sealed (cannot be inherited) or static (cannot be instantiated).

---

### Q36. Can you declare abstract methods as private in C#?

**Explanation:**

No. Abstract methods must be `public` or `protected` (not `private`), so they can be implemented by derived classes.

---

### Q37. Does an Abstract class support multiple inheritance?

**Explanation:**

No. A class (including abstract) can inherit from only one class, but can implement multiple interfaces.

---

### Q38. What are Access Modifiers?

**Explanation:**

Access modifiers control the visibility of types and members:

| Modifier          | Scope                                 |
|-------------------|---------------------------------------|
| `private`         | Declaring type only                   |
| `protected`       | Declaring type and derived types      |
| `internal`        | Same assembly                         |
| `protected internal` | Same assembly or derived types     |
| `public`          | No restriction                        |
| `private protected` | Derived types in same assembly      |

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

### Q39. What is the internal access modifier? Show example.

**Explanation:**

`internal` limits access to types or members to the current assembly. It is commonly used for implementation details not intended for external use.

**Example:**

```csharp
internal class InternalClass { }
```

---

### Q40. What is the default access modifier for a class?

**Explanation:**

- Top-level classes: `internal` by default.
- Class members: `private` by default.

**Example:**

```csharp
class MyClass // internal by default
{
    int number; // private by default
}
```

---

### Q41. What is Boxing and Unboxing?

**Explanation:**

- **Boxing**: Converts a value type (e.g., int) to an object (reference type).
- **Unboxing**: Extracts the value type from the object.

Boxing allocates on the heap, which can affect performance.

**Example:**

```csharp
int number = 5;
object boxed = number;        // Boxing
int unboxed = (int)boxed;     // Unboxing
```

---

### Q42. Which is explicit: Boxing or Unboxing?

**Explanation:**

- **Boxing** is implicit.
- **Unboxing** is explicit (requires a cast).

**Example:**

```csharp
int x = 10;
object obj = x;        // Boxing (implicit)
int y = (int)obj;      // Unboxing (explicit)
```

---

### Q43. Is Boxing and Unboxing good for performance?

**Explanation:**

No. Boxing/unboxing involve heap allocations and type conversions, which can hurt performance in high-frequency scenarios. Avoid in tight loops or performance-critical code.

**Example:**

```csharp
for (int i = 0; i < 100000; i++)
{
    object o = i; // Boxing in a loop is costly
}
```

---

### Q44. What are basic string operations in C#?

**Explanation:**

Common string operations include:

- Concatenation
- Comparison
- Searching (`Contains`, `IndexOf`)
- Substring extraction
- Splitting
- Replacement
- Case conversion

**Example:**

```csharp
string name = "DotNet";
string greeting = $"Hello, {name}";
bool hasD = name.Contains('D');
string upper = name.ToUpper();
```

---

### Q45. What is the difference between String and StringBuilder?

**Explanation:**

| Aspect         | String                  | StringBuilder          |
|----------------|------------------------|------------------------|
| Mutability     | Immutable (cannot change in place) | Mutable         |
| Performance    | Inefficient for many modifications (creates new objects) | Efficient for repeated changes |

Use `StringBuilder` for complex or repetitive string manipulations.

**Example:**

```csharp
string s = "Hello";
s += " World"; // Allocates a new string

var sb = new StringBuilder("Hello");
sb.Append(" World"); // Modifies existing object
```

---

### Q46. When to use String and when StringBuilder?

**Explanation:**

- Use `string` for small or infrequent modifications.
- Use `StringBuilder` for repeated or performance-critical string concatenations (e.g., loops, building large text).

**Example:**

```csharp
var sb = new StringBuilder();
for (int i = 0; i < 1000; i++)
    sb.Append(i);
string result = sb.ToString();
```

---

### Q47. What is String Interpolation in C#?

**Explanation:**

String interpolation (C# 6+) allows embedding expressions directly in string literals using the `$` prefix for cleaner, readable code.

**Example:**

```csharp
string name = "Alice";
string greeting = $"Hello, {name}!";
```

---

### Q48. What are the loop types in C#? When should you use each?

**Explanation:**

| Loop Type      | When to Use                         |
|----------------|-------------------------------------|
| `for`          | Fixed number of iterations          |
| `while`        | Unknown count, condition first      |
| `do-while`     | Unknown count, condition last       |
| `foreach`      | Iterating collections (recommended for IEnumerable types) |

**Example:**

```csharp
for (int i = 0; i < 5; i++) { }
while (true) { break; }
do { } while(false);
foreach (var ch in "abc") { }
```

---

### Q49. What is the difference between `continue` and `break` statement?

**Explanation:**

- **`continue`**: Skips to the next loop iteration.
- **`break`**: Exits the loop immediately.

**Example:**

```csharp
for (int i = 0; i < 5; i++)
{
    if (i == 2) continue;
    if (i == 4) break;
    Console.WriteLine(i);
}
```

---

### Q50. What are the alternative ways of writing if-else conditions? When to use them?

**Explanation:**

- **Ternary Operator** (`condition ? true : false`): For simple, inline decisions.
- **Switch Statement**: For multiple choices.
- **Pattern Matching** (C# 7+): For more expressive type/value checks.

**Example:**

```csharp
// Ternary
int a = 5;
string result = (a > 0) ? "Positive" : "Non-positive";

// Switch
switch (a)
{
    case 1: break;
    default: break;
}
```

---

---

### Q51. How do you implement Exception Handling in C#?

**Explanation:**

Exception handling in C# is managed using `try`, `catch`, and `finally` blocks. Use `try` to enclose code that may throw exceptions, `catch` to handle specific or general exceptions, and `finally` to execute cleanup code regardless of whether an exception occurred.

**Example:**

```csharp
try
{
    int value = int.Parse("abc"); // Throws FormatException
}
catch (FormatException ex)
{
    Console.WriteLine($"Error: {ex.Message}");
}
finally
{
    Console.WriteLine("Cleanup code runs here.");
}
```

---

### Q52. Can we have multiple catch blocks? When is this useful?

**Explanation:**

Yes. Multiple `catch` blocks can be chained after a single `try` block to handle different exception types separately. This allows for more granular error handling and tailored responses to various failure scenarios.

**Example:**

```csharp
try
{
    // Some operation
}
catch (FormatException ex)
{
    Console.WriteLine("Input format is incorrect.");
}
catch (NullReferenceException ex)
{
    Console.WriteLine("Null value encountered.");
}
catch (Exception ex)
{
    Console.WriteLine($"General error: {ex.Message}");
}
```

---

### Q53. When should you use the finally block in real applications?

**Explanation:**

Use `finally` to clean up resources (files, database connections, network streams, etc.) regardless of whether an exception was thrown. It ensures resource release and avoids leaks.

**Example:**

```csharp
FileStream fileStream = null;
try
{
    fileStream = new FileStream("data.txt", FileMode.Open);
    // Read or write operations
}
finally
{
    fileStream?.Dispose();
}
```

---

### Q54. Can we have a try block without a catch block?

**Explanation:**

Yes, but only if the `try` block is followed by a `finally` block. This is useful when cleanup is required, but you don't want to handle the exception in place.

**Example:**

```csharp
try
{
    // Potentially risky operation
}
finally
{
    // Cleanup code
}
```

---

### Q55. What is the difference between Finally and Finalize?

**Explanation:**

- **finally**: A block of code that always executes after the try/catch blocks, used for releasing resources.
- **Finalize**: A destructor method (`~ClassName`) that is called by the garbage collector before reclaiming an object, used for unmanaged resource cleanup.

**Example:**

```csharp
// Using finally
try { /* ... */ } finally { /* cleanup */ }

// Using Finalize (not recommended for most cases)
class Resource
{
    ~Resource() { /* cleanup unmanaged resources */ }
}
```

---

### Q56. What is the difference between `throw` and `throw ex` in C#? Which to use?

**Explanation:**

- `throw ex`: Resets the call stack, losing the original exception source.
- `throw`: Preserves the original stack trace, which is essential for debugging.

**Recommendation:** Always use `throw;` when rethrowing exceptions.

**Example:**

```csharp
try
{
    // ...
}
catch (Exception ex)
{
    // Process or log
    throw; // Best practice: preserves stack trace
}
```

---

### Q57. Explain Generics in C#. When and why should you use them?

**Explanation:**

Generics provide type-safe data structures and methods, allowing code reuse, compile-time type checking, and performance efficiency by avoiding boxing/unboxing. Use generics for collections, utility classes, and methods that work with multiple types.

**Example:**

```csharp
var numbers = new List<int>(); // Only ints allowed
public T Identity<T>(T value) => value;
```

---

### Q58. What are Collections in C#, and what are their types?

**Explanation:**

Collections are classes that manage groups of related objects. C# provides:

- Arrays: Fixed size, type-safe
- List<T>: Dynamic, generic
- Dictionary<TKey, TValue>: Key-value pairs
- HashSet<T>: Unique items
- Stack<T>, Queue<T>: LIFO/FIFO
- LinkedList<T>, ObservableCollection<T>, etc.

**Example:**

```csharp
List<string> names = new();
Dictionary<int, string> people = new();
```

---

### Q59. What is the difference between Array and ArrayList?

**Explanation:**

| Feature        | Array           | ArrayList           |
|----------------|-----------------|---------------------|
| Size           | Fixed at creation | Dynamic             |
| Type Safety    | Strongly typed   | Stores objects (boxing/unboxing for value types) |
| Performance    | Fast             | Slower for value types due to boxing/unboxing |

**Example:**

```csharp
int[] arr = new int[2];
ArrayList list = new();
list.Add(1);
list.Add("text"); // No type safety
```

---

### Q60. What is the difference between ArrayList and Hashtable?

**Explanation:**

| Feature         | ArrayList   | Hashtable            |
|-----------------|-------------|----------------------|
| Storage         | Indexed by integer | Key-value pairs    |
| Key Type        | Not applicable     | Any object         |
| Type Safety     | No                | No (object-typed)  |

**Example:**

```csharp
ArrayList list = new() { 1, 2, 3 };
Hashtable table = new() { { "a", 1 }, { "b", 2 } };
```

---

### Q61. What is the difference between List<T> and Dictionary<TKey, TValue>?

**Explanation:**

- **List<T>**: Stores ordered items of the same type, accessed by index.
- **Dictionary<TKey, TValue>**: Stores key-value pairs, allowing fast lookups by key.

**Example:**

```csharp
List<string> fruits = new() { "Apple", "Banana" };
Dictionary<int, string> idToFruit = new() { { 1, "Apple" }, { 2, "Banana" } };
```

---

### Q62. What is IEnumerable in C#?

**Explanation:**

`IEnumerable` is an interface for collections that can be enumerated with `foreach`. It exposes an enumerator to iterate over elements and is the base for LINQ queries.

**Example:**

```csharp
IEnumerable<int> numbers = new List<int> { 1, 2, 3 };
foreach (var n in numbers)
    Console.WriteLine(n);
```

---

### Q63. What is the difference between IEnumerable and IEnumerator?

**Explanation:**

- **IEnumerable**: Exposes `GetEnumerator()` to return an enumerator.
- **IEnumerator**: Provides `MoveNext()`, `Current`, and `Reset()` for manual iteration.

**Example:**

```csharp
IEnumerable<int> numbers = new List<int> { 1, 2 };
IEnumerator<int> enumerator = numbers.GetEnumerator();
while (enumerator.MoveNext())
{
    Console.WriteLine(enumerator.Current);
}
```

---

### Q64. What is the difference between IEnumerable and IQueryable?

**Explanation:**

- **IEnumerable**: Executes queries in memory, suitable for collections (LINQ to Objects).
- **IQueryable**: Builds expression trees and can translate queries to external data sources (like databases). Enables deferred execution and query composition.

**Example:**

```csharp
// IEnumerable for in-memory collections
List<int> list = new() { 1, 2, 3 };
IEnumerable<int> en = list.Where(x => x > 1);

// IQueryable for remote data (e.g., Entity Framework)
IQueryable<User> users = dbContext.Users.Where(u => u.IsActive);
```

---

### Q65. What is a Constructor? When should you use it?

**Explanation:**

A constructor is a special method called when an object is created, used to initialize the object's state. Use constructors to enforce required data and setup invariants.

**Example:**

```csharp
public class Person
{
    public string Name { get; }
    public Person(string name) => Name = name;
}

var p = new Person("Bob");
```

---

### Q66. What are the types of constructors in C#?

**Explanation:**

- **Default (parameterless) constructor**
- **Parameterized constructor**
- **Copy constructor** (common pattern, not enforced)
- **Static constructor** (for static member initialization)
- **Private constructor** (prevents direct instantiation)

**Example:**

```csharp
public class Demo
{
    public Demo() { } // Default
    public Demo(int x) { } // Parameterized
    public Demo(Demo other) { } // Copy
    static Demo() { } // Static
    private Demo(string s) { } // Private
}
```

---

### Q67. What is a Default constructor?

**Explanation:**

A constructor with no parameters. Automatically generated if no other constructors exist.

**Example:**

```csharp
public class Box
{
    public Box() { /* default constructor */ }
}
```

---

### Q68. What is a Parameterized constructor?

**Explanation:**

A constructor that takes arguments to set initial property or field values.

**Example:**

```csharp
public class Point
{
    public int X, Y;
    public Point(int x, int y) => (X, Y) = (x, y);
}
```

---

### Q69. What is a Static constructor? What is its use?

**Explanation:**

A static constructor initializes static members and runs only once, before any static member is accessed or the type is instantiated. Used for type-level initialization.

**Example:**

```csharp
public class Config
{
    public static readonly string Version;
    static Config()
    {
        Version = "1.0.0";
    }
}
```

---

### Q70. Can static constructors have parameters or access modifiers?

**Explanation:**

No. Static constructors cannot have parameters or access modifiers; they are always parameterless and implicitly private.

**Example:**

```csharp
public class Demo
{
    static Demo() { /* OK */ }
    // static Demo(int x) { } // Error
}
```

---

### Q71. What is a Copy constructor?

**Explanation:**

A constructor that creates a new object by copying fields from another instance. Not enforced by the language but a common pattern.

**Example:**

```csharp
public class Person
{
    public string Name { get; }
    public Person(Person other) => Name = other.Name;
}
```

---

### Q72. What is a Private constructor? What is its use?

**Explanation:**

A constructor marked `private` prevents instantiation from outside the class. Used for singleton patterns, static classes, or utility classes.

**Example:**

```csharp
public class Singleton
{
    private Singleton() { }
    public static Singleton Instance { get; } = new Singleton();
}
```

---

### Q73. What is Constructor overloading?

**Explanation:**

Defining multiple constructors with different parameter lists to provide flexible object creation.

**Example:**

```csharp
public class Rectangle
{
    public Rectangle() { }
    public Rectangle(int width, int height) { }
}
```

---

### Q74. What is a Destructor?

**Explanation:**

A destructor (`~ClassName`) is called by the garbage collector before reclaiming the object. It is used to free unmanaged resources but should be avoided in favor of `IDisposable` and the `Dispose` pattern.

**Example:**

```csharp
public class Demo
{
    ~Demo() { /* cleanup unmanaged resources */ }
}
```

---

### Q75. Can you create an object of a class with a private constructor?

**Explanation:**

No, unless using a static method inside the class (e.g., singleton pattern).

**Example:**

```csharp
public class Singleton
{
    private Singleton() { }
    public static Singleton Instance { get; } = new Singleton();
}
```

---

### Q76. If both base and derived classes have constructors, which executes first?

**Explanation:**

The base class constructor executes first, followed by the derived class constructor. This ensures the base is initialized before specialization.

**Example:**

```csharp
public class Base { public Base() => Console.WriteLine("Base"); }
public class Child : Base { public Child() => Console.WriteLine("Child"); }
```

---

### Q77. What is a Method in C#?

**Explanation:**

A method is a block of code that performs a specific task, can take parameters, and may return a value. Methods promote code reuse and organization.

**Example:**

```csharp
public int Add(int x, int y) => x + y;
```

---

### Q78. What is the difference between Pass by Value and Pass by Reference?

**Explanation:**

- **Pass by value**: The method receives a copy of the argument; original value is not changed.
- **Pass by reference (`ref`, `out`)**: The method can modify the original variable.

**Example:**

```csharp
void Increment(ref int x) { x++; }
int a = 5;
Increment(ref a); // a is now 6
```

---

### Q79. How can you return more than one value from a method in C#?

**Explanation:**

Use `out` parameters, tuples, or custom types. Tuples (C# 7+) are preferred for simplicity.

**Example:**

```csharp
void GetValues(out int x, out int y) { x = 1; y = 2; }
(int, int) GetTuple() => (1, 2);
```

---

### Q80. What is the difference between `out` and `ref` parameters?

**Explanation:**

- `ref`: The variable must be initialized before passing. Method can read/write.
- `out`: No need to initialize before passing. Method must assign a value before returning.

**Example:**

```csharp
void SetValue(out int x) { x = 10; }
void Add(ref int x) { x++; }
```

---

### Q81. What is the `params` keyword? When should you use it?

**Explanation:**

The `params` keyword lets you pass a variable number of arguments as an array to a method. Use it when the number of parameters is unknown at compile time.

**Example:**

```csharp
public void PrintNumbers(params int[] numbers)
{
    foreach (var n in numbers)
        Console.WriteLine(n);
}

PrintNumbers(1, 2, 3, 4);
```

---

### Q82. What are optional parameters in a method?

**Explanation:**

Optional parameters allow a method to be called with fewer arguments than declared. They have default values specified in the method signature.

**Example:**

```csharp
public void Greet(string name = "Guest") =>
    Console.WriteLine($"Hello, {name}");

Greet(); // Output: Hello, Guest
```

---

### Q83. What are named parameters in a method?

**Explanation:**

Named parameters let you specify arguments by name rather than position, improving readability and flexibility.

**Example:**

```csharp
public void Display(string firstName, string lastName) =>
    Console.WriteLine($"{firstName} {lastName}");

Display(lastName: "Doe", firstName: "John");
```

---

### Q84. What are Extension Methods in C#? When should you use them?

**Explanation:**

Extension methods add custom methods to existing types without modifying their source code. Useful for adding utility or helper functions to .NET or third-party types (especially LINQ).

**Example:**

```csharp
public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str) =>
        string.IsNullOrEmpty(str);
}

string s = null;
bool result = s.IsNullOrEmpty();
```

---

### Q85. What are Delegates in C#? When are they useful?

**Explanation:**

A delegate is a type-safe reference to a method. Delegates are used for callbacks, event handling, and functional programming patterns.

**Example:**

```csharp
public delegate int Operation(int a, int b);

public class Calculator
{
    public int Add(int a, int b) => a + b;
}

var calc = new Calculator();
Operation op = calc.Add;
int result = op(2, 3);
```

---

### Q86. What are Multicast Delegates?

**Explanation:**

A multicast delegate can reference multiple methods. When invoked, all methods are called in order. Useful for event broadcast or chaining operations.

**Example:**

```csharp
public delegate void Notify();
Notify notify = () => Console.WriteLine("First");
notify += () => Console.WriteLine("Second");
notify(); // Output: First\nSecond
```

---

### Q87. What are Anonymous Delegates in C#?

**Explanation:**

Anonymous delegates allow you to define inline delegate implementations without a named method. Useful for short, one-off callbacks or event handlers.

**Example:**

```csharp
Action print = delegate { Console.WriteLine("Hello World"); };
print();
```

---

### Q88. What is the difference between Events and Delegates?

**Explanation:**

- **Delegate**: Can be invoked directly by the code that holds it.
- **Event**: Wrapper around a delegate; only the declaring class can invoke it. Used for publish/subscribe patterns.

**Example:**

```csharp
public delegate void Notify();
public class Publisher
{
    public event Notify OnPublish;
}
```

---

### Q89. What is the `this` keyword in C#? When is it used?

**Explanation:**

`this` represents the current instance of the class. Use it to reference instance members, resolve naming conflicts, or pass the current object as a parameter.

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

### Q90. What is the purpose of the `using` keyword in C#?

**Explanation:**

- **Namespace import**: To include namespaces.
- **Resource management**: To define a scope for objects to be disposed automatically (implements `IDisposable`).

**Example:**

```csharp
using System.IO; // Namespace usage

using (var reader = new StreamReader("file.txt"))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

---

### Q91. Can you use `using` with classes other than database connections?

**Explanation:**

Yes. Any class that implements `IDisposable` can be used in a `using` statement for automatic resource cleanup.

**Example:**

```csharp
using (var fs = new FileStream("a.txt", FileMode.Open)) { }
```

---

### Q92. What is the difference between `is` and `as` operators?

**Explanation:**

- **`is`**: Checks if an object is of a given type, returns `bool`.
- **`as`**: Attempts to cast; returns `null` if the cast fails (no exception).

**Example:**

```csharp
object obj = "string";
if (obj is string) { }
string s = obj as string; // s is "string" or null
```

---

### Q93. What is the difference between `readonly` and `const` variables?

**Explanation:**

- **`const`**: Must be assigned at declaration; evaluated at compile time; implicitly static.
- **`readonly`**: Can be assigned in declaration or constructor; evaluated at runtime; can be instance or static.

**Example:**

```csharp
public class Demo
{
    public const int Max = 10;
    public readonly int Id;
    public Demo(int id) => Id = id;
}
```

---

### Q94. What is a Static class? When should you use it?

**Explanation:**

A static class cannot be instantiated, inherited, or contain instance members. Use for utility/helper classes or grouping related static methods.

**Example:**

```csharp
public static class MathHelper
{
    public static int Square(int x) => x * x;
}
```

---

### Q95. What is the difference between `var` and `dynamic` in C#?

**Explanation:**

- **`var`**: Type is determined at compile time; type safety enforced.
- **`dynamic`**: Type is resolved at runtime; bypasses compile-time checks; useful for interop, dynamic languages, or reflection.

**Example:**

```csharp
var x = 5; // int
dynamic y = 5;
y = "now a string"; // OK
```

---

### Q96. What is the `enum` keyword used for?

**Explanation:**

An `enum` defines a set of named constants for grouping related values, improving code readability and type safety.

**Example:**

```csharp
enum Day { Sun, Mon, Tue, Wed, Thu, Fri, Sat }
Day today = Day.Fri;
```

---

### Q97. Can enums be inherited in C#?

**Explanation:**

No. Enums cannot be inherited or serve as a base for other enums.

---

### Q98. What is the use of the `yield` keyword in C#?

**Explanation:**

`yield` simplifies the implementation of iterators by maintaining state across calls. It enables lazy evaluation and streaming of data.

**Example:**

```csharp
public IEnumerable<int> GetNumbers()
{
    yield return 1;
    yield return 2;
}
```

---

### Q99. What is LINQ? When should you use LINQ in real applications?

**Explanation:**

LINQ (Language Integrated Query) allows you to query, filter, and transform data using a SQL-like syntax directly in C#. Use LINQ for working with collections, databases, XML, and more.

**Example:**

```csharp
var evens = from n in Enumerable.Range(1, 10) where n % 2 == 0 select n;
```

---

### Q100. What are the advantages and disadvantages of LINQ?

**Explanation:**

- **Advantages**: Readable, type-safe queries; integrates with C#; reusable logic; supports deferred execution.
- **Disadvantages**: Sometimes less efficient than hand-written queries; debugging can be harder; not all LINQ providers support all features.

**Example:**

```csharp
var nums = new List<int> { 1, 2, 3, 4 };
var evens = nums.Where(n => n % 2 == 0).ToList();
```

---

---

### Q101. What are Lambda Expressions? What are their practical uses?

**Explanation:**

Lambda expressions are concise, anonymous functions that can contain expressions and statements. They are commonly used to create delegates or expression trees and are widely used in LINQ queries, event handlers, and functional programming scenarios.

Modern C# lambdas support capturing variables from their enclosing scope (closures), discards, and pattern matching.

**Example:**

```csharp
Func<int, int, int> add = (a, b) => a + b;
int sum = add(2, 3); // sum = 5

var squares = Enumerable.Range(1, 5).Select(x => x * x);
```

---

### Q102. What is the difference between `First` and `FirstOrDefault` in LINQ?

**Explanation:**

- **`First`**: Returns the first element of a sequence. Throws an exception if the sequence is empty.
- **`FirstOrDefault`**: Returns the first element or the default value for the type (`null` for reference types, `0` for value types) if the sequence is empty.

**Example:**

```csharp
var numbers = new List<int>();
// int n = numbers.First(); // Throws InvalidOperationException
int n = numbers.FirstOrDefault(); // Returns 0
```

---

### Q103. What are the important components of the .NET framework?

**Explanation:**

- **CLR (Common Language Runtime)**: Manages code execution, memory, security, and exception handling.
- **FCL (Framework Class Library)**: Rich set of APIs and types.
- **CTS (Common Type System)**: Defines how types are declared and used.
- **CLS (Common Language Specification)**: Ensures language interoperability.
- **Assemblies**: Compiled code units (DLL/EXE), versioned and reusable.

---

### Q104. What is an Assembly? What are its types?

**Explanation:**

An assembly is a compiled code library for use in .NET applications. Types:

- **Private Assembly**: Used by a single application.
- **Shared Assembly**: Can be shared by multiple applications if placed in the Global Assembly Cache (GAC).
- **Satellite Assembly**: Contains resources for localization.

**Example:**

- `MyApp.dll` (private)
- `System.Text.Json.dll` (shared)

---

### Q105. What is GAC (Global Assembly Cache)?

**Explanation:**

GAC is a machine-wide code cache that stores assemblies intended to be shared by multiple applications. Assemblies in the GAC must have a strong name (version, culture, public key token).

---

### Q106. What is Reflection in .NET?

**Explanation:**

Reflection allows inspection of metadata, types, and members at runtime. It is used for dynamic type discovery, late binding, automated testing, serialization, and dependency injection frameworks.

**Example:**

```csharp
Type t = typeof(string);
foreach (var method in t.GetMethods())
    Console.WriteLine(method.Name);
```

---

### Q107. What are Serialization and Deserialization?

**Explanation:**

- **Serialization**: Converting an object into a format (such as JSON, XML, or binary) for storage or transmission.
- **Deserialization**: Reconstructing an object from its serialized form.

**Example:**

```csharp
using System.Text.Json;
var json = JsonSerializer.Serialize(new { Name = "Alice" });
var obj = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
```

---

### Q108. What is Globalization and Localization in .NET?

**Explanation:**

- **Globalization**: Designing applications to support multiple cultures, languages, and regions.
- **Localization**: Customizing the application for a specific culture or locale (e.g., translating UI, formatting dates/numbers).

**Example:**

```csharp
using System.Globalization;
var ci = new CultureInfo("fr-FR");
double value = 12345.67;
Console.WriteLine(value.ToString("N", ci)); // "12 345,67"
```

---

### Q109. What are Windows Services?

**Explanation:**

Windows Services are long-running background processes that can start automatically at system boot. They are used for applications that run without user interaction, such as monitoring, scheduled tasks, or server daemons.

---

### Q110. What is Garbage Collection (GC)?

**Explanation:**

Garbage Collection is an automatic memory management feature of .NET that reclaims memory occupied by objects that are no longer referenced, preventing memory leaks. GC runs on its own schedule and is optimized for performance.

**Example:**

```csharp
GC.Collect(); // Forces GC, but generally not recommended
```

---

### Q111. What are Generations in .NET Garbage Collection?

**Explanation:**

The .NET GC divides objects into three generations:

- **Gen 0**: Short-lived objects (most collected quickly).
- **Gen 1**: Objects that survived Gen 0 collection.
- **Gen 2**: Long-lived objects (rarely collected).

This generational approach optimizes performance by collecting short-lived objects more frequently.

---

### Q112. What is the difference between `Dispose` and `Finalize`?

**Explanation:**

- **`Dispose()`**: Explicitly releases unmanaged resources. Called by user code, typically via a `using` block.
- **`Finalize()`**: Destructor; called by GC before object is reclaimed. Used as a safety net for releasing unmanaged resources.

**Example:**

```csharp
public class MyResource : IDisposable
{
    public void Dispose() { /* Free resources */ }
    ~MyResource() { /* Cleanup before GC */ }
}
```

---

### Q113. What is the difference between `Finalize` and `finally`?

**Explanation:**

- **Finalize**: Destructor logic executed by the garbage collector.
- **finally**: Code block that always runs after `try`/`catch`, used for cleanup.

**Example:**

```csharp
try { } finally { /* always runs */ }
class Demo { ~Demo() { /* runs on GC */ } }
```

---

### Q114. Can you force the Garbage Collector to run?

**Explanation:**

Yes, by calling `GC.Collect()`. However, this is discouraged as GC is optimized to manage memory efficiently and forcing GC can harm performance.

**Example:**

```csharp
GC.Collect();
```

---

### Q115. What is the difference between Process and Thread?

**Explanation:**

- **Process**: An independent unit with its own memory space and resources.
- **Thread**: A lightweight unit within a process; threads share the same memory within a process.

**Example:**

```csharp
using System.Threading;
Thread t = new(() => Console.WriteLine("Hello from thread"));
t.Start();
```

---

### Q116. What is Multithreading? Why is it useful?

**Explanation:**

Multithreading enables concurrent execution of multiple threads, improving responsiveness and throughput in applications, especially on multi-core CPUs.

**Example:**

```csharp
Thread t1 = new(() => Console.WriteLine("Thread 1"));
Thread t2 = new(() => Console.WriteLine("Thread 2"));
t1.Start(); t2.Start();
```

---

### Q117. What is the difference between synchronous and asynchronous programming? What is the role of `Task`?

**Explanation:**

- **Synchronous**: Code executes sequentially and blocks until the operation completes.
- **Asynchronous**: Code can continue executing while waiting for an operation to complete, improving scalability and responsiveness.

`Task` represents an asynchronous operation, supporting continuations and composition.

**Example:**

```csharp
public async Task<int> ComputeAsync()
{
    await Task.Delay(1000);
    return 42;
}
```

---

### Q118. What is the difference between Threads and Tasks? Why prefer Tasks?

**Explanation:**

- **Thread**: OS-level unit of execution; manually managed; more resource intensive.
- **Task**: Abstraction over threads; managed by the .NET Task Scheduler; supports cancellation, continuation, and high-level parallelism.

**Example:**

```csharp
Task.Run(() => Console.WriteLine("Running in a Task"));
```

---

### Q119. What is the role of `async` and `await`?

**Explanation:**

- **`async`**: Marks a method as asynchronous, enabling the use of `await`.
- **`await`**: Suspends method execution until the awaited Task completes, freeing up the calling thread.

**Example:**

```csharp
public async Task<int> DelayReturnAsync()
{
    await Task.Delay(1000);
    return 7;
}
```

---

### Q120. What is the difference between DBMS and RDBMS?

**Explanation:**

- **DBMS (Database Management System)**: Manages data as files or collections, no relationships.
- **RDBMS (Relational DBMS)**: Manages data as tables with relationships, supports SQL, constraints, transactions.

**Examples:**  
DBMS: MS Access, File System  
RDBMS: SQL Server, MySQL, PostgreSQL

---

### Q121. What is a Constraint in SQL? What are its types?

**Explanation:**

Constraints ensure data integrity in a database. Types:

- **Primary Key**: Unique identifier for a row.
- **Foreign Key**: Enforces referential integrity between tables.
- **Unique**: Ensures all values in a column are unique.
- **Check**: Ensures values meet a specified condition.
- **Default**: Assigns a default value.
- **Not Null**: Disallows null values.

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

### Q122. What is the difference between Primary Key and Unique Key?

**Explanation:**

| Feature          | Primary Key    | Unique Key             |
|------------------|---------------|------------------------|
| Uniqueness       | Enforced      | Enforced               |
| Nulls Allowed    | No            | Yes                    |
| Per Table        | One           | Multiple allowed       |

---

### Q123. What are Triggers and their types?

**Explanation:**

A trigger is a stored procedure that runs automatically in response to certain events (INSERT, UPDATE, DELETE) on a table.

- **AFTER Trigger**: Executes after the event.
- **INSTEAD OF Trigger**: Executes instead of the event.
- **BEFORE Trigger**: Not supported in SQL Server but available in other DBMS.

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

### Q124. What is a View?

**Explanation:**

A view is a virtual table based on the result set of a SQL query. It does not store data itself; used for simplifying queries, security, or abstraction.

**Example:**

```sql
CREATE VIEW ActiveEmployees AS
SELECT * FROM Employee WHERE IsActive = 1;
```

---

### Q125. What is the difference between HAVING and WHERE clauses?

**Explanation:**

- **WHERE**: Filters rows before grouping.
- **HAVING**: Filters groups after `GROUP BY`.

**Example:**

```sql
SELECT Dept, COUNT(*) 
FROM Employee 
WHERE Salary > 5000 
GROUP BY Dept 
HAVING COUNT(*) > 3;
```

---

### Q126. What is a Subquery (Nested or Inner Query) in SQL?

**Explanation:**

A subquery is a query nested inside another query, used for filtering, calculating, or correlating data.

**Example:**

```sql
SELECT Name FROM Employee 
WHERE DeptID IN (SELECT DeptID FROM Department WHERE Location = 'NY');
```

---

### Q127. What is an Auto Increment/Identity column in SQL Server?

**Explanation:**

An identity column automatically generates a unique value for each new row, commonly used for primary keys.

**Example:**

```sql
CREATE TABLE Employee (
    EmpID INT IDENTITY(1,1) PRIMARY KEY,
    Name VARCHAR(100)
);
```

---

### Q128. What are Joins in SQL?

**Explanation:**

Joins combine rows from two or more tables based on a related column, enabling relational queries.

---

### Q129. What are the types of Joins in SQL Server?

**Explanation:**

- **INNER JOIN**: Returns matching rows.
- **LEFT (OUTER) JOIN**: All left table rows + matching right table rows.
- **RIGHT (OUTER) JOIN**: All right table rows + matching left table rows.
- **FULL (OUTER) JOIN**: All rows from both tables, matching where possible.
- **CROSS JOIN**: Cartesian product of both tables.

**Example:**

```sql
SELECT * FROM A INNER JOIN B ON A.Id = B.AId;
```

---

### Q130. What is a Self-Join?

**Explanation:**

A self-join joins a table to itself using table aliases, often used to represent hierarchical data or relationships within the same table.

**Example:**

```sql
SELECT e1.Name, e2.Name AS Manager
FROM Employee e1
LEFT JOIN Employee e2 ON e1.ManagerID = e2.EmpID;
```

---

### Q131. What are Indexes in SQL Server?

**Explanation:**

Indexes are special data structures that speed up data retrieval but may slow down insert/update/delete operations. Indexes can be clustered or non-clustered.

---

### Q132. What is a Clustered Index?

**Explanation:**

A clustered index determines the physical order of data in a table. Each table can have only one clustered index, typically on the primary key.

**Example:**

```sql
CREATE CLUSTERED INDEX idx_EmpID ON Employee(EmpID);
```

---

### Q133. What is a Non-Clustered Index?

**Explanation:**

A non-clustered index is a separate structure from the table data and holds pointers to the data rows. A table can have multiple non-clustered indexes.

**Example:**

```sql
CREATE NONCLUSTERED INDEX idx_Name ON Employee(Name);
```

---

### Q134. What is the difference between Clustered and Non-Clustered Index?

**Explanation:**

| Feature        | Clustered Index   | Non-Clustered Index     |
|----------------|------------------|-------------------------|
| Storage        | Sorts and stores data rows | Separate structure    |
| Per Table      | One              | Many                    |

---

### Q135. How to create Clustered and Non-Clustered Indexes?

**Example:**

```sql
-- Clustered
CREATE CLUSTERED INDEX idx_EmpID ON Employee(EmpID);

-- Non-Clustered
CREATE NONCLUSTERED INDEX idx_Name ON Employee(Name);
```

---

### Q136. Which columns should be indexed to optimize queries?

**Explanation:**

Index columns used in `WHERE`, `JOIN`, or `ORDER BY` clauses for frequent lookups, filtering, or sorting. Avoid indexing columns with low selectivity (many repeated values).

**Example:**

```sql
SELECT * FROM Employee WHERE Email = 'a@b.com';
-- Index on Email column helps performance
```

---

### Q137. What is the difference between Stored Procedure and Function?

**Explanation:**

| Feature            | Stored Procedure             | Function                |
|--------------------|-----------------------------|-------------------------|
| Returns            | Zero/multiple values         | Single value/table      |
| Use in SELECT      | No                          | Yes                     |
| Transactions       | Yes                         | No                      |
| Output Parameters  | Supported                   | Not supported           |

---

### Q138. How do you optimize a Stored Procedure or SQL Query?

**Explanation:**

- Use indexes efficiently.
- Avoid `SELECT *`; select only needed columns.
- Use proper joins and avoid unnecessary cursors.
- Use `SET NOCOUNT ON`.
- Regularly update statistics and analyze execution plans.

---

### Q139. What is a Cursor? Why should you avoid them?

**Explanation:**

A cursor allows row-by-row processing of result sets, but is slow and resource-intensive. Prefer set-based operations for better performance and scalability.

---

### Q140. What is the difference between `SCOPE_IDENTITY()` and `@@IDENTITY`?

**Explanation:**

- **`@@IDENTITY`**: Returns last identity value generated in current session, any table/trigger.
- **`SCOPE_IDENTITY()`**: Returns last identity value in current scope; recommended to avoid unexpected results from triggers.

**Example:**

```sql
INSERT INTO Employee (Name) VALUES ('Bob');
SELECT SCOPE_IDENTITY();
```

---
<!-- ...Previous questions... -->

---

### Q141. What is a CTE in SQL Server?

**Explanation:**

A Common Table Expression (CTE) is a temporary, named result set defined within the execution scope of a single SQL statement. CTEs improve query readability, support recursion, and enable modular query design.

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

### Q142. What is the difference between DELETE, TRUNCATE, and DROP commands?

**Explanation:**

| Command   | Removes Data | Removes Structure | Rollback Possible | Identity Reset |
|-----------|--------------|------------------|-------------------|---------------|
| DELETE    | Yes (rows)   | No               | Yes (transaction) | No            |
| TRUNCATE  | Yes (all)    | No               | No (in most DBMS) | Yes           |
| DROP      | Yes (all)    | Yes              | No                | N/A           |

**Example:**

```sql
DELETE FROM Employee WHERE EmpID = 1;
TRUNCATE TABLE Employee;
DROP TABLE Employee;
```

---

### Q143. How do you get the Nth highest salary of an employee?

**Explanation:**

Use window functions like `ROW_NUMBER()` or `DENSE_RANK()` to rank salaries, then filter by the desired rank.

**Example:**

```sql
SELECT Salary FROM (
    SELECT Salary, DENSE_RANK() OVER (ORDER BY Salary DESC) AS Rank
    FROM Employee
) AS Temp
WHERE Rank = N; -- Replace N with 2 for the second highest, etc.
```

---

### Q144. What are ACID properties?

**Explanation:**

- **Atomicity**: All operations in a transaction succeed or none do.
- **Consistency**: The database remains valid before and after the transaction.
- **Isolation**: Transactions do not interfere with each other.
- **Durability**: Once committed, changes persist even in case of system failure.

---

### Q145. What are Magic Tables in SQL Server?

**Explanation:**

Magic tables (`INSERTED` and `DELETED`) are special tables available in triggers that hold the affected rows during an `INSERT`, `UPDATE`, or `DELETE` operation.

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

### Q146. What is MVC? Explain the MVC life cycle.

**Explanation:**

MVC (Model-View-Controller) is a design pattern that separates application logic:

- **Model**: Business logic and data.
- **View**: UI representation.
- **Controller**: Handles user input and coordinates between Model and View.

**Life Cycle:**  
Request → Routing → Controller → Action Method → Result (View/Redirect/JSON) → Response

---

### Q147. What are the advantages of MVC over Web Forms?

**Explanation:**

- Clear separation of concerns.
- Better support for test-driven development (TDD).
- Fine-grained control over HTML, CSS, and JavaScript.
- Easier maintenance and extensibility.
- RESTful patterns supported natively.

---

### Q148. What are the return types of a controller Action method in MVC?

**Explanation:**

- `ViewResult` / `PartialViewResult` (HTML)
- `JsonResult` (JSON)
- `RedirectResult` / `RedirectToActionResult`
- `ContentResult` (plain text)
- `FileResult` (files)
- `EmptyResult` / `ActionResult` / `Task<ActionResult>` (base type)

**Example:**

```csharp
public ActionResult Index() => View();
public JsonResult Data() => Json(new { Name = "Alice" });
```

---

### Q149. What are Filters in MVC and their types?

**Explanation:**

Filters are custom logic executed before or after controller actions:

- **Authorization Filter**: Security checks.
- **Action Filter**: Logic before/after action execution.
- **Result Filter**: Logic before/after result processing.
- **Exception Filter**: Error handling.

**Example:**

```csharp
[Authorize]
public ActionResult Index() { ... }
```

---

### Q150. What is Authentication and Authorization in ASP.NET MVC?

**Explanation:**

- **Authentication**: Verifies user identity (login).
- **Authorization**: Grants or denies access to resources/actions based on identity or roles.

---

### Q151. What are the types of Authentication in ASP.NET MVC?

**Explanation:**

- **Forms Authentication** (cookie-based)
- **Windows Authentication**
- **OAuth / OpenID Connect**
- **JWT Bearer Authentication**
- **Custom Authentication**

---

### Q152. What is Output Caching in MVC? How do you implement it?

**Explanation:**

Output caching stores the output of controller actions for a specified duration, reducing rendering time and server load.

**Example:**

```csharp
[OutputCache(Duration = 60, VaryByParam = "none")]
public ActionResult Index() { ... }
```

---

### Q153. What is Routing in MVC?

**Explanation:**

Routing maps incoming URLs to controller actions, enabling clean, SEO-friendly URLs and flexible navigation.

**Example:**

```csharp
routes.MapRoute(
    name: "Default",
    url: "{controller}/{action}/{id}",
    defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
);
```

---

### Q154. What is Attribute-Based Routing in MVC?

**Explanation:**

Attribute routing allows defining routes directly on controller/action methods using `[Route]` attributes, providing flexibility and clarity.

**Example:**

```csharp
[Route("products/{id:int}")]
public ActionResult Details(int id) { ... }
```

---

### Q155. What is the difference between ViewData, ViewBag, and TempData?

**Explanation:**

| Feature    | ViewData                | ViewBag                | TempData                  |
|------------|-------------------------|------------------------|---------------------------|
| Type       | Dictionary (string obj) | Dynamic property       | Dictionary (string obj)   |
| Lifetime   | Current request         | Current request        | Until read (across redirect) |
| Usage      | Pass data to view       | Pass data to view      | Pass data between actions |

---

### Q156. How can you pass data from controller to view in MVC?

**Explanation:**

- Using Model objects (strongly typed)
- Using `ViewData`, `ViewBag`, or `TempData` for loose data

**Example:**

```csharp
ViewData["Message"] = "Hello";
ViewBag.Message = "Hello";
return View(model);
```

---

### Q157. What is a Partial View?

**Explanation:**

A partial view is a reusable view component (like a user control) rendered inside another view for modularity and DRY (Don't Repeat Yourself) design.

**Example:**

```csharp
@Html.Partial("_LoginPartial")
```

---

### Q158. What are Areas in MVC?

**Explanation:**

Areas partition an MVC application into functional sections, each with its own controllers, views, and models, making large applications more manageable.

---

### Q159. How does Validation work in MVC? What are Data Annotations?

**Explanation:**

Validation is performed using Data Annotation attributes on model properties (e.g., `[Required]`, `[StringLength]`). MVC automatically validates models and adds errors to `ModelState`.

**Example:**

```csharp
public class User
{
    [Required]
    public string Name { get; set; }
}
```

---

### Q160. What is MVC Scaffolding?

**Explanation:**

Scaffolding is the automatic generation of CRUD code (controllers, views) based on model classes, accelerating development and enforcing conventions.

---

### Q161. What is the Razor View Engine in MVC?

**Explanation:**

Razor is a markup syntax for embedding C# into HTML. It is the default view engine in ASP.NET MVC and supports clean, maintainable templates.

**Example:**

```csharp
@model MyApp.Models.User
<h1>Hello, @Model.Name!</h1>
```

---

### Q162. What is a Layout in Razor View Engine?

**Explanation:**

A Layout is a shared template (like a master page) providing consistent structure (header, footer, navigation) for multiple views.

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

### Q163. How do you use Partial Views in MVC?

**Explanation:**

Partial views are rendered inside views for modular UI development.

**Example:**

```csharp
@Html.Partial("_LoginPartial")
```

---

### Q164. What is an HTML Helper in MVC?

**Explanation:**

HTML Helpers are methods that generate HTML elements in Razor views, simplifying form creation and other markup tasks.

**Example:**

```csharp
@Html.TextBoxFor(model => model.Name)
@Html.ActionLink("Home", "Index")
```

---

### Q165. What is a strongly-typed View in MVC?

**Explanation:**

A strongly-typed view binds to a specific model class, enabling IntelliSense and compile-time checking, improving reliability.

**Example:**

```csharp
@model MyApp.Models.User
<p>@Model.Name</p>
```

---

### Q166. What are Bundling and Minification in MVC?

**Explanation:**

- **Bundling**: Combines multiple CSS/JS files into one.
- **Minification**: Removes whitespace/comments to reduce file size.

These techniques improve page load speed.

**Example:**

```csharp
bundles.Add(new ScriptBundle("~/bundles/jquery").Include("~/Scripts/jquery-{version}.js"));
```

---

### Q167. What is the difference between TempData, ViewData, and ViewBag?

**Explanation:**

- `ViewData` and `ViewBag`: Pass data from controller to view for the same request.
- `TempData`: Persists data between requests (e.g., after a redirect).

---

### Q168. What is Model Binding in MVC?

**Explanation:**

Model binding automatically maps HTTP request data (form values, query strings, route data) to action method parameters or model properties.

**Example:**

```csharp
public ActionResult Edit(User user) { /* user properties auto-bound */ }
```

---

### Q169. What are Data Annotations in MVC?

**Explanation:**

Data Annotations are attributes used on model properties to enforce validation, formatting, and display rules.

**Example:**

```csharp
public class Product
{
    [Required]
    public string Name { get; set; }
}
```

---

### Q170. How do you perform client-side validation in MVC?

**Explanation:**

Enable unobtrusive JavaScript and use Data Annotations. MVC emits validation attributes, and jQuery Validate performs client-side checks.

**Example:**

```csharp
@model Product
@using (Html.BeginForm()) {
    @Html.EditorFor(m => m.Name)
    @Html.ValidationMessageFor(m => m.Name)
}
```

---

### Q171. What is AntiForgeryToken in MVC?

**Explanation:**

AntiForgeryToken protects against Cross-Site Request Forgery (CSRF) attacks by generating a unique token for forms and validating it on submission.

**Example:**

```csharp
@Html.AntiForgeryToken()
[ValidateAntiForgeryToken]
public ActionResult Save(Model model) { ... }
```

---

### Q172. What is Dependency Injection (DI)? How is it implemented in .NET?

**Explanation:**

Dependency Injection is a design pattern where dependencies are provided to a class rather than created inside it. .NET Core has built-in DI via constructor injection and the built-in IoC container.

**Example:**

```csharp
public class HomeController
{
    private readonly IService _service;
    public HomeController(IService service) => _service = service;
}
```

---

### Q173. What is Inversion of Control (IoC)?

**Explanation:**

IoC is a principle where the control of object creation and dependency management is transferred from the application code to a container or framework.

---

### Q174. What are Action Filters in MVC?

**Explanation:**

Action Filters are attributes that execute custom logic before or after controller actions (e.g., logging, authorization, error handling).

**Example:**

```csharp
public class LogActionFilter : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext filterContext)
    {
        // Custom logic
    }
}
```

---

### Q175. How do you handle errors in MVC?

**Explanation:**

- Use `try-catch` blocks in actions.
- Configure custom error pages in `web.config`.
- Use `HandleErrorAttribute` or custom exception filters for global error handling.

**Example:**

```csharp
[HandleError]
public ActionResult Index() { throw new Exception(); }
```

---

### Q176. What is Web API?

**Explanation:**

ASP.NET Web API is a framework for building RESTful HTTP services that return data (JSON, XML, etc.) for web, mobile, or other clients.

---

### Q177. What is the difference between MVC and Web API?

**Explanation:**

- **MVC**: Primarily serves HTML views for browsers.
- **Web API**: Serves data (JSON/XML), typically for clients or SPAs.

---

### Q178. What is a RESTful service?

**Explanation:**

A RESTful service follows REST principles: stateless, resource-oriented, uses standard HTTP verbs (GET, POST, PUT, DELETE), and exposes resources via URLs.

---

### Q179. What is Attribute Routing in Web API?

**Explanation:**

Attribute routing allows routes to be defined directly on controller actions with `[Route]` attributes, simplifying complex routing scenarios.

**Example:**

```csharp
[Route("api/products/{id}")]
public IHttpActionResult GetProduct(int id) { ... }
```

---

### Q180. How do you secure a Web API?

**Explanation:**

- Use HTTPS.
- Implement authentication (JWT, OAuth, etc.).
- Authorize requests based on roles/claims.
- Validate input and sanitize data.

**Example:**

```csharp
[Authorize(Roles = "Admin")]
public IHttpActionResult GetSecret() { ... }
```

---

### Q181. What is the difference between IHttpActionResult and HttpResponseMessage in Web API?

**Explanation:**

- **IHttpActionResult**: High-level, supports testability and abstraction (Web API 2+).
- **HttpResponseMessage**: Low-level, represents the HTTP response.

**Example:**

```csharp
public IHttpActionResult Get() => Ok("Success");
public HttpResponseMessage GetMsg() => Request.CreateResponse(HttpStatusCode.OK, "Success");
```

---

### Q182. What is CORS? How do you enable CORS in Web API?

**Explanation:**

CORS (Cross-Origin Resource Sharing) allows web applications from one domain to access resources on another. Enable CORS using `[EnableCors]` or globally in configuration.

**Example:**

```csharp
[EnableCors(origins: "*", headers: "*", methods: "*")]
public class MyApiController : ApiController { }
```

---

### Q183. What is Swagger? Why is it used?

**Explanation:**

Swagger (OpenAPI) is a framework for documenting and testing RESTful APIs. It generates interactive documentation and client SDKs for APIs.

---

### Q184. How do you version a Web API?

**Explanation:**

- **URI versioning**: `/api/v1/products`
- **Query string/version header**
- **Namespace-based versioning**
- Use libraries like `Microsoft.AspNetCore.Mvc.Versioning`

---

### Q185. What is OWIN?

**Explanation:**

OWIN (Open Web Interface for .NET) is a standard interface between .NET web servers and web applications, decoupling application code from server code.

---

### Q186. What is Katana?

**Explanation:**

Katana is Microsoft's implementation of OWIN, providing middleware components for building web applications with flexible pipelines.

---

### Q187. What is Middleware in ASP.NET Core?

**Explanation:**

Middleware are components in the HTTP request pipeline that can inspect, modify, or short-circuit requests/responses (e.g., authentication, logging, error handling).

**Example:**

```csharp
app.Use(async (context, next) =>
{
    // Before
    await next.Invoke();
    // After
});
```

---

### Q188. What is Dependency Injection in ASP.NET Core and why is it important?

**Explanation:**

Dependency Injection (DI) in ASP.NET Core provides loose coupling, better testability, and modular architecture by managing service lifetimes and dependencies via built-in or external containers.

---

### Q189. What are the service lifetimes in ASP.NET Core DI?

**Explanation:**

- **Transient**: A new instance created each time requested.
- **Scoped**: One instance per HTTP request.
- **Singleton**: One instance for the application's lifetime.

**Example:**

```csharp
services.AddTransient<IMyService, MyService>();
services.AddScoped<IMyService, MyService>();
services.AddSingleton<IMyService, MyService>();
```

---

### Q190. What is Entity Framework (EF)?

**Explanation:**

Entity Framework is an ORM (Object-Relational Mapper) for .NET, enabling developers to work with databases using .NET objects, LINQ queries, and migrations.

---

### Q191. What are Code First, Database First, and Model First in EF?

**Explanation:**

- **Code First**: Define models in code; EF creates the database.
- **Database First**: Generate models from an existing database.
- **Model First**: Design visual model, generate database and code from it.

---

### Q192. What are migrations in Entity Framework?

**Explanation:**

Migrations enable incremental changes to the database schema as your model evolves, using commands like `Add-Migration` and `Update-Database`.

---

### Q193. What is DbContext in EF?

**Explanation:**

`DbContext` is the primary class for interacting with the database in EF. It manages entity objects, queries, and changes.

**Example:**

```csharp
public class MyDbContext : DbContext
{
    public DbSet<User> Users { get; set; }
}
```

---

### Q194. What is a DbSet in EF?

**Explanation:**

A `DbSet` represents a collection of entities of a given type, mapped to a database table, and enables CRUD operations.

---

### Q195. How do you query data using LINQ in EF?

**Example:**

```csharp
var users = context.Users.Where(u => u.IsActive).ToList();
```

---

### Q196. What is Lazy Loading, Eager Loading, and Explicit Loading in EF?

**Explanation:**

- **Lazy Loading**: Related data loaded automatically when accessed.
- **Eager Loading**: Related data loaded up front using `.Include()`.
- **Explicit Loading**: Manually load related data via `.Load()`.

**Example:**

```csharp
var user = context.Users.Include(u => u.Orders).First();
```

---

### Q197. What is the difference between First, FirstOrDefault, Single, and SingleOrDefault in LINQ?

**Explanation:**

| Method           | Returns                     | Throws If None | Throws If Multiple |
|------------------|----------------------------|---------------|-------------------|
| First            | First element               | Yes           | No                |
| FirstOrDefault   | First or default value      | No            | No                |
| Single           | Only element                | Yes           | Yes               |
| SingleOrDefault  | Only or default value       | No            | Yes               |

---

### Q198. How do you handle concurrency in EF?

**Explanation:**

Use concurrency tokens (like a `RowVersion` column), catch `DbUpdateConcurrencyException`, and resolve conflicts as needed.

---

### Q199. How do you execute raw SQL queries in EF?

**Example:**

```csharp
var products = context.Products.FromSqlRaw("SELECT * FROM Products").ToList();
```

---

### Q200. What is Dapper?

**Explanation:**

Dapper is a lightweight, high-performance micro ORM for .NET. It extends `IDbConnection` with methods for executing SQL and mapping results to objects.

**Example:**

```csharp
using (var conn = new SqlConnection(connStr))
{
    var users = conn.Query<User>("SELECT * FROM Users").ToList();
}
```

---

### Q201. What is Microservices architecture?

**Explanation:**

Microservices architecture structures an application as a collection of small, autonomous services, each focusing on a specific business capability and communicating via APIs.

---

### Q202. What are the benefits of Microservices?

**Explanation:**

- Independent deployment and scaling
- Technology diversity
- Improved fault isolation
- Simplified maintenance and evolution

---

### Q203. What are some challenges in Microservices?

**Explanation:**

- Increased system complexity
- Data consistency and distributed transactions
- Service discovery and coordination
- Monitoring and debugging
- Network latency and security

---

### Q204. What is an API Gateway?

**Explanation:**

An API Gateway is an entry point for client requests to microservices, handling routing, authentication, rate limiting, and response aggregation.

---

### Q205. What is Service Discovery in Microservices?

**Explanation:**

Service Discovery enables services to find and communicate with each other dynamically, typically through a service registry (e.g., Consul, Eureka).

---

### Q206. What is Docker? How is it used with .NET?

**Explanation:**

Docker is a platform for containerizing applications and their dependencies, making deployment consistent and scalable. .NET apps can be containerized for cloud-native deployment.

**Example:**

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:7.0
COPY . /app
WORKDIR /app
ENTRYPOINT ["dotnet", "MyApp.dll"]
```

---

### Q207. What is Kubernetes?

**Explanation:**

Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications (like .NET microservices).

---

### Q208. What is the difference between Monolithic and Microservices architectures?

**Explanation:**

| Architecture   | Monolithic                   | Microservices                        |
|----------------|-----------------------------|--------------------------------------|
| Structure      | Single, unified codebase    | Collection of independent services   |
| Scaling        | All at once                 | Each service independently           |
| Deployment     | One unit                    | Multiple, separate units             |
| Complexity     | Simple at first             | More complex at scale                |

---

### Q209. What is SignalR?

**Explanation:**

SignalR is a library for ASP.NET that enables real-time web functionality, allowing server code to push updates to connected clients (e.g., chat, live dashboards).

---

### Q210. What is gRPC?

**Explanation:**

gRPC is a high-performance, open-source RPC framework that uses Protocol Buffers for serialization and supports cross-platform and cross-language communication.

---

### Q211. What is Blazor?

**Explanation:**

Blazor is a framework for building interactive web UIs using C# and .NET, running client-side in the browser via WebAssembly or server-side.

---

### Q212. What is .NET MAUI?

**Explanation:**

.NET MAUI (Multi-platform App UI) is a cross-platform framework for building native mobile and desktop apps using C# and .NET.

---

### Q213. What is Minimal API in .NET?

**Explanation:**

Minimal API (introduced in .NET 6) enables building lightweight, high-performance HTTP APIs with minimal configuration and boilerplate.

**Example:**

```csharp
var app = WebApplication.CreateBuilder().Build();
app.MapGet("/", () => "Hello World!");
app.Run();
```

---

### Q214. What is Health Check in ASP.NET Core?

**Explanation:**

Health Checks provide endpoints to monitor the health and readiness of your app and its dependencies (e.g., database, external services).

**Example:**

```csharp
services.AddHealthChecks();
app.MapHealthChecks("/health");
```

---

### Q215. What are Middlewares in ASP.NET Core?

**Explanation:**

Middlewares are software components that process HTTP requests and responses in the application's pipeline. Examples: authentication, logging, error handling.

---

### Q216. What are Tag Helpers in ASP.NET Core?

**Explanation:**

Tag Helpers are server-side components for generating HTML in Razor views, enabling rich, maintainable markup with C#.

**Example:**

```csharp
<input asp-for="Name" />
```

---

### Q217. What is the difference between Razor Pages and MVC?

**Explanation:**

- **Razor Pages**: Page-centric; each page handles its own model and actions. Simple for page-focused scenarios.
- **MVC**: Controller-centric; better for complex, multi-view applications.

---

### Q218. What is Identity in ASP.NET Core?

**Explanation:**

Identity is the membership system for authentication and user management (registration, login, roles, claims) in ASP.NET Core applications.

---

### Q219. How do you implement JWT Authentication in ASP.NET Core?

**Explanation:**

- Add JWT middleware and configure authentication in `Startup.cs` or `Program.cs`.
- Validate JWT tokens on incoming requests.

**Example:**

```csharp
services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options => { /* config */ });
```

---

### Q220. What are Claims in ASP.NET Core Identity?

**Explanation:**

Claims are key-value pairs representing user data (roles, permissions, email, etc.) and are used for authorization decisions.

**Example:**

```csharp
var claims = new List<Claim> { new Claim(ClaimTypes.Role, "Admin") };
```

---

### Q221. What is Policy-based Authorization in ASP.NET Core?

**Explanation:**

Policy-based authorization allows you to define custom access rules ("policies") using requirements and handlers, providing more granular security.

**Example:**

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdminOnly", policy => policy.RequireRole("Admin"));
});

[Authorize(Policy = "AdminOnly")]
public IActionResult AdminAction() { ... }
```

---

### Q222. What is the Middleware Pipeline in .NET Core?

**Explanation:**

The middleware pipeline is an ordered sequence of middleware components that process HTTP requests and responses. Each middleware can pass control to the next or short-circuit the pipeline.

**Example:**

```csharp
app.UseMiddleware<LoggingMiddleware>();
app.UseRouting();
app.UseEndpoints(endpoints => { endpoints.MapControllers(); });
```

---

### Q223. What is Kestrel?

**Explanation:**

Kestrel is the cross-platform web server for ASP.NET Core, providing high performance and used as the default server for processing HTTP requests.

---

### Q224. What is Hosting in ASP.NET Core?

**Explanation:**

Hosting refers to the environment that runs the ASP.NET Core application, managing startup, configuration, dependency injection, and the middleware pipeline.

---

### Q225. What is the difference between IHost and IWebHost in ASP.NET Core?

**Explanation:**

- **IHost**: General-purpose host for any .NET application (web, background, etc.); preferred in .NET Core 3.0+.
- **IWebHost**: Legacy, specific to web applications. `IHost` is more flexible and standard now.

---

### Q226. What is strongly typed configuration in .NET Core?

**Explanation:**

Strongly typed configuration binds configuration sections (from `appsettings.json`, environment variables, etc.) to C# classes, providing IntelliSense and compile-time safety.

**Example:**

```csharp
public class MySettings { public string Key { get; set; } }
services.Configure<MySettings>(Configuration.GetSection("MySettings"));
```

---

### Q227. How do you read environment variables in .NET Core?

**Explanation:**

Use `Environment.GetEnvironmentVariable("VAR_NAME")` or bind them via `IConfiguration` for centralized configuration.

**Example:**

```csharp
string env = Environment.GetEnvironmentVariable("ASPNETCORE_ENVIRONMENT");
```

---

### Q228. What is appsettings.json? How do you use it?

**Explanation:**

`appsettings.json` is the default configuration file for .NET Core, storing settings, connection strings, etc. Access via `IConfiguration`.

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

### Q229. How do you send emails in .NET?

**Explanation:**

Use `System.Net.Mail.SmtpClient` (legacy) or third-party libraries like MailKit (recommended for .NET Core).

**Example:**

```csharp
using (var client = new SmtpClient("smtp.server.com"))
{
    var mail = new MailMessage("from@a.com", "to@b.com", "Subject", "Body");
    client.Send(mail);
}
```

---

### Q230. What is async/await? Give an example.

**Explanation:**

`async` and `await` enable asynchronous, non-blocking code, improving responsiveness and scalability.

**Example:**

```csharp
public async Task<string> DownloadAsync(string url)
{
    using var client = new HttpClient();
    return await client.GetStringAsync(url);
}
```

---

### Q231. What is a ValueTuple in C#?

**Explanation:**

A `ValueTuple` is a lightweight data structure for grouping multiple values without defining a class.

**Example:**

```csharp
public (int Id, string Name) GetUser() => (1, "Alice");
```

---

### Q232. What is pattern matching in C#?

**Explanation:**

Pattern matching allows concise, expressive checks and deconstruction of objects, supporting type, property, and value patterns.

**Example:**

```csharp
if (obj is string s && s.Length > 0) { ... }

switch (obj)
{
    case int i when i > 0: Console.WriteLine("Positive int"); break;
    case null: Console.WriteLine("Null"); break;
}
```

---

### Q233. What is the difference between public, private, protected, and internal in C#?

**Explanation:**

| Modifier  | Access Scope                        |
|-----------|-------------------------------------|
| public    | Anywhere                            |
| private   | Declaring type only                 |
| protected | Declaring type and derived types    |
| internal  | Same assembly                       |

---

### Q234. What is the difference between abstract class and interface (C# 8 and newer)?

**Explanation:**

| Feature          | Abstract Class                 | Interface                       |
|------------------|-------------------------------|---------------------------------|
| Implementation   | Can provide implementations   | Can (C# 8+), but limited        |
| Fields           | Allowed                       | Not allowed (except static)     |
| Constructors     | Allowed                       | Not allowed                     |
| Inheritance      | Single                        | Multiple                        |

---

### Q235. What is the difference between struct and class in C#?

**Explanation:**

| Feature        | Class (Reference Type)    | Struct (Value Type)       |
|----------------|--------------------------|---------------------------|
| Allocation     | Heap                     | Stack (typically)         |
| Inheritance    | Supports                  | Not supported             |
| Nullability    | Can be null              | Cannot (unless nullable)  |

**Example:**

```csharp
struct Point { public int X, Y; }
class Person { public string Name; }
```

---

### Q236. What is IDisposable and the Dispose Pattern?

**Explanation:**

`IDisposable` defines a `Dispose()` method for releasing unmanaged resources. The Dispose pattern ensures proper cleanup, typically used with `using` blocks for deterministic disposal.

**Example:**

```csharp
public class MyResource : IDisposable
{
    public void Dispose() { /* Cleanup code */ }
}
```

---

### Q237. How do you implement logging in .NET Core?

**Explanation:**

Use the built-in `ILogger<T>`, configure providers (Console, File, Debug, etc.), and inject `ILogger` into classes for structured, flexible logging.

**Example:**

```csharp
public class HomeController
{
    private readonly ILogger<HomeController> _logger;
    public HomeController(ILogger<HomeController> logger) => _logger = logger;
}
```

---

### Q238. What is Serilog?

**Explanation:**

Serilog is a popular, structured logging library for .NET, supporting rich data, multiple sinks (console, file, ElasticSearch, etc.), and powerful filtering.

**Example:**

```csharp
Log.Logger = new LoggerConfiguration().WriteTo.Console().CreateLogger();
```

---

### Q239. What is MediatR?

**Explanation:**

MediatR is a library implementing the Mediator pattern, decoupling the sender and receiver of requests (commands, queries, notifications) for cleaner CQRS and event-driven architectures.

---

### Q240. What is CQRS?

**Explanation:**

CQRS (Command Query Responsibility Segregation) separates read (query) and write (command) operations into different models, improving scalability, maintainability, and flexibility.

---

### Q241. What is SOLID in object-oriented design?

**Explanation:**

SOLID is a set of five design principles for writing maintainable, scalable code:

- **S**ingle Responsibility Principle
- **O**pen/Closed Principle
- **L**iskov Substitution Principle
- **I**nterface Segregation Principle
- **D**ependency Inversion Principle

---

### Q242. What is the Single Responsibility Principle?

**Explanation:**

A class should have only one reason to change, meaning it should do one thing only.

**Example:**

```csharp
class UserService { void Save() { /* save */ } }
class Logger { void Log(string msg) { /* log */ } }
```

---

### Q243. What is the Open/Closed Principle?

**Explanation:**

Software entities should be open for extension, but closed for modification. Use abstraction and inheritance to extend without changing existing code.

**Example:**

```csharp
interface IShape { double Area(); }
class Rectangle : IShape { ... }
class Circle : IShape { ... }
```

---

### Q244. What is the Liskov Substitution Principle?

**Explanation:**

Derived classes must be substitutable for their base classes without altering the correctness of the program.

**Example:**

```csharp
class Bird { virtual void Fly() { } }
class Sparrow : Bird { override void Fly() { } }
// Don't create Penguin : Bird if Penguin can't Fly()
```

---

### Q245. What is the Interface Segregation Principle?

**Explanation:**

Clients should not be forced to depend on interfaces they do not use. Prefer many small, specific interfaces over large, general ones.

**Example:**

```csharp
interface IPrint { void Print(); }
interface IScan { void Scan(); }
class Printer : IPrint { ... }
class Scanner : IScan { ... }
```

---

### Q246. What is the Dependency Inversion Principle?

**Explanation:**

High-level modules should not depend on low-level modules; both should depend on abstractions. Use interfaces and DI to achieve this.

**Example:**

```csharp
interface IMessageSender { void Send(string msg); }
class EmailSender : IMessageSender { ... }
class Notification
{
    IMessageSender sender;
    public Notification(IMessageSender sender) => this.sender = sender;
}
```

---

### Q247. What is TDD (Test Driven Development)?

**Explanation:**

TDD is a development process where you write tests before production code, following the cycle: Red (fail) → Green (pass) → Refactor.

---

### Q248. What is mocking? Why is it used in unit testing?

**Explanation:**

Mocking creates fake objects that simulate real dependencies, enabling isolated unit testing by controlling behavior and responses.

**Example:**

```csharp
var mockService = new Mock<IMyService>();
mockService.Setup(s => s.DoSomething()).Returns(42);
```

---

### Q249. What are xUnit, NUnit, and MSTest?

**Explanation:**

Popular .NET unit testing frameworks:

- **xUnit**: Modern, extensible, open-source.
- **NUnit**: Feature-rich, attribute-based, mature.
- **MSTest**: Microsoft’s official test framework.

---

### Q250. What is Continuous Integration (CI) and Continuous Deployment (CD)?

**Explanation:**

- **CI**: Automates building and testing code on every commit, ensuring integration issues are detected early.
- **CD**: Automates deployment to production after passing CI, enabling frequent, reliable releases.

---

# End of .NET Interview Questions – Professional, Modern, and Practical Guide
