Date of Completion: 08-01-2023
try to divide by 2 and check for a remainder, if true number is odd else its even

```csharp
namespace Solution{
    public class SolutionClass
    {
        public static string EvenOrOdd(int number)
        {
            bool result;
            if (number%2!=0) result=false; else result=true;
            if (result == true) return "Even"; else return "Odd";
        }
    }
    internal class Program
    {
        private static bool Running = false;
        private static void Main(string[] args)
        {
            Running = true;
            while (Running)
            {
                Console.WriteLine("==============================");
                Console.WriteLine("= Is a number even or odd ?  =");
                Console.WriteLine("==============================");
                Console.Write("please input a number => ");
                var input = Console.ReadLine();
                if (input=="q") Running=false;
                Int32 number;
                var result = int.TryParse(input, out number);
                if (!result) Console.WriteLine("You did NOT input a valid number"); else Console.WriteLine($"The number is {SolutionClass.EvenOrOdd(number)}");
            }
        }
    }
}
```