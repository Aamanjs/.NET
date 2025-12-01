## Practice Questions

1. Print the following pattern using nested loops:
   *
   **
   ***
   ****
   *****
```csharp
namespace Q1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for(int i=1; i<=5; i++) {
                for(int j=1; j<=i; j++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }
            Console.ReadLine();
        }
    }
}

```
