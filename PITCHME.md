# Monads

+++

> All told, a monad in X is just a monoid in the category of endofunctors of X, with product × replaced by composition of endofunctors and unit set by the identity endofunctor.

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

+++

![BinaryOperation](Images/Binary_operations_as_black_box_scaled.png)

+++

* +, -, \*, / 
* String concatenation

+++

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

+++

## So Far



## Associativity



+++

## Examples

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
