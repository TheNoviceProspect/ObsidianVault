Date of Completion: 16-01-2023
a wee bit involved, we make sure the array is not empty, then convert it to a list, to able to call List.Remove() of numbers.max and min
then return the result cast back to an array
```csharp
namespace SumWithoutHighestAndLowestNumber;
class Program
{

    public static int Sum(int[] numbers)
    {
        if (numbers == null||numbers.Length == 0) return 0; // <-- ensure empty arrays or null values result in a 0 return code (sum)
        var ourList = numbers.ToList(); // <-- Convert array to list of numbers
        ourList.Remove(numbers.Min()); // <-- Remove smallest element from list
        ourList.Remove(numbers.Max()); // <-- Remove highest element from list
        return ourList.ToArray().Sum(); // <-- return the sum for the remaining numbers (converted back into an array)
    }

    static void Main(string[] args)
    {
        var sample = new[] { 6, 2, 1, 8, 10};
        Console.WriteLine($"The sum is {Sum(sample)}");
    }
}
```