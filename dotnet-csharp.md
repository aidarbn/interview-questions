# .NET and C#

<details>
<summary>What is a weak reference?</summary>

### Definition

A weak reference permits the garbage collector to collect the object while still allowing the application to access the object. A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist. When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected. However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.

### Short and Long Weak Referencess

#### Short

The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection. The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object. A short weak reference is the parameterless constructor for `WeakReference`.

#### Long

A long weak reference is retained after the object's `Finalize` method has been called. This allows the object to be recreated, but the state of the object remains unpredictable. To use a long reference, specify true in the `WeakReference` constructor.
 
If the object's type does not have a `Finalize` method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.

### Strong Reference

To establish a strong reference and use the object again, cast the `Target` property of a `WeakReference` to the type of the object. If the `Target` property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.

### Guidelines

- Use long weak references only when necessary as the state of the object is unpredictable after finalization.

- Avoid using weak references to small objects because the pointer itself may be as large or larger.

- Avoid using weak references as an automatic solution to memory management problems. Instead, develop an effective caching policy for handling your application's objects.

### Code Example

```csharp
class Program
{
    static void Main(string[] args)
    {
        // Creating a strong reference
        var strongRef = new MyClass();

        // Creating a weak reference
        WeakReference weakRef = new WeakReference(strongRef);

        // Dereferencing the strong reference
        strongRef = null;

        // Checking if the weak reference is alive and retrieving its target
        if (weakRef.IsAlive)
        {
            MyClass obj = (MyClass)weakRef.Target;
            if (obj != null)
            {
                Console.WriteLine("Weak reference is alive, and obj is not null.");
                obj.SomeMethod();
            }
            else
            {
                // GC occurred here and collected the object
                Console.WriteLine("Weak reference is alive, but obj is null.");
            }
        }
        else
        {
            Console.WriteLine("Weak reference is dead.");
        }
    }
}

class MyClass
{
    public void SomeMethod()
    {
        Console.WriteLine("Some method called.");
    }
}
```

### Links

- https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/weak-references
- https://csharp.2000things.com/2012/12/13/735-dont-trust-weakreference-isalive-if-it-returns-true/

</details>
