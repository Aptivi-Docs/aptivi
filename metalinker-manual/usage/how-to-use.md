---
description: How do I use this library?
icon: computer
---

# How to use

Metalink files contain metadata about a file, such as hashes, chunks, and other information to help download managers accelerate its download while verifying the checksum to avoid corruption.

***

## <mark style="color:$primary;">How to parse Metalink files</mark>

You can easily parse both Metalink 3.0 and 4.0 files, streams, and XML representations using the `MetalinkParser` class.

<details>

<summary>Functions to obtain a Metalink instance</summary>

You can use the below functions to get the file metadata.

| Function                                                   | Description                                                                                                                         |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `GetMetalinkFromPath(string file)`                         | This function parses the Metalink data by giving it a file path                                                                     |
| `GetMetalinkFromStream(Stream stream)`                     | This function parses the Metalink data by giving it a stream                                                                        |
| `GetMetalinkFromXml(string metalink)`                      | This function parses the Metalink data by giving it an XML representation                                                           |
| `GetMetalinkFromXmlDocument(XmlDocument metalinkDocument)` | This function parses the Metalink data by giving it an XML document instance that contains an XML representation of a Metalink data |

</details>

This is very easy; just call one of these functions when assigning a variable that will hold Metalink-related data, and you'll be able to get information about the file, such as hashes, chunks and their info, and regions for mirrors.

***

## <mark style="color:$primary;">Example of obtaining Metalink</mark>

Here's a very simple example of how to do this using a file stream:

```csharp
// Note that MetalinkLoader is not part of the library
Stream? stream = MetalinkLoader.LoadMetalinkStream("slackware15.iso.metalink");
if (stream is null)
    Assert.Fail("Stream is null");
var metalink = MetalinkParser.GetMetalinkFromStream(stream);
```
