# m4l-TapPanVerb

This is an audio effect made in Max For Live that implements a reverb + bucket-brigade multitap (up to 128 individual taps) delay effect with visual control over inter-tap timing and pan position. It can serve as a simple reverb, simple delay, or incredibly complicated combination of the two.

I originally had an idea that there should be a function in a reverb that lets you control the pan position of the reverb tail at specific times after the initial impulse. I didn't find that in the reverbs that I had, so I decided to mock one up. My first attempt was to use an audio effect rack with five chains spread across the stereo range. Each chain had a delay followed by a reverb. The chain delay increased in some increment across the chains, e.g. chain 1 was 0ms delay, chain 2 was 100ms, chain 3 was 200ms, etc. This had the effect of making "reverb bursts" across the stereo field, which was cool. But it wasn't what I had in mind exactly.

This device is as close as I can figure out how to do this at this point. There is a configurable number of taps (up to 128) that are spaced at a configurable time interval. There are visual controls for pan position and time coefficient that give you very direct control over some wild effects. There is a reverb section, which actually sits in front of the signal before the delay taps. This lets you pre-blur the sound as it goes into the delay circuit. There is also a feedback function with a novel musicality, but it is still super dangerous to use! USE WITH CARE!

## Demos

https://github.com/zsteinkamp/m4l-TapPanVerb/raw/main/images/TapPanVerb-A-720.mov

https://github.com/zsteinkamp/m4l-TapPanVerb/raw/main/images/TapPanVerb-B-720.mov

https://github.com/zsteinkamp/m4l-TapPanVerb/raw/main/images/TapPanVerb-C-720.mov

https://github.com/zsteinkamp/m4l-TapPanVerb/raw/main/images/TapPanVerb-D-720.mov

## Installation / Setup

If you just want to download and install the device, then go to the [frozen/](https://github.com/zsteinkamp/m4l-TapPanVerb/tree/main/frozen) directory and download the newest version there.

### Changelog

* [0.0.1](https://github.com/zsteinkamp/m4l-TapPanVerb/raw/main/frozen/TapPanVerb-0.0.1.amxd) - 2022-05-05 - Initial release.

## Usage

### Taps
This knob controls how many taps are in the tap field.

### Delay Base
This knob controls the default delay between each tap in the field.

### Feed Forward
The taps are arranged in a bucket-brigade, that is tap 1 outputs its signal both to the plugin output, but also as the input to tap 2. The volume of the signal that is sent to the subsequent tap is scaled according to this knob. Set to 100% to hear each tap equally loudly.

### Tap Time Factor
This is a visual input to control each tap's relative delay time. You have to imagine the the taps are along the horizontal axis, equally spaced first to last. Pull the line toward zero to speed up the taps, or up to one to slow it back down. Shift-click to remove points.

### Reverb Mix
Crossfades between dry input signal and that signal put through a reverb.

### Reverb Size
Controls a feedback loop inside of the reverb circuit. Larger numbers will result in a longer reverb.

### Early Refl
Controls balance between late and early sides of the reverb algorithm.

### Liveness
Controls whether the reverb sounds dark or bright.

### Panning Path
This is a visual control that lets you position each reverb tap along a line. You need to imagine that the taps are spaced equally along the horizontal axis. Draw a line to indicate where, from left to right, each tap should be placed. Shift-click to remove points.

### FB Amount
This knob controls how much of the output signal is fed back into the pre-reverb section.

### FB Delay
Allows for some control over the resonant frequencies of the feedback circuit. The circuit has an oscillating delay to try to mitigate ringing, and this knob controls its midpoint and scale (+/-50%).

## TODO

* Better visuals. Perhaps plot the taps as vertical lines behind the two functions.

## Contributing

I'd love it if others extended this device. If you would like to contribute, simply fork this repo, make your changes, and open a pull request and I'll have a look. Or if you have ideas or something to add to the to-do list above, just open an issue here or email me at [zack@steinkamp.us](mailto:zack@steinkamp.us).

