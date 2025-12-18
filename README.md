# rockbox_boost

This lua script for Rockbox forces the CPU into an "overclocked" state.

## Installation

1. Copy `boost.lua` to any location on your device (I suggest `.rockbox/rocks/apps` to tuck it out of the way of your normal `Files` view)
2. Navigate to `Settings` > `General Settings` > `Startup/Shutdown` > `Start Screen`, and choose `Open Plugin`.
3. Navigate to where you copied `boost.lua`. Select it, and choose `lua` on the `Open with` screen.
4. Restart your device. You should see a brief (1/8 second) message appear that says "Boosting..."

## Why?

When playing songs with RockBox on a modded iPod Classic, I would hear high-pitched electronic noises sprinkled throughout anything I listened to after about 5 seconds. This happened regardless of audio format or source. At first I thought it was related to the audio buffering, but changing the buffer time seemed to have no effect.

I poked around the menus looking for _any_ setting that had an effect, and I noticed that it didn't seem to make the noise while I was actively poking around.

After more investigation, I went into the `System` > `Debug (Keep Out!)` menu, where I discovered the `CPU frequency` setting. Sitting at this menu, I noticed that the weird noises started when the `boost_counter` hit `0`. After some spinning of the click wheel, I realized I was able to lock the `boost_counter` to `1` by exiting right after spinning.

It seems that when the CPU on this iPod is in a low power state, it can't cleanly process the audio, but boosting the CPU makes the problem disappear.

I don't have any other iPods to test to see if they also have this issue.
