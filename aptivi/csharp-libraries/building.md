---
description: How do you build our library?
icon: trowel-bricks
---

# Building

You can comfortably build our library using the command line, since it's the most lightweight solution. However, if you're running Windows, Visual Studio will help you build it. However, you must have the prerequisites before being able to build it.

* [.NET 10.0 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/10.0)
* [Git command-line tool](https://git-scm.com/install/windows)

In order to be able to have a successful build, please choose your preferred method:

<details>

<summary>Visual Studio 2026 - Windows</summary>

Before being able to build our projects, please make sure that you have at least Visual Studio 2026 version 18.0 or later that supports building projects for .NET 10.0. You can get Visual Studio [here](https://visualstudio.microsoft.com/).

Once you have Visual Studio installed with at least the .NET 10.0 SDK and the .NET development workload, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Open Visual Studio</mark>

Open Visual Studio and press `Clone Repository`
{% endstep %}

{% step %}
### <mark style="color:$primary;">Write the repository location</mark>

In the repository location field, write `https://github.com/Aptivi/<project>.git`

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Clone the repository</mark>

Press `Clone`. The clone may need to take a few minutes depending on your Internet connection.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open the solution</mark>

Press `Solution Explorer` » `Switch Views` and double click on `<project>.slnx`

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Build the solution</mark>

Press `F6` on your keyboard, or press `Build` » `Build Solution` to build

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

</details>

<details>

<summary>Command-line - All platforms</summary>

If you are a hardcore command-line user or if you prefer using the command-line, follow these steps to build our project right from the command line:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Open your terminal emulator</mark>

Open your terminal emulator on your work directory
{% endstep %}

{% step %}
### <mark style="color:$primary;">Clone the repository</mark>

Execute `git clone https://github.com/Aptivi/<project>.git`
{% endstep %}

{% step %}
### <mark style="color:$primary;">Build the repository</mark>

Navigate to the cloned repository, `Nitrocid`, then execute `adt build`

If you don't want to install Python and ADT, execute `make dbg` for debug builds and `make` for release builds, or `dotnet restore` and `dotnet build`
{% endstep %}

{% step %}
### <mark style="color:$primary;">Run the project (if it's an app)</mark>

If the project is an app, after building is done, run `dotnet run`
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Please consider the following tips:

* To ensure the best build experience, install Python and install the ADT Python PIP package using `pip install --upgrade aptivi-adt`.
* We recommend that you use `make` to build our projects, since it automatically checks for .NET installation and prepares the environment, and implicitly calls ADT.
* If you are building our project on Android, it's recommended that you build the project on a powerful Android device as the building overhead may negatively impact the performance of your phone or tablet.
{% endhint %}

</details>
