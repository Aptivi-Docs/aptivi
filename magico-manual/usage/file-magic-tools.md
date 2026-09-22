---
description: Magic wand that points at your files.
icon: wand-magic-sparkles
---

# File Magic Tools

We have wrapped the file magic tools under a class called `MagicHandler` that is found under the `Magico.Files` namespace. It wraps the `libmagic` library with the `magic.mgc` magic file that is embedded to the library to allow systems that don't have `file` and `libmagic` installed to work, thus achieving portability.

***

## <mark style="color:$primary;">Some of the tools</mark>

You can use some of the tools by expanding one of the below expandables:

<details>

<summary>Obtaining the <code>libmagic</code> version</summary>

You can check the `libmagic` version identifier using the `MagicVersionId` property.

</details>

<details>

<summary>Obtaining the magic file paths</summary>

You can get the magic file paths using the `GetMagicPaths()` function, though this is usually not necessary.

</details>

<details>

<summary>Obtaining detailed file summary</summary>

To get a detailed file summary, you can use the `GetMagicInfo()` function, pointing to the path of the file, to get a summary that is similar to the `file` command that you may have installed in your Linux distribution.

</details>

<details>

<summary>Obtaining MIME information about a file</summary>

You can get the MIME information about your file using the file data and magic number as the indicator instead of simply the file extension. The following functions provide this info:

* `GetMagicMimeInfo()`
* `GetMagicMimeType()`
* `GetMagicCustomType()`

</details>
