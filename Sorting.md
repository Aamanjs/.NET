```csharp
namespace Sorting
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int n;

            Console.WriteLine("Enter number of elements: ");
            n = int.Parse(Console.ReadLine());

            int[] arr = new int[n];

            Console.WriteLine("Enter array elements: ");
            for(int i=0; i<n; i++)
            {
                arr[i] = int.Parse(Console.ReadLine());
            }

            //Bubble Sort Logic
            for(int i=0; i<n-1; i++)
            {
                for(int j=0; j<n-i-1; j++)
                {
                    if (arr[j] > arr[j + 1])
                    {
                        int temp = arr[j];
                        arr[j] = arr[j + 1];
                        arr[j + 1] = temp;
                    }
                }
            }

            Console.WriteLine("Sorted array: ");
            for(int i=0; i<n; i++)
            {
                Console.Write(arr[i] + " ");
            }
        }
    }
}
```
