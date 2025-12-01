1.	Write a C# program to calculate "area of circle" based on the given "radius" value. Note radius is 3.14
```csharp
namespace Q1_Assgn
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int r;

            System.Console.WriteLine("Enter the radius of circle: ");
            r = int.Parse(Console.ReadLine());

            double area = 2 * 3.14 * r;

            System.Console.WriteLine("The area of Circle is " + area);

        }
    }
}

```
2.	Write a program to find out "category of height" based on the given height of a person (in inches), using "if".
Note: 1 inch = 2.54 centimeter
You need to convert the input value (inches) into centimeters.
```csharp
namespace Q2_Assign
{
    internal class Program
    {
        static void Main(string[] args)
        {
            System.Console.WriteLine("Enter height(in inches): ");

            int h = int.Parse(Console.ReadLine());

            if(h * 2.54 < 150)
            {
                System.Console.WriteLine("Person is Short in height");
            } 
            else if(h * 2.54 >= 150 && h * 2.54 <= 165)
            {
                System.Console.WriteLine("Person is Medium in height"); 
            }
            else if(h * 2.54 >= 166 && h * 2.54 <= 180)
            {
                System.Console.WriteLine("Person is Tall in height");
            }
            else
            {
                System.Console.WriteLine("Person is Very Tall in height");
            }
      
        }
    }
}
```

4.	Write a C# program to get nearest thousands of given integer number. Here, let name the input value as "number".
```csharp
namespace Q3_Assign
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Enter the number: ");

            int number = int.Parse(Console.ReadLine());

            int thousands = number / 1000;
            int remainder = number % 1000;

            if(remainder >= 500)
            {
                System.Console.WriteLine("Nearest thousands: "+(thousands + 1) * 1000);
            } 
            else
            {
                System.Console.WriteLine("Nearest thousands: "+(thousands * 1000));
            }
        }
    }
}
```

