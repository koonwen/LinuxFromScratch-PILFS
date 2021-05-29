# LinuxFromScratch-Raspberry-Pi-4
How would you go about building a linux operating system from scratch? <br>
This repo describes what it takes to do that with just a raspberry pi and a _hella_ lot of willpower.

\** ***Disclaimer*** \** <br>
The guide for this build is not owned by me. It has been provided by:
- http://linuxfromscratch.org (Main resource for the build)
- https://intestinate.com/pilfs/ (Supplementary resource if you're building on a pi)

## ...then what is this repo for?
Whilst the guides do cover a lot of ground. I often felt like there were still gaps in my knowledge. Perhaps that has to do with the assumed level of knowledge that the writers expected prospective builders to have. Anywho, I have put together some information that has helped me to make sense of the whole process as well as some advice I would've given to myself. Hopefully this resource can help someone out in the future.

## Let's get started
TIP 1 (How you can learn): Get an idea, hack at it, then revisit to understand
- This is a learning pedagogy that is really effective for this project. Basically, when you come across something that you don't know and need to use, roughly figure out what it does through the documentation and hack at it (this means that you trial and error to try and get something to work with limited knowledge of it). Only come back and re-read the documentaion if it comes up again.
- But wouldn't it be more effective to just read the documentation thoroughly instead of having to go through all that trial and error? Well, from my experience, chances are is that you're only going to need a fraction of what the documentation offers and you'd end up forgetting the majority of what you read. In addition, quick lookups trains your ability to read documentation (This is actually an underated skill). You need to know how to sieve through things and get only what you're looking for. Skimming to find what you're looking for teaches you how to recognize what you need to recognize. Finally, making mistakes when you use things wrongly helps you learn more than getting them right.
- I struggled with following this strategy because I found it hard to identify when I should stop reading the theory and start hacking. Therefore you will notice that I structure subsequent topics in this three step form as a guide.

*The terminal:*<br>
A lot of us may know how to use it but I found that you should also _know_ what it is?<br>
The terminal a.k.a the shell/console/command-line nowadays usually refers to the same thing. However this wasn't the case in the past. Read this to get an idea: https://unix.stackexchange.com/questions/4126/what-is-the-exact-difference-between-a-terminal-a-shell-a-tty-and-a-con

The terminal application that we click on and brings up a black window is just a terminal "emulator" a psudeo-terminal and was a physical device that allowed you to interact directly with th
A lot of work will be done using the command line. Basic navigation and file manipulation will let you get by but a strong base will allow you to do so much more. I recommend that you at least have good working knowledge of the following commands: {cd, ls, cat, less, grep, rm}. In addition, make sure you know how to use piping "|" and redirection ">" & "<".


3. This project can take you anywhere between a few days to a couple of weeks to finish depending on your pre-existing knowledge. Don't be disheartened if it takes you longer than expected. The steeper the learning curve, the more you get out of it. Also you will likely break things and get frustrated or vice versa, all part of the process.
