---
description: How to install?
icon: compact-disc
---

# Installing

Installing this script is easy. To install it, follow these steps, assuming that you have either `curl` or `wget` installed on your Linux system.

<details>

<summary>Local installation</summary>

If you want to install this script to your local home directory, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/dotify/main/dotify > $HOME/.local/bin/dotify
$ wget -O$HOME/.local/bin/dotify https://raw.githubusercontent.com/Aptivi/dotify/main/dotify
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ chmod +x $HOME/.local/bin/dotify
```

</details>

<details>

<summary>System-wide installation</summary>

If you want to make this script available to all users on your system, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/dotify/main/dotify | sudo tee /usr/local/bin/dotify
$ sudo wget -O/usr/local/bin/dotify https://raw.githubusercontent.com/Aptivi/dotify/main/dotify
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ sudo chmod +x /usr/local/bin/dotify
```

</details>
