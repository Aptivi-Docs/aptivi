---
description: Verifying your downloaded files...
icon: badge-check
---

# Attestations

You can verify the integrity of all the release assets in any of our projects (whether it's a binary release or a documentation) using the two methods:

* GitHub Attestations
* Manual Hashing

***

## <mark style="color:$primary;">Attestations</mark>

GitHub have recently introduced a new feature that allows you to verify a binary artifact that a workflow has generated, called the [Attestations](https://github.blog/2024-05-02-introducing-artifact-attestations-now-in-public-beta/). To verify your download, once you've downloaded one of the ZIP files, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Install GH CLI</mark>

Install [GH CLI 2.49.0](https://github.com/cli/cli/releases/tag/v2.49.0) or higher.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Sign in to GH CLI</mark>

Sign in to your GitHub account using `gh auth login`.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Verify the attestation</mark>

Run this command: `gh attestation verify <version>-<type>.zip --owner Aptivi`.

You'll need to replace:

* `<version>`: Version of a project that you've downloaded.
* `<type>`: Type of a ZIP download, such as `bin` and `doc`.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Verify output</mark>

If everything is OK, you should see the below message, such as one for Nitrocid KS 0.1.0.10:

```
Loaded digest sha256:6030eb1eb660f336d8b070202c598e8f51e50c8b9ca9084f30aa8d40ecbb996f for file://0.1.0.10-bin-lite.zip
Loaded 1 attestation from GitHub API
✓ Verification succeeded!

sha256:6030eb1eb660f336d8b070202c598e8f51e50c8b9ca9084f30aa8d40ecbb996f was attested by:
REPO               PREDICATE_TYPE                  WORKFLOW
Aptivi/NitrocidKS  https://slsa.dev/provenance/v1  .github/workflows/prepdraft.yml@refs/tags/v0.1.0.10
```

{% hint style="warning" %}
If you've seen this error message:

```
Loaded digest sha256:78fc7b18c2e5e2753934652d294456d11d8dadad6f638dedc31513c4570587a1 for file://0.1.0.10-bin-lite.zip
✗ Loading attestations from GitHub API failed

Error: failed to fetch attestations from Aptivi: HTTP 404: Not Found (https://api.github.com/orgs/Aptivi/attestations/sha256:78fc7b18c2e5e2753934652d294456d11d8dadad6f638dedc31513c4570587a1?per_page=30)
```

Then, your download is corrupt.
{% endhint %}
{% endstep %}
{% endstepper %}

***

## <mark style="color:$primary;">Manual hashing</mark>

After you've downloaded the ZIP file, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Open the project release page</mark>

Open the appropriate release page that matches your version.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Find a file in the hash sums list</mark>

Look for a file that you've downloaded from the list of expected hash sums.

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Verify the SHA256 sum</mark>

Verify the SHA256 sum using a preferred tool of your choice. In CLI, use `sha256sum` against the file if you're running on Linux, or use `Get-FileHash -Algorithm sha256` in PowerShell against the file if you're running on Windows.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Compare the output</mark>

Verify that the hashes match using the available tools. If hashes match, your download is fine. Otherwise, you'll have to download the file again.
{% endstep %}
{% endstepper %}
