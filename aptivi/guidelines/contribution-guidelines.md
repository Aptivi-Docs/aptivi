---
description: >-
  Participation requires that you read the code of conduct and the contribution
  guidelines.
icon: ballot-check
---

# Contribution Guidelines

Before participating, it's necessary that you read both the code of conduct and the contribution guidelines. Click on the expandable panel to read the guidelines.

<details>

<summary>Contributor Covenant Code of Conduct</summary>

### <mark style="color:$primary;">Our Pledge</mark>

In the interest of fostering an open and welcoming environment, we as contributors and maintainers pledge to making participation in our project and our community a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, sex characteristics, gender identity and expression, level of experience, education, socio-economic status, nationality, personal appearance, race, religion, or sexual identity and orientation.

### <mark style="color:$primary;">Our Standards</mark>

Examples of behavior that contributes to creating a positive environment include:

* Using welcoming and inclusive language
* Being respectful of differing viewpoints and experiences
* Gracefully accepting constructive criticism
* Focusing on what is best for the community
* Showing empathy towards other community members

Examples of unacceptable behavior by participants include:

* The use of sexualized language or imagery and unwelcome sexual attention or advances
* Trolling, insulting/derogatory comments, and personal or political attacks
* Public or private harassment
* Publishing others' private information, such as a physical or electronic address, without explicit permission
* Other conduct which could reasonably be considered inappropriate in a professional setting

### <mark style="color:$primary;">Our Responsibilities</mark>

Project maintainers are responsible for clarifying the standards of acceptable behavior and are expected to take appropriate and fair corrective action in response to any instances of unacceptable behavior.

Project maintainers have the right and responsibility to remove, edit, or reject comments, commits, code, wiki edits, issues, and other contributions that are not aligned to this Code of Conduct, or to ban temporarily or permanently any contributor for other behaviors that they deem inappropriate, threatening, offensive, or harmful.

### <mark style="color:$primary;">Scope</mark>

This Code of Conduct applies both within project spaces and in public spaces when an individual is representing the project or its community. Examples of representing a project or community include using an official project e-mail address, posting via an official social media account, or acting as an appointed representative at an online or offline event. Representation of a project may be further defined and clarified by project maintainers.

### <mark style="color:$primary;">Enforcement</mark>

Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by contacting the project team. All complaints will be reviewed and investigated and will result in a response that is deemed necessary and appropriate to the circumstances. The project team is obligated to maintain confidentiality with regard to the reporter of an incident. Further details of specific enforcement policies may be posted separately.

Project maintainers who do not follow or enforce the Code of Conduct in good faith may face temporary or permanent repercussions as determined by other members of the project's leadership.

### <mark style="color:$primary;">Attribution</mark>

This Code of Conduct is adapted from the [Contributor Covenant](https://www.contributor-covenant.org), version 1.4, available at [https://www.contributor-covenant.org/version/1/4/code-of-conduct.html](https://www.contributor-covenant.org/version/1/4/code-of-conduct.html)

For answers to common questions about this code of conduct, see [https://www.contributor-covenant.org/faq](https://www.contributor-covenant.org/faq)

</details>

<details>

<summary>Contribution guidelines</summary>

First of all, thank you for contributing to our project! This kind of act is the most welcome act to help us keep running our projects the way we want them to run. All your contributions are valuable, but you need to follow these simple rules to get your contribution accepted.

In the pull requests, we might ask you to make a few changes until we can accept them. If there's no reason for us to add your changes to the project, we might reject them altogether.

### <mark style="color:$primary;">Following templates</mark>

Your pull requests should follow the template.

You should be descriptive about what your change is trying to do and what's your opinion about how it affects the whole project. Moreover, it's vital to test your changes before trying to start a pull request to ensure that there are no problems in your initial version. **Always** draft your pull requests.

### <mark style="color:$primary;">Windows compatibility</mark>

When contributing changes to any part of the code, especially when creating files, your pull requests should follow the below requirements:

* File names should not contain forbidden characters, such as `/ \ : * ? " < > |`, and control characters, such as a new line, as files with such names don't sit well with Windows.
* File names should always be treated as case insensitive, even if \*nix systems allow you to create files with same name but different casing, as files that fall into this category don't sit well with Windows.
* When creating shell scripts in Windows, you should give it executable permissions with `git update-index --chmod=+x <SHELLSCRIPT>` prior to committing, as Windows in general has no concept of Unix permissions.
* In general, make sure that any of your changes don't cause incompatibilities with Windows in any way in both build-time and run-time.

{% hint style="info" %}
This doesn't apply to projects that don't use C# or aren't exclusive to Windows.
{% endhint %}

### <mark style="color:$primary;">Code guidelines</mark>

When it comes to coding your changes, they should follow the below coding guidelines to retain the style of our projects' code. These are the below code guidelines:

#### <mark style="color:$primary;">Sorting of Fields and Properties</mark>

Fields must come at the very beginning of each class before the properties. Between the fields and the properties and the functions, there should be an empty line. Moreover, accessibility modifiers should be sorted in the following order:

```
ClassName
  |
  |-> Public Fields
  |-> Public Read-Only Fields
  |-> Internal Fields
  |-> Private Fields
  |-> Internal Read-Only Fields
  |-> Private Read-Only Fields
  |
  |-> Public Properties
  |-> Internal Properties (rare, unless you treat them like C #macros)
  |
(...)
```

#### <mark style="color:$primary;">Sorting of Functions</mark>

Sorting of functions is only affected by their accessibility modifiers in your code. Public functions must come before internal functions, at which the private functions come last.

```
(...)
  |
  |-> Public Functions
  |-> Internal Functions
  |-> Private Functions
  |
 ---
```

#### <mark style="color:$primary;">Arrangement of logic in functions</mark>

Inside functions, the arrangement of logic must be in the below order. Moreover, each part of the logic in each function must be preceded by a comment that explains why is your logic is here and a couple of necessary variables before actual logic.

```
ClassName
(...)
  |
  |-> FunctionName(int arg1, string arg2, ...)
  |     |
  |     |-> Comment explaining why (not what) is this logic here
  |     |-> A couple of necessary variables (optional)
  |     |-> Actual function logic
  |     |
  |   (...)
  |
(...)
```

Example:

```csharp
private static void PollForResize()
{
(...)
    // We need to call the WindowHeight and WindowWidth properties on the Terminal console driver, because
    // this polling works for all the terminals. Other drivers that don't use the terminal may not even
    // implement these two properties.
    if (CurrentWindowHeight != termDriver.WindowHeight | CurrentWindowWidth != termDriver.WindowWidth)
    {
        ResizeDetected = true;
(...)
}
```

#### <mark style="color:$primary;">Tabs versus Spaces</mark>

Here we come to the argument of tabs vs spaces. Our problem with tabs is that there are systems that treat tabs as four spaces, and there are systems that treat tabs as eight spaces. Moreover, there is no universal way to accurately query the operating system for tab lengths, as such queries are up to the application handling tabs.

We recommend that you set your IDE to use **four spaces** instead of literal tabs for each tab press.

#### <mark style="color:$primary;">Functions that do only one thing</mark>

In C#, you can literally make a function without the opening and closing bracelets (`{ }`) if your function only contains one logic. However, you must append `=>` before the logic. Moreover, the logic should be in its own separate line with four spaces as indentation, like the following:

```
access_modifier [static] type SingleLogicFunctionName(string arg1, ...) =>
    MyLogic(arg1, ...).Modify().(...);
```

For example,

```csharp
public static string[] GetWrappedSentences(string text, int maximumLength) =>
    GetWrappedSentences(text, maximumLength, 0);
```

{% hint style="info" %}
This is not applicable to languages that don't support this feature.
{% endhint %}

#### <mark style="color:$primary;">If, while, for, foreach statements that do only one thing</mark>

In C#, you can literally make an if, while, for, and foreach statements without the opening and closing bracelets (`{ }`) if your statement only contains one logic. However, you must append `=>` before the logic. Moreover, the logic should be in its own separate line with four spaces as indentation, like the following:

```
if/while/for/foreach (...)
    MyLogicToDo();
```

For example,

```csharp
// Also, compensate the \0 characters
if (text[i] == '\0')
    vtSeqCompensate++;
```

{% hint style="info" %}
This is not applicable to languages that don't support this feature.
{% endhint %}

#### <mark style="color:$primary;">Naming of Public vs Internal and Private Components</mark>

The naming must satisfy the following rules:

* All public functions, properties, and fields must follow the Pascal Case (FunctionName) naming scheme, regardless of their purpose.
* For argument names in public, internal, and private functions, they must be named in the scheme of Camel Case (argumentName).
* Private and internal functions and properties must also follow the Pascal Case naming scheme.
* Private and internal fields must use the Camel Case naming style.
* Pascal Case should be used in class names at all times.
* You may never use the snake\_case naming (this isn't Rust) or the kebab-case naming scheme (this isn't HTML) in all the components.

{% hint style="info" %}
To learn more about Pascal Case and Camel Case, visit [this site](https://www.freecodecamp.org/news/snake-case-vs-camel-case-vs-pascal-case-vs-kebab-case-whats-the-difference/).
{% endhint %}

### <mark style="color:$primary;">Git commits</mark>

We follow this conventional Git commit scheme:

```
Type - Attributes - Summary

---

Description wrapped with 75 characters word-wise

---

Type: Type
Breaking: Yes/No
Doc Required: Yes/No
Backport Required: Yes/No
AI Assisted: Yes/No
Part: 1/1
```

#### <mark style="color:$primary;">Types</mark>

For types, you should select exactly one type from the following types:

<table><thead><tr><th width="70">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>add</code></td><td>Additions</td></tr><tr><td><code>fix</code></td><td>Bug fixes</td></tr><tr><td><code>rem</code></td><td>Removals</td></tr><tr><td><code>imp</code></td><td>Improvements</td></tr><tr><td><code>ref</code></td><td>Code refactors</td></tr><tr><td><code>upd</code></td><td>Library updates</td></tr><tr><td><code>doc</code></td><td>Documentation updates</td></tr><tr><td><code>dev</code></td><td>Development start points</td></tr><tr><td><code>dcp</code></td><td>Development checkpoints (version bump, etc.)</td></tr><tr><td><code>fin</code></td><td>Development finish points</td></tr><tr><td><code>chg</code></td><td>Minor changes to previous commits</td></tr><tr><td><code>int</code></td><td>Continuous integration changes</td></tr><tr><td><code>bkp</code></td><td>Backports (an empty commit for cherry-picked commits or a full commit for non-cherry-picked backports)</td></tr><tr><td><code>prj</code></td><td>Project initialization</td></tr><tr><td><code>pkg</code></td><td>Packaging-related changes, such as Debian, PKGBUILD, etc.</td></tr><tr><td><code>und</code></td><td>Other changes that don't apply</td></tr></tbody></table>

{% hint style="info" %}
If you want to use `add`, `fix`, `rem`, `imp`, `doc`, or `bkp`, you'll have to provide a description.
{% endhint %}

#### <mark style="color:$primary;">Attributes</mark>

Additionally, attributes are optional and can be specified. Multiple attributes should be separated with the pipe character (`|`). However, there are special cases that you may need to handle when you're committing your changes to your pull request:

* If documentation is required (i.e. your commit requires documentation on GitBook and you've specified `doc`), change the `Doc Required` part to `Yes`, otherwise, `No`.
* If backport is required (i.e. your commit introduces a fix that needs to be backported to previous version series that don't have a fix), change the `Backport Required` part to `Yes`, otherwise, `No`.
* If this commit includes breaking changes (i.e. you've specified `brk`), change the `Breaking` part to `Yes`, otherwise, `No`.
* If this commit is a part of the commit series, specify `prt` and change the `Part` field where it says `1/1` to the current and the total parts in this format: `current/total`. Total parts must be accurate, the title should stay the same as any former commits in the series, and the current part must not be larger than the total part number.

These are the attributes we officially support:

<table><thead><tr><th width="90">Attribute</th><th>Description</th></tr></thead><tbody><tr><td><code>brk</code></td><td>Breaking changes (usually paired with <code>doc</code>)</td></tr><tr><td><code>sec</code></td><td>Security improvements</td></tr><tr><td><code>prf</code></td><td>Performance improvements</td></tr><tr><td><code>reg</code></td><td>Regression fixes</td></tr><tr><td><code>doc</code></td><td>Documentation requirement</td></tr><tr><td><code>ptp</code></td><td>Prototyping</td></tr><tr><td><code>prt</code></td><td>Commit series (part number is required)</td></tr><tr><td><code>bkp</code></td><td>Backportable for older supported version series</td></tr></tbody></table>

#### <mark style="color:$primary;">Backported commits</mark>

Take note that if you've set a commit that is a backport, make sure that the type is not one of the following types:

* Incompatible types with `bkp`: `rem`, `dev`, `dcp`, and `fin`
* Incompatible attributes with `bkp`: `ptp` and `brk`

In addition to that, if you've backported a commit from a different branch or tag, you must specify this stanza directly after the description section, just like this:

*   For tags:

    ```
    The following commits or tags are used for this backport:
      - D877EC56... [Tag 1]
      - C6100AF1... [Tag 2]
    ```
*   For backported commits:

    ```
    The following commits or tags are used for this backport:
      - E3218765...
      - FAE890DA...
      - BE2701D2...
    ```

### <mark style="color:$primary;">Releases</mark>

When planning for a new version, always start the development of the next version by changing the version found in all the relevant files (usually `Directory.Build.props` for C# projects) before starting to push commits that add new features and everything else. When development finishes, before the release tag can be pushed, the `CHANGES` file should be changed to reflect the new release, as long as it follows this convention:

```
Long description of the release

### Changes

This release contains a variety of changes, including, but not limited to:

- `[+]` Added X
- `[*]` Improved Y
- `[-]` Removed Z

Review the commit history if you want to get a deep insight about the changes.

### Feedback?

If you have issues with this version, report to us by [making a new issue ticket](https://github.com/Aptivi/PROJECT/issues/new).

### Sum hashes

To verify integrity of your download, compare the SHA256 sum of your downloaded file with the following information:


```

Two new lines are applied intentionally so that the hash list gets rendered in a way that you'd expect, because the hash sum list gets populated automatically. Also, the `CHANGES.TITLE` file should be changed to match the version whose development finished but tag not pushed, as long as it follows this format:

```
[servicing] PROJECT v1.0.0: Release Name
```

The type at the beginning is necessary as it can tell us and the users in what stage this release belongs to.

Currently, this list of releases should be used:

<table><thead><tr><th width="110">Specifier</th><th></th></tr></thead><tbody><tr><td><code>alpha</code></td><td>This release is an alpha version</td></tr><tr><td><code>beta</code></td><td>This release is a beta version</td></tr><tr><td><code>release</code></td><td>This release is a major release (i.e. changes the major part and/or the minor part)</td></tr><tr><td><code>servicing</code></td><td>This release is a minor release (i.e. changes the build part and/or the patch part)</td></tr></tbody></table>

### <mark style="color:$primary;">Assistance of AI</mark>

Artificial intelligence (AI) is a next-gen technology that every company is leaning to, which we are proud of, but when contributing code or other things to this project, we rely on either human work or AI work + human reviews to ensure maximum quality. You are allowed to use AI assistants as long as they're used responsibly.

When authoring commits that contain AI generated code, the only thing you'll have to do is to answer `Yes` to the `AI Assisted` field. That way, we can tell which commits were made with the assistance of AI, and is only for informational purposes.

### <mark style="color:$primary;">Engagement with the Community</mark>

Thank you for your contribution to our project, but in order for this contribution to be flawless, you must be respectful to all other developers of the projects and the users in general, regardless of whether there is a fight or a heated discussion going on. Try to keep it civil and don't use personal attacks, threats of any kind, derogatory and racist remarks against people or groups of any race, ethnicity, religion, or group, and profanity to try to solve any disagreement with anyone, including the developers of the project.

</details>

Once you read the contribution guidelines, you can now proceed with your contribution.
