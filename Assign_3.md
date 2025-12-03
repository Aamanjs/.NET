Q1.	create a simple car rental program using C#. Your program should model a car rental agency that has a collection of cars, 
each with a make, model, rental price, and availability status.
```csharp
namespace Assign_3
{

    public class Car
    {
        public string Make { get; set; }
        public string Model { get; set; }
        public double RentalPrice { get; set; }
        public bool IsAvailable { get; set; }

        public Car(string make, string model, double rentalPrice, bool isAvailable)
        {
            Make = make;
            Model = model;
            RentalPrice = rentalPrice;
            IsAvailable = isAvailable;
        }

        public void DisplayInfo()
        {
            Console.WriteLine($"Car: {Make} {Model}, Rental Price: ${RentalPrice}, Available: {IsAvailable}");
        }
    }

    public class RentalAgency
    {
        private List<Car> cars = new List<Car>();

        public void AddCar(Car car)
        {
            cars.Add(car);
        }

        public void DisplayAvailableCars()
        {
            foreach (var car in cars)
            {
                if (car.IsAvailable)
                {
                    car.DisplayInfo();
                }
                else
                {
                    Console.WriteLine($"Car: {car.Make} {car.Model} is not available for rent");
                }
            }
        }

        public void RentCar(string make, string model)
        {
            foreach (var car in cars)
            {
                if(car.Make.Equals(make, StringComparison.OrdinalIgnoreCase) && car.Model.
                    Equals(model, StringComparison.OrdinalIgnoreCase) && car.IsAvailable)
                {
                    car.IsAvailable = false;
                    Console.WriteLine($"You have rented the car: {car.Make} {car.Model}");
                    return;
                }
            }
            Console.WriteLine("Car not available for rent.");
        }

        public void ReturnCar(string make, string model)
        {
            foreach (var car in cars)
            {
                if(car.Make.Equals(make, StringComparison.OrdinalIgnoreCase) && car.Model.Equals(model, StringComparison.OrdinalIgnoreCase) && !car.IsAvailable)
                {
                    car.IsAvailable = true;
                    Console.WriteLine($"\nYou have returned: {car.Make} {car.Model}. Thank you!"); 
                    return;
                }
            }
            Console.WriteLine("\nThis car was not rented from us.");
        }
    }

    internal class CarRentalApp
    {
        static void Main(string[] args)
        {
            RentalAgency r = new RentalAgency();
            r.AddCar(new Car("Toyota", "Corolla", 1500, true));
            r.AddCar(new Car("Honda", "Civic", 1800, true));
            r.AddCar(new Car("Ford", "Focus", 1200, false));

            while (true)
            {
                Console.WriteLine("\n------- Car Rental System --------");
                Console.WriteLine("1. Display Car Details");
                Console.WriteLine("2. Rent a Car");
                Console.WriteLine("3. Return Car");
                Console.WriteLine("4. Exit");

                int choice = Convert.ToInt32(Console.ReadLine());

                if(choice == 4) 
                {
                    Console.WriteLine("Exiting the system..!");
                    break;
                }

                switch (choice)
                {
                    case 1: 
                        r.DisplayAvailableCars();
                        break;

                    case 2:
                        Console.WriteLine("Enter Make of the Car to Rent: ");
                        string make = Console.ReadLine();
                        Console.WriteLine("Enter Model of the Car to Rent: ");
                        string model = Console.ReadLine();
                        r.RentCar(make, model); 
                        break;

                    case 3:
                        Console.WriteLine("Enter Make of the Car to Return: ");
                        string makeR = Console.ReadLine();
                        Console.WriteLine("Enter Model of the Car to Return: ");
                        string modelR = Console.ReadLine();
                        r.ReturnCar(makeR, modelR);
                        break;

                    default:
                        Console.WriteLine("Invalid Choice! Please try again.");
                        break;
                }
            }
            
        }
    }
}
```
