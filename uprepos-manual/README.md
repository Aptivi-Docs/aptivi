---
description: Welcome to uprepos!
icon: hand-wave
---

# Welcome!

Welcome to `uprepos`, which is a very small `bash` script that lets you update all your repositories found under a folder containing all your Git repositories.

It's an abstraction of a set of commands that you'll have to execute to update all repositories in a folder so that you can save your time from having to manually update them. `uprepos` attempts to execute the following commands for every directory:

```shellsession
$ git -C Path/To/Repos fetch
$ git -C Path/To/Repos pull --recurse-submodule
$ git -C Path/To/Repos submodule update --remote
```

Remembering and writing all those commands manually is time-consuming, especially if you need a quick shortcut to all the above commands.

***

## <mark style="color:$primary;">Release notes</mark>

In `uprepos`, there have been several releases made. Below shows you the changelogs of every release, from the latest version to the oldest version.

{% updates format="full" %}
{% update date="2024-10-20" %}
## <mark style="color:$primary;">v1.5</mark>

<mark style="color:yellow;">Better support for spaces in folder names</mark>
{% endupdate %}

{% update date="2024-08-30" %}
## <mark style="color:$primary;">v1.4</mark>

<mark style="color:yellow;">We need not to do anything if there is no</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">`.git`</mark>
{% endupdate %}

{% update date="2022-09-01" %}
## <mark style="color:$primary;">v1.3</mark>

<mark style="color:yellow;">Run on current working directory if no path is specified when running this script</mark>
{% endupdate %}

{% update date="2022-08-31" %}
## <mark style="color:$primary;">v1.2</mark>

<mark style="color:green;">Added color themes</mark>
{% endupdate %}

{% update date="2022-08-08" %}
## <mark style="color:$primary;">v1.1</mark>

<mark style="color:green;">Added submodule support</mark>
{% endupdate %}

{% update date="2022-08-08" %}
## <mark style="color:$primary;">v1.0</mark>

The first public version of this script was released.
{% endupdate %}
{% endupdates %}
