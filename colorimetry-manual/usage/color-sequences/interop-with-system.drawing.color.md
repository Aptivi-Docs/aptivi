---
description: Colorimetry's Color meets System.Drawing's Color!
icon: paintbrush-fine
---

# Interop with System.Drawing.Color

We've introduced a new way to interact with `System.Drawing`'s [`Color`](https://learn.microsoft.com/en-us/dotnet/api/system.drawing.color?view=net-8.0) struct! You can find all the tools in the `SystemColorConverter` class. The `Color` struct from `System.Drawing` represents the four color components:

* Alpha (A): Color opaqueness level. 0% means 100% transparency.
* Red (R): Red color level.
* Green (G): Green color level.
* Blue (B): Blue color level.

***

## <mark style="color:$primary;">SystemColorConverter class</mark>

This class provides the following functions:

{% code title="SystemColorConverter.cs" lineNumbers="true" %}
```csharp
public static OurColor FromDrawingColor(DrawingColor drawingColor) { }
public static DrawingColor ToDrawingColor(OurColor ourColor) { }
```
{% endcode %}

Depending on your use-case, use one of the functions:

* From `System.Drawing.Color` to Colorimetry's `Color`: Use the `FromDrawingColor()` function.
* From Colorimetry's `Color` to `System.Drawing.Color`: Use the `ToDrawingColor()` function.

{% hint style="info" %}
This is useful if you're interacting with applications that use `System.Drawing`'s `Color`.
{% endhint %}
