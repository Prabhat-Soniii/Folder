
---

## 📚 Table of Contents

1. [C# & .NET Fundamentals](#c--net-fundamentals)
2. [OOP Principles & Examples](#oop-principles--examples)
3. [Classes, Objects & Constructors](#classes-objects--constructors)
4. [Properties, Methods & Namespaces](#properties-methods--namespaces)
5. [Inheritance, Abstraction & Encapsulation](#inheritance-abstraction--encapsulation)
6. [Polymorphism & Overloading](#polymorphism--overloading)
7. [Advanced C# Features](#advanced-c-features)
8. [Collections, Generics & LINQ](#collections-generics--linq)
9. [Exception Handling](#exception-handling)
10. [ASP.NET Core & MVC](#aspnet-core--mvc)
11. [Entity Framework & Data Access](#entity-framework--data-access)
12. [Web API, REST & Microservices](#web-api-rest--microservices)
13. [Cloud, Docker & Kubernetes](#cloud-docker--kubernetes)
14. [Design Patterns & SOLID Principles](#design-patterns--solid-principles)
15. [Testing, CI/CD & Modern DevOps](#testing-cicd--modern-devops)
16. [SQL & Database Concepts](#16-sql--database-concepts)
17. [Blazor, MAUI & Modern .NET](#17-blazor-maui--modern-net)
18. [Microservices & Distributed Systems](#18-microservices--distributed-systems)
19. [Performance, Security & Best Practices](#19-performance-security--best-practices)
---

## 1. C# & .NET Fundamentals

### Q1. **What is C#? How does it differ from .NET?**

**Explanation:**  
C# is a strongly-typed, object-oriented, multi-paradigm programming language developed by Microsoft. Its syntax is similar to Java and C++, but it includes modern features such as async/await, records, pattern matching, and LINQ.  
**.NET** is an open-source, cross-platform framework and runtime (CLR) supporting multiple languages (C#, F#, VB.NET). It provides APIs, libraries, and tools for building a wide range of applications (web, desktop, cloud, IoT, gaming).

**Example:**  
```csharp
// Modern C# - Top-level program (C# 9+)
Console.WriteLine($"Running on .NET version {Environment.Version}");
```
**Learning Tip:**  
Think of C# as the “language” and .NET as the “environment” or “ecosystem” it runs in.

---

### Q2. **What is OOP? List and explain the four pillars with examples.**

**Explanation:**  
OOP (Object-Oriented Programming) models software as collections of objects with state and behavior. Its four pillars are:

| Pillar         | Description                                 | Example Code                                                | Analogy                        |
|----------------|---------------------------------------------|-------------------------------------------------------------|--------------------------------|
| Encapsulation  | Bundling data and methods, hiding internals | `private string _ssn; public string SSN { get; set; }`      | Car pedals hide engine         |
| Abstraction    | Exposing only essential features            | `abstract class Animal { public abstract void Speak(); }`    | Remote control hides circuits  |
| Inheritance    | Deriving new classes from existing ones     | `class Dog : Animal { public override void Speak() {...} }`  | Dog inherits Animal behavior   |
| Polymorphism   | Same call, different behaviors              | `Animal a = new Dog(); a.Speak();`                          | “Draw” works for all Shapes    |

**Example:**  
```csharp
public abstract class Animal { public abstract void Speak(); }
public class Dog : Animal { public override void Speak() => Console.WriteLine("Bark!"); }
public class Cat : Animal { public override void Speak() => Console.WriteLine("Meow!"); }
Animal pet = new Dog();
pet.Speak(); // Output: Bark!
```

**Learning Tip:**  
Practice OOP by modeling real systems (e.g., Library, E-Commerce) with classes for entities and relationships.

---

## 2. OOP Principles & Examples

### Q3. **What’s the difference between a class and an object?**

**Explanation:**  
- A **class** is a template or blueprint (e.g., `class Car`) defining properties and behaviors.
- An **object** is an actual instance of a class (e.g., `var myCar = new Car();`).

**Example:**  
```csharp
public class Car
{
    public string Model { get; set; }
    public void Drive() => Console.WriteLine($"{Model} is driving...");
}
var myCar = new Car { Model = "Tesla Model 3" };
myCar.Drive(); // Output: Tesla Model 3 is driving...
```

**Learning Tip:**  
Draw UML diagrams to visualize the difference between classes and their objects.

---

### Q4. **What types of classes exist in C#, and when are they used?**

| Class Type | Description 								| Example 								 | Use Case 				   	 |
|------------|------------------------------------------|----------------------------------------|-------------------------------|
| Static     | Only static members, cannot instantiate  | `public static class MathUtils { ... }`| Utility methods 				 |
| Abstract   | Cannot instantiate, base for others		| `public abstract class Shape { ... }`  | Base contracts, default logic |
| Sealed     | Cannot be inherited 						| `public sealed class Logger { ... }`   | Prevent extension 			 |
| Partial    | Split over multiple files				| `public partial class BigClass { ... }`| Large codebases, code gen 	 |
| Record     | Immutable, value-based class (C# 9+)		| `public record Customer(string Name);` | DTOs, configs 				 |

**Example:**  
```csharp
public static class MathUtils { public static double Sqrt(double x) => Math.Sqrt(x); }
public abstract class Shape { public abstract double Area(); }
public sealed class Logger { public void Log(string msg) => Console.WriteLine(msg); }
public record Customer(string Name, int Id);
```

**Learning Tip:**  
Know when to use each type: use records for DTOs, static for helpers, abstract for base types, sealed for final implementations.

---

### Q5. **How do you prevent object creation of a class?**

**Explanation:**  
- **Private Constructor**: Only accessible within the class (Singleton, Factory).
- **Static Class**: Cannot be instantiated or inherited.
- **Abstract Class**: Cannot instantiate directly, only via subclasses.

**Example:**  
```csharp
public class Singleton
{
    private Singleton() { }
    public static Singleton Instance { get; } = new();
}
```
```csharp
public static class Utilities
{
    public static void Print(string message) => Console.WriteLine(message);
}
```

**Learning Tip:**  
Use static classes for utility methods, and the Singleton pattern for shared resources/services.

---

## 4. Properties, Methods & Namespaces

### Q6. **What is a property, and why use it instead of a field?**

**Explanation:**  
A property exposes data with `get` and `set` accessors, allowing validation, logging, and encapsulation. Fields expose raw data with no control.

**Example:**  
```csharp
public class Account
{
    private decimal _balance;
    public decimal Balance
    {
        get => _balance;
        set
        {
            if (value < 0) throw new ArgumentOutOfRangeException(nameof(Balance));
            _balance = value;
        }
    }
}
```

**Learning Tip:**  
Use auto-properties for simple cases, custom accessors for validation/business rules.

---

### Q7. **Property vs Method: When to use each?**

**Explanation:**  
- **Property:** For data/state—should be quick and side-effect free.
- **Method:** For actions/operations—may have side effects or be slow.

**Example:**  
```csharp
public class Circle
{
    public double Radius { get; set; }
    public double Area => Math.PI * Radius * Radius; // Property
    public void Grow(double factor) => Radius *= factor; // Method
}
```

**Learning Tip:**  
If it’s a noun (state), use a property. If it’s a verb (action), use a method.

---

### Q8. **What is a namespace in C#?**

**Explanation:**  
A namespace is a logical grouping of related classes, interfaces, enums, or structs. It helps organize code and prevent naming conflicts.

**Example:**  
```csharp
namespace SuperShop.Inventory
{
    public class Product { }
}
```

**Learning Tip:**  
Structure namespaces to match your folder structure and solution architecture.

---

## 5. Inheritance, Abstraction & Encapsulation

### Q9. **What is inheritance? Give an example.**

**Explanation:**  
Inheritance allows a class (child) to acquire members and behaviors from another class (parent). It enables code reuse and extensibility.

**Example:**  
```csharp
public class Animal { public virtual void Speak() => Console.WriteLine("Some sound"); }
public class Dog : Animal { public override void Speak() => Console.WriteLine("Bark"); }
var pet = new Dog();
pet.Speak(); // Output: Bark
```

**Learning Tip:**  
Use inheritance only for true “is-a” relationships. Prefer composition for “has-a” or “uses” relationships.

---

### Q10. **What is abstraction? How is it implemented in C#?**

**Explanation:**  
Abstraction hides complexity by exposing only relevant parts of an object. In C#, abstraction is achieved through abstract classes and interfaces.

**Example:**  
```csharp
public abstract class PaymentMethod
{
    public abstract void Pay(decimal amount);
}
public class CreditCard : PaymentMethod
{
    public override void Pay(decimal amount) => Console.WriteLine($"Paid {amount} by card.");
}
```

**Learning Tip:**  
Abstract base types allow you to define what must be implemented, not how.

---

### Q11. **What is encapsulation? How is it achieved in C#?**

**Explanation:**  
Encapsulation restricts direct access to an object’s data, exposing it only via properties or methods.  
Achieved using `private`, `protected`, and `public` access modifiers.

**Example:**  
```csharp
public class BankAccount
{
    private decimal _balance;
    public decimal GetBalance() => _balance;
    public void Deposit(decimal amount) { if(amount > 0) _balance += amount; }
}
```

**Learning Tip:**  
Encapsulation protects data integrity and simplifies code maintenance.

---

### Q12. **Difference between abstraction and encapsulation?**

| Aspect        | Abstraction                                      | Encapsulation                        |
|---------------|--------------------------------------------------|--------------------------------------|
| Purpose       | Hide complex implementation, show functionality  | Restrict access, protect state       |
| Mechanisms    | Abstract class, interface                        | Access modifiers, properties         |
| Focus         | What an object does                              | How an object hides its data         |

**Example:**  
A TV remote (abstraction) hides circuit details. The casing (encapsulation) prevents tampering.

---

## 6. Polymorphism & Overloading

### Q13. **What is polymorphism? Types and usage?**

**Explanation:**  
Polymorphism allows objects to be treated as their parent type; the correct behavior is chosen at runtime (overriding) or compile time (overloading).

- **Compile-time (Static):** Method overloading, operator overloading.
- **Run-time (Dynamic):** Method overriding via `virtual`/`override`.

**Example:**  
```csharp
public class Animal { public virtual void Speak() => Console.WriteLine("Animal sound"); }
public class Cat : Animal { public override void Speak() => Console.WriteLine("Meow"); }
public class Dog : Animal { public override void Speak() => Console.WriteLine("Bark"); }
Animal[] pets = { new Cat(), new Dog() };
foreach (var pet in pets) pet.Speak(); // Output: Meow \n Bark
```

**Learning Tip:**  
Polymorphism is key for writing flexible, extensible code (think plug-ins, frameworks).

---

### Q14. **What is method overloading? How can it be done in C#?**

**Explanation:**  
Method overloading allows multiple methods with the same name but different parameter lists.

**Example:**  
```csharp
public class Calculator
{
    public int Add(int a, int b) => a + b;
    public double Add(double a, double b) => a + b;
    public int Add(int a, int b, int c) => a + b + c;
}
```

**Learning Tip:**  
Use overloading for related behaviors (e.g., constructors, utility methods).

---
## 7. Advanced C# Features

### Q15. **What is the difference between `ref` and `out` parameters in C#? Give an example.**

**Explanation:**  
- `ref` parameters must be initialized before being passed and can be read and written inside the called method.
- `out` parameters do not need to be initialized before being passed, but must be assigned a value in the called method before the method returns.

**Example:**  
```csharp
void AddOne(ref int x) { x += 1; }
void Calculate(out int sum, int a, int b) { sum = a + b; }

int value = 5;
AddOne(ref value); // value is now 6

int result;
Calculate(out result, 2, 3); // result is now 5
```

**Learning Tip:**  
Use `ref` for updating existing values; use `out` for returning multiple values or “constructing” new ones.

---

### Q16. **What is a static constructor? When is it used?**

**Explanation:**  
A static constructor initializes static members of a class. It’s called automatically before any static member is accessed or any instance is created. It cannot take parameters or have access modifiers.

**Example:**  
```csharp
public class Logger
{
    public static string LogPath { get; }
    static Logger() // static constructor
    {
        LogPath = "logs/app.log";
        // Initialize other static resources
    }
}
```

**Learning Tip:**  
Use static constructors to set up static state or expensive resources for a class.

---

### Q17. **What are extension methods? Give a practical example.**

**Explanation:**  
Extension methods add new methods to existing types without modifying the type or creating a derived type.

**Example:**  
```csharp
public static class StringExtensions
{
    public static bool IsNullOrWhiteSpace(this string str) =>
        string.IsNullOrWhiteSpace(str);
}

string name = "  ";
bool isBlank = name.IsNullOrWhiteSpace(); // true
```

**Learning Tip:**  
Use extension methods to add utility functionality to .NET/system types or to create fluent APIs.

---

### Q18. **What are delegates and events? Illustrate with an example.**

**Explanation:**  
- A **delegate** is a type-safe function pointer, allowing methods to be passed as parameters.
- An **event** is a wrapper around a delegate, providing publisher/subscriber semantics.

**Example:**  
```csharp
public delegate void Notify(string message);

public class Publisher
{
    public event Notify OnNotify;
    public void Send(string msg) => OnNotify?.Invoke(msg);
}

var pub = new Publisher();
pub.OnNotify += m => Console.WriteLine($"Received: {m}");
pub.Send("Hello!"); // Output: Received: Hello!
```

**Learning Tip:**  
Use events for loosely coupled message passing (e.g., UI controls, observer pattern).

---

### Q19. **What is a lambda expression? Show common usages.**

**Explanation:**  
A lambda expression is an anonymous function using the `=>` syntax. It’s used for concise delegates, LINQ, callbacks, and more.

**Example:**  
```csharp
Func<int, int, int> add = (a, b) => a + b;
int sum = add(3, 4); // 7

var numbers = new[] { 1, 2, 3, 4, 5 };
var squares = numbers.Select(x => x * x).ToList(); // {1, 4, 9, 16, 25}
```

**Learning Tip:**  
Lambdas are a foundation for LINQ, event handlers, and functional programming in C#.

---

### Q20. **What is LINQ? Why is it important in C#?**

**Explanation:**  
LINQ (Language Integrated Query) is a set of features for querying collections using SQL-like syntax, with type safety and IntelliSense.

**Example:**  
```csharp
var people = new List<string> { "Alice", "Bob", "Charlie" };
var namesWithA = people.Where(name => name.StartsWith("A")).ToList(); // ["Alice"]
```

**Learning Tip:**  
LINQ makes code more readable, expressive, and maintainable. Master filtering, projection (`Select`), and aggregation (`Sum`, `Count`).

---

### Q21. **What is anonymous type in C#?**

**Explanation:**  
An anonymous type is a simple class created on the fly with inferred property names and types.

**Example:**  
```csharp
var person = new { Name = "Alice", Age = 30 };
Console.WriteLine(person.Name); // Alice
```

**Learning Tip:**  
Use anonymous types for temporary data shaping, especially in LINQ queries.

---

### Q22. **What is pattern matching? Give modern C# examples.**

**Explanation:**  
Pattern matching enables concise, expressive code for testing and extracting values from objects, using `is`, `switch`, `when`, and positional patterns.

**Example:**  
```csharp
object shape = new { Radius = 5.0 };
if (shape is { Radius: > 0 } c)
    Console.WriteLine($"Circle with radius {c.Radius}");

string message = shape switch
{
    { Radius: > 0 } => "It's a circle",
    _ => "Unknown shape"
};
```

**Learning Tip:**  
Pattern matching is powerful for type-safe, clear logic—especially when combined with records and switch expressions.

---

### Q23. **What is a tuple and what are ValueTuples?**

**Explanation:**  
A tuple is a lightweight data structure for bundling multiple values. `ValueTuple` (C# 7+) supports named elements, deconstruction, and value semantics.

**Example:**  
```csharp
(string Name, int Age) GetPerson() => ("Alice", 30);
var (name, age) = GetPerson();
Console.WriteLine($"{name} is {age} years old"); // Alice is 30 years old
```

**Learning Tip:**  
Use tuples for returning multiple values without defining a class.

---

### Q24. **What is a nullable reference type? How does it help?**

**Explanation:**  
Nullable reference types (C# 8+) improve code safety by distinguishing between nullable and non-nullable references, helping you avoid null reference exceptions.

**Example:**  
```csharp
#nullable enable
public class User
{
    public string Name { get; set; } // Not nullable
    public string? Nickname { get; set; } // Nullable
}
```

**Learning Tip:**  
Turn on nullable reference types to catch potential bugs at compile time.

---

## 8. Collections, Generics & LINQ

### Q25. **What is a generic collection? Why are generics better than non-generics?**

**Explanation:**  
Generic collections (e.g., `List<T>`, `Dictionary<TKey,TValue>`) enforce type safety at compile time and avoid boxing/unboxing. Non-generic collections (like `ArrayList`) store `object`, leading to casting and runtime errors.

**Example:**  
```csharp
List<int> numbers = new() { 1, 2, 3 };
Dictionary<string, int> ages = new() { ["Alice"] = 30 };
```

**Learning Tip:**  
Always prefer generics for performance and type safety.

---

### Q26. **What is the difference between `IEnumerable<T>` and `IQueryable<T>`?**

**Explanation:**  
- `IEnumerable<T>`: Represents in-memory collections; queries are executed in .NET.
- `IQueryable<T>`: Supports building expression trees for remote query execution (e.g., in a database with Entity Framework).

**Example:**  
```csharp
IEnumerable<int> local = new List<int> { 1, 2, 3 };
IQueryable<User> efUsers = dbContext.Users.Where(u => u.IsActive); // Query sent to DB
```

**Learning Tip:**  
Use `IQueryable` for database queries, `IEnumerable` for in-memory collections.

---

### Q27. **When should you use `List<T>`, `Dictionary<K,V>`, `HashSet<T>`, and `Queue<T>`?**

| Type         | Description                          | Example Use Case           |
|--------------|--------------------------------------|---------------------------|
| List<T>      | Ordered, resizable, indexable list   | Maintaining an ordered list of items |
| Dictionary   | Key-value pairs, fast lookups        | Caching, mapping IDs to objects      |
| HashSet<T>   | Unordered, no duplicates             | Ensuring uniqueness                  |
| Queue<T>     | FIFO collection                      | Processing tasks in order            |

**Example:**  
```csharp
var users = new List<string> { "Alice", "Bob" };
var userAges = new Dictionary<string, int> { ["Alice"] = 30 };
var uniqueNumbers = new HashSet<int> { 1, 2, 2, 3 }; // {1,2,3}
var queue = new Queue<string>();
queue.Enqueue("First"); queue.Enqueue("Second");
```

**Learning Tip:**  
Choose the right collection for the job—performance and correctness depend on it.

---
## 9. Exception Handling

### Q28. **How do you handle exceptions in C#?**

**Explanation:**  
Exceptions are handled using `try`, `catch`, and `finally` blocks.  
- `try`: Place code that may throw exceptions.
- `catch`: Handle specific or general exceptions; multiple `catch` blocks for different exception types.
- `finally`: Code here always runs (for cleanup), regardless of success or error.

**Example:**  
```csharp
try
{
    int num = int.Parse("not a number");
}
catch (FormatException ex)
{
    Console.WriteLine($"Format error: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Unexpected error: {ex.Message}");
}
finally
{
    Console.WriteLine("Cleanup or logging here.");
}
```

**Learning Tip:**  
Always catch the most specific exceptions first. Use `finally` for resource cleanup (e.g., closing files, releasing DB connections).

---

### Q29. **What is the difference between `throw` and `throw ex`? Which should you use?**

**Explanation:**  
- `throw ex;` resets the stack trace, losing the original error context.
- `throw;` preserves the original stack trace, making debugging much easier.

**Example:**  
```csharp
try
{
    // Some risky code
}
catch (Exception ex)
{
    // Bad: throw ex; // Stack trace lost
    throw; // Good: stack trace preserved
}
```

**Learning Tip:**  
Always use `throw;` (without a variable) to rethrow exceptions.

---

### Q30. **What are custom exceptions? How do you create one?**

**Explanation:**  
Custom exceptions allow you to represent domain-specific errors clearly. Inherit from `Exception` and provide constructors.

**Example:**  
```csharp
public class InsufficientFundsException : Exception
{
    public InsufficientFundsException(string message) : base(message) { }
}

// Usage
if (balance < withdrawal)
    throw new InsufficientFundsException("Not enough funds to withdraw.");
```

**Learning Tip:**  
Use custom exceptions for meaningful, domain-specific error handling.

---

### Q31. **What is the `finally` block? When should you use it?**

**Explanation:**  
The `finally` block always executes, whether or not an exception is thrown.  
Best for cleaning up resources: closing files, releasing locks, etc.

**Example:**  
```csharp
FileStream? file = null;
try
{
    file = File.Open("data.txt", FileMode.Open);
    // ...read/write...
}
finally
{
    file?.Dispose();
}
```

**Learning Tip:**  
Prefer `using` statements for resource management, but use `finally` for cleanup if `using` isn’t possible.

---

### Q32. **What is the difference between `finally` and `Finalize`?**

| Feature           | `finally`                        | `Finalize` (destructor)                   |
|-------------------|----------------------------------|-------------------------------------------|
| Usage             | In exception handling blocks      | As a class destructor (`~ClassName()`)    |
| Purpose           | Cleanup after try/catch          | Cleanup before object is garbage collected|
| When called       | Always after try/catch           | By GC, non-deterministic                  |

**Example:**  
```csharp
// finally
try { ... } finally { ... }

// Finalize (destructor)
class Demo { ~Demo() { /* cleanup code */ } }
```

**Learning Tip:**  
Use `finally` for deterministic cleanup. Rely on finalizers (`~ClassName()`) only for rare unmanaged resource cleanup.

---

### Q33. **What is the `using` statement? Why is it important?**

**Explanation:**  
The `using` statement ensures that objects implementing `IDisposable` are disposed automatically after use, even if an exception occurs.  
Critical for releasing file handles, database connections, etc.

**Example:**  
```csharp
using (var stream = new FileStream("myfile.txt", FileMode.Open))
{
    // Use the stream
}
// stream.Dispose() called automatically, even if an exception is thrown
```

**Learning Tip:**  
Prefer `using` for all I/O, DB, and network resources. In C# 8+, use `using var` for even simpler syntax.

---

### Q34. **How do you create a custom resource cleanup using `IDisposable`?**

**Explanation:**  
Implement the `IDisposable` interface and define the `Dispose()` method for your class.

**Example:**  
```csharp
public class ResourceHolder : IDisposable
{
    private bool disposed = false;
    public void Dispose()
    {
        if (!disposed)
        {
            // Clean up resources here
            disposed = true;
        }
        GC.SuppressFinalize(this);
    }
    ~ResourceHolder() => Dispose();
}
```

**Learning Tip:**  
Always call `GC.SuppressFinalize(this)` in `Dispose()` if you have a finalizer to avoid double cleanup.

---

### Q35. **What is exception bubbling?**

**Explanation:**  
Exception bubbling is the process of propagating an exception up the call stack until it’s caught by a suitable `catch` block or reaches the top level and crashes the application.

**Example:**  
```csharp
void A() => B();
void B() => C();
void C() => throw new InvalidOperationException("Error!");

try { A(); }
catch (InvalidOperationException ex) { Console.WriteLine(ex.Message); } // Caught here
```

**Learning Tip:**  
Handle exceptions as close to the source as practical, or bubble up to a central handler (e.g., for logging).

---

## 10. ASP.NET Core & MVC

### Q36. **What is ASP.NET Core? What are its main advantages?**

**Explanation:**  
ASP.NET Core is a cross-platform, high-performance open-source framework for building modern, cloud-based, and internet-connected web applications.

**Key advantages:**
- Cross-platform (Windows, Linux, macOS)
- Unified web API and MVC framework
- Built-in dependency injection
- High performance and lightweight
- Modular middleware pipeline

**Example:**  
```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers();
var app = builder.Build();

app.MapControllers();
app.Run();
```

**Learning Tip:**  
Use ASP.NET Core for all new web projects—legacy ASP.NET Framework is only for maintenance.

---

### Q37. **Explain the MVC pattern. How does ASP.NET Core MVC implement it?**

**Explanation:**  
MVC stands for **Model-View-Controller**:
- **Model:** Represents application data and business logic.
- **View:** Handles UI and presentation.
- **Controller:** Handles user requests, manipulates model, returns view.

**ASP.NET Core MVC** uses routing to map URLs to controller actions, binds data to models, and renders views using Razor templates.

**Example:**  
```csharp
// Controller
public class ProductsController : Controller
{
    public IActionResult Index() => View(GetProducts());
}

// View (Index.cshtml)
@model IEnumerable<Product>
@foreach(var product in Model) { <p>@product.Name</p> }
```

**Learning Tip:**  
Understand separation of concerns—keep business logic out of controllers and views.

---

### Q38. **What is middleware in ASP.NET Core? Give examples.**

**Explanation:**  
Middleware are software components that handle HTTP requests and responses in the ASP.NET Core pipeline.

**Common Middleware:**
- Authentication/Authorization
- Logging
- Exception handling
- Routing
- Static files

**Example:**  
```csharp
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.UseEndpoints(endpoints => endpoints.MapControllers());
```

**Learning Tip:**  
Middleware order matters—requests flow through in registration order.

---

### Q39. **How does dependency injection work in ASP.NET Core?**

**Explanation:**  
Dependency Injection (DI) is built-in in ASP.NET Core. Register services in `Program.cs` or `Startup.cs`, and inject them via constructors.

**Example:**  
```csharp
builder.Services.AddScoped<IMyService, MyService>();

public class HomeController : Controller
{
    private readonly IMyService _service;
    public HomeController(IMyService service) => _service = service;
}
```

**Learning Tip:**  
Use constructor injection for testability and loose coupling.

---

### Q40. **What are the lifetimes of services in ASP.NET Core DI?**

| Lifetime    | Description                                  | Example                                                      |
|-------------|----------------------------------------------|--------------------------------------------------------------|
| Singleton   | One instance for the entire app              | `AddSingleton<IMyService, MyService>()`                      |
| Scoped      | One instance per HTTP request                | `AddScoped<IMyService, MyService>()`                         |
| Transient   | New instance each time requested             | `AddTransient<IMyService, MyService>()`                      |

**Learning Tip:**  
Use Singleton for stateless, shared services. Scoped for per-request logic (e.g., DB context). Transient for light, stateless objects.

---

## 11. Entity Framework & Data Access

### Q41. **What is Entity Framework (EF)? Why is it popular in .NET?**

**Explanation:**  
Entity Framework is an object-relational mapper (ORM) for .NET. It allows developers to work with relational databases using .NET objects, eliminating most SQL boilerplate.  
EF supports LINQ queries, change tracking, migrations, and code-first or database-first approaches.

**Example:**  
```csharp
public class SchoolContext : DbContext
{
    public DbSet<Student> Students { get; set; }
}

using var context = new SchoolContext();
context.Students.Add(new Student { Name = "Alice" });
context.SaveChanges();
```

**Learning Tip:**  
Use EF for rapid development and maintainability. For performance-critical code, consider Dapper or raw SQL.

---

### Q42. **What are Code First, Database First, and Model First approaches in EF?**

| Approach      | Description                                                   | When to Use                          |
|---------------|---------------------------------------------------------------|--------------------------------------|
| Code First    | Define C# classes; EF generates DB schema                     | Greenfield projects, domain-driven   |
| Database First| Start from existing DB; generate C# classes                   | Legacy databases, reverse engineering|
| Model First   | Design visual model; EF generates code and DB schema          | Rare now, but good for visual modeling |

**Learning Tip:**  
Code First is modern default in .NET Core.

---

### Q43. **What is a DbContext? What is a DbSet?**

**Explanation:**  
- **DbContext**: The primary class for interacting with a database in EF. It manages entity objects, database connections, and change tracking.
- **DbSet<T>**: Represents a table in the database and provides methods for CRUD operations.

**Example:**  
```csharp
public class BloggingContext : DbContext
{
    public DbSet<Blog> Blogs { get; set; }
}
```

**Learning Tip:**  
Use one DbContext per logical unit of work (usually per HTTP request in web apps).

---

### Q44. **How do you query data using LINQ with EF?**

**Example:**  
```csharp
using var db = new BloggingContext();
var activeBlogs = db.Blogs.Where(b => b.IsActive).OrderBy(b => b.Name).ToList();
```

**Learning Tip:**  
LINQ queries on DbSet are translated to SQL and executed in the database for efficiency.

---

### Q45. **What is migration in Entity Framework?**

**Explanation:**  
Migrations allow you to evolve your database schema in sync with your C# model changes.  
EF Core command-line tools (`dotnet ef migrations add <Name>`, `dotnet ef database update`) manage this process.

**Example:**  
```bash
dotnet ef migrations add AddBirthdateToUser
dotnet ef database update
```

**Learning Tip:**  
Always review generated migrations before applying to production.

---

### Q46. **Explain lazy loading, eager loading, and explicit loading in EF.**

| Loading Type   | Description                                  | Code Example                                  |
|----------------|----------------------------------------------|-----------------------------------------------|
| Lazy Loading   | Loads related data when accessed             | `virtual` nav properties, needs proxies       |
| Eager Loading  | Loads related data up front (`Include`)      | `db.Blogs.Include(b => b.Posts)`              |
| Explicit       | Manually load related data                   | `db.Entry(blog).Collection(b => b.Posts).Load()`|

**Learning Tip:**  
Prefer eager loading for performance-critical, predictable queries. Lazy loading can cause N+1 query issues.

---

### Q47. **What is the difference between `First`, `FirstOrDefault`, `Single`, and `SingleOrDefault` in LINQ/EF?**

| Method           | Throws if not found? | Throws if multiple? | Returns default if not found?  |
|------------------|---------------------|---------------------|-------------------------------|
| First            | Yes                 | No                  | No                            |
| FirstOrDefault   | No                  | No                  | Yes                           |
| Single           | Yes                 | Yes                 | No                            |
| SingleOrDefault  | No                  | Yes                 | Yes                           |

**Example:**  
```csharp
var user = db.Users.FirstOrDefault(u => u.Email == "a@b.com");
```

**Learning Tip:**  
Use `Single`/`SingleOrDefault` only when exactly one match is guaranteed.

---

### Q48. **How do you execute raw SQL queries in EF Core?**

**Example:**  
```csharp
var users = db.Users.FromSqlRaw("SELECT * FROM Users WHERE IsActive = 1").ToList();
```

**Learning Tip:**  
Use raw SQL for complex queries or performance tuning, but prefer LINQ for maintainability.

---

### Q49. **What is change tracking in Entity Framework?**

**Explanation:**  
Change tracking is the process of automatically keeping track of changes (add, modify, delete) to entities so EF can generate correct SQL commands on `SaveChanges()`.

**Example:**  
```csharp
var user = db.Users.Find(1);
user.Name = "New Name";
db.SaveChanges(); // EF updates only changed properties
```

**Learning Tip:**  
Be mindful of memory—DbContext tracks all loaded entities.

---

### Q50. **What is Dapper and how does it compare to Entity Framework?**

**Explanation:**  
Dapper is a lightweight, high-performance micro-ORM for .NET. It focuses on raw SQL queries and manual mapping, making it much faster than EF for simple scenarios, but without change tracking or LINQ.

**Example:**  
```csharp
using var conn = new SqlConnection(connectionString);
var users = conn.Query<User>("SELECT * FROM Users WHERE IsActive = 1").ToList();
```

**Learning Tip:**  
Use Dapper for read-heavy or performance-critical code; use EF for rapid development and complex object graphs.

---
## 12. Web API, REST & Microservices

### Q51. **What is ASP.NET Web API? How is it different from MVC?**

**Explanation:**  
ASP.NET Web API is a framework for building HTTP-based RESTful services.  
- Web API focuses on returning data (JSON, XML), while MVC is mainly for returning views (HTML).
- Web API controllers inherit from `ApiController`, MVC from `Controller`.

**Example:**  
```csharp
// Web API Controller
[ApiController]
[Route("api/[controller]")]
public class BooksController : ControllerBase
{
    [HttpGet]
    public IEnumerable<Book> GetAll() => repo.GetAll();
}
```

**Learning Tip:**  
Use Web API for building APIs to serve mobile apps, SPAs, or other services.

---

### Q52. **What is REST? What are RESTful services?**

**Explanation:**  
REST (Representational State Transfer) is an architectural style for distributed systems.  
RESTful services:
- Use standard HTTP verbs (`GET`, `POST`, `PUT`, `DELETE`)
- Are stateless
- Expose resources via URLs
- Support multiple formats (JSON, XML)

**Example:**  
```http
GET /api/products
POST /api/products
GET /api/products/5
```

**Learning Tip:**  
Design REST APIs with nouns (resources), not verbs, in endpoints.

---

### Q53. **How do you implement routing in Web API?**

**Explanation:**  
Routing maps HTTP requests to controller actions. In ASP.NET Core Web API, attribute routing is commonly used.

**Example:**  
```csharp
[Route("api/[controller]")]
public class OrdersController : ControllerBase
{
    [HttpGet("{id}")]
    public IActionResult GetOrder(int id) { ... }
}
```

**Learning Tip:**  
Use `[Route]` and `[HttpGet]`, `[HttpPost]`, etc., to clearly define RESTful routes.

---

### Q54. **How do you secure a Web API?**

**Explanation:**  
Common security methods:
- HTTPS (always!)
- Authentication (e.g., JWT, OAuth, API keys)
- Authorization (roles, policies)
- Input validation & rate limiting

**Example:**  
```csharp
[Authorize(Roles = "Admin")]
[HttpDelete("{id}")]
public IActionResult DeleteUser(int id) { ... }
```

**Learning Tip:**  
Always validate input. Never trust data from clients—even authenticated ones.

---

### Q55. **What is CORS and why is it important for Web APIs?**

**Explanation:**  
CORS (Cross-Origin Resource Sharing) is a security feature in browsers blocking requests from different origins by default.  
APIs must explicitly allow cross-origin requests.

**Example:**  
```csharp
// In Program.cs or Startup.cs
builder.Services.AddCors(options =>
{
    options.AddPolicy("OpenPolicy", policy =>
        policy.AllowAnyOrigin().AllowAnyHeader().AllowAnyMethod());
});
app.UseCors("OpenPolicy");
```

**Learning Tip:**  
Always configure CORS policies as strictly as your use-case allows.

---

### Q56. **What is Swagger/OpenAPI? How does it help in Web API development?**

**Explanation:**  
Swagger (now OpenAPI) is a specification and set of tools for describing, documenting, and testing REST APIs.  
- Auto-generates interactive docs
- Enables client SDK generation
- Helps with API lifecycle management

**Example:**  
```csharp
// In Program.cs
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
app.UseSwagger();
app.UseSwaggerUI();
```

**Learning Tip:**  
Always provide Swagger for your APIs—it accelerates onboarding and testing.

---

### Q57. **What is versioning in Web API? Techniques to implement it?**

**Explanation:**  
API versioning allows you to evolve APIs without breaking existing clients.  
Common techniques:
- URL versioning (`/api/v1/products`)
- Query string (`?api-version=1.0`)
- HTTP header (`X-Version: 1.0`)

**Example:**  
```csharp
[ApiVersion("1.0")]
[Route("api/v{version:apiVersion}/[controller]")]
public class ProductsController : ControllerBase { ... }
```

**Learning Tip:**  
Start with versioning even if you only have one version.

---

### Q58. **What is a microservices architecture?**

**Explanation:**  
A software design pattern where an application is composed of small, independent services communicating over APIs.  
Each service:
- Is independently deployable
- Owns its data
- Can be scaled and updated separately

**Learning Tip:**  
Microservices solve organizational and scaling problems, but add operational complexity.

---

### Q59. **What is an API Gateway? Why is it used in microservices?**

**Explanation:**  
An API Gateway is a single entry point for clients to access multiple backend services.  
Responsibilities:
- Request routing
- Aggregation
- Authentication/authorization
- Rate limiting

**Learning Tip:**  
Popular gateways: Ocelot (.NET), Kong, NGINX, Azure API Management.

---

### Q60. **How do microservices discover each other?**

**Explanation:**  
Service discovery enables dynamic lookup of microservice endpoints.  
- Centralized registry (e.g., Consul, Eureka)
- DNS-based discovery
- Platform-based (e.g., Kubernetes internal DNS)

**Learning Tip:**  
Without service discovery, microservices can’t scale or survive restarts reliably.

---

## 13. Cloud, Docker & Kubernetes

### Q61. **What is Docker, and how is it used for .NET applications?**

**Explanation:**  
Docker is a containerization platform. It packages applications and dependencies into containers for consistent, isolated deployment.

**Example:**  
```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:8.0
COPY . /app
WORKDIR /app
ENTRYPOINT ["dotnet", "MyApp.dll"]
```

**Learning Tip:**  
Use Docker for reproducible builds, easy scaling, and cross-environment consistency.

---

### Q62. **What is Kubernetes, and how does it relate to Docker?**

**Explanation:**  
Kubernetes is a container orchestration platform.  
- Manages deployment, scaling, and networking of containers (usually Docker).
- Provides self-healing, load balancing, rolling updates.

**Learning Tip:**  
Kubernetes is the de facto standard for running microservices at scale in the cloud.

---

### Q63. **What is Azure App Service?**

**Explanation:**  
A Platform-as-a-Service (PaaS) for hosting web apps, REST APIs, and mobile backends in Azure.  
- Handles scaling, patching, backups, and monitoring
- Supports .NET, Java, Node.js, Python, PHP, and more

**Example:**  
Deploy with `az webapp up` or via GitHub Actions.

**Learning Tip:**  
App Service is a good choice for most .NET web workloads needing easy deployment and scaling.

---

### Q64. **What is Continuous Integration (CI) and Continuous Deployment (CD)?**

**Explanation:**  
- **CI:** Automatically building and testing code with every commit, ensuring early bug detection.
- **CD:** Automatically deploying code to production after passing tests.

**Example:**  
- GitHub Actions, Azure Pipelines, GitLab CI.

**Learning Tip:**  
Automate as much as possible—manual deployments are error-prone.

---

### Q65. **What is Infrastructure as Code (IaC)?**

**Explanation:**  
IaC means defining and managing infrastructure (servers, networks, DBs) using code, enabling repeatable, consistent, and versioned deployments.

**Example:**  
- Bicep/ARM templates (Azure), Terraform (multi-cloud), Pulumi (.NET support).

**Learning Tip:**  
Treat infrastructure like source code—commit, review, and deploy via pipelines.

---

## 14. Design Patterns & SOLID Principles

### Q66. **What are design patterns? Why are they important?**

**Explanation:**  
Design patterns are proven solutions to common software design problems. They enhance code reuse, flexibility, and communication among developers.

**Categories:**  
- Creational (e.g., Singleton, Factory)
- Structural (e.g., Adapter, Decorator)
- Behavioral (e.g., Observer, Strategy)

**Learning Tip:**  
Patterns are guidelines, not rules—apply them judiciously.

---

### Q67. **What are the SOLID principles?**

| Principle   | Description                                               | Example/Benefit           |
|-------------|-----------------------------------------------------------|---------------------------|
| S: Single Responsibility | Class should have only one reason to change      | Easier maintenance        |
| O: Open/Closed           | Open for extension, closed for modification     | Add features, don’t break|
| L: Liskov Substitution   | Derived types replace base types everywhere     | Safe polymorphism         |
| I: Interface Segregation | No client should depend on unused interfaces    | Smaller interfaces        |
| D: Dependency Inversion  | Depend on abstractions, not concretions         | Easier testing, swapping  |

**Example:**  
```csharp
public interface ILogger { void Log(string message); }
public class FileLogger : ILogger { ... }
public class Service
{
    private readonly ILogger _logger;
    public Service(ILogger logger) { _logger = logger; }
    // Depends on abstraction (ILogger)
}
```

**Learning Tip:**  
Review your code for violations—SOLID code is easier to test, scale, and refactor.

---

### Q68. **What is the Singleton pattern? Show a thread-safe implementation.**

**Explanation:**  
Singleton ensures a class has only one instance and provides a global point of access.

**Example:**  
```csharp
public sealed class Singleton
{
    private static readonly Lazy<Singleton> _instance = new(() => new Singleton());
    public static Singleton Instance => _instance.Value;
    private Singleton() { }
}
```

**Learning Tip:**  
The `Lazy<T>` approach is preferred in modern C#.

---

### Q69. **What is the Factory pattern? Why use it?**

**Explanation:**  
Factory pattern delegates object creation to a factory class rather than calling `new` directly.  
- Hides concrete type
- Centralizes creation logic
- Supports open/closed principle

**Example:**  
```csharp
public interface IAnimal { void Speak(); }
public class Dog : IAnimal { public void Speak() => Console.WriteLine("Bark"); }
public class Cat : IAnimal { public void Speak() => Console.WriteLine("Meow"); }

public static class AnimalFactory
{
    public static IAnimal Create(string type) => type switch
    {
        "dog" => new Dog(),
        "cat" => new Cat(),
        _ => throw new ArgumentException("Unknown type")
    };
}
```

**Learning Tip:**  
Use factories when object creation is complex, or you want to decouple consumers from implementations.

---

### Q70. **What is Dependency Injection? How is it related to Inversion of Control (IoC)?**

**Explanation:**  
Dependency Injection is a technique where dependencies are provided from outside the class, not created within.  
IoC is the broader principle; DI is a way to implement it.

**Example:**  
```csharp
public class OrderService
{
    private readonly IPaymentProcessor _paymentProcessor;
    public OrderService(IPaymentProcessor processor) { _paymentProcessor = processor; }
}
```

**Learning Tip:**  
DI enables loose coupling, testability, and adherence to SOLID.

---

## 15. Testing, CI/CD & Modern DevOps

### Q71. **What is unit testing? How do you write tests in .NET?**

**Explanation:**  
Unit testing verifies individual units (methods/classes) of code in isolation.  
Popular frameworks: xUnit, NUnit, MSTest.

**Example:**  
```csharp
public class MathUtils
{
    public int Add(int a, int b) => a + b;
}

// xUnit test
public class MathUtilsTests
{
    [Fact]
    public void Add_ReturnsSum()
    {
        var utils = new MathUtils();
        Assert.Equal(5, utils.Add(2, 3));
    }
}
```

**Learning Tip:**  
Write tests for all business logic. Use dependency injection and mocking for isolation.

---

### Q72. **What is mocking? Why is it useful for testing?**

**Explanation:**  
Mocking creates fake objects to simulate dependencies, allowing you to test units in isolation.

**Example:**  
```csharp
var mockRepo = new Mock<IRepository>();
mockRepo.Setup(r => r.GetUser(It.IsAny<int>())).Returns(new User { Id = 1 });

var service = new UserService(mockRepo.Object);
Assert.Equal(1, service.GetUser(1).Id);
```

**Learning Tip:**  
Use mocking for external systems, DBs, APIs, and anything slow or non-deterministic.

---

### Q73. **What is Continuous Integration (CI)? Why is it important?**

**Explanation:**  
CI is the process of automatically building and testing code with every commit.  
It:
- Catches bugs early
- Encourages small, frequent commits
- Keeps code always in a deployable state

**Learning Tip:**  
Set up CI with GitHub Actions, Azure Pipelines, or equivalent as soon as a project starts.

---

### Q74. **What is Continuous Deployment (CD)?**

**Explanation:**  
CD automates the deployment of code to production after passing all tests and checks in CI.

**Example:**  
- Deploy to Azure App Service using GitHub Actions on every push to `main`.

**Learning Tip:**  
Aim for “push to prod” automation, but use staged environments and approvals for safety.

---

### Q75. **What is code coverage? Why does it matter?**

**Explanation:**  
Code coverage measures the percentage of your code that is tested by automated tests.  
High coverage means fewer untested paths, but 100% coverage does not guarantee bug-free code.

**Learning Tip:**  
Focus on meaningful coverage of business logic—don’t obsess over trivial getters/setters.

---

## 16. Bonus Advanced Topics & Real-World Scenarios

### Q76. **What is CQRS (Command Query Responsibility Segregation)?**

**Explanation:**  
CQRS is a pattern where you separate the read (query) and write (command) operations of your application into distinct models.  
- Queries never change state and are optimized for reading.
- Commands change state and are optimized for writes.
- Useful in large systems for scaling, security, and performance.

**Example:**  
- Queries: `GetOrderById`, `ListOrders`
- Commands: `CreateOrder`, `CancelOrder`

**Learning Tip:**  
Use CQRS when read and write workloads are very different, or you need independent scaling or security.

---

### Q77. **What is Event Sourcing?**

**Explanation:**  
Event Sourcing is a pattern where state changes are stored as a sequence of events.  
- The current state is rebuilt by replaying all events.
- Provides a full audit log and enables time-travel/debugging.
- Common in conjunction with CQRS.

**Example:**  
Instead of just storing the latest account balance, you store every `DepositMade` and `WithdrawalMade` event.

**Learning Tip:**  
Event sourcing adds complexity—use only when you need an audit trail or advanced analytics.

---

### Q78. **What is SignalR? Use cases in .NET?**

**Explanation:**  
SignalR is a library for real-time web functionality—enabling server code to push updates to connected clients instantly (e.g., chat, live dashboards, notifications).

**Example:**  
```csharp
public class ChatHub : Hub
{
    public async Task SendMessage(string user, string message)
        => await Clients.All.SendAsync("ReceiveMessage", user, message);
}
```

**Learning Tip:**  
Use SignalR for real-time collaboration, notifications, or live data feeds in web apps.

---

### Q79. **What is Blazor? Differences between Blazor Server and Blazor WebAssembly?**

**Explanation:**  
Blazor is a .NET framework for building interactive web UIs with C# instead of JavaScript.

| Blazor Server        | Blazor WebAssembly         |
|----------------------|---------------------------|
| Runs on server; UI updates via SignalR | Runs in browser via WebAssembly |
| Fast startup, .NET runtime on server   | True client-side execution      |
| Dependent on connection                | Offline support possible        |

**Learning Tip:**  
Blazor WebAssembly is best for rich, client-side apps; Blazor Server is great for intranets or low-latency networks.

---

### Q80. **What is gRPC and why use it in .NET?**

**Explanation:**  
gRPC is a modern, high-performance, contract-first RPC framework that uses Protocol Buffers for serialization.  
- Enables cross-language, strongly-typed APIs.
- Used for fast service-to-service communication (microservices, cloud).

**Example:**  
Define a service in a `.proto` file; gRPC tools generate C# client and server code.

**Learning Tip:**  
Use gRPC for high-throughput, low-latency, strongly-typed APIs between services.

---

### Q81. **What is Health Check in ASP.NET Core?**

**Explanation:**  
Health Checks provide endpoints to monitor the health and readiness of an app and its dependencies (DB, cache, etc.).

**Example:**  
```csharp
builder.Services.AddHealthChecks()
    .AddSqlServer(connectionString);

app.MapHealthChecks("/health");
```

**Learning Tip:**  
Health checks help orchestrators (Kubernetes, Azure) auto-restart failing apps.

---

### Q82. **What is logging in .NET Core? Popular logging frameworks?**

**Explanation:**  
Logging records information about app execution (errors, info, diagnostics) for monitoring and troubleshooting.

**Built-in logging:**  
- `ILogger<T>` via dependency injection
- Providers: Console, Debug, Azure, etc.

**Popular frameworks:**  
- Serilog (structured logging)
- NLog
- log4net

**Example:**  
```csharp
public class HomeController
{
    private readonly ILogger<HomeController> _logger;
    public HomeController(ILogger<HomeController> logger) => _logger = logger;
    public IActionResult Index() { _logger.LogInformation("Visited Index."); return View(); }
}
```

**Learning Tip:**  
Use structured logging (Serilog) for easier querying and analysis.

---

### Q83. **What is MediatR and where is it useful?**

**Explanation:**  
MediatR is a .NET library for the Mediator pattern.  
- Decouples request/response, notification, and command/query logic.
- Useful for CQRS, clean architecture, modular code.

**Example:**  
```csharp
public record CreateOrderCommand(string ProductId) : IRequest<Order>;
public class Handler : IRequestHandler<CreateOrderCommand, Order> { ... }
```

**Learning Tip:**  
Use MediatR to centralize logic and decouple application layers.

---

### Q84. **What is the difference between synchronous and asynchronous programming in .NET?**

**Explanation:**  
- Synchronous: Code runs sequentially, blocking until each operation completes.
- Asynchronous: Code can continue executing while awaiting time-consuming operations (I/O, DB, network).

**Example:**  
```csharp
public async Task<string> FetchDataAsync()
{
    using var client = new HttpClient();
    return await client.GetStringAsync("https://api.example.com/data");
}
```

**Learning Tip:**  
Use `async`/`await` for I/O-bound operations—never block the main/UI thread.

---

### Q85. **How do you use configuration in .NET Core?**

**Explanation:**  
.NET Core uses `appsettings.json`, environment variables, and other sources for configuration.  
Strongly-typed configuration is recommended for safety and IntelliSense.

**Example:**  
```csharp
// appsettings.json
{
  "MyAppSettings": { "ApiUrl": "https://api.example.com" }
}

// Program.cs
builder.Services.Configure<MyAppSettings>(builder.Configuration.GetSection("MyAppSettings"));

public class MyAppSettings { public string ApiUrl { get; set; } }
```

**Learning Tip:**  
Bind configuration to strongly-typed classes for clarity and safety.

---

### Q86. **What is null-coalescing operator (`??`) and null-conditional operator (`?.`)?**

**Explanation:**  
- `??`: Returns left operand if not null, else right.
- `?.`: Calls a member only if the object is not null.

**Example:**  
```csharp
string? name = null;
string displayName = name ?? "Guest"; // "Guest"

int? length = name?.Length; // null
```

**Learning Tip:**  
Use these operators to simplify null checks and avoid `NullReferenceException`.

---

### Q87. **What is a value type vs. reference type? Give examples.**

| Value Type                | Reference Type             |
|---------------------------|---------------------------|
| Stores actual data        | Stores reference to data  |
| Allocated on stack        | Allocated on heap         |
| Examples: int, double     | Examples: string, class   |

**Example:**  
```csharp
int x = 1;      // value type
string s = "hi"; // reference type
```

**Learning Tip:**  
Value types are faster for small, immutable data; reference types are used for objects and collections.

---

### Q88. **What is boxing and unboxing in C#?**

**Explanation:**  
- **Boxing:** Converts a value type to an object (reference).
- **Unboxing:** Converts an object back to a value type.

**Example:**  
```csharp
int num = 42;
object boxed = num;           // Boxing
int unboxed = (int)boxed;     // Unboxing
```

**Learning Tip:**  
Avoid boxing in performance-critical code (e.g., use generics instead of `ArrayList`).

---

### Q89. **What is a struct? When should you use a struct instead of a class?**

**Explanation:**  
- Structs are value types, immutable by default, and have value semantics.
- Use for small, simple data structures (e.g., `Point`, `DateTime`).

**Example:**  
```csharp
public struct Point { public int X { get; init; } public int Y { get; init; } }
var p = new Point { X = 3, Y = 4 };
```

**Learning Tip:**  
Use structs for lightweight objects that are frequently created and destroyed.

---

### Q90. **What is pattern matching in switch expressions?**

**Example:**  
```csharp
object shape = new { Radius = 5.0 };
string type = shape switch
{
    { Radius: > 1 } => "Large Circle",
    _ => "Unknown"
};
```

**Learning Tip:**  
Pattern matching is powerful for concise, readable code—especially with records.

---

## 17. Real Interview Scenarios & Troubleshooting

### Q91. **How do you troubleshoot a memory leak in a .NET application?**

**Explanation:**  
- Symptoms: Increasing memory usage, app slowing down or crashing over time.
- Techniques:
  - Use tools like Visual Studio Diagnostic Tools, dotMemory, or PerfView to analyze memory.
  - Look for objects that are not being garbage collected (e.g., static references, event handlers not unsubscribed).
  - Check for large object allocations, improper use of `IDisposable`, or collections growing indefinitely.

**Example:**  
```csharp
public class LeakyClass
{
    public static event Action? LeakyEvent;
    public void Subscribe() => LeakyEvent += OnEvent;
    private void OnEvent() { /* ... */ }
    // If not unsubscribed, instance will never be GC'd!
}
```

**Learning Tip:**  
Always unsubscribe from events and dispose resources when no longer needed.

---

### Q92. **How do you diagnose and fix a slow database query in a .NET/EF application?**

**Explanation:**  
- Use logging (e.g., EF Core logging) to capture the generated SQL.
- Analyze query execution plans in your database.
- Look for common issues: missing indexes, N+1 queries, large data loads, unnecessary includes.

**Example:**  
```csharp
// N+1 issue
var orders = db.Orders.ToList();
foreach (var order in orders)
    Console.WriteLine(order.Customer.Name); // Triggers separate query per order!
```
**Fix:**  
```csharp
// Eager load all customers in one query
var orders = db.Orders.Include(o => o.Customer).ToList();
```

**Learning Tip:**  
Use `.Include()` for eager loading, and query only what you need.

---

### Q93. **What steps would you take if a production .NET web app goes down?**

**Checklist:**  
1. Check monitoring/alerts for errors, logs, and CPU/memory usage.
2. Review recent deployments/releases.
3. Attempt to reproduce the issue in staging.
4. Rollback recent changes if necessary.
5. Communicate status to stakeholders.
6. Create a post-mortem to prevent recurrence.

**Learning Tip:**  
Always have monitoring, logging, and a rollback plan in place.

---

### Q94. **How do you secure sensitive configuration data (like connection strings) in .NET Core?**

**Explanation:**  
- Use [Azure Key Vault](https://learn.microsoft.com/azure/key-vault/general/basic-concepts), AWS Secrets Manager, or environment variables.
- Never commit secrets to source control.
- Use [User Secrets](https://learn.microsoft.com/aspnet/core/security/app-secrets) for development.

**Example:**  
```csharp
// appsettings.json
"ConnectionStrings": { "Default": "<do not store secrets here in production>" }
// In production, use environment variables or Key Vault
```

**Learning Tip:**  
Automate secret rotation and access audits.

---

### Q95. **How do you handle breaking changes in a public Web API?**

**Explanation:**  
- Use versioning (URL, header, or query string).
- Do not remove or change existing endpoints without notice.
- Mark old endpoints as deprecated.
- Communicate with consumers and provide migration guides.

**Learning Tip:**  
Always design APIs for evolution; breaking changes should be rare and well-communicated.

---

### Q96. **How would you implement rate limiting in an ASP.NET Core Web API?**

**Explanation:**  
- Use middleware (e.g., `AspNetCoreRateLimit` NuGet package).
- Limit requests per IP or API key over a time window.
- Return `429 Too Many Requests` when limit exceeded.

**Example:**  
```csharp
// Startup.cs
services.AddMemoryCache();
services.Configure<IpRateLimitOptions>(Configuration.GetSection("IpRateLimiting"));
services.AddInMemoryRateLimiting();
app.UseIpRateLimiting();
```

**Learning Tip:**  
Protects your APIs from abuse and helps manage resources.

---

### Q97. **How would you deploy a zero-downtime update to a .NET web application?**

**Explanation:**  
- Use rolling deployments or blue-green deployments.
- Load balancer routes traffic away from nodes being updated.
- Use health checks to ensure only healthy instances serve traffic.

**Learning Tip:**  
Cloud platforms (Azure, AWS, Kubernetes) offer built-in strategies for zero-downtime deploys.

---

### Q98. **What is a deadlock? How to avoid it in .NET?**

**Explanation:**  
A deadlock occurs when two or more threads are blocked forever, each waiting for the other to release a resource.

**Example:**  
```csharp
lock(obj1)
{
    lock(obj2)
    {
        // Do work...
    }
}
// Elsewhere, reversed order
lock(obj2)
{
    lock(obj1)
    {
        // Deadlock risk!
    }
}
```

**How to avoid:**  
- Always lock objects in the same order.
- Minimize lock scope.
- Prefer async/await (which doesn’t block threads) over locks where possible.

**Learning Tip:**  
Use concurrency analyzers and review code for locking patterns.

---

### Q99. **How do you handle time zone and date/time issues in global .NET applications?**

**Explanation:**  
- Store all date/time values in UTC in the database.
- Convert to local time only for display.
- Use `DateTimeOffset` for time zone-aware operations.
- Avoid `DateTime.Now`—prefer `DateTime.UtcNow`.

**Example:**  
```csharp
DateTime utcNow = DateTime.UtcNow;
DateTime local = TimeZoneInfo.ConvertTimeFromUtc(utcNow, TimeZoneInfo.FindSystemTimeZoneById("India Standard Time"));
```

**Learning Tip:**  
Time zones are complex—always test with edge cases (DST, leap years, etc.).

---

### Q100. **What are the most common mistakes to avoid in .NET interviews?**

**List:**
- Giving theoretical answers without practical context or code.
- Focusing only on syntax, ignoring architecture/design.
- Not mentioning security, error handling, or scalability.
- Failing to ask clarifying questions or discuss trade-offs.
- Ignoring testing, CI/CD, or DevOps aspects.

**Learning Tip:**  
Balance depth and breadth: be ready to code, design, troubleshoot, and explain your reasoning.

---

## 18. .NET Performance, Security & Best Practices

### Q101. **What are the best practices for improving performance in .NET applications?**

**Explanation:**  
- Use asynchronous programming (`async`/`await`) for I/O-bound operations.
- Minimize object allocations; reuse objects when possible.
- Avoid unnecessary boxing/unboxing and large object heap allocations.
- Use caching (in-memory, distributed) for frequently accessed data.
- Optimize data access: use pagination, avoid N+1 queries, prefer compiled LINQ queries for hot paths.
- Profile and measure performance using tools (dotTrace, PerfView, Visual Studio Profiler).

**Example:**  
```csharp
// Asynchronous data access
public async Task<User?> GetUserAsync(int id) =>
    await dbContext.Users.FindAsync(id);
```

**Learning Tip:**  
Always measure before optimizing. Use profiling tools to find real bottlenecks.

---

### Q102. **How do you secure a .NET web application against common vulnerabilities?**

| Threat                   | Mitigation Example                            |
|--------------------------|-----------------------------------------------|
| SQL Injection            | Use parameterized queries or EF LINQ          |
| Cross-Site Scripting     | Encode all user input in views                |
| Cross-Site Request Forgery| Use ASP.NET Core’s `[ValidateAntiForgeryToken]` |
| Sensitive Data Exposure  | HTTPS everywhere, encrypt sensitive data      |
| Authentication Bypass    | Use built-in authentication/authorization     |
| Dependency Vulnerabilities| Use Dependabot, audit packages, patch        |

**Example:**  
```csharp
// Parameterized query with Dapper
conn.Query("SELECT * FROM Users WHERE Name = @name", new { name = userInput });
```

**Learning Tip:**  
Adopt security by default: use HTTPS, strong authentication, and input validation everywhere.

---

### Q103. **How does garbage collection (GC) work in .NET?**

**Explanation:**  
- .NET GC automatically manages memory, releasing objects when no references remain.
- Operates in generations (0, 1, 2) for efficiency.
- GC is non-deterministic—use `IDisposable` for deterministic cleanup of unmanaged resources.

**Example:**  
```csharp
using (var conn = new SqlConnection(connStr))
{
    // Connection is disposed (and closed) at the end of the using block.
}
```

**Learning Tip:**  
Don’t force GC (`GC.Collect()`) unless you’re absolutely sure—it usually hurts performance.

---

### Q104. **What is thread safety? How do you achieve it in .NET?**

**Explanation:**  
Thread safety means code behaves correctly when accessed from multiple threads simultaneously.

**Techniques:**
- Use locks (`lock` statement), `Mutex`, or `Monitor` for critical sections.
- Prefer thread-safe collections (`ConcurrentDictionary`, `BlockingCollection`).
- Minimize shared state; prefer immutable objects.

**Example:**  
```csharp
private static readonly object _sync = new();
public void SafeIncrement()
{
    lock(_sync)
    {
        _counter++;
    }
}
```

**Learning Tip:**  
Immutability is the easiest way to achieve thread safety.

---

### Q105. **How do you handle configuration for multiple environments (dev, staging, prod) in .NET Core?**

**Explanation:**  
- Use `appsettings.{Environment}.json` files (e.g., `appsettings.Development.json`, `appsettings.Production.json`).
- Use environment variables to override settings.
- Inject configuration using `IConfiguration`.

**Example:**  
```csharp
// In Program.cs
var builder = WebApplication.CreateBuilder(args);
// config is automatically loaded from appsettings.json and environment-specific files
```

**Learning Tip:**  
Never store secrets in config files—use secure storage (Key Vault, environment variables).

---

### Q106. **What is role-based authorization in ASP.NET Core?**

**Explanation:**  
Restricts access to resources based on user roles.

**Example:**  
```csharp
[Authorize(Roles = "Admin")]
public IActionResult AdminPanel() => View();
```

**Learning Tip:**  
Use policies for more complex scenarios (claims-based, custom logic).

---

### Q107. **How do you implement logging and monitoring in production .NET apps?**

**Explanation:**  
- Use built-in `ILogger<T>` for structured logging.
- Integrate with log aggregators (Serilog, Seq, Application Insights, ELK Stack).
- Set up alerts and dashboards for error rates, performance, and usage metrics.

**Example:**  
```csharp
public class OrdersController
{
    private readonly ILogger<OrdersController> _logger;
    public OrdersController(ILogger<OrdersController> logger) => _logger = logger;

    public IActionResult Get(int id)
    {
        _logger.LogInformation("Fetching order {OrderId}", id);
        // ...
    }
}
```

**Learning Tip:**  
Correlate logs with trace IDs for distributed systems.

---

### Q108. **How do you use dependency injection for testing in .NET?**

**Explanation:**  
- Register interfaces with test doubles/mocks in the DI container.
- Swap production services for fakes in test configuration.

**Example:**  
```csharp
// In test setup
var services = new ServiceCollection();
services.AddScoped<IEmailSender, MockEmailSender>();
```

**Learning Tip:**  
Constructor injection makes code more testable than static/service locator patterns.

---

### Q109. **What’s the difference between synchronous and asynchronous exceptions?**

**Explanation:**  
- **Synchronous exceptions**: Thrown immediately in the current call stack.
- **Asynchronous exceptions**: Occur in async code, often surfaced via `Task` and must be awaited or observed.

**Example:**  
```csharp
try
{
    await SomeAsyncMethod();
}
catch (Exception ex)
{
    // Handles exceptions from awaited async code
}
```

**Learning Tip:**  
Always await async methods or handle exceptions via `.ContinueWith` or `TaskScheduler.UnobservedTaskException`.

---

### Q110. **What are some .NET code review best practices?**

**Checklist:**
- Enforce consistent naming, formatting, and style.
- Ensure all code paths are covered by tests.
- Validate input and output for every method.
- Keep methods small and focused.
- Document public APIs and complex logic.
- Remove dead code and unnecessary comments.
- Review for security, performance, and maintainability.

**Learning Tip:**  
Automate style, formatting, and static analysis with tools (EditorConfig, StyleCop, SonarQube).

---

## 19. .NET Interview Soft Skills, Leadership & Career Questions

### Q111. **How would you explain a complex technical concept to a non-technical stakeholder?**

**Explanation:**  
- Use analogies related to their business or everyday life.
- Avoid jargon—replace with simple terms.
- Focus on the “why” and business value, not just the “how”.
- Use visuals (diagrams, charts) if possible.

**Example:**  
_Explaining microservices:_  
“Think of microservices like a team of specialists in a company. Each person (service) is great at one thing, and they work together. If one is busy or out sick, the others can keep working.”

**Learning Tip:**  
Practice with a friend from a different background—ask if they truly understand.

---

### Q112. **What steps do you follow when starting a new .NET project?**

**Checklist:**  
1. Gather requirements and clarify scope.
2. Choose project type (Web API, MVC, Blazor, etc.).
3. Set up source control (e.g., Git, GitHub).
4. Establish coding standards and architecture (layered, DDD, clean architecture).
5. Set up CI/CD pipeline.
6. Define environments (dev, staging, prod).
7. Plan for security, testing, and monitoring.
8. Document setup and onboarding.

**Learning Tip:**  
Good planning and automation save time and headaches later.

---

### Q113. **How do you collaborate with other developers in .NET projects?**

**Best Practices:**  
- Use version control (Git) with clear branching/merging strategies (e.g., Git Flow).
- Write clear code reviews and accept feedback gracefully.
- Use pull requests for all changes.
- Communicate regularly (standups, chat, documentation).
- Share knowledge (pair programming, code reviews, brown-bag sessions).

**Learning Tip:**  
Technical skills get you hired; collaboration and communication get you promoted.

---

### Q114. **How do you handle disagreements in code reviews?**

**Explanation:**  
- Focus on facts and best practices, not personalities.
- Ask clarifying questions (“Can you help me understand why you chose this approach?”).
- Suggest alternatives with reasoning.
- Escalate only if consensus can’t be reached, and involve a neutral senior engineer.

**Learning Tip:**  
Stay professional—your goal is the best code, not to “win” the argument.

---

### Q115. **What are your strategies for continuous learning in .NET and software development?**

**Ideas:**  
- Follow Microsoft docs, .NET blog, and community leaders.
- Contribute to or review open-source projects.
- Take online courses (Pluralsight, Udemy, Microsoft Learn).
- Attend conferences, webinars, and user groups.
- Teach others—writing or presenting deepens your own understanding.

**Learning Tip:**  
Schedule regular time for learning—technology changes fast.

---

### Q116. **How do you prioritize tasks when working on a .NET project with tight deadlines?**

**Explanation:**  
- Identify critical path items—what must be done first for others to proceed?
- Break tasks into small, manageable pieces.
- Communicate early if something might block progress.
- Use tools (Azure DevOps, Jira, Trello) for visibility and tracking.
- Negotiate scope or deadlines if needed—never compromise on quality/security.

**Learning Tip:**  
Proactive communication and clear priorities prevent fire drills.

---

### Q117. **How do you mentor junior developers on .NET teams?**

**Best Practices:**  
- Pair programming and code reviews.
- Explain not just “what” but “why”.
- Assign progressively challenging tasks.
- Encourage asking questions and experimenting.
- Share recommended resources and learning paths.

**Learning Tip:**  
Empowering others multiplies your own impact.

---

### Q118. **What is the role of documentation in .NET projects?**

**Explanation:**  
- Enables onboarding of new team members.
- Reduces “bus factor” risk.
- Helps with maintenance and debugging.
- Should cover setup, architecture, APIs, and business logic.

**Learning Tip:**  
Treat documentation as part of “done”—not an afterthought.

---

### Q119. **What qualities make a successful .NET technical lead or architect?**

**Qualities:**  
- Deep technical knowledge AND big-picture thinking.
- Empathy for users and team members.
- Strong communication and decision-making skills.
- Ability to balance technical debt, deadlines, and business needs.
- Commitment to mentoring and growing the team.
- Advocates for best practices, security, and code quality.

**Learning Tip:**  
Great leads listen more than they speak and enable others to succeed.

---

### Q120. **How do you handle failure or mistakes in a .NET project?**

**Explanation:**  
- Own the mistake—don’t blame others.
- Communicate transparently with your team and stakeholders.
- Analyze the root cause and document lessons learned.
- Put in place processes or automation to prevent recurrence.
- Move forward—mistakes are learning opportunities.

**Learning Tip:**  
A culture that accepts and learns from mistakes is more resilient and innovative.

---

