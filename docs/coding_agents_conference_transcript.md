# Coding Agents: AI Driven Dev Conference - Transcript
# Duration: 6h 45m | Transcribed: 1159 paragraphs

**Speaker 0** [00:06:22]
Alright. Everyone, what is going on? Welcome to the show. How y'all doing? You good?

**Speaker 0** [00:06:32]
You ready to start? Yeah. We're ready. Right? I know we had a lot of fun.

**Speaker 0** [00:06:38]
You know? We didn't pray to the demo gods or the registration gods, apparently, and they did not take pity upon us. So thanks for the patience on getting in. You all got your name tags or some of you got your name tags. If you didn't, feel free to grab it after or when you find a convenient moment.

**Speaker 0** [00:06:57]
Normally, I don't give talks. I just come and I try and entertain and then bring the actual speakers onto the stage. But every once in a while, I do have something to say. So, normally, what I would do is I would go through and I would say, thank you to the sponsors. Huge shout out to all of them, everyone.

**Speaker 0** [00:07:17]
Check them out when you get, yeah, when you get a chance, make sure you go see them all in their booths and you enjoy their talks and maybe even buy some software, that would be awesome. And then I would tell you that there's a lot of great stuff going on. Right? And you've got workshops. Hopefully, if you signed up for the workshops, you know.

**Speaker 0** [00:07:42]
If you did not sign up for the workshop, I can't guarantee that there's space, but you can still try and filter in during one of them. You should have on your chairs all kinds of agendas if you need it, and that would be it. Then I would bring up the next speaker. But today is different. For better or worse, you gotta listen to me for five minutes because I got something to say.

**Speaker 0** [00:08:07]
There was something that hit me, and it is around this. We're going through a bit of a neo moment. Why is that? I think you could all draw the parallel between I know kung fu, and I just give some skills to my coding agent. Right?

**Speaker 0** [00:08:25]
And now it knows kung fu. So that happened. And if you think back and you think like, wait. How did we used to do software engineering? Like, so long ago?

**Speaker 0** [00:08:38]
In the ancient days, we would have to talk to other humans, and we would have to fiddle with broken environments. Right? And we would have to check out some open source code, try and understand it, maybe even read some documentation. And then you all remember this? What?

**Speaker 0** [00:08:55]
This? Wait a minute. I used to live in there. I used to try it was like my badge of honor. Right?

**Speaker 0** [00:09:02]
We used to go in there all the time. But now what do we do? We do this. That is actual footage of Sid, our first speaker, when he's coding. That's what he's doing, orchestrating his agents right there, and he gets pretty intense.

**Speaker 0** [00:09:17]
So we'll ask him about that later. Because as we're orchestrating all of these agents, something inevitable happens, and this is what I really wanna talk to you about today. What happens is is that we get out of our depth kinda quick. So maybe you're an ML engineer, and next thing you know, you're coding React. Or maybe you're a front end engineer, and next thing you know, you're creating a recommender system.

**Speaker 0** [00:09:43]
And so you say, what happened there? Well, whatever the case happened, we have now come to the era of the mythical land of side quests. That is where we are right now. Right? And let me explain the anatomy of a side quest to you in story form because I've heard that humans remember stories much better than they remember just straight facts and data and bullet points.

**Speaker 0** [00:10:13]
Let me introduce our protagonist, John. He's he's there. If he bears a striking resemblance to me, just forget about that because we're in the mythical land of side quests. Right? Just get that out of your head.

**Speaker 0** [00:10:25]
Now John wants to create a simple RSS reader from for, like, newsletters, to summarize newsletters, and he says, okay. He goes to his agent, and then he creates it within an hour. He's got a little Python script, and he ships it, and it's great. But then he realizes, this thing doesn't run when my computer's not on. So he goes down the rabbit hole of virtual machines.

**Speaker 0** [00:10:54]
And then he's like, you know what? Actually, I wanna share this with some friends. So then he starts looking at cloud, and he starts using Kubernetes because, obviously, he's got seven concurrent users. Time for some Kubernetes, boys. So that's what I'm talking about.

**Speaker 0** [00:11:13]
So then he goes, you know what? All these concurrent users, it's kinda getting expensive with these LLM calls. Maybe I should use some open source LLMs, and I should host it on my own cheap GPUs. Yeah. Just kidding.

**Speaker 0** [00:11:34]
There's no such thing as cheap GPUs. We all know that. But let's pretend in this mythical land of side quest there is. So you see my point, though. Right?

**Speaker 0** [00:11:43]
John started with a script, and he ended up accidentally becoming an infrastructure engineer. That is the land of side quests. But this path right here, this problem, frustration, skill acquisition, that's not new. That's something we've been doing for ages. That didn't change.

**Speaker 0** [00:12:04]
What changed is how fast that happens. The speed, what used to take John six months and a whole lot of learning tax, Now takes him a weekend and a max subscription plan. So the trough of disillusionment, it's littered with bodies, but we are less likely now to get stuck in it. And that's not just because we're asking agents to do everything and then we go and have Mai Tais on the beach. Right?

**Speaker 0** [00:12:36]
That's because we now have a new form of interacting. We now can, before diving into Kubernetes, say, what are the key things that I need to know as someone who doesn't understand Kubernetes so that when I do dive into a new technology, I'm able to get to the tip of the spear much quicker. And then after I go through and I have a session with my agent, we can have it summarize the biggest pieces, the biggest key learnings so that we can interrogate that too, and we can better understand what's happening. We can relentlessly, relentlessly interrogate agents about our code base, about design decisions, and they do not tire, and that is beautiful. So we get through this trough so quickly.

**Speaker 0** [00:13:28]
And now something beautiful is happening because we're starting to experiment, and we're starting to get a little bit out of our depth, but we're all becoming our own little mini r and d departments. So when we talk to our friends, that's what we look like. Right? In the last two weeks, how many of you let's just get interactive real fast. How many of you have gone on a side quest like John?

**Speaker 0** [00:13:57]
Everybody. Right? We've all done that. So how many have learned something new with agents, or you've tried something new while coding that you wouldn't have tried? Yeah.

**Speaker 0** [00:14:08]
These are rhetorical questions now. You can keep your hands down. It's we know. Right? So my point is that everyone in the room is exploring.

**Speaker 0** [00:14:19]
You're learning. You're pushing the limits. And that's why I wanted to organize this event today because we're all seeing things in different ways, and I implore you to go hang out, talk with people. The best parts about these days are that all of us in here is our little mini r and d departments, and so we get to share what we've learned with others. That's why you probably saw an email from me trying to introduce you to somebody.

**Speaker 0** [00:14:48]
I wanna make sure that everybody has a friend or a buddy by the time that they get here, and you get to exchange what's been working for you, what's not been working. Right? Because now you are learning new tricks, and I just want to say, enjoy the side quest. That is my spiel for the first five minutes, and that's enough of me. I'm gonna bring on our first speaker, Sid, who created a tool that can take a one x engineer and make them a 10 x engineer.

**Speaker 0** [00:15:23]
And as we all saw yesterday, he can take a 10 x engineer and then downgrade them to a one x engineer. Claude, code, please work. Please work today. The productivity of the world depends on it. Please.

**Speaker 0** [00:15:40]
Alright. So let's get a big round of applause for Sid from Anthropic. Get up here, man. Alright. So I've got all kinds of questions for you.

**Speaker 0** [00:15:55]
I know that my friend, Jeanette, told me he told me, hey. Make sure that it is actually, wait. Can we set the mood real fast? AV team, you all can can you throw up? There we go.

**Speaker 0** [00:16:09]
That's what I like. Thank you. So if you thought this was gonna be, like, professional in any way, think again. I think hopefully, you all are feeling the vibe. My friend, Jeanette, told me, he said, oh, so it's like a high level fireside chat.

**Speaker 0** [00:16:26]
I said, no. We're going deep. Sid is not about to stay high level with me. If at any point you want more from what Sid just just said, just say go deeper. And this is a bit of a social experiment, so if it turns out to be a shit show, sorry.

**Speaker 0** [00:16:45]
However, we're gonna pass around a mic later on too so that you all have the chance to ask Sid any questions that you may. Alright. Let's start with this, being ambitious with AI these days. How much can one person actually do, and where are the boundaries?

**Speaker 1** [00:17:01]
Yeah. Sure. First of all, thanks for having me. This is a this has been blast. But I think that that's a very interesting question because how much can one person really do changes every two months with a new model release.

**Speaker 1** [00:17:13]
So I think you have to constantly recalibrate how much can you really do, and it's quite tough because, like, by the time you're really used to exploring the boundaries and edges of one one model, the next model's already here. So I think most people constantly underestimate, like, how much they can really do.

**Speaker 2** [00:17:29]
Yeah.

**Speaker 1** [00:17:31]
For me, personally, I've been constantly surprised by how much I can do. I think I can safely say, like, looking back at my career and the projects that I've done, those projects, usually about four to five people took, like, three months each. Everything included, like, infrastructure, back end, front end. I think those projects can now be, like, one person projects for a few weeks. So it's it's it's really, like, my the thing I say to everyone is is, like, be more ambitious with what you can do.

**Speaker 1** [00:18:02]
If you if you think you you need another person to come join you or if you need an expert, you know, infra expert, as you said, to to run your Kubernetes cluster for six concurrent users, you you can do it yourself. Yeah.

**Speaker 0** [00:18:15]
So what can we not do right now? Where should we be thinking about, like, not trying to push the boundary?

**Speaker 1** [00:18:22]
I I think you can do everything. The only thing that that it falls apart is really reliability. Right? So I think in my in my view, today's systems, today's models where they are today, they can pretty much do anything that you can you set them to. The only problem is with some tasks that are more complex, the reliability is not there.

**Speaker 1** [00:18:46]
So you may have to steer the model. You may have to point it towards resources, or you may have to tell it to read a doc or, like, fetch something from from your, like, from your doc server, but it can do it. Right? So I think the thing the the way to think about this is, like, how reliably can an agent do task x, and that differs from task to task. Yeah.

**Speaker 0** [00:19:12]
So verification has always been interesting one and being able to know without me as a human going and clicking through does this stuff work that I just told it to do. Have you found any tricks there?

**Speaker 1** [00:19:28]
I think optimizing your stack for verification is really helpful. Like How do we do that? Like, one example that comes to mind is, like, a lot of companies use remote dev environments, and I think Anthropic has also started to use some of these. And when we first started using them, what became really tricky was verification using using browser agents. Right?

**Speaker 1** [00:19:49]
So Cloud Code has a slash Chrome plugin where it can, like, open up your Chrome or you can use Playwright or whatever other other MCP server to to to use that. But as soon as you use a remote dev environment, like, that breaks. Right? Because you now you don't have a a Chrome instance running on your on your on your dev instance on your dev server. So the first thing we did was we changed that so that there's, like, a a proxy that proxies to your local laptop, opens up Chrome there, and it gives Cloud Code access to that Chrome.

**Speaker 1** [00:20:17]
So it's I mean, that's for, like that's a simple thing for, like, UI stuff. But the other thing that's really helpful is giving Cloud access to your log server, so Datadog or GCP logging or or things like that. Like, anything that you can see as a as a engineer and you can use to verify whether something's working, Cloud can do that too if you can use if you can give it the the tools to to access those things.

**Speaker 0** [00:20:42]
Now working on teams, I know there's a lot of folks that have come with a team or are here and are trying to figure out the most optimal way of having the right amount of I I know governance is kind of a boring word, but when do I make a skill ready for the whole team? When is it just for me? When do I use a rule? When am I trying to say, hey. This is how we optimize prompts.

**Speaker 0** [00:21:11]
Like, how have you and your team been able to really figure out the best ways to disseminate the knowledge across the team?

**Speaker 1** [00:21:23]
Yeah. This is something that comes up a lot, and I think the answer to this is really let everyone do whatever they want and go as fast as they want. And quite quite quickly, patterns will will emerge for, like, what what skills are being used, what plug ins are being used, what is resonating, and what's not. And, you know, this this is it is an exploratory journey. You know, as the models are getting better, maybe you have to simplify your skills now.

**Speaker 1** [00:21:52]
Right? Because, you know, the models can infer things from your code base, and you don't have to explicitly tell them. So this is going to be constantly changing. It's not like you have one set of skills that you're using now, and your team can use that for the next year. Like, your team can probably use that for the next few months.

**Speaker 1** [00:22:07]
So one thing that's worked really well for for companies that that we work with is just having some sort of, like, a plug in marketplace and then just tracking the number of users or downloads for each plug in and how often they're being used. And that's, like, a pretty clear signal on, like, what's working and what's not working. Team governance in general, though, is is an interesting topic.

**Speaker 0** [00:22:33]
Before we go down that route

**Speaker 3** [00:22:34]
Yeah.

**Speaker 0** [00:22:35]
More on that skills.

**Speaker 1** [00:22:36]
Yeah.

**Speaker 0** [00:22:37]
Is it all skills? Is that the main thing that you're doing? You're not doing any kind of, like because there's a lot of knobs you can fiddle with. Right? But skills tend to get you the most bang for your buck?

**Speaker 1** [00:22:49]
It's a combination of skills and MCP servers and then kind of, like, you know, memory systems that people create for themselves. And I think skills are interesting because, essentially, they're just like context blobs. Right? They're just like bags of context. You can dump anything inside them.

**Speaker 1** [00:23:08]
They're like a more generalizable version of CloudMD or agent MD files in some ways. Right? So it's like they and more and more, we're seeing that the the all the models need are, like, access to the right tools, which is MCP servers, and instructions for how to use those tools and where to find information that it it's not that that is not easy to infer. And both of those things can be accomplished with skills in MCP servers. So, yeah, I I think a lot of the a lot of the, like, the, you know, the cool, like, harnesses and the complicated harnesses that people are building can just boil down to these two things.

**Speaker 0** [00:23:43]
Any harnesses you have seen that have been very interesting and you wanna shout out right now since you mentioned it? I know I put you on the spot. I didn't preempt you with that question. No. It's all good.

**Speaker 0** [00:23:55]
No.

**Speaker 1** [00:23:56]
I think well, I I haven't experimented with a lot of, like, open source ones recently, but one concept that really appeals to me is kind of having this cause of, like, adversarial agents. So, essentially, the the idea is that you you tell one agent to do something, and then you tell another agent to critique it. And this can you can kinda go as far as you want with this. So you can even once you've built something, you tell one agent to review it, and then you tell the other agent to critique the review. And so it's I I think this goes pretty far, and I think harnesses that are kinda doing this are are quite effective.

**Speaker 1** [00:24:33]
The thing is you don't need a harness for this again. You can just have a skill. And as the models get better, you know, it kind of takes away the the custom boilerplate code you're building Yeah. For for the harnesses.

**Speaker 0** [00:24:46]
You bring up a great point, which is running agents in parallel. And I try so hard, But by the time one agent is done or one agent is up and running, and then I get the second one up, and then the third one, the first one's already it's, like, done already. And so I've been having the hardest time really figuring out where to leverage that. How are you doing it? Because that is one of the things where you see your boy Boris is like, run more in parallel.

**Speaker 0** [00:25:15]
And I'm like, I'm trying here. I can't figure it out. How have you been doing it? And what do you got for us?

**Speaker 1** [00:25:23]
I guess having ADHD is a good thing. Right? Like, that that probably helps the most, but it's it's hard. It's really hard. Keeping track of all the different streams of work that you're doing is is really hard.

**Speaker 1** [00:25:37]
Personally, I I try to make it a little bit easier on myself. Like, I have a system for my work trees, and then I have a system for, like, my remote sessions. And the way I do it is, like, my I have five predefined work trees in my local laptop, and I have some, like, magic Apple scripts. It's kind of it's kind of silly, but I have some magic Apple scripts where, like, I can I use Alfred, which is, like, the the search the search thing? Mhmm.

**Speaker 1** [00:26:05]
And I have a few commands where I'll say, like, work tree one, and it opens up a new iTerm window with three tabs. It creates a new branch for me, you know, gets on the gets gets cloud code set up there. And then as I'm working, it also goes and changes the the tab the window name and the tab name for the tab that I'm working on. So if I have five work trees, I basically have five item windows, each on their own branch, which is named appropriately, and each with a window title that is named appropriately. And so it's a little bit easier for me to keep track of what's where, but it's still hard.

**Speaker 1** [00:26:42]
I mean, it's you know, it's kind of, like, constantly, like, shifting between between terminals between Windows. And the other thing that's that kinda makes us even more complex is is, like, remote sessions. So, like, I've started using Cloud Code on the web a lot more. So and and I use it from my phone. So, like, any anytime I have an idea or if I'm, like, talking to you and then this conversation and I think of something, I'll just, like, go back and just, like, be like, hey.

**Speaker 1** [00:27:07]
Like, bill me this. And it's it doesn't one shot everything, but it's it's a great it's a great way to just, like, increase agency by just telling your agents to do something and that you can come back to it and review that code and it just spurred if nothing else, it just spurns more ideas. Mhmm. So at any point in time, I have about, like, five to 10, like, plot code on the web like, web sessions running, doing random things, random ideas that I've had through the day, and then I have about five work trees on my local laptop. So that's that's kind of what my session my setup looks like, but it it's hard.

**Speaker 1** [00:27:45]
Like, I struggle with just too many things happening at the same time too, so some organization there is useful.

**Speaker 0** [00:27:52]
I'll ask the audience. Has anyone felt like they fully have gotten the parallel agents down yet? Anybody with their hand? I oh, I like it. Alright.

**Speaker 0** [00:28:03]
Later, we'll chat. Maybe we can do a podcast. That's perfect. So okay. I cut you off when it comes to the governance piece.

**Speaker 0** [00:28:12]
Right? Tell me more.

**Speaker 1** [00:28:15]
Yeah. Governance is so I think what we're seeing now is, like, with with agents and with Cloud Code, like, the number of PRs that someone like, that the average person on the team, submits and merges is kind of going up exponentially. And a lot of things kind of happen when when, you know, when something like this, kind of sudden shift takes place in a small compressed amount of time. And the most unexpected thing that happens is, like, CI fails. I don't I don't know if people over here have experienced this, but, like, if you have just that many more PRs kind of going into your system, your CI systems are overloaded.

**Speaker 1** [00:28:54]
So you have to kind of, like, scale those out. I don't know if I think GitHub has has been having a bunch of outages recently too, so, like, GitHub has been failing. And I think they put out a stat that, like, on average, they're getting seeing, like, 40% more PRs a day or something like that, which is crazy. So the other thing that happens is, like, as people can do more, like, it's more important that your product has a a vision that you're building towards. Because if everyone's printing, you wanna make sure everyone's printing in the right direction.

**Speaker 1** [00:29:25]
Reviews become an interesting part of the cycle. Like, how do you keep up with the volume of reviews coming into your system? You know, how do you make sure that everyone on the team is aligned for how what is the future direction of the product? So I think we're still grappling with all of these things. The number of, like, bugs that your system has also increases just because, as I think, at some level, the base failure rate per PR remains about constant.

**Speaker 1** [00:29:54]
So if you just have, like, you know, five x more PRs going into your system and your failure rate is about the same, you can expect a lot more bugs and a lot more, like, incidents kind of that that start to happen. So there's a lot of things to to still figure out, and we're still in the process of figuring it out right now. But I think, like, you my personal perspective and and our team is quite divided on this, be honest. So my personal perspective is that you kinda have to offload more to Claude. So we rely really heavily on Claude reviewing our code in our, like in on GitHub.

**Speaker 1** [00:30:31]
Right? So every time we submit a PR, there's, like, a custom kind of harness with using Claude code that reviews the PR three different ways. It has, like, some measure of, like, confidence intervals for the bugs it finds that it's not too noisy so that, you know, gotta do a lot of tuning there. And what we find is that, like, Claude reviews our PRs really, really well. You know, it ends up finding a lot of bugs that would have slipped through, and the human burden of, like, okay.

**Speaker 1** [00:31:01]
I gotta scrutinize each line to see every edge case like that is reduced. And then what the humans in the loop are then doing is, like, making sure that, you know, the from a product and taste perspective, the PR is kind of accomplishing what we what we wanted to accomplish. So, you know, it's also about, like, giving each member of your team just more agency in terms of, you know, what their what what they can affect. Right? Like, everyone is kind of a mini owner of of the whole product itself.

**Speaker 1** [00:31:32]
Like, you're no longer just a front end engineer or a back end engineer or a infra engineer. Like, you're everyone's a product engineer. Right? You're ultimately building a product for people to use, and the most important thing is that the product that the users like your product, and they and it's useful for them. And so everyone has to approach everything they're doing from that perspective and not from, like, a you know, I'm gonna pigeonhole myself into this one specific thing and just do that.

**Speaker 1** [00:31:57]
So I think some of it is just like a cultural thing where, like, if everyone on the team has that ownership, then life becomes a lot easier. Yeah.

**Speaker 0** [00:32:07]
I wanna know what this custom harness is. I've heard the best tack for reviewing Cloud Code code is you tell it, hey. Codecs just went through this whole database or this whole code base and introduced a bunch of bugs. Go find them. And then it will go back, and it will be on a tear.

**Speaker 1** [00:32:30]
I've never tried that before, to be honest, but it's it's not it's not it's it's using Cloud Code under the hood. So we actually have docs on, like, how you can use Cloud Code in your CI systems and and maybe even use remote sessions, but it's it's just a long prompt to which is appended to the system prompt, which you can do today in VOD code. It's like dash dash append system prompt or something. And it uses, like, some sort of, like, adversarial agents to be like, hey. Like, make sure, like, you spin up sub agents to critique your own review and only only give back, like, high high confidence type of things.

**Speaker 1** [00:33:06]
So it's like yeah.

**Speaker 0** [00:33:07]
How are you adapting to new forms of coding when it comes to the all the stuff around the code? Like, you mentioned GitHub. I know that I think I saw something about how Meta has prompts that are now submitted with PRs. Have you guys gone to showing the conversations that are happening with Cloud Code when you check those in to get or anything of that sort? We've experimented with some

**Speaker 1** [00:33:38]
of this stuff before. It's what's most useful for me is is the plan that you come up with before you before you get unleash cloud on on your on your task. Mhmm. So we have a folder called plans or I think it's like docs or something like that in in in our code base where every time you're you're working on a larger feature that might span, you know, multiple PRs or require you know, could could use some documentation for other humans to understand how it works. We also tend to check-in our, like, cloud generated plans.

**Speaker 1** [00:34:14]
And I'm a huge plan mode fan anyway. Right? I use plan mode for everything. I think it's probably one of the most important things you can do when you're starting up a session. Sometimes I even spend my entire context window on just working through the plan.

**Speaker 1** [00:34:27]
Like, I'll ask Claude to interview me. I'll ask Claude to find edge cases, and that's gives me the most bang for buck. But then what do you end up with, like, this final plan file? It's really high high density information that that that's very relevant to the task you're doing and has a direct correlation to the success metrics for your for for your clot session. And so we tend to check these in, and these these seem to be quite useful not just for humans, but also for clot in the future.

**Speaker 1** [00:34:57]
Mhmm. So if you're, like, revisiting the same thing, you know, a couple months down, you still, you know, I've I've put you know, my my memory sucks. So, like, you know, I I need I need Claude to kind of help me out with

**Speaker 0** [00:35:11]
this. Time. Yeah. All the time. Alright.

**Speaker 0** [00:35:12]
I wanna open it up to the audience. We've got a few minutes. Anybody got any questions for Sid? We've got one right here. You're close, so I'm gonna give you my microphone.

**Speaker 0** [00:35:23]
Alright. Yeah.

**Speaker 2** [00:35:24]
Thanks. Hi. I was just wondering, you know, with all the different, points that you can, like, put in hooks or scripts or automation to prevent, you know, like, your test from failing or your builds from failing or your linting. And and as the agents iterate and especially if you're, like, having multiple passes or, you know, working in parallel and stuff, like, have you found, like, a consistent pattern to apply across code bases for, like, when to actually either apply that or to prevent it from like, I've just seen cases where it doesn't, you know, depending on the way it makes the the edit to the code, it doesn't apply the linting right away. Or if it does, it I don't know.

**Speaker 2** [00:36:05]
It just causes a lot of friction, and it it works ultimately the way I have it set up. But I you know, I'm just wondering if there's a more frictionless kind of pattern that you're following.

**Speaker 1** [00:36:16]
I think especially with linting and, like, and testing, these things are so code based dependent and, like, framework dependent that ultimately, it's not a one size fits all solution. Like like, for like, we have multiple different repos, and they all have like, one's a TypeScript repo, the other is, like, primarily Python and Go. And the hooks that we have there are are are different. They they do tend to like, you probably already have the existing infra for this. It's just about, like, setting up those hooks to to to to to hit into your existing infra.

**Speaker 2** [00:36:54]
I was just wondering at what point you put in the like, at which places you do abstract it. Like because you could abstract this technically in multiple different places, you know, even within the hooks. That would step in the hook pipeline, you know, the different hook events or pre commit, post commit, or tons of other events that can happen throughout the pipeline with the files being edited, closed. It could be linked in automatically separate or, you know, things like that. So I was just wondering, you know but hooks are the primarily the abstraction point that you're still, like, using for most of this.

**Speaker 2** [00:37:26]
Oh, sorry. Are are hooks the primary method that you're using for automation?

**Speaker 1** [00:37:32]
Yeah. Hooks are quite effective for for that type of thing. My sense is

**Speaker 2** [00:37:36]
Pre commit, post commit, and other methods of injection or events that happen during

**Speaker 0** [00:37:40]
Yes.

**Speaker 1** [00:37:40]
Life cycle. We also there's also, like, LSP plug plug ins, for for Cloud Code, and, like, those can those I think work on, file edit hooks. So every time Claude edits a file, the LSP runs, and it gives it immediate feedback.

**Speaker 2** [00:37:55]
Well, there's just so many ways to do this. So I was just wondering if if you guys have, you know, kind of fallen into your favorite ways or things that you found that you didn't like.

**Speaker 1** [00:38:04]
I think for me, personally, I like the pre commit hooks because I find that sometimes if it's if it's per edit or, like, it's a file edit hook, you can confuse Claude by giving it too much information while it's in in its, like, you know, in its zone and and building things. But the reason why we have hooks in in some ways is because we we understand that, like, every project is different Mhmm. And everyone's requirements are different. So you can kind of hook in according to your your projects' current requirements.

**Speaker 2** [00:38:32]
Thank you.

**Speaker 0** [00:38:34]
Hey, Sid.

**Speaker 4** [00:38:36]
Sid. Every tool that gets created to solve a problem obviously creates new sets of problems. And the intent behind this question is as a production engineering manager, my job is to sort of anticipate these problems and, you know, get ahead of it. And we have talked about the most obvious ones, how to run this at scale, how to run agents as teams, what have you. But what are the nonobvious problems you think you know, I'm asking you to read the crystal ball here.

**Speaker 4** [00:39:02]
But what are the non obvious problems that you think that most people don't know about, and what problems do you envision these tools being created that we need to start looking at?

**Speaker 1** [00:39:12]
Yeah. It's a good one. I think CI was a non obvious problem that, at least for me, I I didn't I didn't out of all everything that could break, I I didn't think that CI would start breaking, just because of how many new PRs are going in. I think more generally speaking, though, I think the kinds of problems that emerge now are more about, like, product and vision problems rather than, like, coding problems. Like, I think coding and the actual execution of your tasks is is is getting abstracted away quite quickly.

**Speaker 1** [00:39:41]
And then kinda what happens next is, like, okay. If you can build anything and the cost of building something is close to zero or trending towards zero, what matters now is, like, what you choose to build. And and and I think that's kinda where the problem is going to be. You're gonna switch the problem from, like, how fast can I build this and how to build this to what should I build? But yeah.

**Speaker 3** [00:40:06]
Thank you.

**Speaker 5** [00:40:08]
Sid, I was curious about your take on context window capacity. Sorry. You mentioned, you know, sometimes you use up the whole context window in a plan mode. And I think most of us who have experimented are aware of, like, the dumb zone where the agent starts to tip over and give you bad outputs. I was curious as we're moving towards larger models that have, the million token window, do you feel like there's still a point which you should kind of avoid?

**Speaker 5** [00:40:35]
Is it still 60%, which I kinda understand is the the given best practice today? Or, you know, what's your thoughts on that?

**Speaker 1** [00:40:43]
Yeah. I think, like, as the models get better, they also get better at utilizing their context window more efficiently. So if I look back at, like, I don't know, Sonnet three five or something, like, it definitely was there was a very clear mark around, like, the 100 k, 110 k token window where it was like, it's falling off the cliff. Let's, like, do something else. I think the models are progressively getting better at that, so and I'm hoping that they continue to do so.

**Speaker 1** [00:41:10]
My personal experience with OPUS four six has been that it it's a it's like a vibe thing. Like, sometimes it's in the zone and it's building things, and it's, like, going down the right it's it's it's chosen the the right way to solve a problem. Now just, like, let it fly, and it, like, auto compacts and does its thing. Sometimes I I find that I have to fight with it a little bit. You know?

**Speaker 1** [00:41:32]
Like, I'm steering it. I'm, you know, going back and forth. I'm still ideating. I I, myself, don't really know how I wanna build this. And in those cases, I still do find that sometimes it kinda gets confused later.

**Speaker 1** [00:41:44]
And and I think that's when, like, having a plan file is really, really helpful because this plan file can kind of have keep your most important state, and then you can just clear the context and start again from the same file. So it's it's a it's I don't have a hard and fast rule around, oh, 7070%, like, you know, clear it. It just depends on on the use case, and it's it's it's kinda vibe based.

**Speaker 6** [00:42:07]
Last one. Yeah. Hi. Yeah. I was curious.

**Speaker 6** [00:42:11]
You you mentioned using agents for code review, and, like, we're doing that, obviously. But, like, there's trust issues with, like, do you trust the code review? And so I'm curious. That's a real bottleneck. Like, what do you view today the role of humans for code review, and where do you see that going?

**Speaker 1** [00:42:31]
Yeah. Some of this is prompt tuning. Right? Like, what we've we've been through many, many iterations of our, like, code review agents as as I'm sure, like, a lot of you have too. And improving the prompt and, like, improving maybe the harness for the for the code reviews has material impact on the quality of the code reviews.

**Speaker 1** [00:42:56]
When we started off, we were we were seeing that like, we would get three, four, five comments on every PR, and and people would just lose trust on those comments. It was too much signal too much noise, not enough signal. Right? And as soon as you for any product, like, as soon as you have that, like, you lose trust immediately. So the number one thing that we we focused on was, like, how do we reduce these, like, five to 10 comments into just, like, two comments.

**Speaker 1** [00:43:22]
Right? Like, let let's say we we we only focus on the high priority ones. Even if we have high certainty but low priority, we, like, let it go. So some of it is just, like, prompt tuning and also the model's getting better. I think, like, Opus four six is much, much better at at code reviews than, Sonnet three five was, and I I I presume this is gonna continue to to be the case.

**Speaker 6** [00:43:44]
But do you do you have other humans reviewing like, the the human who wrote the code and generated the PR, do you have a different human that's reviewing those comments, and are they doing a thorough job? Like, what's the responsibility there, and and how do you see that trend?

**Speaker 1** [00:43:59]
Yeah. I think, like, for for the Cloud Code team, everyone's really good about taking ownership of the code that they're writing. So, effectively, if my wrote something that broke production, it's it's my Claude's job to go and fix it later. Right? So, like, it's it it but that wasn't just and it really, though, like, it's it's if you're submitting something, I I think okay.

**Speaker 1** [00:44:26]
Let me rephrase this. I think the bars for approving PRs has gone down in my opinion. Right? Like, people are people are more willing to accept things than not, especially if it's been reviewed by Claude, and they've, like, unleashed their Claude on it. However, the buck stops with the person who wrote the code.

**Speaker 1** [00:44:44]
So I think you need like, the person who's writing the code needs to be more responsible for, like let let's assume that you had no PR reviews and you had no branch protections in your code base. Right? Anyone could just push domain whenever they wanted to. And that's actually how the Cloud CodeRipo was for, like, the first, like, two or three months when we were building. Like, we we were just, like, YOLO ing changes in it.

**Speaker 1** [00:45:03]
And our velocity was incredible. We would break things, but then we would fix them immediately after. And something that, like, Adam, one of Adam Wolf, who's on our team, he he says is quick remediation is much better than proactive proactively trying to catch bugs. Like, you will have bugs no matter what happens. A 100%.

**Speaker 1** [00:45:23]
Or, like, there is nothing you can do in this world that would, like, prevent any single bug from getting in. But what's most important is, like, how are you quick to to to to rectify it and fix it going forward? And so I think that's some of the kind of a thing that we've kind taken as well.

**Speaker 0** [00:45:38]
Amazing. Sid, give it up for Sid. Thank you. Thank you, Jason. Yeah.

**Speaker 0** [00:45:48]
Hey. He's there. You give a big round of applause for Scott. Yes. There you go.

**Speaker 0** [00:46:02]
Come on up, man. Cool. We got the pointer here, and it is all yours.

**Speaker 3** [00:46:06]
I thought you were gonna make me grab one of the chairs too,

**Speaker 2** [00:46:08]
so I

**Speaker 3** [00:46:08]
was I was preparing. You never know. Cool. Thanks, Demetrius. See you.

**Speaker 3** [00:46:14]
Hi, folks. I'm Scott. I'm cofounder and CEO at Kilo. We are the all in one agentic engineering platform. There's a lot of slides.

**Speaker 3** [00:46:23]
So I'm here to tell you about all the lessons we learned. So, Kilo, we we started this company in March, so this time last year. We launched in May. And since then, we've processed over, I think the agenda originally said 20,000,000,000,000 tokens. But since we submitted this talk a month ago, we are now at 25,000,000,000,000 tokens.

**Speaker 3** [00:46:44]
And so our goal is just to kinda share some of the learnings, some of the bruises, some of the bumps we've had along the way. We probably learned maybe 25,000,000,000,000 lessons, but I will keep it to a handful because I know we only have, like, twenty minutes. But really excited to share what we've learned. I've got some time for questions at the end. Feel free to save them up, and then we can dig in.

**Speaker 3** [00:47:04]
So before we dig into the lessons, I really wanna talk about the transformation that we're seeing within the entire industry, and this is this is pretty personal for Kilo because this is the journey I've seen in the Kilo team. What's changing is the the dev team is evolving. If you looked at what a team was capable of maybe a year ago, this time in March, they were shipping one feature every two to three weeks and kilo included. Where we are today, it's orders of magnitude different. We are shipping one to two features a week.

**Speaker 3** [00:47:41]
And what's changing is not, you know, we didn't quadruple the team. We didn't change the deadlines. We're not nine nine sixing. What we're doing is we stop working like it's 2023, and we start working like it's 2027. And that's just that kind of fundamental shift that I'm gonna unpack a little bit on the next slide.

**Speaker 3** [00:48:02]
What's what's really changing, and, again, we've seen this firsthand at Kilo, is the role of the developers completely changing. You know, there's some people that are already doing this, and there are gonna be some people that are gonna take another five, ten five to ten years to get there, but this is what high performing teams are doing right now. The old paradigm, developer is code monkey. You are writing every line of code. You're doing templates.

**Speaker 3** [00:48:26]
You're doing boilerplate. You're collaborating. There's an alignment meeting, and there's a review meeting, and then there's, like, a dock that, you know, with the product requirements that sits open for two weeks that someone everybody has to, like, touch before you even start coding. And then you're always just kinda waiting on someone or context switching. Like, I'm doing a task.

**Speaker 3** [00:48:47]
I'm sending it, you know, for an input, and then I gotta switch to another task. What's happening instead is that the developer is becoming the orchestrator. They're managing AI agents. They're guiding the vision. They're doing the things that humans are are really, really good at.

**Speaker 3** [00:49:06]
And then what we're also doing at Kilo, and take this please take this the right way. It's like, we try to avoid collaboration at all costs. We are very anti collaboration. Big, you know, shout out to the post hoc team. They have a great blog post on kind of the downside of collaboration.

**Speaker 3** [00:49:22]
Yes. Our our engineers do talk to other engineers, but we make sure it's not the default. We you only are supposed to kind of collaborate with someone if you really need to, and it adds value. Because I think a lot of times, a lot of this collaboration is kind of like almost like a, I don't know, like a safety blanket that that people do just to feel comfortable. And when you strip it away, it's like, you really don't need it.

**Speaker 3** [00:49:44]
And then so you've got these, you know and I guess the other thing is just because we're not collaborating, we're doing end to end ownership. So at Kilo, every engineer owns a feature. It is not a team that owns a feature. There's only one engineer per feature. Suresh, for example, owns code reviews from end to end, from conception to coding, to deploying, to actually working directly with the end users to get feedback and to iterate.

**Speaker 3** [00:50:06]
And so we're we're we're kind of avoiding those velocity killers, and we're instead leaning into these velocity multipliers. And and what we found is, like, in the age of AI, is coding is the easy part, and the bottleneck is no longer the coding. It's kind of all the process. And so those are some of the biggest gains we've seen a kilo, what's really kind of unlocked our speed. And, you know, we have a saying a kilo, which is the proof is in production.

**Speaker 3** [00:50:29]
I encourage you all to take a look at, like, our product release notes every Friday. We ship and we ship fast, and I think we only had, like, 15 engineers at the time and just kinda that's kinda showing you you what's what's possible when when you've kind of gone all in on AI and and minimize the velocity killers. But I think what's important to remember is that everybody in this room, I think, is very bought into everything I said. Like, I'm sure you were nodding like, uh-huh. Uh-huh.

**Speaker 3** [00:50:57]
Uh-huh. We do that. We do that. We'd like to do that. But not everybody is.

**Speaker 3** [00:51:02]
Over kind of half of engine around half of devs don't even use AI every day. Three quarters aren't using it to do kind of monitoring and deployment. And, you know, at Kilo, we've seen some of the biggest gains and, honestly, some of the most boring things have been automated away in terms of monitoring and deployment. And yet 75% of people three quarters are not doing that. And then you've got the kind of 16% that I call, like, you know, putting their head in the sand.

**Speaker 3** [00:51:30]
That's that's real. Like, outside of the bay, outside of this room, there's a lot of people in the world that are still kind of getting up that learning curve. And, you know, I'm gonna talk to you about how we've, at Kilo, have ourselves got up that learning curve and how we've seen our end users get up that learning curve. And we speak from experience. We've had 25 plus trillion tokens processed since we launched in May and over 1,500,000 developers.

**Speaker 3** [00:51:58]
And so what we've done is we've kinda combined some anecdotes from talking to users and actually the the data we mined to to pull some lessons on kind of what mistakes we made and maybe you can avoid making. I think the first thing is that developers don't just like jump into AI. They're not like, you know, the matrix. It's not like I know Gung Fu right away. You plug in.

**Speaker 3** [00:52:20]
It's a journey. You have to climb, and you have to earn it. And so I kind of think of it as like auto complete is that like a gateway drug. You know, you're in control. You're tabbing.

**Speaker 3** [00:52:30]
You don't even think of it as, like, AI. It's just, you know, autocomplete. And, again, you don't have to think about it. Then you start to chat. You're you're still in control.

**Speaker 3** [00:52:40]
You're asking questions. You're you're kinda giving it the right context. And, you know, and then you've got, like, single agent. You're delegating, you know, one task, and you're kinda watching it. And, like, honestly, that's where we were probably August, September is is single agent.

**Speaker 3** [00:52:55]
I kinda think of that as you know, when you were kind of getting your driver's lesson when, like, you're in a car, but there's, like, you're in the driver's seat, but there's also, like, the instructor has their own steering wheel. That's like you give AI the steering wheel, but you're also have a secret steering wheel and a secret brake that you can stop at any time. And then the last step is is orchestration where you're kinda going deep. You are actually your role has changed to being very hands off in letting the agents run. And at that point, it's like, AI's got the wheel.

**Speaker 3** [00:53:24]
You better pray. And in order to get up that that kind of ladder, you have to give more and more trust. And we saw that even at Kilo when when a developer you know, we will often have developers join Kilo, and they'll come from a traditional company that's operating in 2023. And we'll see that journey as you know, usually takes a week, but, you know, at first, they're kind of very much in control. And then they start to see the people around them moving faster and faster and kind of see what's capable, then and they earn the trust and they get up to orchestration.

**Speaker 3** [00:53:54]
And so now at Kilo, at any given time, our developers are using two, three, four parallel agents breaking up what their tasks are and and kind of their role is is essentially orchestrator of agents. I think on that ladder, what we've really learned from kind of looking at user data from our experiences that, like, at any point, the the the trust can can be broken, and you can just fall down the ladder. You know, for example, if you get in a few set of slow suggestions in a row, I'm turning off auto complete. And, you know, we even noticed that when our latency peaked at two hundred milliseconds, usage went down. And, I mean, I think that's what we've been obsessively focused on is monitoring how how usage is kind of trending and assessing about how to make it faster and faster because latency is real.

**Speaker 3** [00:54:45]
If you're typing and it's like suggest something that you've already moved on or it's not relevant, again, trust is lost. If your agent is editing in the wrong file path, you're just like, woah. This is scary. I'm not gonna do it. And then if you have an and, you know, everybody's like, yeah, you just tell AI and it just does stuff.

**Speaker 3** [00:55:06]
And then every thirty thirty seconds, it's like, hey. Can I have permission or can you review that? Or maybe it's just coming up with terrible suggestions, and therefore you feel like you have to review it, and you you end up actually moving slower because you're using AI. Again, that's an opportunity where, like, trust is lost. And so what we found is really important at Kilo for the kind of engineering experience is, like, we need to be very careful about these moments where trust can be created or it can be lost.

**Speaker 3** [00:55:32]
And and we we we consistently see AI, you know, adoption breaking at the same three points. It's it's context. It's just making sure that AI, you know, the your agentic engineering tool knows what it's talking about, has the right information. And, you know, we were chatting about context in the in the in the last talk, and, I mean, just context is so important. And, again, you gotta get it right.

**Speaker 3** [00:55:55]
The next is having the right model for the job. We're big believers that you need the right model for the right task, and you need a tool that helps you, you know again, there's some people that want to know all the dials and and kinda select which model. I think most of us just want it to be done and it to find the right model for us. And then the last bit is, you know, AI is changing so fast in AI tooling. You want a tool that just gets better every day that, like, you know, there's you know, AI is moving fast, and so your tool might have a sharp edge, but your the expectation is that sharp edge is gone later that day, the next day, or the next day.

**Speaker 3** [00:56:30]
And so you want we've we've been really focused that whenever we kinda get feedback, we're learning from it, and we're like, the auto complete, we're making it faster and faster every single time. And so what's what's kind of the ironic thing is, like, for you kinda gotta give trust to get trust, which is essentially, like, saying, as you get deeper and deeper down that AI rabbit hole or further up the ladder, what's really important is as a user, you need to be kind of opening up the books, kinda giving more and more information to your agentic engineering platform, to your AI tool to be more and more effective. And, therefore, it will have more effective results, which will then kind of lead to more trust. So it's kind of that trust cycle. And so when you first start autocomplete, you don't really have to give it much context.

**Speaker 3** [00:57:15]
It has to look at the file, maybe some imports, may maybe some some relevant files, but it's it's you don't really have to open up the books. When you're looking at chat, then you're starting to kinda have a look at multiple files, the broader repository, related files, the docs. And then, you know, when you've got agents, full repo, dependencies, upstream, downstream, they it needs to know the ecosystem. And then lastly, when you're doing orchestration, it's not just it needs to know the agent just needs to know one repo. It needs to know all your repos.

**Speaker 3** [00:57:46]
And so I I'll give you an example. I'm a data guy by background, and, you know, we've got an amazing data team at kilo. It's a like all teams at kilo, it's it's like a team of one. His name is Pedro. He's a one person army.

**Speaker 3** [00:58:01]
When he came into kilo, we did not have much in terms of data infrastructure. What he did really effectively was he built in a week or two from the ground up, our whole DBT data model. It would have taken, I don't know, six months in a previous world. And how he did it was he didn't just interrogate the data. He gave he did it all in Kilo.

**Speaker 3** [00:58:23]
He gave Kilo the repository that he was working with, the project he was working on. He gave it access to the actually, the repository that had the application code. So what was important is his agent that was developing transformations for data warehouse actually was aware of the application itself and how it was structured, the application that was creating the data. And that was the huge unlock for him is that kind of he went deep in that orchestration kind of tier because he really embraced and said, hey. I want this agent to have all the context about the entire organization, and it it meant that he can move 10 times faster than he would have because it knew where how the data was created, had the origin story, it didn't have to ask.

**Speaker 3** [00:59:02]
Another kind of philosophy that that is really important for us at Kilo is is picking the right model for the job. And I'll be honest, like, we messed up here when we first started. We were just like, fuck. Yeah. Let's, like, send it to the most expensive model.

**Speaker 3** [00:59:19]
I'll get the best result. And sometimes that is the right way to go. Opus is a phenomenal model. Great to start with architecture, but some of these big models are expensive and a little slower because they're big and complex. And so you might kinda get in a state where you if you throw everything at the latest state of the art model, you spend a lot of money, you're essentially heating your home with inference.

**Speaker 3** [00:59:42]
It's just like churning, and it's slow when you're not moving fast. What we're big believers on is picking the right model for the job. You know, for those complex architecture tests, yeah, start with a state of the art model. For when you're coding, debugging, and you wanna move fast, use one of those more cost effective models like

**Speaker 0** [01:00:00]
Kimmy or MiniMax or GLM. And I think what the power is and what we've seen across all of our users is not when they use one model or this model, it's when they combine the models and use the right model for the job. The the the other thing that we've learned is that, you know, trust is measurable. It's not like this, like, oh, like in in the air, like, it's trust. It's actually trust is it's measurable to see if people actually are using the feature and kind of trusting the results.

**Speaker 0** [01:00:31]
And it you know, to be transparent, it gets harder and harder the further someone goes up that level of advancement in agentic engineering. When you first start with auto complete, we're like, you get great signal to noise. You get, like, if someone accepting your auto complete or is it not? And I think that's like that's the scoreboard and that's the thing you optimize for, and you get huge volume of it because, like, just you know, tab auto complete is the kind of the biggest kind of request quantity versus kind of just chat or any other category. What happens, though, when you start to get into chat is that, like, you know, someone will, you know, make a make a request.

**Speaker 0** [01:01:12]
They'll get back results. Are they copying it? Are they ignoring it? It's not necessarily clear if they're moving you're they're taking action on it on it, and it's there's a little bit of a delay. It's seconds.

**Speaker 0** [01:01:22]
And so you still we still get signal. We still get signal if if our agent is the prompt is right, the model is working well, but it's not nearly as effective as auto complete. What starts to get tricky is when you start to get an agent, some that's running kind of long term autonomously or multiple agents because you may find that, like, the test that's running and the result happens, you know, minutes, hours, days later. We found that's kind of when you start to get really, really challenging in understanding if, you know, the request to to the orchestrator, the request to that agent was effective. And so we've really spent a lot of time on instrumentation just to make sure that we're knowing and getting as much signal as we can on whether the features in kind of Kilo are are trustworthy and people are using it, and it's been really, really helpful in refining and finding areas where we honestly need to improve.

**Speaker 0** [01:02:13]
And what's great is because we ship so fast, we're able to quickly quickly get rid of those rough edges. Let's see. The the the other thing I wanna chat about is and I've seen this at at in Kilo at our team is the the work is not going like, it's not like people are working any less at Kilo and and kind of the the users of Kilo. It's it's shifting. And so I kinda think, like, if before your world was 20% really deep brain thinking and 80% coding, and, again, coding is working its own.

**Speaker 0** [01:02:47]
But what's what's shifting is you're going to, like, 80% thinking, 20% coding, or even less coding, and that's quite taxing. I mean, I think what what I've what's been really interesting to to observe is as someone joins the Akilo engineering team, how they kind of have to, like, warm up their muscle to the brain to, like, be spending that much time thinking. It's a real shift, and I I I think, like, we all as an industry need to figure out how to adjust because it is much harder to do forty hours a week where you are the architect and orchestrator, and, you know, you are supporting it's called two hundred hours a week of someone an agent coding versus four hours a week of architecture and thinking and kind of thirty six hours of coding. And I think that's that's something that we've been really conscious to support our engineers as they kind of get used to that balance, but it is something I think we all need to be aware of as the world shifts and the the role of an engineer shifts. And so, ultimately, what does the shift look like?

**Speaker 0** [01:03:44]
The developer is the conductor of an orchestra. They are the taste maker, the architect, the they're deciding the quality gates, and then the agent is just handling all the execution. It's doing all the typing. The boil the boilerplate is hunting for that missing comma or semicolon. It's looking up the documentation.

**Speaker 0** [01:04:01]
It's writing your documentation. Again, at Kilo, everything is reviewed by human, maybe not every single line. We leave it to the discretion of the developer to to kind of conduct a level of review that's needed. But what happens when you get to this world, you're seeing that's when you're seeing the the 10% improvements in shipping velocity. And, again, like I said, we have a saying at Kilo, which is the proof is in production.

**Speaker 0** [01:04:24]
Really don't believe me on these stats. Just take a look at kind of our product road map and see how quickly we're shipping features. If you really do embrace this new role of a of a developer, velocity follows. And so just, you know, here's here's a quick example of the five out of the box agents that come at Kilo. We got our orchestrator.

**Speaker 0** [01:04:42]
We've got our architect, code agent, ask agent, debug agent. And so, for example, Suraj Shuli, who ends who owns the code reviews end to end, you know, as soon as he joined Kilo, he used the ask agent. He's like, yeah. Tell me about Kilo. Teach me.

**Speaker 0** [01:04:56]
Like, he wasn't going to a colleague to get briefed on the code base. He was going to the ask agent. And then it was going to the architect agent to help them help him construct and design the features he wants to build, and then he went to the code agent to actually implement. And then as he felt those sharp edges, he was debugging it in the debug agent. And then, you know, we also have a lot of custom agents and custom modes that developers have made within Kilo.

**Speaker 0** [01:05:19]
One of our engineers called Brian, and so he made Brian mode. And so a lot of our developers use Brian mode, which is Brian settings. And so what's really important is to customize your team, you know, in a world where where the developer is the manager of a team of agents, you really need to have the right team. And so just to review where we're at, you know, you gotta meet users where they are. You can't kind of shove AI down their throat.

**Speaker 0** [01:05:42]
You know, if they are just just starting, you know, start them on tab autocomplete. Get them started to get into the chat. Build the trust and be very conscious of those opportunities where you can lose trust. Solve those infrastructure, you know, issues early. Again, if you are not, you know, solving the issues where people might potentially lose trust, you can very, very quickly lose people along the journey, and then trust is key.

**Speaker 0** [01:06:06]
I mean, you've gotta build it. To be successful, you've gotta have that feedback loop. And I mean, if you do that, I think what we found is that's helped us move fast, help us get our kind of 1,500,000 users up that up that learning curve, and it's been something that we've we've been really focused since day one at Kilo. Cool. That's it for me.

**Speaker 0** [01:06:25]
I think we've got four minutes of questions ish, maybe. Demetrius is giving one and a half thumbs up. Two. Two thumbs up. Okay.

**Speaker 0** [01:06:33]
Cool. Any questions? Hi.

**Speaker 1** [01:06:38]
So you mentioned that now one engineer is responsible for multiple features?

**Speaker 0** [01:06:43]
One feature. One engineer, one feature.

**Speaker 1** [01:06:46]
Okay. When it's not a team and just one engineer, how do you deal with things like vacations, other times off, maybe they have an emergency from an organizational perspective?

**Speaker 0** [01:06:57]
Yeah. I mean, great question. We don't allow time off. No. No.

**Speaker 0** [01:07:00]
It's it's no. We do. We do. But it's really interesting. So I'll tell you what.

**Speaker 0** [01:07:04]
We've got a whole product road map at Kilo, and what's next to it is a lot of our new features is just a blank line. And the single thing that's gating us starting that feature is hiring a person. And honestly, when that person goes away for a week, that product might not move for a week. And we're cool with it because the gains we have when that person is on is so much more. Yeah.

**Speaker 0** [01:07:25]
We'll make sure we have coverage. We always have an on call. But I think, you know, it's it's one person team, and, you know, when they they're off for a week, you know, that's if code reviews doesn't progress for a week, Suresh was probably on vacation that week. But, yeah, great question. Cool.

**Speaker 0** [01:07:42]
Oh, thank you. What if it's a production issue? A production issue? So we always have one on call engineer at all times. And so night or day, they'll jump in.

**Speaker 0** [01:07:53]
If it is during the day and it is related to that person's feature, they might jump in as well. But what's great is we've got great, you know, proactive monitoring. So we discover these issues ideally ideally before they become big issues. And then, you know, the the kind of on call developers using the ask agent to kind of understand the problem literally. And what's the most one of the most popular features at Kilo is our Slack bot.

**Speaker 0** [01:08:19]
You know, if I'm making a change to our website, I just I don't go into Kilo anymore. I just say, Kilo, extend this promotion one more week or change the color on this page. The first thing a lot of times the the on call engineer will do is, like, at kilo, analyze the problem, tell me what's going on. And I think that's it's been, like, a huge unlock because they don't have to search around the con you know, search where the the right context is. The agent is kinda pointing them in the right direction from day one.

**Speaker 0** [01:08:44]
But, yeah, great great question. Really, really great question. Cool.

**Speaker 2** [01:08:48]
This is it.

**Speaker 3** [01:08:49]
Yeah. You talked about, say, from agent then to orchestration. For many people, they may just use maybe a single agent, say, for building, for debugging, for many things. How how are you really do, like, the orchestration, say, maybe by hand, say, use several agents and I try to orchestrate by a person, or you may build some workflow to really, you know, do the application.

**Speaker 0** [01:09:13]
So out of the box, our orchestration agent, you run, like, ask the orchestrator. It will break up the task and give it to the right agent. And so you don't even have to think of, like, I wanna go multiple agent. You'll just say, work is like, orchestrator, this is the thing I wanna do. It'll come up with a plan.

**Speaker 0** [01:09:29]
It will kick off several agents, and it'll just do it. So, I mean, it's it's just the the idea is to make it seamless, but really great question.

**Speaker 4** [01:09:36]
I have a question on PM to engineer ratios. I think to use the twenty twenty three mindset, to use your term, we usually, if we think about it, one product would be like six to eight engineers. It sounds like you guys are more towards like closer to a one to one. Do you see that one to one is sort of like the ideal where it gets? And I guess a second part of the question is for the your customers that are using your product are the best ones getting like what are those ratios look like?

**Speaker 0** [01:10:05]
Yeah. That's a great question. We don't really believe in PMs at Kelow. So that's like, you know, every engineer is their own PM. They are they're setting the product road map.

**Speaker 0** [01:10:17]
They are kind of they're doing the building. They're implementing. They are kind of everything. So we we have actually, we have one PM in in the entire company. And, you know, this is a great question to kind of you know, when it was a production issue question, over there, it's like where we found the value of having a PM is kind of on that platform on the horizontal.

**Speaker 0** [01:10:38]
So if you can imagine all of the kind of the the developers own these kind of vertical type features that are owned by a broader KeyLab platform, That's where we've seen the value of having the PM is focusing on that that kind of horizontal underlying platform that kind of supports all of the features that each of the engineers own. The ratio, I think it's all over the place. I mean, I think, like, we've definitely drank the the bright yellow Kool Aid of Kilo and, like, are all in the one to one. I think we're probably in the 1% of folks. Like, most of our our, you know, we're we're very big on encouraging all of our our users to be kind of as full stack as possible, but I think a lot of organizations are somewhere in that journey between peanut buttering AI on the existing, like, you know, org structure to making a fundamental change in, like, somewhere in that journey.

**Speaker 0** [01:11:26]
But I think we're we're definitely on the deep end on that one. But happy to I'm I'm gonna hop, but happy to chat about that. I'll be in the back after this. Alright. Cool.

**Speaker 0** [01:11:32]
Scott. Thank you, Dimitris.

**Speaker 2** [01:11:34]
It was good.

**Speaker 5** [01:11:35]
That was great.

**Speaker 0** [01:11:36]
Thank you.

**Speaker 5** [01:11:37]
That was great. Alright. So we're gonna keep that applause going. Please give a warm welcome to Jess from Brain Trust.

**Speaker 3** [01:11:50]
Thank you.

**Speaker 1** [01:11:53]
Oh, awesome.

**Speaker 6** [01:11:57]
Alright. Hi, everyone. So I'm Jess from BrainTrust. I'm a bit shorter, so I'm just gonna stand over here. So BrainTrust is a platform that lets you do observability and evals for your AI tooling.

**Speaker 6** [01:12:13]
So pretty much in this talk, I'm gonna talk about what Evals are, why they're important, and then I'll talk through a real life pretty complex Eval that we ran a couple weeks ago. Okay. So I have been in legitimate calls where teams have told me that they've shipped AI features, either one because the engineering team told them that it was ready or a PM tried a couple of prompts, and they said it looks good. That's very problematic because you're essentially making ship decisions based off of vibes, which is not good. Ideally, you would like to be able to quantify when you're shipping by saying things like we ran 200 different test cases and 94% of them passed, and so therefore we're shipping it, or, to be able to say nuance things like, we ship this change and it improved the tone but decreased accuracy by 5%.

**Speaker 6** [01:13:16]
This is why evals are important. Actually, can I get a raise of hands of how many people have heard just the term evals? Or okay. Good. Okay.

**Speaker 6** [01:13:25]
Glad. Glad we're on the same page. Okay. So evals are important for a couple of reasons. They can answer questions.

**Speaker 6** [01:13:31]
So which LLM is the best choice for our needs, especially when new models drop? This is always a big question in our minds. How does the AI perform across diverse real world scenarios? So for example, it could perform really well on Python code bases, but not TypeScript code bases. It could do really well with English inputs, but not Japanese.

**Speaker 6** [01:13:54]
Cost efficiency, can we achieve high performance without excessive costs? Does the AI reliably reflect our company's voice and standards? Are we learning from users and improving iteratively? And how do we know when something breaks or gets worse? Actually, this is a really interesting real world scenario that happened.

**Speaker 6** [01:14:16]
So in April 2025, so about a year ago, OpenAI actually had to revert an entire model update because the changes that they made to make it more helpful actually made it too agreeable and therefore not very useful. And so this is an example of when it's very easy to overtrain models, and so you wanna be able to catch these nuances early on. Okay. So there are four major parts to kind of creating an eval. The first is you have to create a dataset.

**Speaker 6** [01:14:53]
So a dataset is gonna be a collection of test cases that you are going to pass into your system. These are usually gonna be your golden use cases, your edge cases, and then failure modes. Then you need to write a task. So a task is going to essentially tell your system how you want it to behave when it takes in an input and gives you an output. So this is usually in the form of a prompt and then also picking a specific model to do this task with.

**Speaker 6** [01:15:25]
Then you want to write a scoring system. So for your scoring system, essentially, it is what tells you whether the AI's output is good or bad. There's a couple. If you've heard of them before, there's deterministic scoring. There's LM as a judge, and there's human in review.

**Speaker 6** [01:15:44]
But, essentially, you who are writing the score is defining the criteria of what comprises what good and bad is. And then the last thing is you want to experiment. This is the most fun part. But, essentially, one run of this specific configuration of your dataset, your task, and your score is equal to one experiment run. So as you are testing out different hypothesis and trying to tweak things in your system, these will all turn into different experiment runs.

**Speaker 6** [01:16:18]
So then once you have a bunch of experiments, you can actually start to compare them. So you can essentially see if there are any regressions or improvements across your experiment runs, and you can also click into individual rows to see which test cases have changed. BrainTrust also has a feature called loop, which allows you to query your experiments using natural language. So, essentially, I can ask it, highlight problems in my experiments or highlight specific patterns that you're seeing in my experiments. Or if you ran a a bunch of different experiments, you can ask it which experiment performed the best.

**Speaker 6** [01:17:03]
I was honestly really skeptical of loop when I joined the company, but I use it a lot now mostly because traces, like long traces of, like like, an LM does a bunch of turns and it hallucinates or it drifts is really, really hard to manually read through. And so I find that lube is just bad it's faster than what I can do, and it's better at detecting these patterns than I can. Yeah. And then the last thing is you can log. So you can just wrap your code using the Brain Trust SDK, and you can start to get live production logs.

**Speaker 6** [01:17:38]
So the way that we chain this altogether is, essentially, you have some sort of application. So, for example, let's say, it's a documentation page with a chatbot on the side where people can ask questions about documentation. So what happens is you have users or customers that use the chatbot or the chat panel, and so they we start to get live production logs that have the user question as well as what the LLM responded with and then whatever metadata that you want to pass into those logs as well. Then you can take those logs and sample 10 to 20% of them depending on how much traffic you're getting in production and turn that into a dataset. Using that dataset, then you can start to write evals.

**Speaker 6** [01:18:30]
So you can start to tweak the dataset or tweak your score or tweak your prompt. And you might try to write a prompt that is more concise or you want the AI to answer more enthusiastically or things like that, whatever you and your team think is correct for a response. And then based off of how the evals do and what you learn from them, you will then bring that back into the app and ship code changes and tweak the app based off of what you learned from the evals. So that's usually how it works in a loop. If you are the type of person who's taking pictures on your phone, this is the best slide in the deck.

**Speaker 6** [01:19:10]
So it's the one slide I did not make. So but I my coworker made the slide, and it's just so good that our entire team has been using it over and over again. So evals are a team sport. I really like this. Evals, on the right, you can see they comprise of a lot of different steps.

**Speaker 6** [01:19:29]
If you've ever done an eval before, you'll understand that it's a living, breathing machine, and it requires a lot of components. So you have, like, the AI engineer engineer that is bringing data to the platform as well as obviously making the bug changes and feature feature changes as well. Then you have the product manager who you know, if you work at KiloCodes, might just be the same as engineer because they don't believe in product managers. But, I mean, the sorry. That was not that did not that came out aggressive.

**Speaker 6** [01:20:08]
But, like, they could be the same thing, which is totally fine. But they are the people who develop hypotheses or, also tell you what the success criteria is. Then you have subject matter experts, who help label the data or tweak the prompt. This is especially useful, I've seen in, like, medicine fields or law fields or insurance fields where they're very niche subsets of knowledge, and you need subject matter experts to help you, like, label data. And then you have data analysts that help you define the scores and, obviously, analyze data.

**Speaker 6** [01:20:45]
So evals are a team sport. Okay. So now that we've kind of gone through a lot of the concepts of evals, I thought it would be interesting to tie it to a real life scenario, a real life eval. So I wanted to talk about an eval that I ran to measure which one is better, agentic search or vector search. This was actually an idea from our CEO, Ankur.

**Speaker 6** [01:21:13]
He often pings me with things I should eval. I do ignore him about 99% of the time, but this one was interesting. So he is on Twitter a lot, and he sent our Slack channel this article from Cursor talking about how they use semantic search, also know I call it agentic search, to significantly improve their coding agent experience or performance. And after a quick search online, I did see there was a lot of discourse about whether agentic search or vector search was better, and I just thought it would be interesting thing to independently eval. So we did that.

**Speaker 6** [01:21:52]
Okay. So because we're comparing agentic search and vector search, I just thought it'd be good to get us all on the same page about what vector search is. So vector search is essentially the process of converting data, like text or code into numerical representations called embeddings. These embeddings capture semantic meaning, so similar items will live closer together in a very high dimensional space. So if you look at the chart on the right, you'll see that words like wild west and broncos are close together.

**Speaker 6** [01:22:27]
Basketball and soccer are close together, and antelope and wild beast are close together. Obviously, this is a two d representation, but you can kind of imagine this in an n space dimension. And then what happens is that these embeddings get chunked up and stored into effector database like pinecone. So for example, if I were to ask, where does the database logic in my code base live? Essentially, my code base would be vectorized and embedded and stored into my VectorDB.

**Speaker 6** [01:22:59]
And then the VectorDB would find the closest embeddings that match my query, so words like database or logic. Okay. So then what is agentic search, also known as semantic search? So agentic search is what tools like Claude code uses. And, essentially, what happens is the LLM has access to CLI, command tools like grep or find l s cat, things like that.

**Speaker 6** [01:23:28]
And it basically reads the code very similar to how a human would. So it would search for a function name, open the file, read the file, sees that the file calls another piece of logic or another function, and then follow that reference and repeat until it finds whatever it needs to. So it's more like how a real human would act. So that's the difference between agentic and vector search. Okay.

**Speaker 6** [01:23:55]
So now that we understand the differences, let's build an eval to see which one works better or works better. Okay. So for this experiment design, I created two different datasets. So the first one was using Microsoft's TypeScript Go repo. Essentially, what we did is we pulled merged PRs from that code base, anything with the word fix in the title.

**Speaker 6** [01:24:25]
And then from there, we checked out the parent commit so that the code base was in a known buggy state essentially before the fix. And then we used Claude to synthesize a bug description for that PR diff. So, essentially, we're trying to get, like, a format, like a linear task group, like, bug ticket. And that way, we can pass it into the agent and tell it to find the bug and fix it. And then we use the Go test suite as kind of our like, if it passes the Go test suite, then it passes the eval.

**Speaker 6** [01:25:00]
So, hopefully, that makes sense. And then the second dataset is essentially using the same thing, but we basically pulled a couple rows from the industry standard, SuiteBench verified. Have people heard about do people know what SuiteBench verified is? Okay. Couple less people who knew what evals were.

**Speaker 6** [01:25:18]
It's if you read, like, any sort of it's it's what, like, Anthropic and OpenAI AI use to, like, benchmark their models. So it's, more of industry standard. So we pulled 25 rows from that, specifically from the the Django related data rows, but the idea is the same. And then the reason why I used two different datasets is mostly because I just wanted to have some variety, and I wanted to test agentic search and vector search on two different languages and two different code bases. So Django is much more of a massive legacy code base, and TypeScript Go is newer and more modular.

**Speaker 6** [01:25:58]
So I just wanted to see if there was any difference in how they performed across two very different types of code bases. Okay. So the next thing we had to do is implement vector search and agentic search. So implementing agentic search was really easy because Claude code uses agentic search by default. So all we did was just set Cloud Code on all of these tasks.

**Speaker 6** [01:26:23]
For the vector search variant, that was a little bit more difficult. So, essentially, what we did is we, implemented a basic vector search and had the agent call that through a script. But the problem was we still wanted to use Claude code to keep the eval experiment as consistent as possible. But the key constraint is we actually had to prevent Cloud Code from falling back to agentic search, which it really wanted to do. So this took, like, a couple of days.

**Speaker 6** [01:26:54]
I had to really block it from using agentic search and try to call that vector search script every time. To do this, we basically did two things. So I used CloudCodes disallow tools flag to block any agentic search. So block calling grep or find or things like that. And the second thing I did is I very explicitly said in the prompt that anytime I wanted to use search, it should use vector search.

**Speaker 6** [01:27:24]
So I believe this is a screenshot of the prompt I used. But, yeah, without these two things, it would continue calling agentic search, which would have screwed up the whole experiment. So we really had to make sure that it was only using vector search. Okay. One other thing that was difficult when we were doing this eval is, that Cloud Code runs as a subprocess, which means that the traces were orphaned, and they weren't actually being connected to the parent trace, ID.

**Speaker 6** [01:27:56]
So the fix that we did here was passing in the parent span IDs as environment variables so that the subprocess could actually attach itself to the right trace tree. If you don't know what that means, don't worry. I brought pictures. So here is what it looks what the trace looks like before we did that fix. So you can see it says run Cloud Agent, but you don't actually get any visibility into what the Cloud Agent is doing, like, what it's actually trying to do.

**Speaker 6** [01:28:28]
And here's what it looks like after we implemented the fix. So you can see that now every single LLM call and command line execution is logged in the trace here. So you can see it's calling Clotsonnet, and it's, you know, running things like find and read and things like that. And you can also see, like, in the LLM call, like, what is actually inputting and outputting to the LLM. So, yeah, this was really critical for us to implement because it allowed us to actually debug why certain things were failing or passing.

**Speaker 6** [01:29:09]
And then in terms of the scoring, we just implemented kind of just one score, which is essentially did the fix pass all the repos existing tests. So if they passed, then the eval run got a 100%. And if they failed, it got a 0%. There is one interesting nuance here for the SWE bench dataset. So SWE bench actually gave us a test suite called pass or sorry, called fail to pass, which is essentially a a list of tests that were failing before the fix but should be passing after the fix.

**Speaker 6** [01:29:48]
But the interesting thing is if the fix passes everything in fail to pass, but then fails another test that's not in that test suite, it still passes the eval because, technically, it it did fix that specific issue. So that's just an interesting nuance I wanted to note there. And then we also tracked met metrics like duration, total tokens, and cost. Okay. So here are the results.

**Speaker 6** [01:30:20]
So for the sweep bench dataset, which was, again, the 25 Django related code bugs, the vector search got a 60% accuracy, so it passed 60%, and then AgenTick got a 68% accuracy. And then for the TypeScript Go code bugs, the vector search and AgenTick search actually both scored 70%. But as you can see here, VectorSearch spent a lot more tokens and money. When you look at these results, I the one thing I'll note is I would take this with a grain of salt. I highly doubt that vector search cost me over $4 per run because if you do the math, that's $40, and it didn't cost me $40.

**Speaker 6** [01:31:10]
So I I think the exact cost is probably off, but what I would look at is the comparison between vector search and agentic search, essentially seeing that agentic search is x multiplier cheaper. So another thing I'll call out is the reason why I don't have the metrics for SWE bench is because I was running this eval last night, and it takes a really long time to complete. And so I just didn't have time to get the numbers for SweetBench. But yeah. Yeah.

**Speaker 6** [01:31:45]
Doing this last minute. Okay. So there are three main takeaways that I got when I looked through the results and also the the Cloud Code traces. The first interesting thing was that vector search returns a lot of chunks of code. So in these chunks of code, there might not be, like, the relevant imports or relevant type definitions or the relevant code calling code above it.

**Speaker 6** [01:32:13]
And so, essentially, the agent doesn't get enough signal for what else to look for. So, for example, in the SWE bench dataset, one of the runs, the agent made 26 different vector search calls. Essentially, it was just trying to, like, guess and check so many times, and it just couldn't find the right place in the code base where the bug the bug was happening. And the contrast is, you know, in agentic search, the agent can essentially look for the function name, read the entire file top to bottom, see the import chain, and then follow it and solve the task a lot more quickly that way. So the way that I like to kind of think about it or conceptualize it is that vector search gave the agent a lot of proximity to relevant code but didn't but didn't give the connective tissue between the code for it to actually implement a fix.

**Speaker 6** [01:33:13]
The second thing is agentic search enabled or was able to do a lot of chain of thought exploration. So it's kind of what I mentioned before where it's actually able to look at the function and see what calls it and actually be able to travel to different files to follow the logic, whereas vector search can't really do that, at least in the traces that I saw. And the third thing is the more searches, the more expensive. So the reason why vector search took so many more tokens and took so much more money is because it was making so many more calls because it just couldn't find exactly where in the code the bug was happening. So that's why it was so much more expensive.

**Speaker 6** [01:33:57]
Now the last thing I'll say is I don't consider this eval close to being done at all. Like, I would not publish a blog post about this yet. Mostly because just from a gut sense, I act like, this eval basically is saying that agentic search is a 100% better than vector search, which I don't think that's the case. I think there are places where vector search is better. And so something I would do is, one, I would run multiple trials per task.

**Speaker 6** [01:34:28]
LLMs are very nondeterministic, and so I would not be surprised if I ran this eval multiple times with all the exact same criteria that it might have a difference of 10 to 15%. So that's one thing that I would run multiple trials and kind of average the scores across them. The second thing is, honestly, I think this I would improve the vector search implementation. It was a very basic vector search implementation, so maybe that's why it's not performing that well. I'm not an expert on vector search, but I do think there's things like like chunk overlapping or splitting the text or retrieval models that can be implemented to improve vector search.

**Speaker 6** [01:35:12]
So it might just be that my vector search implementation was just bad. And then the third one, which is not really a blocker, but it would be interesting, is to try a hybrid approach. I do think a lot of companies now are doing a hybrid between vector search and agentic search. And then the fourth is to expand the dataset. So, obviously, a dataset of ten ten rows, if it fails one of them, that's a swing of 10% in the score.

**Speaker 6** [01:35:38]
So just expanding dataset, adding more rows, and also adding potentially more languages or more code bases. And that's it. That's kind of evals and also example of how to use an eval in in real life. Yeah. I I think I only have one minute for questions, but we can do, like, one or two if that's helpful.

**Speaker 6** [01:36:01]
Yeah. Does anyone have any questions?

**Speaker 7** [01:36:07]
Thanks. Hi. I I wonder if you did anything to to try and isolate or characterize the the token usage from restricting Claude from going into agentic mode.

**Speaker 6** [01:36:23]
Yeah. Yeah. That is that would be something I'd add to the improvements. It was something I thought of. The the short answer is no.

**Speaker 6** [01:36:33]
I didn't, but I did think of it.

**Speaker 7** [01:36:34]
That's a

**Speaker 6** [01:36:36]
So it was definitely something I thought could be inflating the token count. And so as I'm trying to iterate on this eval, I would definitely probably look through the traces, like the cloud code traces, and see if it's inflating the token count every time it's trying to essentially do an agentic call but can't do it and then has to switch over to Vector. So yes. Yeah.

**Speaker 7** [01:36:56]
And one more question if I could. Have you run against human respondents?

**Speaker 6** [01:37:02]
Like, having a human review it?

**Speaker 7** [01:37:05]
Group for for for a similar set of questions or a subset of the questions that you're asking the AI?

**Speaker 6** [01:37:12]
Wait. Sorry. Say that again.

**Speaker 7** [01:37:14]
As a control group for questions that you're asking AIs, have you considered asking humans for responses to those and measuring differences?

**Speaker 6** [01:37:24]
Yeah. That's a good question. So the SWE bench dataset actually comes with a golden golden answer. So SWE bench, because it's an industry standard, already has, like, the answer key essentially that was, like, human coded. So we could technically compare it against that human, like, golden the the the answer set essentially for SuiteBench.

**Speaker 6** [01:37:47]
For the TypeScript Go ones, I guess, technically, because these are merged PRs, we can also just compare it against the actual fix from the PR. So I guess we could actually compare it against the actual code and probably use some sort of, like, LLM as a judge to see how close the code is. So I didn't I haven't done that, but I think that's a really good suggestion. Yeah.

**Speaker 2** [01:38:10]
First of all, thank you for the presentation. I'm curious about this. I I work closer to the users. And one of the things that we are seeing as we are building a conversationally product on top of data is that we are starting to deal with a lot more people who have smaller retention spans. And what that means in translation of the product is they will start a question, for example, thinking about where can I get a matcha?

**Speaker 2** [01:38:37]
From there, they will go to where can I buy a Lululemon? From there, they will go to the latest price of Tesla. From there, they'll go to something else about, you know, Elon Musk's latest conspiracy, whatever. Now what I'm curious about is it is becoming increasingly harder for me to think about evals in that perspective because the idea of a golden dataset suddenly doesn't make sense to me. I it's impossible for me to emulate the thought of this person.

**Speaker 2** [01:39:01]
I've thought about maybe getting a synthetic agent to, like, think about this. But for a for a case like this where there's no going to be there's not going to be a straight chain of thought, there's not going to be a consistent golden dataset, How do you think about evals, and are this something that you may have published that we should probably be thinking about or reading about?

**Speaker 6** [01:39:21]
Yeah. Definitely. So I think if you are seeing it in your application or if you're seeing it in whatever product that you're building, that's enough because, essentially, you should be able to log that and turn that and add that to your dataset. So if you're seeing people who have short attention spans or jumping through different questions or different parts of your app, that should be logged somewhere, and you should be able to turn that add that to your dataset. So that'd be my answer.

**Speaker 6** [01:39:53]
Then from there, sure, you can use AI to add more synthetic rows to your dataset based off of that, but I think that's the biggest thing is just to turn your actual user journey into just something in your dataset. Yeah. Okay. Awesome. Yeah.

**Speaker 6** [01:40:07]
Thank you,

**Speaker 5** [01:40:08]
Chris. Thank you so much. How are doing right now? Quick vibe check on the floor. How's it going?

**Speaker 5** [01:40:18]
We're doing alright? Yeah. I like that. Alright. We got some good energy in here.

**Speaker 5** [01:40:23]
That's cool. Good people. So spoiler alert, that was me on your app there earlier, my man in the front row. I'm your problem, so we can talk later. I could tell you too much TikTok is the answer.

**Speaker 5** [01:40:37]
So I got one more talk before we hit lunch. I'm gonna invite up from Union, mister Nils. Where are you at, dude? Here we go. Put This is yours.

**Speaker 1** [01:40:52]
I got a I got a mic here. Okay. Cool. Hey, everyone. Alright.

**Speaker 1** [01:41:00]
So I'm Niels Ventilin. I'm the chief ML engineer at Union, and I've been building and maintaining a open source ML orchestration product called Flight for the past five years. And through this product, I've been helping companies like LinkedIn, Stripe, Spotify, and more recently, Mistral helping build and deploy production grade ML and AI systems, you know, from fraud detection to oh, let's see. Oh, here I am. Fraud detection to recommendation systems to LLM foundation model training systems.

**Speaker 1** [01:41:41]
I don't do the hard work. I build the tools that our customers and our open source users do all the hard work to to do all that. But today, I wanna share with you some of the lessons that I and we at Union have learned productionizing agentic systems with with our orchestrator. And in particular, I wanna tackle the question of what is the orchestration stack for observable, debuggable, and durable agents? And to tackle this story, I wanna take you through my agent adoption timeline.

**Speaker 1** [01:42:16]
I guess just out of curiosity, who here has installed OpenCLaw? I I haven't, so I can't. Cool. Who is willing to install it on their company infrastructure? Okay.

**Speaker 1** [01:42:27]
No one. Cool. There there are the more secure versions that I know I know now, like ZeroClaw, a few of them out there. I haven't checked them out personally. But, basically, in 2022, I, like probably many of you, made first contact with LLMs that have coherent long range text generation, and we are all like, oh, wow.

**Speaker 1** [01:42:47]
It kind of working now. Right? In 2023, I went about sort of fine tuning LLMs. That was a big story back then. Open weights models, fine tune it on flight code, see if it can generate flight code well or any other type of DSL or subset of a programming language.

**Speaker 1** [01:43:05]
Also started looking at RAG as a system to overcome the context window problem, which I guess is still a problem, but, you know, now we have 1,000,000 token context window models. Oops. Then in 2024, know, just I'm not an early adopter in these things. I continued learning and prototyping. So line chain had come out already.

**Speaker 1** [01:43:28]
So I I tried building some line chain apps for internal use cases. I started using cursor. And at the time, long range or or end to end tasks weren't really working then. So it was mostly, like, tab complete vibe coding with, like, editing in the loop. Right?

**Speaker 1** [01:43:47]
Also started using tools like Perplexity and desktop and things like that, and that was starting to give us an inkling of of agents that can do more than just like turn by turn chats. Then last year, we made the critical decision to modernize flight. And so we set out to build flight two point o. And this was our answer to some of the things that I and we as a as a company had learned building these things internally. So we internalized all the feedback we were getting from users, our own internal tastes of how we like building agents.

**Speaker 1** [01:44:21]
And so flight two was our move to answer the answer the question of durable, fully dynamic, crash proof with some caveats, infrastructure aware orchestration, not only for agents, but also good old classical ML and data science and ETL. So this is where we built Nodi. This is an internal agent ambient agent that sort of reconfigured Kubernetes node pool configurations for our customers. So customer on Slack would say, hey. I want this kind of node pool, and then Node would go.

**Speaker 1** [01:44:58]
And, you know, it's kind of like the Rick and Morty butter robot. All it does is change node pool configs, build a few more of these internal tools, started using cursor agents and Claude code kind of at the tail end of that year, and so I was, like, pretty much agent pilled at that point where you can mostly do end to end tasks, and then, obviously, you have to review the code and fix all the crazy bugs and things that it would introduce. And now it's 2026, and it arguably is the year of agents. And so what we're doing now and what I wanna share with you is how we are thinking about productizing all of our learnings. And in particular, I am leading a team to help build agents for the thing we know and love, the best, which is data science, machine learning, AI engineering, ML Ops.

**Speaker 1** [01:45:50]
Okay. So the crux of the problem here that I wanna highlight today is the agent infrastructure problem. So you build an agent. Great. That's the first step.

**Speaker 1** [01:46:01]
You optimize its prompts. You engineered its context. You built an eval harness, and it works beautifully in production. But what we found in development sorry. But what we found in production is actually oftentimes the infrastructure gets in the way.

**Speaker 1** [01:46:15]
Tools oops. This is not the latest version of the slide, but it's okay. I'll make do with it. So tools need secure and least privilege access to your and I'm talking not personal use on your laptop. Right?

**Speaker 1** [01:46:29]
This is like you're building stuff, agents that have access to your organizational data assets and databases and data lakes and whatnot. Oh, wow. Fixed itself. Great. Wow.

**Speaker 1** [01:46:42]
What was that? There's an agent loop in there. Tools and agents that require variable compute resources. So if you're building a machine learning agent, you you a single node runtime is not gonna cut it. You know, the agent may run on a small CPU box, but it's gonna train a model that's loading a several gigabyte dataset.

**Speaker 1** [01:47:00]
Right? So the agent needs some way to provision its own compute, like, in its inner loop. Right? Same thing with paralyzed sub agents and tool calls. If you have a single node or some, like, fixed set of nodes, you're gonna get resource contention, gonna get degraded performance.

**Speaker 1** [01:47:20]
Containers go, oh, anyone here who's trained a model or done anything with data has seen this type of thing. The your nodes are killed by the scheduler. Spot instance are preempted. Then ultimately, these kinds of infra failures lead to agent memory loss or corruption, and this wipes out precious context. So agents fail at multiple layers of the orchestration stack.

**Speaker 1** [01:47:44]
And the problem isn't that agents fail. It's that recovering from failure is challenging without the full context of how infra, networking, logical, semantic layers, all of these interact so that the agent can figure out how to dig itself out of the hole it's found itself in. And so what agents are saying, agents are say telling us, help me, help you. Agents now are very capable of helping themselves if they have the right context, even infra infra level failures, if you give them the right context and capabilities. And so for the rest of this talk, I'll be sharing not, like, things that are written in stone.

**Speaker 1** [01:48:24]
These are just kind of design principles we've distilled down into six of them. I'd like three or four, but, you know, got got six. And these are more like rules of thumb, things that you should think about when you're building agents. And so I'll dig into these more, but, basically, number one, use plain Python, TypeScript, JavaScript, or whatever, like, general purpose programming language that an LLM knows. Knows.

**Speaker 1** [01:48:47]
So pick that. And those languages will have frameworks that you can, you know, quickly build agents on. But what we found is for us, for example, flight two works with Plate and Python. That's just really easy to to access all the constructs, programming constructs for the human and the agent to use in building. The second design principle is providing durability and observability hooks.

**Speaker 1** [01:49:13]
Then make failures cheap so that when you do fail, that your run, your agent rollout can recover really quickly and and continue where it left off without having to recompute all the other stuff. Provide infrastructure as context. This is a a key thing that that we found that's quite quite important when you're building sort of variable compute agents that require variable compute in the inner loop. Providing agent self healing utilities. So these are things that where the agent can fix its inner loop, which I'll show you what what I mean exactly later.

**Speaker 1** [01:49:52]
Self healing is a little buzzwordy, but it it's what basically, how do you recover from failure in the inner loop? And, the utility in this case would be sandboxes so that they can inject a little bit more creativity in how they solve the the particular problem that the user's given them. And then finally, human in the loop as the final recourse. So agents break up, as I mentioned earlier, multiple multiple layers. Layers.

**Speaker 1** [01:50:19]
Right? Right? So So from from infrastructure infrastructure to to network network to to logical logical to to semantic, semantic to tool execution and context. And, actually, what we found is there's there are a lot of techniques and a lot has been written about how to handle network to context. Those are those five levels.

**Speaker 1** [01:50:37]
And it's it's not no by no means a solved problem, but there's I think we found that there's still a lot of pain in the infrastructure layer of this. And I'll show you an example in a little bit. And I think one of the problems is that there's a context and evaluation gap. So your your evals typically test semantic correctness. Does it answer correctly?

**Speaker 1** [01:51:01]
Is it hallucinating? Are am I is the tool call arguments formatted correctly? That kind of stuff. And likewise, agents typically focus on recover recovering from these kinds of logical and semantic failures. But agents don't often directly handle or reason about surviving a network outage or a timeout or recovering from system level errors or recalling state across retries.

**Speaker 1** [01:51:26]
And so the one insight I wanna give you today is that agents can actually recover reliably from all the errors in this this stack that I mentioned earlier, even infrastructure level ones, but only if you're given the right context and the right capabilities to dig themselves out of that hole. So context engineering is not just not just, you know, shuffling tokens and getting more data sources, and and those are important activities. These are, like, the the key ones that you need when you're initially building your agent. But context engineering is also an infra problem. If a failure wipes the agent state, then all the hard earned earned contacts that you've implemented in your agent loop is is worthless.

**Speaker 1** [01:52:11]
And so we think about durability as making it super easy to do the following, to immediately resume an agent rollout where it left off, to share to not re execute shareable compute and IO bound workloads, and to save and restore state and memory between tasks through intermediate state persistence. So these are just basic building blocks that benefit not only agent builders, but MLEs and data scientists alike. And so these three elements I want to dive into before going into the design principles just because I think they're important. And they're the core building blocks of flight and any other system you may want to implement, I think. So what is a replay log?

**Speaker 1** [01:52:57]
This these aren't, like, official terms. This is, like, what we call them. But a replay log is essentially a service that records the state of an agent and its subtasks at a super granular level at each step. And the benefit of this is you can avoid re executing tasks, prevents memory and context loss, even it recovers from crashes in the root agent process. So in this case, you have an agent.

**Speaker 1** [01:53:23]
Does that have a pointer? That's fine. Agent that does tool call one, sub agent call one, tool call 2, and it succeeds at the first two steps and fails in the third one for whatever reason. Right? A replay log will keep a log of all those steps and all the intermediary outputs.

**Speaker 1** [01:53:40]
So in the case of a crash, it recovers. Tool call one's done already. It doesn't have to do that. Recompute it. Sub agent one tool call sub agent call one is done.

**Speaker 1** [01:53:50]
Don't need to recompute. Now then it just can pick up from tool call two. And so imagine this is like a thousand steps. And I'll I'll tell you about a case study of a customer who had this type of very long running agent with many, many steps. So this is super important because at this gives you this, like, fine grained micro cache per run that if there are any network or system outages that you can just take for granted that your agents are gonna just gonna pick up from where it left off.

**Speaker 1** [01:54:26]
And this is similar to go global caching, but as opposed to this run run level replay log, global caching is, as the name suggests, is work shared across all agents and all agent runs. So in this case, you see an agent where I'm calling it with the same prompt, write a report about LLMs. It does a web search that in flight, you can say, I wanna cache that step. Does a DB read tool? I wanna cache that step.

**Speaker 1** [01:54:52]
But then I wanna disable it for the composer sub agent, which then synthesizes the outputs of the two previous tool calls. And so, you know, maybe the the AI builder says, I want to inject a little bit more creativity or entropy to that last step. And so each time I call it, I wanted to reuse the the research kind of deterministic tool calls, but then regenerate a new report each time. And finally, you have intermediate state persistence, which is the idea that you can just take for granted that once you use what I'm calling well, describe later as these functional durability hooks, these decorators you see on these functions that, you know, when you call the LLM the first time, the output of that agent state is stored just to object store in s three or something somewhere. Right?

**Speaker 1** [01:55:41]
So you just take it out for granted. You don't need to write any of your serialization, deserialization code. It's just there. You get data lineage just out of the box. Same with your first tool call.

**Speaker 1** [01:55:52]
Same with your second LLM call. So all of these under the hood in flight will be stored to your object store. So then those are the three building blocks that sort of unlock the implementation for these six design principles. And so I won't go through these line by line. I'll show you a little bit of code.

**Speaker 1** [01:56:16]
I'm not sure if you can read it too clearly, but the first one is to use plain Python. And the benefits of this, I think, are fairly obvious. You get loops, fan out, conditionals, try except, async synchronous programming in Python and whatever the equivalents are in whatever language you choose. There are no DSL surprises. There's nothing new to learn.

**Speaker 1** [01:56:38]
But if you do choose to use a framework, you can use it. Right? It's it's pretty straightforward. And this is a point I'll I'll hammer through the rest of this is that exceptions are actually a perfect delivery mechanism for critical context about failures at all layers of the stack. So this, you can squint and you can start to see, oh, what if I can catch an out of memory error here at this that the system actually bubbles up into my into flight.

**Speaker 1** [01:57:07]
Right? And leading to my next point, providing functional hooks make it really easy to add durability to your system, whatever implementation that you choose. Right? So assuming that you're using functions or whatever class methods that these hooks give you the ability to trace, checkpoint, and do the persistent intermediate state serialization and deserialization I mentioned earlier. And so in flight, the first thing you do is you define your task environment.

**Speaker 1** [01:57:41]
I'm mentioning this partly to show off flight, but partly to just show you how we're thinking about this type of problem. Right? So this allows you a task environment allows you to specify your container, your image, your dependencies, your resource requests. And tasks, you can think of as these containerized functions. These run on a Kubernetes pod.

**Speaker 1** [01:58:03]
These run on their own container. So agents running multiple of these tasks have container isolation. You get a lot of security benefits out of this as well. You give its own AIM role. You get a lot of nice downstream benefits of this.

**Speaker 1** [01:58:18]
And flight trace, you can think of as a helper function so that you don't have to pay the cost of spinning up a new container. This is just a helper function that gets you all of those persistence and crash proof guarantees that I mentioned earlier. This makes failures really cheap. So if you have an agent that writes code, that runs the code, and then finalizes the answer, and so this is our first iteration of an MLE agent, you have all the tracing and caching enabled to be able to have build an MLE agent that just has all of these crash proof guarantees built into it. And as an added bonus, failed runs become training data or additional context from the agent to learn from.

**Speaker 1** [01:59:05]
And not only is this an out of band process where you you know, query the flight database to grab all the failures and create a training dataset, you can actually react to them in line in your agent loop. And so this unlocks infrastructure as context. So this is where the agent can see things like out of memory errors, system level ephemeral outages, and retry based on those without, you know, totally crashing. So here, you can catch an out of memory error. You can have the agent respond to that and provision more resources based on the error in the code that it wrote and make adjustments that are sent back from in the for loop such that the the platform can provision more resources for, for example, in this case, a training job.

**Speaker 1** [01:59:59]
But not all fail

**Speaker 0** [02:00:00]
Be done in such a structured guardrail format. Right? So in this resource example, you're just outputting a dictionary of some predefined outputs and and values. What if you want the agent to orchestrate the actual tools in its tool belt? So this is there are two types of sandboxes I'll talk about.

**Speaker 0** [02:00:21]
There's a third one that we don't quite quite support yet, but code mode is something that I think Anthropic, the Anthropic team coined. This is where you replace all the context bloat associated with tools and formatting tool arguments and getting the results out of that. And you have the agent. You give it a a toolbox and say, write Python code that's sandboxed. So you can't do IO.

**Speaker 0** [02:00:47]
You can't do network calls. You can't do extra imports. You're writing pure function calls and conditionals in your code mode mode loop. Right? So the agent writes this pipeline.

**Speaker 0** [02:00:59]
The orchestrator can run this code generated by the agent securely in this limited subset of Python. Shout out to Pydantic Monty, by the way. I forgot to put it in my slide, but we're using that here. It's a cool project. Check it out.

**Speaker 0** [02:01:19]
And then you have this really tight error iteration loop to fix the orchestration code bugs. So you're you're, you know, you're no longer having to do an eval kind of out of band. Right? You could do that, of course, definitely, but you have the agent just fix its own errors. But sometimes you don't want just orchestration.

**Speaker 0** [02:01:40]
Right? So what if a user asks the agent something that for which a tool does just not just doesn't do the job? So that's where a stateless code sandbox is super useful. And so this is where you can introduce additional third party libraries. You can do imports.

**Speaker 0** [02:01:56]
You could do limited network IO. You could do limited readwrites on the file system. But so this stateless code sandbox is not that. So this is just a one shot. The agent writes the code.

**Speaker 0** [02:02:08]
It runs end to end and then produces some output. So it's it's kind of like a pure function. So this is what I just said. And you can even do cool things like have it write its own unit tests. Right?

**Speaker 0** [02:02:25]
So and then finally, there are a class of errors for which maybe the prompt is purely poorly formatted or the system prompt just doesn't work or there's just the agent just does not have the context it needs to solve the task. So human in the loop recourse is ultimate recourse to course correct an agent when it's kind of gone off the rails. So in this case, when the agent has exhausted its max iter budget, you can just have a very Pythonic way to say, hey, I need more context. And then in the UI, you can type in whatever additional context. You can upload a new file.

**Speaker 0** [02:03:08]
You can give it a zip file of a directory with more markdown files,

**Speaker 1** [02:03:13]
which is apparently how we do things now.

**Speaker 0** [02:03:18]
And then you recursively call the agent. So the flight supports recursion. There's a cleaner nonrecursion way of doing this, but I thought this was cool. So you basically call the agent function itself with the additional context. Right?

**Speaker 0** [02:03:33]
And this is the coolest slide because it has Wolverine on it. What you get out of all of these building blocks is an agent with a healing factor. Right? It's not perfect. It's still gonna fail.

**Speaker 0** [02:03:42]
It's still gonna fall over. But in this case, I don't expect you to read this, but this first error was an out of memory error. And then the red box there, it adjusted the sandbox resources. It gave itself more memory. In this error, it had an import for pandas that was not specified that it did not specify in its dependencies.

**Speaker 0** [02:04:04]
So then it writes more code. It updates its dependency structure and adds pandas. Then finally, for all those logical semantic tool execution failures, here's just a simple division by zero error. So that's error. It just you give it the error, and it fixes the the code.

**Speaker 0** [02:04:26]
And so I don't have much time left, but what does this look like in practice? We worked with a customer called Dragonfly who provides a basically, a a deep research SaaS product. So you go to them. You say, hey. I want a Jira like thing, but not Jira, and then they'll do research to figure out what stack you wanna use for your company.

**Speaker 0** [02:04:48]
Right? So their challenge was to build an automated solutions architect, an agent that creates a living knowledge graph of SaaS products. And so these were two fifty k or so software products. Each agent call had about 200 steps. Each product call each product had about a 100 LLM calls associated with it.

**Speaker 0** [02:05:11]
And so we help them with a kind of a tiered architecture. And so this is this is like scaling agents. Right? These are not the the agents you may be used to in very tight chat interfaces. These are agents that just run ambiently, that just power their database.

**Speaker 0** [02:05:29]
Right? So this thing will just run at some cadence and populate their database that powers their their SaaS product. And so at the top, you have the agent driver. So you have four replicas. You have research coordinators that have eight replicas.

**Speaker 0** [02:05:44]
You have underneath that 12 researchers, and yet underneath that are tool 12 replicas of a tool layer that each researcher has access to. And so we help them do cross run caching. Right? So this is a global cache I mentioned earlier. So they don't have to redouble pay for LLM API calls given the same research prompt.

**Speaker 0** [02:06:07]
They did this really cool thing that I need to learn more about, but it is basically some semantic conversions detect detection. So every once in a while, the coordinator layer would look at all the research threads they were spinning up. And based on some similarity semantic similarity, they would group and consolidate them so as to avoid duplicate work for their researchers. Checkpoint based recovery, this is what I talked about with the durability piece. They use spot instances heavily to reduce costs, and it became basically a nonissue.

**Speaker 0** [02:06:38]
Spot instances would go away. They would come back a few seconds later, and you wouldn't lose any progress. And you have full auditability. Every single LLM call or every single tool call is traced. And so the result is I actually onboarded them, so I helped them.

**Speaker 0** [02:06:56]
And within an hour, they onboarded their local BAML agent prototype into production in about an hour. And this got them two two thousand plus concurrent runs, and the onboarding was really because it was just Python. Just like, here's the task config. Here's the decorators. Just go.

**Speaker 0** [02:07:13]
Do your thing. Reduce their recovery failure recovery time by 50%, increase their development velocity by 30%, and they save twelve hours a week on infrastructure maintenance because of this. So in conclusion, if you're an agent builder or starting to build agents, do yourself a favor and your agents a favor. Consider that observability is necessary but not sufficient. Durability helps agents recover quickly.

**Speaker 0** [02:07:43]
Don't aim for failure proof. Aim for cheap failures, fast recovery, and a very tight, quick agent loop feedback. Think about infrastructure as context. So when you begin, you're starting probably with a single node, but when you start scaling out, this you're gonna start feeling this pain. And secure sandboxes facilitate self healing in that in the inner loop, the agent can fix bugs and build itself new tools as needed.

**Speaker 0** [02:08:10]
Help your agents help themselves. Thank you.

**Speaker 1** [02:08:17]
We got time for a question? Who's got a question around here? Anybody? Let's see. Let's see.

**Speaker 0** [02:08:26]
I think people are hungry.

**Speaker 1** [02:08:28]
We got one over here.

**Speaker 2** [02:08:35]
Wondering if you've, got got an opinion on what the right size and number of agent tiers are. You you showed an example of four tiers. Is that typical? Or

**Speaker 0** [02:08:48]
That was special just because they they had a pretty scaled out use case. Like and so as you saw, it was, like, 200 steps, a 100 a 100 LLM calls per software product. And that's nondeterministic too. Like, for any given prompt high level prompt to populate a particular SaaS product, you don't know how many research threads are gonna happen. Right?

**Speaker 0** [02:09:14]
So I think that from my experience, at least, that's kind of like the upper limit of scale that I've seen so far. Generally, it's just an agent and a subagent. Like, I wouldn't go generally deeper than that. And even then, just one agent with a bunch

**Speaker 1** [02:09:28]
of tools. Like, I feel like that's

**Speaker 0** [02:09:30]
for for at least the internal use cases we've built, that works really well, especially if there are, like, the butter robot. They just do one the one thing, and they just do that one thing. Right? But if you're doing deep research and you're you have, like, this coordinator layer, and and I think they arrived at that solution because they were finding a lot of duplicate research threads. And so that, you know, they implemented that semantic convergence algorithm.

**Speaker 0** [02:09:58]
Yeah. But, generally, I just start with one and then one sub agent layer of sub agents. So the sub agents can do different things. Right? Yeah.

**Speaker 1** [02:10:09]
Excellent. Let's give one more round of applause for Niels.

**Speaker 0** [02:10:13]
Thank you.

**Speaker 1** [02:10:13]
Thank you, dude. Yeah. Cheers, man.

**Speaker 0** [02:10:16]
Yeah. Thanks. Don't leave us here?

**Speaker 1** [02:10:18]
No. Alright, folks. Go eat. We'll be back here at around two, I think. You should have the agendas.

**Speaker 1** [02:10:25]
You probably know better than I do. Enjoy. Hopefully, you make some new friends. You munch your lunch with a new bunch. I don't wanna see anybody eating with anybody they already know.

**Speaker 1** [02:10:34]
Alright? So we'll be reconvened back here. And yeah. The link with everyone in the company because they were streaming it in live.

**Speaker 0** [02:10:42]
Oh, nice. Oh, cool. Nice.

**Speaker 0** [03:11:53]
Alright. You all were wild enough to join this session that you don't know what it's about at all. I'm sure you're sitting here, and you're like, oh, there's a session now? What? So here the thing that we're gonna do, and it's only gonna work if we get participation.

**Speaker 0** [03:12:12]
So please don't leave me hanging. And we can't do that trick where it's like, you expect the other person to do it, so you don't do it. You know, there's some psychological, thing. I can't remember what it's called, but we're screwed if you do that. Alright?

**Speaker 0** [03:12:27]
We need you to scan this here QR code. That's step one. Scan the QR code, and it should take you to a question. And this is the whole reason we're doing this session is because folks wanted a chance to share what's been working with them, and it's less me talking at you and us talking together. So there's one question there.

**Speaker 0** [03:12:54]
You should see it by now. It says what does it say? It says what what's your best tip for using coding agents? So now we'll take five seconds, ten seconds. I'll tell you a little joke.

**Speaker 0** [03:13:12]
By the time that it's done, you should have put your best tip in there, and you should also be upvoting everybody else's tips. Whoever has the most upvotes comes on stage, and they defend or they explain what their tip is. Okay? So while you are doing that, here's my joke. Let's see how this goes.

**Speaker 0** [03:13:39]
Set the expectations very low. Let's just bring them down beforehand. So I was playing with Claude code the other day, and I said, Claude, choose a random number between one and fifty. And it said 32. And I went, that's it.

**Speaker 0** [03:14:00]
For the next thirty two days, I'm not gonna talk to you. I'm not gonna engage with you. I'm not gonna do anything with you. Thirty two days, cold turkey, nothing. And it said, can I choose another number?

**Speaker 0** [03:14:12]
And I went, oh, that's so sweet. Of course, you can. Yeah. Go for it. And then it replied, and it said, 50.

**Speaker 0** [03:14:22]
So there's my there's my joke. Alright. Where's the upvotes? Do we get any upvotes or not? Yes?

**Speaker 0** [03:14:31]
Yeah? Upvotes? We got one upvote, two upvotes, three upvotes. Here we go. So, hopefully, it filters with upvotes, and we can see which ones are voted the most.

**Speaker 0** [03:14:46]
And then we'll have whoever that is come on stage, and let's just see what we've got so far. Get your agent to create a screenshot walk through of every feature and then have it review changes before every oh. Ask it to first understand the code base and fill the context window. I like that too. Alright.

**Speaker 0** [03:15:08]
Create an entire workflow for the software development life cycle starting with project manager to architect to coding and QA. It can run sub agents and have them so that's good. I just don't know what that would mean in practice. Do centaur reviews. What's a centaur?

**Speaker 0** [03:15:24]
The human in machine or human in horse? The AI directs a human to pay attention to the most important things. Mhmm. Alright. Where we at?

**Speaker 0** [03:15:35]
Which ones have the most upvotes so far? Is there a way to scroll on this or no? Can we scroll? Is there so now would be the time to drop in as many upvotes as you want. What's your best tip?

**Speaker 0** [03:15:53]
Long term memory. And that gets oh, here we go. Here's a clear winner. Always start out with a plan. Who did this one?

**Speaker 0** [03:15:59]
Who is it? Get up here and explain yourself. Here we go. What do you mean by this? I'll go You're coming up all the way.

**Speaker 0** [03:16:08]
Actually, you can be right here, and then we can interact. You can use this.

**Speaker 1** [03:16:12]
Oh, okay.

**Speaker 0** [03:16:13]
Alright. Rafael.

**Speaker 1** [03:16:14]
I'm Rafael. Basically, everybody's talking about how, like, this last December was the advent of, like, AI agents, but it was really the year before. And if you have been using, like, plan dot MD files, just planning out your code, what you want the agent to do before actually having a code, you could still you could have been getting the results that you that we're getting this year. I'm an older developer, and all the developers know, remember when you had to plan out your code because you had to wait to compile and all that stuff. So when people are just, like, vibe coding and, you know, expecting the LLMs to do everything correctly, that's just not gonna work.

**Speaker 1** [03:16:52]
But if you always plan whatever you do, coding, life, whatever, if you plan, you will always be more successful.

**Speaker 0** [03:16:59]
Hey, Thank you. Alright. We'll take it. Any questions for Rafael before he goes back to his seat? Anybody?

**Speaker 0** [03:17:06]
The planning? Plan mode? I'm gonna start doing that. I do have a little bit of a question there is if you can tell me what you add in the plan. Anything specific?

**Speaker 1** [03:17:18]
So I actually always have a a two part structure. First of all, you want your plan to be clear, actionable with code snippets. So have the agent code out or, like, write out the code in the plan dot m d. That makes it a lot more accurate. But, also, add an executive summary because AI can just write a shit ton of stuff for you.

**Speaker 0** [03:17:42]
Mhmm.

**Speaker 1** [03:17:42]
It can write out a shit ton of stuff for you that you don't wanna read. But if you have it, write an executive summary at the top. It will tell you everything that you need to know, and you don't have to

**Speaker 0** [03:17:51]
read the

**Speaker 2** [03:17:51]
rest of the stuff.

**Speaker 0** [03:17:52]
Alright. I like it. Thanks, Rafael. Let's keep it rocking. Now would be the time to add more upvotes.

**Speaker 0** [03:18:01]
Where are we at? What else do we got here? Can we can't filter by upvotes, can we? That might be too much too much. I know there were some fire ones below.

**Speaker 0** [03:18:10]
If we go, it's okay. I don't wanna put you on the spot. We got one. Use Brumi. Alright.

**Speaker 0** [03:18:18]
But where else? Do you Rob, you wanna come talk about Brumi? Alright. Get up here. We got one upvote here.

**Speaker 0** [03:18:24]
And then there's plan early, plan often. I think that goes with Rafael's. Plan early, plan often. I would like the continuous life cycle of that, though. Alright.

**Speaker 0** [03:18:34]
Broomy, what is it?

**Speaker 3** [03:18:35]
You mentioned when talking earlier

**Speaker 0** [03:18:37]
You gotta you gotta talk into that.

**Speaker 3** [03:18:39]
You mentioned when talking earlier that working with parallel agents is often a pain if you're using regular tools. I agree. It is normally a pain. I've built an open source project called broomy.org. That's like broomy sweep with a y at the end.

**Speaker 3** [03:18:52]
It makes it super easy to work with lots of agents at once. It creates work trees for you. It works with all the major agents. You can see for all your agents when they're working, when they're blocked, when they're asking you for help, and it automates things like having them do mergers, having the right pull request, having them review stuff. So all your flows get pretty easy.

**Speaker 0** [03:19:11]
Oh, I like it. And you know I'm a fan. Yep. Any questions for Rob and Brumi? Anything about parallel agents?

**Speaker 0** [03:19:19]
Alright. I know some people might have just come in. So if you don't have access to this, slide that scan that QR code up there. Thanks, Rob, for this. Thank you for talking about Broomy.

**Speaker 0** [03:19:31]
I appreciate it. Can we keep scrolling through this and see what else we got? What was that? The biggest trip trick is dangerously skip permissions every time. Here we go.

**Speaker 0** [03:19:42]
Get agents to record all design decisions in design folders. So feel free. We need upvotes right now. Upvote so we can know which ones we want to get on here, or drop in your best trick, and we will have it there. Why Centaura not Robocop?

**Speaker 0** [03:20:00]
I don't know what this means. You gotta be a I'm like the agent with no context right now. Alright? So get your agent I like this one. Who did this one?

**Speaker 0** [03:20:11]
Get your agent to create screenshot walk throughs of every feature and then have it review changes. Who was this? Oh, get over here. Get back up here. Tell us more.

**Speaker 0** [03:20:22]
Tell us more. You all remember Rob?

**Speaker 3** [03:20:25]
This this this one's super powerful. This is what I use in multiple projects. So, like, if you go to manual QA to see if your agents broke stuff, that's going be such a bottleneck. What you can do is just have as part of your instructions to your agents that whenever it does any kind of user facing change, it creates a sequence of screen shots with a textual walkthrough, say all the flows which were affected and what's supposed to happen. And then the cool thing is that when you do your next release as part of the process, it replays all those screen shots at the last release and the next release snapshot.

**Speaker 3** [03:21:00]
It looks at every screenshot that changed. It analyzes what's expected to change based on the PRs that were merged, and it highlights for user a prototype set of things for human review. This is a major accelerant.

**Speaker 0** [03:21:14]
But the screenshots are only in the context window, or also you're putting them into Git or what?

**Speaker 3** [03:21:18]
The screenshots go that those dev files, they don't go into Git because it can regenerate them. Uh-huh. So during the release process, you jump back to the last release for checkout. You run the the scripts from Playwright to generate all those screenshots. Then you jump right forward to the new release tag.

**Speaker 3** [03:21:35]
You generate them again. You do a pixel diff. For everyone that differs, you get another sub agent to say, okay. This screenshot, this is a is this a thing you'd expect to happen based interpreting the images and and the the intents of the things? And then based on that, it prioritizes which are high risk, low risk, for for human reviewer.

**Speaker 3** [03:21:53]
Massive accelerant.

**Speaker 0** [03:21:55]
Doesn't that slow down your CI

**Speaker 4** [03:21:56]
a lot, though?

**Speaker 0** [03:21:57]
Slow down the CI?

**Speaker 3** [03:21:58]
I don't do it in CI. I do it in a in a separate build box. It it's it's really slow. You just do it for release. You don't you cannot do this in PR merge.

**Speaker 3** [03:22:07]
It's way too slow. Just do just do it on release.

**Speaker 0** [03:22:12]
This is exactly why I wanted to have this session because that right there is a nugget of gold that I'm going to take home, and I appreciate you. Alright. Rob, awesome. Yeah. Whoo.

**Speaker 0** [03:22:22]
That's right. Did you put any other ones in? You wanna just come defend them while you before you come back down? Yeah. You did put a few more, or do they have fire emojis by them?

**Speaker 0** [03:22:35]
Let's see. What else what was the other one?

**Speaker 3** [03:22:38]
Yeah.

**Speaker 0** [03:22:42]
Come over here. Get over you guys remember Rob. Right?

**Speaker 3** [03:22:46]
Always run your agent in a container because if you run-in a container, you can do dangerously skip permissions, it's not dangerous. If you've got approval, you're a tool use. That's real hell. It's gonna really slow you down.

**Speaker 0** [03:22:57]
Awesome. I guess I

**Speaker 4** [03:22:59]
have something for that one.

**Speaker 0** [03:23:00]
Alright. Get up here. Thank you, Rob. That was a blessing right there. I appreciate that.

**Speaker 0** [03:23:08]
What's your name? Where are calling in from?

**Speaker 4** [03:23:10]
Yari from calling from San Diego Picnic Health. Nice. But, yeah, we you know, like everybody here probably had the same problem of, like, yeah, the permission stuff gets really annoy really annoying really fast. And most of the time, you're like, find yourself, like, approving the same things. And then with the latest model, it got really good at coding things.

**Speaker 0** [03:23:26]
But then

**Speaker 4** [03:23:26]
every one of those is a new script, and it's means a new prompt, and you can't preapprove them. So added a hook into the approval process. And if it was if it passed the regular checks, it would be prompted. And then that would fire off a LLM call with a specific prompt around kind of the things that we wanted to look for, like dangerous things. And then it would if it felt like this was the safe change, it would actually approve it.

**Speaker 4** [03:23:51]
And so you you know, as a user, you would see it briefly ask, and then it would be like approved, and then it would just go. So you could just go walk away and and and the other thing that it would do is also learn from itself. So it would list keep a list of history of what you've approved and then Nice. Kinda learn from that go, oh, they're approving this. So it must be okay for this session.

**Speaker 4** [03:24:09]
And you could make that session specific or, you know, be broader and have it be specific to you complete, like, across your sessions.

**Speaker 0** [03:24:17]
Nice. So let me just make sure I understand this correctly. You add the hook right before every, like, asking for permission.

**Speaker 3** [03:24:26]
Yep.

**Speaker 0** [03:24:26]
And then

**Speaker 4** [03:24:28]
So that calls and that basically runs a prompt passing the

**Speaker 0** [03:24:32]
That's it.

**Speaker 4** [03:24:33]
Command that you're trying to run to an LLM, which has, like, other guidance around it, like, you know, evaluate it for dangerous stuff, like

**Speaker 0** [03:24:40]
Make sure you're not leaking secrets.

**Speaker 4** [03:24:42]
Writing into our production database, you know, make sure you prompt the user, things like that. And then it does a, you know, quick evaluation and then comes right back and approves it.

**Speaker 0** [03:24:50]
Awesome.

**Speaker 4** [03:24:51]
Yeah. So that that's been huge. Questions?

**Speaker 0** [03:24:55]
Questions here? No? That's great, man. I appreciate that. Alright.

**Speaker 0** [03:25:00]
What else do we got here? Who else has got some spicy stuff? Can we keep scrolling down maybe? Use them or use agents, interact, work with agents until you get code you want. Teach it.

**Speaker 0** [03:25:14]
Yeah. There was one that I saw about the context asking it to review the I don't know where it is, but asking it to review the code base and then put that in the context. Who was that? Rob, it better not be you. Better not have been you.

**Speaker 0** [03:25:29]
Was it you? No. No? Alright. Who was that?

**Speaker 0** [03:25:32]
Did they leave? Can't hold their attention. Where Claude Max Plan is 10 times cheap cheaper using than using the API. Yes. That actually I have found that.

**Speaker 0** [03:25:46]
Yeah. We've all found that. Alright. That's not a big of a hot take. Okay.

**Speaker 0** [03:25:50]
But that is true. Use hooks. Whose is this? Use hooks to force limiting, commits, tests, and correctness? Get on up here.

**Speaker 0** [03:26:00]
You know what time it is. Oh, scrap and restart. Yep. I've learned that. Clear the context.

**Speaker 0** [03:26:08]
Okay. So hooks are one that I just haven't played with enough. I like this use case. I like this use case, so enlighten me. What's your name?

**Speaker 0** [03:26:19]
Where are you calling in from?

**Speaker 2** [03:26:20]
Yeah. My name is Josh. I am from East Bay here near Berkeley. So, yeah, I think if you're using Cloud Code, I don't know if, you know, other things like OpenCode or Codecs have this, but, you know, basically, you have life cycle hooks that let you run scripts or, you know, follow text instructions at various points when it's doing things. So, you know, I don't know about you, but often, if I have an agent working on a task, it might quit early or it might try to forego even if I put in my, you know, agent.md or cloud.md, like, ensure your lint rules all pass, ensure that, you know, your TypeScript compiles, ensure your tests all pass.

**Speaker 2** [03:27:13]
It will not do that, but you can use hooks to actually enforce this. You can also have it, like, play sounds, send off notifications to devices. Just digging into that really helps your workflow a lot. I also said don't be afraid to scrap and restart.

**Speaker 0** [03:27:28]
That was

**Speaker 2** [03:27:28]
both in terms of context clearing. I think, like, more context is not always better. You start seeing that, like, it doesn't know it has no inherent sense of what is more important. So having more information can lead to less focus. So don't be afraid for that.

**Speaker 2** [03:27:47]
But also, like, if you're working on a feature and it's just, like, not working, sometimes just, like, starting over and not being afraid to just, like, lose that code in progress because it's so cheap to start again is way better.

**Speaker 0** [03:28:00]
Yes. Wait. Wait. Don't go anywhere. There's some questions.

**Speaker 1** [03:28:03]
Yeah. I was just gonna ask that. If you put your context in the plan file, you can just erase your

**Speaker 0** [03:28:09]
extension. Exactly.

**Speaker 2** [03:28:11]
And I think keep, like make sure your plan file also has your updated tasks. I guess like Claude now tracks tasks. But I think having it written in a document so you can go between agents and, you know, self observe what's going on rather than having like to ask the agent itself where it is in its list of tasks is easier.

**Speaker 0** [03:28:32]
So the TLDR of the hooks are that you use them to really enforce what you really want to happen?

**Speaker 2** [03:28:41]
Yeah. Absolutely. So, yeah, if you need your you wanna make sure your tests are running or even just, like, you start, you give a prompt that has really clear success criteria, you can force it to do that. I think also, like, if you have a certain set of tests that it cannot alter because it likes to, you know, proceed even if that means deleting or changing the test, like, you know, have a criteria like you're not stopping until this happens or, you know, what have you.

**Speaker 0** [03:29:09]
Excellent. Well, thank you for that. Alright. It looks like we've got another one. Put your plan in plan MD rather than plan mode.

**Speaker 0** [03:29:16]
Was this you, Rafa? Alright. Get up here, Rob. Go on. What is this about?

**Speaker 0** [03:29:25]
Just sit closer next time.

**Speaker 3** [03:29:27]
This one helps a lot.

**Speaker 0** [03:29:29]
Rob. You all remember Rob. Right?

**Speaker 3** [03:29:31]
Here we go. This one helps a lot. So if you use a standard Claude code plan mode, one, it like shows it in an already awkward way in the terminal. Two, it's like hard to discuss it in as good a way. And if not, can quit as the repo.

**Speaker 3** [03:29:45]
It's awkward in lots of ways. You can just tell it to write its plan as a plan dot md file. Then you can view it and scroll it around nicely in markdown. You can discuss Patlcos and forwards edits to it. You can commit it.

**Speaker 3** [03:29:58]
It just tends to work a lot better. And if you're using Broomy, it automatically shows the plan dot m d in a nice UI.

**Speaker 0** [03:30:05]
So you're specifically saying to it always, or is that a skill that you've created that, like, whenever it's in plan mode, transfer everything to a plan?

**Speaker 3** [03:30:14]
So, basically, rather rather than switching to plan mode, just tell Claude, write a plan to. It directly writes the plan. Basically, it works as if plan mode, but does it as a file.

**Speaker 0** [03:30:24]
Yeah. I see. That's cool.

**Speaker 3** [03:30:26]
It's it's much easier to edit it and discuss it and view it.

**Speaker 0** [03:30:29]
I like that. Alright. What else do we got? And folks that just came in, this is an interactive session, so feel free to scan that bad boy right there. Give us your best tip for using coding agents because we're it's we wanna learn from each other.

**Speaker 0** [03:30:47]
Basically, we're learning from Rob today a lot. So hit hit that. Take a minute, and tell us what is your best tip. What tips do you got? In the meantime, let's scan through and see if we have anything new that is coming.

**Speaker 0** [03:31:06]
Yeah. I really like that one about scrapping and restarting on the actual feature. That is a cool one. What else? Starting project and defining use voice.

**Speaker 0** [03:31:18]
Okay. Who's this? Who's this one? The voice dictation. I've been all about that.

**Speaker 0** [03:31:25]
Get on up here. I I see that learn TMUX. If you haven't already, is that you, Rob? No. It's not.

**Speaker 0** [03:31:32]
Who was that? Was it you, Rafa? TMUX? No? Who was the TMUX?

**Speaker 0** [03:31:39]
It is good. Alright. So?

**Speaker 2** [03:31:42]
So I think we have this tendency to think, like, we we when you're typing, you go slower. You have more polish to your communication. And I think when you're doing some parts of agentic coding, like that clear direct instruction is useful. But when you are first figuring out what your project is, what your specs are, just doing a free flow dictation that is imperfect, like, one, the LLMs are really good at summarizing and putting finding connections between what you're talking about. But I think also, like, a lot of what you're building is like we're very bad at defining intent.

**Speaker 2** [03:32:20]
If we could just, like, describe products well, inspect them well, you know, we wouldn't have jobs, really, honestly. Yeah. And, like, everyone could just do this stuff. But that's really hard, and I think you get a lot of intent by just speaking freely and having that get summarized. So when you're in that planning stage, I think rambling is good and beneficial.

**Speaker 0** [03:32:44]
I am on the same page a 100% because when you're in when you're speaking with your voice, you just don't even realize it, but you give so much more context. I've noticed that even with, like, externally facing agents. So if you want a actual agent that is for users, same thing. If you can get it with voice and you need that context, you'll get it. Can I ask a follow-up for you?

**Speaker 0** [03:33:06]
Yeah. Of course. That's what we're here for.

**Speaker 5** [03:33:08]
What what what tooling do you use?

**Speaker 0** [03:33:10]
What tooling do you use?

**Speaker 2** [03:33:12]
I use WhisperFlow, and it's pretty good. I think it's always I I usually just, like, you know, hold down whatever your shortcut key is to dictate, and then it just goes into whatever text box. So if I'm using Cloud Code, it just, like, pops in there. It's I use VIM mode then because inevitably, like, some word is misspelled or, like, especially, like, proper nouns and context can get off a little bit. So it's, like, much faster to edit, for me at least, in VIM mode rather than having to just, like, use arrow keys indefinitely.

**Speaker 0** [03:33:46]
But Yeah.

**Speaker 2** [03:33:47]
Yeah. Use TMUX in VIM mode.

**Speaker 5** [03:33:50]
Do you find yourself editing your speech?

**Speaker 4** [03:33:52]
Or you, like

**Speaker 0** [03:33:53]
Do you edit your speech?

**Speaker 2** [03:33:54]
Yeah. I I I'm I

**Speaker 5** [03:33:55]
just would be worried that I'd be, like, constantly, like, self judging the words just like

**Speaker 4** [03:34:00]
I self judge the keys.

**Speaker 2** [03:34:02]
Well, I think that's the thing. That's

**Speaker 0** [03:34:03]
wild. Yeah.

**Speaker 2** [03:34:04]
I like, getting out of the habit of doing that, like, using it and seeing that it doesn't matter. Like, also, like Yep. At least right now, your LLM is only judging you if you send it off onto MoltBook. So, you know, like, who cares? Like, if you're a little bit dumb, that's fine.

**Speaker 2** [03:34:22]
Like, I think it's a feature, not a bug that you can speak freely to it. You don't have to worry about, you know, judgment or what you say, and then it, like, responds, and you can correct it afterwards.

**Speaker 0** [03:34:34]
Yeah. I I agree. Highly recommended. Alright. That's a great hack.

**Speaker 0** [03:34:39]
Use voice mode, especially when starting. Thank you, sir. What else do we got? For the people that just came in, I see some new faces. Scan that QR code.

**Speaker 0** [03:34:51]
Give us your best trick. Can we scroll up and see what else? And now if you've already given your best trick, now it's time to upvote so we know which ones we should have come on stage. Who likes what? Have Claude update all your MD files.

**Speaker 0** [03:35:06]
No need to write any instructions yourself. Get Claude to do hold on. Get Claude to do product design research. Who's that? Who's no.

**Speaker 0** [03:35:16]
Fuck off, Rob. Are you serious? What the hell, man? Come on. Good lord.

**Speaker 0** [03:35:24]
Somebody upvote something else besides Rob's. Alright.

**Speaker 3** [03:35:29]
This one's really powerful. If you're trying to work out what to do in your product, how to solve a problem, Claude code isn't just good at, like, writing code. Just give it a big open ended thing. Say, research what the competitors are doing. Research what you know about user behavior.

**Speaker 3** [03:35:42]
Really delve into the datasets and come up with a good proposal. And, often, it does a really good job of just working out what you should do.

**Speaker 0** [03:35:49]
Wow. So you're just telling it when you're starting out a feature or when you're starting a product? Like, how big of a scope can you give it?

**Speaker 3** [03:35:57]
It can be pretty big. Just give it a big wide open question and tell it to do a ton of research. I will warn you, though, this can really, really flaunt your tokens. Because if it's reading a ton of websites and ton of data sets, reading a ton of papers, it'll often use a lot of con use a lot of context and a lot of tokens to do it, but it can do a really good job. You you get some surprising insights you hadn't thought of.

**Speaker 3** [03:36:18]
You'll resell, like, it'll research your customers about their history and their org charts and all the different people and what they want. Wow. Or research where your competitors and work at what they're doing, what their weaknesses are.

**Speaker 0** [03:36:28]
And you're not specifically calling that out, like, research this my competitors and give me their org charts?

**Speaker 3** [03:36:34]
You you given us that are, like, open questions and let it run.

**Speaker 0** [03:36:38]
Uh-huh.

**Speaker 3** [03:36:39]
But, like, it can do a really good job with this.

**Speaker 0** [03:36:41]
And you're not saying, like, make sure to remember to check archive papers or that stuff. You just are saying, go for it.

**Speaker 3** [03:36:49]
There's there's advantages in throwing some questions in there, but the way I recommend doing this, do it as a brain dump. Let's say imagine you had a team of a 100 researchers. Just write all the open all questions you've got, like, what do my customers want? What's their history? Who are the key key people?

**Speaker 3** [03:37:04]
What do they want? What's the history? What what do users want? What challenges are like you facing? Just spin out another question, stream of consciousness style, and tell it to do the research and assemble you something.

**Speaker 0** [03:37:13]
I like it. Alright, Rob. I get the feeling this isn't the last time I'm gonna see you. So and whose is this? You can make expert skills about whatever you want.

**Speaker 0** [03:37:25]
Hey, Rafa. Get back up here. For folks that are not participating, it is much more fun when you do. So feel free to scan that QR code and give us your best tip. The the idea here is we wanna have, we wanna learn from each other.

**Speaker 0** [03:37:44]
Alright, Rafa. What you got?

**Speaker 1** [03:37:46]
Yeah. So one of the things that I keep forgetting about context engineering the way that I use context engineering is to put rails on what I want my agent to do. So I will write a plan that MD file to be like, okay. This is exactly what you need to do. But another part about context engineering is priming the agent.

**Speaker 1** [03:38:03]
So, the LLMs are trained with, like, almost everything on the Internet. Like, they already have a universe of information. So you can use skills to prime the the LLMs to give you that expert information that's already in there. So if you take a look at the front end design skill that cloud provides, I thought it was going to be, like, a bunch of guidelines about how to design correctly, etcetera. No.

**Speaker 1** [03:38:29]
But it's only, like, 40 lines that says, say, you are an expert designer, that doesn't use tacky AI designs or something like that. It's just very simple. So you can make yourself a skill about whatever you need to research or understand. Like, if you wanna understand trademarks or how to go to market or, you know, how to be a PM or, like, something out there in the world. The LLMs are already trained on that information, you can just make yourself skills about whatever you want.

**Speaker 0** [03:38:56]
That's cool. Yeah. Okay. So it's like just landing in latent space. The skill is how to make it locate itself.

**Speaker 1** [03:39:06]
Yeah. The LLMs already know how to do whatever a human does whatever a human does. So you just need to

**Speaker 0** [03:39:13]
prime it. Questions for Rafa? Are we gonna let him go back to his seat?

**Speaker 1** [03:39:17]
Alright.

**Speaker 0** [03:39:18]
Hey. There we go. What else do we got? Question. Oh, we got a question back here.

**Speaker 0** [03:39:24]
Hit us. Why do

**Speaker 6** [03:39:26]
you need to make a already knows how to

**Speaker 2** [03:39:29]
do it?

**Speaker 0** [03:39:29]
Why do you need to make a skill if it already knows?

**Speaker 1** [03:39:32]
Skills skills are a really nice reusable abstraction. That's why. If you go back to the days of prompt engineering, like, you could always do, like, you are an expert designer or you are blah blah blah blah blah, and it will your response will be primed with that context. But if if this is something that you use a lot, that's what skills are for. It's like your way to make yourself a literal reusable expert.

**Speaker 1** [03:40:00]
So in my own workflow, I just have a bunch of different experts. And as I'm going through, like, my day to day and if I have, like, different kinds of questions, etcetera, like, I'll just use a skill to ask the expert in that area. And so it's just the reusability. Like, that's the value of adding the skill.

**Speaker 0** [03:40:18]
Brilliant. Good. Satisfactory. Oh, I Alright. Kinda,

**Speaker 6** [03:40:27]
though.

**Speaker 4** [03:40:38]
Yeah.

**Speaker 0** [03:40:44]
Uh-huh.

**Speaker 1** [03:40:45]
Yeah. And I wasn't a believer in skills, but it's the reusability aspect of it that I that I really use now.

**Speaker 0** [03:40:55]
I like this. I felt like we just had a nice Volley there. Let's keep that up. So there's one that's that was just down. Can I see that again?

**Speaker 0** [03:41:05]
If you build off a new code base, use well executed open source projects to get design prompts. Whose was this? Well, get on up here again. That is a good one. And then we've got the rebuttal, I think, to Rob's, unless this was yours, Rob, if we scroll up.

**Speaker 0** [03:41:27]
But in the meantime, tell us.

**Speaker 2** [03:41:29]
So I think, like, especially, like, I often build things that have less common good use cases or, like, if I'm building, like, web audio stuff or, like, music applications, if I don't give it anything to work off of well, like there's a bunch of timing stuff, anything that's nuanced, if you know that there's already an open source code base that does this stuff well, build a skill. Or even just like when you're building out your architecture, like you can ask it to analyze someone else's code base to come up with that stuff. So that way, you get to build things in areas you're not yet an expert in and, you know, get a little bit of a head start.

**Speaker 0** [03:42:10]
Hell, yeah. I love that. Any questions? Anything? That is awesome.

**Speaker 0** [03:42:16]
There's so many tricks now that I'm gonna have to I'm glad we're recording this because I'm gonna have to remember them by watching the video later. Okay. What do we got? Tell the agent to add documentation comment to the top of every file, a good read me to every folder, and make sure it stays up to date. Who's that?

**Speaker 0** [03:42:36]
No. You gotta be joking, man. Stop, bro. I'm telling you, it's more fun when you participate. Look how much fun Rob is having over here.

**Speaker 0** [03:42:47]
And you can use those.

**Speaker 3** [03:42:50]
This one's a killer. Like, if you want your agents to understand the code base, the code base needs to be understandable, particularly if it's like using a Gen six cert to find where stuff is. So it's really valuable to have agents read every file one at a time, make sure each one has a documentation comment at the top, really explaining how it works and how it connects to other files. And suddenly, have a read me for each folder saying what all the files are in there and how they work because then the agent can work out how your code works. Yeah.

**Speaker 3** [03:43:18]
And if humans do this, it's not viable because humans don't keep yourself up to date. Yeah. Agents do because just tell them to with a hook.

**Speaker 0** [03:43:24]
Are you making sure that you're saying always update the read me in in the prompt?

**Speaker 3** [03:43:30]
The way I do it is I've got a validation skill that it does at the end of everything it commits. And so one of the things it has to do as part of validating its work is make sure the documentation comments are up to date.

**Speaker 0** [03:43:41]
Oh, awesome. Okay. Alright. What else do we got? Wait.

**Speaker 0** [03:43:46]
Whose was this? Use deep research products like Parallel or ChatGee. Hey. We got somebody new. This was this is similar to what you were talking about, Rob, but it's a little bit it's how to do that but save money so you don't just burn through all your tokens, I guess.

**Speaker 0** [03:44:02]
Get on up here. We got a new contestant. Fresh blood. Hey. Alright.

**Speaker 0** [03:44:11]
Tell us your name and where you're calling in from.

**Speaker 7** [03:44:15]
So I'm Omeh. I'm local. I've used this trick with Claude, the product research thing that you mentioned, especially with Opus 4.6, just the tokens get out of budget very quickly. There's this meme of Pablo Escobar, the sad meme from Narcos show that people have seen probably. Whenever you get rate limited, that's how I feel these days where you just don't know anything to do.

**Speaker 7** [03:44:38]
So I typically use, and I have no allegiance to perplexity or charge GBD, but I do use them to do deep research, construct a plan, and then give that plan to Claude, and that does allow me to overcome. So I'd recommend to give that a shot. I have one other shout out or comment on the

**Speaker 0** [03:44:56]
previous We're not going

**Speaker 3** [03:44:57]
to complain.

**Speaker 7** [03:44:57]
Again, no allegiance here, but Devon, has a really cool feature where if you're using back end, it'll actually produce UI screenshots and even videos of how the change is gonna look like. And you can actually look at it before even approving PRs. And I would wish, like, somebody like Claude Court would eventually add that feature because it does help in just visualizing how something is getting built in real time.

**Speaker 0** [03:45:22]
Should have been here earlier. Rob was talking about that and how that works. That that's awesome. Well, thank you. What else do we got?

**Speaker 0** [03:45:29]
I think we have one more. Also, Christina, Mikael is here for the workshop. He just texted me, so we might need to find him. Alright. Oh, I did like this one.

**Speaker 0** [03:45:41]
What was although if it is one of the three people that have already been up here all day, the bug tracker. Whose was this? No. Alright. We're done.

**Speaker 0** [03:45:49]
We're not doing that. Let's get somebody else up here. Did anyone else put any other trick? Anybody? Something.

**Speaker 0** [03:45:57]
No? What what trick? Get up here. Tell us about your trick. We're trying to spread the love.

**Speaker 0** [03:46:03]
What do you got for us? There we go. New newcomer coming through. Tell us your name. Where are calling in from?

**Speaker 8** [03:46:12]
Chad, longtime listener, first time caller. This is really basic, and there's, like, refining your plans and refining your specs. There's tons of things to do that. There's, like, VMAD and Cloudflow and whatever else, but I do a really simple thing. I'm like, okay.

**Speaker 8** [03:46:31]
I've got the seed of whatever of a plan or a spec or something to start with, and then I have one or more agents. Just it's a skill that says, critique this, and then write it like my plan is plan v one, and then it's like critique opus v one. Critique GPT v one, or whatever model or critique human if it's something I wrote. And then I have a revised skill that reads those, and it says, okay. And they'll they'll always find new things.

**Speaker 8** [03:47:07]
And then there's a revised skill that reads those and says, okay. I'm gonna update the plan, make a v two, and then I'm gonna write an acknowledgment v one acknowledgment v one for all of the ones. And then you just repeat that. And for simple things, it'll sort of resolve and say, no. This is good.

**Speaker 8** [03:47:25]
I don't find anything else. For bigger things, it will go as as much as you have tokens, but that's a good way to see it refined. And you when you have that version history, you can also say, okay. Look back, and you can see maybe where it got things wrong or it drifted. So that's the way I've been approaching just refining the markdown files.

**Speaker 0** [03:47:45]
I like it. Well, thank you, sir. Yeah. Any questions? And well, yeah, we got a question.

**Speaker 0** [03:47:50]
Wait up. Are you

**Speaker 4** [03:47:51]
does it do it automatically,

**Speaker 2** [03:47:52]
or are you you kinda

**Speaker 0** [03:47:53]
figuring yourself? Is it doing it automatically?

**Speaker 8** [03:47:55]
Sometimes I do it manually. I'm I made a skill that looped over it, and then that burned several $100 worth of tokens, so I don't do that too much anymore.

**Speaker 0** [03:48:05]
Nice. We got one? Alright. We got one. Where are you calling

**Speaker 2** [03:48:11]
in from?

**Speaker 6** [03:48:12]
I'm Tevye. I'm calling in from OnStage. You won't burn through hundreds of dollars of tokens if you use the max plan because it won't let you. I burned through, like, $800 of tokens, and then I realized I could have spent 200 for the month. It's literally 10 times more expensive on the API.

**Speaker 6** [03:48:33]
I don't know why. Say it again. Personally, I use an. Okay. Employ anyway, don't use the API.

**Speaker 6** [03:48:43]
My my workflow is kinda like yours. I have I just specify really simply using voice. It I have an architecture agent that writes up an architecture plan, a reviewer that reviews it, and then it goes in a cycle. When it's done, it summarizes the architecture for me. I usually have comments and changes.

**Speaker 6** [03:49:05]
But once I've solidified the architecture, that's pretty much all the review I do because then there's a TDD agent that writes all the tests. There's a coder. There's a code reviewer, and then it actually checks whether the code matches the architecture plan. And if Claude thinks it does, it's gonna do a way better job than I could ever do. So, really, all I'm doing is reviewing the architecture.

**Speaker 6** [03:49:28]
And then as long as the tests pass, I just ship.

**Speaker 0** [03:49:31]
But you're not writing the tests?

**Speaker 6** [03:49:33]
No. I'm not doing anything, really. Just reading. Yeah.

**Speaker 0** [03:49:38]
Don't tell many people that. Awesome. Alright. There's another good one here. What?

**Speaker 0** [03:49:43]
You got one? I see you. Just get up. Come on. Let's see what you got.

**Speaker 0** [03:49:47]
What's your best trick? Name, where are calling in from?

**Speaker 9** [03:49:52]
So I'm I'm Chubo. I came from Fresno. And I'm curious if you guys agree with me, but I said that handle your agent almost as you would be its therapist. And so this is not like, okay. I'm doing planning mode and whatever.

**Speaker 9** [03:50:15]
This is generally how I conduct with the agent because I know that the agent is super intelligent, but at the same time, it's dumb as well. I also know that let's say, I'm I'm not stupid, but I can also forget things, and and I can be stupid sometimes. So when I'm talk with the agent, let's say, want the agent to conduct a plan a new feature or some new iteration on it. I'm not necessarily instructing you that do this. Let's say, implement a new graph algorithm with that specific graph graph algorithm, but I rather try to ask questions like, do you think it would be good to implement this new algorithm?

**Speaker 9** [03:51:11]
Because then I give a little express expressiveness, a little creativity to also critique me and maybe even come up with a new algorithm I haven't known before. And so I I navigate this fine line of dealing with psychophanty, which is much better now when it than it was. So kudos to the big labs. They worked on that. But it can be still psychophantic.

**Speaker 9** [03:51:43]
And also to so to not instruct it too hard to so it can blossom its own intelligence, but at at the same time, it under control if it would be stupid.

**Speaker 0** [03:51:55]
Yeah.

**Speaker 9** [03:51:55]
So it it is a final.

**Speaker 0** [03:51:57]
I like it.

**Speaker 9** [03:51:58]
I I wonder if if you agree because I know Sweeks, for example, he he he says that don't don't anthropomorphize the agents. And for this, you kind of anthropomorphize the agents. It yeah. I I treat it almost like a a human. Right?

**Speaker 0** [03:52:13]
Yeah. Ask those questions. I like it. Anybody got questions? No?

**Speaker 0** [03:52:19]
Alright. I I think we've got time for one more. And since this layered memory one, if it is not, don't tell me it's you, Rob. It's not alright. We're gonna go with the hey.

**Speaker 0** [03:52:30]
We got a new caller. Get on up here. Let's see what you got. So I have a three layer memory system. MemoryMCP works on Cloud Code and desktop.

**Speaker 0** [03:52:41]
Cloud Code newest built in auto memory for each repository project and Joplin. I don't know what Joplin is, but give us I know you. Welcome. You you can use that mic. Tell us what you're talking about.

**Speaker 10** [03:52:56]
So this is something that I have been doing for not that long, like a week or two, but it's been very useful. First, I started using the memory MCP, the most kind of popularly available stock memory MCP. And that's nice because it the memories are accessible both from Cloud Desktop and from Cloud Code. So I when I jump in between, I have very similar resources available. And then Cloud Code maybe, I don't know, last five versions or so released this auto memory feature where they automatically create files in the dot cloud memory folder, I think, for each repository or project that you're working on.

**Speaker 10** [03:53:45]
And so and then third, I personally use this markdown editor called Joplin, which is very similar to Obsidian, if that's known to others, but that's really nice for basically, it's markdown native, so it speaks the language of LLMs and you can pull content directly from the output of Claude and it's nicely formatted and easy to read and edit and so forth. It's a little bit like Evernote, if people are familiar with that. And so I have all of that and I have my CloudMD instructing Cloud Code when to use each of these systems. So it uses memory and the memory MCP for overarching memories, allows it to just default to its auto memory for each repo and then exports to Joplin if I wanna save something. So that's been really nice for me.

**Speaker 0** [03:54:43]
And with Joplin, you're throwing the whole conversation into Joplin, or you're throwing just the code?

**Speaker 10** [03:54:48]
No. I'm I'm using it as a library. So I'm essentially it won't write to Joplin unless I explicitly tell it to. So if I run research on something, I'll tell it to output that to a Joplin note.

**Speaker 0** [03:55:02]
Uh-huh.

**Speaker 10** [03:55:03]
And then I'll at some later point, if I'm working on something, I'll say, hey. See this Joplin note for resources, and, you know, that might contain a list of links or other things. And then I'm kind of ramped up on that subject even if I haven't been active on it for a week or two.

**Speaker 0** [03:55:19]
Nice. Okay. Thank any questions? Anybody? We're good?

**Speaker 0** [03:55:25]
Alright. You're free to go. Well, that was it. I think the next question that I had in there was what's your hottest take? I don't know if anybody actually threw in their hot take.

**Speaker 0** [03:55:40]
Doesn't have to be on ML Ops. It can just be your hot take. We've got a few minutes before the next talk, I think, so people should start filing in. Anybody got a hot take they wanna defend in front of the crowd? Where we at with the hot takes?

**Speaker 0** [03:55:56]
It's a little cold in here. No spiciness? Nothing? What's your hot take? I see one participant typing.

**Speaker 0** [03:56:06]
Alright? So we're not gonna have the biggest field. What? You got a you got a hot take? The only safe job is entrepreneur.

**Speaker 0** [03:56:14]
Get up here and defend that. Come on now.

**Speaker 6** [03:56:21]
I I I've been an entrepreneur for three years, and what I realized is it doesn't matter how good you are at building products. If you can't sell them, you're never gonna succeed. Sure. And so now it's even more unimportant because Cloud Code can just build products all day long. So if you wanna succeed, you have to figure out how to get people to pay for things.

**Speaker 6** [03:56:48]
And Cloud Code can theorize about that, but I don't know if it's gonna replace that ability. If it does, it's gonna just become the world's richest AI. So, yeah, I think everyone should become an entrepreneur because we might all be Need to sell. Unemployed soon.

**Speaker 0** [03:57:09]
You need to sell. I like it. Alright. So there's a few hot takes coming through here. Any rebuttals on the entrepreneur front?

**Speaker 0** [03:57:18]
No? We're good? Which one should we do? Which one of these should we have? Mustache contest.

**Speaker 0** [03:57:26]
I like it. Where is Dex? Is he around here? I'll get you Dex. Don't tell me that twice.

**Speaker 0** [03:57:32]
Alright. The funniest one I thought was if we scroll down a little bit, where's the designer should be should have been coding this whole time. Joe, chill. Who is that? Rafa, chill, dude.

**Speaker 0** [03:57:52]
It's alright, man. Go get some more boba. We'll be alright. The designers, they're doing what they can. Rag does not equal vector search.

**Speaker 0** [03:58:01]
That's kinda hot. I like it. Where who was that? Who's that? Oh, you wanna get up here and defend that?

**Speaker 0** [03:58:08]
You wanna tell us why? No. Rag does not equal vector search. You saw that talk earlier. Is that what spurred this?

**Speaker 0** [03:58:18]
Perhaps. Yeah. Perhaps. Alright. Come.

**Speaker 0** [03:58:20]
Tell us why RAG is not vector search. What do we got? And what's your name? Where are calling in from?

**Speaker 5** [03:58:27]
Kareem calling in from Los Angeles. So Rag was popularized around vector search and vector DBs and so on.

**Speaker 0** [03:58:38]
That's the mic. Yes.

**Speaker 5** [03:58:39]
Rag was popularized around vector DBs and vector search and so on. And then there was this idea that long context windows make RAG not a thing that you should do anymore. The thing that frustrates me oftentimes is even with a long context window, you have to retrieve something to put in that context to get the output you want. So I think people got hyper fixated on a particular implementation of RAG. And really in generality you should be asking what information retrieval or REXIST techniques do I need for the problem I'm trying to solve?

**Speaker 5** [03:59:17]
Oh.

**Speaker 0** [03:59:20]
How we feel I like that one. How we feeling about that? Yeah? Any questions? Any anything?

**Speaker 0** [03:59:27]
I like that. Alright, Kareem. Thank you, sir. Now we've got one or two more, and Zach should be up. We've got a we've got the talk starting in four or five minutes, so I imagine people are gonna three.

**Speaker 0** [03:59:44]
Three minutes. This guy keeps the trains running on time. There we go. So which one, folks? We gotta upvote.

**Speaker 0** [03:59:51]
Which ones are we doing? Last one. I'm gonna ask everyone to upvote what you've got here. Where we at? Out of all

**Speaker 0** [04:00:00]
These hot takes, which one do we bring up to defend themselves? Where are you at? Oh, specialization will actually be more important. Early adoption is not automatically better. Alright.

**Speaker 0** [04:00:15]
We'll see more people decide that AIs are conscious. I'm not I'm we're not gonna do that one. That that is a hot take, but I'm not doing it. Siloed roles are dead. We all have to be ducks.

**Speaker 0** [04:00:28]
I like that. Alright. Yes. We should have mustache concert. Okay.

**Speaker 0** [04:00:34]
I think we gotta go back up because that got the most upvotes. Who did this one? Specialization will actually be more important. Important. Whose Whose is is that?

**Speaker 0** [04:00:44]
That? Where Where are are you you at? At? Alright. Alright.

**Speaker 0** [04:00:47]
You come defend your hot take. This is the last one, and then we're gonna have the talk. What you got?

**Speaker 1** [04:01:01]
Partially, I was just inverting something that was already.

**Speaker 2** [04:01:06]
But I

**Speaker 1** [04:01:07]
do actually think increasingly when anyone can do anything I don't necessarily mean specialization in terms of coding, although I do think there are still gonna be things there. Like, right now, if you don't know anything about security and you wanna build something production ready, like, because

**Speaker 2** [04:01:26]
Not gonna know.

**Speaker 1** [04:01:27]
You can, you know, vibe out or agentically code and what is production ready are not always the same thing. But I think, like, having specialization and especially, like, building knowing what to build and how to build it becomes, like, a specialization. Like, you know an industry, you're much more likely to be able to go and build the right thing for that than to just say, oh, I see an opening here, and I'll do that. So I think, like, general knowledge does will still has a place. You can do a lot more with a lot less, but knowing something still matters.

**Speaker 0** [04:02:02]
He gets a clap. Hey. What? Question? Rebuttal?

**Speaker 0** [04:02:06]
What do you got? Did you hear that? Subject matter expertise can be expressed in MD files? So we're taking you off mute right now? Alright.

**Speaker 1** [04:02:46]
One more.

**Speaker 3** [04:02:48]
So subject matter expertise that could be expressed in one MD file is not specialization, but it is the most that we currently have from the subject matter expertise. Specialization will grow, but the current form will extinct.

**Speaker 0** [04:03:04]
Different kinds of specialization. What are gonna say?

**Speaker 1** [04:03:07]
I I I think you can you definitely want this is not say, don't build skills, don't provide that, only rely on what you know. But I think having an edge of knowing a domain very well will matter, and those things are not easily consolidated down always into a skill.

**Speaker 0** [04:03:29]
A markdown file.

**Speaker 1** [04:03:30]
Or a markdown file.

**Speaker 0** [04:03:32]
Alright. I like it. Can we hit the bell to let people know that the talk's coming so we can try and file them in from the fun floor AV team, any possibility of hitting that bell so that people in the other room can

**Speaker 2** [04:03:49]
I did twice already?

**Speaker 0** [04:03:50]
Oh, you did? Alright. So you heard it, hopefully. Can oh, you weren't doing it in here. That's nice.

**Speaker 0** [04:03:57]
Nice feature. Alright. We're gonna have two more minutes, and then we're gonna bring up Zach wherever he is.

**Speaker 4** [04:04:03]
Where are

**Speaker 0** [04:04:03]
you? Hey. There he is. Zach. Alright.

**Speaker 0** [04:04:05]
We're gonna wait just two minutes. Is that cool with you? Yeah.

**Speaker 2** [04:04:08]
Okay.

**Speaker 0** [04:04:08]
Cool. So oh, I lost my Slido. Last hot take I was hoping for. Can I see the Slido again? The last taste matters more than anything.

**Speaker 0** [04:04:17]
Not so hot. Base models are better before instruction tuning. Kinda hot. Whose was that? Get up here.

**Speaker 0** [04:04:30]
Tell me what you oh, is that hot?

**Speaker 2** [04:04:32]
No. Do I know you? I can't see with the lights.

**Speaker 0** [04:04:36]
I thought you were somebody else. Forgive me. Get up here. Tell us what you're talking about and what kind of models you've been playing with.

**Speaker 4** [04:04:47]
Okay. So I think that one of the most, like, unexamined, like, defaults that has now been adopted is instruction tuning, which really hasn't evolved much since, like, GPT 3.5 instruct in the original ChatGPT. This idea that, like, a model is something that I give instructions and then, like, based on the instructions that comes out. And in the process of doing this, it just, like, nerfs all the entropy and, like, gives you these, like, really, really predictable paths, which is, like, great when you're working, but there's, like, all these different types of interactions that could exist with models. And so if you use base models, like, you get out like, it it's way more of a slot machine, but, like, you get way more rich diversity of outputs.

**Speaker 4** [04:05:33]
And this is most visible with creative writing because, like, creative writing doesn't have to, like, compile or run and things like that. So it's a little bit, like, more fault tolerant. But it's just, like, you get this, like, really rich set of ideas. You're like, woah. I've never actually thought about that, but you can't do it in a natural pattern.

**Speaker 4** [04:05:49]
You can't be like, write me a a story about this. You have to say like, you have to do, like, the autocomplete thing. Like Mhmm. Either, like like, the following is a story about. And you can kinda do this with code too.

**Speaker 4** [04:06:03]
So if you if you're getting frustrated with the lack of creativity or the lack or the, like, over predictability of models, you can actually go and find base models, like, particularly from the LAMA series or some of the, like, open source ones. And, like, the the the types of stuff you get out of them is, like, super wide. And I think it just means that, like, we have to, like, think seriously about what like, if most people don't have compute for post training. But at least, like, think about what are the things we would ask of models and, like, make that more diverse so those that do have setups for that can, like, produce different things. And so that's my take.

**Speaker 2** [04:06:38]
I like that. That was that was spicy.

**Speaker 0** [04:06:40]
Any rebuttals? Anybody wanna say anything about that? Jeremy?

**Speaker 2** [04:06:45]
Are you coding with baseball?

**Speaker 0** [04:06:48]
Are you coding with baseball?

**Speaker 4** [04:06:50]
Very rarely. Mostly if I'm trying to make, like like, mostly artistic stuff. Like, I actually found my first vibe one of my first vibe coded things from 2021 because, like, the original GPT three could do, like, JavaScript and CSS animations, and they're, like, super weird and blinky, and most of them were broken. But, like yeah. Like, it can do, like, front end stuff with the bay the the latest base model.

**Speaker 4** [04:07:12]
So sometimes. Not when I'm trying to get work done. But

**Speaker 2** [04:07:16]
When you're trying to vibe, I like it. Yeah. Alright. Jeremy, thank you.

**Speaker 4** [04:07:19]
Yeah. What I'm trying to vibe.

**Speaker 0** [04:07:19]
Here we go. So, folks, I'm gonna bring up our next speaker. I am excited. He's coming from the land of the Adobe architecture. Can you put your hands together for Zach, the founder and CEO of Warp?

**Speaker 0** [04:07:34]
Let's hear it. And, Zach, you got any hot takes for us? You got a whole Whole presentation of hot takes.

**Speaker 2** [04:07:49]
Gonna be hot takes.

**Speaker 0** [04:07:50]
There we go. Are you mic'd up? Or you wanna use that mic? Use that mic. Yeah?

**Speaker 0** [04:07:54]
Yeah. Perfect.

**Speaker 2** [04:07:55]
I wanna be able to do a demo. Will I be able to do that?

**Speaker 0** [04:07:57]
Alright. We'll try.

**Speaker 2** [04:07:59]
Okay.

**Speaker 0** [04:07:59]
I think we're gonna do this. Okay. And you can give your talk while I figure this out. How's that sound?

**Speaker 2** [04:08:06]
That sounds great. Yeah. This doesn't need to go on for a bit, so I'll get started. Yeah. Don't share the things you don't wanna share.

**Speaker 2** [04:08:14]
We need to adapt. Okay. Alright. Hi, everyone. I am Zach.

**Speaker 2** [04:08:21]
I am the founder and CEO of Warp. I'm excited to be here. I'm thank you. Today, I'm I'm gonna talk about agent orchestration, which I think is a hot topic and increasingly hot topic this year. This how I do the slides?

**Speaker 2** [04:08:38]
Yes. It is. Okay. Cool. I'm making a bold prediction that 2026 will be the year of agent orchestration.

**Speaker 2** [04:08:46]
So what does that mean? Me start, I guess, with a little bit of I don't know if it's a story. It's more of a question. But the the way that we are working now at warp, I assume this is true for a bunch of you, is, like, increasingly running multiple agents at once and starting to run into the limits of, like, what our laptops can do. So for us, we have a code base that's, like, million lines of Rust code.

**Speaker 2** [04:09:12]
I have maybe four or five of these checked out on my laptop. I am running agents in them. Typically, we're running, like, warp's own agent, but this is probably happening to people who are running Cloud Code or Codex. It's the same thing everywhere. Just, like, show of hands, are people is this a thing that's happening to other people, or is this just us?

**Speaker 2** [04:09:33]
So it's starting to slowly happen. What is, like, driving the overall trend here? So there was an intro slide for me, but but I've been an engineer for over twenty years. I was a I used to be a principal engineer at Google. Most of my career has been spent writing code by hand.

**Speaker 2** [04:09:54]
Like, literally, you know, what I would do every day is I would come in and I would open up a code editor, an IDE, and I would type code. And sometime last year, I've totally switched the way that I'm working to be writing by prompt. And I'm still you know, even now, I still ship software and warp, but I haven't written code in the last six months. Again, show of hands. I assume everyone in here, this is a very agent forward crowd.

**Speaker 2** [04:10:21]
Is is this resonating with people? This is how you code. And so from, like, a big picture perspective, I think sometime in 2025, coding switched over from being, you know, you're writing code by hand to to writing by prompt. And the way that I can see of the prompting that most people are doing right now interactive. And so what I mean by that is, like, if you wanna fix a bug or implement a future, you open up your terminal or maybe you open up your IDE and you start typing something like, you know, I want to fix this bug, and then you pair with an agent while it does stuff.

**Speaker 2** [04:11:05]
And then you might do that with a second agent or a third agent. And so but the the key thing is, like, you're you're there. You're guiding the agents, and the agents are doing the work while you, like, have this conversation. But my hypothesis and a thing that we're working on at at warp and I guess maybe I should have introduced warp for people who aren't familiar. Warp is it's in, like, an agentic terminal.

**Speaker 2** [04:11:30]
So it's a terminal that has agents built in, but it's more than that. We're actually moving into this, you know, the space of how do you how do you orchestrate agents that aren't tied to your terminal. But the issues that we keep running into are things like, literally, it's the laptop capacity, like, if you're running a lot of agents. But it's also like if you're running an engineering team or running a company, you you know, all the agents that are running on, like, your engineers' individual laptops, all of their work is kind of just happening in a place where it's not visible. Like, you can't see what your engineers are doing, so you don't have a sense of, like, how does agent adoption look like.

**Speaker 2** [04:12:13]
You you can't have a a clear view of, like, do you have security holes with your agents? If agents are tied to your laptop, there's an issue that those agents can only run when your laptop is on and connected to the Internet. So there's all of these sorts of problems that are brand new problems that are only occurring because we've moved to a spot where you can truly run multiple agents at once on your laptop. So what's what's the solution to this? It's a picture of me on a on a horse.

**Speaker 2** [04:12:46]
We did a commercial while I was on a horse. It was cool. I think this the solution to this is is that companies and engineering teams over the next year are going to want to bring control to the chaos of, like, having multiple just like having everyone run all of their coding own coding agents on their laptops. And they're gonna wanna do this in a way that doesn't ruin the productivity gains. So, you know, it's it's awesome right now that, like, developers are trying out all these new tools.

**Speaker 2** [04:13:17]
They're trying out Cloud Code, tools like Warp, Codex, etcetera. But it also is is creating an untenable situation, and it's also just a limiter on productivity. So, you know, my prediction is this year, there will be solutions for this. There's one other big important reason besides just the issue of like you're hitting laptop limits. It's also that the actual, like, types of tasks that you want these agents to do require them to run for longer and also potentially require them to, like, you know, run for you know, run as teams, not just run as individual agents.

**Speaker 2** [04:14:03]
And so for this, there's there's, like, two classes of things that we're gonna wanna fix this year. One is just, like, long single threaded agents that are doing hard tasks. And if you're, you know, if you're an engineer working on a hard coding task right now with an agent, you probably are you know, you're probably sometimes hitting issues where the agent, you know, exceeds its context window. Maybe you compact your agent context. It starts to forget stuff.

**Speaker 2** [04:14:29]
And so you need some sort of, like, primitives for doing longer, harder tasks. And then the second thing that's gonna happen this year is you're gonna actually have agents that are working together. And so you're gonna have a class of tasks that are amenable to multiple to sorry, to multiple agents working on them at once. So this is another thing that's happening right now, and there needs to be infrastructure for it. So what are the use cases?

**Speaker 2** [04:15:00]
So it's not just interactive coding tasks. One big use case this year that's gonna become more and more common is automations that are built using agents. And so think of this as, like, every time we do a warp release, for instance, an agent looks at our code base and it looks at our documentation, and it comes up with a PR document sorry, to update the documentation based on what's in the latest release. Or there's another class of automation, which is like we have an agent that runs on a timer every week. It looks for feature flags that are basically guarding dead code that we're never gonna turn off, and so it it can remove those.

**Speaker 2** [04:15:43]
And so if you're running an engineering team or if you're an individual engineer, you're gonna want the ability this year to build these kinds of automations, which is another reason you're gonna want coding agents off of your laptops. On top of that, there's like agents are a new programming primitive. And what I mean by this is that if you're an app builder, whether you're building internal apps or you're building customer facing apps, you're gonna actually wanna be able to add agents into those. So, you know, I'll I'll show you an example of an app that we've built internally at Warp where we triage our GitHub issues. And it's it's interesting.

**Speaker 2** [04:16:27]
It's not like it's not an automation. It's an app. But within the app, you can launch agents to do certain types of tasks. And so there's all these use cases, again, where you're gonna want to basically take the coding agents that everyone in here is using all the time, whether, again, it's like Cloud Code or Codex or Warp's coding agent or whatever, and you're gonna wanna be able to program those to run off of your laptop. That's the theme.

**Speaker 2** [04:16:55]
I know I called it orchestration, and and orchestration is part of it. But I think, actually, you know, the other big part is just moving to the cloud. So if you wanna do this type of workflow where you're working with coding agents and you're not, you know, stuck to your laptop, you might think that you just wanna build this yourself. And there's a bunch of, you know, there's a bunch of primitives out there that let you run agents in cloud sandboxes, and that is one of the primitives that you need. And if you're, you know, if you're a company, actually, several companies have been in the news recently, like, launching their own internal agent orchestration systems.

**Speaker 2** [04:17:40]
I think Stripe launched one called Minions. I think Ramp launched one. You might find that you you wanna build this, and that's a reasonable thing, I think, for a company or an organization of a certain size. But you also might find that you don't wanna spend the time building all this scaffolding for running agents in the cloud. And if you don't, like, this is a I mean, kinda I'll talk through, I think, what the primitives are that you wanna sort of be able to use off the shelf.

**Speaker 2** [04:18:12]
And I I'll talk a little bit about a product that Warp launched in this space, but I'm not I don't wanna spend too much time on our own products. But what are the primitives? And what would it take if you wanted to build Cloud Agents yourself? So I think the primitives are things like environments. So you need some place that defines, like, what the agent has access to.

**Speaker 2** [04:18:38]
So this is, like, what's the tool chain? What's the what code does it have access to? You need hosting. So these agents need to run on computers somewhere in the cloud, and there's a bunch of things like maybe Daytona or e to b or Docker sandboxes or namespace. These are ones that we use.

**Speaker 2** [04:18:57]
You're gonna want some ability to get visibility into what the agents are doing. And so there's there is actually a bunch to build here. I think you definitely, if you're gonna build a system like this, wanna build it so that there's still a human in the loop. And what I mean by that is, like, if I mean, I think it's obvious. What I mean, it's, like, you want the ability to see what these agents are doing when they run-in the cloud, even if they're running as part of automations or app back ends so that you can can guide them, you can step in if they only do 80% of the work and make sure that you finish it off correctly.

**Speaker 2** [04:19:36]
So we we just launched a product called Oz, which I'll demo in a bit, which you can think of as kinda like, you know, Vercel for Cloud Agents or Supabase for Cloud Agents where we're trying to make it super easy for developers and development teams to move these workflows off of their laptop. The primitives, I think this is interesting, whether you use Oz or not, are like you want a great coding agent, or I actually think you want multiple great coding agents. So one of the things that we're working on with Oz is the ability to run any agent harness. The harnesses have different pros and cons. You want something called, like, tracking.

**Speaker 2** [04:20:23]
We we call this feature of Oz auto tracking where no matter where you launch an OZ coding agent and how you launch it, you get a link to what it's doing. And all the, like, artifacts of the agent run are automatically recorded. So if you want to go back and see what an agent did, if you wanna see how it reasoned, you get that information. You want handoff. So this is about human in the loop.

**Speaker 2** [04:20:54]
So if an agent is, you know, working in a cloud system and it can get only 80% of the way there and you want an engineer to pick up what it did, that should be easy. I mentioned earlier, you want some sort of environment definition and hosting. And then I think the final thing that you want if you're building a system like this is that you want it to be fully programmable. And so what I mean by that is, like, you should be able to launch agents via API or SDK or CLI. You should be able to configure environments.

**Speaker 2** [04:21:28]
You should be able to pull artifacts. You should be able to pull conversation history. And you should do that not just for, like, human programmers to use, but this is actually these are the building blocks that will allow agents to actually orchestrate each other. And so our approach here has been, like, you know, build this all in a very programmer first way. So I'm gonna switch over doing some demos.

**Speaker 2** [04:21:54]
Hopefully, this will work. Where I show you, you know, what I what I think of as, like, orchestration and action and how it can be helpful. So let me switch here and figure out how to do the mic. That one works. This one will work.

**Speaker 2** [04:22:09]
So should I turn this one off? Or

**Speaker 0** [04:22:12]
okay. Alright.

**Speaker 2** [04:22:14]
Put this down here. Okay. Cool. Yeah. So I'm I'm gonna I'm gonna show you a few different use cases here, and and it's all about, like, agent orchestration.

**Speaker 2** [04:22:30]
So let me first start here. And for people who aren't familiar, this is Warp. Warp is it's a terminal with agents built in. The history of Warp is we started off building a sort of modern terminal and then as, you know, as agents have become more and more popular, we've built in features that just make it super easy to launch agents from directly within warp. Within warp, you know, I can I can sort of use it as a terminal here?

**Speaker 2** [04:23:00]
But what I actually wanna show you is how you can do multi agent work. So I'll go here and I'll show you a project that I've been working on or actually someone from my team has been building, which is we vibe coded our own version of Google Docs. And this is this is the product that I used to I used to work on at Google, so it's pretty fun to work on again. We built this in a couple days, but it's it's pretty incomplete. And so if you go over and look at our version of the spreadsheet here, it can do simple formulas.

**Speaker 2** [04:23:36]
So it can do like a sum formula, but if you go over here and try and have it do an absolute value formula, it's actually not currently implemented. And so what I'm able to do now, go back to warp here, this will show you the use case of like being able to do multiple parallel agents in the cloud. I'm gonna go over here and I will I'll first show you how, like, the regular agent works. So with the regular agent, I kinda just go into a new conversation here. I could be like I could be like, you know, implement all the formulas that are missing that start with the letter a.

**Speaker 2** [04:24:24]
And so this launches our interactive agent. And so in the old way of working, what I would do is if I wanted to do multiple of these at once, I might pop open another tab over here and basically do let me copy this for a second. I might go over here and say implement all the formulas that start with the letter b. And I could do that, but I'm gonna start to run into these limits of, you know, just like these laptop limits. So the thing that we've built in that I think people are gonna increasingly want is the ability here to do this directly in the cloud.

**Speaker 2** [04:25:01]
So I'll go here and this is instead of being a local conversation has the exact same sort of UI, but this will launch it into the cloud. And so I'll do this and I'll start this as a cloud job. Now what's cool is I can actually just kinda go back here. You can see here this one is starting up and I can go back and look at it in a second. But you can also here, this one's going over here and doing the implementation, which is cool.

**Speaker 2** [04:25:30]
I can also go ahead and over here launch the one that implements the the formulas that start with the letter c. Oops, I didn't do this as a cloud agent. I meant to. So we go back here. I'll do this c and I'll do this one again.

**Speaker 2** [04:25:48]
I'll do it d And I'll do it again. E. And so I'm not sure if you all are catching this, but what I'm able to do is just like massively multi thread the work that I'm doing here by launching these agents into the cloud. So this this is using Warf's built in agent, but the thing that we're working towards is supporting this actually to work with any agent harness. So if you're running a whole bunch of cloud codes or whatever and you just wanna be able to launch them in the cloud, can do it.

**Speaker 2** [04:26:20]
So if we go and like look at one of these, I think the cool thing here, I think this is another thing that that you probably want with orchestration is like you get a view, you'll notice that looks identical to the one that's working locally. But if I go over here, this is going into the Oz web app and this should give you a sense of what I mean when I talk about orchestrating. I can see that all of these agent runs are actually being tracked now across the team. So this was launched locally. I launched it.

**Speaker 2** [04:26:55]
And you can see that this is like a run that was done by me. But I can also see in here all the other things that agents across my team are doing, which is super cool. So I can see something that my teammate Matthew was doing. I can see something that my teammate Ian was doing. And you can see actually the artifacts that these agents are creating as they go.

**Speaker 2** [04:27:16]
So you can see that this one created a PR. And if I want, I could actually go in here and I'll open this up. I could see the work that he did. So to me this is like super cool. It's it's almost like a Google Docs for agents type concept.

**Speaker 2** [04:27:34]
And I can see exactly what the record was of how this PR was produced. I can go here and actually look at the PR and, you know, I can see that Ian made this. And so he could also again, these things don't have to be public, but I'm running this in such a way that is public. But it's all behind access control. So you're all of a sudden, building with agents becomes a team sport.

**Speaker 2** [04:27:56]
So this thing that I started locally, implement missing formulas starting with e, even though it looked like I was running this on my laptop, I can also update it, like open this up here on the web and see it working and this will be the identical view to what I was doing here. I could open this on my phone, which is super cool, and I could even steer it. So if I go over here and I'm like, you know, actually let's do e and f as the formulas. This should actually then adjust the task. So again, it's like you could be away from your computer.

**Speaker 2** [04:28:39]
This is running in the cloud. So this is one use case of what I mean by orchestration. I think it's super cool. It's more like just as an individual, let me move these tasks off of my laptop. Having these things in the cloud though opens up other possibilities.

**Speaker 2** [04:28:54]
So I'm gonna I'm gonna show you a a second use case. And I'll try and leave some time for questions if people have them. But a second use case is that you can actually define what we call they're kinda like let's see if this maybe takes a second to load. Live demo risk here. You can define what we call named agents.

**Speaker 2** [04:29:18]
And so named agents are like repeated tasks. And the way that these work is pretty interesting in in Oz where you basically define a skill. And I know folks have been talking about skills today. Any skill that's in any of your repos can become a thing that is like a repeatable automatable thing. So for instance, if you look through these skills, you can see here we have we have a skill for analyzing customer feedback.

**Speaker 2** [04:29:49]
We have a skill for fraud checking. And these named agent runs become something that you can set up across your team. You can set them up on a schedule, which is cool. You can go ahead and look at the actual skill. And so this is all, like, from a version controlled skill file.

**Speaker 2** [04:30:08]
And then you can go and see all of the runs that the skill actually executed. So if I I could find a fraud run here. And, again, I think the cool thing here is it's turning it's turning agents from a solo individual laptop sport into a team thing where you can see everything that's going on across your team. And so these these skill based agents can be scheduled. So this one, I don't know exactly how often it's running, but it's something that runs on its own.

**Speaker 2** [04:30:41]
It also will produce PRs. And so that's one of the cool things about it being a coding agent is it uses the coding context to do its work. I'll show you one final use case and then maybe I'll I'll answer some questions. But there's another use case that I think is interesting and important, which is the ability to use agents as like an intelligence feature that you put into apps. And so this is an app that I built.

**Speaker 2** [04:31:12]
It's called PowerFixer. It's open source if people wanna play with it. It's a it's a tool that we use internally to triage GitHub issues at warp. And so if I go in here, I can hit this issues view and I can see this is a this is a live view of like warp's GitHub issues. And if anyone has done a bunch of issue triage, we have like thousands of issues here.

**Speaker 2** [04:31:35]
You know, there's a set of repeatable problems that comes up. One is that I want to know if there are duplicates. And so what we have Oz doing is automatically dedupping every issue that gets filed. And again, could go and I could just kinda see this like dedupe run. But the other cool thing that I can do is like if I find an agent sorry.

**Speaker 2** [04:31:56]
If I find an issue as a triager that I wanna directly fix, I can just from this TUI app that I built, launch an agent to do a fix for it. And so I could add to the prompt, I don't have to, But this is all using that exact same infrastructure so that when I launch this agent to do the fix, again, you get something that is tracked across your team. So this will take a second to to spin up, but this also would show up in this same tracking location. So let me just step back for one second. So the let me grab the mic, actually.

**Speaker 2** [04:32:35]
Is this working? Cool. So, yeah, the the way to think about what we've built here and the way that we're approaching this is, like, it's a set of APIs for running and managing agents in the cloud. And the sort of next step for it is, like, it lets people who are trying to build multi agent systems where the agents talk to each other have the right set of primitives to do that. So the the next big thing that we're gonna do on this is not just, these, like, one off agent runs in the cloud.

**Speaker 2** [04:33:04]
It's more like how do you go from a concrete plan for a hard task that might benefit from multiple agents to using all of these same APIs to, like, coordinate sorry, coordinate those agents to accomplish that task. So, anyhow, let me let me stop there, and I think we're just about a time. And if folks have any questions, I'd be happy to answer them. One question? Cool.

**Speaker 2** [04:33:27]
Just one question. Yep.

**Speaker 5** [04:33:34]
Here we go. So everybody can hear you.

**Speaker 2** [04:33:38]
Have you tried GitHub agents? They run effectively the same kind of thing as Cloud Code in the cloud. I haven't used them much myself, but I'm just curious if that how that compares to what you're doing. I I I've used them a little bit. Similar idea.

**Speaker 2** [04:33:57]
I think yeah. I couldn't do, like, a feature by feature comparison of them, but it's just the same general principle I think you're gonna see with a lot of people who are working on agents of, like, how do you make it easy to have these things on the cloud? The specific areas that we're we're focusing on to maybe really lean into are, like, how do you make these programmatic? Especially if you're what we're finding when we talk to a lot of companies is, like, the existing systems for doing this tend to be very rigid. Like, you have to set up a docker environment and, like, run it on your, you know, in some cloud host.

**Speaker 2** [04:34:31]
And so we're really trying to lean into, like, you can bring the agent into your own infrastructure and still get a bunch of these tracking features.

**Speaker 6** [04:34:41]
Cool. Thank you so much.

**Speaker 2** [04:34:43]
Yeah. Thank you all for having me.

**Speaker 6** [04:34:55]
And now I'd like to introduce our first speaker for our nutlining talk, Faye Zhang from Pinterest. Oh. Alright. Where's the clicker thingy? Here.

**Speaker 6** [04:35:09]
Right here. Okay. Perfect.

**Speaker 7** [04:35:11]
Hey, everyone. Good afternoon. My name is Faye. Welcome to the lightning talk, how to productionize a subagents for LM post training. I'm a tech lead at Pinterest Growth AI applications.

**Speaker 7** [04:35:24]
Excited to be here with you all today. So as we know that the ClockCode or any cogen tool has accelerated the software development from zero to production ready in a matter of days. But how about machine learning and AI engineering? What does the model training now looks like? Because no matter what are you building, it's if it's a agentic CRM tool or threat hunting security products, you want your model to be a line of what's what we called good, meaning the right reasoning, the right time for two calling, and the right persona to answer a customer's question.

**Speaker 7** [04:36:00]
So before ClawCode, we call it BC, our model training process looks like this. It's a giant linear process where you first define what's your data look like with cleaning JSON parquet and then download your hugging face models with hyperparameters, choosing your LoRa, QLoRa, full fine tuning process and define your loss function and reward config. And then you start the big eval development restart loop. And once you have productionized your model, oftentimes, you get user preference data and you use reinforcement learning for DPO, PPO type of training. So all of that is incredibly manual and takes four to six weeks.

**Speaker 7** [04:36:47]
Now introducing our new workflow, which just takes about a week using ClawCode. We effectively break down the model generation of the training data using ClawCode SQL ingestion and also training parameters. And all of that task has been paralyzed using sub agent structure. Now for full transparency, we did explore other agent architect as well. So right now, off the box, Claude does support sub agents and agent teams, also known as agent swarms.

**Speaker 7** [04:37:22]
The biggest difference is for sub agents, you essentially communicate with the sub agents only via your main agent, and you report back once the task is done. But for the swarm mode, the agents share a task list, and then each teammate communicate with each other and, check each other work until you move to the next stage. So one might say, hey. The second method works better. Right?

**Speaker 7** [04:37:48]
Because it sounds way more advanced, but not necessarily true for model pace post training. This is because we quickly found out two bottlenecks. Number one is context limitation. As you imagine, each model keep giving other models the results of its own task and the context window quickly expand exponentially. And number two is the richness of the orchestration.

**Speaker 7** [04:38:12]
So right now, ClawCode doesn't support a dynamic scaling, meaning you will quickly run into what we call the hot celebrity problem in system design, where one of the agents become incredibly busy and bottled down with a task, and there's no way to easily scale sub agents among that. So we started our journey with a sub agent structure. And for a side note, if Opus is way too expensive, I would highly recommend MiniMax 2.5. It's a fraction of a cost of 0.27, cents on the dollar here. And, also, it's trained on PARL, privacy alignment reinforcement learning.

**Speaker 7** [04:38:52]
It essentially kinda solve the second problem of the swarm agent from Claude and knows when to dynamically scale your sub agent when it needs to. So in production, we also quickly realized there are a few patterns that a coding agent for post training often fail. Number one is Spectrift. Meaning, throughout the iteration of training eval redo, the model main framework often forget what the success metrics looks like. And the second is data distribution.

**Speaker 7** [04:39:24]
Arguably, this is the biggest bottleneck to the success training of the model where you have very uneven data representation bias, and that's what at least to a training training and loss graph over here. And the third is memory collapse. Once you started to train your models after twenty, thirty to a 100 epochs, the model essentially forgot how to get the right memory config from previous time, and they started to hallucinate. And lastly, tool misuse. This has become less a problem, I think, this year just because as industries, ourselves, we learn how to better define tool use for agents, but it's still something to watch out for.

**Speaker 7** [04:40:10]
I wanted to provide some fixes that have improved the post training mechanism. Number one is reinforce the agent orchestration with agent SDK. The agent from Mythropic is a open source agent orchestration tool. You're essentially can define your full loop, beyond just the graph, the chains. It also have the nice hook mechanism where you can gate each model output from your agents as a machine readable artifact.

**Speaker 7** [04:40:39]
For example, for our data processing, we will have agents write their own dataset report, the representation of each country, each user, and etcetera. And in the end, we also have gated decision to reject or ship instead of doing the linear process that we previous have. The two tip I want to quickly share here, number one is the structuredskills dot MD. Now we moved from a natural language style MD to more structured perspective. This is because we quickly realized the better instruction you give the agent itself, for example, you wanna kick start on the hyperparameter that you wanna choose, the better the agent align with the process.

**Speaker 7** [04:41:23]
And if you don't know where to start, I highly recommend the MS model that is open source to teach agents how to train your LMs. And the second big get unlock we see is actually implementing what we call the two calling two dot o two calling two point o. Essentially, of a giving agent just back and forth information, how is the data looking? Is it not good enough? Let me redo it.

**Speaker 7** [04:41:50]
We essentially giving the agent capability to write its own code to solve its question. So the traditional path looks like this. You have five requests, five response. But just letting agent handle you one response with a script and then have the loop until you checks its own work drastically reduce 70 to 50% of the token consumption. Now tips number two is customize your agent memory.

**Speaker 7** [04:42:19]
We all know how the clock code SDK agent memory work, where you have the procedural memory and your MD and also the episodic memory for each training episode. So what we did differently is because not all the training log is helpful for us, we developed our own memory API tool. Meaning, we add our own pruning and compression logic on the server side to decide what is useful to store. And then we also put a very lightweight reward model for the agents of what kind of memory gets written here. Now I do wanna claim that it is working in our production now, but very likely in the next three to six months, this is gonna become tech debt.

**Speaker 7** [04:42:59]
It depends on how fast our agent evolves. And in the end, I wanna leave you all, like, kind of open question or thought. What happens for long horizon development memory? Without long horizon memory, model often collapse. And then we see beyond cloud code, what cursor is doing right now, it's essentially using a hybrid retrieval semantic search and also compile its constant constant re synced memory via Merkle tree, which is the backbone of how cryptocurrency, for example, Ethereum is is created.

**Speaker 7** [04:43:36]
And also for open source tool, Leta, it's essentially using the agent blocked memory from archive retrieval and also on top of vector database. So the two papers I read this month, thought it was quite interesting is number one, essentially treat memory as a learned memory, with the agent and answer using PPO and how to answer using GRPO. And then very lastly, a very interesting deep dive on infra side where this paper, condensed the memory into hot domain and cold storage via MCP. So thank you for the time, and I'll be down there if anyone has any question.

**Speaker 6** [04:44:21]
Thank you so much, Faye. Next, we have Yanis He from Scale AI. Let's give him a warm welcome.

**Speaker 5** [04:44:29]
I think I have this mic. Alright. Hello, everyone. Okay. Let me see if this work.

**Speaker 5** [04:44:43]
Alright. Okay. There's a delay. Cool. Hello, everyone.

**Speaker 5** [04:44:48]
My name is Janis. I'm one of the founder of three bench pro. In the next few minutes, I want to quickly talk about how we get to SuiteBench Pro and what excites me when I think about the next of coding agents. So if we look way back, there aren't much change about how we code for almost twenty years. But in the last several years, the change has been wild.

**Speaker 5** [04:45:15]
We start seeing cursor, which is ID plus AI, and we also start seeing foundational models start competing on coding agent capability. We also start seeing the development of scaffolding, which is basically tools we've given to agents to explore, to run, and to write code. And later last year, we start seeing foundational models start training with the scaffold. On the measurement wise, a team from Princeton developed a benchmark called SV Bench, and it sets a cornerstone for the entire coding agent measurements. It used GitHub issue resolution as the proxy to measure how AI can do coding.

**Speaker 5** [04:46:01]
And then the entire bench universe start diversify. There are basically different kind of three bench testing the similar problem on different kind of code base, but many of them has a problem. It is the contaminations. As model grew larger and train on more code, data contamination become hard to avoid. So it was natural for us to think, hey, what if there's a benchmark we can create it with code that no model has trained on?

**Speaker 5** [04:46:38]
That leads to the development of SuiteBench Pro. And we started selecting repos with a very strict license, and we realized, hey, that wasn't enough. We want to be more extreme, so we start acquiring company for their proprietary code base. So beyond solving the minimal contaminations, we also have humans to verify each problem has the right amount of context, so it's both challenging but also solvable. We also want to make sure we have enough coverage into different domain industry to make sure the problem are being challenging but for a good reason.

**Speaker 5** [04:47:20]
So that has been a pretty good success. SuiteBench Pro has become the industry standard and different model release start using SuiteBench Pro as their coding capability verification. And we recently got a shout out from OpenAI where three bench pro was recommended over OpenAI's their own benchmark. However, there has been a question I keep thinking about after the release of three bench pro. What is the next thing?

**Speaker 5** [04:47:48]
Should we keep building a harder problem? SuiteBench, like ultra max plus? It might be helpful, but is there anything else we can contribute? By a quick show of hands, I wonder who here is or has been a software engine. Cool.

**Speaker 5** [04:48:11]
That's lots of you. And please raise your hands again if you have been doing more than just GitHub issue resolution. That's almost the same group. So I think here's my conclusion. Coding is not just GitHub resolution.

**Speaker 5** [04:48:32]
There are a lot more to do being a software edge. So what else do? We ran a quick surveys among engineers and we found issue resolution is around a quarter of time and that quarter has been declining because of the coding agent capability. SuiteBench Pro measured that quarters which encouraged the industry to develop in this direction, but what else? How can we encourage the industry to measure and build towards the rest of the ecosystem?

**Speaker 5** [04:49:03]
So that's why we start building again. So today is actually the first day we are launching this one to the public. The official launch of the first stage release will be tomorrow, but we are launching a new benchmark that assess how agent can understand, validate, and improve the software system in real repository. So the first days will be tomorrow and each of the type of task require more than just observation from the code base. We require coding agent to actually go in, explore, and run the codes in order to do the multi file reasoning.

**Speaker 5** [04:49:41]
Beyond just measurements, we also create post training data to help model builders to improve this capability. And within our benchmark, we have rubrics to help different model builders to their failure analysis. I don't want to give give away too much before tomorrow's launch, but I'm very excited to see, these improvements of coding agents in the new directions. To end this presentation, I want to quickly share about our insights about next stage coding agents. We start seeing a trend of coding being the lags and hence for AI.

**Speaker 5** [04:50:21]
Our vision believe if we give coding agents enough freedom, it will start developing tools that it make more sense to the agent themself, that's more intuitive and effective. Actually, we've seen some early signal. Terminal bench, which is another benchmark developed by Stanford team, they measures how AI can explore their capacity through con command line. And we have seen another signal which is OpenClaw. It's very popular nowadays.

**Speaker 5** [04:50:54]
We see agents start bringing their own tools to solve a generic problem that's not just software edge. So in order to match our visions, we have a road map which one of them is to develop a more diverse playground for the coding agents. Where agents can go in and explore their own intelligence and expand their capability. And of course, we don't want to leave human behind, so we also want to increase human agent interactions. We strengthen agents capability to escalate and call humans when it needs help, where information are missing, contradicting, or is unclear.

**Speaker 5** [04:51:35]
We are also doing another collaboration with the original terminal bench team to develop the next generation of terminal bench, and we are expanding into different professional domain, such as healthcare, finance, legal, or different kind of engineers. To close this presentation, I wanna share that we never expect what we are leaving to this world as the final thing of coding agents, but we are very excited to see what kind of a splash we can make to this world. We hope what we're doing can serve as a stepping stone for this community to build the next era of coding agents. Thank you.

**Speaker 6** [04:52:27]
Thank you so much, Yannis. Next, we actually have Erin Ahmed from Clerk. Please give a warm welcome.

**Speaker 8** [04:52:39]
Hey, everyone. My name is Erin. I'm the head of product at Cleric. And today, I'm gonna talk, through a little bit about what we've learned building a learning agent. So let's start with what is a learning agent.

**Speaker 8** [04:52:51]
Well, it's the opposite of a stateless agent. A stateless agent starts a session fresh with no memory or context of past conversations. Imagine a coworker that, shows up to work every day with no recollection of what happened yesterday. That's the current state of most of our agentic coworkers today. A learning agent or a stateful agent, on the other hand, is one that learns from experience, and it adapts to improve performance.

**Speaker 8** [04:53:17]
And at Cleric, we use agents for every aspect of building our own agent, and this is where we see the puck moving. Agent capabilities are commoditized. This is not this wasn't the case at this time last year. And the next horizon of differentiation is going to be learning or self learning. This is a a conviction that we've built our product around.

**Speaker 8** [04:53:40]
The agents that earn their place will be the ones that accumulate knowledge about three things, your environment, your team, and how you work, and past outcomes and corrections. So for Cleric, Cleric's an AI SRE. It learns from every production incident. You connect it to your infrastructure and your observability, and it immediately starts building a model of your environment. You drop it into your alerts channel, and it learns from your past incidents and your your channel history.

**Speaker 8** [04:54:10]
And you use it as an investigation assistant, and it learns your preferences and your procedures over time. We've deployed it to dozens of customers at this point, and what we've learned over months and to you know, now bordering on years of trial and error is that there are essentially three things that make a good learning agent. The first thing is good learning agents make it easy for users to correct or to teach via correction. You know, wrong answers are inevitable, and accuracy is important. But the agents that win will be the ones that make it easy to correct mistakes and not visibly repeat those mistakes later.

**Speaker 8** [04:54:50]
So for Cleric, this looks like proposing memories that persist across investigations. It looks like self harvesting skills to encode learned procedures and capturing user ratings on agent messages as an explicit quality signal. But the most important part is the visibly never repeating the mistakes. It's especially important for a team based agent like Cleric where one user session and the the corrections that are learned from that apply to the next user session. And it leads into lesson two, which is good learning agents reward corrections with better performance.

**Speaker 8** [04:55:28]
You you lose your users' trust when they expend the effort to teach the agent something, and that lesson is not retained. A correction should do three things. It should persist, compound, and then be visible. By persist, what I mean is to the the agent applies that knowledge in the same context. So for example, if after an outage, a user were to teach Cleric how to perform a customer impact assessment, you should expect the agent to recall that procedure the next time it's asked to do the same thing.

**Speaker 8** [04:56:02]
By compound, I mean, that knowledge or sorry. Generalizing that knowledge into a different context. So perhaps there's something in that procedure, like some guidance about how to distinguish between an internal instance and a production customer instance. A compounding effect would be the agent using that context in a different investigation, like, automatically excluding internal instances from, you know, an error rate analysis of production customer instances, for example. And the third thing is to be visible, which is essentially just the agent needs to show its work.

**Speaker 8** [04:56:38]
You know, display the use of knowledge and its actions and reasonings. It does that does two things. One, it gives the user the visibility as to when a bit of its knowledge needs to be corrected, and it also, shows them the impact of their contributions, which encourages them to to contribute more. But you can't rely on just the user to correct the agent, which leads us into lesson three, which is that good learning agents absorb context continuously. Identify opportunities to put the agent in the path of real work automatically and absorb every source of environment specific context available so that learning happens ambiently and doesn't rely on the user, you know, calling on the agent explicitly.

**Speaker 8** [04:57:21]
The richer the model of the the the richer the agent's model of the user's world, the the higher the utility. And, ultimately, this you know, all three lessons apply to this single learning loop. And the current state is, you know, individuals that use stateless agents are only ever able to to complete the first section. You use your your agent to act, to do to take an action, to fix a bug, to develop a feature, or even to investigate an incident. But the missing piece here is memory.

**Speaker 8** [04:57:56]
It's operational memory. That's what allows you to complete the loop. And the the three lessons, they all make up this this loop. You can't have, one lesson without the other. If you have, if you make it easy to correct, but you don't visibly improve, then you lose the user's trust.

**Speaker 8** [04:58:19]
If you visibly improve, but you don't ambiently learn, then you're only ever learning from where the user directs you. It limits your learning. And if you're ambiently learning, but you don't allow the user to correct you, then you run the risk of compounding errors. I mean, think about all the dead code or the outdated documentation that's just laying in wait for the agent to stumble on. So I would say that, where I think this is going is that the, agents that we'll be talking about, at this conference next year will be the ones that are investing in this loop today.

**Speaker 8** [04:58:53]
So if you are building a learning agent or you want to learn more, you wanna trade notes, come talk to me. I'd love to talk to you. Thank you.

**Speaker 5** [04:59:05]
There's anybody that has a question.

**Speaker 6** [04:59:07]
Sure.

**Speaker 4** [04:59:21]
Running back. Alright.

**Speaker 5** [04:59:25]
Be speedy. Be expedition.

**Speaker 4** [04:59:29]
Do you think everything you're describing can be accomplished through context engineering, or do you think you need to do some kind of fine tuning or adjust the weights at some point?

**Speaker 8** [04:59:40]
We're not doing any fine tuning. So maybe that answers the question. But I'm yeah. I think it's possible, at least today. And, you know, as Peter Steinberger says, these are the worst the models are ever going to be.

**Speaker 8** [04:59:56]
So I think that they will just, like, continue to improve over time, and

**Speaker 0** [04:59:59]
this

**Speaker 0** [05:00:00]
Get easier. I think also the foundation models are going to be releasing a lot of these features and that we'll we'll start to see, you know, we'll start to see these features being available and not just in specialized agents.

**Speaker 1** [05:00:15]
Oh, good? Okay. Thank you. Alright. That's a question.

**Speaker 1** [05:00:24]
Go ahead. It's like, oh, thank you so much. So thank you so much again. Next, we have Milan Williams from Sync Grip. If anybody have any questions for Erin, you can grab her afterward.

**Speaker 1** [05:00:38]
She's sitting over there. Let's give her a warm welcome.

**Speaker 2** [05:00:48]
Sweet.

**Speaker 3** [05:00:54]
Awesome. Hi, everyone. I'm Milan Williams. I'm a pro oh, can you hear me? Oh, perfect.

**Speaker 3** [05:00:59]
Thank you. Got it. I'm Milan Williams. I'm a product manager at Semgrep. Semgrep builds fast developer first security tools that are used by hundreds of engineering teams.

**Speaker 3** [05:01:12]
My day to day at Semgrep is really about how to make security something that developers like you all are excited to use. So in the last twelve months, my job has changed a lot. As you all have seen today, AI is taking on a whole new world when it comes to cogeneration. It's not just suggesting a few lines of code. It's now hundreds of thousands of lines of code that are mostly generated via these long standing, mostly autonomous sessions.

**Speaker 3** [05:01:41]
And with that shift comes a pretty massive change in how security is thought of. Agents are writing code, but they're also running shell commands. They're touching your file system. They're doing all these actions with elevated credentials and whatever access you've decided to give them. And when something goes wrong, unfortunately, most people have really little idea of what an agent is doing underneath the hood.

**Speaker 3** [05:02:08]
In the vast majority of cases that I've seen with our customers, the root cause is pretty obvious. It's that most of us, myself included, spent, what, maybe five minutes, maybe ten, about six months ago, two years ago, setting up their agent and then never really stopped again after that to think about all of the access that we handed over. And so in this very short talk, I wanna give you three very practical tips that you can set up this afternoon to make sure that if you go viral on Twitter, it's for what you built and not for getting hacked. Cool. The first tip there is minimally scope permissions.

**Speaker 3** [05:02:43]
So before you even prompt or set up any single line of code, stop and ask yourself, what does the agent actually need access to? Most of us wouldn't hand a new intern all of our production systems on day one, and my view is that we should provide the same guardrails to agents. What's on the screen is instructions for GitHub specifically, but you should know that every major source code manager and cloud provider gives you the ability to downscope your access tokens. So if you can avoid it in all costs, please don't use your personal token or anything that's an admin level access. Create something that scopes to what you actually need the agent to do.

**Speaker 3** [05:03:20]
The best case, let's say the agent just gets confused, or worst case, it gets hijacked through a prompt injection or something worse. Your blast radius is only limited to the repo and environment that you've given it, not everything in your system. The second one is set up logging. It's not the most exciting thing, but trust me on this one when I say in every postmortem I've been in, the first question is always the same, which is just what happened. And if you don't have a record, it is very, very difficult to figure out what the agent did, where it went wrong, and how to prevent it from happening again.

**Speaker 3** [05:03:53]
I do have to give kudos to Cloud Code. They do a really good job out of the box here. If you look in your projects folder, you can see every single session and all the actions that happened. You can also get more structured logs if you wanna pipe it to your SIM or any other security tooling that you have. For any other tooling, though, there's not a lot here.

**Speaker 3** [05:04:11]
So I'm sure the rest of the industry will catch up over time. But I think other folks talk about it today, but most agents have some concept of hooks that are built in or scripts that are guaranteed to run after every single agent accent action no matter no matter what. It's a deterministic part of the product. I put together a simple one here that's on the screen that just shows it logs every single shell command that cursor runs with the time stamp associated with it. So it's just four lines.

**Speaker 3** [05:04:38]
It's really simple. If you're on a team, you can distribute it via an m d MDM. Just that way, every developer has it automatically. But just some way so you have a record of everything that happened. So you know if things do go wrong, you have some some proof points to go back to.

**Speaker 3** [05:04:54]
Obviously, you can make this way more advanced depending on your own security posture and what you need, but it really doesn't need to be sophisticated in order to be useful if something does go wrong. And then the last one I've got for you. Great. Let's say your agent has built something awesome. It's generated thousands and thousands of lines of code.

**Speaker 3** [05:05:11]
One thing you need to be aware of is how do you know if that code is secure. Manual code review is probably not gonna scale with long run running sessions. There are lots of options for code scanning, for enforcing vulnerabilities, and for just good coding practices. There are language specific linters like GoSec. Claude has their own built in security review bot.

**Speaker 3** [05:05:31]
Really, you can take your pick. I work at Semgrep, and I specifically work on our MCP server. What we've built integrates with all the major coding agents. It integrates with Cursor, with Cloud Code, Windsurf, whatever you like. I think it's a great tool for this because, in most engineering orgs today, it's pretty rare that every developer is using the exact same agent.

**Speaker 3** [05:05:52]
Someone's using Cursor, Cloud Code, another third thing. Semgrip is a really great way to provide a deterministic set of security checks that run regardless of what end agent someone is using. It runs totally automatically. It runs on every single line that the agent generates, so you don't have to opt in or try to remember to run it. It's totally free, and the docs are on the screen.

**Speaker 3** [05:06:14]
Cool. That's my quick takeaway. So three simple things. Downscope your credentials before you start. It takes two minutes and can save you from a really bad day.

**Speaker 3** [05:06:22]
Wire up an audit trail with hooks. That way, it doesn't need to need to be sophisticated, but it'll be save you from knowing what's went on in your system. And number three, scan the product before it ships. There's lots of free options, but give some rep a try. That's it.

**Speaker 1** [05:06:41]
We have time for two questions. Anybody? If not, let's give her a a welcome again. I mean alright. We have our last speaker.

**Speaker 1** [05:07:06]
We have Ash Lewis from Fostino.

**Speaker 4** [05:07:10]
Hey, Graham.

**Speaker 5** [05:07:15]
Hey. Thank you. Hey, everyone. So, yeah, what I'm gonna talk today about is choosing the right model. It's a really hard thing to do.

**Speaker 5** [05:07:29]
And then once it's in production, maintaining the model accuracy is even harder. So I'm the founder and CEO of Fastenal Labs, who work on a product called Pioneer. And my company before this was a company called DevGPT, which we were using GPT-three for that dev agent. It went viral, which was great, but then we spent $2,000,000 on OpenAI's system, which wasn't so great. But we learned a lot of lessons about building agents.

**Speaker 5** [05:07:56]
So we've put this company together. We're based just down the road in Palo Alto. Most of us are ex Stanford, Google, DeepMind, and Apple. And, yeah, we're fixing this problem of how do you actually put small models into agents. So first of all, the reason why this is a difficult problem is, you know, there's lots of new models that gets released.

**Speaker 5** [05:08:14]
We don't really know which which model is best for which thing. And, actually, that changes really often as well. So we don't really know, you know, next week which which model will be set be out for a specific task. And because of the way benchmarking works, actually, something that's, for example, good at coding might not be good at your very specific type of coding. So other than that, it's really hard to actually fine tune these models, not because it's necessarily difficult to do, but because it's time consuming.

**Speaker 5** [05:08:41]
It's very difficult to get the data to fine tune the models, which it turns out you have that data. It's in your inference logs, but we just don't get it from the LLM providers. And then what's even harder, which again we have through inference, is is to evaluate the model. You know, actually, how how good is the small model at your task? So we've we've kinda put together a solution for this called Pioneer, which is coming out in a few weeks time.

**Speaker 5** [05:09:04]
It's actually on on a wait list right now. And the idea of Pioneer is we think that deploying an open source language model is actually the first step as opposed to that being kind of the the final thing you do after fine tuning. So what I mean by that is we deploy a model, be it be it Lama, Quen, Deepsea, Kimi k two, and then we monitor the inference from from that model. We collect and we label that with with synthetic data. We refine tune, and we reevaluate the model before redeploying the model.

**Speaker 5** [05:09:35]
So the idea is is that, let's say that you've put a model in place for model routing or or code generation. We're actually gonna be repeatedly doing experiments on the background with an agent that's checking can we actually improve what is in in in situation today. And what that looks in reality is that you end up with a situation in which you've deployed LAMR, and it's actually getting more accurate over time as opposed to the alternative, which would be that because of model drift, it's actually getting less accurate over time. And and so so there's a couple ways, best practices to make this work, and the first one is you need to partition your usage. So instead of using, you know, Clawd Opus 4.6 for everything, we actually say, okay.

**Speaker 5** [05:10:17]
Let's use lots of different instances of whichever model for lots of different things, and then we can actually improve all of those models independently. So so no no longer do we actually necessarily mind which model we're selecting. It could be Kimi k two. It can be Lama. It can be Quinn.

**Speaker 5** [05:10:34]
It actually just it's just a description of the task. And then, you know, our agent will go ahead and figure out while we're inferencing what what's what's actually best for the task. So a quick kind of demonstration of how this works. So, you know, if I was to go and ask for this model that turns weather information into JSON blobs, Again, as a developer, I have no idea which model is best for this. I definitely don't have time to fine tune a bunch of models, and I don't really have a benchmark for this.

**Speaker 5** [05:11:02]
So what's gonna happen is our agent's basically gonna go ahead and figure out the answer to the question of which model we should be using. So in this case, as you can see at the bottom here, it's done experiments with Lama, Gliner, DeepSeq, and it's giving you accuracy reports for each one of those. And more importantly, what's gonna happen is as we're inferencing, we can use all that great inference data because we know what your users are actually using the model for to improve the model's performance over time, which has an added benefit of we can actually reduce the cost and latency over time as well because we might be able to use a smaller model for the same use case. So here we are digging into the inference logs here to actually see see what experiments the agent has has ran on our behalf. You can also fine tune models on this platform on the left here.

**Speaker 5** [05:11:47]
We have, like, a Casa style agent where you can you can fine tune models for those use cases as well. But, yeah, this this model is in oh, sorry. This this product is in private alpha right now, and we're launching it in a few weeks' time. So we'd we'd love folks to to join the wait list. Yeah.

**Speaker 5** [05:12:05]
And that's about it. I got a couple minutes left for for questions.

**Speaker 4** [05:12:08]
Yeah. Sorry.

**Speaker 5** [05:12:11]
A little bit fast.

**Speaker 1** [05:12:20]
Great. Thank you so much, Ash.

**Speaker 5** [05:12:23]
Thank very much. Thank you.

**Speaker 2** [05:12:40]
Hello. Hello. How is everyone doing? A huge shout out to everybody who just spoke. It was a great lightning talk according to me.

**Speaker 2** [05:12:50]
How do you all feel? Cool. Let's move on to the next set of keynote speakers. So I will be calling upon Ankit Ankit Mathur from Databricks. Over to you, and big round of applause for him.

**Speaker 4** [05:13:40]
Alright. Thanks everyone for being here. My name is Ankit. I work on infrastructure at Databricks. Excited to chat today about coding agents.

**Speaker 4** [05:13:52]
So representing a lot of work from Arushi, my co speaker, she wasn't able to make it except some travel issues. But let's let's get started. I feel like we live in one of the most exciting times to be an engineer, and and it's really incredible. Like, for many years, the impact of technology has been extremely substantial in the sense that people are working super hard. You know, technology is deployed in society, and it's creating incredible change.

**Speaker 4** [05:14:25]
But what's been rare is having resources like engineers who are really, really incredible and high output. And now we live in an era where it feels like every time a new model comes out, we have just another kind of 10 x engineer. And so there's lots of coding tools out there. I'm sure all of you have tried several of them, Cloud Code, Gemini CLI, Cursor Codex, you know, Google actually has two. So it's naturally, I think it's going to become a huge challenge to figure out how to actually get these things deployed within your enterprise.

**Speaker 4** [05:14:58]
So let's take a little bit of a different perspective on deploying coding agents today and think about it from the perspective of an IT admin. Even though we as engineers are having some of the best times ever, right, this solving this problem is actually a lot of work for IT, especially at large enterprises where data security is important. What are the main problems? Right? If you're actually using multiple of these coding tools, then you typically are having to manage multiple different vendor contracts, different admin consoles.

**Speaker 4** [05:15:29]
Your billing is all over the place. You're getting charged by every different kind of coding provider. You don't actually know who's using what in your enterprise, and it's actually difficult to enforce critical security policies like not having data be used for training for any of these models if you wanna pass PII. These are real problems that most IT admins have to deal with. And so even though for us as engineers, it's awesome to try out every new tool, this is something that actually is slowing down the deployment of these incredibly valuable resources, these incredibly valuable 10 x engineers in today's enterprise landscape.

**Speaker 4** [05:16:06]
When you take a security lens on it, it it gets even more complicated. Right? These are some of the most privileged users. They have you want them to actually have access to everything. You want them to be able to read the description of a task in Jira, action on it based on your cloud infrastructure and your code repository.

**Speaker 4** [05:16:26]
You want it to have access to external APIs so that it can do a lot more information gathering when you're debugging an incident. And and you want it to really be able to read about the context of your company too. You want it to know your code words and all the different design docs that might be in play. So that's actually the power of these tools, but at the same time, you'd wanna make sure that if only your executive team has access to a document that it's not pulled in when an API call from an agent is being made. So these are real problems that are very hard to solve today, and I I actually think these are some of the number one reasons that people aren't using more coding tools.

**Speaker 4** [05:17:06]
What do developers actually do in enterprises? Well, typically, there is some tool of that, you know, has been blessed by IT. That's the tool of record, and everyone uses that one. But what's actually happening with how fast today's landscape is moving is that developers are taking a look at the various complex nuanced benefits of each kind of model and using them for different use cases. So you might, for example, use a different tool for refactoring code than for writing tests and maybe a different one to review the code.

**Speaker 4** [05:17:41]
Like, I myself use Claude code to write my code, but then I use a different model, codecs, to review it. And I found a lot of success in that model because it tends to be the case that if the model wrote the code, it doesn't see fundamental design flaws that might be in it. I mean, by the way, that's like kind of the same as humans. Right? So this is something that's really a workflow that enhances productivity.

**Speaker 4** [05:18:05]
Right? And I think that first slide that we had that talked a little bit about the leverage that these coding tools buy is extremely important to remember in this context. Before, when you used to bet on software, you'd pick one and it would be mostly fine because things were 15% better, and, you know, that's not enough to move the needle on that kind of thing. But if you're getting 10 to 15% more productivity or better code, that's the most kind of valuable asset that you can have. So you should absolutely use the best tool for your use case, even if that's not the one size fits all solution that you have already.

**Speaker 4** [05:18:40]
So it's just extremely limiting as a developer, and I think this will become more and more true as more bottles become amazing at coding. It's already the case that people's different harnesses I mean, we even saw a a number of the talks that we've seen today. A lot of investment and innovation is going into harnesses on top of the models. And so for different use cases, this is going to continue to be true. Now if you take what this what what happened here with the slide before that, where IT admins have a lot of trouble just even managing procuring a few of the tools, and then you have all these developers who are actually just trying to use stuff on their own, and and they're probably gonna work around it.

**Speaker 4** [05:19:20]
You end up with a really, really challenging problem. And so this is and and, like, you know, for the reasons that I said around security, this isn't a trivial thing. This isn't a process problem. This is a real issue that needs to be solved. And so we call this thing agent sprawl, and it's happening everywhere.

**Speaker 4** [05:19:41]
As more and more of us use these coding tools, I really believe that coding tools are gonna be a top 10 cost driver for all of these companies. So this is a really important problem for us to solve. So today, I'm gonna talk a little bit about a technology that we've built to address this problem and and how we use coding tools at Databricks to to maybe just share some learnings from that. What we built was this thing called the coding agent gateway. We really believe strongly that developers should be free to use whichever tools that they want.

**Speaker 4** [05:20:12]
But in order to do that, we need to meet admins and enterprise admins exactly where they're at and help them solve the important security problems and procurement problems that they have. And so we think a gateway helps solve those things. What does a gateway do? Well, it just provides observability. Right?

**Speaker 4** [05:20:29]
The first important thing is always to just collect data on what's going on. And so you want to know which users are hitting rate limits. Who are the people who are your power users? Because they're probably also your biggest champions to make coding tools more and more popular in your engineering organization. You want dashboards to actually show all of this information.

**Speaker 4** [05:20:49]
Right? If it's the top 10 cost driver, inevitably, your finance team is going to care about it at some point. And that's related to cost controls. Right? It it doesn't make sense if you're using three tools to have three different cost controls in different places.

**Speaker 4** [05:21:05]
Ideally, you'd like to be able to say, hey, like, let this person use, let's say, a thousand dollars a month, but across any coding tool that they really want to. That puts freedom and control back in the hands of the developer. But you as an admin can get a single bill from that. And then privacy. Right?

**Speaker 4** [05:21:23]
Like a lot of people work at companies where there's really critical data, there's PII that people don't wanna pass into models and have it be trained on. You wanna make sure that you're controlling for that because that is really, really important to the compliance posture of your company. And and even though coding has gotten a lot faster, compliance hasn't gotten any easier. So we think this is better for kind of all sides of a company. And I'm gonna show you a little bit today of what that looks like in practice.

**Speaker 1** [05:21:56]
Let's see.

**Speaker 4** [05:22:02]
Okay. Cool. So here I'm in my laptop. Right? And what does it look like to have this, like, multi AI coding gateway?

**Speaker 4** [05:22:11]
Well, we have a very, very lightweight wrapper that just reports metrics to our gateway and points coding tools at it. Right? And so all I need to do is this, and it logs in in one place, and boom. You've got Cloud Code here, and you can talk to it. You'll notice that it's point sorry.

**Speaker 4** [05:22:28]
What? Can you increase the font size? Oh, yes. Absolutely. Sorry about that.

**Speaker 4** [05:22:31]
Okay. Hopefully, that's a little bit better. There we go. So you'll notice this is pointed at this like Databricks Opus four six. That's because we're providing that capacity natively within our serving platform.

**Speaker 4** [05:22:50]
So you don't have to then go like kind of yet a separate relationship with a different provider. So that solves your procurement problem. Okay. Cool. So let's say I wrote some code with Cloud Code, and I wanna actually just review it myself before I send it Right?

**Speaker 4** [05:23:04]
All I need to do is something like this. And boom. Now I have Codecs open, and I can do the same thing. Hey, please review my code. And it'll just kick itself off.

**Speaker 4** [05:23:18]
Right? You could do now you can imagine doing the same exact thing for for cursor or for any of the many other coding tools that are out there. And each of these coding tools will have their own strengths and their own weaknesses, and I think that will continue over time. So developers will typically like to will will like to use the tool that's best for the use case in that case. Right?

**Speaker 4** [05:23:39]
Okay. Cool. So I did all this stuff. Right? That's what it looks like for the developer.

**Speaker 4** [05:23:43]
Super easy, not too different from your existing workflow. You're using the same harness that you were using before. But what did it get for the admin? Well, so we have this thing that, you know, looks like an AI gateway, and it has a bunch of frontier models in it. It has open source models in it.

**Speaker 4** [05:24:00]
I think there's a lot of amazing open source coding models that are extremely fast. But critically, it has built in dashboards and reporting that goes into the same place where all your other cost data goes, which is your data warehouse. Here you can see a lot of important metrics, like how many requests have been sent, how many tokens am I using, which cloning tools are popular within my company, which are the users who are using the most, and which ones are they using. And then if you actually are ingesting all those metrics, right, you can start visualizing them in one place too. There's critical metrics like how many lines of code you're adding, how many sessions you're doing that are that are important for people to track.

**Speaker 4** [05:24:40]
And so these kinds of things we feel are extremely important to being able to deploy these coding tools really, really rapidly. So when, for example, the codex models get better, it's not a debate between developers and admins about whether we should get it or not. You just get it. You point it at the same gateway, and you have comfort that you have the same observability that you did before. Let's go back to the slides.

**Speaker 4** [05:25:10]
So there is something I think that we haven't talked about, but is super important. And I think it might even be like the elephant in the room. It's maybe the number one coding innovation coding tool innovation that I have experienced in the last couple months. So what is it? It's MTPs.

**Speaker 4** [05:25:29]
I think like, you know, these API endpoints that people have, giving access to these MTP servers has dramatically expanded what these coding tools can do. Now, rather than like me taking information from my calendar and posting it in explicitly, I can actually have these agents work on my behalf in many, many capacities across work, not just writing code. But in order to do that, the typical setup flow involves local token storage where you store these things in like plain text. They're not necessarily rotated. They might be cut, you know, set up in a custom way, and so that creates these like kind of security concerns.

**Speaker 4** [05:26:08]
And, again, the way that these things manifest is is that they're just not available inside of lots of enterprises. Like, there just isn't a JIRA MCP until there's a reasonable story for how it would be secured. And so this is a problem we also wanna solve. Right? But we don't think it should be using any kind of locally stored tokens.

**Speaker 4** [05:26:28]
And so we've kind of just put this into the same data catalog that people already had. It's fully encrypted. It's it's fully managed. We have auto rotation. And this way, you're just able to point at your API endpoints, and you don't really have to think about it.

**Speaker 4** [05:26:42]
You o off once into Databricks. You already did that for setting up your coding tool. And now you have access to all of those tokens that are either, you know, user pass through. So you kind of, you know, are accessing accessing it as yourself. Or they're a shared token and you're accessing it as the organization.

**Speaker 4** [05:27:02]
That's kind of now in the control of these admins. And so this again enables people to start having lots of MCP tools. So I wanted to talk a little bit about this because I wanted to explain like this thing is how we have deployed coding tools at Databricks. And so I wanted to just share some learnings with the with the group, and and, you know, after this, I'd love to talk to more people and learn from all of you as well. So what is what is a little bit of about Databricks?

**Speaker 4** [05:27:28]
Like, have a lot 2,000 plus engineers across lots of different offices. Lots of code is being written in at least seven languages, and usually someone is pushing for an eighth or a ninth or whatever. So code's being merged all the time. So this is a really, really important problem for us. What was helpful for us?

**Speaker 4** [05:27:47]
Well, I I think like measuring everything was really, really helpful, and I'll show you a little bit of of the dashboards that we've built. Everyone needed to be leaning in. We have awesome developers at Databricks, but it took a lot of effort to convince people that they needed to spend all their time learning how to use these tools. It's not just like do the same stuff you were doing before. I feel there's at least a little bit of learning curve on how to actually use these things effectively.

**Speaker 4** [05:28:14]
And to do that, every single person, not just like the newest engineers, needs to lean into using these tools. And finally, the industry is moving at just an incredible pace. New models come out every week that improve the frontier, And so it's no longer true that in order to move the frontier, you needed to do five years of of research. Like, the frontier is moving every week, so you need to move fast as well. So what do we what do we have that, like, kind of developers can use?

**Speaker 4** [05:28:43]
We have this harness, like, you know, I showed it to you locally. We call it internally Isaac. Isaac allows you to use any of the coding tools, but it's a single interface that people can use to launch them so that they get unified reporting on metrics as I had shown as and so that like a bunch of configurations under the scenes, for example, MTPs and token capacity can be configured. So within Isaac, we route the metrics through our coding gateway as well as our MCP logins. And the coding gateway is then dumping that usage data in those dashboards which I showed.

**Speaker 4** [05:29:19]
The capacity is pointed at a single place. So we have one place where our finance team gets all the the full bill for all the different models. And we have tool calls that go directly through this gateway. So every day when I start my work, I log in to Isaac and Isaac me into a new you know, refreshes my token. And now I'm build I'm able to use all the MCP servers I had connected.

**Speaker 4** [05:29:41]
So this is like one of the internal dashboards that we have. I I wanted to show exactly how important this is for us. The default the dashboard I had shown you was the default, but the critical piece of data is that the dashboard is just built on tables within Databricks. And so you can reorganize that however you want. We have executive views on the dashboard for tracking how many what percentage of the company is using coding tools, which ones they're using, how many lines are being written.

**Speaker 4** [05:30:08]
And then we also have team level drill downs where, you know, people can in, like, look in within specific orgs, like who is using the most tools or the most coding tools. So so this is really, really critical, and this is the dashboard that our executive team now reviews every single meeting. In terms of MCPs, right, we've registered them on one page. And when you log in, you can actually configure which connections you want. Like, do I want to be connected to Glean, Jira, and Google, or just a few of them?

**Speaker 4** [05:30:40]
It is important to actually configure that because if you just pick every MCP server, you're actually flooding the input context of your requests and making them slower and more expensive. So that's a decision that users still have to make today. But then, yeah, like I said, right, all I do is when I log in as a developer, I get this URL, I click on it, I authenticate, and I'm good to go. Everyone needs to be leaning in. I I I always like showing this slide where this our our CEO, Ali, actually is writing code now using Isaac and and and modifying it as well.

**Speaker 4** [05:31:17]
We would not have been as successful deploying coding coding tools within data within Databricks without explicit executive, like, demand to deploy these things. And so this is really, really critical, I think, to to expanding the impact of this technology. And finally, we think the bottlenecks are shifting really dramatically. I I I wanna talk about, like, coding code reviews. I I feel like it's much, much harder, and the volume of code code reviews that, you know, at least I personally now have is way way up, and it feels like the tooling hasn't been able to keep up.

**Speaker 4** [05:31:53]
So I think there's a huge amount of open opportunity for better code reviews and better tools to do these things, but this isn't a solved problem. And I would now say that at least the Databricks, our velocity is most bottlenecked by this one thing, by our ability to scalably scalably review this code. Same thing with CI. If you're deploying 10 to a 100 agents per human, you've suddenly made massive scalability requests from your CI team. And so our CI is is now costing us way more than it did before, And it's really, really painful when people mess up, for example, the dependency graphs and lots and lots of tests are running for every change.

**Speaker 4** [05:32:40]
So it's more important than ever to have the right abstractions between projects and between different services so that this becomes less of a problem and agents have a faster dev loop. And the final thing is testing. The models are still not like perfect at admitting code. And at least one thing that we have discovered is giving them an explicit validation signal on the code very early in the life cycle, allows quality to go up and allows the model the model and the agents to enter virtuous loops where they're improving the code effectively. One of the things engineers do is they have context on the world in which their code will be deployed, and they reason about the way that they write things in that way.

**Speaker 4** [05:33:25]
The models don't always have that context. A lot of that is in our heads or in a document somewhere, and it takes a lot of explicit effort to go and write that down, and then also to design shift left kind of testing methodologies where you're able to call command and have the tool tested. So we, for example, had a technology that was kind of like used by some people that's now used by a lot of people, which allows you to like develop a service and then swap it into a staging instance. This is incredible for the agents because they're able to write their code, and then you can swap it into a realistic environment where you can use the product. Without that, like when without that thing in the middle, what we found is that the agents were often writing code that was completely unrealistic to deploy or was extremely unperformant.

**Speaker 4** [05:34:15]
So more and more investment needs to go into shifting this kind of testing left. So we would love to just learn from everyone here who's using coding agents. Thank you for for listening. If you build coding tools and wanna supercharge your users experience, like, please reach out to us. We're really focused on bringing things like governance, observability, and privacy for coding tools, and we really wanna help developers use all of them.

**Speaker 4** [05:34:39]
Thank you very much.

**Speaker 6** [05:34:44]
I think we got time for we got time for some questions. Who's got something? Anything? Where are

**Speaker 5** [05:34:53]
we at?

**Speaker 4** [05:34:53]
One in the back.

**Speaker 6** [05:34:56]
That was a that was a good talk. There's one in the back? Oh, way back. Alright. Make me run for it.

**Speaker 6** [05:35:00]
Here we go.

**Speaker 7** [05:35:07]
Yeah. Hey. Thank you so much. Leak to talk. Love how you covered the MCPs.

**Speaker 7** [05:35:11]
Curious how you would integrate skills and kind of the proliferation of skills and knowing what's actually happening in your your organization, who's using what skills, and why.

**Speaker 4** [05:35:23]
Yeah. That that's a that's a great point. And it and it's something that we haven't really built out yet, but which is super top of mind for us because, yeah, as soon as skills launched, they just like, every team has a skill now, and most of them are doing the same thing. So it doesn't feel like there's enough organization yet where, you know, the where people within engineering are able to leverage the work other people did. So I do think there's a lot of work to do.

**Speaker 4** [05:35:50]
To be honest, I don't a 100% know how to solve that. Like, one thing that would be useful at least for me, from my perspective is if you could like, when I'm introducing a skill, if if there was some, like, way to know that there was a very similar skill already, that would be great because then I would just add to that. But it feels really intractable for humans to read, like, thousands of markdown files. So not sure the answer to that, but I do think skills are gonna be important part of governance.

**Speaker 8** [05:36:19]
Just a quick question on Isaac. I know you measure HTTP requests, but what about actual tool calls on the computer that's running? Do you have, like, any performance metrics that you level up so that, let's say, a particular command line tool is being used a lot by the organization? Do they get visibility on that?

**Speaker 4** [05:36:39]
Yeah. Great question. Yes. So one thing I wasn't able to show is that but but which is there in production already is that with MLflow, you can actually trace all the Cloud Code requests, and we do that as well. So we're ingesting, you know, thousands of of tray tens of thousands of traces per day.

**Speaker 4** [05:36:58]
And one of the things we discovered from that particular piece of data is that Claude code, for example, like to do a lot of file search. And we had, like, like, we in our cloud environment, for some reason, the standard one it wanted to use was very slow. So at the top level repo Claude MD, we actually added a very explicit instruction, which was like, please use RG to search for stuff. Do not use anything else. And that was super valuable and would not have been something people would have noted like, figured out easily without that.

**Speaker 9** [05:37:35]
Thanks. Earlier, you had mentioned that as part of the gateway, you have to pick and choose the MCPs so you don't flood with context. So this leads to a couple of things. How do you curate the MCPs which

**Speaker 10** [05:37:47]
are

**Speaker 9** [05:37:47]
allowed? And also at what point do you need an MCP for your MCPs?

**Speaker 4** [05:37:55]
Yeah. That's like really related to this like title for like, you know, you have this like meta multiverse thing. Yeah. I I think that, for example, some of the folks I know who build harnesses have spelt have spent a lot of time on this on on MCP tool selection. So I actually think that and and, like, recently, Anthropic launched tool search as a tool within the model.

**Speaker 4** [05:38:20]
So I do think the harness layer is going to figure out soon how to manage the MCPs. Today, I think it is still true that developers are best off managing it on their own, like, per use case. I don't think that will be true like even two months from now. I hope we don't need MCPs for MCPs because that sounds pretty complex, but who knows? I I don't think that will be needed because MCP itself is kind of just a wrapper on like existing APIs and, like, a standardizing methodology for existing APIs.

**Speaker 4** [05:38:51]
So, hopefully, we don't need a layer in front of that. I do think we need, like, a governance layer for those MCPs.

**Speaker 10** [05:38:58]
Cool. One one of the things I've seen, I think the thing you mentioned about being able to write code locally and then hot swap it into a staging or preview environment seems to be one of the biggest bottleneck outside of, like, overall lots of code to review and things like this. Like, what do you think is what have you seen as state of the art in terms of, like, the time it takes to go from one or more repos with local changes to something that a user can interact with?

**Speaker 4** [05:39:23]
Yeah. I I think this is something where each, like, organizations build tools are different. And so it's like an area for the testing teams to invest in. I think historically, one may have argued that, oh, it's like, why don't you just write unit tests and then deploy it into dev? So I think that it's an investment everyone needs to make on their own.

**Speaker 4** [05:39:44]
But, like, for people, for example, who use Docker based services, like, not hard to swap in a new image, but you do need, like, some way of, like, routing to that service. And so for integrating with this like hot swap technology required our services to actually update themselves. So we have code in our services that basically says, if you're in swap mode, like point at some other thing in from a networking perspective. So it took work to onboard to it.

**Speaker 6** [05:40:14]
Excellent. Ankit, thank you. Let's give it up, everybody. Thank you, sir. That was awesome.

**Speaker 6** [05:40:19]
Dude, very stoked on that presentation. Alright. Before I bring up Dex, I gotta say I met James, and James yeah. Can you stand up real fast? James told me this morning that he is going we can't see the QR code.

**Speaker 6** [05:40:34]
You gotta hit it up. He's gonna be having dinner tonight, and everybody's invited. So if you wanna go, just scan that QR code real fast and go hang out with James. That's awesome. And that's what we're going for here.

**Speaker 6** [05:40:48]
That is great. Yeah. You rock. Yeah. That's I I like it.

**Speaker 6** [05:40:52]
I like it too. Okay. So I'm gonna bring up Dex. Earlier, somebody said we need to have a mustache competition. I don't think that's gonna happen, but I will say that he gave us 200 slides that he's about to present.

**Speaker 10** [05:41:06]
Woah. Woah. A 100 a 158. A 158.

**Speaker 6** [05:41:08]
We're gonna keep him honest on the timing. Alright? So let it start now.

**Speaker 10** [05:41:14]
Amazing. Buddy. Let's do it. What's up, everybody? Dex.

**Speaker 10** [05:41:17]
Yeah. I am Dex. This is a talk with a very long title that I'm not gonna read because we're on the clock now. I have been talking about coding agents for quite a while, basically, since, like, August. We did a long talk in November.

**Speaker 10** [05:41:32]
There's this methodology that we've been talking about a lot called research plan implement. Lot of upvotes on Hacker News. There's probably 10,000 people who have gone to our open source and grabbed our prompts and are using them internally from small startups up to the enterprise. It all started with this guy. This guy, Igor has anyone seen this talk?

**Speaker 10** [05:41:50]
Yes. Yes? Okay. So Igor went in and he said, like, okay. Cool.

**Speaker 10** [05:41:53]
We're using a lot of tokens. We're spending a lot of money to get AI developer productivity. But what he found was that it actually tends to lead to a lot of rework. Like, you are shipping 50% more, but half of that is just cleaning up the slot from last week. And the other thing they found, these are last year's numbers, so this does not account for Opus 4.5.

**Speaker 10** [05:42:09]
So I would I would inflate this a little bit, but, like, it's great for low complexity greenfield tasks, not great for high complexity brownfield tasks. And so I could give you a talk about RPI and why it's great, but that would be boring. And there's other talks. So if you haven't seen them, go watch them. They'll give more context, but I'm gonna tell you everything we got wrong about RPI today.

**Speaker 10** [05:42:32]
We thought we had to say I think thing figured out. I am am humble enough to admit when I was wrong. So we got a couple things wrong. One thing that's very relevant if you've been on Twitter today is I don't think it's okay to not read the code. I also don't think you should read really long plan files.

**Speaker 10** [05:42:49]
We'll get those two are related. And, no, Claude should not be allowed to have you if you're writing production code that is used by users and you're gonna get patient 3AM if it's broken, no slop. This is the year 2026. No more slop. So we're all on this journey.

**Speaker 10** [05:43:04]
We're all figuring this out. We all are wrong all the time. We didn't get get a couple things right. There is no magic prompt. Do not outsource the thinking.

**Speaker 10** [05:43:11]
You, the engineer, are an important part of this process and seek leverage. There's a lot of code being written. Find ways to make sure it's correct without having to read all of it and resteer after the fact. So lots of people I'm sure have heard of research plan implement. Has anyone actually run this Claude command research code base?

**Speaker 10** [05:43:28]
Okay. Cool. Leave your hand up if you've run it like this. Tell me how this system works. Has anyone run it like this of like, hey, I wanna build this thing.

**Speaker 10** [05:43:36]
Go do the research. Okay. Or maybe go fetch a ticket or something. What about the create plan, prompt? Okay.

**Speaker 10** [05:43:43]
Couple hands. How many of you run it like that? Know, hey. We gotta go build this thing. Yes?

**Speaker 10** [05:43:49]
Has anyone run it like this? Work back and forth with me starting with your open questions and outline before writing the plan? Okay. Some of you found out about the magic words. A lot of people didn't, though.

**Speaker 10** [05:43:59]
We'll get into why that's a problem. So since October, we've basically worked with thousands of engineers from tiny startups all the way up to Fortune five hundreds. And we would find over and over again, we would give these tools to an expert, and they would get great results. They would go and sit and talk to Claude for seventy hours a week, and then it starts shipping like crazy. And then they would go give it to their team, and the results were not always so good.

**Speaker 10** [05:44:20]
And so people weren't getting good results. And so we got in the trenches with our users, and we went to go figure out what was going wrong. And the first thing that was going wrong was people were not getting good research. So we talked about this in November. This is, one of the only slides I'm reusing, but you would pick a zone of your code base.

**Speaker 10** [05:44:35]
You would say, oh, we're gonna build something over here. And then you would launch in a coding agent session to go send these sub agents through these deep vertical slices through the code base for just the context, compressed context about what is the thing we're about to go build. Right? And we said keep things objective. Discourage opinions.

**Speaker 10** [05:44:52]
Don't actually put any implementation details in there. You just wanna compress the truth. What is true about how the code works today? And a skilled engineer was really good at taking, okay. Here's my ticket.

**Speaker 10** [05:45:02]
Let me write some questions that will cause the model to go touch all the parts of the code base that matter. So if it was, you know, add a new endpoint to reticulate splines across tenants, we would say something like, okay. Tell me how endpoint endpoints work and trace the logic flow for everything that touches splines and go find the workers that do all the reticulation. So if this is your ticket, a lot of people would run it like this. They would just say, hey.

**Speaker 10** [05:45:24]
Research code base. Here's what I'm building. And the problem is that a good research is all facts. But if you tell the model what you're building, then you get opinions. And we don't we'll get into why the model shouldn't have opinions later.

**Speaker 10** [05:45:33]
Comes back to this thing that Jake from Netflix came up with, which is do not outsource the thinking. The other thing that wasn't working is people were getting not great plans. And, basically, there were these steps built into this planning prompt that was this single giant, like, monolithic thing with 85 or more instructions. And it had these steps in it of, cool. Present design options to the user, get feedback on the structure before you actually go write the plan.

**Speaker 10** [05:46:00]
And so a good planning session would look something like, you know, you have your Claude system tools and your prompt, and then you say, hey. Create plan. Loads the skill, looks at your ticket, loads your research doc, launched a bunch of sub agents to go find a bunch of things that are true about the code base, just confirm some stuff that wasn't maybe in the research. This is all one big context window, by the way. Usually, I'll use these columns to mean separate context windows, but today, this is all one session.

**Speaker 10** [05:46:22]
I just slides are sideways, so I had to put them on next to each other. But the agent would come and ask questions. So, okay. Here's our options for question one. User would pick an option.

**Speaker 10** [05:46:31]
User would pick an option. And then eventually, it would say, cool. Here's the order we're gonna do the things. What do you think? And the user could say, well, we need to add a testing step up front, and I wanna swap phases three and four.

**Speaker 10** [05:46:41]
Assistant would give the new outline of the phases. Then the user would approve it, and only then would we write our plan file. Complex process of aligning with the user on what was was gonna be built. But for about 50% of people, maybe more, if you didn't prompt it with this work back and forth with me or Opus was just feeling dumb for that that particular hour of the day, it would just take the stuff and it would just immediately go and write the plan out. And so you would get this and then it'd be like, cool.

**Speaker 10** [05:47:10]
Wrote the plan. Didn't ask me any questions. Made all the decisions for me. Yikes. So we give the tools to people and some people got good results and some people didn't.

**Speaker 10** [05:47:19]
And we dug in and we're like, what's the difference? And people would literally say this to me. They're like, well, you have to say the magic words. And I found myself in workshops full of enterprise engineers saying, well, guys, guys, guys, yeah, here's the software, but don't forget to say the magic words. It was quite frankly, it was embarrassing.

**Speaker 10** [05:47:34]
But if you said this, work back and forth with me starting with your open questions and outline before writing the plan, then the agent wouldn't ask you the questions. And this isn't the user's fault. If you built a tool that requires hours and hours of training and reps to get, like, good results from, go fix the tool. And so I'll talk about how we did that. But why these steps were getting skipped?

**Speaker 10** [05:47:53]
The one of the big takeaways I'll give you today is, like, you have an instruction budget. My cofounder Kyle is somewhere over here. He wrote this really good blog post in December or November, I guess, technically. They basically cited this archive paper, which, again, this is from last year. So the number is probably a little bit higher now, but that Frontier LMs could only follow about a 150 to 200 instructions with, like, good consistency.

**Speaker 10** [05:48:15]
Anything more than that, and it's kind of half attending to all of them, and you're rolling the dice. So if you have a prompt with 85 instructions and your CloudMD and your system prompt and your tools and your MCP, yeah, you're not likely to get full adherence to the workflow. So more on how we fix this later. The other thing that I think really wasn't working for people was, like, we advocated for reading the plans that were output. This is me on stage in November telling people you have to read the plan.

**Speaker 10** [05:48:44]
Otherwise, it won't work. Some people even would PR their plans and code review them together. But a thousand line plan tends to be about a thousand lines of code within 10% or so, and plans can have surprises. So you would go and you would review the plan, and then you would go write the code, and it would be different. And so you're telling you're asking one of your coworkers, okay.

**Speaker 10** [05:49:03]
Go spend an hour reading this and tell me what's wrong with it, and then you would go implement it. It would be different. They have to go read the code again and see what the surprises were and what changed. And so this isn't leverage. Leverage is about, like, do less work to get more output.

**Speaker 10** [05:49:16]
So the new advice, don't read the plans. Please read the code just because it's it's the same amount of work. And, like, look for leverage elsewhere, and I'll talk about how we found better leverage. And you may say, hey, Dex. In August, you said don't read the code.

**Speaker 10** [05:49:30]
You said the the plans are enough. Just don't just just go to ship and let Claude do its thing. I was wrong. I am humble enough to admit when I was wrong. This is actually a very big conversation right now.

**Speaker 10** [05:49:40]
Please, please read the code. We tried not reading the code for, six months. It did not end well. We had to rip out and replace large parts of that system. And you would say, hey, Dex, but other people don't read the code.

**Speaker 10** [05:49:51]
Bids, 300,000 lines and counting. No one's read that code, allegedly. OpenClaw, Pete's like, okay. You know, I know the structure and the pieces and how they fit together, but I don't read every line of every PR. These are OSS projects.

**Speaker 10** [05:50:05]
They don't charge money. Nobody gets paid at 3AM if it's broken, and no one gets fined millions of dollars if it's done wrong. I will also say though, these are OSS. They are very, very cool projects. I am humbled, deeply humbled by the accomplishments of the maintainers, and the stakes are still high.

**Speaker 10** [05:50:22]
Like, if you break open, Claude, a lot of people are gonna be upset, but they are different than if you're, say, working in a regulated industry shipping production SaaS code. So if you have people who depend on your code, please, I'm begging you. Please read it. Please read it. We have a profession to uphold.

**Speaker 10** [05:50:38]
2026 is supposed to be the year of no more slop. Literally, everyone is talking about the difference between slop and craft. This is why I'm a little mid on agent swarms and the whole gas town thing because you still need to be able to ensure quality, and, like, going 10 times faster doesn't matter if you're gonna throw it all away in six months. So shoot for two to three x. That's actually another talk of, like, how you measure this and how you actually get there and maintain, like, a near human level of quality.

**Speaker 10** [05:51:05]
But I'll talk about the goals and like what you should think about if you wanna get there is you should have high leverage planning. You should not outsource the thinking, read and own the code, and ideally, will avoid magic words. So we got better research. We got better plans. We got better leverage.

**Speaker 10** [05:51:21]
I'm gonna talk about each of those as far as like in general what we and like in specifically what we did and also some general concepts as you're building workflows and systems around coding agents what you can do. So we talked about a skilled this is the least exciting one, but talking about how a skilled engineer could detangle the ticket to the questions to the research, and then the research would be very objective. Basically, we just hide the ticket from the context window that's doing research, and we do it deterministically. So, basically, you have one context window to generate questions and then a fresh context window with no knowledge of what we're building to go make your research doc. This is pretty trivial.

**Speaker 10** [05:51:55]
If you're familiar with the concept of query planning, it's similar in concept, but for, you know, LMs reading through code bases. So I've been hacking on agents for a while, and before we did the coding agent stuff, I wrote this paper called 12 factor agents, which was, allegedly the first time anyone was, like, talking a lot about context engineering. There's two ways to read context engineering, and most people jumped in. Is anyone building, like, rag pipelines? Is it raise your hand if you built a rag pipeline.

**Speaker 10** [05:52:23]
Okay. Some people are feeling not, like, not raising their hands today. But it's like, okay. Put more inform you put too much information in, the model can't make sense of it. I actually think the more interesting read of context engineering is, like, better instructions and simpler tasks and smaller context windows.

**Speaker 10** [05:52:38]
Of course, we all know Jeff now. I don't have to introduce him anymore. He said that I used to to tell people who Jeff was when I was talking. We talked about this, like, context window thing is the idea of the dumb zone, which is, you know, you have about a 168,000 tokens and 200,000, but some of them reserved for output. You have various things that they're for.

**Speaker 10** [05:52:56]
And around, like, 40% on average depending on what you're doing and how much of your context is user messages versus files and all of this stuff, you hit this point where you have degrading results. And, obviously, sometimes you can get still good good enough for you results at 60%, but the less of the context window you use, the better results you will get. Our friends at Databricks were just talking about you have too many MCPs. The whole context window is full of instructions about how to use a bunch of tools that you don't care about. And then by the time you're writing code, the model is, like, not good at following your instructions.

**Speaker 10** [05:53:24]
So you're not just giving the model too much information. You're also probably giving it too many instructions. And so the idea of what we're doing was this thing, like, makes a lot of sense. Use prompts for control flow. This is a customer support example, but, you know, if it's a complaint, go do this.

**Speaker 10** [05:53:38]
If it's product feedback, go do this. If it's a billing issue, go do this. And what you can do instead is you can instead of using prompts for control flow, you can kinda classify the input and then feed it to a series of smaller, more focused prompts where there are far fewer instructions and far fewer actions to choose from. I'm sure many of us have already done things like this to improve the performance of pipelines. So this was a single mega prompt with 85 instructions.

**Speaker 10** [05:54:03]
And if you did it right, you would go through all these different steps. All these different phases were part of that. And if any of the instructions didn't get followed, you would skip the things that made this really high leverage. So we split it across several prompts. And so, like, before it was research, plan, implement.

**Speaker 10** [05:54:15]
Now it's questions, research, design, structure, plan, work, tree, implement, PR. We're actually not gonna have time to talk about the implement side of the thing today, but we split up the planning into a design discussion and outline and a plan. And before it was 85 instructions, now they're all less than 40, which is really exciting. And I think some of them could actually be even smaller. We're still iterating on them.

**Speaker 10** [05:54:35]
The lesson is don't use prompts for control flow if you can use control flow for control flow. Like, the if statement is really, really powerful, and LMs are really good at classifying things. This is not just true for coding agents. This is any AI LLM based system you're building. And it's really funny because we were writing all this stuff, and we got on stage, we said, like, full fat agents don't work.

**Speaker 10** [05:54:53]
Don't just call tools in a loop. Do context engineering and build workflows and graphs and micro agents. We told everybody don't do this. And then we turned around in August, and we're like, oh, alright. But this Cloud Code thing's pretty good.

**Speaker 10** [05:55:04]
And we turned around, we wrote this giant monolithic prompt. So we figured it was time to actually go drink our own Kool Aid. Mind your instruction budget. How do we get better leverage? So we split things up to get better instruction following.

**Speaker 10** [05:55:17]
Right? These three different phases. But we also got more leverage. I'm gonna talk about why. Because even if the plan is a thousand lines and the code is a thousand lines, your design discussion might only be 200 lines, and you get a lot of opportunities to resteer in that moment.

**Speaker 10** [05:55:30]
And so what this looks like is basically where are we going, what does the final solution look like, and it has, you know, the current state, the desired end state, It has the patterns to follow. How many of you were, like, sent off a coding agent and it, like, found the wrong way to do a thing in your code base and it followed the bad patterns? Yes? Right. This is your chance to go read all the patterns it found that it thinks are relevant and be like, nope.

**Speaker 10** [05:55:50]
That's not how we do atomic SQL updates. That's some engineer that doesn't work here anymore, and it's crazy, and everyone hates it. Go find the way we do it over there. It'll keep track of resolved design decisions that we've made. It will ask open questions.

**Speaker 10** [05:56:01]
This is sort of like taking Cloud Code plan mode and the ask user question tool and just brain dumping it all to a single document that you can interact with is, like, moldable and flexible. Matt Pocock has this idea. He calls it the design concept, and it's this idea of, like, the thing that is locked up in this context window that is the shared understanding between you and the agent of what's being built and how. So we put it in a two underline markdown artifact. And so we now have human agent alignment.

**Speaker 10** [05:56:29]
And the idea here is, like, you're forcing the agent to brain dump out all the things it found, all the things it wants to do, all the things it thinks you want and ask you questions about things it doesn't know. So you can do brain surgery on the agent before you proceed downstream. It's all about do not outsource the thinking. You wanna give the agent every single opportunity to show you what it's wrong about before you go write 2,000 lines of code. So 200 lines instead of a thousand, a little bit more leverage.

**Speaker 10** [05:56:54]
We also get better leverage from the outline. So if design is like where are we going, the structure outline is how do we get there? Or if you're an engineer who is miserable because of sitting in meetings all day, there's the, like, architecture review, and then there's the sprint planning meeting. What are we gonna build, and then how do we break it down into tasks? And so we take our design, and we take it to ticket and the research.

**Speaker 10** [05:57:14]
We build up a new context window, and we create the structure outline. And this is basically high level overview of the phases, not the exact code we're gonna write, but just kinda what it's gonna look like, what order we're gonna do the changes in, and how we're gonna test it along the way. Now I don't actually test in between every phase, everything I'm building, but if it's sensitive or if it's hard or if it's complex, I wanna be able to catch it before it goes and writes all the code. I wanna make sure each two, three, 400 line block is correct. And these docs mean lighter reviews.

**Speaker 10** [05:57:43]
Instead of reviewing the plan, this is two things for the same feature. Plan, eight pages. Structure outline, two ish pages. Much shorter. I like to think of this has anyone ever written a c header file, a dot h file?

**Speaker 10** [05:57:55]
Yeah. Okay. So if the plan is the implementation, the outline is the c header files. Just here's the signatures and the new types that we're changing, enough again for you to see what the agent is thinking and correct it if it's wrong. And the reason why we do this is despite, like, every single model and trying to prompt this out and eval the hell out of this, we cannot get models to stop writing horizontal plans.

**Speaker 10** [05:58:16]
Or it, like, this is the best way to fix their need to write horizontal plans. And when I say horizontal plans, I basically mean you start with models love to, like, we're gonna do all the database, and then we're gonna do all the services, and then we're gonna do all the API, and then we're gonna do all the front end. And before you know it, you're on the other side of 1,200 lines of code, and it's not working. And now you have to go figure out which part is broken because there was no nothing really to test along the way, whether the model is verifying it or whether you, the human, are jumping in and checking it's correct. And so what we've seen work really, really well across orgs of all sizes is what I call vertical plans.

**Speaker 10** [05:58:50]
This is how I build when I'm like, before AI, I would, like, make a mock API endpoint and then get it working in the front end and then wire that and then mock out the services layer and then do the database migration and then put everything together. And so even though it's the same amount of code, you have these, like, checkpoints where you can see if it's working. If And it's not, you can pause and fix it before you go try to do the rest of it. So these are markdown docs too. Like, you can and should ask for more detail.

**Speaker 10** [05:59:14]
They start high level, but, like, here's an example of, like, I don't think you're gonna get this right. Tell me what you're thinking. And then, like, dumped out the types and the signatures. And then getting better leverage from the plan itself. I mean, again, like usual, like we've been doing, we just take that artifact.

**Speaker 10** [05:59:28]
We build it up with all the previous artifacts, and then we can go build the plan. And it is the same if you use create plan. It's the exact same template, exact same setup, exact same prompt, but this is a tactical doc for the agent. We've already done enough aligning that, like, I'm just gonna spot check this, and then we save the deep review for the actual code. And so if you've used any of the RPI plans, they look like this.

**Speaker 10** [05:59:48]
It's the model saying, hey. Here's all the changes I'm gonna make. The most important part of this leverage is not just about you and the agent, though. Like, human agent alignment is important, and knowing what the agent's gonna do and correcting that is is good.

**Speaker 0** [06:00:00]
But it's also you know, if you're working with a team of engineers, we found a lot of value from taking these design discussions, these structure outlines, and review. I said don't review the plans, but these shorter docs are really, really good. I I am not the code owner of most of our code at HumanLayer, my cofounder is, and I send him my design discussions on purpose. We don't have a required step, but I wanna I wanna know that when we get to code review, it's just gonna be like, yep. That's that's what I wanted.

**Speaker 0** [06:00:28]
That's it. That's it. So any any of my bad decisions are headed off on a 200 line doc before I've gotten and written the code and gotten it working and I'm attached to it. And so this is really, really powerful. Before AI, we basically the

**Speaker 1** [06:00:41]
way another way to think about

**Speaker 0** [06:00:42]
it is like time savings. You would say, okay. It's a two day feature. I gotta do all this stuff. The coding is probably two to four hours.

**Speaker 0** [06:00:48]
If you just pick up Cloud Code and use it to ship for you, you do get some speed up because now the coding takes twenty minutes. It's still a two day feature because I still have to, like, align with my team on what we're gonna do. I still have to get a code review and fix stuff. Maybe I'm working across repos that I don't personally own, and then we still have to verify and test it. But if you use AI to help you with your planning and alignment, then you also save time there, and I think you get much better alignment.

**Speaker 0** [06:01:13]
And so your code review and rework is also much shorter because you already know it's coming. The team that's reviewing it already kind of, like, had their chance to resteer you, and really good teams do this. It's their meeting that's called architecture review where we decide, you know, what's our technical design doc and how we're gonna build this. So, as far as testing and verifying, sorry. I don't have a good answer for you.

**Speaker 0** [06:01:31]
It's a whole other talk. If you went to Drew's talk downstairs, go find Drew Bruning after this. He will tell you all about testing and verifying. Let's put this all together. So we have these five stages of research and planning.

**Speaker 0** [06:01:43]
The process is basically questions, research, design, structure outline, plan, work tree, implement, finally, pull request. That didn't make a very good acronym, though, so we just picked the ones we liked, and we're calling this CRISPI. So RPI to CRISPI. That's the there you go. What's next, and what did I not have time to talk about today?

**Speaker 0** [06:02:04]
Three steps is already a lot for some people to learn, and now there are seven. I thought we're supposed to make this easier for teams to learn this and adopt it. We can talk about how we're, like, thinking about that. The idea of how do you measure the impact of doing this in engineering teams, I think, is like we've been trying to measure developer productivity for fifty years, and we still don't know how to do it very well. And then it's like if you're a central kind of platform team rolling out changes to everybody in your org, how do you make these prompts better?

**Speaker 0** [06:02:31]
How do you make this engineering system better? I mean, we're just talking about, oh, every team has a skill now, and we wanna consolidate and make that shared and let people benefit from each other's learnings. How do you make that stuff better without, like, breaking somebody's workflow or regressing it for some some team? If you wanna help us, if you're in San Francisco and you're working on critical systems and you wanna, like, figure out how to get coding agents to do more, let's chat. We're also hiring.

**Speaker 0** [06:02:57]
Send us a note either way, founders@humanlayer.dev. We're building the IDE that orchestrates this stuff for you. You don't need this to get this value out of this, but this is the kind of stuff we're working on. If you wanna hang out, I'm doing a sandbox research hackathon on Saturday. We're gonna just get together with a bunch of cool builders, test all of the sandbox providers together, and see which one's the best, and then share our learnings.

**Speaker 0** [06:03:21]
I'll be also be at the Daytona Compute Conference. And if you feel like coming to Miami, AI engineer Miami is gonna be really fun. We'll be giving the updated version of this talk with more stuff that I don't have time to get to today. Thank you so much to all of you for your energy, to Dimitrios and the entire organizing squad.

**Speaker 2** [06:03:38]
Whoo. Good luck. Questions. Who's got a question for Dex? That was super fast.

**Speaker 2** [06:03:45]
I like it. I was very doubtful that you were gonna get through it, but I it.

**Speaker 3** [06:03:49]
Alright. I'm I'm curious about reading the code. Like, it's not scalable. Right? Like, are we are you gonna be saying the same thing in six months?

**Speaker 0** [06:03:56]
I mean, six months ago, said not to read it. And so I think everyone who is saying don't read the code now is gonna be in six months being like, yeah. We had to throw that out. There's something there's something in the middle. Right?

**Speaker 0** [06:04:07]
We're binary searching through the space, of how much of the code should you read. I think, yeah, the idea is if you still read the code, you can still get two to three x speed up, and that's actually better business outcomes than than going 10 x faster and shipping a bunch of slop and hoping that, you know, GPT seven will fix it for you.

**Speaker 4** [06:04:30]
K. Hit things, Nick. Awesome talk. Curious your thoughts on, like, the software factory. I think it's like strong DM that's saying the opposite, which is like never have a human read either side of it.

**Speaker 4** [06:04:45]
And I think that pushes us further into evals and stuff like that. So what is your thinking on that?

**Speaker 0** [06:04:53]
Yeah. There is a whole class of like, there's a whole rabbit hole you can go down with, like, formal verification and TLA plus. Or I talked to a guy who's building a new TLA plus. There's TLA plus plus that is like, okay. What if we don't read the code?

**Speaker 0** [06:05:04]
How can we actually, like, formally verify everything that's working? I think there's a lot more to be built, and I think there's a lot of people right now who need to ship, like, code to production systems faster. So, like, maybe someday, but, like, I used to cite Sean Grow's talk where he was like, it's just the spec. Just write the document that explains the desired behavior, and you treat the code like it's assembly, and you never read it anymore. I do not endorse that.

**Speaker 0** [06:05:30]
Let's put it that way.

**Speaker 2** [06:05:34]
We got one more. Alright. Last one.

**Speaker 5** [06:05:38]
I know you mentioned one of the slides about the, like, context window and the the dumb zone. Right? I know you researched that, like, heavily a few like, have you have you, like, gone back to look at that again to see how true that still is after certain, window, especially with, like, all the auto compaction they have now and other methods for that?

**Speaker 0** [06:05:59]
I mean, I think, like, for if you've been using AI coding agents for six to nine months and you use them for sixty hours a week, like, the dumb zone is not a useful concept to you. I will regularly go up to 60. I will regularly, like, aggressively keep it below 30. It depends on the complexity of your task, the amount of instructions versus information. So, like, your mileage may vary.

**Speaker 0** [06:06:24]
If you are using coding agents for the first time, this is what I this is what we teach people. It's like, if you don't know what to do and you haven't developed that intuition, then, like, shoot to keep it under 40. And if you get up to 60, like, think about wrapping it up and, like, you can keep iterating on the same dock. That's what's also nice about these is, like, we don't use the built in because everything that matters is going into static assets. And so you can always resume from where you left off without having to worry about the quality of an auto compact or manual compact.

**Speaker 2** [06:06:50]
Brilliant. Dex, well done, dude. Works. Thank you. Let's give it up for him.

**Speaker 2** [06:06:55]
Yes. And now the final act of the day. We've got Harrison and Sam coming up. It's rare that you get two folks of this caliber on the stage at the same time. We managed to do it.

**Speaker 2** [06:07:12]
So I'm going to present Sam Partee and Harrison Chase. Get on up to this stage, and let's give them a big round of applause. These guys need no introduction. Thank you, dude. Here's this for you.

**Speaker 1** [06:07:31]
Oh, I get the mic? Way too nice of an introduction. Do I need this? Do I get a mic? I think we both have mics.

**Speaker 1** [06:07:38]
Oh. I don't think I need this.

**Speaker 6** [06:07:41]
I don't need it. Alright. We're figuring this out live. Hello. My name's Harrison Chase.

**Speaker 6** [06:07:49]
I'm the cofounder and CEO of LangChain, and I have the clicker here which I'm giving to my friend, Sam.

**Speaker 1** [06:07:55]
Thank you for announcing that. Hi. I'm Sam Partee. I'm CTO and cofounder of arcade.dev. And today, we're gonna talk about general purpose agents.

**Speaker 1** [06:08:03]
And something that Harris and I have talked about for a long time, which is why coding agents are actually the foundation for general purpose agents. This might not immediately make sense, but hopefully over the course of the talk, it does make more sense. So what is a coding agent? What does it help you do? Things that we use every single day.

**Speaker 1** [06:08:23]
Right? Clot code, yada yada. What does it have access to a file system? It reads and writes files. It is able to over time, over its iterations, keep in store, only things like memory, but just task execution data in a workspace local to itself.

**Speaker 1** [06:08:44]
And so in doing so, it's able to keep and store things that as it's working on, it can go back and reference and keep not in its context window, but it's something that is a retrievable object. And so this is a paradigm that you can extend not only through just simple search like rag, but all the way through tool calling. And we'll show over the course of the talk how it extends through a bunch of different paradigms as well. Now, the point of the talk is actually also to get you to a general purpose agent, not just something that works on your laptop for one user, but something that works for an entire organization for all of your users. And so how do you do that?

**Speaker 1** [06:09:24]
Well, you start with a coding agent. And that's the primary object of what Harrison's gonna talk about today. So what are we gonna talk about? We're gonna talk about two things. First, Harrison's gonna talk about the agent harness and why it's important and why this gives you the coding agent paradigm.

**Speaker 1** [06:09:38]
Why this gives you a basis for what you need for that ClaudeCode like experience. And then I will talk about the tool runtime and what's necessary there to make these two things combine into what is necessary in our view for a general purpose agent for your company, not only for yourself or for your company, for your friends, for your users, what have you. These two things that we can say when we put together make a general purpose agent, have different responsibilities. And they might seem like they're really similar. It might seem like clogged code calls tools and reason write files through tools, or that it extends its memory through some interface through the tool runtime.

**Speaker 1** [06:10:20]
When actually, these two things actually have very different responsibilities and have an incredible responsibility in the foundation of a general agent. So first, Harrison's gonna talk about that agent harness piece. And that is the foundation that gives you that ClawCode like experience. And then I will talk about the next piece that brings it out, the general purpose station as well.

**Speaker 6** [06:10:44]
Cool. So agent harness is a fun term to describe the scaffolding around the model that lets you interact with the environment and do things. And so I wanna talk a little bit about how we think about agent harnesses at Linkchain, how we've thought about building our own agent harness called deep agents, and then some of the things that we've added into it which are very similar to things that are in other agent harnesses like Cloud Code or Codecs or things like that. So what is an agent? Most people would probably technically define an agent as an LLM running in a loop calling tools.

**Speaker 6** [06:11:18]
So so what is the difference between that and an agent harness? Basically, an agent harness adds more things in. So you can think of it as having more batteries included. And so what are some of the things that it adds in? One of them very commonly is a planning tool or instructions for doing planning.

**Speaker 6** [06:11:36]
Another very common component is file system tools. So these are for interacting with the file systems. These can be to read and write search files, glob, grep files. Depending on the hardness that you're using, it may have a few of these. It may have a lot of these.

**Speaker 6** [06:11:53]
That kind of depends on on what else it has in terms of kind of like code execution tools because sometimes you can just execute code to do the same thing. And and and the file system is oftentimes where the agent definition is actually stored. So you can represent an agent as basically an agent dot m d and skills and an m c p dot json. And if you think about all these things that you use in coding agents to define the code to to kind of, like, guide the coding agents to do things, I would argue that's basically how you can define a custom agent. You can kind of think as your of your coding agents as custom agents in some way.

**Speaker 6** [06:12:29]
Sub agents are another aspect of this that can also kind of like be defined by by files on disk or or or through some other method. We build a bunch of open source things at LangChain and that's kind of evolved over the years as the whole space has evolved. We started off with LangChain in the middle actually. It's kind of like an agent framework. And then we actually built LangGraph as a lower level kind of like agent runtime.

**Speaker 6** [06:12:52]
So we think of a framework mostly concerned with abstractions and integrations. We we think of LangGraph runtime as more infrastructure almost. It has durable execution. It has streaming. It has human loop.

**Speaker 6** [06:13:04]
It has persistence. And then recently, we started on deep agents, which we think as as as this agent harness, and it really has more of of these batteries included things. So what's actually in a harness? I wanna talk about this in a little bit more detail. So we talked about file systems.

**Speaker 6** [06:13:23]
So these are the six that we have in deep agents. We have list, read, write, edit, glob, and grep. Other agent harnesses so this is pretty heavily based off of Claude code, so it actually has all those. Codecs has a smaller subset. So it I think just has I think it just has read and write and then it relies on using the bash tool for for other options.

**Speaker 6** [06:13:44]
So you can pick and choose which ones you want here. One of the really cool things that we added in DeepAgents that is pretty unique is that we have this concept of what we call kind of like a pluggable back end. So when you run Cloud Code, it runs locally against your file system, like your real file system that you have. What we have in, deep agents is is that file system, it it can be your real file system or it can be a virtual file system. So we can use a database to store, quote, unquote, files.

**Speaker 6** [06:14:14]
So you store it in database, but you represent it as a file system to the agent because that's what it knows and that's what it interacts with. This also makes it easy to run DeepAgents remotely because you can just plug it into a sandbox or something where the files are stored elsewhere. We have we have a planning tool in DeepAgents. This is a really simple tool. All it does is it asks the LLM to generate a plan.

**Speaker 6** [06:14:38]
It doesn't even save the plan. It just puts that plan in the in the LLM's context window. It kind of it's like it's taking notes to itself as it goes along. This is pretty heavily based off of Clawd Clawd's planning tool as well. Other agents do things where they actually write the plan down to a markdown file.

**Speaker 6** [06:14:55]
That's obviously a much more persistent way of of keeping it. And but but a lot of the planning tool is really just to have the agent think about the plan and and put it in the context window so that it informs future generations. We have sub agents in in deep agents. They work pretty similar to sub agents in other agent harnesses. The the really useful thing that sub agents do is they have this context isolation where you give a sub agent a task and it just sees that task.

**Speaker 6** [06:15:25]
It doesn't see anything previously. And all the work it does, the main agent doesn't see any of that. It just sees the final result. And so that's really good for spinning up a bunch of these in parallel and having them just work on things in a very focused way, and then they come back and report the main result. Fun kind of like side note, there there can absolutely be communication issues here.

**Speaker 6** [06:15:44]
So you need the main agent to be specific about what the sub agent should do, and the sub agent needs to respond with the right info. If there's breakdowns in either of those, then this doesn't work as intended. Skills. So we support skills. Most coding agents support skills.

**Speaker 6** [06:15:58]
They're pretty cool and a nice way to package up instructions and tools in a way where you can kind of like discover them as you go along. Some of the things that we do around kind of like context engineering that are built into a harness, and again, this is what I mean by harnesses comes with more batteries included. This is this is kind of beyond the l on just running in a loop calling tools. One of the things we do is that I think other harnesses do as well is offload large tool results to files. So rather than see, a massive JSON file that's returned from a tool, we'll actually just put that in a file, show you the first 100 lines, say, here you go.

**Speaker 6** [06:16:33]
If you wanna see more, you can read the file, and then and then it can explore it that way. So this prevents you from kind of like blowing up your context window quickly and and lets the LLM a lot of this is in spirit of giving the LLM more control over managing its own context window. For compaction, what we do is when you get to a certain point relative to the context window size, we do a compaction step. We save all the original messages into the file system so that if it wants to go look at those later, it absolutely can. We're also thinking about giving it a tool that will let it trigger its own compaction.

**Speaker 6** [06:17:05]
So again, in the spirit of giving the LLM more control over its own context window. Human loop is really important. We built deep agents on top of lane graph, and so it naturally supports pretty robust human loop controls. And so we have a nice little config where you can specify whether you want tools to interrupt before they are executed or not. And with that, I'm gonna hand it over to Sam to talk more about some tool stuff.

**Speaker 1** [06:17:31]
Well done. So human to loop is actually a really good jumping off point, because it's one of the points at which the harness needs to communicate with something that's other than the file system of that agent. And so what you just heard from Harrison a lot was how that agent can utilize those local aspects of the computer, from everything from just writing and reading a file to, like, something like computer use. Right? And so these are necessary aspects that the harness provides.

**Speaker 1** [06:17:58]
And so where does the tool runtime come in after that? What is necessary besides that local aspect of a standard IO type MCP server working with a harness? Right? And really, the essence is in the multi user and authentication authorization and third party services, and that the things your users or you want to be able to use. And so how do I access my data and secure, my services securely that aren't on my local computer or that my users wanna use with my agent, that aren't local to their computer.

**Speaker 1** [06:18:35]
So I'll give you an example of this. Let's say you're booking a flight. Okay? And you you wanna do so with an agent. I know this might seem not realistic, but this is actually something that an enterprise company of ours does now with agents.

**Speaker 1** [06:18:52]
So you have to check a calendar. How do you know which calendar Outlook or Google? How do you sign in as that user? If you're giving this agent to a company, how does that company use their SSO to sign into that agent? Finding flights, do you have an integration with that?

**Speaker 1** [06:19:11]
You might have an MCP server, but are you gonna surface all of the flights and the flights that are particularly relevant for that particular user? What happens when you log in to amazon.com? It's your Amazon. It's the one that has the relevant results for you. It has personalized results with your information curtailing those specific results.

**Speaker 1** [06:19:32]
Why don't agents do that yet? Book the flight, actually pay for it, payment mechanisms. Notifying your team on Slack once again, off integration, off integration, off integration, off integration. This is the necessary evil that the tool runtime is responsible for is the dirty work of making sure that every system inside of your company, every enterprise that uses this particular one off OWASP server for their one off service and this integration here, there, and beyond all integrate with your agent properly that's running inside of the harness. This runtime has that responsibility of both that authentication and authorization layer as well as that integration layer.

**Speaker 1** [06:20:22]
These two can't be separated because now the agent is an intermediary that you can't take out of the equation. It's no longer just a web app with social sign in you can use the user token for. And why is this? Well, there's two failure patterns we see. One is the service token.

**Speaker 1** [06:20:40]
So what happens with a service token? Well, it's either got incredibly elevated privileges to the point where no CISO is gonna let your product be bought at enterprise, or it's got so low privileges your agents not useful. And it's only good for one maybe local user on their laptop. And that could be helpful, right, for that single user. But when you wanna deploy an agent firm wide, how are you having that firm's SSO or login making sure that that particular user is using that particular agent?

**Speaker 1** [06:21:13]
And then even more than that, them to access their Google. It's not just the front door off. See that is. It's the auth z authorizing them to access their own Google. And so there's two forms here that that integration can't be separated from now that the agent is an intermediary.

**Speaker 1** [06:21:36]
This ends up looking what like what we call delegated agent authorization. Essentially, you're not giving it a user token. You're giving it a portion of your user token for as many services as there are. The way we've approached this is that Arcade will hold one token for the subset of permissions you've authorized for that particular agent at that particular time for that user for that service. So we've covered both of those doors such that the least level of privilege is given to that agent for that particular user in that particular company.

**Speaker 1** [06:22:14]
And in doing so, it's the same model that you would have had for a website with Okta in the front door and had no auth z. But now an agent has the exact same profile that a CISO has approved for the last fifteen years. And so what does this actually look like in code? Which is what I always wish people did in talks when they talked at this kind of level. What does this look like in code?

**Speaker 1** [06:22:38]
Well, this is an example of a tool to go to Reddit. And now it actually isn't the whole tool. K? It's just basically the function signature. But it is the part of the tool that specifies the exact level of privilege needed by this action action that the agent's gonna take.

**Speaker 1** [06:22:59]
And in doing so, the agent now can say, does this user have that privilege for that service in this database? And in doing so, you can now say with certainty that no agent will take any action that an authorized user did not authorize them to take and that you do not have a log of them saying yes to. And human in the loop of the agent harness is a big part of this because how do you surface when the run time says no to the user? We do this in a Slack agent that a lot of enterprises use. What if it's just yeah.

**Speaker 1** [06:23:38]
So I forgot that I had animations in the slide. It's not it's not the user's token for that service. It's a delegated subset. You don't wanna give an agent r m dash r f to your Google Drive. That's a bad idea.

**Speaker 1** [06:23:55]
Giving them delete is almost never a good idea. And so why delegate them that privilege with your user token you've been sticking in your environment variables on your laptop for a standard IO server, which stopped doing that, by the way. But please. Someone posted one on LinkedIn the other day. It's like, man, I can log in as you right now.

**Speaker 1** [06:24:17]
But the user it's not the user token, it's a subset. And even if it's just a secret, once again, please don't put this in your environment variables. Instead, put them in a secret store. In the case of Arcade, we've made it so that each function can be labeled with the secret name, and that could be for an org project or a user. And so you have multiple levels of control over where that secret gets applied.

**Speaker 1** [06:24:47]
Moving on, it's injected. It's not in context. But I'm gonna well, I should probably should have paused it, shouldn't I? Contextual access is another part of this. So what if you already have an RBAC system?

**Speaker 1** [06:25:00]
What if you already have some way you do PII? If you already have some way you do named entity recognition and you don't wanna replace it? Well, what we can do is now take your tools and say pre and post execute, what do you want to have happen? And in doing so, hook into your entitlement system or your Kerberos system that's been there for forty years. It's this legwork that the tool runtime is responsible for and takes care of when you actually wanna take your agent and go sell it to an enterprise.

**Speaker 1** [06:25:35]
And so in doing so, it gives the agent harness an ability to say, I'm positive that this is that user at this time for this action with this level of privilege to go out into the world and take some action on behalf of that user, not just for that user, but as that user. It's probably the most important part. Doing work for the user is good. Doing work as the user is much better in many cases. Because in doing so, you're doing their work for them, not a bot, not a service token that's over or underprivileged.

**Speaker 1** [06:26:14]
You're doing their work as them, which is usually much nicer sending the email as you instead of making you copy paste, for example. What this ends up looking like is something along the lines of this diagram. I tried to make this as uncomplicated as I could, but obviously it's a pretty big system. So I will say there's a Helm chart you can read, which for me is much easier. However, you could see some of the things that are part of the runtime here.

**Speaker 1** [06:26:42]
I've mentioned the connection to enterprise systems, but I feel like most people could imagine an MCP server writing a tool that's privileged for their system. What's a little bit harder is actually those layers of the registry access. How do I manage all of these things? How do I do this at an enterprise? And that's what you see in the core on the right hand side there.

**Speaker 1** [06:27:04]
All of this, of course, connects directly to those harnesses that you see. Put it in the line chain, put it in the line graph, you're writing it from scratch, or take deep agents and just hook up the MCP server directly. Put it in a skill named the MCP servers, and it works immediately. This is what that looks like. You can basically just go inside of Arcade and use our gateway, which essentially takes multiple MCP servers and says, want a new MCP server.

**Speaker 1** [06:27:35]
Give me that tool, that tool, GitHub, Google, Microsoft, this, make an MCP server, now serve it on the Internet securely. That's what a gateway does, and it looks something like that. And then you can take that URL and that slug and plug it right in the line chain and use it immediately or a clog code or what have you. Deep Agents is pretty great. So bringing this all together, and we'll talk about something we've recently done together to kind of bring this even more together.

**Speaker 1** [06:28:07]
But these two pieces are distinct in the fact that they're responsible for major pieces of making an agent general and the purpose of that agent general. Hopefully that has come through.

**Speaker 6** [06:28:21]
And so talking a little bit about what this looks like in general purpose world. One of the things that we have a really good integration for is what we call agent builder and arcade. So we talked about how this underlying harness, which is very similar to coding agent harnesses is is can in fact power general purpose agents. I don't I don't really think the interface for general purpose agent is in the terminal. I think that's I I don't think my mom would use that.

**Speaker 6** [06:28:51]
I think there's a different interface that other people would, and I think you see some ideas with this with with with Manus and Claude Cowork kind of like pushing in this direction of what does a more user friendly interface for these things look like. And and so that's what agent builder is. It's powered by deep agents. You can connect to how how many tools does Arcade have? A thousand?

**Speaker 1** [06:29:11]
Over 8,000.

**Speaker 6** [06:29:12]
Over 8,000? Okay. You can connect to over 8,000 tools through there as well. And and and and what it is is basically a way to create agents in in a no code way by just chatting with them. One of the things that's built into the agent builder is this memory aspect.

**Speaker 6** [06:29:31]
The memory is just done by modifying the files on the file system. We talked about how you can represent agents as files on a file system with agent dot m d and skills and sub agents and m c p dot json. And so when you talk to this agent, all it does is it just modifies those files, and it creates and evolves its definition of an agent along the way. So we have a number of very general purpose templates here. So the where is it?

**Speaker 6** [06:29:56]
The email assistant is one that I use I use daily. I no longer check my email. I check my email

**Speaker 1** [06:30:02]
He actually does use it.

**Speaker 6** [06:30:03]
I actually yeah. I I've been I I was using it I've been using it for, like, a year and a half.

**Speaker 0** [06:30:07]
Started off been a

**Speaker 1** [06:30:08]
lot since we did agent inbox.

**Speaker 6** [06:30:09]
It's it's evolved a lot. It started off on LangChain and then went to LangGraph and then went to DeepAgent, and now it's an agent builder. And and and and LinkedIn recruiter is a good one as well that that we use to kind of, like, source candidates. We're hiring, by the way. Nice plug for that.

**Speaker 1** [06:30:26]
Social media one's fun too. What? The social media one's fun too. You can there's one that someone put out recently to impersonate anyone you want on social media, which may or may not be a great idea, but it is very fun to do. This is the integration that you see right here.

**Speaker 1** [06:30:41]
Essentially, it's a very similar page to what you've seen before. This will be coming out soon, but, essentially, it'll enable this already really easy to use interface to just access all of the tools in Arcade, hence, giving all of the deep agents that are inside of there with those easy to use templates a ton of different tools to be able to use. So, hopefully, most people can see how that'll be really fun and an easier to use interface like your mom would use.

**Speaker 6** [06:31:04]
Yeah. Yeah. We've done integrations for a while, but this is definitely the tightest one. And so For sure. Excited to get that.

**Speaker 6** [06:31:09]
And maybe just wrapping things up with three real simple takeaways. Tools really matter. And if you wanna use tools in a production ready way, use arcade. Like, the design around the tools, you guys wrote a really I don't know whether it's a blog post or website, but you had, like, 80 different, like, tips and tricks

**Speaker 0** [06:31:26]
for tool design.

**Speaker 6** [06:31:26]
Patterns. You can check

**Speaker 1** [06:31:27]
that online. Basically, just things we've learned about building tools since the past two and a half years.

**Speaker 6** [06:31:33]
Two, the harness matters. So this is this is what's powering the agent under the hood. You can use lane chain deep agents, or the best part is it's fully open source. So you can fork it and then modify it as as you wish. We have lots of middleware to hook in and control that.

**Speaker 6** [06:31:48]
And if you wanna use them together and you don't wanna code at all, but you wanna get the power of these agents, use agent builder. And

**Speaker 1** [06:31:56]
That's pretty much it.

**Speaker 2** [06:31:57]
That's pretty much all.

**Speaker 1** [06:31:58]
Yeah. Thank you, guys. Alright.

**Speaker 2** [06:32:02]
Nice. Who's got a question? We

**Speaker 1** [06:32:06]
have fifteen seconds left. Come on. That was pretty good. Right? We tied that up.

**Speaker 1** [06:32:09]
Perfect.

**Speaker 2** [06:32:10]
And funny story, the reason I got Harrison to give this talk is I prompt injected his little Google agent.

**Speaker 1** [06:32:19]
I can't believe you said that.

**Speaker 3** [06:32:20]
This is great, guys, and the combination makes a lot of sense. I'm I'm curious, like, how you think about, you know, the issue of a legitimately authorized tool used maliciously or with emergent misalignment. You know, like, Harrison, if you're you know, someone's sending you a prompt inject in your email

**Speaker 1** [06:32:39]
Yep.

**Speaker 3** [06:32:40]
That then does a thing that does a thing, or the agent gets confused.

**Speaker 6** [06:32:44]
Yep.

**Speaker 3** [06:32:44]
And I'm just curious how you're approaching that.

**Speaker 6** [06:32:48]
I can talk about some of what we do. You can talk about some of what you do. I think we both have different approaches. So one of the things that's in agent builder is basically guardrails about what tools can and cannot get executed automatically. And by default, tools with right operations can't.

**Speaker 6** [06:33:06]
And so yeah. Like, sending emails, I'm still in the loop. I go in and improve. Editing its own memories, you can toggle and you can toggle this on and off. So if you wanna be riskier, but by default, anything with a write operation is generally human in the loop.

**Speaker 6** [06:33:20]
It's a great example

**Speaker 1** [06:33:21]
of how now, once again, if they're both nest like, the the file system there that's controlling the read and write. Right? That's not in the tool definition themselves. That's in the agent harness layer. And then at our layer, we have things like custom verifiers.

**Speaker 1** [06:33:36]
So when someone clicks a link to authorize, we're gonna either make you go to your IDP, Us or Lang Smith in the case of agent builder. We're gonna make you go to something to say you are you first no matter what, and then we'll make you authorize to Google to send your email. And that was learned the hard way. So it's a very good question.

**Speaker 4** [06:33:57]
Yeah. Thanks. Awesome talk. You mentioned kind of model or agent that your mom would wanna use very similar to what Peter Steinberg says, with OpenClaw. And so curious your thoughts on how you see this space evolving.

**Speaker 4** [06:34:12]
If you two are kind of converging and Menace and all of those, it seems like this is gonna be the space for the next ninety days at least.

**Speaker 1** [06:34:21]
Yeah. Well It's actually a really long time. Thank you.

**Speaker 6** [06:34:27]
I mean, it's funny that you say that because, like so we released agent builder, the first version in kind of, like, in whatever alpha beta thing, probably around the time, like in some initial early version of Open Claw came out, but like before it exploded. And since then, that's that's like informed our North Star of where we might wanna go a lot. Like, I think they did a lot of things really, really well. I think like

**Speaker 1** [06:34:50]
A lot of things.

**Speaker 6** [06:34:51]
Yeah. Like, Chad being the primary interface is is is I think a really good one there. I think this idea of, like, how you expose the agent to the external world is also really interesting. I was chatting with Sam about, like, I if create an agent and expose it to Sam, does it use does it use Sam's credentials as, a pass through, or does the agent have its own kind of, like, identity? And I think, like, with OpenClaw, I think we saw actually these agents take on their own identity, which I think was really interesting and not at all what we'd seen kind of like previously.

**Speaker 6** [06:35:21]
Previously, we'd seen everyone always wanted to pass their credentials through. And now with OpenCloud, there's this idea of like an agent identity, and it has its memory and it has its credentials. And that's really interesting, and I don't know what it means, and it'll probably figure out in ninety days or or probably more or something like that. But yeah. I mean, I think pretty clearly the agent of the future have they have they have they have they can write and execute code.

**Speaker 6** [06:35:45]
They have some aspect of memory. They're connected to a bunch of tools. They're exposed through different services. I think there'll be two types, some that have their own identity, some that take on their user's identity. Where I I guess, like, maybe one thing that I haven't said that is more future looking.

**Speaker 6** [06:36:02]
One of the things that we do in agent builder that is distinctive is we have this concept of agents that are triggered by events. So, running in the background ambiently, and we have this concept of an inbox where you go in and you see all the agents that are stuck and need human approval for tool calls and stuff.

**Speaker 1** [06:36:15]
Well, it channels in OpenCLO. Kinda.

**Speaker 6** [06:36:18]
Okay. I haven't I I actually have okay. Should go check that out then. Yeah. See, I'm already updating my belief today.

**Speaker 6** [06:36:23]
So but but I think this idea of agents running in the background and then pinging you when they they need help, like, kind of like, yeah, they they push things to you rather than you go in and and and kind of like pull, I think I think that's maybe where more and more things will go will go. I think what a lot

**Speaker 1** [06:36:36]
of people saw with Ocala two is that it was really, really cool, but the reason you need to buy a Mac Mini is that there's things that need to be figured out. Yeah. And we're still figuring that out. The agent identity piece is really important. I think we're still in in many ways learning how to deploy agents that do stuff as you.

**Speaker 1** [06:36:56]
Right? I think the agent identity is another piece that needs to get figured out that in addition to something like delegated auth, we need to be able to do so that, like Harrison said, there can be a remote memory service that says, oh, it's that agent for that user that had use using this service, and they can pull that specific memory only for that user or only for the org. But right now, that is still an early topic.

**Speaker 2** [06:37:23]
Alright. Before we get to the next question, I just have a friendly announcement. I can't see anyone. Me in the back over here. So we've got a booth crawl happening right after this q and a.

**Speaker 2** [06:37:34]
Make sure to grab a ticket for drinks when you're leaving. There's gonna be a few people handing them out. Alright. Next question.

**Speaker 7** [06:37:42]
Alright. Thanks, guys, for the presentation. My question is about often and with MCPs and all. We I work in ITS ops. One of the things we've seen is that when our agent tries there's a case where there's, like, a a manager that's taking care of someone that went on vacation, and they need to run an Ansible like, agent wants to run an Ansible playbook, but they don't have the permission, so they have to go through, like, procurement and whatnot.

**Speaker 7** [06:38:07]
Have you guys seen a way where you could the agent could say, like, hey. This person will definitely get permission, and we really just wanna run this one thing to solve and mitigate the issue.

**Speaker 1** [06:38:16]
You should use Arcade. Yes. We've seen that a lot. That is that is a core issue. So, essentially, what is being described as, believe it is, look.

**Speaker 1** [06:38:26]
This person is running this workflow with this token, and now this person's on vacation. Now this manager is responsible for it or something like that. And now I have no visibility or chain of command over this workflow. And so now how do I see which user did what, and how do I do that now if they're not there? Is that roughly correct?

**Speaker 7** [06:38:45]
Yeah. It's also like they don't have the permissions.

**Speaker 1** [06:38:48]
Yeah. Exactly. So even worse. Right? They haven't been delegated those specific permissions.

**Speaker 1** [06:38:53]
Only that one person that, you know, they've gotten fired or they're on vacation or what have you. We've actually seen that in both cases. And how do you change or revoke even worse? Like, if they got fired, how do you revoke them? That is functionality that we've built, again, the the hard way of figuring it out.

**Speaker 1** [06:39:11]
So you basically need all of those things for your agent. You need to be able to say that token for that user is no longer viable because they got fired. Or this person's on vacation, I need to be able to have a step up authorization flow that authorizes a new user to do this exact thing. And delegating that token and enforcing that at runtime is a nontrivial challenge. I will tell you that.

**Speaker 1** [06:39:34]
It has been a lot of fun to learn a ton about off. I'll tell you that. You I'm not being sarcastic at all. But, yes, that is a very common problem at enterprises for sure, especially in IT departments.

**Speaker 8** [06:39:46]
Hi. Thank you. For I'm back here too. For enterprises that are worried about sending their private data to the public AI companies, Can you run your own LLMs on prem with all of this stuff?

**Speaker 1** [06:40:03]
Yes. So that is a big part of why we can work well together is that there are companies that deploy everything we're talking about today entirely inside their VPC. I don't think you take care of models though. I mean

**Speaker 6** [06:40:17]
No. We don't do models. The only thing I'd say is like for a lot of these agent harnesses, the models do have to be good enough to actually take advantage of all the tools that they're given. We're doing some stuff to benchmark different open models on on deep agents and see where they see where they stack up. But, like, you know, to to be honest, if you're using OpenAI or Anthropic right now, those are gonna have the biggest kind of like performance.

**Speaker 6** [06:40:40]
I am really, really excited for an open source model that can reliably drive these harness. GLM, Tammy? We hooked it up the other day and it wasn't amazing, but we're doing more rigorous testing.

**Speaker 1** [06:40:52]
I've used GLM before personally. I I will say there's a severe if you're going from 4.6, hope it's to anything pretty much right now. It's you're gonna have a tough time, in my opinion.

**Speaker 4** [06:41:04]
Yeah. Hey, Sam. Just follow-up. You touched on the Mac Mini, which I saw something walking in here that was really interesting. They said that people are actually buying Mac Minis just for access to iMessage.

**Speaker 0** [06:41:17]
Blue blue bubble.

**Speaker 6** [06:41:18]
Yeah. Right?

**Speaker 1** [06:41:19]
I I

**Speaker 4** [06:41:19]
And going through the CLI interface to do that. So I think everything you touched on is cool, but I think that's another avenue that's gonna explode too.

**Speaker 1** [06:41:27]
So skills. Right? So Blue Bubble and a lot of those work through skills. Right? And they use the CLI.

**Speaker 1** [06:41:32]
And I personally, when I I can I contributed to PR, I got closed by a automatically somehow? Peter's on it. But the thing that you're talking about with the CLI skills, a lot of people do also feel uncomfortable with CLI access, like shell command access, and that is also why they're buying that, which is a great point. I also bought Mac Mini for the blue bubble part because of exactly that thing. So that is very true.

**Speaker 1** [06:42:00]
I will say it's a lot of fun. Channels are a really interesting concept. With where we're going in agent builder, I think that's gonna be a really interesting topic to be discussed. But I think, especially OpenClaw kinda nailed it. It really scorched the earth, to be honest with you.

**Speaker 1** [06:42:16]
If you look at the code base, I mean, it is full. Let's put it that way. But that concept of channels in particular that allows you to do that, like Bluebubble or whatever iMessage thing that you're using to be able to do that on the CLI. It's an important part of where we're going, and it's not just MCPs. It's also skills on the CLI.

**Speaker 1** [06:42:35]
It's a good point.

**Speaker 2** [06:42:37]
Thanks for doing this, guys. I appreciate you so much. Give it up for him. Thank you. Yes.

**Speaker 2** [06:42:43]
Awesome. Alright. We've got the booth hangout. There's food. There's drinks.

**Speaker 2** [06:42:51]
I wanna say thank you all for coming. This was an awesome day. I learned a ton. Hopefully, you learned a ton. And I'll let you go.

**Speaker 2** [06:42:59]
Maybe I could tell one joke. I told it earlier, but there was only, like, five people here. So Dex is in. Okay. So I was talking with Claude Code, and I said, hey.

**Speaker 2** [06:43:10]
Choose a random number between one and fifty. And it said, alright. 32. And I went, that's it. For the next thirty two days, we're not gonna talk.

**Speaker 2** [06:43:21]
I cut off all communication. You and I were finished. And then it said, can I choose another number? And I thought, wow. That's so sweet.

**Speaker 2** [06:43:31]
Of course, you can. Go ahead. Choose. And it said, 50. So have a great day.

**Speaker 2** [06:43:37]
You all are awesome. Enjoy the side quests that are to come.
