---
description: How do you use it?
icon: lightbulb-on
---

# Preface

To use this library, you first need to know exactly why do you need to install Terminaux into your console application. If your application is intended to be an interactive one, or if your application shows graphics (text, info box, ...), then Terminaux is the right library for you.

***

## <mark style="color:$primary;">Terminal actions</mark>

Terminaux provides several terminal actions, like reading an input (was on TermRead), getting color information (was on ColorSeq), and using VT sequences and filtering them (was on VT.NET).

{% hint style="info" %}
Any call to any function that require VT sequences and advanced console features, such as fancy writers and mouse pointer events, will cause Terminaux to check your console.
{% endhint %}

### <mark style="color:$primary;">Reading an input</mark>

To get started reading input, follow the below page to get started:

{% content-ref url="input-reader/" %}
[input-reader](input-reader/)
{% endcontent-ref %}

### <mark style="color:$primary;">Other console tools</mark>

For other console tools that Terminaux provides, you can access the below page:

{% content-ref url="console-tools/" %}
[console-tools](console-tools/)
{% endcontent-ref %}
