# Hi! 

## It's Friday! 

---

# What we're doing here in general 

^ There's a lot to being a developer, and Erika and Jen are only going to teach you part of it. They decided to bring me in to pinch hit on a bunch of small things that I wish someone had told me, or in some cases that someone DID tell me, that I can now pass along to you. What sorts of things? 

--- 

* How to feel like a real developer 
* Fun things about Xcode 
* Stupid things about Git 
* How to talk to clients 
* The dark underbelly of storyboards 
* How to work with assholes* 
* Reviewing someone's code when you feel dumb 
* Making a five-year-plan

---

# What we're doing today 

---

> Fighting imposter syndrome every time you open your terminal 

^ One thing that weirdly got on my nerves after I graduated out of the bootcamp I went to and out of the apprenticeship here at Labs is that all the other, big-girl-pants developers I worked with had some fancy tricked-out command line, but I just had boring default text. I felt super self-conscious about it and like a total imposter each time I looked at my command line. Which is a bummer, and unnecessary emotional overhead. So, for you this morning I am going to teach you how to have a real live developer fancy command line prompt. It sounds silly, but I promise you it will help you feel like a badass real dev. 

---

## `vim ~/.bash_profile`

^ So open up your terminal...I'm kidding, I'm not going to make you do this in vim. Although, if you want to feel like an actual facts hacker, learn how to navigate and use vim. What text editors do you all use? 

---

## `<editor> ~/.bash_profile` 

^ okay, now who is getting a message that they don't have one? Sidenote, every single time I do this, I swap the . and the / so make sure you didn't do that. I did it fifteen times last night alone. 

--- 

## `cd ~/`
## `touch .bash_profile`

^ How much did they teach you about moving around on the command line? Don't worry if it's not a lot, I'm just curious. What this first line is doing is taking us to the home folder, and the second line is creating but not opening a file called .bash_profile Now, if you didn't have one before, go back and do this (back up one slide)

--- 

## `PS1=""`

^ You are looking for a line that says this. Maybe you don't have one, that's cool. Go ahead and type that in if you don't have it already. This PS1 business is a parameter, the first parameter, and it expands into the first line of your terminal prompt. If you want two lines, you'd add a PS2. PSes 3 and 4 do other things, though, so satisfy yourself with two lines. 

--- 

## `PS1="Hello, friend "`

^ So you have a parameter, great, what do you want to put in it? try typing this. Then, save your file, and go back to your terminal and run 

---

## `. ~/.bash_profile` 

^ OH LOOK YOUR COMPUTER THINKS YOU ARE FRIENDS. I bet you feel bad about all those things you said to it this week. 

--- 

> That's great, Anne. 
> Creepy, but great. 
> How about something useful? 

---

\a : an ASCII bell character (07)
\d : the date in “Weekday Month Date” format (e.g., “Tue May 26”)
\H : the hostname
\u : the username of the current user
\t : the current time in 24-hour HH:MM:SS format
\T : the current time in 12-hour HH:MM:SS format
\@ : the current time in 12-hour am/pm format
\A : the current time in 24-hour HH:MM format
\h : the hostname up to the first ‘.’
\H : the hostname
\W : the basename of the current working directory

^ There's a whole secret code to the sort of thing you can put into your bash profile, and I regret to inform that it's a lot of unintuitive cryptic nonsense. There's more than what I've got here, and I'll have some links at the end that I will send all of you that will show you all the options. For now, we're going to do today's date, the current working directory, and an emoji. 

--- 

## `PS1="🥞 \u \W $ "`
##  
## `. ~/.bash_profile` 

^ I like pancakes, let's go with pancakes. I like to use the $ as the sort of end...guy, that lets you know where to start typing, but you can go ahead and put something else there if you like. remember to run that bash_profile line to reload it and see how it looks. 

---

> This is...okay...

^ So that's a start right? Already looking a bit better? But what is this, the first half of Wizard of Oz? We live in a technicolor world. Don't worry, we can add colors very easily. 

---


\[\033[0;30m\] # Black
\[\033[0;31m\] # Red
\[\033[0;32m\] # Green
\[\033[0;33m\] # Yellow
\[\033[0;34m\] # Blue
\[\033[0;35m\] # Purple
\[\033[0;36m\] # Cyan
\[\033[0;37m\] # White

^ Like I said, cryptic nonsense. I'm sure this makes perfect sense to people who understand more about bash scripting that I do, and I am very happy for them. But there are color codes that we can wrap around parts of our PS1 code to make them even prettier. These are what are called the "Regular" colors, there's also "High Intensity" options. Also, these are only going to change the text colors, if you want to change the background colors for any of these bits, you can do that too. I've got links at the end for more details. 

---

## PS1="🥞 \[\033[1;34m\]\u \[\033[1;35m\]\W\[\033[1;37m\] $ " 
##  
## `. ~/.bash_profile` 

^ and here's how colors work. Let me walk you through this, because things just got a LOT more complicated. We've got our emoji, then we have the color code for blue and it will make everything following it blue, until it gets another indication to stop the blue. We have the slash-u for our username and then we have the next color code, this one for yellow, that will just make everything that follows yellow text and then the color code for white so your final prompt guy and everything you type will be white. Let me know when you want me to go back to the color code slides so you can try out different colors. remember to run that bash_profile business each time to see the new output. 

--- 

## You know what sucks? typing the same long thing over and over. 

^ Possibly, by now, you are getting sick of typing dot tilde dot slash dammit delete delete delete dot space tilde slash... 

--- 

## alias reload=". ~/.bash_profile" 

^ back in the profile, add this line above the PS1 business. Save it, and this time, on your command line, just type "reload" You maybe didn't notice anything, but...go back, change a color or something and try it again. 

--- 

# Aliases are cool 

^ This is another cool thing you can do to help yourself feel like a Real Developer. Set some aliases in your bash profile and they will be available to you globally. 

--- 

alias branch="git checkout -b"
alias gb="git branch"
alias gco="git checkout"
alias update="git pull upstream master"
alias jj="cd ~/Development/JJ/jimmy-johns-ios"
alias c="clear"

^ here's a few I have, I have actually got dozens, some of which I hardly use and some that have completely replaced the actual command in my brain and muscle memory. I don't know how to make a new branch anymore. 

---

# Some resources: 

* http://bashrcgenerator.com/ 
* http://blog.taylormcgann.com/tag/prompt-color/
* https://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/
* http://ezprompt.net/ 
* http://osxdaily.com/2006/12/11/how-to-customize-your-terminal-prompt/

--- 

# Other Cool Things 

* get the weather 
* alias common typos 
* show your git branch name 
* show your git status 