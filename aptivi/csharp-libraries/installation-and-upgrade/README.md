---
description: Learn how to install and upgrade our C# libraries
icon: compact-disc
---

# Installation and Upgrade

The most reliable way to use our libraries in your .NET application or library is to use NuGet.org as the _only_ official source. Each and every single library, application that provides extension support, or an application-library hybrid, can be installed as a NuGet package.

{% stepper %}
{% step %}
### <mark style="color:$primary;">Installation</mark>

To install our library to your .NET project, click on the below page to get started.

{% content-ref url="installation.md" %}
[installation.md](installation.md)
{% endcontent-ref %}
{% endstep %}

{% step %}
### <mark style="color:$primary;">Upgrade</mark>

To upgrade our library in your .NET project to a newer version, click on the below page.

{% content-ref url="upgrade.md" %}
[upgrade.md](upgrade.md)
{% endcontent-ref %}
{% endstep %}

{% step %}
### <mark style="color:$primary;">Attestation</mark>

It's a good practice to verify that your download is not corrupt using the methods outlined in the below page.

{% content-ref url="../attestations.md" %}
[attestations.md](../attestations.md)
{% endcontent-ref %}
{% endstep %}

{% step %}
### <mark style="color:$primary;">Building</mark>

If you want to build our project from source, click on the below page.

{% content-ref url="../building.md" %}
[building.md](../building.md)
{% endcontent-ref %}
{% endstep %}
{% endstepper %}

{% hint style="info" %}
This requires an active Internet connection to proceed. If you'd like to use your local NuGet feed, upload the appropriate packages to your feed first so that all machines that use your feed will be able to download packages from that feed. Consult [this page](https://learn.microsoft.com/en-us/nuget/hosting-packages/overview) for more information on how to host our libraries in your feed.
{% endhint %}
