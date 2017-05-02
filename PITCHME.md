# Monads

+++

> All told, a monad in X is just a monoid in the category of endofunctors of X, with product × replaced by composition of endofunctors and unit set by the identity endofunctor.

---

# Monoids

---

## Set

* {2, 4, 6}
* {"Hello", "World"}
* ℤ - all integers
* Int32
* Float

---

## Binary Operation

+++

![BinaryOperation](Images/Binary_operations_as_black_box_scaled.png)

+++

* +
* -
* \*
* / 
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

---

S × S → S

+++

string x int32 → string

---

## Associativity

+++

A x (B x C) = (A x B) x C

---

## Identity Element

+++

Integer Multiplication

+++

Integer Addition

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

---

## Examples

+++

Positive integers with addition

+++

Floats with multiplication

+++

```csharp
public SHA256 HashString(string value, string hashKey)
{
  ...
}
```

---

# .NET

+++

```csharp
Nullable<T>
```
```csharp
IEnumerable<T>
```
```csharp
Task<T>
```
```csharp
Func<T>
```

---

### References and Images

* https://en.wikipedia.org/wiki/Monoid
* https://en.wikipedia.org/wiki/Binary_operation
