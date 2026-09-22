---
description: Installing our library into your project
icon: disc-drive
---

# Installation

There are two ways to install our library into your project:

* Using Visual Studio's NuGet package manager
* Manual installation

You can choose a way to install a package in a way you prefer.

***

## <mark style="color:$primary;">Visual Studio's NuGet package manager</mark>

{% hint style="info" %}
This only applies to those who are using Windows.
{% endhint %}

If you're using Visual Studio to build your project, it provides you an easy way to install NuGet packages, such as our libraries, into your project.

{% stepper %}
{% step %}
### <mark style="color:$primary;">Open your project</mark>

Open Visual Studio to a project that you want to install our libraries to.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open the NuGet package manager</mark>

Right click on either the project or the `Dependencies` entry beneath the project in the Solution Explorer pane and select `Manage NuGet packages...`

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Search for a library</mark>

Click on `Browse` and click on the `Search` text box. Then, write the desired library you'd like to install, such as Terminaux.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Install a library</mark>

Click on any of the libraries that show up in the search results, and click on `Install`.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Accept the license</mark>

If any package asks for your acceptance of the license, read the license contained by clicking on their license names, then click on `I Accept`.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Verify the installation</mark>

The package is installed! Verify by expanding the `Dependencies` entry beneath the project and expanding the `Packages` entry.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

***

## <mark style="color:$primary;">Manual installation</mark>

If you'd like to manually install a NuGet package to a project with your favorite editor or if you're unable to use Visual Studio for some reason, you can use this installation method. However, this method comes in two ways:

* Visual Studio
* Text editor

### <mark style="color:$primary;">Visual Studio</mark>

If you are using Visual Studio, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Open your project</mark>

Open Visual Studio to a project that you want to install our libraries to.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open the project file</mark>

Double click on the project as shown in the Solution Explorer pane

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Add a library reference</mark>

Place this snippet at the end of the project file just before the `</Project>` designator (replace `Terminaux` with any other library and `8.0.14` with the desired version of the library)

```xml
<ItemGroup>
  <PackageReference Include="Terminaux" Version="8.0.14" />
</ItemGroup>
```
{% endstep %}

{% step %}
### <mark style="color:$primary;">Save project and restore packages</mark>

Save the project file. It should automatically install the required packages. If, however, the package restoration didn't automatically start, right-click on the solution and select `Restore NuGet Packages`.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

### <mark style="color:$primary;">Text editor</mark>

If you are using your favorite text editor, such as Visual Studio Code or Sublime Text, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Open your project folder</mark>

Open the file explorer and navigate to the target project directory that contains the project file (not the solution `.sln` or `.slnx` file)

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open your text editor</mark>

Right-click on the project file -> `Open With` -> your favorite text editor

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Add a library reference</mark>

Place this snippet at the end of the project file just before the `</Project>` designator (replace `Terminaux` with any other library and `8.0.14` with the desired version of the library)

```xml
<ItemGroup>
  <PackageReference Include="Terminaux" Version="8.0.14" />
</ItemGroup>
```
{% endstep %}

{% step %}
### <mark style="color:$primary;">Save project and restore packages</mark>

Save the project file. Then, open the terminal emulator in your preferred way and execute `dotnet restore`.
{% endstep %}
{% endstepper %}
