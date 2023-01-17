Date of Completion: 16-01-2023
This is a fairly straight thing really, we create a copy of the list then iterate through each item, replace it with its opposite (check [[CodeWars/Completed Solutions/Opposite Numbers Solution]]), finally return the copied list.
```csharp
namespace InvertValues;
class Program
{
    public static int[] InvertValues(int[] input)
    {
      List<int> dump = new List<int>();
      if (input.Length==0|| input == null) return dump.ToArray();
      foreach (int value in input) {
        dump.Add(value*-1);
      }
      return dump.ToArray();
    }

    static void Main(string[] args)
    {
        var sample1 = new[] {-1,-2,-3,-4,-5};
        var sample2 = new[] {-1,2,-3,4,-5};
        var sample3 = new int[] {}; // <-- This is the more verbose version of the other arrary definitions
        var sample4 = new[] {0};
        int[] result1 = InvertValues(sample1);
        int[] result2 = InvertValues(sample2);
        int[] result3 = InvertValues(sample3);
        int[] result4 = InvertValues(sample4);

        Console.WriteLine($"Sample 1 : {sample1.ToString()} | Result 1 : {result1.ToString()}");
        Console.WriteLine($"Sample 2 : {sample2.ToString()} | Result 2 : {result2.ToString()}");
        Console.WriteLine($"Sample 3 : {sample3.ToString()} | Result 3 : {result3.ToString()}");
        Console.WriteLine($"Sample 4 : {sample4.ToString()} | Result 4 : {result4.ToString()}");
    }
}
```