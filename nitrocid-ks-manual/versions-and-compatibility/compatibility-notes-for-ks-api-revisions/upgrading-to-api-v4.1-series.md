---
description: Follow the compatibility notes when upgrading your mods to API v4.1 series
icon: up
---

# Upgrading to API v4.1 series

As API v4.1 is still in development, the breaking changes get committed and land here. They describe what broke and what should be used instead.

***

## <mark style="color:$primary;">From 0.2.0.6 to 0.2.1</mark> <a href="#from-0.0.24-to-0.1.0" id="from-0.0.24-to-0.1.0"></a>

This version introduces many changes to the kernel API to make it easier to use than never before. It also deprecates and removes APIs that are no longer necessary, while introducing new features that make it easier for you to create useful kernel modifications.

### <mark style="color:$primary;">Updated Terminaux to 8.8</mark> <a href="#updated-terminaux-to-6.0" id="updated-terminaux-to-6.0"></a>

We've updated Terminaux to 8.8 to bring improvements. However, this doesn't come without the cost of having to deal with the breaking changes, which, in this case, is many.

You can consult the list of breaking changes that result from upgrading to Terminaux 8.8 by pressing the below button:

{% content-ref url="https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/breaking-changes/api-v8.0" %}
[API v8.0](https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/breaking-changes/api-v8.0)
{% endcontent-ref %}

### <mark style="color:$primary;">Detailed important changes</mark> <a href="#detailed-important-changes-2" id="detailed-important-changes-2"></a>

This section explains how to adapt the important changes to your mod code so that it works with 0.2.1 and higher. This highlights the most important changes that we have compiled for you.

<details>

<summary>Removed all SpecProbe wrappers</summary>

SpecProbe wrappers were implemented in `KernelPlatform` before getting moved to SpecProbe so that more applications were able to use them outside Nitrocid. As a result, we've removed all SpecProbe wrappers.

The following functions were removed as of 0.2.1 Tech Preview:

* `IsOnWindows()`
* `IsOnUnix()`
* `IsOnUnixMusl()`
* `IsOnMacOS()`
* `IsOnAndroid()`
* `GetTerminalEmulator()`
* `GetTerminalType()`
* `IsRunningFromTmux()`
* `IsRunningFromScreen()`
* `GetCurrentGenericRid()`

We will probably move more SpecProbe wrappers as we introduce different versions for different .NET frameworks in a future version of SpecProbe expected around July 2026.

</details>

<details>

<summary>Removed screensaver properties</summary>

The two properties (actually one property and function) have been finally removed from both the base class of a screensaver and its underlying interface. The reason is that because we wanted to simplify the implementation of a screensaver, which led to the removal of the following properties and functions:

* `ScreensaverResizeSync()`
* `ScreensaverName`

Since they essentially do the same thing as preparing the screensaver for first display and giving the screensaver the same name as the class name, we've decided to remove them.

{% hint style="info" %}
We will bring back the resize sync condition in the screensaver initialization code once the API has been restructured during July and August.
{% endhint %}

</details>

<details>

<summary>Refactored the widget system</summary>

In both the base widget class and its underlying interface, we have run a refactor that caused us to remove the following functions:

* `Initialize()`
* `Cleanup()`

Which, in turn, removed several functions from the `WidgetTools` class, such as:

* `RenderWidget()`
* `InitializeWidget()`
* `CleanupWidget()`
* `GetWidgetNames()`

We have also reworked on how to define the widget options that the Widget Canvas JSON uses, which caused the `Options` property to be removed, replacing them with public properties that the author defines as public.

In the `WidgetCanvasTools` class, we've also removed a function overload of `RenderFromInfos()` that let you specify whether the refresh was required, since that variable required `Initialize()` which no longer exists due to this refactor.

{% hint style="info" %}
You can now use `Render()` from the widget class instance itself to render a widget to a string, which you can then use with one of the console writers that Terminaux provides.
{% endhint %}

</details>

<details>

<summary>Moved regular expression tools</summary>

We have moved the regular expression tools class, `RegexpTools`, to `Nitrocid.Base.Drivers.Regexp` from `Nitrocid.Base.Misc.Text.Probers.Regexp` to maintain consistency as it is a sole class in the latter namespace.

</details>

<details>

<summary>Used Terminaux's built-in input lock system</summary>

{% code expandable="true" %}
```csharp
public static class InputTools { }
```
{% endcode %}

We have used Terminaux's built-in lock system that version 8.6 introduced to reduce the amount of helper classes. This locking mechanism is now available for all Terminaux applications, not just Nitrocid, that can benefit from this feature, such as screensavers and other features.

</details>

<details>

<summary>Removed the <code>FullCalendar</code> renderer</summary>

As a result of ongoing improvements made to the calendar renderer on Terminaux 8.6, we've decided to remove the `FullCalendar` renderer to minimize code repetition on two different projects and to increase maintainability.

{% hint style="info" %}
We advise you to render your calendars from the `CalendarPrint` class.
{% endhint %}

</details>

<details>

<summary>Moved <code>Nitrocid.ConsoleBase</code> to <code>Nitrocid.Kernel.ConsoleBase</code></summary>

We've moved the entire `ConsoleBase` namespace containing a public class, `ConsolePointerHandler`, and an internal class, `ConsoleResizeHandler`, to the `Nitrocid.Kernel` parent namespace as the restructure is now complete for the console subsystem for Nitrocid.

{% hint style="info" %}
Update the `using` clauses to point to the new namespace, `Nitrocid.Kernel.ConsoleBase`.
{% endhint %}

</details>

<details>

<summary>Refactored kernel update mechanism</summary>

{% code expandable="true" %}
```csharp
public static KernelUpdate? FetchBinaryArchive() { }
public static KernelUpdate? FetchAddonPack() { }
```
{% endcode %}

The above two functions were implemented as wrappers for the update checker for different update kinds. Since they only call the master function, `FetchKernelUpdates()`, with the appropriate arguments, we felt that the above wrappers are unnecessary.

{% hint style="info" %}
Replace all occurrences of the above functions with calls to `FetchKernelUpdates()`, passing `UpdateKind.Binary` or `UpdateKind.Addons`, respectively.
{% endhint %}

</details>

<details>

<summary><code>WindowsUserTools</code> migrated to <code>KernelPlatform</code></summary>

{% code expandable="true" %}
```csharp
public static class WindowsUserTools { }
```
{% endcode %}

The above class was available with only one function that was related to the host Windows user, and `KernelPlatform` seemed to be a better fit. We've moved the class:

* From: `WindowsUserTools.IsAdministrator()`
* To: `KernelPlatform.IsCurrentWindowsUserAdmin()`

This rename was also done to clarify which user was it referring to.

</details>

<details>

<summary>Refactored the <code>Equals</code> function in notifications</summary>

{% code expandable="true" %}
```csharp
public bool EqualsNoId(Notification? other) { }
```
{% endcode %}

The above function has been merged to `Equals()`, which now has another overload with `withId` argument set to `true` by default. When `withId` is set to `false`, the notification comparison without the notification ID is done.

</details>

<details>

<summary>Moved <code>DockTools</code> back to the Nitrocid base library</summary>

{% code expandable="true" %}
```csharp
public static class DockTools { }
```
{% endcode %}

We've moved the above class back to the Nitrocid base library as part of the refactoring project to make Nitrocid tidier.

{% hint style="info" %}
You should consider using the `DockTools` class directly while removing any references to inter-addon communication tools.
{% endhint %}

</details>

<details>

<summary>Color conversion tools moved to Colorimetry</summary>

```csharp
public static class ColorConvertTools { }
```

We've moved the above class to Colorimetry as we have seen potential for refactoring. We have also kept it up to date with the Coloritmetry library, as well as Terminaux, to add new color models.

{% hint style="info" %}
You can now use the same class directly from Colorimetry.
{% endhint %}

</details>

<details>

<summary>Moved shell tools to appropriate places and condensed them to partial classes for shells</summary>

We have moved the following tools in `ShellPacks` to the below namespaces:

* `ArchiveTools` is now at `Nitrocid.ShellPacks.Shells.Archive.Tools`
* `FTPTools` is now at `Nitrocid.ShellPacks.Shells.FTP.Tools`
* `FTPLogger` is now at `Nitrocid.ShellPacks.Shells.FTP.Tools`
* `FTPTransferProgress` is now at `Nitrocid.ShellPacks.Shells.FTP.Tools.Transfer`
* `FTPTransfer` is now at `Nitrocid.ShellPacks.Shells.FTP.Tools.Transfer`
* `FTPHashing` is now at `Nitrocid.ShellPacks.Shells.FTP.Tools.Filesystem`
* `FTPFilesystem` is now at `Nitrocid.ShellPacks.Shells.FTP.Tools.Filesystem`
* `HTTPTools` is now at `Nitrocid.ShellPacks.Shells.HTTP.Tools`
* `JsonTools` is now at `Nitrocid.ShellPacks.Shells.Json.Tools`
* `MailHandlers` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools`
* `MailTransferProgress` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools.Transfer`
* `MailTransfer` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools.Transfer`
* `MailPingers` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools.Transfer`
* `PGPContext` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools.PGP`
* `MailManager` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools.Directory`
* `MailDirectory` is now at `Nitrocid.ShellPacks.Shells.Mail.Tools.Directory`
* `RSSTools` is now at `Nitrocid.ShellPacks.Shells.RSS.Tools`
* `RSSBookmarkManager` is now at `Nitrocid.ShellPacks.Shells.RSS.Tools`
* `SFTPTools` is now at `Nitrocid.ShellPacks.Shells.SFTP.Tools`
* `SFTPTransfer` is now at `Nitrocid.ShellPacks.Shells.SFTP.Tools.Transfer`
* `SFTPFilesystem` is now at `Nitrocid.ShellPacks.Shells.SFTP.Tools.Filesystem`
* `SqlEditTools` is now at `Nitrocid.ShellPacks.Shells.Sql.Tools`

Some of those tools have also been condensed to shell instance partial class, such as archive shell tools whose functions got moved to `ArchiveShell`. Therefore, you may need to check the shell instance itself to get access to some of the tools. Some of them may have been moved to their standalone classes as mentioned above.

</details>

<details>

<summary>Login and login-related classes moved to <code>Nitrocid.Base.Login</code></summary>

All classes that are related to logging in, such as `Login`, have been moved to a namespace by itself, which is `Nitrocid.Base.Login`. The login tools class has also been renamed to `LoginTools` to avoid conflict with the namespace.

{% hint style="info" %}
You'll have to update the using statements to point to `Nitrocid.Base.Login`.
{% endhint %}

</details>

<details>

<summary>Refactored the RSS tools for the login</summary>

{% code expandable="true" %}
```csharp
public static class RSSTools { }
```
{% endcode %}

The `RSSTools` class in the base kernel has only one function, which was responsible for showing the latest article. However, this function wasn't supposed to be public, because it was called only once by the kernel entry point. As a result, we've decided to move the function to a private function in the entry point, removing the class altogether.

</details>

<details>

<summary>Refactored the RPC tools</summary>

{% code expandable="true" %}
```csharp
public static void WrapperStartRPC() { }
```
{% endcode %}

In the `RemoteProcedure` class, there was this above function that was called once on kernel startup. It wasn't intended to be called from user mods, so we had to make it clear by removing this function, inlining it to a kernel stage code.

To assist this process, we've also refactored the entire RPC tools and changed how it handled commands from a dictionary of actions to fully-fledged command classes for more flexibility, fixing some edge cases along the way.

{% hint style="info" %}
You don't need to do anything, since we haven't removed any other functions or classes that are commonly used (as of yet).
{% endhint %}

</details>

<details>

<summary>Decoupled shell tools</summary>

We've decoupled the shell tools as we found them necessary so that mods (and future kernel features) can benefit from this refactor. We've also removed shell-specific prefixes from function names (we're still working on it), and this was done back when Nitrocid was still using Visual Basic, and we had to work around how it imported static classes (modules in VB).

As a result, we've moved the following tools:

* `OpenSqlFile()`
* `CloseSqlFile()`
* `SqlCommand()`
* `SFTPListRemote()`
* `SFTPDeleteRemote()`
* `SFTPGetCanonicalPath()`
* `SFTPMakeDirectory()`
* `SFTPExists()`
* `SFTPFileExists()`
* `SFTPDirectoryExists()`
* `SFTPGetFile()`
* `SFTPUploadFile()`
* `SFTPDownloadToString()`
* `HttpDelete()`
* `HttpGetString()`
* `HttpGet()`
* `HttpPutString()`
* `HttpPutFile()`
* `HttpPostString()`
* `HttpPostFile()`
* `HttpAddHeader()`
* `HttpRemoveHeader()`
* `HttpEditHeader()`
* `HttpListHeaders()`
* `HttpHeaderExists()`
* `HttpGetCurrentUserAgent()`
* `HttpSetUserAgent()`
* `NeutralizeUri()`
* `FTPListRemote()`
* `FTPDeleteRemote()`
* `FTPMoveItem()`
* `FTPCopyItem()`
* `FTPChangePermissions()`
* `FTPMakeDirectory()`
* `FTPExists()`
* `FTPFileExists()`
* `FTPDirectoryExists()`
* `FTPGetHash()`
* `FTPGetHashes()`
* `FTPGetFile()`
* `FTPGetFolder()`
* `FTPUploadFile()`
* `FTPUploadFolder()`
* `FTPDownloadToString()`
* `CreateMailDirectory()`
* `DeleteMailDirectory()`
* `RenameMailDirectory()`
* `MailChangeDirectory()`
* `OpenFolder()`
* `MailListDirectories()`
* `PopulateMessages()`
* `MailListMessages()`
* `MailRemoveMessage()`
* `MailRemoveAllBySender()`
* `MailMoveMessage()`
* `MailMoveAllBySender()`
* `MailPrintMessage()`
* `MailRenderMessage()`
* `DecryptMessage()`
* `MailSendMessage()`
* `MailSendEncryptedMessage()`

</details>

<details>

<summary>Network connections are now strongly typed</summary>

The `NetworkConnection` class has been improved so that it would be broken into three types:

* `NetworkConnection`: Abstract class that contains the most basic information about a network connection
* `NetworkThreadConnection`: Indicates that this network connection is run by a thread
* `NetworkInstanceConnection`: Indicates that this network connection is run by an object instance.

As a result, functions like `EstablishConnection()` have been changed so that they would support two types of network connections, and the functions have been changed to be more strongly-typed with generic type parameter.

</details>

<details>

<summary>Removed network drivers</summary>

{% code expandable="true" %}
```csharp
public static class NetworkDriverTools { }
public interface INetworkDriver : IDriver { }
public abstract class BaseNetworkDriver : INetworkDriver { }
```
{% endcode %}

We've removed network drivers as part of a refactoring process involving network transfer tools, so we've moved function implementations inside the network transfer class, which is `NetworkTransfer`.

{% hint style="danger" %}
You can no longer use network drivers to change how Nitrocid transfers files and performs other network operations.
{% endhint %}

</details>

<details>

<summary>Refactored user management code</summary>

{% code expandable="true" %}
```csharp
public static bool InitializeUser(string uninitUser, string unpassword = "", bool ComputationNeeded = true, bool ModifyExisting = false) { }
public static void InitializeUsers() { }
```
{% endcode %}

The above two functions have been removed as they're not meant to be called from kernel mods. `AddUser()` does what the above two functions do, but `InitializeUsers()` has been kept as an internal function.

</details>

