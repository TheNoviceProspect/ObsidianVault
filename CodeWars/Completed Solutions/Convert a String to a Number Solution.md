Date of Completion: 16-01-2023
A simple approach to use TryParse() on a string, if it returned true (successful parse) then return the numerical result, otherwise return 0
```csharp
using System;
  public class Kata
  {
    public static int StringToNumber(String str) {
      int output = 0;
      bool result = int.TryParse(str, out output);
      if (!result) return 0; else return output;
  }
}
```