---
description: How do I log events?
icon: list-tree
---

# Logging

This library uses an abstract base logging class that you must inherit from to describe how your application is going to log events. Usually, it's just a simple call to functions like `Debug()`, `Info()`, and so on.

***

## <mark style="color:$primary;">Base loggers</mark>

That class that you'll need to inherit from in your custom logger class is called `BaseLogger`. However, this can be sometimes difficult, depending on how you want your application to log its events.

For this reason, for the sake of simplicity, we've created pre-built inherited classes in three different libraries.

<details>

<summary>Pre-built inherited classes</summary>

| Package                   | Class           | Description                                                                                                                                                                    |
| ------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Aptivestigate.Log4Net`   | `Log4NetLogger` | Uses the [Log4Net](https://logging.apache.org/log4net/) library to log application events                                                                                      |
| `Aptivestigate.Serilog`   | `SerilogLogger` | Uses the [Serilog](https://serilog.net/) library to log application events (you can use all available [Serilog sinks](https://github.com/serilog/serilog/wiki/provided-sinks)) |
| `Aptivestigate.NLog`      | `NLogLogger`    | Uses the [NLog](https://nlog-project.org/) library to log application events                                                                                                   |
| `Aptivestigate.ZLogger`   | `ZeeLogger`     | Uses the [ZLogger](https://github.com/Cysharp/ZLogger) library to log application events                                                                                       |
| `Aptivestigate.Microsoft` | `MsLogger`      | Uses the [Microsoft.Extensions.Logging](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging) library to log application events                                    |

{% hint style="info" %}
You can create a new instance of any of the logger class mentioned in the above table (leave all arguments empty to print to the console, or specify a configurator)
{% endhint %}

</details>

***

## <mark style="color:$primary;">Usage of the</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">`LogTools`</mark> <mark style="color:$primary;"></mark><mark style="color:$primary;">class</mark>

You can use the `LogTools` class that provides you with functions that allow you to easily log an event to different log levels using the base logger as the first parameter.

<details>

<summary>Functions for logging</summary>

| Function    | Description            |
| ----------- | ---------------------- |
| `Debug()`   | Debug messages         |
| `Info()`    | Informational messages |
| `Warning()` | Warning messages       |
| `Error()`   | Error messages         |
| `Fatal()`   | Fatal error messages   |

</details>

<details>

<summary>Example</summary>

Here's a simple example of how to log to the console using the Serilog console sink (for all levels):

```csharp
var logger = new SerilogLogger();
var exc = new Exception("We really can't do this.");
LogTools.Debug(logger, "Test message without formatting");
LogTools.Debug(logger, "Test message with formatting: {0}, {1}", "Hello", "John Smith");
LogTools.Info(logger, "This is an informational message!");
LogTools.Info(logger, "Saying: {0}, {1}", "Hello", "John Smith");
LogTools.Warning(logger, "Warning: this may not work properly.");
LogTools.Warning(logger, "Warning: a component, {0}, may not work properly.", "fusion reactor");
LogTools.Error(logger, "Error: Ship is out of fuel!");
LogTools.Error(logger, "Error: Fuel level is empty! {0}/{1}", 0, 320);
LogTools.Error(logger, exc, "Error.");
LogTools.Fatal(logger, "FATAL ERROR!");
LogTools.Fatal(logger, "FATAL ERROR: We can't do this! {0}", "Invalid operation.");
LogTools.Fatal(logger, exc, "FATAL ERROR!");
```

</details>

For exceptions, you must place an exception instance before the message but after the logger instance. This is so that you can format the string with ease.

{% hint style="info" %}
You can also use the class functions to log application events to the logger.
{% endhint %}
