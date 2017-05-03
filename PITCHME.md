# Monads

+++

> All told, a monad in X is just a monoid in the category of endofunctors of X, with product × replaced by composition of endofunctors and unit set by the identity endofunctor.

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

+++

Amplification

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
public string Concat(string x, string y)
{
  return x + y;
}

```

---

## Monoid Definition

* Set: S
* Binary Operation: S × S → S
* Associative
* Identity element

---

## Examples

+++

Floats with multiplication

+++

```csharp
public SHA256 HashString(string value, string hashKey)
{
  ...
}
```

+++

Positive integers with addition

---

What's all this got to do with Monads?

+++

> All told, a monad in X is just a monoid in the category of endofunctors of X, with product × replaced by composition of endofunctors and unit set by the identity endofunctor.

---

What's all this got to do with programming?

+++


```csharp
Nullable<T>
```
```csharp
IEnumerable<T>
```
```csharp
Func<T>
```
```csharp
Task<T>
```

---

## Rule 1
Method to turn a value into a Monad

+++

```csharp
static Nullable<T> CreateNullable<T>(T item) where T: struct 
{
  return new Nullable<T>(item);
}
```

+++

```csharp
static IEnumerable<T> CreateIEnumerable<T>(T item)
{
    yield return item;
}
```

+++

```csharp
static Func<T> CreateFunc<T>(T item)
{
    return () => item;
}
```

+++

```csharp
static Task<T> CreateTask<T>(T item)
{
    return new Task<T>(() => item);
}
```

---

## Requirement 2
Get a value out of a Monad?

+++

```csharp
Nullable<int> a = CreateNullable(2);
Nullable<int> b = a + 1;
```

+++

```csharp
static Nullable<int> AddOne(Nullable<int> nullable)
{
    if (nullable.HasValue)
    {
        int newValue = nullable.Value + 1;
        return CreateNullable(newValue);
    }
    else
    {
        return new Nullable<int>();
    }
}
```

+++

```csharp
static Func<int> AddOne(Func<int> func)
{
    int newValue = func() + 1;
    return CreateFunc(newValue);
}
```

+++

What if we pass this to the above:

```csharp
() => DateTime.Now.Seconds
```

+++

We would like AddOne to give us:

```csharp
() => DateTime.Now.Seconds + 1
```

and not:

```csharp
() => X + 1
// X = time of new monad creation
```

+++

```csharp
static Func<int> AddOne(Func<int> func)
{
    return () =>
    {
        return func() + 1;
    };
}
```

+++

>it is not a simple wrapper around a value [...] rather, it produces an object whose structure encodes the sequence of operations that are going to happen on demand.

+++

```csharp
static IEnumerable<int> AddOne(IEnumerable<int> enumerable)
{
    foreach (var e in enumerable)
    {
        yield return e + 1;
    }
}
```

+++

Adding one is great.
Now let's generalise.

+++

```csharp
static Nullable<int> ApplyFunction(Nullable<int> nullable, Func<int, int> function)
{
    if (nullable.HasValue)
    {
        int newValue = function(nullable.Value);
        return new Nullable<int>(newValue);
    }
    else
    {
        return new Nullable<int>();
    }
}
```

+++

```csharp
static Nullable<T> ApplyFunction<T>(Nullable<T> nullable, Func<T, T> function) where T: struct
{
    if (nullable.HasValue)
    {
        T newValue = function(nullable.Value);
        return new Nullable<T>(newValue);
    }
    else
    {
        return new Nullable<T>();
    }
}
```

+++

```csharp
static Nullable<R> ApplyFunction<A, R>(
  Nullable<A> nullable, 
  Func<A, R> function) 
  where A: struct where R : struct
{
    if (nullable.HasValue)
    {
        R newValue = function(nullable.Value);
        return new Nullable<R>(newValue);
    }
    else
    {
        return new Nullable<R>();
    }
}
```

---

## Requirement 2
An operation on a wrapped value produces another wrapped value, preserving the desired "amplification"?

+++

```csharp
static Monad<R> ApplyFunction<A, R>(
  Monad<A> amplified, 
  Func<A, R> function)
```

+++

---

### References and Images

* https://en.wikipedia.org/wiki/Monoid
* https://en.wikipedia.org/wiki/Binary_operation
* https://ericlippert.com/2013/02/21/monads-part-one/ used heavily!
