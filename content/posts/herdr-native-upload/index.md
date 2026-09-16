+++
date = '2026-09-16'
draft = false
title = 'Dragging local files into my remote Herdr sessions'
summary = 'My Codex sessions now run on a Netcup root server. Getting local files into those sessions led to a Herdr patch, implemented end to end by GPT-6-Astra while I oversaw and steered it.'
tags = ['herdr', 'ssh', 'remote-work', 'ai', 'linux']
categories = ['projects']
+++

I've moved my workflows, including my Codex sessions, onto my Netcup root server. I want to be able to pick up where I left off from whichever device I have with me: my iPad, another laptop, my Omarchy setup, a Mac, or even my phone.

Having the work stay on the server makes that possible. But there's still something that lives on the device in front of me: the files I want to send into a session.

It could be an image, a PDF, an archive, or another file I need on the remote machine. Whatever it is, I want to get it across and carry on with what I'm doing.

That's the reason for [herdr-native-upload](https://github.com/janaki-sasidhar/herdr-native-upload).

## Drop the file and keep going

The patch adds native file uploads to [Herdr](https://github.com/herdrdev/herdr). With the client running locally and a saved SSH machine selected, you focus a pane and drop a file into the terminal.

The file goes over SSH to the remote machine. A centered overlay shows the progress, and once the upload is verified, its remote path appears in the pane. The prompt stays unsubmitted, so you can finish writing before pressing Enter.

That last bit makes it useful in an agent session. Getting the file there is only part of it; I also need to tell the agent what I want done with it. The inserted path gives me something to refer to in that message.

There's no file-sharing service in the middle. The transfer goes to the machine where the work is happening.

## GPT-6-Astra implemented it

I should be clear about how this came together: **GPT-6-Astra implemented it end to end. I was overseeing and steering it.**

That's how this project connects to something I mentioned in [my Linux and Omarchy post]({{< relref "posts/from-my-first-laptop-to-omarchy" >}}). Having an AI coding tool available makes me more willing to change the software around my workflow.

Here, I knew what I wanted: get a file from my local device into the remote session without making it a separate task to deal with. I could steer the implementation towards that behavior while the model did the coding.

This is also why I'm being specific about my role. When I share something like this, I want people to know how it was made.

## Trying it

This is an independent source patch for **Herdr 0.9.0**, and you'll need to build the local client. The [README](https://github.com/janaki-sasidhar/herdr-native-upload#readme) walks through the build and setup.

The tested setup is **Linux ARM64 with Ghostty**. My goal of resuming work across devices is broader than the upload patch's current tested support. Other client setups still need testing.

The local-client part matters: an ordinary SSH session with Herdr running entirely on the server can't read files from your laptop.

Uploads have configurable limits, and Esc cancels a transfer. The path is inserted as text; whether an agent can read a particular file format depends on the agent.

The [source and issues](https://github.com/janaki-sasidhar/herdr-native-upload) are public. If you try it with a different terminal or file manager, let me know how it goes. That's particularly useful feedback at this stage.
