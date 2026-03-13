---
title: Coding Agents Lunch & Learn, Session 5 - #1
source: Gradual
---

# Coding Agents Lunch & Learn, Session 5 - #1

## Transcript

[00:08:00,461] Rob Ennals: Hello. Can you hear me?

[00:08:09,084] Leo Walker: Yep, I got you, Rob. Can you hear me over here?

[00:08:11,886] Rob Ennals: I can hear you loud and clear.

[00:08:14,138] Leo Walker: It's beautiful. Beautiful, beautiful. Looks like we had, you know, at least a handful of dozen people signed up. So should be a good talk today.

[00:08:25,722] Rob Ennals: Have a fun conversation.

[00:08:26,621] Leo Walker: Yeah, absolutely. Absolutely. I was, I was playing around with Broomy last night. Just like digging into it more and pretty awesome stuff there. Pretty awesome

[00:08:34,397] Rob Ennals: Achoo.

[00:08:35,445] Leo Walker: stuff. I uh, I didn't know too much about uh. Bike work trees overall, like I've been like learning about that more and more over the past week. So it's awesome how you leverage some of that stuff. And yeah, super excited to learn more on a lot of your decisions for me.

[00:08:56,315] Rob Ennals: Work trees are definitely well worth using if you're using parallel agents, because if you're like doing a whole separate clone for each thing. That can get huge really quickly or tight itself and not really quickly, and work trees are just like designed for this.

[00:09:11,372] Leo Walker: Oh yeah. Oh yeah. Yeah, I think. Yeah, I, I think that a lot of people are familiar with Git and Git commits and, you know, branching that way. But now that agents are out, work trees are fantastic, so. Welcome everyone. We'll give a little bit more time to. Get everyone in before we go through the introduction here to Rob and and Brumi. Overall. This is a. Definitely want to be an interactive session. So while I'm leading the conversation here with Rob and talking, if you guys have any questions or want to kind of. Put your two cents in to help us guide the conversation. Feel free to raise your hand. Raise your hand. And just come on. I will call you on to the mic to to talk more and whatnot. So should be a really good time.

[00:10:01,848] Rob Ennals: Yeah, yeah. And if the one last week is only while we have an agenda of what we say we're going to talk about, we might go totally sideways and talk about something different if that's what people want to talk about.

[00:10:12,497] Leo Walker: Oh, absolutely, absolutely. There there's as I was digging in more and more into it, there's so many things that I'd love to learn more about. I didn't even know about Electron until Broomy. So yeah.

[00:10:25,295] Rob Ennals: Well, I bet you've been using apps that run an electron because VS Code is electron. I think Slack is electron.

[00:10:31,688] Leo Walker: Oh, OK.

[00:10:33,844] Rob Ennals: I got a large fraction of popular apps right now running. I don't actually tell you, but electron is like everywhere.

[00:10:39,076] Leo Walker: It nice, nice. OK, so it's like a framework that a lot of people are actually using, but if you're not in the application world that you might not be seeing the filler. Familiar with it like. Salesforce or Stripe is like, hey, everyone relies on it, but it's not super obvious.

[00:10:56,975] Rob Ennals: The most excellent shout out of the UI how we use Electron.

[00:11:00,815] Leo Walker: Uh, yeah. Exactly.

[00:11:04,795] Rob Ennals: Yeah, those are not familiar with the electrons in an app. That's a framework that lets you very easily write apps or run on any platform. By basically having your code be written in React and then stick a Chromium web browser within a a bridge so that some stuff runs native code to talk to the core system APIs. But most of it is literally just React website setup. And it just makes a lot of development easier to run, easier to see multi platform. One of the things I love about Electron is the hot refresh. So if you're building stuff in the EO traditional C compiler way, the cycle from you've changed things with updates live can be really slow and annoying. With electronics like instantly change, it's updated just like with the React app.

[00:11:51,277] Leo Walker: That that is huge for iteration speed and just being able to test immediately. And that's that's actually great for.

[00:11:59,907] Rob Ennals: Yeah.

[00:12:00,215] Leo Walker: For having us start this conversation here so. This is session five of the Coding Agents Lunch and Learn. In the past sessions we've talked about UMM. Uh, Cloud Codes best practices. We've talked about running evaluations. We've had, uh, people talk about what kind of tools they're using from Cursor to Cloud Code to VS Code with Copilot and everything in between. And as we've, you know, gone through more and more. In order to kind of like level yourself up, everyone is saying work more in parallel. And. Me trying to like look at a bunch of different streams and seeing what the workflows are, what are the file changes? Like if I kick four different agents off to do the same thing, how do I choose which one to accept? And it's gotten really overwhelming to me in certain workflows and certain edge cases. So there's people that are tackling this. In production and Rob. Had to use parallel agents to build Brumi, and Brumi does stand on top of other things like cloud code and things like that so. I'm actually gonna hand this over to Rob to kind of introduce Broomy and. We'll have at least the 1st 10 minutes to go over some of his design. Design decisions there and just, you know, teaching us about Brumi to set the stage up for digging. Deeper into the basics and the production level. Parallel agents.

[00:13:32,032] Rob Ennals: Cool, so the core idea behind Forumi is to build an IDE which is designed from the ground up. On the assumption you're working with lots of agent sessions in parallel. So things like Visual Studio Code are. Really awesome at doing what they're designed to do. They're designed to do is a developer. Doing one thing at a time. Mostly by themselves. And. Then when we layered agents on top of that, we kind of kept a lot of that paradigm, which again made sense for those tools for design. And it also made sense of where the level the agents were at to begin with, like when we first got. Coding. When you first got AI coding, it was like it wasn't that good and so you really had to only give it enough free range to tiny things. He's also complete because if you did more than like a few lines of code, it was going to screw it up. You have to manually check a few lines of code. It made no sense to be parallel agent. In the early days. Coding, I always just could do a few lines and the next step you have things like like what cursor would do, where you could OK say OK. Give me write me a functional. Do me this one thing and you'd review different chunks of stuff and that was more like peer programming. And again, it wouldn't make sense to be parallel there. But now we've got to the point, particularly if Oprah's 4.6, where it can actually do a fairly large amount of work in one go and will actually run pretty reliably for a few minutes without needing to you to intervene. And if it's going to run for a few minutes? Without you having to intervene. What are you doing those few minutes? So I've seen a lot of people, they just sit there and stare at the agent to watch it work, and they scroll up and down and say, OK, what's it doing? What's it doing? But you don't really need to do that. You can split off another agent. Another agent. I've often got like 10 running at a time. And we can talk more about how to make that. Process work nicely, but if you've got 10 running at a time. How the hell do you manage that? And the first one I do is I would have like. Another different screens, each running their own cursor or VS Code. And it just got overwhelming. Can be swiping, swiping, swiping, swiping, swiping. So I said, OK, who's stuck? Who's gone sideways? Who's doing something really, really stupid to stop it doing? But like the whole like swiping through all these screens just was not. It wasn't easy. And it was also like. Frying my brain because I was having to do these like paying attention to lots of micro things like. The human brain doesn't deal well with a huge fire hose of information that most of which is not relevant. You will know just what's really relevant. And so I bought Bromi basically to solve my own pain points and the pain points of other people I talked about. Just if you start from the ground up or assume you're doing multiple agent sessions in parallel. The other things are that well. And. One principle I had to start with developers where they are, don't give them something totally alien and bizarre. Because people won't get that. Store something which is basically where they are, and let them gradually, incrementally step up to something a bit weirder. So Rumi at its core. Is you've got an idea on the right for whatever session you're in with a lot of familiar stuff like it literally is the same editor of VS Code. And on the left you've got a a side boat. You can see all the different sessions you've got running. And each one has an indicator saying is it? Working is it. Got something to show you, Is it idle? Hasn't done anything since you last looked so you can quickly see how that one needs help. I jump in and see. And then on top of that I built a few other things to get make this flow quicker and easier. Like initially I found that I'd often have to type a lot of the same things to each agent. Things like OK, commit this work, do merge. All conflicts with everyone else is on the on on main. Write a good PR with all the stuff. Write all the tests. But although a lot of other other folks like OK, explain to me everything that's going on or you appear to be stuck, please tell me what's what's up here or what on the major design. None of these common things. So the next thing. It's kind of like customizable command buttons where you can specify them in this kind of like. Command Jason thing in your roomy setup just saying what? Standard commands. When you want to run, you can click a button. So a lot of time I'm using brewing, I'm just like jumping between these sessions, choosing the button to click and it then manages up and gives them whatever report I want to see. I just had a lot people should ask. Play some more stuff. You've often made to play some stuff now. Some thoughts.

[00:17:56,776] Leo Walker: Yeah. Yeah, yeah, yeah. No, I mean, I spot on as far as the friction that people have that like. If I go and let Claude cook for. A minute. I might do the same thing as Braun over there. I might scroll through some memes and I might grab my phone. And to scroll for like 30 seconds and that made a mental toll. On my attention and my brain because I'm just doing context switching to nonsense, right? And if I. You know, have it cooked for three to 5 minutes, then hey, maybe I could go update documentation or maybe I could like read another feature and there's a lot of context switching there. Which like again, hurts my brain a bit. So it's awesome that you could stay focused on being like, hey, this agents done. I see that another agent is already done and ready for, you know, my attention and you could go and stay in work mode and work with that, you know, call it a coworker. Right. And you just stay focused and attention to it and that you built some, I guess a harness or a little bit of a framework on top of Claude code because if anyone's going to use Brumi. You could use it with Cloud Code Gemini CLI, you could use it with codecs so it stands on top of that and. I find it very interesting because. A lot of those commands that you just said, like explain to me or summarize or stuff like that. Some of those Clis already have those slash commands in there, so. It's not like you're. Trying to replace what they're doing, you're just like. Complementing what they're doing of like, hey. I think that I need this for better parallel. Utilization. I'm going to make sure that whenever anthropics ship something, that's fire. I want to make sure that that is integrated with Broomy, but I also want to make sure that I empower people with Brumi. So it's really cool what you did there.

[00:19:47,517] Rob Ennals: No, yeah. So, so, so at we just said my intention is very much don't reinvent wheels that other people are building. Or realistically, anthropic is going to build a better harness for things like explaining this and stuff and we shouldn't. They are seeing we can do that better. What we can do is have a better user interface to. How you look at all these agents? I think another thing is that. We're in a horse race and so right now as of this month. Anthropic is the clear leader. But given a few weeks and Codex might be better. Give it a few weeks and Gemini might be better. Who knows what these other models might be doing. You don't want to have a workflow that locks you into. You have to use this agent. And so some of the companies that build these agents have reasonably good tools you can use to run the agents. But if you get your workflow baked into that. You're not really looked into that aid into an awkward way. Was I really wanted to have a flow where. You really can just jump from agents very easily. And you talked about how things like Claude often have these built-in skills that can do some of these things well. An important detail there is that when you define a command in brewme. You don't have to just define it once. You can define different variants for the different agents if you change agent. You could do what that same command button it doesn. Invokes a different scale or sub agent or whatever which is specific to that agent. The unmuted Leo.

[00:21:11,376] Leo Walker: Yeah, my bad. Yeah, absolutely. That kind of like. Buy into your current. Like framework like thankfully a lot of people. Are adopting Mcps so. You know, if you're using MCP server with cloud code, Gemini and Codex could use that. I'm I'm very bullish on. On all of the closed source models. I think that the open source will eventually catch up, so I'm glad that you have some. Like availabilities there, but I'm I'm also glad you could choose between all of the closed source ones there because yeah, this horse race, we're not sure which ones the best, but at least their integrations are all looking pretty similar. With MCP and skills and some kind of markdown rules. And uh. Yeah, it very well could be that Gemini 4 comes out sometime and crushes Claude 4, so. But uh. This is a good bridge into like the basics of like hey if you don't want to be locked in to only using cloud code. At we're only using Gemini. Then you have to make sure that you understand the basics of. You know, the orchestration, the skills and everything that you said there. So. I think you want to start digging into the basics there of like what is some of the things that you need to make sure that you have structured or kind of have the right to have guardrails in place or skills or things like that to. Together I start this orchestration.

[00:22:39,289] Rob Ennals: Yeah, sure. I think the. The more you want to run agents in parallel, the more you've got to set things up so that they can do good jobs. Cannot be market managed. And for one thing I noticed is that a lot of engineers, they. They micromanage their agents so that they'll sit and watch them and they'll like, review every tool use, or they'll review every little thing they've done with them, tiny bits of steps and stuff, and they'll poke them out. Mistakes in this particular bit of code and give them guidance and that particular bit of code. And. That's often the most effective thing to do short term if you're just working with that one agent for this one piece of work. But if you want things to scale long terms or lots of agent sessions at once, or other developers in your team also doing good stuff, you really want to do the work just to sculpt your system and workflows so that agents can naturally do the right things. And there's lots of things along those lines. So one really simple thing I found super effective if at any point when you're looking at Co produced by an agent, you notice some kind of bad smell or thing it's doing you don't like. It's really high value to work out a way of having a validation flow. Catch that. So one simple thing is. I even feel really good at writing custom years. So if you notice a common coding pattern which is bad. What ideally is already at ESL or biomin rule that captures that thing if there isn't? Right one. Or if it doesn't really fit into any excellent rule, have it put a custom script to spot that bad thing. Or have it create a. A skin or a subatom that looks for that bad pattern. It's OK every time you've done a new PR. It I'll probably your validation package. This sub agent looks at and so OK has it got this bad pattern I know he wants it to not have. Along those lines, it's really useful to have a dedicated validation of sub agents which does. All the different validations you think is really important. That runs all your unit tests, does all your limbs, all your custom rules, fires off sub sub agents and do these other checks. Because you don't have to do that. You and you don't want that running in the context of your main agent, because then it's gonna bake in the assumptions. Validation is really important to have in a separate context. Because if your agents made some dumb decision or false assumption. And it does validation in that context window. It's got that false assumption. Similarly I found if you don't have a sub agent doing a validation, you just specify in Claudia MD. Often the agent just forgets some of it, partly because it's done so much work in this one thing, it blows its context window and forgets its other part. So there's a little value in just really curating your validation.

[00:25:07,727] Leo Walker: Yeah. Yeah, I, I kind of want to double click on some of that a little bit. You started off with like, hey, don't micromanage your agents too much and try to like dedicate yourself to read over that. And I'm kind of wondering if you learned a lot of that? Add some of your previous companies that you worked at like. Especially a lot of the big tech companies is like hey. If you have. Junior engineers, or if you're a distinguished engineer and you have other people under you. You're not trying to micromanage them, right? And if you are micromanaging them, you're probably not doing a good job of providing a lot of guardrails. And things like that. And then as you continue to describe that, you're like, yeah. You almost want to empower them. You want to make sure that they have good patterns to reference, that they know what you're. Like standards are for when you go do a PR that if they follow a wrong pattern, you're going to. You're going to give them a little bit of tough love because you set the standards of what? Of what. You as a. Higher level engineering expects And then I also heard like, oh, if I have a team under me. I want to make sure one person is a QA member or like mainly like a reviewer validation QA person that you know reviews all the PRS for me like. Am I hearing that right? Did you learn? A lot of that stuff. Like managing people.

[00:26:29,986] Rob Ennals: Oh yeah, Toda, I think so much of. What it means to manage agents well right now is what it means to manage people well, because the the smarter they get, the more they behave like people, both on what they do well than what they do wrong. So just let you want somebody else reviewing a PR as a human. You want somebody else reviewing a PR as an agent. And just like you want to avoid micromanaging a human. Instead, give clear guidelines. You want to do the same thing for agents. And see a lot of the same things that's up like. It's very easy to get distracted. Focus on the the near term win of just handholding this person or this agent. But that doesn't make you scale. And the author of Working Well with Agents is allowing you to scale. Because you have scarce human attention, and the more you can have the agents do that, well, it helps. Another thing on those lines, it's really valuable if you can teach your agents how to manage up. So just like as. With humans, you want them to be really good at knowing what to escalate to you, how to present their work, how to summarize. That's really valuable for agents too, like if if the way you review them. Is by looking through. Code line by line. And by yourself curating all the work and walking through the thing. That's not making good use of your time, and it doesn't scale that well. Still, if you tell her to write a report summarising the core design decisions they made. The cool things that might need further attention. That's much more valuable. Similarly, you should not have to do QA. So 1 workflow I found is super valuable is as part of every. Piece of code that's done that actually changes anything user facing. The AI should create a screenshot based walkthrough showing. The sequence of things you can now do in the app, exactly what is seen and a description of why that screenshot is showing doing the right thing and then. Before you look at those screenshots. And another AI should look at those screenshots confirm it looks right. And it only gets to you. But it really deserves human attention.

[00:28:31,281] Leo Walker: Yeah, yeah. I think that there's a lot of really good stuff there. Umm, a couple of it is like, hey. How do you manage like? OK, so if I think about this, how A-Team would work? You have like document high level documentation of what the product is or what the epics are that you're working on you. Digest those down into. Like product features that get built out and those features turn into stories. These parallel agents could be working on a feature and then different, you know, user stories in between there. However, I'm like, where do I keep this documentation so they always have the right reference material on what the feature is and what they're working on? And part of me is like whoa, we should stick that in a docs folder in. In the repo. I'm like, well that's decent, but. A lot of business users like to use Word documents so that you know if you're reviewing what an agent does or just making sure that the high level plan. Makes sense that you could use like Notion or a Word document so. What reference material or what kind of like self? Updating. Documentation. Do you have that all of these agents are kind of writing to? And then when they put that report with screenshots together, where does that live?

[00:29:51,308] Rob Ennals: All very good questions. I think to some a lot of these questions, including previous ones are ones where. There is no necessarily sets known best answer because so much of this tech is so new that we don't have best practices yet. Like for olden tech patent tech, we were slowly had time for best practices to emerge. I don't know if there are best practices, so I do personally what I find works pretty well. Is everything should be in the repo in one exists other places as well. But everything's at least also be in the repo. Because it was in the repo, it's easier for the agents to come across as an easy diversion, control it, et cetera. And maybe in some cases you want to also sync it with some other doc somewhere else. Author like GitHub issues are also quite easy to access because there's an API I can get hold of them. So the way we tend to work is that. Everything is either in the repo or in a GitHub issue or on a PR that these things are very easy for the agents to. Gabap. Another thing along those lines I found is really helpful is. There's a lot of value in having very strict code documentation requirements. Like I like to have a link rule that. Every file must have a. Comment at the top saying. What does this file do? How does it do it? What are the key design decisions it follows and how to relate to other files? And. Similar, I like to have a requirement for Remi dot MD if every folder where it says. What is this folder about? What is the key philosophy of the things in this folder? For each, then for each file in this folder, what is it for? And. Having that stuff exists makes it way easier if your agent wants to navigate the code, because agents nowadays mostly the semantic search, they find out what goes on by like. Walking around the tree, reading files, following links. And if your cobase is a. Spider's nest of. Who knows what that's not going to work for? Was if everything is OK, I know what this file is, where it's from, I can walk up the top and like. You can easily navigate. It'll work better than humans. And the reason why humans don't normally do that is because a ton of work. If every time you touch a file. You've got to update the documentation from that far and every related file and the folders. It's the pain that humans don't want to do it. But the great thing about agents is their time is cheaper than ours. They're not necessarily super cheaper compared to a human that pretty super cheap. And so it's usually worthwhile to say OK as part of your validation process. You've got to have checked all your doctor up to date and make sure there are. Done similarly with with things like lint rules. It's really worthwhile saying that. There's unit test. The breezy high unit test coverage engineers wouldn't stand for. These kind of things were. Agents can do this on this. Painful bureaucratic requirements that humans. Too much overhead for. But it pays off.

[00:32:41,413] Leo Walker: Yeah, yeah. I'm I I almost wanna like dig into that deeper of asking like hey. How big are these doctrines at the top of each file? And then how big are your docstrings for each function? But I feel like that's like, you know. Like mission dependent on what's the standards of the code teams and things like that because and then also like. In bigger teams. People could be pushing code and then you might have a documentation person. So do you use a different agent for that? But maybe Rick has a little bit more light on that because he raised his hand. Would love to hear him come on.

[00:33:17,139] Rahul Parundekar: I think time I went first but.

[00:33:21,116] Rick Lewis: Oh, hello.

[00:33:22,438] Leo Walker: Yep, we can hear you.

[00:33:22,945] Tanmay Tiwari: No, it's my voice number.

[00:33:23,390] Rick Lewis: So you have anything more on this more the question is? This is fantastic. This is stuff that I've been trying to off of medium post and this and that.

[00:33:30,787] Tanmay Tiwari: Yeah.

[00:33:32,878] Rick Lewis: This Treaty of this together. Is there some Bible on how to do this well? Because I don't have to reinvent the wheel, nor does anybody else care. Does anybody know where that Bible exists?

[00:33:45,339] Rob Ennals: I was. I'm not aware of a Bible that I think is covers everything. And partly I think part of the reason it doesn't exist is writing a good Bible takes time, and the world's moving so fast that by the time you wrote it will be out of date. I've been considering writing A blog post to cover all this stuff, which maybe you'll like when I do that. I I blog at Matthew Progress. Put substack.com.

[00:34:08,101] Tanmay Tiwari: Yeah.

[00:34:08,433] Rob Ennals: And I'm probably going to do a blog post about these kind of practices sometime this week. Other than that, I'm not aware of any like definitive covers everything valuable but also like. This knowledge is split across Allah different people as. Pretty, pretty. Everything is written by somebody, somewhere. Another feather single source, unless somebody else knows of 1.

[00:34:27,855] Leo Walker: Well, let, let me put that back to you there, Rob, when you were at Google versus Quora versus Facebook. Did each of those companies have a Bible that you know? Were similar to each other's? Or was Google's Bible different than Facebook's Bible, if they even had a Bible for each of your teams?

[00:34:46,758] Rob Ennals: Oh my, there was a variety of different docs on different things. My reckless. Obviously it was a while since I was at Google. My memory is kind of fuzzy. They'll offer me docs, OK? He is the coding standards in this language or he is like. Basic design principles of this system. I don't think essentially it doesn't usually have one. Don't, but my memory is fuzzy. And definitely like different teams wouldn't necessarily work the same way, partly because there's different requirements. Like you don't necessarily want exactly the same ways of working in every piece of your code base because. So much the tradeoffs are different. But it's possible the trade-offs are less different with agents because you've got this bigger thing that their time can be wasted more effectively. That some of the things. Often just worth just being super strict with everything because their time is. Someone says strict libraries used by Google Fang and Fang don't. It wouldn't do it that much anyway.

[00:35:43,621] Leo Walker: Yeah.

[00:35:44,809] Rob Ennals: Some things and stuff.

[00:35:46,836] Tanmay Tiwari: So what I said was.

[00:35:47,116] Leo Walker: Yeah, Todd, may I, I saw you raise your hand. You want to elaborate on what you typed up there a little bit?

[00:35:52,264] Tanmay Tiwari: Yeah, yeah. So what I have found is that. Uh, see, uh, AI. Knows lies. To do action a lot. It is so it will try to do anything it has to so. A lot of probability goes behind it scenes. And doesn't matter if it's Opus, Sonet or anything. We have not seen in practical that much improvement if we go beyond a. Context window. So if you see let's say 150 context window, it starts off getting fuzzy. The beauty it starts its when you start a. Fresh project. It is very good at that. But let's say you have gone through a week into a project also. Or anything. Then this MD files matter much more than. Before actually. Because. Is the project. See the main difficulty in coding was never algorithm. Actually nobody used to write algorithm by themselves, they used to Google it. If you see in it, an algorithm is easier for LLM to do because see it is difficult for humans, but it is a very fixed constraint to what? Let's say I have to get more followers. I have to do. It may sound difficult for a human, but. There is a pattern recognition there. The apps where AI is very good. AI is very good at maths. And structure. That's why it does Rust very well. Right, So what I have found is the most important part. It is it needs to know the database schema very well. What each table is there? Interface file is the most important thing in it. Now what happens is whatever task you are doing so it has a front end part, back end part could be a database part change also. Init and an infra part. So let's say you are adding some properties anything. So the database part needs to be done first. So it knows what the contract is. What the contract is then basically do some sub agent. So what happens when it is deciding the planning stage it knows. I will do 810 things. Write it. We we force it to think like in using soul MD files to think like. A senior Fang engineer. Do not ask it to think like an engineer. It will go through it. You have to force the memory you have to see. Fine tuning is not that much needed. You have to show it some examples on it. It then triggers it on it. So the what does a Fang engineer do? It has. O log NON, that's the most important thing they try to do. So it complexity is reduced. Second is they try to do it make it distributed as much as possible.

[00:38:24,307] Leo Walker: Yep.

[00:38:24,395] Tanmay Tiwari: 3rd is they tried to make it uh reuse component as much as possible. So when you force it into that, it starts thinking in that that and when you give it 20 years experience. So it starts thinking like an old man.

[00:38:36,600] Leo Walker: Yeah, I.

[00:38:36,714] Tanmay Tiwari: He doesn't think of. Pressure. So these are all psychological promptings we do. You know, people don't realize that any LLM can. Talk in any emotion also. If we can get some emotion, anything you do not need to do fine tuning in that much. It can abuse you into anything.

[00:38:51,216] Leo Walker: Yeah.

[00:38:52,079] Tanmay Tiwari: It's not that difficult to do, right? When you do that, the main thing that happens is when sub agents run. The problem arises. So it has a plan. But let's say this file change. That file changed. So you cannot have much more agents running because what this change to that? So it has to connect a lot.

[00:39:09,369] Leo Walker: Yeah.

[00:39:10,845] Tanmay Tiwari: So that time it is thinking that. Well, so beyond 2-3 agents for let's say front end, beyond 2-3 agents for back end together. From my experience, it doesn't work. That well. Ex. High opus and extended thinking is good in planning mode. Beyond that, it's a waste of token and if you see. The the biggest problem is. If you go over 200 K context window. So what happens in chatting is when you chat it a lot less. Token goes but in coding every time it gives everything and they got like $5 let's say till 200 K then they asked 10 dollar $10 per input million token.

[00:39:38,719] Leo Walker: So yeah.

[00:39:48,048] Tanmay Tiwari: So if you got 500 token you will get bankrupt very fast.

[00:39:48,362] Leo Walker: Yeah, yeah.

[00:39:52,804] Tanmay Tiwari: So that's why open source models will win there. So that's what my experience has been in doing it.

[00:39:59,542] Leo Walker: OK. I I think that you hit on a lot there, so I'm going to try to like. Breeze over it real quick to make sure I understand it and correct me if you see anything wrong here SO.

[00:40:08,815] Tanmay Tiwari: At.

[00:40:09,239] Leo Walker: What I heard is like, hey, LLMS are wicked smart, but they don't have. A lot of their own baked in standards because they graduated from every university in the United States. So if I grab a individual that attended every university in the United States and I tell it to. Create me a website that.

[00:40:26,105] Tanmay Tiwari: Yeah, yeah.

[00:40:27,464] Leo Walker: Each agent might use different frameworks and might use different libraries.

[00:40:31,195] Tanmay Tiwari: Yeah, yeah, yeah, yeah, yeah.

[00:40:31,577] Leo Walker: And different things to build it so. If you grab these PhD candidates that attended every university and you stick it in a company, that company has to have standards and has to have a planning aspect that says hey. This is how we decompose things from epics to features to users. This is how we.

[00:40:49,887] Tanmay Tiwari: Yeah.

[00:40:50,511] Leo Walker: Have our different compute storage and um. Like hooks through it. These are the patterns that we use that are acceptable. These are the patterns that are unacceptable and. When we decompose these tasks down that. We have certain orders that we do things because it makes sense, IE. Like write up a schema. If you ever have that schema in Prisma or whatever that you need to make sure it aligns with the database and any kind of planning that touches the front end needs to align with the schema. I think that any company that you go to,

[00:41:20,884] Tanmay Tiwari: MMM.

[00:41:21,779] Leo Walker: any good company that you go to should have a lot of those standards written out.

[00:41:25,673] Tanmay Tiwari: Yeah.

[00:41:28,293] Leo Walker: So that if a really smart person joins that team that they're just not going at what they did at the last company, but they're. They're adhering to the standards at the new company. And the new company has. QA validation, stuff like that. So I think that's the harness that Rob was talking about there is like, hey. Your QA. Isn't just like a hey. ChatGPT QA this code for me it's like hey. Here's our standards that you should be investigating this by. And then for the coding agents, they're like, hey, look. You have the MCP tool that allows you to query. Schemas. Here is the folder that has the database that has the schemas and. For every website that you're talking to. This is the patterns that we follow and things like that. So I think that. You could grab the smartest person. You know, from Harvard. And you could grab a person that hasn't even. I attended Harvard, just did a lot of online. Coding training and that's like what I view the open source and I view the Harvard graduate as the closed source ones. Google hires both of them, right? But Google assesses both of them like hey, how well can this Harvard graduate and this self-taught?

[00:42:37,719] Tanmay Tiwari: Yeah, yeah.

[00:42:44,874] Leo Walker: Coder abide to our standards and whichever 1 abides to our standards better, we're going to use. And hey, we're paying $300,000 a year to this engineer so. Really, we don't care what tooling they use. Like if they use software that's. $50.00 a month versus $1000 a month because. The the opportunity for what they're building is just so high. So I think that like what Rob has is this framework of like running agents in parallel is there because at these big companies how you do get control is huge and if you put. A dozen engineers on a single team and tell them to work on a single feature, There's someone have a lot of those conflicts. Of working with like get merged.

[00:43:26,333] Tanmay Tiwari: That's why they make model. So they make modelers Sir, if you see Google. Google has so many small modeler components in it. Content projection, let's say on front end and these kind of stuff. Startups don't do it. They're that way because we have to focus on a lot of speed, actually. So that's how we try to do less conflict and they used to raise a lot of PRS also. So if you see in Google, if you go anything I had like as a contractor experience. Small PRS are much more required here. In startup, it is not there like we have, let's say, a very hard deadline and we have to go. Through that. That was my experience there. And district libraries they used to use. Startups don't do that. That much, uh.

[00:44:05,742] Leo Walker: Cool. Well, it's it's the standards, right? It's like startups are moving fast. They didn't have a lot of time to set their standards in the documentation. Google has had a long time and they have principal engineers that their whole job is to make sure that the organization runs well, right where startups might have that principle.

[00:44:20,082] Tanmay Tiwari: One thing you. I'll say is most people don't realize this as most have not used sub agents. You will see a lot of burnout happening in 5-6 months. The reasoning is it's like a machine gun attack coming to you. So what happens? Yes. So you have to let's say 1 1/2 two hours work. Then you have to take rest for 30-40 minutes. The reasoning is. Earlier when you used to do work was you had a plan and you then you went into like a silent mode. You would like? Flow straight in doing things now.

[00:44:48,721] Leo Walker: Yeah, yeah, yeah.

[00:44:49,164] Tanmay Tiwari: Now because. Output is coming. You have to check what is breaking or not. Constantly. So you have to.

[00:44:57,154] Leo Walker: OK.

[00:44:57,158] Tanmay Tiwari: Process a lot more information. You may not be writing the code. But you are.

[00:45:01,309] Leo Walker: Yeah, yeah.

[00:45:02,897] Tanmay Tiwari: Discussing what it may be breaking or not breaking.

[00:45:06,434] Rob Ennals: Ideally you don't.

[00:45:07,073] Tanmay Tiwari: And.

[00:45:10,073] Rob Ennals: If you're having to manually check what's breaking, what's not breaking? You've got a problem in your process. It's like, let's say you're the CEO of a company.

[00:45:16,643] Tanmay Tiwari: Yup.

[00:45:17,601] Leo Walker: Yeah.

[00:45:17,871] Rob Ennals: If you have to, if you. Of a company I'm to constantly track whether you're engineers or. Breaking your product. You got the wrong processes. Ideally if you if you every time you find an agent does something that breaks stuff. That isn't the case where you need to micromanage that Aiden. That's the case. We need to improve validation flow. Idea. You've got to have a better E3 test, a better unit test, or better sub agents who are checking particular properties, or better screenshot walkthroughs or whatever validation screenshot walkthroughs.

[00:45:43,802] Tanmay Tiwari: Yeah.

[00:45:47,629] Rob Ennals: But yeah, I think if you are micromanaging tons of parallel agents, you can have burnout. Because like, humans just don't cope that well without a few huge tons of stuff. Particularly of most of the stuff they're reviewing. Is noise or low signal or stuff doesn't matter. So it's really important to teach the agents to manage up so everything they show you. And is like almost like deep works. You get a secret's OK, here's a deep fun thing to think about. Here's another deep fun thing to think about. Really like the way humans like to think. Was if you really are just jumping agent to agent micromanaging them.

[00:46:26,674] Tanmay Tiwari: No, yeah, if that will crash. That will cry, but.

[00:46:28,993] Rob Ennals: What's up? Yeah, yeah.

[00:46:30,546] Tanmay Tiwari: In enterprise. My experience is definitely you are right, we will have some kind of process later. In enterprise, what happens? We have small business logic everywhere because they're see what will happen. Most people not realizing is let's say Fortune 500 have agent to agent. Right, everyone will have it. So the advantage won't be the agent. So you will need much more. We will have we having a third layer coming. This will be the real Web 3. Like agent to agent happening behind the scenes. Because see, if only one or two companies had it, then it would have been an advantage. Because you are rolling this out to basically thousands of companies. So there will be a, that's what. I am seeing I could be wrong on this. I'm not saying but you will reach a limit to it. And you will having a much work will not decrease actually. And. Work will increase. What I am saying is because see. Every company asks an ROI. Right right now because we are in an inning phase, each company where I have seen like 2-3 experience, I have like.

[00:47:29,798] Leo Walker: Yeah, yeah, yeah.

[00:47:34,878] Tanmay Tiwari: From other people. Now companies inside are asking. What we will or we see, that's what Amazon is doing right now. Amazon asks for KIRO. Why did it break what they are auditing? That's why they asked us slow down. This is happening in much more places than people realize.

[00:47:50,419] Leo Walker: Was so so. I think this is a good segment for. US transitioning from the basics to making it actually work and covering the hard things because. What you're covering here is some of the hard things here is like. How do you like manage your attention across the agents there for it is what we just digged into. And then how exactly do sub agents or agent-to-agent handoffs work? So if you're working with agents in parallel? They have to be talking to one another.

[00:48:17,509] Tanmay Tiwari: Yeah. Yeah, exactly.

[00:48:18,403] Leo Walker: Hey, today is Google's like framework for how agents talk to each other but. How? How Rob has Brumi? If the agents are writing to a document. That they all could read and write from.

[00:48:30,743] Tanmay Tiwari: Yeah, yeah.

[00:48:31,020] Leo Walker: Then they're essentially talking to each other, right, because they're handing over some documentation. And this also gets to the part of like how big is a team at Google and what is the? Size of the feature requests or the pull requests at Google could be very different than at Facebook could be very different at. Open AI, which can be very different from Mitchell, right? So like. We can't set hard set rules on how big PRS are or how big teams are because. Really. Depending on how you structure your standards for the organization and also how you. Allow people in the organization to talk to each other. You know, Slack or. How will you even teach them to meet? To communicate with each other? Could be. Organization wide of how big your teams are, so I think the same thing could be for parallel agents. And if you are really good at. You know, handling a big team. You could have a bigger team and. If you're only using git. Umm, branches then. You have a limitation. There were a funnel, A bottleneck there. So Rob found that to use get workflows that it really helped our work trees.

[00:49:35,700] Tanmay Tiwari: Those are.

[00:49:39,921] Leo Walker: It really helps there. So Rob, do you want to go into anything of? That we're talking about here of making things work and some of this hard. Stuff that we might be covering here.

[00:49:50,033] Rob Ennals: I think there's a variety of things you can touch on here. I think the the topic of how agents should communicate with each other. I thought that's a very new and open space like. Claude only just released the Agent team's thing It's experimental feature and select. This is very new thing for workout. How to make this work? Well, I've played around with a variety of approaches for doing it. I wouldn't so I've. Got a strong opinion what works best. One approach is the very simple thing of just. Tell one agent the other agent exists in some other work tree. It literally goes and looks at what they're doing and literally go and looks at their planned files and they can just do that stuff. I don't know if that's a good approach, but I've done it. Another approach is tell them to write have a docs plans doc that describes. All the different things currently going on. So that agents can be aware not just to watch on the repo right now, but what might be in the repo in the future so they can align with it. I think another thing is that potentially this kind of alignment matters less for agents than for humans. For two reasons. One is the agents are really good at resolving merge conflicts. So one of the reasons why humans want to coordinate is that for humans, resolving merged conflicts is one of the least pleasant parts of being a software engineer, and you want to avoid it at all costs, even if it means lots and lots of extra human coordination effort, but with agents. Just give him a skill that says read the P, read all the PRS committed since he last pulled in, work out their intents, and then work out. When you merge in everything. Use the understanding to fix everything, align it and it usually works pretty well. Not just for the syntactic conflicts like get noticed, emerge conflict, but also like the more semantic ones of these are going different directions and for humans you don't want to waste their time in doing it because reading every PR is like a hassle. And fixing everyone these. Several 100 conflicts are the hassle. But this is the kind of grunt work which agents are really good at, and if having them do that works, saves human attention of trying to coordinate stuff in advance. It's probably worth. Another thing along those lines is with humans. You really want to make sure the architecture is right up front. Because if you need to refactors with different architecture is this huge ton of wasted human effort. As you really try and book this effort in that front of like a greedy architectural advance. Well, I think that matters less with agents. Because it's more OK to waste their time. And they're generally pretty good at those. Those kind of refactorings where you're external validation stays fixed and E2E stays the same, and your integration tests stay the same and it knows if it did it right. They're pretty good at that kind of stuff. So often just worth just like. Let them go in the wrong direction with architecture. Don't necessarily block that to an advance. Change it afterwards, and to some extent you do that with humans as well, like if you did like architectural review of every change. That wouldn't scale, but I think the threshold of at what point you need to coordinate versus at what point you back up and undo it. I think is different when working with agents.

[00:53:04,285] Leo Walker: Yeah, I oh man, I I think that. Back when you know teams would do full PR reviews of bringing you know 5 engineers in to review it at the same time or something like that. And then that's like, you know, $100.00 an hour or whatever of their time. That's a really expensive PR. And wasting their time for multiple hours sounds really expensive.

[00:53:22,718] Rob Ennals: Yeah.

[00:53:25,109] Leo Walker: And you're like, yeah, I could let Opus cook. I could let 5 opuses cook and cook for five. Dollars each. And that I could literally throw out four of those options and still save more money than if I did a PR with, you know, a lot of. Actual engineers and you could do that over and over again before the PRS. So that sounds very interesting of like. I don't mind wasting Opus time even if it is. Literally dollars or millions of tokens of. Tokens there.

[00:53:55,113] Rob Ennals: One thing to bear in mind here is this is the most expensive and least capable these models will ever get. So it's worth designing your workflows around an assumption these models are going to get better and cheaper.

[00:54:08,224] Leo Walker: Yeah. Yeah. Oh man, I don't even know if cost is too much of a factor right now because like. If I cook through Opus. And I'm like oh GPT 4 is cheaper or Gemini 3.1 is cheaper. I'm like no no, I'd rather pay an extra $5 and go through Opus than save money on GP or on Gemini 3.1 right now. For something SO. Ah man, I I know that people always talk about the cost of tokens. But for enterprise? And that slope going to 0. If people don't care about it now, will they care about it eventually with what you said? The cost per. Valuable token. Is only going to go down.

[00:54:54,332] Rob Ennals: Yeah.

[00:54:55,774] Leo Walker: For sure.

[00:54:56,274] Tanmay Tiwari: Leo, I think that it matters a lot in a lot of places, actually. There may be less, but we have quotas everywhere. That is why ah. From my experiences, open source models, even the top ones if you have skill MD files in them, are. Equally good as Opus or anything. And they are way cheaper. Uh, like, see, on a planning stage, I get it. On a planning stage, you may get it. But once you have got certain pipelines going, see. You will, uh, you. Maybe for a few days you may not know, but for certain tasks you will have basically. Some procedures you will find. Tune it OK, know it. Now you will keep learning new things in future but. For production you will do some kind of. Doing so, it has much more reliability towards it. Right now because. Internally, everybody wants to ask how we'll get this reliable. Everybody asks. Even at the top, it's silently as it is done that way. One more thing that is coming what I see is the concept of pods. So you will have multi agents working like differently in pods so you will. Let's say I explained from my experience front and back end, but let's see, you got a marketing team. Also what our sales team. You also got different things, so all will have different memories to it. So that way you will have multiple agents running. Different tasks on it. Each task may have a limit to let's say 2-3 agents you can run. Maybe you can run 10, Who knows right? But and that they have a shared memory to it. So let's say you have got and you can have a very big agent running your live music. That's where I see it happening. Well.

[00:56:32,307] Leo Walker: Yeah.

[00:56:35,510] Tanmay Tiwari: Towards it. And I will say one thing, Chinese models. Are way more powerful than people realize.

[00:56:44,392] Leo Walker: I I think they're.

[00:56:45,340] Tanmay Tiwari: A way more of half.

[00:56:45,861] Leo Walker: I agree with you. I I think the Chinese models is where opus. 4 point like 1 was you know and Opus 4.1 was fire.

[00:56:53,997] Tanmay Tiwari: Mono support and Friday. Say 4.5 you can say Kimmy and see you have to make.

[00:56:58,509] Leo Walker: I don't know. I don't.

[00:56:59,000] Tanmay Tiwari: See what what Opus does behind the scenes is They have got more architecture, they have made it understand Claude MD well. For that not to make it a skill MD file say. In this this is that This is that if you do that. It understands. See LMS are not that different to each other.

[00:57:15,603] Leo Walker: Yeah, I I agree.

[00:57:15,742] Tanmay Tiwari: Not that.

[00:57:17,019] Leo Walker: It's just like what they've been trained on, like. I was listening to.

[00:57:23,404] Tanmay Tiwari: I think they format the structure of the API also Sir. So when we run open source.

[00:57:23,407] Leo Walker: Anthropic CEO talk about like, Oh yeah, like. A lot of them are good on short context window stuff because they've been trained on short context window, but what happens when you've been training on 200K that Claude could could crush it there? Oh.

[00:57:40,858] Tanmay Tiwari: We do not have that. Thing right. So when you are getting the surface from anthropic, they have made it to so Claude MD file it gets it there. There is. See if you see if you use Anthropic Opus model on cloud code versus cursor. On cloud code it was better than cursor. Same model, same API pricing you are giving it. But if you see it, see. Plot code got famous, cursor got destroyed.

[00:58:06,679] Leo Walker: Uh, it's all how you manage the context window, right? And like, whatever the framework is.

[00:58:09,695] Tanmay Tiwari: Yeah. So cloud board action, Yeah, exactly so.

[00:58:10,852] Leo Walker: Like Rob's for that.

[00:58:12,231] Tanmay Tiwari: Report was stumbled for it actually.

[00:58:14,027] Leo Walker: Yeah, and.

[00:58:14,783] Tanmay Tiwari: That's why same model, same model. You are playing the same API price, right?

[00:58:17,445] Leo Walker: Yeah. Exactly the the whole part of like. Like I said before, if I hire a PhD, that's. That's graduated from every university.

[00:58:25,959] Tanmay Tiwari: Yeah, yeah.

[00:58:26,126] Leo Walker: Whatever harness or standards I give it will it will perform differently at my company than at Rob's company, right? Exact same person will perform differently

[00:58:32,622] Tanmay Tiwari: Yeah, yeah.

[00:58:33,086] Leo Walker: at each of our companies and differently than at your company, right. And I think that I agree with you that like hey. If we move towards like how we're doing with humans. Every scrum team should have a marketing person and a QA person and you know every scrum team has this multi agent team so.

[00:58:51,945] Tanmay Tiwari: That's gonna happen. That's gonna happen.

[00:58:53,537] Leo Walker: Why can't? Your parallel agents have a marketing person, a business operations agent, you know all of that stuff, right? And I think that's where it's going to go. And you know where you keep on saying like, hey, open source could be fire. Yeah, Google hires self-taught coders, right? But in general.

[00:59:09,450] Tanmay Tiwari: Exactly, Yeah.

[00:59:11,520] Leo Walker: They would like to see a degree. You know. Like degrees typically do a little bit better and that's where I think closed source models typically do a little bit better, yeah. You could get the. The self coder. To to crush it, but. Degrees matter to some people.

[00:59:29,892] Rob Ennals: Although one thing to talk about along these lines is. I know one of the best ways to reduce. Costs is to find places where. Your Asians often churn. And work out ways to either build scripts or tools or skills or docs. They don't get stuck in that thing often. If you look at your agents, who knows, OK, they often get very, very stuck. Rat holding on this. And you, as a more experienced person, can say no, let's just write a. A PMPM script or a code mod thing that does that thing really really quickly and easily. And that's often one of the most effective ways of like pruning down. Both. It's a wasted time and that's how much they quickly do stuff and have a few mistakes they make and potentially. If you do that in the right way, you can. Authors simplify a task to the point where you can use a cheaper agent. Like, maybe if you don't guide things very well, you've got to use. Claude Opus 4.6 because it's a hard task, but if you break it down with the right scripts and the right. Docks and the right skills. There may be a simpler model can do it because now you've given enough of a framework and a handhold. Or if you get really simple, maybe a script does the whole damn thing. And then Sean knows what's useful and so they get a really smart multi, really, really thoughtful and write the script. And then it does the rest of it.

[01:00:50,045] Leo Walker: Yeah, yeah. And I. I mean. Open source files will catch up. We'll see. We'll see how they go and exactly that. Like open source models, you could fine tune more, you could do on certain things and. Like what I would use open source models for right now is a lot of OCR. Stuff like don't use old OCR. Like models use. Uh, any of the fireworks ones, you know? Umm, yeah. Yeah. So we're getting towards the end here. We've got about 5 minutes left or so. Are there any questions from the community that would like to ask or Rob, is there anything that? We haven't covered that you wanted to cover during this.

[01:01:36,888] Rob Ennals: I think we cover a lot of the stuff I was going to talk about, I guess. One that I hinted on may want to draw up more strongly. I think there's a lot of value in getting humans out of the loop. I think that any time you find yourself need to be in the work loop. Checking something, approving something, walking through. OK, why? There's a lot of value in workout? How could I have not needed to do this? It's like. Give you make sure your agents have access to sensory so they can pull in sensory logs directly. Make sure they're really well set up for playwrights. They can exercise the app directly. Make sure you've got a. Good enough? E2E tests that really actually can test things for real, so you don't have to have separate manual validation. Make sure they know how to do proper UI validation so you have to do as much UI takes. Anytime you have to do a thing. Look at how could I not have to do that thing? And sometimes it's just a hard enough thing that the. There yet been a few weeks they will be probably.

[01:02:38,495] Leo Walker: You you keep on hitting on the the human stuff that I'm getting to where whatever you're saying just makes me trigger the human stuff that I'm thinking because I'm like. OK as. As a developer, as a person that wants to grow up through the org, how do I delegate my tasks down to someone else? And how can I justify that I need to hire someone to do these tasks so I don't have to do them? And in organizations, if I hire a team. And I delegate those tasks I have to a. Write a job description BI have to find a person that I could trust to do that stuff and then see. I need to be doing. Monthly, if not quarterly, if not for sure, annually reviews to that person to tell them how they're doing and how they can improve. And if depending on how they're doing and how those reviews do. Is it a failure on me for not giving them clear enough instructions and boundaries and evaluations? Or. Did I just not pick a smart enough candidate? Should I have gone with? The open source because I thought it was cheap. And I needed a, you know, offshore candidate or? Can I pay the expense of? You know. Local. Workers that are near me and am I good? Am I a good enough boss or am I just are they failing me and it's because I'm failing them?

[01:04:00,298] Rob Ennals: There's a lot of truth there. I think one important difference is when you're hiring people. And you really want to be very cautious about hiring the right person because it's really mean if you lay them off a few weeks later because of the wrong person. The AI, if you start using a model, it doesn't really work very well or you find out actually AI can't do this kind of validation to us very well and you decide to stop. Doing it. It's not necessarily cruel to stop using agent in the same way. So in some ways it's very, very similar to hiring people, and in some ways it's very importantly different because the risk of hiring the wrong person is much higher than the risk of hiring the wrong agent.

[01:04:35,998] Leo Walker: Absolutely, absolutely. Especially if you have them move across country or something like that. Or you tell them that you hire them for one job and you're telling them to do a completely different job.

[01:04:46,276] Rob Ennals: Yeah, yeah.

[01:04:46,365] Leo Walker: Models will not care if you change their job for them for sure. Um, so awesome. Awesome. Well. Is there anything else everyone? Any questions, comments? I see some stuff going through. Yes, we will get the recordings out. I'm not 100% sure about the transcripts. But this will be available to reference later. Awesome.

[01:05:10,607] Rahul Parundekar: Any any ideas on what next week? What do you want to chat about?

[01:05:16,596] Leo Walker: Umm, I might actually, uh, put a pause on it for next week 'cause I I might be traveling. But if anyone has any suggestions on what to cover? Call it in two weeks from now. Be happy to see it in the chat or in the Coding Agents channel. If we want to hear more from Rob or Broomy. Definitely give us feedback there. Really appreciate your your time, Rob. Really valuable insights and awesome conversations here. I'll hand it back to you if there's anything last that you want to say before closing out or Rahul if you want to say anything either.

[01:05:52,223] Rob Ennals: Sweet, this was.

[01:05:54,150] Rahul Parundekar: No, I think I'm a bit.

[01:06:01,893] Leo Walker: Rob, I can hand it to you. Yeah.

[01:06:01,931] Rob Ennals: Off. I accidentally talked over somebody. Whoever I was talked over, please jump in again.

[01:06:10,563] Leo Walker: Awesome, awesome. Well, thank you everyone. Uh. Put feedback in the Coding Agents channel on the Slack channel will. Put out when the next session is and thank you very much. You guys have a great weekend.

[01:06:26,171] Rick Lewis: Thank you very much for putting this together.

[01:06:27,332] Leo Walker: Hi everyone.

[01:06:29,298] Rob Ennals: This was fun.

