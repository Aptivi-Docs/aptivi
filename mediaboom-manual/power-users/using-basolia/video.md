---
description: Watch a video with MediaBoom!
icon: film
---

# Video

MediaBoom provides you with an event handler that allows you to render a frame from a video of almost all formats, including MP4 videos. This feature works with either the software renderer or the OpenGL renderer.

{% hint style="info" %}
You'll have to install the `glfw` library if you want to be able to use OpenGL while rendering videos. This will make use of your graphics card to render video frames.
{% endhint %}

<details>

<summary>Listening to video frame changes</summary>

To subscribe to the `FrameAvailable` event that gets fired for every change to the video frame, you'll need to define a function that tells the application to update the frame. That depends on the application and how it's going to render the frames.

```csharp
basolia.FrameAvailable += UpdateFrame;
```

For example, the MediaBoom CLI player defines this function that samples the frame to color data that Terminaux will then render.

{% code title="VideoDisplayer.cs" %}
```csharp
private static void UpdateFrame(object? sender, VideoFrameEventArgs e)
{
    // Process the update frame event args
    IntPtr pixels = e.Backend switch
    {
        VideoRendererBackend.Software => e.SWFramePointer,
        VideoRendererBackend.OpenGL => e.GLPixelPointer,
        _ => IntPtr.Zero,
    };
    if ((e.Format != "rgb24" && e.Format != "rgba8") || pixels == IntPtr.Zero || e.Width <= 0 || e.Height <= 0)
        return;

    SampleToGrid(pixels, e.Width, e.Height, e.Stride);
}
```
{% endcode %}

Be sure to unsubscribe from the event once done, such as closing the app, by doing this:

```csharp
basolia.FrameAvailable -= UpdateFrame;
```

{% hint style="info" %}
If you're using an OpenGL renderer, you'll have to tell MediaBoom to enable GL readback.

```csharp
basolia.GLReadbackEnabled = true;
```
{% endhint %}

</details>

<details>

<summary>Switching video backends</summary>

To switch between video backends, you can use the `SwitchBackend()` function from the `BasoliaMedia` instance to initiate the switch between backends. You have two options to choose:

<table><thead><tr><th width="100">Backend</th><th>Description</th></tr></thead><tbody><tr><td><code>Software</code></td><td>Software rendering (uses CPU)</td></tr><tr><td><code>OpenGL</code></td><td>OpenGL rendering (uses GPU)</td></tr></tbody></table>

Those backends are defined in the `VideoRendererBackend` enumeration.

</details>
