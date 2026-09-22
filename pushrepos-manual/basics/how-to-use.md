---
description: How do you use this script?
icon: question
---

# How to use?

Running this script is so easy, especially when you have to push a change to hundreds of repositories in your Git repository library (a directory containing your Git repositories) on the remote side.

***

{% stepper %}
{% step %}
### <mark style="color:$primary;">Pushing a change on the current working directory</mark>

To push a change to all the repositories on the current Git repository library, just run the script with no arguments:

```console
$ pushrepos
```
{% endstep %}

{% step %}
### <mark style="color:$primary;">Pushing a change on a specific directory</mark>

To push a change to all the repositories on any specified directory, run the script with the relative or absolute path to the directory containing your repositories:

```console
$ pushrepos Path/To/Repos
```
{% endstep %}

{% step %}
### <mark style="color:$primary;">Pushing a change on a specific directory with a message</mark>

To push a change to all the repositories on specified directory with a custom commit message, run the script with the relative or absolute path to the directory containing your repositories:

```console
$ pushrepos Path/To/Repos "General Commit Message"
```
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Depending on the commit size and your network connection speed, it might take a while.
{% endhint %}
