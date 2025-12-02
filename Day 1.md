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
3. Write a program with a class Calculator containing methods Add, Sub, Mul, and Div. Call these using object.
```csharp
namespace Q3
{
    class Calculator
    {
        public int add(int a, int b)
        {
            return a + b;
        }

        public int sub(int a, int b)
        {
            if (a > b)
            {
                return a - b;
            }
            else
            {
                return b - a;
            }
        }

        public int mul(int a, int b)
        {
            return a * b;
        }

        public int div(int a, int b)
        {
            if (a > b)
            {
                return a / b;
            }
            else
            {
                return b / a;
            }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Calculator c = new Calculator();

            while (true)
            {
                Console.WriteLine("Welcome to Calculator!! ");
                Console.WriteLine("Select operation to perform: ");
                Console.WriteLine("1. Add");
                Console.WriteLine("2. Substract");
                Console.WriteLine("3. Multiply");
                Console.WriteLine("4. Divide");
                Console.WriteLine("5.Exit");
                Console.WriteLine("---------------------------------");
                Console.WriteLine(" ");


                int choice = int.Parse(Console.ReadLine());

                if (choice == 5)
                {
                    Console.WriteLine("Exiting from Calculator");
                    break;
                }

                switch (choice)
                {
                    case 1:
                        Console.WriteLine("Enter two numbers: ");
                        int a1 = int.Parse(Console.ReadLine());
                        int b1 = int.Parse(Console.ReadLine());
                        Console.WriteLine("Result: " + c.add(a1, b1));
                        Console.WriteLine(" ");
                        Console.WriteLine("--------------------------");
                        break;

                    case 2:
                        Console.WriteLine("Enter two numbers: ");
                        int a2 = int.Parse(Console.ReadLine());
                        int b2 = int.Parse(Console.ReadLine());
                        Console.WriteLine("Result: " + c.sub(a2, b2));
                        Console.WriteLine(" ");
                        Console.WriteLine("--------------------------");
                        break;

                    case 3:
                        Console.WriteLine("Enter two numbers: ");
                        int a3 = int.Parse(Console.ReadLine());
                        int b3 = int.Parse(Console.ReadLine());
                        Console.WriteLine("Result: " + c.mul(a3, b3));
                        Console.WriteLine(" ");
                        Console.WriteLine("--------------------------");
                        break;

                    case 4:
                        Console.WriteLine("Enter two numbers: ");
                        int a4 = int.Parse(Console.ReadLine());
                        int b4 = int.Parse(Console.ReadLine());
                        Console.WriteLine("Result: "+ c.div(a4, b4));
                        Console.WriteLine(" ");
                        Console.WriteLine("--------------------------");
                        break;

                    default:
                        Console.WriteLine("Invalid choice! Please select a valid operation.");
                        break;

                }
            }
        }
    }
}
```
4. Create class Employee with fields id, name, salary. Create another class SalarySlip that prints employee salary slip using object of Employee in SalarySlip class.
```csharp
namespace Q4
{
    public class Employee
    {
        public int id;
        public string Name;
        public int salary;

        public Employee(int id, string Name, int salary)
        {
            this.id = id;
            this.Name = Name;
            this.salary = salary;
        }

    }

    public class SalarySlip
    {
        public void PrintSlip(Employee emp)
        {
            Console.WriteLine("------- Employee Salary Slip -------");
            Console.WriteLine("Employee ID: "+ emp.id);
            Console.WriteLine("Employee Name: "+emp.Name);
            Console.WriteLine("Employee Salary: "+emp.salary);
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Employee e1 = new Employee(101, "Aaman", 56000);

            SalarySlip slip = new SalarySlip();

            slip.PrintSlip(e1);
        }
    }
}
```
5. Create a BankAccount class with Deposit, Withdraw, and CheckBalance methods. Use encapsulation so balance cannot be directly accessed.
