---
description: Making your own themes easily.
icon: palette
---

# Theme Studio

<figure><img src="../../../.gitbook/assets/image (339).png" alt=""><figcaption></figcaption></figure>

The theme studio allows you to make your own custom themes easily by letting you edit every single color type. It provides you with a fully-fledged color wheel provided by Terminaux to ensure that what you select is accurate and tailored to your needs. You can simply run this program by running the `mktheme <name>` command.

This saves you the need of manually making a JSON file containing theme data, whose specification can be found here:

{% content-ref url="https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/usage/console-tools/console-themes" %}
[Console Themes](https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/usage/console-tools/console-themes)
{% endcontent-ref %}

***

## <mark style="color:$primary;">Available options</mark>

Once you're done making your own theme, the theme studio provides you with these options:

<table><thead><tr><th width="130">Keybinding</th><th>Description</th></tr></thead><tbody><tr><td><code>ENTER</code></td><td>Changes color for a specific color type</td></tr><tr><td><code>F1</code></td><td>Copies current color to another color type</td></tr><tr><td><code>F2</code></td><td>Saves the theme file to the current directory</td></tr><tr><td><code>F3</code></td><td>Loads a theme from a theme JSON file</td></tr><tr><td><code>F4</code></td><td>Saves the theme file to a specified directory</td></tr><tr><td><code>F5</code></td><td>Saves the theme file to the current directory as another name</td></tr><tr><td><code>F6</code></td><td>Saves the theme file to a specified directory as another name</td></tr><tr><td><code>F7</code></td><td>Loads a theme from one of the pre-built themes</td></tr><tr><td><code>F8</code></td><td>Loads the current colors and undoes any changes made.</td></tr></tbody></table>

Once you're done with the theme, the theme studio doesn't automatically save your theme file. Therefore, you'll have to manually save it by pressing `F2`.

{% hint style="info" %}
You can set your kernel theme to use your custom theme by executing the `themeset` command with the path to your theme JSON file as the first argument, such as `themeset Colorful.json`.
{% endhint %}
