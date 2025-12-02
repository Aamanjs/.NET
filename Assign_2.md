1. Create a medical bot application that can prescribe medication based on the patient's symptoms and age.
Hint:(Your task is to create a C# console application that simulates a medical bot named Bob. Bob should be able to prescribe medication based on the symptoms of a patient passed as an argument.)
```csharp
using System;

namespace Q1_Assign2
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Welcome to Medical Bot Bob!");
            Console.WriteLine("Enter patients age: ");
            int age = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("Enter patient's symptom (fever, cough, headache)");
            String symptom = Console.ReadLine().ToLower();

            String prescription = PrescribeMedication(symptom, age);
            Console.WriteLine("Prescription: " + prescription);


        }

        static string PrescribeMedication(string symptom, int age)
        {
            switch (symptom)
            {
                case "fever":
                    if (age < 12)
                        return "Paracetamol syrup (children dose)";
                    else
                        return "Paracetamol tablet (500mg)";

                case "cough":
                    if (age < 12)
                        return "Cough syrup (children formula)";
                    else
                        return "Cough syrup (adult formula)";

                case "headache":
                    if (age < 12)
                        return "Mild rest and hydration (avoid strong meds)";
                    else
                        return "Ibuprofen (200mg)";

                default:
                    return "Symptom not recognized. Please consult a doctor.";

            }
        }
    }
}

```
2. Create simple C# code that converts various values from one type another type.
```csharp
namespace Q2_Assign2
{
    internal class Program
    {
        static void Main(string[] args)
        {
            String strNumber = "123";
            int intNumber = Convert.ToInt32(strNumber);
            Console.WriteLine("Hello, World!");

            int intVal = 42;
            double doubleVal = Convert.ToDouble(intVal);
            Console.WriteLine("Int to Double: " + doubleVal);

            double pi = 3.14159;
            string strPi = Convert.ToString(pi);
            Console.WriteLine("Double to String: " + strPi);

            bool flag = true;
            string strFlag = Convert.ToString(flag);
            Console.WriteLine("Bool to String: " + strFlag);

            string strBool = "true";
            bool boolVal = Convert.ToBoolean(strBool);
            Console.WriteLine("String to Bool: " + boolVal);

            char letter = 'A';
            int asciiValue = Convert.ToInt32(letter);
            Console.WriteLine("Char to Int (ASCII): " + asciiValue);

            int num = 66;
            char charVal = Convert.ToChar(num);
            Console.WriteLine("Int to Char: " + charVal);

        }
    }
}

```
