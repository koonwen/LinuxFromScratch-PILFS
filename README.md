# LinuxFromScratch-Raspberry-Pi-4
How would you go about building a linux operating system from scratch? <br>
This repo describes what it takes to do that with just a raspberry pi and a _hella_ lot of willpower.

\** ***Disclaimer*** \** <br>
The guide for this build is not owned by me. It has been provided by:
- http://linuxfromscratch.org (Main resource for the build)
- https://intestinate.com/pilfs/ (Supplementary resource if you're building on a pi)

## ...then what is this repo for?
So you've decided that you want to follow along LinuxFromScratch to learn about what it takes to build an operating system. It should be manageable because all you need to do is follow a comprehensive step by step guide right? Perhaps if you are really careful and follow all the instructions to a tee, then you could have a smooth sailing journey. However mishaps are likely going to happen and you're going to need to fix it. But being able to understand the system which you're building in order to understand the system is a serious chicken and egg problem. In my opinion, the LFS truly only makes sense to people who already have general system administration skills, experience with linux and a broad and high level overview of the entire stack of computing. However if you're like me and using it as a launchpad for learning... you're in for a hell of a ride (Just a gauge, I've had about a year of college computer science experience and taken a operating systems course and still found myself highly confused). For those daring and enthusiastic individuals that after reading this think that they may be biting off more than they can chew, I write this for you. This repo is meant to bootstrap you to help you get through LFS without (hopefully) too many knowledge gaps. 

I have mainly three sections in this repo:
- Tips & Advice: Generally has to do with your approach and attitude
- Broad concepts: Peripheral information that has helped me put things together
- What on earth is going on here: An easy to read summary to get a feel of what you're doing at each section of the guides.

## Tips & Advice
TIP 1: How you can learn
- Get an idea, hack at it, then revisit to understand
- This is a learning pedagogy that is really effective for this project. Basically, when you come across something that you don't know and need to use, roughly figure out what it does through the documentation and hack at it (this means to trial and error and get something to work with limited knowledge of it). Only come back and re-read the documentaion if the same command needs to be used multiple times.
- Wouldn't it be more effective to just read the documentation thoroughly instead of having to go through all that trial and error? Well, from my experience, chances are you're only going to need a fraction of what the documentation offers and you'd end up forgetting the majority of what you read. In addition, quick lookups trains your ability to read documentation (This is actually an underated skill). You need to know how to sieve through things and get only what you're looking for. Skimming to find what you're looking for teaches you how to recognize what you need to recognize. Finally, making mistakes when you use things wrongly helps you learn more than getting them right.
- I struggled with following this strategy because I found it hard to identify when I should stop reading the theory and start hacking. Therefore you will notice that I structure subsequent topics in this three step form as a guide.


TIP 2: Know how to use the manual
- Information about how to use/what a shell command does should always be looked up on the man page (this is an internal manual built in your system and directly accessible from the command line). To search for an available command that your system provides but you don't know about, use ```man -k <keywords of what you want to search for>```. This command shows you what commands/functions are provided by your system to interact with your operating system.
- The number associated to the command in brackets, e.g. ls(1) refers to the section in the manual that the documentation writes about. For our purposes, we will only likely be reading into (1): user commands or (8): System administration tools and Daemons. (search ```man man```) to get more info. This is probably the only time you want to read more "in-depth" contrary to what was advised in TIP 1.


TIP 3: Setting expectations
- Depending on skill level, this could take you somewhere between a couple of days to a few weeks to finish. By finish I not only mean have a working system but also understand what is going on in the system.
- Getting discouraged when you can't seem to figure something out is what I encountered on the daily. Just push through and things will eventually come together. A great deal of complexity has gone into the creation of an operating system and to expect that you will be able to figure it out in a few days is expecting too much.
- The steeper the learning curve, the more you get out of it. Also you will likely break things and get frustrated or vice versa, all part of the process.


## Broad concepts
*The operating system in the entire computer stack:*<br>
The problem with trying to figure out the operating system is that it is only one part in the entire stack of computing. By the stack of computing, I mean from the electricity flowing through metal to how code runs in order for you to use the applications you have on your computer. The operating system is somewhere in the middle of all this and there is really no such thing as learning about it in isolation. This does not mean that you need to be an expert at everything but you will at least need to be able to orient yourself and know what you're dealing with.

Let's say you want to build an entire computer from scratch. Most people can name-drop a couple of the parts you need to make the computer (CPU, Harddisk, Monitor, Keyboard, etc.). We also know that electricity is involved in some way. However, between switching on the power supply and our computers becoming usable is a big gap and if you think hard about it, having electricity turn into an interactive display that we can interact with a keyboard is a huge jump. If you have come to the conclusion that the operating system makes the hardware usable, you are absolutely correct. The operating system makes it possible for hardware to work together in the system. I like to think of the operating system as the government and hardware as different societal functions. Either one by itself can't achieve anything. However put together, the operating system can "initiate" and "organize" the hardware in the system such that it makes our computer usable. This is an extremely high level idea of what is going on. But the some things that give good context is that:
1) The operating system is a fancy name for a program that makes the hardware work as they were intended to
2) Because the operating system is itself a program, it needs someway to start. When you run electricity through the system, electricity encounters what we call a BIOS which directs the flow of electricity in such a way that we end up with some primitative instructions. (Think of pouring water into an elaborate pipe system, water will flow according to the pipe system and depending on the pattern, kick start some kind of motion).
3) This motion involves checking for hardware and getting the operating system to run.
4) The operating system once up and running is then responsible for being the translation medium between your devices (e.g. if you want to display something on your screen, both your screen and the hardisk where what you want to display is involved. The operating system is responsible for initiating and facilitating the communication between these two pieces of hardware)


*The terminal:*<br>
A lot of work will be done using the command line. Basic navigation and file manipulation will let you get by but a strong base will allow you to do so much more. I recommend that you at least have good working knowledge of the following commands: {cd, ls, cat, less, grep, rm}. In addition, make sure you know how to use piping "|" and redirection ">" & "<".

A lot of us may already know how to use it but I found that it helps to _know_ what it is?<br>
The terminal a.k.a the shell/console/command-line nowadays usually refers to the same thing. However this wasn't the case in the past. Read this to get an idea: https://unix.stackexchange.com/questions/4126/what-is-the-exact-difference-between-a-terminal-a-shell-a-tty-and-a-con




