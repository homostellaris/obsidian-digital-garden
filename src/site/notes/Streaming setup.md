---
{"dg-publish":true,"permalink":"/streaming-setup/","tags":["gaming"]}
---

Rather than having a gaming console I have a Windows desktop PC in my office which has some decent hardware for games which I stream over ethernet to my LG C2 downstairs in the living room.

The reason I went with this setup is to 'have the best of both worlds' in terms of both console and PC gaming. I like to both experiences in different ways but being able to fire up some classic RTS like Starcraft 2 is non-negotiable to me and I don't have enough time to play games to justify both a gaming PC and a console.

That being said the streaming setup has often been a pain in the ass causing me to spend time investigating various issues. The aim of this page is to document the steps taken to help others with the nuances.
# Options explored
## Steam Link (hardware)
- Can't do 4k
- Controller doesn't work sometimes 
## [[Moonlight on WebOS\|Moonlight on WebOS]]
- Simpler setup to just use TV
- Bandwidth limit on TV prevents anything more than 4k@60hz
- Controllers can be used for other apps on the TV.
## Nvidia shield
- Xbox button navigates to home
- Quite expensive 
- Limited to 4k@60hz which is less than 120hz the TV is capable of
- YouTube is better on LG Web OS because it has Dolby vision or something
## Long wires
- Can't remote play on other devices or outside the network
# Custom mini-PC as streaming client
- Very expensive
- More things to configure and go wrong
# Option chosen: Moonlight

I'll flesh this out to a full guide later but here's a braindump of all steps required.
1. Setup Moonlight. Follow [this guide](https://www.reddit.com/r/MoonlightStreaming/s/sMDKpXrHk3).
2. Purchase Bluetooth controllers and pair them with TV (I went with Xbox ones).
3. Purchase keyboard and mouse and pair with TV.
4. Purchase HDMI dongle. Configure Windows to only use when main display is not available.
5. Configure Moonlight to have a sane experience with keyboard and mouse (this is an outstanding issue with the client).