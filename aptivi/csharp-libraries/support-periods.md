---
description: Not all versions of libraries are supported.
icon: question
---

# Support Periods

When a library is released, it typically comes with just one version series, which is typically 1.x or 0.1.x. Only eligible projects can have their own support period for all versions in the series.

***

## <mark style="color:$primary;">Version legend</mark>

The version legend is used in the changelogs for every single version that was released, when the version series is under support:

* <mark style="color:green;">**Green**</mark>: Indicates additions
* <mark style="color:yellow;">**Yellow**</mark>: Indicates improvements
* <mark style="color:red;">**Red**</mark>: Indicates removals
* <mark style="color:purple;">**Purple**</mark>: Indicates something else

***

## <mark style="color:$primary;">General support cadence</mark>

In general, projects that are eligible for support periods can follow this guide:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Projects that reached 1.x or later</mark>

As soon as the new 1.x version series starts, such as Terminaux 7.0.x to 8.0.x, the support period ending will be assigned immediately under the following:

* One-year window is applied to projects that get updated frequently.
* Two-year window is applied to projects that get updated less frequently.
* Three-year window is applied to projects that get updated occasionally in an unplanned schedule.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Projects that are in the 0.x.y series</mark>

As soon as the new 0.x.y version series starts, such as Nitrocid 0.1.0 to 0.1.1, the support period ending will be assigned immediately under the following:

* Nine-month window is applied to projects that get updated frequently.
* One-year window is applied to projects that get updated less frequently.
* Two-year window is applied to projects that get updated occasionally in an unplanned schedule.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Projects that are in the 0.0.x.y series</mark>

There is no support for these versions except the latest version, which won't last long. As soon as the library or the application moves to the 0.x.y series or the x.y.z series, none of the 0.0.x.y series will be in support.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
When a beta version of a specific version series is announced, the beta versions are supported through the lifetime of the testing period until the first public release of the version, after which all beta versions expire.

For example, Nitrocid KS 0.0.6 had a beta testing period that lasted 6 versions (0.0.5.9 -> 0.0.5.14) until the first public release.
{% endhint %}

***

## <mark style="color:$primary;">Exceptions</mark>

Applications and libraries may have exceptions that deviate from the general support plan shown above.

The following projects that were given exceptions are here:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Nitrocid</mark>

The following release support terms are divided into two sections:

* <mark style="color:$primary;">**Short term releases**</mark>: 9 months for each minor release (such as 0.1.1 and 0.1.2)
* <mark style="color:$primary;">**Long term releases**</mark>: 5 years of non-security fixes and 5 years of security and critical fixes for each major release (such as 0.1.0 and 0.2.0)

You can consult the supported versions list [here](https://app.gitbook.com/s/yhORwVwuIgJMLsQRqN3S/versions-and-compatibility/supported-versions).
{% endstep %}

{% step %}
### <mark style="color:$primary;">BassBoom and MediaBoom</mark>

The following release support terms are divided into two sections:

* <mark style="color:$primary;">**Short term releases**</mark>: Versions like 1.1.0, 1.3.0, etc. will get 1 year of support
* <mark style="color:$primary;">**Long term releases**</mark>: Versions like 1.0.0, 1.2.0, etc. will get 5 years of support

The current supported versions are:

* <mark style="color:$primary;">**1.0.x.y series**</mark>: Supported until May 1st, 2031.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Terminaux</mark>

The following release support terms are divided into two sections:

* <mark style="color:$primary;">**Short term releases**</mark>: Versions like 7.0.0, 9.0.0, etc. will get 1 year of support
* <mark style="color:$primary;">**Long term releases**</mark>: Versions like 8.0.0, 10.0.0, etc. will get 5 years of support

The current supported versions are:

* <mark style="color:$primary;">**8.x.x series**</mark>: Supported until October 13th, 2030.
{% endstep %}
{% endstepper %}

***

## <mark style="color:$primary;">Operating system support</mark>

When it comes to supporting operating systems in our apps, the below support dates will override the above main support dates if the end of our support of an operating system comes before the main support date.

{% tabs %}
{% tab title="Windows" %}
Windows versions have a long term support duration for each major version.

| Version    | Support status | End of support   |
| ---------- | -------------- | ---------------- |
| Windows 11 | Supported      | To be determined |
| Windows 10 | Supported      | May 1st, 2031    |
{% endtab %}

{% tab title="macOS" %}
Generally, a macOS version will end its support three years after the initial release.

| Version                | Support status | End of support    |
| ---------------------- | -------------- | ----------------- |
| macOS 27 (Golden Gate) | Supported      | To be determined  |
| macOS 26 (Tahoe)       | Supported      | To be determined  |
| macOS 15 (Sequoia)     | Supported      | October 1st, 2027 |
| macOS 14 (Sonoma)      | Supported      | October 1st, 2026 |
{% endtab %}

{% tab title="Linux" %}
We support running our applications on Linux distributions, as long as the following conditions are met:

* A non-rolling Linux distro version you're running, such as Ubuntu, must be supported.
* A rolling Linux distro you're running, such as Arch Linux, must receive continuous updates.
* For .NET projects, a distro must provide updates for the appropriate .NET runtime version.

For our projects, our main support dates can be overridden if the distro version becomes unsupported before the main support date.
{% endtab %}

{% tab title="FreeBSD" %}
We update our projects to support the latest version of FreeBSD. When a FreeBSD version series ends its support, we end our support, too.

| Version | Support status | End of support       |
| ------- | -------------- | -------------------- |
| v15.0   | Supported      | September 30th, 2026 |
| v15.1   | Supported      | March 31st, 2027     |

If you are running a FreeBSD version not listed here, there's no guarantee that our projects will work in your FreeBSD system.
{% endtab %}

{% tab title="Android" %}
We support running our applications on Android devices under the following conditions:

* The manufacturer must be able to provide security updates to their Android devices for the minimum of 3 years.
* The manufacturer must be able to provide at least 2 Android version upgrades.
* Your device must be manufactured after 2021 with an ARM64 processor.

Please note that:

* We don't officially offer support for Android 11 or lower
* We don't officially offer support for non-Samsung devices (Google Pixel, Huawei, Xiaomi, etc.)
* We don't officially offer support for Android versions that we don't have access to yet

For Samsung users, we are offering support for One UI 6.0 as the minimum version up to One UI 8.x as the maximum version. The following support periods can be found below:

| Version                 | Support status    | End of support      |
| ----------------------- | ----------------- | ------------------- |
| One UI 6.x (Android 14) | Supported         | December 30th, 2027 |
| One UI 7.0 (Android 15) | Supported         | December 2nd, 2032  |
| One UI 8.x (Android 16) | Supported         | December 2nd, 2032  |
| One UI 9.x (Android 17) | Not supported yet | To be determined    |
{% endtab %}
{% endtabs %}
