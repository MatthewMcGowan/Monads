# Monads

---

# Monoids

+++

## Set

* {2, 4, 6}
* {"Hello", "World"}
* &#2124 - all integers
* Int32
* Float

+++

## Binary Operation

![BinaryOperation](Images/Binary_operations_as_black_box.png)

+++

## Binary Operation

* +, -, \*, / 
* String concatenation

+++

## Binary Operation

```csharp
public string Repeat(string x, int times)
{
  string retVal = string.Empty;
  
  for (int i = 0; i <= times; i++)
  {
    retVal += x;
  }
  
  return retVal;
}

```

---

# .NET

+++

## Examples

* Nullable\<T>
* IEnumerable\<T>
* Task\<T>
* Func\<T>

---

# References and Images

* https://en.wikipedia.org/wiki/Monoid
* https://en.wikipedia.org/wiki/Binary_operation
