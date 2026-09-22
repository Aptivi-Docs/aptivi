---
description: Enumerable tools to help you manipulate with them!
icon: folder-open
---

# Enumerable Tools

Enumerable extensions can be found in the `EnumerableExtensions` static class that is found under the `Magico.Enumeration` namespace. You don't have to explicitly reference the class, because you can just place a dot after the `IEnumerable` instance.

{% hint style="info" %}
You can access the extensions in one of the forms:

```csharp
// Form 1
int length = enumerableVar.Length();

// Form 2
int length2 = EnumerableExtensions.Length(enumerableVar);
```
{% endhint %}

<details>

<summary><code>Length()</code></summary>

{% code title="EnumerableExtensions.cs" lineNumbers="true" %}
```csharp
public static int Length(this IEnumerable enumerable) { }
```
{% endcode %}

This extension counts the elements inside this enumerable class instance, and it's adaptive to several enumerable types for performance, as in:

* Arrays
* Lists
* Dictionaries
* Collections
* Non-generic `IEnumerable` instances

{% hint style="info" %}
In case this extension encounters an unknown non-generic `IEnumerable` instance, it'll attempt to generate a generic `IEnumerable<object>` class prior to counting the elements.
{% endhint %}

</details>

<details>

<summary><code>GetElementFromIndex()</code></summary>

{% code title="EnumerableExtensions.cs" lineNumbers="true" %}
```csharp
public static object? GetElementFromIndex(this IEnumerable enumerable, int index) { }
```
{% endcode %}

Gets an element using the index number from the enumerable that is either generic or non-generic. It's adaptive to several enumerable types for performance, as in:

* Arrays
* Lists
* Dictionaries
* Collections
* Non-generic `IEnumerable` instances

{% hint style="info" %}
In case this extension encounters an unknown non-generic `IEnumerable` instance, it'll attempt to generate a generic `IEnumerable<object>` class prior to counting the elements.
{% endhint %}

</details>

<details>

<summary><code>Zip()</code></summary>

{% code title="EnumerableExtensions.cs" lineNumbers="true" %}
```csharp
public static IEnumerable<(TFirst First, TSecond Second)> Zip<TFirst, TSecond>(
    this IEnumerable<TFirst> source, IEnumerable<TSecond> second) { }
```
{% endcode %}

This extension merges two generic `IEnumerable` instances into one.

</details>

<details>

<summary><code>ToDictionarySafe()</code></summary>

{% code title="EnumerableExtensions.cs" lineNumbers="true" %}
```csharp
public static Dictionary<TKey, TValue> ToDictionarySafe<TSource, TKey, TValue>(
    this IEnumerable<TSource> source, Func<TSource, TKey> keySelector, Func<TSource, TValue> valueSelector)
    where TKey : notnull
{ }
```
{% endcode %}

This extension converts the source enumerable instance of the source type to a dictionary that is of a selected key type and value type. This ensures safe conversion.

</details>
