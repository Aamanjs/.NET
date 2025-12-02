## Practice Questions

1. Print the following pattern using nested loops:
```txt
   *
   **
   ***
   ****
   *****
```
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
2. Create a Car class with variables model, color, and price. Create two car objects and display their details.
```csharp
namespace Q2
{
    public class Car
    {
        public string model;
        public string color;
        public int price;

    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Car Details: ");

            Car c1 = new Car();
            Car c2 = new Car();

            Console.WriteLine("Car 1: ");
            c1.model = "BMW";
            c1.color = "Black";
            c1.price = 8000000;
            Console.WriteLine("Model: " + c1.model);
            Console.WriteLine("Color: " + c1.color);
            Console.WriteLine("Price: " + c1.price);

            Console.WriteLine("Car 2: ");
            c2.model = "Merc";
            c2.color = "White";
            c2.price = 7000000;
            Console.WriteLine("Model: " + c2.model);
            Console.WriteLine("Color: " + c2.color);
            Console.WriteLine("Price: " + c2.price);

        }

    }
}
```
