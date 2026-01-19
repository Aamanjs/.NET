```csharp
namespace EX1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int n, sum = 0;

            Console.WriteLine("Enter number of elements: ");
            n = int.Parse(Console.ReadLine());

            int[] arr = new int[n];

            //Read array elements
            Console.WriteLine("Enter array elements:");
            for(int i = 0; i<n; i++)
            {
                arr[i] = int.Parse(Console.ReadLine());
                sum += arr[i];
            }

            //Print sum
            Console.WriteLine("Sum of array elements = " + sum);

            //Print array in reverse order
            Console.WriteLine("Array elements in reverse order: ");
            for(int i=n-1; i>=0; i--)
            {
                Console.Write(arr[i] + " ");
            }
        }
    }
}
```
