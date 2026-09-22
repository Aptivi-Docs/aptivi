---
description: We need colors!
icon: palette
---

# Color Sequences

Colorimetry provides a functionality to generate color sequences and to get information about colors themselves. It allows you to generate a color with three modes:

* 16 colors
* 256 colors
* 16-bit colors (true color)

This functionality contains several functions that you can make use of in your application:

* Building a `Color` instance that supports RGB and 255-color modes
* Getting console color information from the 255-color mode
* Simulating color-blindness during compilation
* Applying transparency using the `Opacity` settings in the `ColorSettings` instance

More functionality is available in the right pane for conversion, parsing, and more.

***

## <mark style="color:$primary;">Building a</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">`Color`</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">instance</mark>

You can build your own `Color` instance for usage in your application using a variety of ways. Choose a section to expand.

<details>

<summary>Color specifier syntax</summary>

You can use a constructor to specify a `ColorSpecifier`, which can be of the syntax specified in another page. Click the button below to learn more.

<a href="color-model-parsing.md" class="button primary">Color model parsing</a>

</details>

***

## <mark style="color:$primary;">Color information</mark>

There are several properties that you can use to get color information. You can also get the color ID if you used color number from 0 to 255 by referencing the `ColorId` property. This property returns the nearest color ID for true color.

{% hint style="info" %}
In addition to the `PlainSequence` property, you can also use the `ToString()` function to get the same value from that property. This allows easier string interpolation, such as:

```csharp
BoxFrameTextColor.WriteBoxFrame($"Red, Green, and Blue: {selectedColor}", hueBarX, rgbRampBarY, boxWidth, boxHeight + 2);
```
{% endhint %}

There are several actions you can do with the color information, including:

<details>

<summary>Terminal emulator's color palette</summary>

You can choose whether to use your terminal emulator's color palette or to use the real colors that come from the true colors. By default, Terminaux 8.1 or higher chooses to use the terminal emulator's color palette to maintain consistency.

</details>

<details>

<summary>Obtaining a list of known colors and web colors</summary>

You can get detailed information about the console color ranging from 0 to 255 by calling the `GetColorData()` function under the `ConsoleColorData` class:

```csharp
public static partial ConsoleColorData[] GetColorData();
```

Similarly, you can also get the web-safe color list by using the `WebSafeColors` class and the `GetColorList()` function. Properties that specify every color are also available under the same class.

{% hint style="info" %}
You can use this data as a general-purpose color data, and is not specific to console applications.
{% endhint %}

</details>

<details>

<summary>Obtaining RGB information</summary>

You can get the RGB information by simply calling the `RGB` property in the `Color` class. From there, you'll get an instance of `RedGreenBlue` that contains the `R`, `G`, `B`, and their normalized properties.

{% hint style="info" %}
You can also get this information from the color code using the `GetRgbFromColorCode()` function. The string representation can also be get using the `GetRgbSpecifierFromColorCode()` function.
{% endhint %}

You can convert this color model instance to various color models, such as `RYB`, `CMY`, `YUV`, and `HSV`. In order to do this, consult the below page:

<a href="color-model-conversions.md" class="button primary">Color model conversions</a>

</details>

<details>

<summary>Obtaining color name and enumeration</summary>

You can get the color name for all the color types according to the nearest color that is selected in accordance to the X11 color map. Just use the `Name` property in a `Color` instance to get the color name.

{% hint style="info" %}
You can also get the nearest color information using either the `Color` instance, the RGB instance, or the RGB numbers using `GetNearestColor()` found in `ConsoleColorData`. Then, you can get this information to return the equivalent `Color` instance using the `Color` property.
{% endhint %}

For color enumeration, a `Color` class contains the following properties:

| Property       | Description                                                                                                                                        |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ColorEnum255` | Always populated related to the nearest matching color in the X11 color map. Can be used for `ConsoleColors` enumeration found within Colorimetry. |
| `ColorEnum16`  | Is not populated for color IDs that exceed `15`. Can be used for `ConsoleColor` enumeration found within the C# standard library.                  |

</details>

<details>

<summary>Obtaining brightness and contrast</summary>

You can check to see if a color is a light or a dark color using the `Brightness` property, which returns either of the following:

* `Dark`
* `Light`

</details>

<details>

<summary>Obtaining a gray color</summary>

You can get a gray color either for the current background color or for your custom background color using the `GetGray()` function. This allows you to easily get an appropriate color if you want to write something in it and you don't know what color to choose.

{% code title="ColorTools.cs" lineNumbers="true" %}
```csharp
public static Color GetGray() { }
public static Color GetGray(Color color) { }
```
{% endcode %}

{% hint style="info" %}
The color brightness and contrast feature is used to determine the appropriate gray color, which contains a function found in the same class.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Color transformation</mark>

Color transformation is another feature of Colorimetry to allow you to transform the color using one or more of the formulas.

<details>

<summary>Transformation formulas</summary>

The following transformation formulas are available:

<table><thead><tr><th width="140">Formula</th><th width="140.3333740234375">Sub-type</th><th>Description</th></tr></thead><tbody><tr><td><code>ColorBlind</code></td><td><code>Protan</code></td><td>Color blindness simulation with Vienot and Brettel's formula. Red/green color blindness. It makes red look more green.</td></tr><tr><td></td><td><code>Deutan</code></td><td>Red/green color blindness. It makes green look more red.</td></tr><tr><td></td><td><code>Tritan</code></td><td>Blue/yellow color blindness.</td></tr><tr><td><code>Cyanotype</code></td><td></td><td>Makes all colors represent just the cyan shades.</td></tr><tr><td><code>Inverse</code></td><td></td><td>Reverse video.</td></tr><tr><td><code>Monochromacy</code></td><td><code>Monochrome</code></td><td>All grayscale and colored shade colors. Grayscale.</td></tr><tr><td></td><td><code>Red</code></td><td>Red shades</td></tr><tr><td></td><td><code>Green</code></td><td>Green shades</td></tr><tr><td></td><td><code>Blue</code></td><td>Blue shades</td></tr><tr><td></td><td><code>Cyan</code></td><td>Cyan shades</td></tr><tr><td></td><td><code>Magenta</code></td><td>Magenta shades</td></tr><tr><td></td><td><code>Yellow</code></td><td>Yellow shades</td></tr><tr><td><code>Sepia</code></td><td></td><td>Takes you to the old times.</td></tr></tbody></table>

</details>

<details>

<summary>How to transform color</summary>

In order to simulate color blindness and other color transformation formulas, you can change the value of the `Transformations` property in the `Color` instance that you want to edit.

This property is an array of transformation formula classes based on `BaseTransformationFormula` and `ITransformationFormula` that provide the following properties:

* `Frequency`
  * Specifies the density ranging between 0.0 and 1.0 from lowest to highest

{% hint style="info" %}
Depending on the `Render()` implementation of the transformation formula classes, it may or may not take note of the `Frequency` value. However, it's recommended to use it for general purposes, except if you can't do it for some reason.
{% endhint %}

Once the new class instance is created with the `Transformations` property being populated with several transformations, you can get a transformed color.

</details>

<details>

<summary>Obtaining a color contrast ratio</summary>

If you want to get a color contrast ratio, you can use the `GetContrast()` function found in the `TransformationTools` class that returns a contrast ratio in double-precision floating point value.

```csharp
public static double GetContrast(Color firstColor, Color secondColor) { }
```

This uses the `GetLuminance()` function, which is available in the public API. It lets you get the luminance rate for a color instance.

```csharp
public static double GetLuminance(Color color) { }
```

</details>

<details>

<summary>Obtaining dark and light backgrounds of a color</summary>

If you want a darker version of your color, you can use the `GetDarkBackground()` function, passing it the source color that you want to darken in a new copy of the `Color` class. This is normally suitable for backgrounds that are responsive.

```csharp
public static Color GetDarkBackground(Color source) { }
```

If you want a lighter version of your color, you can use the `GetLightBackground()` function, passing it the source color that you want to lighten in a new copy of the `Color` class. This is normally suitable for backgrounds that are responsive.

```csharp
public static Color GetLightBackground(Color source) { }
```

</details>

<details>

<summary>Obtaining a saturated and desaturated color</summary>

You can saturate the color to make it lighter, and desaturate the color to make it darker. This manipulates the saturation value in the HSL representation of the color.

```csharp
public static Color Desaturate(Color source, int target) { }
public static Color Saturate(Color source, int target) { }
```

</details>

<details>

<summary>Obtaining a dark and light color</summary>

You can darken the color to appear darker, and lighten the colors to appear lighter. This manipulates the lightness value in the HSL representation of the color.

```csharp
public static Color Darken(Color source, int target) { }
public static Color Lighten(Color source, int target) { }
```

</details>

<details>

<summary>Other color transformations</summary>

### <mark style="color:$primary;">Spins and Complements</mark>

You can not only spin the color using a specified hue angle to add to the HSL angle from the color, but you can also get a complement by adding 180 to the hue angle in degrees.

```csharp
public static Color Spin(Color source, int target) { }
public static Color Complement(Color source) { }
```

</details>

***

## <mark style="color:$primary;">Color contrast</mark>

The color contrast tools provides you with various tools for color contrast and its manipulation functions.

<details>

<summary>Determining the "seeability"</summary>

{% code title="ColorContrast.cs" lineNumbers="true" %}
```csharp
public static bool IsSeeable(Color color) { }
public static bool IsSeeable(ColorType type, int colorLevel, int colorR, int colorG, int colorB, ColorSettings? settings = null) { }
```
{% endcode %}

You can determine the color "seeability" using this function. The color can be considered "seeable" if it meets the following conditions:

* The color type is either a 256- or a 16-color and not one of the following colors:
  * `ConsoleColors.Black`
  * `ConsoleColors.Grey0`
  * `ConsoleColors.Grey3`
  * `ConsoleColors.Grey7`
* The color type is a true color and all the RGB levels are above 30 out of 255.

</details>

<details>

<summary>Determining the color contrast with NTSC</summary>

You can get the color contrast (either black or white) using the `Y` (luma) component of the YIQ color model used by NTSC 1953 by calling the below function:

{% code title="ColorContrast.cs" lineNumbers="true" %}
```csharp
public static Color GetContrastColorNtsc(this Color color)
```
{% endcode %}

It returns either black or white, depending on the luma part of the color calculated using this formula:

<p align="center"><span class="math">Y = ((r * (0.299 * 1000)) + (g * (0.587 * 1000)) + (b * (0.114 * 1000))) / 1000</span></p>

If the color luma is bigger than 128, it returns the black color for high contrast. Otherwise, white.

</details>

<details>

<summary>Determining the color contrast using half-white color number</summary>

You can also get the color contrast using the half-white color number method by consulting the below function:

{% code title="ColorContrast.cs" lineNumbers="true" %}
```csharp
public static Color GetContrastColorHalf(this Color color)
```
{% endcode %}

This function makes use of a formula that divides the number (`0xffffff`) by 2, making a color number of half white. It takes a decimal version of the RGB color and compares it to that of the half-white number. If the RGB decimal is bigger than the half-white color, it gives you the black color for high contrast. Otherwise, white.

</details>

***

## <mark style="color:$primary;">Using settings</mark>

You can also generate colors with your specific settings, such as color transformation formula, by making a new instance of `ColorSettings` to store your own color settings.

However, by passing in your new instance of `ColorSettings`, you're affecting this color generation only once. To make it affect all generations, you'll have to change the global color settings, which can be found on `ColorTools.GlobalSettings`.

{% hint style="info" %}
Any change to a value in the global settings affects all color generations. Use your instance of `ColorSettings`, if possible.
{% endhint %}

You can also use your `ColorSettings` instance when parsing your color specifier.

<details>

<summary>Specifying the color opacity</summary>

Whenever it comes to opacity, Colorimetry attempts to simulate the transparency using the chosen opacity color. However, you can override that by selecting a color that would be faded to when transparency is applied.

{% code title="ColorSettings.cs" lineNumbers="true" %}
```csharp
public int Opacity
{
    (...)
}

public Color OpacityColor
{
    (...)
}
```
{% endcode %}

When the opacity is set to 255, you're making a completely opaque color that holds just the color that you've chosen. However, when you choose any other opacity, such as 50% transparent (128), you're mixing 50% of your color with 50% of either the black color or your selected opacity blending color. If you choose 0%, you're essentially getting the opacity color that is opaque.

{% hint style="info" %}
Generally, it's recommended to set these two properties in a separate `ColorSettings` instance, unless you're making experiments. The color selector allows you to select the global transparency, but it may affect all the colors, even if closed.
{% endhint %}

{% hint style="warning" %}
This is not a real transparency, but a simulated one. That doesn't make text and elements rendered on top of the elements visible for the opacity that you choose. For example, you don't get to see text that is over-written by another text if you set the opacity.

Additionally, the default color that gets chosen is the black color, which may not match the background color of the terminal in console applications. In this case, you'll have to manually set the opacity color to the current background color.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Other tools</mark>

In addition to the above features, you can also make use of the other tools below. Expand one to get started.

<details>

<summary>X11 and ConsoleColor translation</summary>

You can translate from X11 to ConsoleColor and vice versa using the below functions. The `ConsoleColor` enumeration has an order of colors that is slightly different from the X11 colormap definitions for the first 16 colors. The following colors differ from each other:

| ConsoleColor              | X11                      |
| ------------------------- | ------------------------ |
| `ConsoleColor.DarkBlue`   | `ConsoleColors.DarkRed`  |
| `ConsoleColor.DarkCyan`   | `ConsoleColors.Olive`    |
| `ConsoleColor.DarkRed`    | `ConsoleColors.DarkBlue` |
| `ConsoleColor.DarkYellow` | `ConsoleColors.DarkCyan` |
| `ConsoleColor.Blue`       | `ConsoleColors.Red`      |
| `ConsoleColor.Cyan`       | `ConsoleColors.Yellow`   |
| `ConsoleColor.Red`        | `ConsoleColors.Blue`     |
| `ConsoleColor.Yellow`     | `ConsoleColors.Aqua`     |

In the `ColorTools` class, you can find two functions that translate between the two color mappings:

*   If you want to translate from `ConsoleColor` to X11's representation (`ConsoleColors`), use the `TranslateToX11ColorMap()` function, provided that its signature is:<br>

    ```csharp
    public static ConsoleColors TranslateToX11ColorMap(ConsoleColor color) { }
    ```
*   If you want to translate from `ConsoleColors` to .NET's representation (`ConsoleColor`), use the `TranslateToStandardColorMap()` function, provided that its signature is:<br>

    ```csharp
    public static ConsoleColor TranslateToStandardColorMap(ConsoleColors color) { }
    ```

</details>

<details>

<summary>ConsoleColor map correction for X11</summary>

Colorimetry also provides a function that gets the correct color mapping for the specified color. The function is found under `ColorTools`, called `CorrectStandardColor()`. The signature is defined below:

```csharp
public static ConsoleColor CorrectStandardColor(ConsoleColor color) { }
```

</details>

<details>

<summary>Gradients generation</summary>

Colorimetry also supports creating a list of intermediate colors that would transition from either the source color or multiple colors to the target color. This is called gradients. This feature aims to make implementing the gradients easier than before.

Just specify the source color that you want to transition from, the target color that you want to transition to, and the number of steps needed, and call `ColorGradients`'s `GetGradients()`. You will need to assign a variable to hold an instance of `ColorGradients`.

```csharp
public static ColorGradients GetGradients(Color sourceColor, Color targetColor, int steps)
```

{% hint style="info" %}
You can enumerate through all the gradients either with the for-loop or the foreach-loop to get all their intermediate color. This ensures that it covers all the intermediate colors in exactly the number of steps that you've specified.
{% endhint %}

In addition to that, you can specify an array of target colors with their level ranging from 0.0 to 1.0, as well as specifying the end color. Use the below function to get started:

```csharp
public static ColorGradients GetGradients((double, Color)[] colors, Color ending, int steps)
```

</details>

<details>

<summary>Shades, tints, and stage levels</summary>

There are types of gradients that are also implemented:

* Shades: It returns a list of colors that go from the selected color down to the black color. You can use the `GetShades()` function.
* Tints: It returns a list of colors that go from the selected color up to the white color. You can use the `GetTints()` function.
* Stage level: It returns a color that specifies the stage level of a specified number according to the stage positions. It uses the gradient function if you're using the smooth version. You can use the `StageLevelSmooth()` function.

</details>
