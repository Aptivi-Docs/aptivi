---
description: >-
  Here are some of the warnings you'll need to consider when building or running
  .NET projects on Android
icon: mobile
---

# Warnings for .NET on Android

When you're trying to build or run .NET projects on Android, you'll need to consider the following warnings:

<details>

<summary>Failed to create CoreCLR, HRESULT: 0x8007000E</summary>

Trying to run or build any .NET application on an ARM64 Android device (e.g. Android devices with Qualcomm Snapdragon 8 Gen 2 as SoC) with Termux emits the following error message:

<pre class="language-shell-session"><code class="lang-shell-session">$ dotnet build
<strong>GC heap initialization failed with error 0x8007000E
</strong><strong>Failed to create CoreCLR, HRESULT: 0x8007000E
</strong></code></pre>

In order to fix this message, append the below environment variable before each `dotnet build` command like this:

<pre><code><strong>$ DOTNET_GCHeapHardLimit=1C0000000 dotnet build
</strong></code></pre>

For a more permanent fix, you will have to change `~/.profile` so that it automatically exports this environment variable for each login:

<pre class="language-shell-session"><code class="lang-shell-session"><strong>$ echo "DOTNET_GCHeapHardLimit=1C0000000" >> ~/.profile
</strong><strong>$ . ~/.profile
</strong></code></pre>

</details>

<details>

<summary>error MSB6006: "csc.dll" exited with code 139.</summary>

{% hint style="info" %}
Usually, updated .NET versions no longer face this problem. However, in case you're still suffering from the below error messages, follow these steps.
{% endhint %}

Trying to run or build any .NET application on an ARM64 Android device (e.g. Android devices with Qualcomm Snapdragon 8 Gen 2 as SoC) with Termux emits the following error message:

<pre><code>$ DOTNET_GCHeapHardLimit=1C0000000 dotnet build
(...)
<strong>error MSB6006: "csc.dll" exited with code 139.
</strong><strong>Build FAILED.
</strong></code></pre>

In order to fix this message, either update proot to its latest version, or download the fixed version of `proot` using [this link](https://drive.google.com/file/d/1J9euzuGB5w6WGLVNVxTFVnrauTEzISAV/view?usp=sharing) ([mirror if down](https://mega.nz/file/6dYT2YrY#IPKfJRx3Rt8xql1ggyQ95rgEkpDd_vksP02vnnaOPd4)) and run these commands outside the Ubuntu `proot-distro` environment:

<pre class="language-shell-session"><code class="lang-shell-session"><strong># dpkg -i proot_5.1.107-50_aarch64.deb
</strong><strong># apt-mark hold proot
</strong></code></pre>

</details>
