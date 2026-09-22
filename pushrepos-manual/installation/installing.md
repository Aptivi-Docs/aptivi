---
description: How do you install this script?
icon: compact-disc
---

# Installing

Installing this script is easy. To install it, follow these steps, assuming that you have either `curl` or `wget` installed on your Linux system.

<details>

<summary>Local installation</summary>

If you want to install this script to your local home directory, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/pushrepos/main/pushrepos > $HOME/.local/bin/pushrepos
$ wget -O$HOME/.local/bin/pushrepos https://raw.githubusercontent.com/Aptivi/pushrepos/main/pushrepos
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ chmod +x $HOME/.local/bin/pushrepos
```

</details>

<details>

<summary>System-wide installation</summary>

If you want to make this script available to all users on your system, you'll need to execute one of the below commands, depending on what you have:

```console
$ curl -fsSL https://raw.githubusercontent.com/Aptivi/pushrepos/main/pushrepos | sudo tee /usr/local/bin/pushrepos
$ sudo wget -O/usr/local/bin/pushrepos https://raw.githubusercontent.com/Aptivi/pushrepos/main/pushrepos
```

After that, you'll need to execute the below command to ensure that the script is executable:

```console
$ sudo chmod +x /usr/local/bin/pushrepos
```

</details>
