# Assignment-2-Arrays-and-Strings

**1. When to use String vs. StringBuilder in C#?**

**String:** Immutable. Every modification (like concatenation) creates a new string object. Use when:
The string is small or changes infrequently.
You are performing simple operations like comparisons or formatting.
**StringBuilder:** Mutable. Efficient for frequent modifications. Use when:
You are building or modifying strings in loops.
You need better performance for large string operations.

**2. What is the base class for all arrays in C#?**

System.Array is the abstract base class for all arrays in C#.
All arrays (e.g., int[], string[]) inherit from System.Array.

**3.How do you sort an array in C#?**

Use Array.Sort():
int[] numbers = { 5, 2, 9, 1 };
Array.Sort(numbers);  // numbers = {1, 2, 5, 9}

**4. What property of an array object can be used to get the total number of elements?**

Length property.
int[] arr = {1, 2, 3, 4};
Console.WriteLine(arr.Length); 

**5.Can you store multiple data types in System.Array?**

Yes, but only if the array type is object[].
object[] mixed = {1, "hello", 3.14};
Normal strongly-typed arrays like int[] cannot store different types.

**6.What’s the difference between the System.Array.CopyTo() and System.Array.Clone()?**

Array.CopyTo() copies the elements of an array into an existing array
while Array.Clone() creates a new array that is a shallow copy of the original.
