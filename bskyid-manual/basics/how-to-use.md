---
description: How do you use BskyId?
icon: question
---

# How to use

This script is easy to use. Just get your BlueSky handle from your BlueSky account that you can find over the [BlueSky](https://bsky.app/) website, and pass it to the script. This ID is a unique identifier for your BlueSky account and can't be edited.

***

## Usage

To use this script, select your operating system from the list below:

<details>

<summary>Windows</summary>

```powershell
Set-ExecutionPolicy Bypass -Scope Process
./bskyid.ps1 $handle [-plain/-nocolor]
```

</details>

<details>

<summary>Linux</summary>

```console
$ ./bskyid $handle [-plain/-nocolor] # Local installation
$ bskyid $handle [-plain/-nocolor]   # Global installation
```

</details>

Both scripts return just a BlueSky ID associated with your BlueSky account. Replace the `$handle` variable with your BlueSky handle linked above. The following switches are supported:

<table><thead><tr><th width="119.99993896484375">Switch</th><th>Description</th></tr></thead><tbody><tr><td><code>-plain</code></td><td>Outputs the BlueSky ID handle in a plain JSON response instead of just the ID.</td></tr><tr><td><code>-nocolor</code></td><td>Don't use colors on success or failure.</td></tr></tbody></table>

{% hint style="warning" %}
You must write your handle before any switch can be used.
{% endhint %}
