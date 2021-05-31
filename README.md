# LinuxFromScratch-Raspberry-Pi-4
How would you go about building a linux operating system from scratch? <br>
This repo describes what it takes to do that with just a raspberry pi and a _hella_ lot of willpower.

\** ***Disclaimer*** \** <br>
The guide for this build is not owned by me. It has been provided by:
- http://linuxfromscratch.org (Main resource for the build)
- https://intestinate.com/pilfs/ (Supplementary resource if you're building on a pi)

## ...then what is this repo for?
So you've decided that you want to follow along LinuxFromScratch to learn about what it takes to build an operating system. It should be manageable because all you need to do is follow a comprehensive step by step guide right? Perhaps if you are really careful and follow all the instructions to a tee, then you could have a smooth sailing journey. However mishaps are likely going to happen and you're going to need to fix it. But being able to understand the system which you're building in order to understand the system is a serious chicken and egg problem. In my opinion, the LFS truly only makes sense to people who already have general system administration skills, experience with linux and a broad and high level overview of the entire stack of computing. However if you're like me and using it as a launchpad for learning... you're in for a hell of a ride (Just a gauge, I've had about a year of college computer science experience and taken a operating systems course and still found myself highly confused). For those daring and enthusiastic individuals that after reading this think that they may be biting off more than they can chew, I write this for you. This repo is meant to bootstrap you to help you get through LFS without (hopefully) too many knowledge gaps. 

I have three sections in this repo:
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
### **The operating system in the entire computer stack:**<br>
The problem with trying to figure out the operating system is that it is only one part in the entire stack of computing. By the stack of computing, I mean from the electricity flowing through metal to how code runs in order for you to use the applications you have on your computer. The operating system is somewhere in the middle of all this and there is really no such thing as learning about it in isolation. This does not mean that you need to be an expert at everything but you will at least need to be able to orient yourself and know what you're dealing with.

Let's say you want to build an entire computer from scratch. Most people can name-drop a couple of the parts you need to make the computer (CPU, Harddisk, Monitor, Keyboard, etc.). We also know that electricity is involved in some way. However, between switching on the power supply and our computers becoming usable is a big gap and if you think hard about it, having electricity turn into an interactive display that we can interact with a keyboard is a huge jump. If you have come to the conclusion that the operating system makes the hardware usable, you are absolutely correct. I like to think of the operating system as the government and the hardware as different societal functions. Either one by itself can't achieve anything. However put together, the operating system can "initiate" and "organize" the hardware in the system such that it makes our computer usable. This is an extremely high level idea of what is going on. But the foundational takeaway here is that:
1) The operating system is a fancy name for a program that makes the hardware work as they were intended to
2) Because the operating system is itself a program, it needs someway to start. Check this explanation to get an idea https://www.quora.com/How-do-computers-work-the-way-they-do-When-does-electricity-become-executable-logic-and-how
3) The operating system once up and running is then responsible for being the translation medium between your devices (e.g. if you want to display something on your screen, both your screen and the hardisk where what you want to display is involved. The operating system is responsible for initiating and facilitating the communication between these two pieces of hardware)


### **The terminal:**<br>
A lot of work will be done using the command line. Basic navigation and file manipulation will let you get by but a strong base will allow you to do so much more. I recommend that you at least have good working knowledge of the following commands: {cd, ls, cat, less, grep, rm}. In addition, make sure you know how to use piping "|" and redirection ">" & "<".

A lot of us may already know how to use it but I found that it helps to _know_ what it is?<br>
The terminal a.k.a the shell/console/command-line/tty nowadays usually refers to the same thing. However this wasn't the case in the past. Read this to get an idea: https://unix.stackexchange.com/questions/4126/what-is-the-exact-difference-between-a-terminal-a-shell-a-tty-and-a-con

## What on earth is going on here
When you build any program, you need to make sure that it can run on your machine. Likewise, when you build an operating system, you're building a program that can be run by your computer's processor. In light of this, part of the book aims to teach you the idea of "cross compiling". The aim of cross compilation is to make the program you're building runnable on a processor of your choice regardless of the processor that you're building your program on. For example, let's say you have a machine that uses an x86 processor and you have a program on it that you want to run on a ARM processor, in that case then you would need to cross compile. In the LFS guide, the assumption is that you're building LFS to be run on the same machine that you are building it. That means that you don't actually need to do cross compilation. The book 'fakes' cross compilation as an educational detour by taking you through the steps you would take if you were actually cross compiling. However, because you run LFS on the same machine as you build on, you could actually just use the compilier already built into your computer.

Depending what your setup is, if it differs from the guides, you should try to anticipate what problems you could encounter. In my case, I decided to build LFS on my Raspberry pi 4 which has an ARM processor. Be aware that LFS was written targetting x86 machines, so some of the steps/configurations in the guide don't pertain to the ARM processor. Additionally, the raspberry pi has a specific bootloader developed for it so it doesn't use the typical linux GRUB bootloader. I highly recommend that once you reach the point of the bootloader, save your work and then try to successfully use the raspberry pi's own bootloader before trying to integrate GRUB.

Here I also feel like I should add that in building the operating system you're not actually going to write any source code. Instead a better description of what you're doing is cherry picking tools that have already been written and available on the internet and packaging it together to acheieve a minimal operating system. If you wanted to learn actual low level kernel devlopment, you'd have better luck working through a C programming textbook and go through the exercises. 

Now on to the specific chapters...

### Chapter 1: (Pre-requisites):
Like I mentioned, in order to build an operating system, unfortunately you need a working one to build another one off of. The recommendation is to have one of the more popular linux distributions because they are more likely to have all the tools you already need to start working with. If not, you will need to follow the instructions and get all your missing packages.

### Chapter 2: (Preparing the host):
Host, what host? Things can get messy when you're building an operating system on a system that already has one. We need some way to separate the two so that we can later on interact with them separately and make sure our new system can work without reliance on the old one. This is where partitioning comes in. All we are really doing here is developing our new operating system on a partitioned disk. I initially got intimidated by the sound of that. I have no idea how to do that! Don't worry, it's not that scary. Things that you need to know are: Storage devices and Filesystems
1: Storage devices are any kinds of devices on your system whose job is to hold data. You could very well partition your storage devices so that instead of 1 large block of 1TB it appears to your computer that you have two 500GB storage spaces.
2: Filesystems are just ways of organizing data in these blocks. 
For reason's I am not yet aware of, you would think that two comes together but they don't. What I mean by this is that conducting a partition on your storage device which implies that you could just split the space in half and if you had existing data and it was under 500GB, it would all be in the first partition. Unfortunately, it's not entirely obvious that the spave on the hardrive is stored like that. You would first need to downsize the filesystem which will help you determine that storage is confined in the range of the first half before actually conducting the partition.

### Chapter 3 & 4: (Downloading packages & setting up the environment):
This is the part that where you will get all the recommended tools that LFS thinks would help you build a minimal system. There are various ways of downloading these packages from the internet but you will need to know "how to download from source". In general, you will be downloading these files called "tarballs" which are archived folders (compressed source code) that you will need to first decompress, then specify configurations before you compile and install. Setting up the environment is setting a user that you will use specifically when developing the system so as to sandbox your permissions and don't go accidently deleting things you aren't meant to.

### Chapter 5: (Cross compiling toolchain):
You should've paused towards the end of the previous paragraph. Before you are able to compile these packages, you need to have a compiler that can compile for your target processor architecture. This is where the cross compiling toolchain comes in. It is refered to as a toolchain because compilation is actually a multistep process. Namely when you turn source code into executables it goes through preprocessing -> converting to assembly code -> converted to object files -> linking all the object files. Each step here is made available by combining three tools that are in the packages that you downloaded and are {binutils, gcc, glibc}. Therefore this chapter deals with how to build a cross compiling toolchain which allows us to produce a compiler that can firstly run on the target architecture that we are building for AND compile code for that target architecture. This is a tricky idea to get around. What we want to do is compile a compiler that runs on and compiles for our target processor.

### Chapter 6: 
