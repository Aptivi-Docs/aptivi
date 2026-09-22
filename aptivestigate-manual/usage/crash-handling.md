---
description: We need to know why this application crashed.
icon: burst
---

# Crash handling

This library provides you a way to handle crashes using the built-in [UnhandledException](https://learn.microsoft.com/en-us/dotnet/api/system.appdomain.unhandledexception) event in the `AppDomain.CurrentDomain` property. It uses either a built-in crash handler, which saves the crash dump containing crash information to a log file, or a custom handler, which is a delegate of type `Action<UnhandledExceptionEventArgs>` that allows you to specify how you want to handle crashes.

***

## <mark style="color:$primary;">The process</mark>

To install a crash handler, you can call the `InstallCrashHandler()` function in the `CrashTools` class. It can hold either a parameter that specifies such a delegate, or you can pass nothing, which is equivalent to passing null, that uses the built-in crash handler.

The crash handling process works like this:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Application crash</mark>

The application crashes with any exception.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Crash handler running</mark>

Either a custom crash handler or a built-in one is called when an application crashes with an unhandled exception caused by some bug in the code or other factors.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Second chance crash handling</mark>

In case the handler crashes, it checks to see if the crash handler is a custom one.

1. If the crash handler is a custom function, the handler will re-run with the built-in handler in case the problem is with the custom crash handler, but will not propagate the exception that caused the custom handler to crash.
2. If the crash handler is a built-in handler, the handler will throw an exception.

The exception is then passed to the second-chance crash handler that outputs just a simple crash dump file.
{% endstep %}

{% step %}
### <mark style="color:$primary;">Third chance hard fail stage</mark>

If the second-chance crash handler fails, the exception is passed as an argument to the [`FailFast()`](https://learn.microsoft.com/en-us/dotnet/api/system.environment.failfast) function in the `Environment` class, which makes the operating system handle the crash.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Crash logs are created in the following directories:

* Windows: `%LOCALAPPDATA%\Aptivi\Crashes`
* Linux: `$HOME/.config/Aptivi/Crashes`

Fatal crash dumps are prefixed with `f_`.
{% endhint %}
