---
description: News right at your fingertips!
icon: newspaper
---

# RSS Feeds

This feature provides a set of functions that allow you to get a list of articles from an RSS feed from a single site.

***

## <mark style="color:$primary;">Usage</mark>

If you want to get all RSS feeds from a single site, you can use the `RSSTools` class from the `Nettify.Rss` namespace. Just follow the below steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Creating a new instance</mark>

Create a new instance of the `RSSFeed` class that contains the necessary constructor.

```csharp
public RSSFeed(string FeedUrl, RSSFeedType FeedType)
```
{% endstep %}

{% step %}
### <mark style="color:$primary;">Refresh the instance to get articles</mark>

Call either `Refresh()` or `RefreshAsync()` to get the latest information about your feed, depending on the scenario.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you're either doing web development, or you're developing in an asynchronous program, call the `RefreshAsync()` function where appropriate.
{% endhint %}

***

## <mark style="color:$primary;">Structure</mark>

The RSS feed class contains a structure that is explained when you expand one of the following items.

<details>

<summary>The constructor</summary>

The constructor provides the following required arguments:

<table><thead><tr><th width="119.66668701171875">Argument</th><th>Description</th></tr></thead><tbody><tr><td><code>FeedUrl</code></td><td>Specifies the URL to the RSS feed, for example, <a href="https://www.techrepublic.com/rssfeeds/articles/">https://www.techrepublic.com/rssfeeds/articles/</a></td></tr><tr><td><code>FeedType</code></td><td>Specifies the feed type to parse</td></tr></tbody></table>

</details>

<details>

<summary>Feed types</summary>

`FeedType` can be one of the following:

<table><thead><tr><th width="120.3333740234375">Feed type</th><th>Description</th></tr></thead><tbody><tr><td><code>RSS2</code></td><td>Assumes that the RSS feed in the given URL is an RSS 2 feed</td></tr><tr><td><code>RSS1</code></td><td>Assumes that the RSS feed in the given URL is an RSS 1 feed</td></tr><tr><td><code>Atom</code></td><td>Assumes that the RSS feed in the given URL is an Atom feed</td></tr><tr><td><code>Infer</code></td><td>Automatically detects the RSS feed type</td></tr></tbody></table>

</details>

<details>

<summary>RSS feed instance</summary>

For the RSS feed info, `RSSFeed` contains the following properties:

<table><thead><tr><th width="169.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>FeedUrl</code></td><td>URL to the feed</td></tr><tr><td><code>FeedType</code></td><td>Feed type as described above</td></tr><tr><td><code>FeedTitle</code></td><td>Feed title provided by the host</td></tr><tr><td><code>FeedDescription</code></td><td>Feed description provided by the host</td></tr><tr><td><code>FeedArticles</code></td><td>List of feed articles</td></tr></tbody></table>

</details>

<details>

<summary>Feed article list</summary>

In the RSS feed instance, `FeedArticles` is a list of feed articles, `RSSArticle`, that you can enumerate within the for loop, for example:

```csharp
var feed = new RSSFeed("feedurl", RSSFeedType.Infer);
foreach (RSSArticle article in feed.FeedArticles)
{
    // Your code here
}
```

This class contains the following properties:

<table><thead><tr><th width="199.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>ArticleTitle</code></td><td>Title of the article</td></tr><tr><td><code>ArticleLink</code></td><td>Link to the article</td></tr><tr><td><code>ArticleDescription</code></td><td>Description or summary of the article</td></tr><tr><td><code>ArticleVariables</code></td><td>Additional article parameters</td></tr></tbody></table>

</details>

***

## <mark style="color:$primary;">Searching RSS feeds</mark>

When it comes to searching RSS feeds, Nettify uses Feedly to give you a functionality that allows you to search Feedly for all the RSS feeds. For instance, if you're searching for Linux using this feature, it'll return all feeds that have to do with Linux. Check out Feedly's website if you don't know what it is yet:

{% embed url="https://feedly.com/" %}

To get articles from the RSS feeds that are found within a search term, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Get a list of RSS feed sites</mark>

Use one of the following functions:

* `GetRssFeeds()`
* `GetRssFeedsAsync()`

Once you call one of these functions, you can use this array of `SearcherInstance` to get information about the resultant feeds.

{% hint style="info" %}
If you're either doing web development, or you're developing in an asynchronous program, call the `GetRssFeedsAsync()` function where appropriate.
{% endhint %}
{% endstep %}

{% step %}
### <mark style="color:$primary;">Obtain an RSS feed instance from the searcher</mark>

Use one of the following functions:

* `GetFeedFromSearcher()`
* `GetFeedFromSearcherAsync()`

Once you call one of these functions, you can get an instance of `RSSFeed` that you can use to get articles.

{% hint style="info" %}
If you're either doing web development, or you're developing in an asynchronous program, call the `GetFeedFromSearcherAsync()` function where appropriate.
{% endhint %}
{% endstep %}
{% endstepper %}

If you don't want to obtain an RSS feed from the searcher, you can use it for something else.

<details>

<summary>Searcher instance properties</summary>

A `SearcherInstance` class contains the following properties:

<table><thead><tr><th width="169.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Description</code></td><td>Gets the first line of the description</td></tr><tr><td><code>FullDescription</code></td><td>Gets the whole feed description</td></tr></tbody></table>

</details>
