---
description: What is the server address when I just know my mail address?
icon: envelope
---

# Address Investigator

This feature allows you to get a server address from just your mail address or your host name. It uses Thunderbird Autoconfig to get such info for easy configuration.

***

## <mark style="color:$primary;">Usage</mark>

If you want to get an ISP configuration from a mail address or a hostname, use the `IspTools` class from the `Nettify.MailAddress` namespace.

<details>

<summary>Functions</summary>

<table><thead><tr><th width="170.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetIspConfig()</code></td><td>Gets an ISP configuration from either a mail address or a host</td></tr></tbody></table>

This function downloads the relevant information for the specified mail address from the ISP database and processes it before returning the client configuration. Mail clients can use this configuration to set up automatic mail server configuration detection akin to Mozilla Thunderbird.

{% hint style="info" %}
Autoconfiguration information is taken from Mozilla Thunderbird's [automatic configuration server](https://autoconfig.thunderbird.net/v1.1/), which gets synchronized with a list of dominating domains [here](https://github.com/thunderbird/autoconfig/tree/master/ispdb).
{% endhint %}

</details>
