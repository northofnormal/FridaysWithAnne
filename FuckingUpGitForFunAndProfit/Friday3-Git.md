
# ~~Fridays~~ 
# ~~Thursdays~~
# With Anne 

---

# Everything is Chaos and Time is Meaningless 

___

# Git Dilemmas 


^ In my notes, this is called "Fucking Up Git For Fun and Profit: Your New Career." But that sounds dire, so I went with this instead. Basically, Git is the thing you will be doing most, after actual iOS stuff. And it's how we keep track of our work and how we keep from killing each other. 

---

## `git add -p` 

^ So the first thing you need to know is how to make sure you are sure that you wanted to make every change and that every change is a thing you are doing on purpose. One way to do that is to LOOK AT ALL OF THEM ONE AT A TIME BEFORE YOU STAGE THEM. Know what you are adding to a commit. 

^ Open up the sonnets file, remove the text at the top and one random line. Use git add -p to make a commit that cleans things up. 

--- 

## I've been working for six hours and I have 475 changes addressing 14 different features and NO ONE CAN KNOW MY SHAME 

^ I know that Erika and Jen have probably been explaining the important of small commits, and breaking up your work into sensible, self-contained digestible bits. But I am here to tell you that you are going to screw that up and git add -p is a good way to pretend you aren't a lazy jerk. 

^ If you've been working on a card for updating the login UI and in the past few hours, you've changed the wording of the password prompt, added a new font and updated all the labels to the new font, and moved the login button to the bottom of the screen and changed the background color, and also fixed that typo in a totally unrelated file that's been bugging you for a week...and haven't committed a single thing, you can selectively add each bit of that to individual commits. This isn't an excuse to not have good practices, it's just a way to fake it on the rare occassions when you forget. 

--- 

## I've got all these changes and I don't want to commit them but I need to context switch and oh god what do I do with all this stuff? 

^ So let's say you've been working on something, and maybe it's not done yet, but you need to context-switch. One of your pull requests has a comment on it, and you need to hop over to another branch and you don't want to commit all the work that's in progress, but...you don't want to lose it, either. 

--- 

## `git stash`
## `git stash pop` 
## `git stash list` 
## `git stash save <friendlyname>` 
## `gist stash apply stash@{#}` 

^ git stash works like a little pocket you can sweep all your changes into. They will sit there quietly until you are ready to come back to them. (delete a line, save, stash-switch to another branch, see that the line is still there, switch back and pop) 

^ You can also check what you have stashed, and selectively apply stashes, maybe skipping the most recent one to the one below. This works well with git-stash-save-name, so you can give your stashes friendly names and keep track of them that way. 

---

## I hate all of this and everything is garbage  


^ And sometimes you start working on something and an hour goes by and my god this is all garbage and this will never work you just need to set it all on fire. Fuck everything, none of this works. And you could ctrl-Z everything, but it's been an entire bloody hour. 

---

## `git reset --hard` 

^ demonstrate by deleting a bunch of lines, putting in the cupcake ipsum, save, the noping them back (Bonbon fruitcake croissant powder. Gummi bears toffee powder croissant apple pie. Ice cream carrot cake topping tart carrot cake cupcake danish chocolate cake cotton candy. Lollipop caramels lemon drops chupa chups muffin chocolate cake cupcake cupcake. Carrot cake icing muffin pie halvah chupa chups icing pudding. Chocolate croissant tart cake liquorice gingerbread. Candy canes caramels soufflé bear claw gingerbread apple pie jujubes lemon drops. Halvah gummi bears carrot cake oat cake marshmallow tart pie topping carrot cake. Candy jelly marzipan wafer candy canes cupcake sugar plum. Halvah sugar plum jelly-o fruitcake. Icing pudding croissant muffin cheesecake. Halvah cotton candy pastry.)

---

## I added something to a commit but I don't actually want it there when I finalize the commit 

^ I tend do this a lot--I like to leave comments to myself in my code. Do this next, this doesn't work, refactor this later, etc. And sometimes those comments get accidentally staged, or added to the work I want to commit. Unstaging is actually pretty easy at this point. 

---

## `git reset <filename>` 


^ Make some changes, add one line of cupcake ipsum, save, then stage everything. Then, git reset  the staging and run git add -p again 

---

## ...oh crap, I actually committed that 💩

^ Sometimes we don't catch these things and accidentally commit them. It happens. You can either remove it and make a new commit, or you can undo that original commit, reset and re-stage everybody and then redo the commit. Persuch: 

--- 

## `git log --oneline` 

## `git reset HEAD~` 

^ Makes some changes, save them, make the commit. Then run the above. Explain git log and why oneline is helpful. Then! reset HEAD~ 

---

## I made my branch off the wrong branch. 

^ I do this ALL THE TIME. Sometimes you are building off something that hasn't been merged in to master yet. And sometimes, you screw that up. And by you I mean me and by sometimes I mean always. 

--- 

## REBASING IS TERRIFYING

^ I'm not going to lie. Rebasing scares the shit out of me, always. Usually, before I attempt it, I make a branch off the wrong branch so I can silo some of the code and not lose my work if something goes wrong. I'm not actually going to show you how to do this, because it's some serious high-flying business, and it's a good moment to find an adult. But I want you to know that a) it's a thing that exists and b) it's not a thing you need to worry about often. 

--- 

## There's a merge conflict, I need to quit this job and go live in the woods. 

^ Instead, let's talk about something that IS a thing you will need to do, and will need to do often. A merge conflict. Conflicts occur when the git algorithms can't figure out what to change and what to keep, so they throw up their hands and say--you figure it out, smartypants. They are scary, but they aren't the end of the world. 

^ SO I'm going to try and generate a merge conflict, and also show you how they can happen. (make additions to one line on branch-1, go back to master and make a change to the same line, go back to branch-1, try to merge master!) 

^ And hopefully we have a conflict. Now it gets scary, because we are using vim. Here's some commands in vim that you are going to want to carve on your soul: 

--- 

## `:/>>>>>` 

## `:/wq` 

^ So, a merge conflict looks like this. It will tell you what the HEAD changes are--HEAD here is going to be the top, or latest changes, of your branch--and the conflicting changes in the branch you are trying to merge in. Basically, you need to decide which changes you want to keep going forward, and which you want to get rid off, and then you need to get rid of the signal text for each conflict. Talk through what you do! You have muscle memory and they don't!


--- 

## Never ever ever force push. Ever. Don't do it. * 

--- 

\* Some conditions apply

* If you know, like super know, like are really sure you are right 
* If you've just rebased or reverted or did something to muck up the git history 
* If you are definitely trying to overwrite something for a super good reason (this is vaguely shady, though, so be cautious) 

--- 
 

## Being a good Git citizen

^ The whole thing about git is that it's about working with other people peacefully and productively. 

--- 

## A Good Pull Request 

* The reason you did it (link to a card or ticket or whatever) 
* What you did (description of the work/feature) 
* How you did it (details on your approach, decisions made, etc) 
* How they can do it (testing details)
* Here, look at it! (screenshots)

--- 

## Reviewing Code 

* How would you do it? 
* How did they do it? 
* Does it follow agreed-upon standards? (code style, patterns) 
* Do you understand it? 
* DOES IT WORK? 