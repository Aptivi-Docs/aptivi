---
description: Getting a color from a text-based color representation.
icon: badge-check
---

# Color Model Parsing

Colorimetry parses the color model representations when creating a new instance of the Color class to give you an accurate representation of the color. This is important for any color manipulation that your application does. Expand a section to get started.

<details>

<summary>Supported color model specifiers</summary>

In addition to Colorimetry supporting RGB color model, you can also use the CMYK and other color models when creating the color instances, provided that their specifiers that you must use are:

| Syntax                             | Condition                                                                                                                                                                                      |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<num>`                            | `<num>` should be of the range between 0 and 255                                                                                                                                               |
|                                    | If `<num>` is positive and larger than 255, it describes the color code from 256 up to 16777215 for true color instances, and anything higher than it will be wrapped to `0;0;0` and counting. |
| `<ColorName>`                      | Color name from either the `ConsoleColors` enumeration or the `ConsoleColor` enumeration                                                                                                       |
| `#000000`                          | Hexadecimal representation of the color for HTML fans.                                                                                                                                         |
| `#000`                             | Hexadecimal representation of the color for HTML fans.                                                                                                                                         |
| `<rrr>;<ggg>;<bbb>`                | `<rrr>`, `<ggg>`, and `<bbb>` should be of the range between 0 and 255                                                                                                                         |
| `cmyk:<ccc>;<mmm>;<yyy>;<kkk>`     | `<ccc>`, `<mmm>`, `<yyy>`, and `<kkk>` should be of the range between 0 and 100                                                                                                                |
| `cmy:<ccc>;<mmm>;<yyy>`            | `<ccc>`, `<mmm>`, and `<yyy>` should be of the range between 0 and 100                                                                                                                         |
| `hsl:<hhh>;<sss>;<lll>`            | `<hhh>` should be of the range between 0 and 360 in degrees and not radians                                                                                                                    |
|                                    | `<sss>` and `<lll>` should be of the range between 0 and 100                                                                                                                                   |
| `hsv:<hhh>;<sss>;<vvv>`            | `<hhh>` should be of the range between 0 and 360 in degrees and not radians                                                                                                                    |
|                                    | `<sss>` and `<vvv>` should be of the range between 0 and 100                                                                                                                                   |
| `hwb:<hhh>;<www>;<bbb>`            | `<hhh>` should be of the range between 0 and 360 in degrees and not radians                                                                                                                    |
|                                    | `<www>` and `<bbb>` should be of the range between 0 and 100                                                                                                                                   |
| `ryb:<rrr>;<yyy>;<bbb>`            | `<rrr>`, `<yyy>`, and `<bbb>` should be of the range between 0 and 255, just like RGB.                                                                                                         |
| `yiq:<yyy>;<iii>;<qqq>`            | `<yyy>`, `<iii>`, and `<qqq>` should be of the range between 0 and 255                                                                                                                         |
| `yuv:<yyy>;<uuu>;<vvv>`            | `<yyy>`, `<uuu>`, and `<vvv>` should be of the range between 0 and 255                                                                                                                         |
| `xyz:<xxx>;<yyy>;<zzz>`            | `<xxx>`, `<yyy>`, and `<zzz>` should be of the range between 0 and 100 in floating point units                                                                                                 |
| `yxy:<yyy>;<xxx>;<yyy>`            | The first `<yyy>` should be of the range between 0 and 100 in floating point units                                                                                                             |
|                                    | `<xxx>` and the second `<yyy>` should be of the range between 0 and 1 in floating point units                                                                                                  |
| `hunterlab:<lll>;<aaa>;<bbb>`      | `<lll>` should be of the range between 0 and 100 in floating point units                                                                                                                       |
|                                    | `<aaa>` and `<bbb>` should be of the range between -128 and 127 in floating point units                                                                                                        |
| `cielab:<lll>;<aaa>;<bbb>`         | `<lll>` should be of the range between 0 and 100 in floating point units                                                                                                                       |
|                                    | `<aaa>` and `<bbb>` should be of the range between -128 and 127 in floating point units                                                                                                        |
| `cielab:<lll>;<aaa>;<bbb>;<o>;<i>` | Same as above, but with `o` and `i` notations. See the tip below.                                                                                                                              |
| `cieluv:<lll>;<uuu>;<vvv>`         | `<lll>` should be of the range between 0 and 100 in floating point units                                                                                                                       |
|                                    | `<uuu>` should be of the range between -134 and 220 in floating point units                                                                                                                    |
|                                    | `<vvv>` should be of the range between -140 and 122 in floating point units                                                                                                                    |
| `cieluv:<lll>;<uuu>;<vvv>;<o>;<i>` | Same as above, but with `o` and `i` notations. See the tip below.                                                                                                                              |
| `cielch:<lll>;<ccc>;<hhh>`         | `<lll>` should be of the range between 0 and 100 in floating point units                                                                                                                       |
|                                    | `<ccc>` should be of the range between 0 and 131 in floating point units                                                                                                                       |
|                                    | `<hhh>` should be of the range between 0 and 230 in floating point units. It should be an angle at degrees, not radians.                                                                       |
| `cielch:<lll>;<ccc>;<hhh>;<o>;<i>` | Same as above, but with `o` and `i` notations. See the tip below.                                                                                                                              |
| `ypbprsdtv:<y>;<pb>;<pr>`          | `<y>`, `<pb>`, and `<pr>` should be of range between 0 mV and 700 mV in floating point units.                                                                                                  |
| `ypbprhdtv:<y>;<pb>;<pr>`          | `<y>`, `<pb>`, and `<pr>` should be of range between 0 mV and 700 mV in floating point units.                                                                                                  |
| `ypbprhivi:<y>;<pb>;<pr>`          | `<y>`, `<pb>`, and `<pr>` should be of range between 0 mV and 700 mV in floating point units.                                                                                                  |
| `ydbdr:<y>;<db>;<dr>`              | `<y>` should be of the range between 0 and 1 in floating point units.                                                                                                                          |
|                                    | `<db>` and `<dr>` should be of the range between -1.333 and 1.333 in floating point units.                                                                                                     |
| `lms:<lll>;<mmm>;<sss>`            | `<lll>`, `<mmm>`, and `<sss>` should be of the range between 0 and 1 in floating point units.                                                                                                  |
| `ycbcrsdtv:<y>;<pb>;<pr>`          | `<y>` should be of range between 16 and 235.                                                                                                                                                   |
|                                    | `<cb>`, and `<cr>` should be of range between 16 and 240.                                                                                                                                      |
| `ycbcrhdtv:<y>;<pb>;<pr>`          | `<y>` should be of range between 16 and 235.                                                                                                                                                   |
|                                    | `<cb>`, and `<cr>` should be of range between 16 and 240.                                                                                                                                      |
| `ycbcrhivi:<y>;<pb>;<pr>`          | `<y>` should be of range between 16 and 235.                                                                                                                                                   |
|                                    | `<cb>`, and `<cr>` should be of range between 16 and 240.                                                                                                                                      |

{% hint style="info" %}
The `o` and `i` notations represent the observer (2 or 10 degrees) and the illuminant number starting from zero. These two notations will be used to get the 3D reference values (`X`, `Y`, and `Z`) used for calculation. This is returned by the `GetIlluminantReferences()` function in `IlluminanceTools`.
{% endhint %}

{% hint style="info" %}
You can also specify just a string, an integer, a `ConsoleColor`, or a `ConsoleColor` enumeration value when making a variable that holds the `Color` class like the following:

```csharp
Color ColorInstance = 18;
Color ColorInstance = "94;0;63";
Color ColorInstance = "#0F0F0F";
Color ColorInstance = "#F0F";
Color ColorInstance = "Magenta";
Color ColorInstance = ConsoleColors.Magenta;
Color ColorInstance = ConsoleColor.Magenta;
```
{% endhint %}

</details>

***

## <mark style="color:$primary;">How to parse a color model specifier</mark>

To get a color instance from just the specifiers mentioned above, follow the below steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Pick a source specifier</mark>

You'll have to pick a source specifier. For example, if you want an RGB color instance from HSV's specifier, you must have a string that holds the HSV color specifier as mentioned above.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Parse the specifier</mark>

Call the `ParsingTools`'s `ParseSpecifier()` function, passing it that specifier, to get an RGB instance.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Convert, if needed</mark>

You can convert the RGB instance that you obtained from the previous step to HSV using the available conversion tools that you can consult in the below page.

{% content-ref url="color-model-conversions.md" %}
[color-model-conversions.md](color-model-conversions.md)
{% endcontent-ref %}
{% endstep %}
{% endstepper %}

{% hint style="info" %}
For parsing, you have two options if you don't want to rely on exceptions:

* For boolean-based checks, you can rely on the output of the `IsSpecifierValidRgbHash()`, `IsSpecifierConsoleColors()`, and `IsSpecifierValid()` on `ParsingTools`.
* If you want to also check the values, you can consult the `...AndValueValid()` sibling functions.

You can also use the color-model-specific `IsSpecifierValid()` function, such as `RedYellowBlue`.
{% endhint %}
