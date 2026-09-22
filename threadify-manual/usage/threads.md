---
description: Hey, can you run two or more tasks at once?
icon: arrow-progress
metaLinks:
  alternates:
    - https://app.gitbook.com/s/bMaIp29Xf3tHDgiWo9BZ/usage/calendars
---

# Threads

Threads are a great way to perform tasks more than once! They play a huge role on preventing the block from happening on the main thread, as well as speeding up time-consuming tasks, especially when it comes to CPU-heavy operations. Single-threaded applications usually get blocked by long operations, but threads solve this problem.

***

## <mark style="color:$primary;">How do threads get managed?</mark>

Threadify manages the threads that are created by the `ThreadInstance` instances. It allows this library to manipulate with these threads more efficiently, and they provide you with convenience functions that allow you to start and stop threads, as well as abstract away common functions to make your life easier.

Threadify exists to solve a major problem regarding restarting threads that can't otherwise be restarted. Normally, in .NET, you can't restart a thread by calling `Start()` again after it gets stopped; you'll have to maintain a list of parameters you've originally provided when you were constructing the thread for the first time to be able to regenerate and start the thread. Threadify, however, simplifies this task for you!

`ThreadManager` provides you a whole set of functions and properties to efficiently manage your threads from listing all active threads to sleeping to benchmarking the sleep function.

<details>

<summary>How to make your thread instance</summary>

To make your `ThreadInstance`, just call its constructor with the following parameters:

<table><thead><tr><th width="124.99993896484375">Parameter</th><th>Description</th></tr></thead><tbody><tr><td><code>ThreadName</code></td><td>Thread name.</td></tr><tr><td><code>Background</code></td><td>Whether the thread is a background thread.</td></tr><tr><td><code>Executor</code></td><td>A function to execute in the thread. It can be either of the type <code>ThreadStart</code> or of the type <code>ParameterizedThreadStart</code>.</td></tr></tbody></table>

You can then start the thread using the `Start()` function for normal threads or the `Start(object)` function for parameterized threads.

{% hint style="warning" %}
You can't start the thread once it's stopped by `Stop(false)` until it's regenerated either automatically by `Stop()` or manually by `Regen()`, and you can't call `Regen()` before calling the `Stop(false)` function.
{% endhint %}

</details>

<details>

<summary>Thread instance structure</summary>

A `ThreadInstance` has the following values:

<table><thead><tr><th width="149.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Name</code></td><td>Gets the name of the thread.</td></tr><tr><td><code>IsBackground</code></td><td>Checks to see if the thread is a background thread.</td></tr><tr><td><code>IsAlive</code></td><td>Checks to see if the thread is alive.</td></tr><tr><td><code>IsReady</code></td><td>Checks to see if the thread is ready.</td></tr><tr><td><code>IsFailed</code></td><td>Whether a kernel thread has failed or not</td></tr><tr><td><code>ThreadFailures</code></td><td>Gives you a list of management errors that occurred during the lifetime of the thread.</td></tr><tr><td><code>IsStopping</code></td><td>Checks to see whether the kernel thread is stopping.</td></tr><tr><td><code>ParentThread</code></td><td>If the thread is a child thread, this will return its parent. Else, it returns <code>null</code>.</td></tr><tr><td><code>ThreadId</code></td><td>Managed kernel thread ID.</td></tr></tbody></table>

{% hint style="warning" %}
Please note that `ThreadFailures` doesn't maintain a list of errors that happened on a thread action itself; you'll have to maintain them manually based on scope.
{% endhint %}

</details>

<details>

<summary>Child threads</summary>

Child threads are the threads that run with the parent thread and follow the parent thread's lead to perform operations together.

### <mark style="color:$primary;">Adding a child thread</mark>

In your thread, to add a child thread, you must call the `AddChild()` function regardless of whether said child thread takes parameters or not on the parent thread instance to make a new child thread and connect it to the parent thread.

#### <mark style="color:$primary;">Example of adding child threads</mark>

For example, to spawn three child threads from the parent thread, you must call the `AddChild()` function like this:

<pre class="language-csharp"><code class="lang-csharp">ThreadInstance thread = new("Test thread", true, ThreadInstanceTestHelper.WriteHello);
<strong>thread.AddChild("Test child thread", true, ThreadInstanceTestHelper.WriteHello);
</strong><strong>thread.AddChild("Test child thread #2", true, ThreadInstanceTestHelper.WriteHello);
</strong><strong>thread.AddChild("Test child thread #3", true, ThreadInstanceTestHelper.WriteHello);
</strong>thread.Start();
Thread.Sleep(3000);
thread.Stop();
</code></pre>

Starting the parent thread will start all the child threads simultaneously, and stopping the parent thread will stop all the child threads at once.

#### <mark style="color:$primary;">Example of adding extra child threads while running</mark>

You can also add extra child threads to the parent thread that's already running using the same function. Example code is provided below:

<pre class="language-csharp"><code class="lang-csharp">ThreadInstance thread = new("Unit test thread #5", true, ThreadInstanceTestHelper.WriteHelloWithAppendingChild);
thread.AddChild("Unit test child thread #1 for parent thread #5", true, ThreadInstanceTestHelper.WriteHelloFromAppendingChild);
thread.AddChild("Unit test child thread #2 for parent thread #5", true, ThreadInstanceTestHelper.WriteHelloFromAppendingChild);
thread.AddChild("Unit test child thread #3 for parent thread #5", true, ThreadInstanceTestHelper.WriteHelloFromAppendingChild);
thread.Start();
Thread.Sleep(1000);
<strong>thread.AddChild("Unit test additional child thread #4 for parent thread #5", true, ThreadInstanceTestHelper.WriteHelloFromAppendingChild);
</strong><strong>thread.AddChild("Unit test additional child thread #5 for parent thread #5", true, ThreadInstanceTestHelper.WriteHelloFromAppendingChild);
</strong><strong>thread.AddChild("Unit test additional child thread #6 for parent thread #5", true, ThreadInstanceTestHelper.WriteHelloFromAppendingChild);
</strong>Thread.Sleep(3000);
thread.Stop();
</code></pre>

You can get the child thread information and manage child threads inside child threads using the `GetChild()` function, passing it the child thread index starting from zero, usually accompanied by the `ChildThreadCount` property.

</details>

<details>

<summary>Looping until a thread stops</summary>

If your thread consists of an infinite loop doing something useful, like updating the timer screen, the only viable way to implement such a loop within a `ThreadInstance` instance is to put a `while` clause, polling the condition of (`!MyThread.IsStopping`).

Even better, you should catch a `ThreadInterruptedException` in case your thread does something that takes a long time. Here's an example of how it's used in the timer update thread (excluding the actual logic inside):

{% code title="TimerScreen.cs" lineNumbers="true" %}
```csharp
private static void UpdateTimerElapsedDisplay()
{
    var FigletFont = FigletTools.GetFigletFont(TimerFigletFont);
    while (!TimerUpdate.IsStopping)
    {
        (...)
    }
}
```
{% endcode %}

{% hint style="danger" %}
Never use the `IsAlive` property to implement such loops, or your thread will deadlock 60 seconds after it's told to stop in case the `ThreadInterruptedException` isn't getting caught.

Be sure to use the correct thread in which you're checking for `IsStopping`.

If you want to use this property, be sure that you still check for `IsStopping` somewhere in your logic, or at the end of your logic so that you can break out of the infinite loop with polling for the `IsAlive` property.
{% endhint %}

As soon as `Stop()` is called on your thread, `IsStopping` will be set to `true` to notify your threads that it's stopping and that it should take appropriate action to stop. After the thread ends, it'll be reverted to `false`.

</details>

<details>

<summary>Sleeping</summary>

Threads can now delay operations by using one of the following `Sleep()` functions:

<table><thead><tr><th width="316.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>SleepNoBlock(long)</code></td><td>Sleeps until either the time specified, or the current thread is no longer alive.</td></tr><tr><td><code>SleepNoBlock(long, Thread)</code></td><td>Sleeps until either the time specified, or the specified standard thread is no longer alive.</td></tr><tr><td><code>SleepNoBlock(long, ThreadInstance)</code></td><td>Sleeps until either the time specified, or the specified Threadify thread is no longer alive.</td></tr></tbody></table>

#### <mark style="color:$primary;">Determining the precise sleep duration</mark>

The thread manager contains these functions designed to get the total elapsed ticks, milliseconds, or time span to sleep for a specified milliseconds:

<table><thead><tr><th width="230.333251953125">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetActualMilliseconds()</code></td><td>Gets the actual milliseconds time from the sleep time provided in milliseconds</td></tr><tr><td><code>GetActualTicks()</code></td><td>Gets the actual ticks from the sleep time provided in milliseconds</td></tr><tr><td><code>GetActualTimeSpan()</code></td><td>Gets the actual <code>TimeSpan</code> from the sleep time provided in milliseconds</td></tr></tbody></table>

</details>
