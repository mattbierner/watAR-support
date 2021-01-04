# watAR

watAR is an augmented reality app for iOS that lets you distort real world surfaces around you as if they were made of water. Add waves and raindrops to any flat vertical or horizontal surfaces. The app is [available for free on the app store][app].

This repo provides documentation on using watAR. If you run into any issues or have any feature requests, you can also [file an issue][issues] here.

## Using the app

### Placing the AR plane

To get started with watAR, first you need to select a real world surface to apply the water effect to. You can place the effect on any flat horizontal or vertical surfaces. The app will walk you through the placement process.

> 🎵 **Note**: Pinch to scale the placed plane up and down. This also works after you have placed the plane.

If you are having trouble placing the effect:

- Try moving the device about a little. On devices without a LiDAR sensor, this helps with surface detection.
- Make sure there is enough light for the cameras. Surface detection struggles in low light.
- Use a surface that has some visual details. Surface detection struggles when pointed at solid color surfaces, such as white walls.

### Waves

The wave effect lets you add waves to the surface. Tap on the wave icon to adjust parameters for the waves:

- `Amplitude` — The max height of a wave.
- `Size` — How large the waves are (wave length).
- `Speed` — How fast the waves travel across the surface.

To turn off the wave effect, simply adjust the `Amplitude` down to zero.

### Rain

Use the rain effect to add raindrops to the surface. Tap on the drop icon to start rain and adjust the rain parameters:

- `Rate` — Number of raindrops falling on the surface.
- `Drop Size` — Controls how large of an area the drop distorts when it first hits the surface.
- `Drop Strength` — Controls how much each drop distorts the surface.
- `Simulation speed` — How fast the water simulation is run. When you increase this, waves will propagate across the surface more quickly. Older devices may struggle with high simulation speeds.
- `Decay` — How fast ripples die off.

To turn off the rain, simply adjust the `Rate` down to zero.

As you scale the water plane up or down in size, you may want to adjust some of these parameters as well. Also keep in mind that not every combination of settings will actually look realistic (or good).

### Touch Interaction

Tap and drag on the water plane to create ripples.

### Sharing

Tap the circular camera button to capture a screenshot of the current effect. This screenshot hides all UI elements so that you only see the effect.

Tap and hold the camera button to start recording a video. This starts a countdown, with recording starting after three seconds. Tap the camera button again to stop recording. While recording, you can interact with the app and adjust water effects. Videos also record the microphone input.

After taking a video or screenshot, you can download it to your photos or share it using the standard iOS share sheet.


## Advanced options

Note that both of these advanced options require a device with a LiDAR sensor, such as the iPhone 12 Pro.

### Foreground occlusion

Foreground occlusion uses depth data from the LiDAR sensor to avoid distorting objects that appear in front of the water effect. This foreground object could be a person, your hand, or a wall. The result makes it look like the water effect is better integrated into the world instead of merely being an effect on your screen.

To enable foreground occlusion, tap the lightbulb icon and toggle "Foreground Occlusion". Keep in mind that the effect is not perfect. If you don't need it, I suggest turning the feature off.

For best results with foreground occlusion:

- Make sure the water plane is exactly placed on the real world surface. You may notice significant issues if the plane is placed a few cm above or below the real surface. 

- Only enable foreground occlusion if the surface is flat. If the surface is angled or pitted, foreground occlusion may cause weird artifacts.

- Keep in mind that objects only a few cm from the surface will be considered part of the surface. Foreground occlusion works best when there is at least a 25cm difference in depth between the foreground object and the surface (although the margin it uses internally is closer to 10cm). 

- Foreground objects can only be around 4 meter from the phone. This is a limitation of the LiDAR sensor.

### Interactive surface

The interactive surface feature builds on foreground occlusion to let you distort the surface using your hands, feet, or other real world objects. Imagine reaching down and creating ripples in the solid ground with the wave of your hand. It's really trippy.

Again keep in mind that, like foreground occlusion, the interactive surface feature is not perfect and can cause significant artifacts when used on an improper surface or in cases where the LiDAR sensor cannot pick up accurate depth information. If you aren't using it, I recommend keeping this feature disabled.

Suggestions for getting best results from the interactive surface feature:

- Make sure the water plane is exactly placed on the real world surface. You may notice significant issues if the plane is placed a few cm above or below the real surface. 

- Place the water plane on a flat surface. Anything jutting out of the surface may cause unwanted ripples.

- Keep the water plane under around 3M in size. The larger the plane, the less sensitive it will be to touches. 

- The virtual surface you are interacting with is between 10 and 20cm away from the real world surface. This margin exists so that flat objects on or near the real world surface itself do not end up producing ripples.

- The rain `Drop Size` setting controls how much your touches distort the surface.

- Remember that the app is not magic. For the interactive surface feature to work, your device's LiDAR sensor must see the point of contact where some real world object actually gets near the water effect surface. We can't detect points of contact that occur offscreen or that are occluded by some foreground object.


## Feedback

Love watAR? Be sure to tell your friends about it and share any cool content you create using the app. If you are feeling especially generous, please also write an App Store review. This really helps other people find the app.

Run into a bug or want to request a new feature? Just [file an issue][issues]!

[app]: https://apps.apple.com/us/app/watar/id1546980861
[issues]: https://github.com/mattbierner/watar-support/issues
