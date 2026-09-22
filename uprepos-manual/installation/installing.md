---
description: How to install this script.
icon: compact-disc
---

# Installing

Installing this script is easy. To install it, follow these steps, assuming that you have either `curl` or `wget` installed on your Linux system.

<details>

<summary>Local installation</summary>

If you want to install this script to your local home directory, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/uprepos/main/uprepos > $HOME/.local/bin/uprepos
$ wget -O$HOME/.local/bin/uprepos https://raw.githubusercontent.com/Aptivi/uprepos/main/uprepos
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ chmod +x $HOME/.local/bin/uprepos
```

</details>

<details>

<summary>System-wide installation</summary>

If you want to make this script available to all users on your system, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/uprepos/main/uprepos | sudo tee /usr/local/bin/uprepos
$ sudo wget -O/usr/local/bin/uprepos https://raw.githubusercontent.com/Aptivi/uprepos/main/uprepos
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ sudo chmod +x /usr/local/bin/uprepos
```

</details>
