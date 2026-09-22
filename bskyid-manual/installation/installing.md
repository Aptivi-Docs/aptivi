---
description: How to install?
icon: compact-disc
---

# Installing

Installing this script is easy. To install it, follow these steps, assuming that you have either `curl` or `wget` installed on your Linux system. Choose your operating system to get started:

<details>

<summary>Windows</summary>

Just use this command in your PowerShell command prompt:

```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/Aptivi/bskyid/main/src/bskyid.ps1 -OutFile bskyid.ps1
```

</details>

<details>

<summary>Linux</summary>

Installation on Linux systems can be done in two ways.

{% hint style="info" %}
You'll have to install `curl`, irrespective of what method you prefer, since this script internally uses `curl`.
{% endhint %}

### <mark style="color:$primary;">Local installation</mark>

If you want to install this script to your local home directory, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/bskyid/main/src/bskyid > $HOME/.local/bin/bskyid
$ wget -O$HOME/.local/bin/bskyid https://raw.githubusercontent.com/Aptivi/bskyid/main/src/bskyid
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ chmod +x $HOME/.local/bin/bskyid
```

### <mark style="color:$primary;">System-wide installation</mark>

If you want to make this script available to all users on your system, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/bskyid/main/src/bskyid | sudo tee /usr/local/bin/bskyid
$ sudo wget -O/usr/local/bin/bskyid https://raw.githubusercontent.com/Aptivi/bskyid/main/src/bskyid
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ sudo chmod +x /usr/local/bin/bskyid
```

</details>
