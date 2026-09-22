---
description: Define "dictionary".
icon: book
---

# English Dictionary

The English Dictionary is a list of English words and their definitions, as well as other information, such as synonyms, antonyms, examples, and others.

***

## <mark style="color:$primary;">Usage</mark>

If you want to get a definition of a word, use the `DictionaryManager` class from the `Nettify.EnglishDictionary` namespace.

<details>

<summary>Functions</summary>

<table><thead><tr><th width="189.6666259765625">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetWordInfo()</code></td><td>Gets a word info</td></tr><tr><td><code>GetWordInfoAsync()</code></td><td>Gets a word info asynchronously</td></tr></tbody></table>

You can then use the resulting array to iterate through possible words and get the values from them.

{% hint style="info" %}
If you're going to use this feature on web projects or in situations that require you to use the asynchronous version, use the `GetWordInfoAsync()` function.
{% endhint %}

</details>
