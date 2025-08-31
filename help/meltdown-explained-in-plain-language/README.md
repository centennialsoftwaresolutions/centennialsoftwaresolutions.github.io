# Meltdown explained in plain language

![meltdown](meltdown.png)

This post attempts to explain Meltdown in plain language.

Meltdown allows a program to get something it shouldn't be able to get.

An operating system manages a computer. Windows 10 and Mac OS X are operating systems. The operating system helps the computer run programs like Firefox and Office. Operating systems and the computer ensure that programs like Firefox and Office **cannot** get **special things** that the operating system needs to keep private. **Meltdown** allows a user program to get these special things.

Meltdown works by exploiting how computers **actually** run programs - as opposed to how they were **designed** to run programs. A computer is designed to run as much of a program as it can. It is even designed to start running parts of a program that the user hasn't asked for. It does this to have the things those parts "get" ready **if** the user needs them. Its like going and getting a glass of water for your grandma before she asks you for it.

Computers are also designed to allow programs to keep things "**close**" a.k.a. at hand. If a program needs something and it is already "close" the program can just use the thing that's at hand instead of needing to go get it. This is akin to getting out all of the art supplies needed for a project so that you don't have to continually go to the cabinet to get them.

The program that "fetches water for grandma before she asks for it" also saves stuff "**close**" so that it can get it quickly. If grandma doesn't want the water, the computer gets rid of anything related to the program **except the stuff that the grandma program brought in "close," like the actual glass of water.** Having this unneeded stuff "close" is usually not a big deal, unless the stuff that's "close" is the secret thing that only the operating system should be able to see.

Remember, the computer and operating system are **designed** to stop a program from getting at its secret things. Because of the way a computer is **actually implemented** the program can actually **infer** if the secret thing is "close," Extending the art supply analogy, its as if someone got out a locked box of art supplies with the label: "colored pencils." You can't actually get in the box, but you **infer** there's colored pencils in it because of the label. Note: if the computer writes "colored pencils" on a box, there will be colored pencils in the box.

Meltdown starts by building a bunch of boxes without labels. It then runs the "get grandma a glass of water program". This program will write a label on **one** of the boxes: the name of the secret thing. Meltdown will look for the one label that has been filled out after the grandma program runs. Once it finds it, it knows the secret thing.

Please let me know in the comments below if this description helped you understand Meltdown.

\* Meltdown image at [link](http://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Meltdown_with_text.svg/1200px-Meltdown_with_text.svg.png) found with Google image search