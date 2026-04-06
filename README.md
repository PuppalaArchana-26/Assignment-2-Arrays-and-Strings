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

**ARRAYS**
1.
using System;

class Program
{
    static void Main()
    {
        // Step 1: Create the original array with 10 items
        int[] originalArray = new int[10] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

        // Step 2: Create a second array with the same length as the first using Length property
        int[] copyArray = new int[originalArray.Length];

        // Step 3: Use a loop to copy elements from originalArray to copyArray
        for (int i = 0; i < originalArray.Length; i++)
        {
            copyArray[i] = originalArray[i];
        }

        // Step 4: Print both arrays to verify
        Console.WriteLine("Original Array:");
        foreach (int item in originalArray)
        {
            Console.Write(item + " ");
        }

        Console.WriteLine("\nCopied Array:");
        foreach (int item in copyArray)
        {
            Console.Write(item + " ");
        }
    }
}

**2.**

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Create an empty list to store items
        List<string> myList = new List<string>();

        // Infinite loop for user input
        while (true)
        {
            Console.WriteLine("Enter command (+ item, - item, or -- to clear):");
            string input = Console.ReadLine();

            if (string.IsNullOrWhiteSpace(input))
            {
                Console.WriteLine("Invalid input. Try again.");
                continue;
            }

            // Clear list if input is just "--"
            if (input.Trim() == "--")
            {
                myList.Clear();
                Console.WriteLine("List cleared.");
            }
            // Add item if input starts with "+"
            else if (input.StartsWith("+"))
            {
                string itemToAdd = input.Substring(1).Trim();
                if (!string.IsNullOrEmpty(itemToAdd))
                {
                    myList.Add(itemToAdd);
                    Console.WriteLine($"Added: {itemToAdd}");
                }
            }
            // Remove item if input starts with "-"
            else if (input.StartsWith("-"))
            {
                string itemToRemove = input.Substring(1).Trim();
                if (myList.Remove(itemToRemove))
                {
                    Console.WriteLine($"Removed: {itemToRemove}");
                }
                else
                {
                    Console.WriteLine($"Item not found: {itemToRemove}");
                }
            }
            else
            {
                Console.WriteLine("Invalid command. Use +, -, or --.");
            }

            // Display the current list
            Console.WriteLine("Current list:");
            if (myList.Count == 0)
            {
                Console.WriteLine("(empty)");
            }
            else
            {
                foreach (string item in myList)
                {
                    Console.WriteLine("- " + item);
                }
            }

            Console.WriteLine(); // Empty line for readability
        }
    }
}

**How it works:**

+ item → Adds item to the list.
- item → Removes item from the list if it exists.
-- → Clears the list completely.
Each iteration shows the current contents of the list.
Infinite loop (while (true)) lets the user continue managing the list until they manually close the program.

**3.Write a method that calculates all prime numbers in given range and returns them as array
of integers
static int[] FindPrimesInRange(startNum, endNum)**

using System;

class Program
{
    static void Main()
    {
        int[] primes = FindPrimesInRange(10, 50);

        foreach (int p in primes)
        {
            Console.Write(p + " ");
        }
    }

    static int[] FindPrimesInRange(int startNum, int endNum)
    {
        int count = 0;

        // First pass: count primes
        for (int num = startNum; num <= endNum; num++)
        {
            if (IsPrime(num))
                count++;
        }

        // Create array with exact size
        int[] primes = new int[count];
        int index = 0;

        // Second pass: store primes
        for (int num = startNum; num <= endNum; num++)
        {
            if (IsPrime(num))
            {
                primes[index] = num;
                index++;
            }
        }

        return primes;
    }

    static bool IsPrime(int num)
    {
        if (num < 2) return false;

        for (int i = 2; i * i <= num; i++)
        {
            if (num % i == 0)
                return false;
        }

        return true;
    }
}

**EXPLANATION**

Loop through all numbers from startNum to endNum.
For each number, check if it’s divisible by any number from 2 to sqrt(num).
If not divisible, it’s a prime → add to the list.
Convert the List<int> to int[] and return.

**4.**
using System;

class Program
{
    static void Main()
    {
        // Read array input (space-separated)
        string input = Console.ReadLine();
        string[] parts = input.Split(' ', StringSplitOptions.RemoveEmptyEntries);

        int[] arr = new int[parts.Length];
        for (int i = 0; i < parts.Length; i++)
        {
            arr[i] = int.Parse(parts[i]);
        }

        // Read k
        int k = int.Parse(Console.ReadLine());

        int n = arr.Length;
        int[] sum = new int[n];

        // Perform k rotations
        for (int r = 1; r <= k; r++)
        {
            int[] rotated = new int[n];

            // Rotate right
            for (int i = 0; i < n; i++)
            {
                int newIndex = (i + r) % n;
                rotated[newIndex] = arr[i];
            }

            // Add to sum array
            for (int i = 0; i < n; i++)
            {
                sum[i] += rotated[i];
            }
        }

        // Print result
        Console.WriteLine(string.Join(" ", sum));
    }
}

**5.**

using System;

class Program
{
    static void Main()
    {
        // Read input array
        string[] input = Console.ReadLine().Split(' ', StringSplitOptions.RemoveEmptyEntries);
        int[] arr = new int[input.Length];

        for (int i = 0; i < input.Length; i++)
        {
            arr[i] = int.Parse(input[i]);
        }

        int maxLength = 1;
        int currentLength = 1;
        int bestValue = arr[0];

        for (int i = 1; i < arr.Length; i++)
        {
            if (arr[i] == arr[i - 1])
            {
                currentLength++;
            }
            else
            {
                currentLength = 1;
            }

            if (currentLength > maxLength)
            {
                maxLength = currentLength;
                bestValue = arr[i];
            }
        }

        // Print result
        for (int i = 0; i < maxLength; i++)
        {
            Console.Write(bestValue + " ");
        }
    }
}

**6.**

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Read input array
        string[] input = Console.ReadLine().Split(' ', StringSplitOptions.RemoveEmptyEntries);
        int[] arr = Array.ConvertAll(input, int.Parse);

        // Dictionary to store frequencies
        Dictionary<int, int> freq = new Dictionary<int, int>();
        int maxCount = 0;
        int mostFrequent = arr[0];

        foreach (int num in arr)
        {
            if (freq.ContainsKey(num))
                freq[num]++;
            else
                freq[num] = 1;

            // Update most frequent number
            if (freq[num] > maxCount)
            {
                maxCount = freq[num];
                mostFrequent = num;
            }
            // Tie: do nothing, we keep the leftmost
        }

        Console.WriteLine($"The number {mostFrequent} is the most frequent (occurs {maxCount} times)");
    }
}

printing the leftmost if multiple numbers have the same maximal frequency:

Use a Dictionary<int,int> to count occurrences.
Track maxCount and update mostFrequent only when a higher count appears.
Ties automatically keep the first/leftmost number.
