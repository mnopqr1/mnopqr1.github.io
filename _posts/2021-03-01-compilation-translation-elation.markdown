---
layout: post
title:  "Compilation, Translation, Elongation"
---

...and then it was March! Spring is slowly beginning to show itself where I am. Scroll down for: a Retro Game on a Home-Grown Compiler, what The Stack has to do with Fashion Choices, and Translation Trouble.

Last week and this weekend, I wrote a [compiler](https://github.com/mnopqr1/MyNand2Tetris/tree/master/Compiler) for the language "Jack", [project 11 of the Nand2Tetris course](https://www.nand2tetris.org/project11). The parser I wrote about in my previous post was about the halfway point. Now that I have the compiler the one thing that I did not build myself "from scratch" is the operating system. 

Sunday evening was spent writing a clone of [Space Invaders](https://github.com/mnopqr1/MyNand2Tetris/tree/master/JackSpaceInvaders) into Jack, so that I had something original to test my compiler on. Retro vibes:

![Sunday Space Invaders](/assets/jackspace.gif)

Yes, yes, yes, I know, the graphics capabilities of the "Hack" computer platform are limited, and the "clone" is unfinished -- the aliens don't shoot back and, more importantly, they also don't die. 

But *aren't they cute*?[^compilation1] 

Zooming out a bit, this is what it actually looks like inside the "Virtual Machine Emulator" provided by the Nand2Tetris course for testing purposes. You can think of this as the "shell" in which your program runs. Als comparable to the program `python` when you type `python my_cool_script.py` or the program `java` when you type `java MyLovelyProgram` into a terminal. Except this virtual machine shows a lot more information about what is going on under the hood.

![VM Emulator](/assets/vmemscreen.png)

Some learning highlights for me from the second half of the Nand2Tetris course:

* The **stack abstraction**, or: how a college student chooses what clothes to wear. 

    You only allow the machine to throw things on a pile and then take things off the pile one at a time. The last thing you threw on the pile is the first thing you take off the pile. 

    This may sound very restrictive, and it is. But it is (perhaps surprisingly given the clothes analogy) a nice way to organize memory usage - as with most things, once I got used to it, it made sense to organize things that way.

    Oh, I should say, the real name for that pile is the stack. Although the French call it *la pile*. Throwing things on it is called *pushing* and taking things off of it is called *popping*.

* **Compilation = translation.** When you write high level code in Jack or Java [^compilation2], it is first translated into code that that talks mostly about the stack, pushes and pops, can do some iffing and elseing, maybe a function call here and there, but that is it. No objects. No while loops. No variables even! This step is itself executed by a computer program called The Compiler. It takes as input the high level code, and spits out a list of instructions in "Virtual Machine Language": [here's an example of what that looks like](https://github.com/mnopqr1/MyNand2Tetris/blob/master/JackSpaceInvaders/SpaceInvadersGame.vm). A computer's central processing unit still can't read code in the VM language: this code needs to be translated into "Assembly Language" - that's where you really get down to the level of 0's and 1's. So the order is:

    High-level language --> VM language --> Assembly language --> Central processing unit

    Interestingly, the Nand2Tetris course (Did I already mention that I liked this course a lot? Because I did.) teaches this entire process "in reverse": you start with constructing a CPU that can transform assembly instructions into actual electronic events, then an assembler, then a translator from VM language into assembly, and only at the very end a compiler. The compiler has a parser as a crucial component, see my previous post on this blog.

    In a sense, *all* of computer science is ultimately **about** translation, at least as much as it is about math. I believe that having a good feeling for language can be just as (more?) important for becoming a good programmer as being good at math is. Unfortunately education systems in some countries tend to push their most motivated students to take math and sciences courses, while they then (completely mistakenly, in my opinion) label language courses as being "just for fun". 

* **Oblong or elongated**, that is the question.

    This is not directly related to Nand2Tetris but it is related to translation, and possibly also to my next project. Some fellow Recursers and I were playing [Codenames](https://codenames.game) last week and was the *Spymaster* for the first time. If you're not familiar with the game: you are shown 25 words, 10 of which are for your team. Only the spymaster knows which words they are, and needs to point their other teammates towards them as quickly as possible, while steering them away from the other 15. To direct them towards these words, every turn, the spymaster gives a *clue*, which can be any English (here starts the trouble, or fun, for my team) word, except proper nouns. (And of course you can't actually say one of the words that your team members are supposed to guess.)

    I like this game a lot, and (because?) I am pretty bad at it. I was trying to find a common description that applies to, if I remember correctly, "bulb", "gun" and "hammer", and I wanted to say the English equivalent of *[langwerpig](https://www.deepl.com/translator#nl/en/langwerpig)*, which I now know most commonly translates to `elongated`, but the internet said `oblong`. So my clue was `oblong`. This thoroughly confused my teammates, since, so I learned, "oblong" in English has a very math-y association, and they were therefore looking for something way deeper and mathier than I intended (they ended up guessing *mirror*). Anyway, this is becoming a very long and boring description of a situation where you probably just had to be there to actually appreciate it and see why it was funny but hey, let me try to learn how this blogging thing works okay.

    Translation trouble can lead to el(ong)ation.

---





[^compilation1]: I'm biased, of course, because I [redrew them myself, pixel by pixel](https://github.com/mnopqr1/MyNand2Tetris/blob/master/JackSpaceInvaders/alienpixel.dat) and then [generated the correct Jack code](https://github.com/mnopqr1/MyNand2Tetris/blob/master/JackSpaceInvaders/generatedrawcode.py) for them because the Jack language isn't really well-equipped to deal with big-ish arrays.


[^compilation2]: Okay okay OR RUST, stop yelling at me.
