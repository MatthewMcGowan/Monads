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

![BinaryOperation](https://github.com/MatthewMcGowan/Monads/tree/master/Images/Binary_operations_as_black_box.svg.png)

+++

## Binary Operation

* +, -, \*, / 
* String concatenation

+++

## Binary Operation

```csharp
public string Repeat(string x, int times)
{
  string retVal;
  
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
