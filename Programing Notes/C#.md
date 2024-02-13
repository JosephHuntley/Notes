# Best Practices

- Good Naming 
    - Project and solution names should be different.
    - End class libraries with library. E.g. DemoLibrary
    - Classes should be named singular. E.g. Person not People
- Only one class per file
- Use properties, not public fields 
- Method should only do one thing.
- KISS: Keep it stupidly simple
- Consistency
- Use curly braces for if statements
- Concatenate using "$"
- Use StringBuilder over string if you're concatenating with a loop
- Avoid global variables
- Use public only when necessary
- Never trust the user.
- Plan before you build
    - 5 Major Steps
        - Initialization
        - Planning
            - 
        - Executing
        - Monitoring
        - Closing

# .Net 

- Don't use string interpolation when you log. Instead, use structured logging.
- .Net Framework is a combination of a Common Language Runtime (CLR) and a Base Class Library (BCL).
- Roslyn is the C# complier used to compile code into intermediate language.
- Assembly is where the type is stored in the file system. They commonly end in `.dll` (Dynamic Link Library).
- The namespace is similar to an address to identify a type.
- .Net Framework is legacy and Windows only.
- .Net Core is Microsoft's effort to try and make .Net Framework cross-platform and decouple it from the Windows OS.
- .Net Core was renamed .Net and began with version 5.0 to prevent confusion with .Net Framework which ended with version 4.x.
- `sudo ~/dotnet-core-uninstall/dotnet-core-uninstall remove --all-previews-but-latest --sdk` Run to remove previous versions of .net
- Inside a code file, you should order the contents as shown in the following list:
    - External alias directives
    - Using directives
    - Namespaces
    - Delegates
    - Enums
    - Interfaces
    - Structs
    - Classes
- Within a class, record, struct, or interface, you should order the contents as shown in the following list:
    - Fields
    - Constructors
    - Destructors (finalizers)
    - Delegates
    - Events
    - Enums
    - Interfaces
    - Properties
    - Indexers
    - Methods
    - Structs
    - Nested classes and records
- Packages define APIs while a framework is a grouping of packages.
- Always check the target framework of a class library and then manually change it to something more appropriate if necessary. Make a conscious decision about what it should be rather than accepting the default.
- There are three ways to deploy a .Net application:
    - Framework-Dependent Deployment (FDD)
        - Requires .Net to be installed on the system.
        - Must be executed by the `dotnet` CLI
    - Framework-Dependent Executable (FDE)
        - Requires .Net to be installed on the system.
        - `.EXE` file
        - Can be ran from the command line.
    - Self Contained
        - Larger file but can run on any system including a USB Stick.
- Use `RuntimeIdentifier` for a single RID and `RuntimeIdentifiers` for multiple. 
- True single file apps can only be released on systems that already have .net.
- Add `<PublishTrimmed>true</PublishTrimmed>` to enable trimming and add `<TrimMode>Link</TrimMode>` as well if you want to enable type and method trimming as well.
- Almost always use fixed dependencies. e.g. `4.0.0` instead of `4.0.*`
- Configuration property values that are true or false values cannot have any whitespace, so the entry cannot have a carriage return and indentation.
- Cross-OS Support
    - ASP.NET Core websites, including Razor Pages and MVC
    - ASP.NET Core web services (REST/HTTP), including Web APIs, Minimal APIs, and OData
    - ASP.NET Core-hosted services, including gRPC, GraphQL, and SignalR
    - Console App command-line interfaces
    - Xamarin apps for mobile iOS and Android
    - .NET MAUI for desktop Windows and macOS, or mobile iOS and Android
- You can give `Random` a `Seed` value that can work as an unsecure secret key between applications.
- `Random` is not truly a random number. For true random numbers use `RandomNumberGenerator`.
- `StringBuilder` is better if you need to concatenate multiple strings together. When you use the `string` class you create multiple new strings in memory. 
- You can change the color of a string by using `StringSyntax(StringSyntaxAttribute.<Value>` flag
- `SecureString` removes the string from memory after finished using and encrypts it.
- Lambda functions `=>` are read as 'goes to' for instance `name => name.Length > 10` would be read aloud as name goes to name.length is greater than 10.
- You should create a separate class library project for your entity data models. This allows easier sharing between backend web servers and frontend desktop, mobile, and Blazor WebAssembly clients.

## Entity Framework 

- A Object-relational mapping (ORM) that is designed to work with relational DB.
- EF Core has been slimmed down and supports non-relational DB.
- EF 6.3 and later have been extracted from .NET Framework as a separate package, so it can be supported on .NET Core 3.0 and later.
- Only use legacy EF6 if you must; for example, when migrating a WPF app that uses it.
- EF Core 7 targets .NET 6 or later. This means that you can use all the new features of EF Core 7 with either .NET 6 or .NET 7.
- As well as traditional RDBMSs, EF Core supports modern cloud-based, nonrelational, schema-less data stores, such as Azure Cosmos DB and MongoDB, sometimes with third-party providers.
- There are two approaches to using EF
    - Database First: A database already exists, so you build a model that matches its structure and features.
    - Code First: No database exists, so you build a model and then use EF Core to create a database that matches its structure and features.
- `ADO.NET` is more efficient than EFCore for SQLlite. 
- Different SQL Versions require different EF packages:
    - `SQL Server 2012 or later` - Microsoft.EntityFrameworkCore.SqlServer
    - `SQLite 3.7 or later` - Microsoft.EntityFrameworkCore.SQLite
    - `In-memory` - Microsoft.EntityFrameworkCore.InMemory
    - `Azure Cosmos DB SQL API` - Microsoft.EntityFrameworkCore.Cosmos
    - `MySQL` - MySQL.EntityFrameworkCore
    - `Oracle DB 11.2` - Oracle.EntityFrameworkCore
    - `PostgreSQL` - Npgsql.EntityFrameworkCore.PostgreSQL
- Properties are assumed to match column names
- Property `Id` or `ID` is assumed to be the primary key. Along with `classNameId` and `classNameID`. If its the type or int or Guid type then it auto-increments.
- Annotations
    - `[Required]`: Not Null
    - `[StringLength(n)]`: Ensures the value is up to `n` characters in length.
    - `[RegularExpression(expression)]`: Ensures the value matches the specified regular expression.
    - `[Column(TypeName = "money", Name = "UnitPrice")]`: Specifies the column type and column name used in the table.
- Instead of property names you can use Fluent API
```c#
    modelBuilder.Entity<Product>()
    .Property(product => product.ProductName)
    .IsRequired()
    .HasMaxLength(40);
  ```
- Another benefit of the Fluent API is to provide initial data to populate a database. EF Core automatically works out what insert, update, or delete operations must be executed.
```c#
    modelBuilder.Entity<Product>()
    .HasData(new Product
    {
        ProductId = 1,
        ProductName = "Chai",
        UnitPrice = 8.99M
    });
```
- `DbSet<t>` Represents tables in EFCore.
- `OnModelCreating` Use in the `DbContext` derived class where you can write fluent api statements.
- `dotnet ef` can be used to auto generate classes for the tables and dbcontext.
    - Generates partial classes
    - Uses a tool named `Humanizer` to automatically singularize the class name.
    - `[InverseProperty]` attribute to define the foreign key relationship.
- `ModelConfigurationBuilder` to configure EFCore properties.
- Checking for “not any” by calling !products.Any() is more efficient than checking for a count of zero as shown in the following code: products.Count() == 0.
- `LogTo` requires an `Action<string>` delegate. EF Core will call this delegate, passing a string value for each log message.
    - Passing the Console class WriteLine method, therefore, tells the logger to write each method to the console. Note: The Console class is statically imported here therefore we can call the method with `WriteLine` instead of `Console.WriteLine`.
    ```c#
        optionsBuilder.LogTo(WriteLine) // Console
        .EnableSensitiveDataLogging();
    ```
- Filter LogTo messages by passing an array of output event Ids.
```c#
    optionsBuilder.LogTo(WriteLine, // Console
    new[] { RelationalEventId.CommandExecuting }) 
    .EnableSensitiveDataLogging();
```
- You can annotate a LINQ query using the TagWith method to add SQL comments to the log.
- You can use SQL Like function by using `EF.Functions.Like` in you LINQ query. 
- `EF.Functions.Random` to get a random number between 0 and 1.
- `HasQueryFilter` Can be used  in the `OnModelCreating` method to filter certain rows.
- `ExecuteUpdate` and `ExecuteDelete` are efficient ways t modify the db since it doesn't cause the data to be brought into memory before executing. 
- Don't mix `ExecuteUpdate` and `ExecuteDelete` with traditional `Update` and `Delete` as the change tracker will not know what you have updated and deleted using those methods.
- Every time you call the `SaveChanges` method, an implicit transaction is started so that if something goes wrong, it will automatically roll back all the changes. If the multiple changes within the transaction succeed, then the transaction and all changes are committed.
- Transactions are ACID, which is an acronym explained in the following list:
    - A is for atomic. Either all the operations in the transaction commit, or none of them do.
    - C is for consistent. The state of the database before and after a transaction is consistent. This is dependent on your code logic; for example, when transferring money between bank accounts, it is up to your business logic to ensure that if you debit $100 from one account, you credit $100 to the other account.
    - I is for isolated. During a transaction, changes are hidden from other processes. There are multiple isolation levels that you can pick from (refer to the following table). The stronger the level, the better the integrity of the data. However, more locks must be applied, which will negatively affect other processes. Snapshot is a special case because it creates multiple copies of rows to avoid locks, but this will increase the size of your database while transactions occur.
    - D is for durable. If a failure occurs during a transaction, it can be recovered. This is often implemented as a two-phase commit and transaction logs. Once the transaction is committed, it is guaranteed to endure even if there are subsequent errors. The opposite of durable is volatile.
- Transaction types
    - ReadUncommitted: 
        - No Locks
        - Dirty reads, non-repeatable reads, and phantom data
    - ReadCommitted
        - When editing, it applies read lock(s) to block other users from reading the record(s) until the transaction ends
        - Non-repeatable reads and phantom data
    - RepeatableRead
        - When reading, it applies edit lock(s) to block other users from editing the record(s) until the transaction ends
        - Phantom data
    - Serializable
        - It applies key-range locks to prevent any action that would affect the results, including inserts and deletes
        - None
    - Snapshot
        - None
        - None
- You should always order data before calling Skip and Take if you want to implement paging. This is because each time you execute a query, the LINQ provider does not have to guarantee to return the data is in the same order unless you have specified it. Therefore, if the SQLite provider wanted to, the first time you request a page of products they might be in ProductId order, but the next time you request a page of products they might be in UnitPrice order, or a random order, and that would confuse users! In practice, at least for relational databases, the default order is usually by its index on the primary key.

### Loading 

- There are three different types of loading in EF.
    - Eager Loading: Load data early.
    - Lazy Loading: Load data automatically just before it is needed.
    - Explicit loading: Load data manually.
- To enable lazy loading, developers must:
    - Reference a NuGet package for proxies.
    - Configure lazy loading to use a proxy.

## Language Integrated Query (LINQ)

- LINQ has several parts; some are required, and some are optional:
    - Extension methods (required): These include examples such as `Where`, `OrderBy`, and `Select`. These are what provide the functionality of LINQ.
    - LINQ providers (required): These include LINQ to Objects for processing in-memory objects, LINQ to Entities for processing data stored in external databases and modeled with EF Core, and LINQ to XML for processing data stored as XML. These providers are what execute LINQ expressions in a way specific to different types of data.
    - Lambda expressions (optional): These can be used instead of named methods to simplify LINQ queries, for example, for the conditional logic of the Where method for filtering.
    - LINQ query comprehension syntax (optional): These include C# keywords like `from`, `in`, `where`, `orderby`, `descending`, and `select`. These are aliases for some of the LINQ extension methods, and their use can simplify the queries you write, especially if you already have experience with other query languages, such as Structured Query Language (SQL).
- Any class that support `IEnumerable` support LINQ.
- LINQ uses deferred execution.
```c#
    // a string array is a sequence that implements IEnumerable<string>
    string[] names = new[] { "Michael", "Pam", "Jim", "Dwight", 
    "Angela", "Kevin", "Toby", "Creed" };
    SectionTitle("Deferred execution");
    // Question: Which names end with an M?
    // (written using a LINQ extension method)
    var query1 = names.Where(name => name.EndsWith("m"));
    // Question: Which names end with an M?
    // (written using LINQ query comprehension syntax)
    var query2 = from name in names where name.EndsWith("m") select name;

    // Answer returned as an array of strings containing Pam and Jim
    string[] result1 = query1.ToArray();
    // Answer returned as a list of strings containing Pam and Jim
    List<string> result2 = query2.ToList();
    // Answer returned as we enumerate over the results
    foreach (string name in query1)
    {
    WriteLine(name); // outputs Pam
    names[2] = "Jimmy"; // change Jim to Jimmy
    // on the second iteration Jimmy does not end with an m
    }
```
    - Due to deferred execution, after outputting the first result, Pam, if the original array values change, then by the time we loop back around, there are no more matches because Jim has become Jimmy and does not end with an m, so only Pam is outputted.
- Extension methods can be chained if the previous method returns another sequence, that is, a type that implements the `IEnumerable<T>` interface.
- Once you have finished working on a query, you could change the declared type from var to the actual type to make it clearer what the type is. This is easy because your code editor can tell you what it is.

### Common LINQ extension methods

- `Where`
    - Used to filter items in a sequence.
    - Needs to return a bool 
- `OrderBy` & `ThenBy`
    - `OrderByDescending` & `ThenByDescending`
    - Used to order the sequence.
    - `ThenBy` is chained to an `OrderBy`
    - In .Net 7 & above you can use `Order` &  `OrderDescending` to sort by the item itself. For instance in an array of strings it would sort alphabetically.
- `OfType<T>()` 
    - Filter by type where type is `<T>.`
- `Join` & `GroupJoin`
    - `Join`: This method has four parameters: the sequence that you want to join with, the property or properties on the left sequence to match on, the property or properties on the right sequence to match on, and a projection.
    - `GroupJoin`: This method has the same parameters, but it combines the matches into a group object with a Key property for the matching value and an `IEnumerable<T>` type for the multiple matches.

## Importing (Using)

- Global imports can be found in `<projectName>.GlobalUsings.g.cs`.
- Use the following syntax for using alias `using aliasName = namespace`

## Data Types

- Use sizeOf to determine the size of a data type
- `object` can be used to store any data but can't implicitly run any method.
- `dynamic` can be used to store any data but at the cost of performance.
- `default` keyword can be used to set a value back to its default state.
- By default value types cannot be `null`.
- Value types can have a null value if you use the ? as a suffix `int? x` or you use the `Nullable` stuct `Nullable<int> x`.
- Initialism for null:
    - NRT - Nullable reference types: A compiler feature introduced with C# 8 and enabled by default in new projects with C# 10 that performs static analysis of your code at design time and shows warnings of potential misuse of null values for reference types.
    - NRE - NullReferenceException: An exception thrown at runtime when dereferencing a null value, aka accessing a variable or member that has a null value.
    - ARE - ArgumentNullException: An exception thrown at runtime by a method invocation when an argument has a null value when that is not valid.
- `#nullable disable` to disable nullabe feature for a single file.
- Suffix of ! is used to override types nullability. e.g. `Street = null!;`
- Null conditional operators return null if a property is not available. e.g. `WriteLine(address.Building?.Length);`
- C# 7 introduced the `is` keyword. It can be used to evaluate if a property is not null. e.g. `!(thisCouldBeNull is null)`. C# 9 introduced `is ot` to make it even clearer. e.g. `thisCouldBeNull is not null`
- null-coalescing operator: If the value is `null` it evaluates to a specified value. e.g.
```c#
    // result will be 3 if authorName?.Length is null 
    int result = authorName?.Length ?? 3; 
    Console.WriteLine(result);  
```
- C# 10 introduced a convenience method to throw an exception if an argument is null `ArgumentNullException.ThrowIfNull(PARAMETER);`. 


### Stack vs Heap

- Stack memory is faster to work with, but limited in size.
- Stack memory is located near the CPU in the L1 or L2 cache.
- Windows limits stack memory to 1mb while Unix-based operating systems limit to 8mb
- Value types are located in stack.
- Reference types are located in heap.
-  Heap memory is a type of computer memory that allows dynamic allocation and deallocation of memory blocks at runtime. It is called "heap" because the memory is allocated from a large pool of available memory that is dynamically managed by the operating system or programming language runtime.
- Heap memory is typically used for data structures such as arrays, linked lists, and trees, where the size of the data is not known at compile time and may change during program execution. The memory is allocated using functions like malloc() or new in C and C++, or alloc() in other programming languages.
- Heap memory is also prone to memory leaks, where allocated memory is not properly released after its use. This can lead to programs consuming excessive amounts of memory and crashing. Therefore, it is important to manage heap memory properly to avoid such issues.
- `class` and `record` are create reference type objects.
- `struct` and `record struct` are value types. 
- `Zip` pairs items in the list together.
- `Union` concatenates distinct values.
- `Distinct` returns unique values.  `DistinctBy` returns unique values as defined by a lambda function. E.g. `cohort2.DistinctBy(name => name.Substring(0, 2))` returns names where the first two letters are unique.
- 



### Casting

- Implicit
    - Happens automatically.
    - Safe.
    - Only happens when data won't be lost.
    - Example: int casting to double.
- Explicit
    - Must be preformed manually.
    - May lose data.
    - Telling the C# compiler that you understand and accept the risks.
    - Example: decimal to double.
- Converting
    - Must be preformed manually.
    - May lose data
    - Difference between casting explicitly and converting is `9.8` becomes `9` when casting but `10` when converting.
    - Example: string to int.
- Converting uses bankers rounding, different than school rounding.
- All objects have a `ToString()` method which converts it's value to a string.
- Parsing throws an error if the value cannot be converted. One way to avoid this is with the `tryParse()`

### Strings 

- Reference Type
- Treats `==` and `!=` as if it was a value type.
- Types or strings
    - Literal string
    - Raw string literal
    - Verbatim string
    - Interpolated string
- Prefix a string with `@` to tell the complier to ignore escape sequences such as `\t`.
- You can have multi-line strings by using raw string literals. This can be accomplished with three or more double quotes `"""`.
- Raw interpolated string literals are a way of having a multiline string with dynamic values. 
```c#
var person = new { FirstName = "Alice", Age = 56 };
string json = $$"""
              {
                "first_name": "{{person.FirstName}}",
                "age": {{person.Age}},
                "calculation", "{{{ 1 + 2 }}}"
              }
              """;
Console.WriteLine(json);
```
    Would output:
```json
{
  "first_name": "Alice",
  "age": 56,
  "calculation", "{3}"
}
```
    - The number of dollars tells the compiler how many curly braces are needed for something to become recognized as an interpolated expression.

### Numbers

- Value Type
- Types of numbers
    - int
    - long
    - short
- Use underscores to improve legibility. `int million = 1_000_000;`
- `a++` increments after assigning `++a` increments before assigning.
- Its good practice to never combine assigning a variable with increment or decrement operators (Unary Operators).
- Unary Operators `a++` and `a--` or `++a` and `--a`.

### Real Numbers AKA Decimals

- Value Type
- Types of real numbers
    - float
    - double
    - decimal
    - Half: Inaccurate like doubles or float, but half the size of floats. Mostly used for ML.
- Never use `==` when dealing with doubles or floats due to the inaccuracies.

### Var

- A literal number without a decimal point is inferred as an int variable, that is, unless you add a suffix, as described in the following list:
    - L: Compiler infers long
    - UL: Compiler infers ulong 
    - M: Compiler infers decimal
    - D: Compiler infers double
    - F: Compiler infers float



## Controlling Flow

- Always include brackets when using if statements. Not including brackets can lead to serious bugs such as the famous #gotofail bug.
- If statements can check type by `if(o is int i)` if the variable `o` is an int then the variable is assigned to `i` which can be used in the if statement.
- In switch statements you can use the `goto` keyword to jump to a separate case or label. However, it is highly frowned upon.
- You can use lambda functions with switch statements to reduce number of lines.
- Any collection type should support `foreach`. In order to support `foreach` they must follow these rules:
    - The type must have a method named GetEnumerator that returns an object.
    - The returned object must have a property named Current and a method named MoveNext.
    - The MoveNext method must change the value of Current and return true if there are more items to enumerate through or return false if there are no more items.
    - It's best practice to implement `IEnumerable`.
- `foreach` is readonly.
- 

### Loops
- Continue, Break, and Return
    - `continue`: Stops the current loop, but continues the iteration.
    - `break`: Stops the loop entirely.
    - `return`: Stops the method call.

## Arrays

- Use `GetUpperBound()` to determine the upper index bound of a multidimensional array.
    - This can be particularly helpful when dealing with jagged arrays.
- Types of arrays
    - `string[]`: Regular single dimension array.
    - `string[,]`: Two dimension array.
    - `string[,,]`: Three dimension array. 
    - `string[][]`:  Jagged array. AKA a multidimensional array who's child arrays are of varying sizes.
    - `string[][][]`: Array of arrays of arrays
- Arrays should be used over Lists in the following conditions
    - Not using LINQ
    - Not adding or removing values
    - Not dealing with a large number of values.
-

## Functions

- Instead of defining functions in your `Program.cs` file create a `Program.Functions.cs` file and create a `partial` class of Program where you can define the functions.
- Use XML Comments `\\\` to create documentation and add description to your function when the developer hovers over the function name. 

## Logging

- Debug and Trace are the two most common ways to log.
- Debug gets stripped away when running the release configuration. Therefore, you can use `Debug.WriteLine` liberally throughout your code.

## Testing

- MSTest: Microsoft proprietary testing framework.
- xUnit.net: Built by the same team who built NUnit, but they fixed a few of their mistakes.
- Types of testing include:
    - Unit: Tests the smallest unit of code, typically a method or function. 
        - Test to ensure expected result as well as exception handling.
    - Integration: Tests if the smaller units and larger components work together as a single piece of software. 
        - Sometimes involves integrating with external components that you do not have source code for.
    - System: Tests the whole system environment in which your software will run.
    - Performance: Tests the performance of your software.
        - Example: Your code must return a web page full of data to a visitor in under 20 milliseconds.
    - Load: Tests how many requests your software can handle simultaneously while maintaining required performance
        - Example: 10,000 concurrent visitors to a website.
    - User-Acceptance: Tests if users can happily complete their work using your software.

### Unit Tests

- A well written unit test will contain three parts.
    - Arrange: This part will declare and instantiate variables for input and output.
    - Act: This part will execute the unit that you are testing. In our case, that means calling the method that we want to test.
    - Assert: This part will make one or more assertions about the output. An assertion is a belief that, if not true, indicates a failed test. For example, when adding 2 and 2, we would expect the result to be 4.

## Exceptions 

-  Only catch and handle an exception if you have enough information to mitigate the issue. If you do not, then you should allow the exception to pass up through the call stack to a higher level.
- Usage Error: A programmer misuses a function, typically by passing invalid values as parameters.
- Execution Errors: When something happens at runtime that cannot be fixed by writing “better” code. 
    - Program Errors: Can be programmatically fixed by writing smart code.
        - Example: DB is down but program tries to connect.
    - System Errors: Often cannot be fixed programmatically.
- Very rarely should you define new types of exceptions to indicate usage errors. .NET already defines many that you should use.
    - ArgumentNullException
    - ArgumentException
    - NotSupportedException
    - InvalidOperationException
- When defining your own functions with parameters, your code should check the parameter values and throw exceptions if they have values that will prevent your function from properly functioning.
-  If a function cannot successfully perform its operation, you should consider that a function failure and report it by throwing an exception.
- `ArgumentNullException.ThrowIfNull(accountName)` Checks if null and throws an exception.
- You can rethrow an exception after catching it in case you want to log the issue, but throw it higher up the call stack
    - `throw`: Throws the exception with original call stack
    - `throw ex`: Throws the exception as if it happened at the current call stack position.
    - `innerException`: Throws an exception with more information that surrounds th current exception.

### Exception Handling

- You should never have an empty catch block in production.
- Specific catch exceptions should occur first followed by generic ones such as `System.Exception`.
- You can catch with filters such as `catch (FormatException) when (amount.Contains("$"))`.
- Use `checked` to check for data overflow. Default compiler behavior
- Likewise, use `unchecked` to not check for data overflow.

### Call Stack

- The stack of method called starting with Main

## OOP 
- The concepts of OOP:
    - Encapsulation:  Control what can access those actions and the data; for example, restricting how the internal state of an object can be accessed or modified from the outside.
    - Composition: What an object is made of. For example, a Car is composed of different parts, such as four Wheel objects, several Seat objects, and an Engine.
    - Aggregation: what can be combined with an object. For example, a Person is not part of a Car object, but they could sit in the driver’s Seat and then become the car’s Driver—two separate objects that are aggregated together to form a new component.
    - Inheritance: Reusing code by having a subclass derive from a base or superclass. All functionality in the base class is inherited by, and becomes available in, the derived class.
    - Abstraction: Capturing the core idea of an object and ignoring the details or specifics.
    - Polymorphism: Allowing a derived class to override an inherited action to provide custom behavior.

## Types

- It's better to use read-only over constant because constant changes out the variables during meaning you'll be required to rebuild any project if the constant changes.
- Use read-only fields over constant fields for two important reasons: the value can be calculated or loaded at runtime and can be expressed using any executable statement. So, a read-only field can be set using a constructor or a field assignment. Every reference to the read-only field is a live reference, so any future changes will be correctly reflected by the calling code.
- Avoid types imported into the `System.Collections` namespace. Use types imported in `System.Collections.Generics` and other namespaces instead.
- Generics specify their type in brackets e.g. `list<int>`
- Finalizer(destructor) are similar to constructors that will be called by the .NET runtime when the resources need to be released. The method signature is the same as a constructor except the name is prefixed with a tilde `~`.
- To allow a developer to dispose of your type implement the `IDisposable` interface.
- You can use the `using` statement to ensure an unmanaged resource is disposed even when an exception is thrown. `using (ObjectWithUnmanagedResources thing = new())`
- When someone uses a type that implements IAsyncDisposable you can use `await using (ObjectWithUnmanagedResources thing = new())`

### Objects

- In C# 9 and above you can use the `new()` keyword alone without having to repeat the type. `XmlDocument xml3 = new(); // target-typed new in C# 9 or later`

### Class

- Reference type
- `partial`: Split the definition of a class across multiple files. 

- Members:
    - Fields: Used to store data
        - Constant: Data never changes.
        - Read-Only:  The data cannot change after the class is instantiated, but the data can be calculated or loaded from an external source at the time of instantiation.
        - Events: The data references one or more methods that you want to execute when something happens, such as clicking on a button or responding to a request from some other code.
    - Methods: Used to execute statements.
        - Constructors: The statements execute when you use the new keyword to allocate memory to instantiate a class.
        - Properties: The statements execute when you use the new keyword to allocate memory to instantiate a class.
        - Indexer: The statements execute when you get or set data using “array” syntax. Allow the calling code to use the array syntax to access a property.
        - Operator: The statements execute when you use an operator like + and / on operands of your type.
    - Access Modifier
        - public: Accessible anywhere.
        - private: Member is accessible inside the type only. This is the default.
        - protected: Only accessible  inside the type and any type that inherits from the type.
        - internal: Member is accessible inside the type and any type in the same assembly.
        
        * - internal protected: Member is accessible inside the type, any type in the same assembly, and any type that inherits from the type.
        * - private protected: Member is accessible inside the type and any type that inherits from the type and is in the same assembly. 
- To pattern match on the properties of an object, you must name a local variable, like p, that can then be used in an expression.
- To pattern match on a type only, you can use _ to discard the local variable.
- The switch expression also uses _ to represent its default branch.
- Abstract classes were mostly used prior to the interface feature default implementation. However, some still prefer abstract classes over default implementation.
- You can use the `sealed` keyword to prevent others from inheriting your class or overriding an already overridden method.
- You can hide a inherited method with the `new` keyword or override and `virtual` inherited method with the `override` keyword.
- When the method is hidden with `new` and you use the superclass as the type then it runs the superclass method.
- In 99% of scenarios `override` and `virtual` is the way to go.
- You must explicitly cast down to a subclass. However, casting up to a superclass is implicit.
- Use the `is` keyword to check if a type is of a certain type. e.g. `if(aliceIsPerson is Employee)`. The advantages of this is while using polymorphism. 
- Use `as` keyword to explicitly cast to a subclass as it will return `null` instead of throwing an exception. e.g. `Employee? aliceAsEmployee = aliceInPerson as Employee;`
- Constructors are not inherited and must be specified with the `: base()` syntax.
- Use `static class` and `(this paramType paramName)` to extend sealed classes.
- Extension methods cannot be used to override a method.
- 

### Enum

- You can make Enums convert to `bytes` instead of `int` and save 75% in memory.
    - This only works when there are less than 8 values.
- Use `[Flags]` when the enum represents a potential list of values.
- 

### Tuples

- Value Types
- A way to combine two or more values as a return type.
- Are indicated using `(string, int, etc)` as the return type.
- By default the value are `Item1, Item2, etc.`.
- You can name the tuple values using the following syntax `(string Name, int Number)`.
- You can deconstruct tuples by using the following syntax `(string theName, int theNumber) = TupleStringAndNumber();`

### Methods

- Actions that an object can perform, either on itself or on related objects
- Any type can have a `Deconstruct()` method by using the `out` keyword.
- You do not explicitly call the Deconstruct method. It is called implicitly when you assign an object to a tuple variable.
- Method signature is a list of parameter types that can be passed when calling the method.
- Overloaded methods can't differ in the return types.
- Default parameters can be assigned in the method signature `(string name = "Jeff")`. Now, by default, the name variable is Jeff.
- Parameters can be passed three ways:
    - Value: This is the default way. Think of these as being in-only. Is a copy of the variable.
    - Out:  Think of these as being out-only. out parameters cannot have a default value assigned in the parameter declaration and they cannot be left uninitialized.
    - Ref: Think of these as being in-and-out. Like out parameters, ref parameters also cannot have default values, but since they can already be set outside the method, they do not need to be set inside the method.
- In C# 7.0 and later, we can simplify code that uses the out parameter:
    ```
    int d = 10; 
    int e = 20;
    WriteLine($"Before: d = {d}, e = {e}, f doesn't exist yet!");
    // simplified C# 7.0 or later syntax for the out parameter 
    bob.PassingParameters(d, ref e, out int f); 
    WriteLine($"After: d = {d}, e = {e}, f = {f}");
    ```
- Simple Properties automatically generate the field
- `required` Modifier: If you use it on a property or field, the compiler will ensure that you set the property or field to a value when you instantiate it.
- Setting a property or field to be required does not mean that it cannot be null. It just means that it must be explicitly set to null.
- Indexers: Allow the calling code to use the array syntax to access a property.
    ```
    // indexers
    public Person this[int index]
    {
    get
    {
        return Children[index]; // pass on to the List<T> indexer
    }
    set
    {
        Children[index] = value;
    }
    }
    ```
- You can overload indexers
- A method that creates a new object, or modifies an existing object, should return a reference to that object so that the caller can access the results.
- You can assign operator methods with the following syntax:
    ```
    // operator to "marry"
    public static bool operator +(Person p1, Person p2)
    {
    Marry(p1, p2);
    return p1.Married && p2.Married; // confirm they are both now married
    }
    ```
- The return type for an operator does not need to match the types passed as parameters to the operator, but the return type cannot be void.
- Unlike methods, operators do not appear in IntelliSense lists for a type. For every operator that you define, make a method as well, because it may not be obvious to a programmer that the operator is available. The implementation of the operator can then call the method, reusing the code you have written. A second reason for providing a method is that operators are not supported by every language compiler; for example, although arithmetic operators like * are supported by Visual Basic and F#, there is no requirement that other languages support all operators supported by C#.
- The init word allows you to set a property only during instantiation. `public string Name {get; init;}`

### Delegates

- Delegates have built-in support for asynchronous operations that run on a different thread, and that can provide improved responsiveness.
- Delegates allow us to implement events for sending messages between different objects that do not need to know about each other.
- Microsoft has two predefined delegates for use as events:
    - `object? sender`: This parameter is a reference to the object raising the event or sending the message. The reference could be null.
    - `EventArgs e` or `TEventArgs e`: This parameter contains additional relevant information about the event that is occurring. For example, in a GUI app, you might define MouseMoveEventArgs that has properties for the X and Y coordinates for the mouse pointer. A bank account might have a WithdrawEventArgs with a property for the amount to withdraw.
- Delegates are multicast meaning you can assign multiple delegates to a single delegate field.
- When the delegate is called, all the assigned methods are called, although you have no control over the order in which they are called.
- Operators can be used in the following ways:
    - `=` Assign the method to the delegate
    - `+=` Assigns an additional method to the delegate
    - `-=` Removes a method from the delegate

#### Events
- Actions that happen to an object. e.g a button has a click event.
- Microsoft’s convention for method names that handle events is `ObjectName_EventName`.


### Records

- Reference type unless the keyword `struct` is placed after
- Should not have any state that changes after instantiation.
- Immutable
```c#
    // simpler way to define a record
    // auto-generates the properties, constructor, and deconstructor
    public record ImmutableAnimal(string Name, string Species);
```
- Implements `==` and `!=` automatically for you. Operates similar to string.
- Microsoft recommends explicitly specifying `record class` or `record struct` even though `class` is inferred. 

### Interfaces

- Interfaces are a way to implement standard functionality and connect different types to make new things.
- If a type implements an interface, then it is making a promise to the rest of .NET that it supports specific functionality. Therefore, they are sometimes described as contracts.
- `IComparable` is used to implement `ComparTo()` and sort arrays.
    - `CompareTo()` returns a number to represent position if array. 
        - -1 before
        - 0 same as
        - 1 after
- If a class doesn't implement `IComparable` and you don't have access to the source code you can use IComparer
- If two interfaces are implemented with method having the same call signature you can explicitly define the methods with the following syntax
```c#
    public class Person : IGamePlayer, IKeyHolder
    {
        public void Lose() // implicit implementation
        {
            // implement losing a key
        }
        void IGamePlayer.Lose() // explicit implementation
        {
            // implement losing a game
        }
    }
```
    And can be called with:
```c#
    // calling implicit and explicit implementations of Lose
    Person p = new();
    p.Lose(); // calls implicit implementation of losing a key
    ((IGamePlayer)p).Lose(); // calls explicit implementation of losing a game
    IGamePlayer player = p as IGamePlayer;
    player.Lose(); // calls explicit implementation of losing a game
```
- Interfaces are meant to be fixed contracts, but sometimes you need to add new members after release. The problem with this is it will break any class currently implementing the interface. However, C# 8.0 introduced default implementations. This allowed for interfaces to add additional members after release. The syntax is simple, it identical to creating methods in classes.
- Only deals with public fields and methods

### Struct

- Value Type 
- If a `struct` uses field types that are not of the `struct` type, then those fields will be stored on the heap, meaning the data for that object is stored in both the stack and the heap!
- Number types (`int`, `double`, `decimal`, etc.) are struct along with other system types like (`dateTime`, `char`, `bool`, etc.). But the majority of types are classes most notably is the `string` type.
- If the total memory used by all the fields in your type is 16 bytes or less, your type only uses value types for its fields, and you will never want to derive from your type, then Microsoft recommends that you use `struct`. If your type uses more than 16 bytes of stack memory, if it uses reference types for its fields, or if you might want to inherit from it, then use class.

## Regular Expressions

- Use `@""` with regex to disable the ability to use escape characters.
- Common Regex:
    - `/d`: Single Digit
    - `/D`: Single non-digit
    - `/s`: Single whitespace
    - `/S`: Single non-whitespace
    - `/w`: Single Word character
    - `/W`: Single non-word character
    - `[A-Za-z0-9]`: Range of characters
    - `[aeiou]`: Set of characters
    - `[^aeiou]`: Not in set of characters
    - `^`: Start
    - `$`: End
    - `+`: Used as a prefix to allow one or more. E.g. `^/d+$`: One or more digits
    - `?`: None or one
    - `{3}`: Exactly Three
    - `{3,5}`: Three to five
    - `{3,}`: At least Three 
    - `{,3}`: No more than Three 
    - `.`: Any single character
- 

## Collections

- All Collections implement the `ICollections` & `IEnumerable` interface.
- `EnsureCapacity()` Increases performance by pre-sizing a collection.
- If you import the `System.Collections.Immutable` namespace, then any collection that implements `IEnumerable<T>` is given six extension methods to convert it into an immutable list, dictionary, hash set, and so on.
    - To improve performance, many applications store a shared copy of commonly accessed objects in a central cache. To safely allow multiple threads to work with those objects knowing they won’t change, you should make them immutable or use a concurrent collection type that you can read about at the following link: https://docs.microsoft.com/en-us/dotnet/api/system.collections.concurrent.
- Let’s say you need to create a method to process a collection. For maximum flexibility, you could declare the input parameter to be IEnumerable<T> and make the method generic, as shown in the following code:
```C#
    void ProcessCollection<T>(IEnumerable<T> collection)
    {
    // process the items in the collection,
    // perhaps using a foreach statement
    }
```
    - One of the performance problems with `IEnumerable<T>` is also one of its benefits: deferred execution, also known as lazy loading. Types that implement this interface do not have to implement deferred execution, but many do.
    - But the worst performance problem with `IEnumerable<T>` is that the iteration must allocate an object on the heap. To avoid this memory allocation, you should define your method using a concrete type, as shown highlighted in the following code:

### Lists

- Ordered Lists
- Implements `IList<T>` interface,
- Items index can change
- Use array if the data size will not change after instantiation.
- `Add()` to add an item to the end of the list and `Insert()` to add the item at a certain index.
-  Similar to the above is `Remove()` & `RemoveAt()`

### Dictionary

- Key value pair.
- Known as `hashmaps` in other languages.
- Implements `IDictionary<TKey, TValue>`
- `Add(TKey, TValue)` to add an entry and `Remove(TKey)` to remove an entry.

### Stacks

- Last In, First-Out (LIFO) behavior.
- Can only directly access or remove last item, but can enumerate through entire stack
- Word processor use this to implement "Undo" feature.
- `Push()` to add a new item and `Pop()` to remove the last item.
- Use `Peek()` to access top item without removing.


### Queues

- First In, First Out (FIFO) behavior.
- Can only directly access or remove first item, but can enumerate through entire queue.
- Example: People standing in a line.
- .Net 6 introduced priority queue where each item has a priority level.
- `Enqueue()` to add an item to the end and `Dequeue()` to remove/access an item from the beginning. 
- Use `Peek()` to access first item without removing.

### Sets

- A collection of one or more distinct objects.
- A multiset, aka bag, is a collection of one or more objects that can have duplicates.
- Sets are a good choice when you want to perform set operations between two collections.

### Sorted

- There are three auto sorting collections and they can impact performance:
    - `SortedDictionary<TKey, TValue>`: This represents a collection of key/value pairs that are sorted by key.
    - `SortedList<TKey, TValue>`: This represents a collection of key/value pairs that are sorted by key.
    - `SortedSet<T>`: This represents a collection of unique objects that are maintained in a sorted order.
- The difference between sorted dictionary and list is their impact on memory and performance.
    - `SortedList<TKey, TValue>` uses less memory.
    - `SortedDictionary<TKey, TValue>` has faster insertion and removal operations for unsorted data, O(log n) as opposed to O(n) for  `SortedList<TKey, TValue>`.
    - If the list is populated all at once from sorted data, `SortedList<TKey, TValue>` is faster than  `SortedDictionary<TKey, TValue>`.
    - `SortedList` actually maintains a sorted array, rather than using a tree. It still uses binary search to find elements.


## Span, Indexes, Ranges

### Spans

- If you need to work with a subset of an array, use a span because it is like a window into the original array. This is more efficient in terms of memory usage and improves performance. Spans only work with arrays, not collections, because the memory must be contiguous.
-

### Index

- More formal way to store an index
- Supports counting from the end
```c#
    // two ways to define the same index, 5 in from the end
    Index i3 = new(value: 5, fromEnd: true); 
    Index i4 = ^5; // using the caret operator
```

### Ranges


## File Systems

- Check that a drive is ready before reading properties such as TotalSize or you will see an exception thrown with removable drives.
- To manage directories, use the `Directory`, `Path`, and `Environment` static classes. 
- Accessing files should be done in a try block so that you can close them with `finally`.
- GetTempFileName creates a zero-byte file and returns its name, ready for you to use. GetRandomFileName just returns a filename; it doesn’t create the file.
- 

### Streams

- A stream is a sequence of bytes that can be read from and written to.
- Although files can be processed rather like arrays, with random access provided by knowing the position of a byte within the file, it can be useful to process files as a stream in which the bytes can be accessed in sequential order.
- Streams can also be used to process terminal input and output and networking resources such as sockets and ports that do not provide random access and cannot seek (that is, move) to a position. 
-  All streams implement IDisposable, so they have a Dispose method to release unmanaged resources.
- Common properties
    - `CanRead`, `CanWrite`:These properties determine if you can read from and write to the stream.
    - `Length`, `Position`: These properties determine the total number of bytes and the current position within the stream. These properties may throw an exception for some types of streams.
    - `Dispose`: This method closes the stream and releases its resources.
    - `Flush`: If the stream has a buffer, then this method writes the bytes in the buffer to the stream and the buffer is cleared.
    - `CanSeek`: This property determines if the Seek method can be used.
    - `Seek`: This method moves the current position to the one specified in its parameter.
    - `Read`, `ReadAsync`: These methods read a specified number of bytes from the stream into a byte array and advance the position.
    - `ReadByte`: This method reads the next byte from the stream and advances the position.
    - `Write`, `WriteAsync`: These methods write the contents of a byte array into the stream.
    - `WriteByte`: This method writes a byte to the stream.
- Plugin Streams:
    - `System.Security.Cryptography` - CryptoStream: This encrypts and decrypts the stream.
    - System.IO.Compression - GZipStream, DeflateStream: These compress and decompress the stream.
    - System.Net.Security - AuthenticatedStream: This sends credentials across the stream.
- Stream Helper:
    - StreamReader: This reads from the underlying stream as plain text.
    - StreamWriter: This writes to the underlying stream as plain text.
    - BinaryReader: This reads from streams as .NET types. For example, the ReadDecimal method reads the next 16 bytes from the underlying stream as a decimal value and the ReadInt32 method reads the next 4 bytes as an int value.
    - BinaryWriter: This writes to streams as .NET types. For example, the Write method with a decimal parameter writes 16 bytes to the underlying stream and the Write method with an int parameter writes 4 bytes.
    - XmlReader: This reads from the underlying stream using XML format.
    - XmlWriter: This writes to the underlying stream using XML format.
- Before calling the Dispose method, check that the object is not null.
- You can use `using` to automatically call dispose.
-

## Serialization

- Object Graph: Multiple objects that are related to each other either through a direct reference or indirectly through a chain of references.
- Serialization: The process of converting a live object graph into a sequence of bytes using a specified format.
- Two most common formats are JSON and XML
- JSON is more compact and is best for web and mobile applications. XML is more verbose but is better supported in more legacy systems. Use JSON to minimize the size of serialized object graphs. JSON is also a good choice when sending object graphs to web applications and mobile applications because JSON is the native serialization format for JavaScript, and mobile apps often make calls over limited bandwidth, so the number of bytes is important.
- Empty Constructor - The constructor does not need to do anything, but it must exist so that the XmlSerializer can call it to instantiate new Person instances during the deserialization process.
- When using XmlSerializer, remember that only the public fields and properties are included, and the type must have a parameterless constructor. You can customize the output with attributes.
- Choose `Json.NET` for developer productivity and a large feature set, or `System.Text.Json` for performance. 

## Benchmarking

- A popular library used by Microsoft for benchmarking is `BenchmarkDotNet`.

## Asynchronous

- Tasks are used to represent an asynchronous action.
- Their are three methods to wait for async tasks to finish.
    - `t.Wait()` - Waits for task `t` to finish before continuing.
    - `Task.WaitAny(Task[])` - Waits for one task in the array to finish.
    - `Task.WaitAll(Task[])` - Waits for all tasks in the array to finish.
- `Task.CompletedTask` to return an async void method.
- Use `lock` to prevent multiple threads from accessing the same object.
- The C# compiler changes the lock statement into a try-finally statement that uses the Monitor class to enter and exit the conch object (I like to think of it as taking and releasing the conch object).
- You cannot use value types (`struct` type) as a conch. `Monitor.Enter` requires a reference type because it locks the memory address.
- Deadlocks can occur when there are two or more shared resources (each with a conch to monitor which thread is currently doing work on each shared resource), and the following sequence of events happens:
    - Thread X “locks” conch A and starts working on shared resource A.
    - Thread Y “locks” conch B and starts working on shared resource B.
    - While still working on resource A, thread X needs to also work with resource B, and so it attempts to “lock” conch B but is blocked because thread Y already has conch B.
    - While still working on resource B, thread Y needs to also work with resource A, and so it attempts to “lock” conch A but is blocked because thread X already has conch A.
- .NET events are not thread-safe, so you should avoid using them in multithreaded scenarios.
- There is a type named `Interlocked` that can perform atomic actions
- It is important to understand which operations are atomic in multithreading because if they are not atomic, then they could be interrupted by another thread partway through their operation.
- `Main` method is async in C# 7.1 and further

# Patterns

- Generally there are three types of models
    - Entity Model - DB Data
    - DTO Model - Data Transfer 
    - View Model - Data the user sees

## Repository

- With the Repository pattern, we create an abstraction layer between the data access and the business logic layer of an application. By using it, we are promoting a more loosely coupled approach to access our data from the database. Also, the code is cleaner and easier to maintain and reuse. Data access logic is in a separate class, or sets of classes called a repository, with the responsibility of persisting the application’s business model.

## Dependency Injection

- Always use interface with DI.
- Allows you to change a dependency in one place instead of 100. Similar to a variable.
- By default it is in ASP.Net core projects.
- Not set up by default in WPF, Console or WinForms applications.
- Allows us to ask for and instance of a class rather than having to create a new instance.
- Creates loose coupling.
- Dependency Injection supports three service types:
    - Transient
        - New instance every time you ask for it.
        - Most common.
    - Singleton
        - Same instance every single time. 
        - Often overused
        - Stays in memory for live of application.
        - Often better than a static class
    - Scoped
        - Middle ground.
        - A singleton per 'person'. For instance, each instance of a a blazor webpage would have their own singleton.
        - Stays in memory only while the client is in use. 
        - 

### Configuring

- 

### Benefits

- Allows you to disconnect pieces of your application easily.
- Allows you to test pieces of your application independently. 

## MVC

### Model

- Although the ErrorViewModel class created by the MVC project template does not follow this convention, I recommend that you use the naming convention {Controller}{Action}ViewModel for your view model classes.

### View

### Control ler

- Controllers should be thin, meaning they only perform the above-listed activities but do not implement any business logic. All business logic should be implemented in services that the controller calls when needed.




# ASP .Net

- Two Windows servers for .Net are Kestrel and internet information service (IIS)
- ASP .Net Core replaced the single `System.Web.dll` with many modular lightweight packages.
- CMSs that support modern .NET include Optimizely Content Cloud, Piranha CMS, and Orchard Core.
- There are no formal definitions, but services are sometimes described based on their complexity:
    - Service: All functionality needed by a client app in one monolithic service.
    - Microservice: Multiple services that each focus on a smaller set of functionalities.
    - Nanoservice: A single function provided as a service. Unlike services and microservices that are hosted 24/7/365, nanoservices are often inactive until called upon to reduce resources and costs. 
- What are some differences between a microservice and a nanoservice?
    - A microservice implements more than one function grouped into a small domain and is always running. A nanoservice implements a single function and is not always running, i.e., it can be "serverless."
- What is Blazor?
    - Blazor is a .NET-based technology for implementing client-side web user interfaces. It is designed to be used instead of single-page applications (SPAs) like React, Angular, and Vue.
- Good Practice: Endpoint routing replaces the IRouter-based routing used in ASP.NET Core 2.1 and earlier. Microsoft recommends that every older ASP.NET Core project migrates to endpoint routing if possible.
- The web application `builder` registers services that can then be retrieved when the functionality they provide is needed using dependency injection. The naming convention for a method that registers a service is `AddNameOfService`. Our code registers two services: Razor Pages and an EF Core database context.
- 

## Services AKA Dependency Injection 

- `AddMvcCore`: Minimum set of services necessary to route requests and invoke controllers. Most websites will need more configuration than this.
- `AddAuthorization`: Authentication and authorization services.
- `AddDataAnnotations`: MVC data annotations service.
- `AddCacheTagHelper`: MVC cache tag helper service.
- `AddRazorPages`: Razor Pages service including the Razor view engine. Commonly used in simple website projects. It calls the following additional methods:
    - `AddMvcCore`
    - `AddAuthorization`
    - `AddDataAnnotations`
    - `AddCacheTagHelper`
- `AddApiExplorer`: Web API explorer service.
- `AddCors`: CORS support for enhanced security.
- `AddFormatterMappings`: Mappings between a URL format and its corresponding media type.
- `AddControllers`: Controller services but not services for views or pages. Commonly used in ASP.NET Core Web API projects. It calls the following additional methods:
    - `AddMvcCore`
    - `AddAuthorization`
    - `AddDataAnnotations`
    - `AddCacheTagHelper`
    - `AddApiExplorer`
    - `AddCors`
    - `AddFormatterMappings`
- `AddViews`: Support for .cshtml views including default conventions.
- `AddRazorViewEngine`: Support for Razor view engine including processing the @ symbol.
- `AddControllersWithViews`: Controller, views, and pages services. Commonly used in ASP.NET Core MVC website projects. It calls the following additional methods:
- `AddMvcCore`
    - `AddAuthorization`
    - `AddDataAnnotations`
    - `AddCacheTagHelper`
    - `AddApiExplorer`
    - `AddCors`
    - `AddFormatterMappings`
    - `AddViews`
    - `AddRazorViewEngine`
- `AddMvc`: Similar to `AddControllersWithViews`, but you should only use it for backward compatibility.
- `AddDbContext<T>`: Your DbContext type and its optional `DbContextOptions<TContext>`.
- `AddNorthwindContext`: A custom extension method we created to make it easier to register the NorthwindContext class for either SQLite or SQL Server based on the project referenced.

## Structure 

- Good Practice: You should create a separate class library project for your entity data models. This allows easier sharing between backend web servers and frontend desktop, mobile, and Blazor WebAssembly clients.
- Static files should be stored in `wwwroot` folder.
- The call to `UseDefaultFiles` must come before the call to `UseStaticFiles`, or it will not work. 
- Dynamic files should be stored in a folder named `Pages`
- `_ViewStart.cshtml` is used to establish the default layout
- `_Layout.cshtml` good practice for the name of the layout file

### HTTP Piperline

- HTTP requests and responses flow in and out.
- The pipeline is made up of a connected sequence of delegates that can perform processing and then decide to either return a response themselves or pass processing on to the next delegate in the pipeline. 
- Delegate for the HTTP request pipeline `public delegate Task RequestDelegate(HttpContext context);`
- `HttpContext`: Provides access to HTTP request, URL path, query string parameters, cookies, and user agent.
- These delegates are often called ***middleware*** because they sit in between the browser client and the website or web service.
- Middleware delegates are configured using one of the following methods or a custom method that calls them itself:
    - `Run`: Adds a middleware delegate that terminates the pipeline by immediately returning a response instead of calling the next middleware delegate.
    - `Map`: Adds a middleware delegate that creates a branch in the pipeline when there is a matching request usually based on a URL path like /hello.
    - `Use`: Adds a middleware delegate that forms part of the pipeline so it can decide if it wants to pass the request to the next delegate in the pipeline. It can modify the request and response before and after the next delegate.
- For convince you can use `UseMiddleware<T>`, where T is a class that has:
    - A constructor with a RequestDelegate parameter that will be passed to the next pipeline component.
    - An Invoke method with a HttpContext parameter and returns a Task.
- 

## Razor

- In the HTML markup of a web page, Razor syntax is indicated by the @ symbol. Razor Pages can be described as follows:
    - They require the @page directive at the top of the file.
    - They can optionally have an @functions section that defines any of the following:
    - Properties for storing data values, like in a class definition. An instance of that class is automatically instantiated, named Model, which can have its properties set in special methods, and you can get the property values in the HTML.
    - Methods named OnGet, OnPost, OnDelete, and so on that execute when HTTP requests are made, such as GET, POST, and DELETE.
- `@RenderBody()` is similar to children in React
- You can separate the logic from the UI by creating another file that ends in `.cshtml.cs`.
- If you have a .cshtml Razor Page that does not have a code-behind file, then you can inject a dependency service using the @inject directive instead of constructor parameter injection, and then directly reference the injected database context using Razor syntax in the middle of the markup.

### Partial Views

- By convention, the names of partial views start with an underscore.
- If you put a partial view in the `Shared` folder, then it can be found automatically.
- 

# Working with DB

- ADO.Net is the most common interface for running db queries.
- Frameworks like Entity Framework rely on ADO.Net to run queries

# Third-Party Libraries

## Serilog

- Serilog can be told to write serialized structured data to the log. The @ symbol prefixing a parameter tells Serilog to serialize the object passed in, instead of just the result of calling the ToString method.
``` C#
    var lineitem = new { ProductId = 11, UnitPrice = 25.49, Quantity = 3 };
    log.Information("Added {@LineItem} to shopping cart.", lineitem);
```
- Sinks are what serilog refers to its data stores. Their are many official and third-party sinks, including:
    - serilog.sinks.file
    - serilog.sinks.console
    - serilog.sinks.periodicbatching
    - serilog.sinks.debug
    - serilog.sinks.applicationinsights
    - serilog.sinks.mssqlserver
- 

## Automapper

## ImageSharp

- Most popular library for working with images.
- ImageSharp has two libraries for drawing and working with images online.
    - SixLabors.ImageSharp.Drawing
    - SixLabors.ImageSharp.Web
- 