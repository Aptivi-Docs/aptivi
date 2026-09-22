---
description: How do you use this script?
icon: question
---

# How to use?

Running this script is so easy, especially when you have to check hundreds of repositories in your Git repository library (a directory containing your Git repositories) for updates on the remote side.

***

{% stepper %}
{% step %}
### <mark style="color:$primary;">Checking for updates on the current working directory</mark>

To check for updates on the current working directory, just run the script with no arguments:

```console
$ uprepos
```
{% endstep %}

{% step %}
### <mark style="color:$primary;">Checking for updates on a specific directory</mark>

To check for updates on any specified directory, run the script with the relative or absolute path to the directory containing your repositories:

```console
$ uprepos Path/To/Repos
```
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Depending on the repository size and your network connection speed, it might take a while.
{% endhint %}
