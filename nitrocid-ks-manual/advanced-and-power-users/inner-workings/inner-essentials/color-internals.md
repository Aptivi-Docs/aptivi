---
description: All of the colors!
icon: swatchbook
---

# Color Internals

<figure><img src="../../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

Nitrocid uses Terminaux to manipulate with the colors and configure them for the kernel to use. The kernel employs several of the color types for the kernel components, your addons, or your mods to use when writing text using the Nitrocid's console writer.

Scroll down in this page to learn more about Nitrocid-specific features. For the general color tools, you may consult the Terminaux manual for console colors:

{% content-ref url="https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/usage/console-tools/console-colors" %}
[Console Colors](https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/usage/console-tools/console-colors)
{% endcontent-ref %}

Colorimetry is also used for more general color tools, which you can consult here:

{% content-ref url="https://app.gitbook.com/s/BdESDsiuTO9fbDXLJ8HV/usage/color-sequences" %}
[Color Sequences](https://app.gitbook.com/s/BdESDsiuTO9fbDXLJ8HV/usage/color-sequences)
{% endcontent-ref %}

***

## <mark style="color:$primary;">Color types</mark>

Nitrocid provides you with the following color types to help you make an inspiring theme with nice colors for each type:

<table><thead><tr><th width="230">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>ContKernelError</code></td><td>Continuable kernel panic text (usually sync'd with Warning)</td></tr><tr><td><code>UncontKernelError</code></td><td>Uncontinuable kernel panic text (usually sync'd with Error)</td></tr><tr><td><code>NotificationTitle</code></td><td>Notification title text</td></tr><tr><td><code>NotificationDescription</code></td><td>Notification description text</td></tr><tr><td><code>NotificationProgress</code></td><td>Notification progress text</td></tr><tr><td><code>NotificationFailure</code></td><td>Notification failure text</td></tr><tr><td><code>DevelopmentWarning</code></td><td>Development warning text</td></tr><tr><td><code>StageTime</code></td><td>Stage time text</td></tr><tr><td><code>LowPriorityBorder</code></td><td>Low priority notification border color</td></tr><tr><td><code>MediumPriorityBorder</code></td><td>Medium priority notification border color</td></tr><tr><td><code>HighPriorityBorder</code></td><td>High priority notification border color</td></tr></tbody></table>
