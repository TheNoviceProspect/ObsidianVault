Date of Completion: 08-01-2023
parse each string into a number and then check whether or not it is lower than five or not

```csharp
internal class Program
{
    public static string FakeBin(string x)
    {
        // The Kata actually requires us to set this to "" instead since we don't have access to the String namespace
        var result = String.Empty;
        for (int i = 0; i < x.Length; i++)
        {
            int num;
            int.TryParse(x[i].ToString(), out num);
            if (num<5) result = result+"0"; else result = result+"1";
        }
        return result;
    }

    private static void Main(string[] args)
    {
        Console.WriteLine("Hello, World!");
        var input = "45385593107843568";
        Console.WriteLine(FakeBin(input));
    }
}
```