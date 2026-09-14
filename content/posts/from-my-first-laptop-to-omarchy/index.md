+++
date = '2026-09-14T12:37:42+02:00'
draft = false
title = 'From my first laptop to Omarchy'
summary = 'From discovering GNU and installing Arch to spending most of my time inside Emacs, then wanting a simpler setup. How Omarchy got me interested in my desktop again.'
tags = ['linux', 'gnu', 'emacs', 'omarchy', 'arch-linux', 'i3', 'asahi', 'personal']
categories = ['personal']
+++

Back in 2019, I got my first laptop, a Lenovo IdeaPad 330. Seven years ago now, which feels a little strange to write.

I liked that laptop a lot. It came with Windows, and that's what I used at first. But somewhere along the way I got curious about Linux, GNU, and everything around them. Filesystems, kernels, networking. There was a lot I didn't understand, and I wanted to figure it out.

My interest in GNU grew after watching talks on YouTube about [Richard Stallman](https://stallman.org/) and the Free Software Foundation. I got interested in the free software movement and wanted to learn more about the ideas behind the software I was exploring.

This was before AI assistants were part of how I worked. A lot of the learning came from reading, trying something, getting it wrong, and going back to read again.

My first Linux installation was Ubuntu, dual-booted with Windows. From there I got interested in Linux VPS machines too. Gradually, I started understanding what a distribution was, what a desktop environment was, and how those pieces fitted together.

Then I found Arch.

## Getting Arch installed was only the beginning

I think I failed three or four times before I successfully installed Arch Linux. I was doing the manual installation, following the documentation step by step. Whenever I got stuck, I'd go back, try to understand what I'd missed, and give it another go.

Getting it to boot was satisfying. Then came the next part: the setup I'd installed was bare. No desktop environment, no graphical login screen. I had to decide what I wanted to put on it.

That led me through KDE, GNOME, and eventually i3wm. **i3 was my absolute favourite at the time.**

I got very into ricing, which is basically customizing how your desktop looks and behaves. I spent a lot of time on it. The desktop itself became something to work on, and I enjoyed having that much control over it.

I also tried compiling Gentoo for a while and spent time with distributions like Manjaro. But whatever else I tried, I kept coming back to Arch with i3. That was the setup for me.

## The days when everything was inside Emacs

I also spent quite a while in the Emacs ecosystem. I started with Doom Emacs in Evil mode, using its Vim-style bindings, and later moved to Emacs's own keybindings.

I used Org mode a lot. Telegram was in there too, through [telega.el](https://github.com/zevlg/telega.el), along with mail clients. Apart from the browser, pretty much everything I did was inside Emacs during those days.

It wasn't a particularly frustrating experience, either. I spent a lot of time there and liked it. Eventually I drifted towards VS Code. Once I was employed, I had less free time for exploring and playing with my setup. There wasn't some big problem that made me leave Emacs; I just gradually started using other things.

## Then I bought a MacBook

Coming from the Lenovo with its slow hard drive, the MacBook felt like a breath of fresh air. And honestly, I liked macOS too.

I still missed being able to customize things the way I could on Linux, though. That part never really went away.

Over time, I had less appetite for switching distributions and spending hours on the desktop. I still liked Linux. I just wanted a setup that worked for me without always having another thing to configure.

I used Fedora for quite a while, and Arch stayed around on my VPS machines. Linux was still part of what I did, even when I wasn't constantly rebuilding my desktop around it.

## Finding my way back

Before I found [Omarchy](https://omarchy.org/), I'd already come across [Asahi Linux](https://asahilinux.org/) and tried it on my M1 MacBook Pro. I tried setups with KDE and Arch along the way, but I wasn't getting as excited about the desktop as I used to.

More recently, I got interested in [DHH](https://dhh.dk/)'s work and found Omarchy. That caught my attention.

By then, AI coding tools had also become part of the picture. There's a separate post I want to write about those, but they matter to this story because they change how approachable desktop customization feels to me.

A lot of the parts I want to change are controlled by configuration files and code. If I want the bar to behave differently, I can work on that with an LLM. I can describe a change, look at what it produces, try it, and adjust it.

There's still reading and testing involved. But being able to get help working through a change makes me more willing to try it. I can start with a desktop that works for me and change the bits I care about as I go.

That's an appealing place to be after spending so much time both customizing Linux and wanting a break from customizing Linux.

And now I've ended up building things for my desktop again: [Codex LB for Omarchy]({{< relref "posts/codex-lb-for-omarchy" >}}) and [Window Shelf]({{< relref "posts/window-shelf-for-omarchy" >}}).

Back on that Lenovo, I was trying to get Arch installed and figure out what all the pieces did. These days, I'm more interested in making a few of those pieces work the way I want. Omarchy has given me a reason to spend time on that again.
