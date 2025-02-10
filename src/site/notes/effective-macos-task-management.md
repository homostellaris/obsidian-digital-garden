---
{"dg-publish":true,"permalink":"/effective-macos-task-management/","tags":["productivity"]}
---

I believe that operating systems generally have frustrating task management and that we generally underestimate how much this slows us down. If we think something like "I want to see my latest Slack messages" then it should be effortless to do that but instead many of us start the absurd process of alt-tabbing an undetermined amount of times until we get to the Slack window. This constant friction is like death by a thousand cuts for productivity.

However I've found a system with MacOS that sucks significantly less hard than others I've tried.
# High-level
At a high level you are doing one of these three activities when using a computer:
1. Focusing on a task
2. Communicating
3. Doing admin / busywork

Lets combine that with a few principles:
1. We want to spend as much of our total time towards the top of this list as possible.
2. Alt-tabbing is only worth using to switch to the last window or maybe the one before that otherwise it just slows us down compared to other methods.

In essence this system just defines how to setup desktops for the different types of tasks and how to configure some apps to provide alternative ways of navigating between windows so we can reduce our usage of alt-tab to only those times when its optimal.
# Spaces
Spaces is the MacOS term for 'desktop', as in the additional virtual desktops you can create distributed across your monitors.
## Main monitor
1. Slack (full-screen)
2. General desktop, contains everything else
3. Focus desktop, contains only windows for the main task that I'm working on
## Secondary monitor
This monitor contains only one desktop that is only used when the current task can benefit from a second window that is always visible.
# Usage
Only use alt-tab in the focus desktop which should only contain a few windows. For anything else use the switch windows shortcut. Raycast is so fast and responsive that you'll find this much quicker and more enjoyable to than alt-tabbing.

Make heavy use of the other shortcuts and you'll find it trivial to move windows about so that you can switch focus to another task or move them to the second monitor organically as your current task demands.

To switch between spaces you can use shortcuts like `ctrl + 1`. However this doesn't work for full-screen windows like Slack so Raycast can be used to assign a dedicated shortcut for that like `ctrl + s`.
# Apps
You'll need to install these two excellent free to use apps.
## [Raycast](https://www.raycast.com/)
This is a game-changing MacOS productivity app that aims to replace the Spotlight feature but it does much more than Spotlight and is better seen as an OS command palette for general productivity.

Configure keyboard shortcuts for the following commands (I've included the ones I use as sub-points):
- Next desktop
	- `command + ctrl + →`
- Previous desktop
	- `command + ctrl + ←`
- Next display
	- `command + ctrl + option + →`
- Previous display
	- `command + ctrl + option + ←`
- Switch windows
	- `command + option + space`
- Slack (or whatever your main communication app is)
	- `ctrl+s`
## [AltTab](https://alt-tab-macos.netlify.app/)
This is an alternative to MacOS' default alt-tabbing. Configure it to only show windows from visible spaces.