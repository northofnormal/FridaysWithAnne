# Reviewing PRs as a Junior Dev 

^ So I wanted to talk about something that caused me a lot of angst when I was super junior. The way almost every project at Labs works is that you do some work, put up a PR on github, and then...pull down someone else's PR and review their work. Depending on the size of your project, it might just be you and one other, much more experienced developer. It'll fall to you to review their code, and man, that terrified me at first. How do you review the code of someone who has a ton of experience when you are single-digit days out of an apprenticeship? 

---

![](book.jpg)

## Read chapter 14 and tell me if the characterization is consistent...

^ Not to mention that reviewing PRs when you are onboarding to an existing project can feel a little like being given a middle to late chapter of a Russian novel and being asked to evaluate if this one secondary character is being written correctly. 

--- 

# Я не знаю, что это говорит

^ Sometimes, it feels like that AND ALSO that the novel is still written in Russian. 

---

## “I mean, it works and they know stuff and I don’t so… 👍? I guess?” 

^ And it's going to be super tempting to do this. Because, I mean, you are reviewing a complicated logic PR written by someone with eight years of experience who very patiently explained to you how to format a label yesterday. They are smart, and they've been doing this a while, and you have no damn clue what this code is doing anyway... 

--- 

# 🙅🏼‍♀️🚫👎🏻😐⛔️🚮
# Do not do this

--- 

# PRs Are Important

## So do it right 

^ There's a lot of reasons why the pull request workflow is important. It spreads knowledge around so everyone has some visibility into and understanding of all the work being done on a project. It provides a vital sanity-check to make sure work is being done correctly and according to the given criteria. It ensures that someone with fresh eyes and an independent perspective reviews all the code that is headed for the codebase. It's a constant monitor of and guarantee of code quality. It's one of the tools we use to collaborate on projects, and they serve as one mode of communication with and about the code we are writing and one avenue of feedback about our work (ideally, it's not the only one of either of those things, though). And no one is exempt from or can opt out of participating in any of that because they are too experienced or not experienced enough. 

--- 

# Step One: Does it do the thing it says it does? 
- what about when you are logged out? 
- what about when you don't have anything in the cart? 
- what about when the data is bad? 

^ There's a card on Jira with what this work is supposed to accomplish. Read that, understand it, then just...try it out. Then try it out in different circumstances or via different paths. Obviously this will be project specific, but it's a thing to consider. Sometimes, projects break work into happy path and error handling, but even when that's the case, you should poke a little. 

--- 

# Step Two: Is it formatted correctly? 
- Does it follow the agreed-upon code style for the project 
- Does it match a pattern set by similar parts of the code
- Do the function and variable names make sense? 

^ After you've confirmed that the PR does the stuff it's supposed to, start looking at the code. And going after the low-hanging fruit is a good way to start. Most projects have a code style, usually the Ray Wenderlich Swift Style guide, so take a quick look at how the code is formatted. Is there weird random white space? Is there not enough white space and things are scrunched together? Does this code "look" like the rest of the code in the project? This one is kind of weird and fuzzy, but just like an author will have a "voice", so do developers. The trick is to make sure the entire codebase sounds more like the voice of collaboration and doesn't have discordant notes. You wouldn't want to be deep into some NK Jemisin and suddenly trip over surprise Hemingway or something. If part of the code stands out as seeming "weird" somehow, think about that and try to figure out why that is and how you would re-write it. Function and variable names are one of the places where this can happen and where it can be fixed. They should be descriptive and understandable and give you a clue to what a function is doing when it's called. Nate West, one of the devs here that was really influential to how I think about code, told me once that code should read like sentences. Variables are your nouns, methods are your verbs, and when you put them together, it should be understandable if not perfectly grammatical. User dot is logged in, for example, I would expect returns a bool. 

--- 

# Step Three: How would I do this? 

^ After I've done the first two things, I take a minute to think about, very roughly how I would have done this work. I don't even get as far as pseudocode, it's entirely conceptual. Let's say we're displaying a button if the user is logged in, and hiding it when they are logged out. So I'd check the user's login status, set the isHidden property based on that, maybe do some other UI stuff so the layout doesn't look goofy without the button... that's as far as I'll go. And, to be clear, especially at this stage, it's totally okay if your response to "how would I do this?" is "fuck no, I'd run and hide and maybe cry." If you have flat-out no idea how you'd approach this work, that's fine. But give yourself some credit and think abstractly. Networking stuff always intimidates me, I don't know why. So when I'm reviewing a networking card, my first instinct is WELL I DON'T KNOW HOW NETWORKING HAPPENS SO WHO THE HELL KNOWS WHAT I'D DO. Then, I calm down, and remind myself that I'd make a call to the API or check some stored state for the user's login status...blah blah blah. 

^ The reason you want to do this step is so you have some grounding for evaluating what the other developer ACTUALLY did. Is it wildly different? Mostly in line? Surprising in some way? Confusing? 

--- 

# Step Four: Do you understand what they did? 

^ Does it make sense? Do you understand what the code is doing? On a fundamental level, do you get this? Can you explain it to someone else? Is there some a pattern or some syntax or something about this code that you aren't familiar with or don't understand? This part is important for a couple of reasons. The first is that you are going to be in learning mode for a real long time and that's okay. It's what you are here for, and why you are on a project. If there's stuff that you aren't familiar with or don't entirely grok, pay attention to that and use it as an opportunity to learn. The second is that this is your codebase, too. And you are going to be poking at the new feature or bug fix code that you are reviewing right now at some point. And you need to know what it's doing, and more importantly, you are going to need to know what it's doing three months from now after you've learned 10k new things and slept a few times and went to your friend's birthday party and adopted a kitten...you aren't going to hold this code in your head forever, and part of the reason why it's important to have clear and descriptive names for things and for writing clean and easily comprehended code is so you can come back to it later and be able to figure it out again quickly. Clever code is a bad idea. Complicated ternaries and fancy show-off-y code are a bad idea. They inhibit your ability to understand the code when you come back to it.  

--- 

# Step Five: Ask questions! 
- what is this method doing? 
- how does this pattern work? 
- I've never seen this syntax/construction before, can you explain... 

^ Again, there's a bunch of reasons for this, including the fact that you are learning. And, you might be tempted to do something like note your questions on a sticky note and approving the PR and thinking you will get your questions answered at some other date. DO NOT DO THIS. This is your codebase, and you are the gatekeeper of this PR. Never, ever, approve a PR that you don't understand. Don't do it. Pose the questions right there in the PR, ideally at the site of the code that confuses me, and get them answered. Keep asking until you get an answer you understand. Keep your sticky fingers off that approval button until you feel like you can explain what this PR is doing on your own. 

--- 

# Step Six: Ask more questions! 
- So I thought I'd would have done...
- How did you know to...
- What made you think that...

^ I hope you are picking up on a theme here, not just from this little presentation but from everything I've shared with you so far. Your entire job is basically going to be asking questions. Remember when I said you should think about how you would approach the task? Now is a great time to ask about an approach that is different that what you would have done. Why did they do it that way? Sometimes the answer will be more opportunities to learn--there's an angle you aren't seeing, or a danger they are fending off against, or a complication that they have encountered before. Ask more questions about that. When they explain that "well, in the past, we did it the way you thought, and it led to this problem later", that's a great time to ask, "okay, how does this approach prevent that complication?" and learn something new! And sometimes, the answer to "why didn't you do it this way" is, "Meh, I just like this way better" and, honestly, so long as it follows best practices, that's cool. And sometimes, sometimes, the answer is going to be, "...huh. I didn't think of that. Yeah, that might be a better approach. Lemme go change it." 

--- 

# Scary Truth: You might be right! 

^ And this is another reason to keep questioning. You might feel like you don't know a lot just yet. But you don't know nothing. And you have the advantage of new eyes and a clean perspective, especially when you are just starting on a new project. You just sat here for three months while Erika pounded all kinds of best practices and clean code principals and the Right Way To Do Things into your brains. My four year old niece has entered the Word Police stage of development, where she's very eager to tell me every time I swear that "That is NOT A NICE WORD Aunt Annie" which is fair, because I should be dropping f-bombs around the four year old anyway. I probably shouldn't compare you to a four year old, but the truth is you can provide a good reminder that we should be setting a good example and making sure our code is clean, clear, not too clever, and all those good things. You've been taught the latest and greatest stuff, so you may be aware of new approaches that others on your team haven't had time to start using. 

--- 

# Step Seven: Look at everything
- yes, even the storyboard stuff 
- yes, even the .pbxproj 
- yes, this means open Xcode 

^ So, okay, we didn't talk about the .pbxproj file and I'm not sure it's going to be discussed much here, but it's essentially a collection of the files in the project. So don't skip over it when you see it in a PR. Look and see what's added and what's removed. If files are added, make sure you understand why they were necessary, and if they were removed, make sure you understand the thinking behind that as well. We talked about the storyboard xml last week, and reviewing the changes in that in a PR is one of the ways I got so comfortable reading through that mess. What layout changes happened? Do they all make sense? If an outlet is added, what's it being used for? And definitely make sure you look at every file that has any change. 

^ And context matters. Don't just look at the diff on Github and think that's good enough. Open up Xcode and look at every change in context. Does it make sense that this code is where it is? I think Jen talked about code organization a couple weeks ago--is somebody putting socks in coffee cups? One thing I like to do is click through the life of a method, who calls it? where? when? does that all make sense to me? You don't get that just looking at the green and red lines on github. 

---

# Step Eight: 🍰

^ Last point, and this is kind of a labs-specific thing that one of our devs came up with. I like it, so I'm doing my part to spread it around. If you see a thing on a PR that is super minor, like a renaming suggestion for a variable, or changing an `if let` to a `guard`--the kind of thing that's nice to have but you don't feel like holding up a PR for it, leave a comment to that effect with the cake emoji. It's cake, it's nice but not necessary. Sometimes I'll approve a PR that has a bunch of cake comments on it, or leave a mix of requested changes or questions and some cake comments. It's a good idea and leads, I think, to cleanlier code bases and friendlier PR reviews. You get to call out minor things and the author of the code gets to decide if they are worth the effort. 

---
 
# Another Scary Truth: It's big girl pants time 

^ In a couple of weeks, you all are going to walk out of this room as apprentices for the last time and walk into Labs as professional software developers for the first time. And this is part of the job. We aren't just contributors to a codebase, we are stewards of it as well. It's our collective team responsibility to build for our clients the best project we can. And that means we do things like review and question our code from a bunch of different angles before we ship it out to customers. PRs are a chance to learn and grow, both to sharpen your Swift skills and to build your understanding of the entire project you are working on, but ultimately, they are also and maybe mostly, about making sure no garbage gets into the codebase. Overly complicated and clever code will be harder to understand later, so it will be harder to build off of. Same for code that doesn't work as described. Same for code you approved on faith that you are going to have to work with later. I'm not saying this to scare you--in the end, we make apps that sell sandwiches, not apps that launch missiles or regulate pacemakers.  But this is part of your job, and you don't need to be afraid of it. 










