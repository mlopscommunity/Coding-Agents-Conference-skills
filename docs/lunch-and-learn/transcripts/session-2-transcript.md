---
title: Coding Agents Lunch & Learn s.2 - #1
source: Gradual
---

# Coding Agents Lunch & Learn s.2 - #1

## Transcript

[00:00:00,000] Leo Walker: Everywhere that says Claude, feel free to replace it with whatever you use if you want to share a story. So a lot of these artifacts. Umm, through here. Like hey, do things in parallel. Cursor does the same thing, or Codex could do the same thing, or depending on what kind of coding agent you use, it could do a lot of the same stuff of working in parallel. Or you know, starting everything in plan mode that cursor definitely has that, you know, invest in your Claude is cursor rules and you know other ones have rule identities there so. How we're going to set this up is that there's 10 rules here. I'll make sure to post this in the chat right now so if you guys want to read through it or get kind of a. Idea of the 10 steps here. Were the 10 rules here? And that anyone that wants to talk about. Their experience with that one will have like 1 to 2 minutes. Maybe have two people per rule or so and see how it goes to really. I don't know get this going. Are there any questions, comments, concerns from anyone before? We get it rolling and whatnot. Demetrios a ruble? Anything to to add?

[00:01:11,658] Rahul Parundekar: Yeah, Demetrius gave us some context on all all the amazing coding stuff that you have been. Watching an upcoming conference as well.

[00:01:19,224] Demetrios Brinkmann: Well, yeah. I think the the cool thing about this is that we're all our own little R&D. Departments these days. I don't know if you guys have noticed it, but. Being able to come and get together and share. Is. It's helped me so much and it the kind of the spark for this was when we did the reading group in January and it was talking about vibe coding. And it. Devolved into something where we. Just started talking about what has been successful for us. And so we wanted to do more of that and I appreciate. Raoul and Leo. For saying, yeah, we'll, we'll do the more of that, let's do it. And then we just get together and we hang out so. The real idea here is let's make it interactive and let's share. What we've been. Researching and what's been effective. And I also want to call out like at the. We're doing a coding agents conference right in South Bay in. On March 3rd. And I want to figure out like. If folks know. Or have ideas on how we can make? The sessions in there more like this sharing. Let me know. Hit me on upon Slack or. Umm yeah, tell me in here in the chat, but I don't want to divert the conversation too much so. Hit it, Leo. I'll let you take the floor.

[00:02:49,158] Leo Walker: Awesome. Well, so anyone could come off mute or raise your hand if someone else is talking for sure. If you guys want to share, we'll go ahead and get started with one of the first rules and. To be honest, for me this is really hard for this working in work trees or even. In multiple like branches here, they say like, hey, Claude has these work trees, but also people could just like check out multiple ranches, whether or not you're have cloud agents or like local agents. And just like being able to review and contact switch between all of the different agents working on different branches and then having it to merge together is like very hard for me. So this is one that I actually would love to hear if anyone has been successful with this. What are the bites? What's it like the size of work that? Anyone has had success with? Making multiple work trees work.

[00:03:49,406] Rahul Parundekar: So. I think. Around the same time in December, these guys also posted like hey, they built out. Claude Co work using Cloud code. And they, I think the, the data point they gave us was like everybody's running like. About 6 to 8 agents in parallel. I cannot. Have like brain cycles enough they're more than three so I'm always like stuck with.

[00:04:11,680] Leo Walker: Wow.

[00:04:13,181] Rahul Parundekar: Just Max 3. Agents, maybe different projects or maybe 1 project, 2 agents, but that's all I can do. And then. The do more in parallel. I haven't been successfully able to do get work trees but. I know a few people who when they're doing research, they're doing it with work trees.

[00:04:33,076] Leo Walker: Yeah, I, I think the research part is great that if you could have sub agents like go away and fill out markdown files or do research on how it all stitches together. But doing big code changes, uh, in parallel and then having to, you know, merge those together could be hard or umm. Uh, cursor has a way that you could send off multiple agents for the exact same task and then you could kind of like see which ones better that way And umm, I think Cloud's kind of moving towards that too of like, hey, uh. Do like a council of like send off 5. Workers to work on the same one and then have another worker judge which of the five did the best and then accept that one could be a pretty wild way to work in these work trees.

[00:05:21,094] Demetrios Brinkmann: Yeah, I've seen actually two weeks ago one of the talks that we had. They were saying do that, send five workers off. On the exact same task and then whichever. Code passes tests the most. That's the one you choose.

[00:05:37,994] Leo Walker: Yeah. Yeah, like test based. Umm. For there for sure. Anyone else in the audience have a? Any experience with this or would like to share?

[00:05:52,559] Addison Klinke: I think I find. Empirically this is kind of two to three range as well if it is more deep coating, umm. One thing I was noticing. Earlier this week. Maybe we'll start paying a bit more attention to IS. There are. Decent amount of tests I have to do that. Are not necessarily coding. Maybe not writing code so like PR reviews or writing design docs or? Whatever else and so. Rather than trying to paralyze a whole bunch of clawed. I could do a little bit less there and have. One of those be my. Kind of. I'm filler. So that. By the time Claude's done like, I still effectively get more things done because I have all that other. Non coding stuff out of the way. But it's. Easier to. Kind of context switch off of that into code. Back and forth. Than like 10 different. Things coding at once.

[00:06:55,677] Leo Walker: Yeah, yeah. I think using it for research and I'm not sure if you have like markdown documents that it's updating or where exactly that you're. You know, having code update and then having, you know, some other kind of workflow update. But I think that's a great use case. All right, anyone else before we move on to the next one? This was a kind of hard 1 so.

[00:07:19,868] Justin Kellam: Yeah. Can you guys hear me all right?

[00:07:22,056] Leo Walker: Yeah.

[00:07:23,711] Justin Kellam: Yeah, I'm just gonna say I I've kind of run to the same thing with like not being able to run. More than two or three agents at the same time, but then. Just the last couple days. I mean, the last week once I've started playing around with uh. The newest clod focus model 4.6. I decided to try to like. Have it manage multiple things for me so I was still only interacting with one. And uh. Granted all the things that I had it. Manage. We're in the same repo so that. It would might be different if you were trying to have it do like 5 projects but. Like really having a really good research and planning session beforehand to say like. Here's all the things I'm trying to do. Let's break it up into chunks. And then some of these are parallel, some of these aren't. But then at the end, I just still said like, I only want to interact with you, this one Opus agent. And you can spin up as many teams or sub agents in the background and each one of those can have work trees if needed. And like just report back to me on the plan. And then? That worked actually pretty well the first time I tried it. So I feel like it'd be interesting to try something more like that. Where? Because I just I agree with you guys that like. Once you're managing more than two or three, it's like, I can't even like, remember what? I'm doing here anymore but. If you just have one. One agent managing all those in the background. I I tried something like that before and I didn't think that the other models were really able to keep up, but it seemed like to me 4.6 Opus 4.6 was able to so. Some success with that.

[00:08:47,676] Leo Walker: Yeah. Things highlight there. Opus's Fire. For sure. And then yes, we're going to hit on sub agents and planning in other rules. So if people want to chime in on that at those rules as well to help harden Justin's idea there, that's that's fantastic.

[00:09:06,343] Justin Kellam: But then also to give like a little more context. So then at the end of that. Basically the output was. It delivered to me. Five different Pris that we're doing. Totally different features. And I just had to review the five PRS myself just to kind of see what was going on. But they did all that.

[00:09:22,696] Rahul Parundekar: Yeah, but sometimes like. Sometimes I think the. Agent starts going in a local minima and then it starts running with it. And that's why I want to pay attention to what it is doing, because otherwise it's just stuck. And it's something completely incorrect.

[00:09:39,417] Leo Walker: Yeah. Yeah. So that's that's a great segue into the next one. Start complex tasks in plan mode. Huge that you have planned mode here and then you know. Depending on how you structure the plan that different tasks could be done by different agents or so. At least that's how I handle it in cursor. And that. In Claude, I think you could do that the same way, send off to do exactly what you're just talking about, Justin. It's like, hey, like. I have this one person that maintains this plan. They will be the orchestrator of what sub agents do the different parts. And even when it comes down to the definition of done and the reviewing of the definition of done, that you could have other sub agents review that stuff. So I'm huge fan of plan mode. Anyone want to chime in about plan mode?

[00:10:40,821] Demetrios Brinkmann: You go first.

[00:10:43,913] Leo Walker: OK, Brian.

[00:10:44,115] Burhan Qaddoumi: Yeah, I was just. I'll just say, uh. Plan mode has been pretty.

[00:10:47,681] Demetrios Brinkmann: Run.

[00:10:49,459] Burhan Qaddoumi: Pretty much where I spend most of my time, honestly. With with agents that I'm working on, code is I spend. More time there. Just refining or iterating? The feature of the task the. Whatever needs to be done and. You know, usually by the end of that. I can kind of set it off and let it do its thing. Come back and and. Don't have? Too much of a mess to clean up. Umm, it is tricky I think sometimes keeping. Things aligned after the plan is. Really flushed out sometimes. Gotta break it apart into separate documents, but yeah the the that helps. Quite a bit. Umm. And then I also have started to. During the planning process. Try to separate. You know, work with a planning agent to separate out. What parts can be done in parallel? To be able to launch separate. You know, separate agents to do. Those tasks. Simultaneously instead of sequentially.

[00:12:02,540] Demetrios Brinkmann: I love that. Dude that's so good I didn't even think about that. I I just wanted to chime in and say. I found this skill. Brainstorming skill and it. Has made my plan mode. So much better. It just like. Basically clarifies the shit out of your plan mode. And it really is rigorous on the follow up questions that it asks. And. So I would encourage folks to try it. Let me know if like. It is as good as I think it is.

[00:12:42,986] Leo Walker: Yeah, yeah. Big, big things there of plan mode. How do you scope out how big that plan is? Umm, to be able to manage it into future manageable feature requests that you could review. And I like what you said of having multiple agents when I described my plan. Of laying it out. I'm like, hey. Tell me how many agents are running and tell me which ones are running what task in what phase. So essentially each phase it will say like which agents are running what tasks and so that helps to decide it in parallel and for you to like understand. Who's doing what during like? You know, quote UN quote phase of the plan is what I found useful. Got another minute or so. Anyone else for plan mode?

[00:13:28,188] Rahul Parundekar: So I had a question about plan mode which is when I put a skill. And in the skill. So I usually use skills to capture workflows which is like. Start from the pedantic model. Then build the business logic, then build the route, then use uh. Open API schema to create the types in the front end. So it's like an end to end flow right? But. Even if the skill says switch to plan mode, it doesn't switch to plan mode. Is has anybody uh. Seeing if that can be done at all like. Does does the agent follow instructions and skills to switch to plan motor? Do you start with a plan mode? How about the brainstorming skill Demetrius? Do you start with the plan 1?

[00:14:11,533] Demetrios Brinkmann: I yeah, I've only seen it switch out of plan mode. I've never seen it switch into plan mode.

[00:14:16,969] Leo Walker: So cursor. Cursor can switch into plan mode. Like if I'm even just chatting with it and I'm talking about a plan, it'll ask me to switch to plan mode. I haven't experienced that with Claude yet.

[00:14:27,899] Rahul Parundekar: Yeah, yeah. Because like all my skills say, switch to plan mode, but it doesn't do that. So then I'm kind of stuck. But it's fine. It's just 111 tab away, right? One shift tab away.

[00:14:37,666] Leo Walker: Absolutely. All right, let me start with the next one. Invest in your clawed markdown. This is uh. Pretty big, you know, overall, I guess you could have it a couple of different ways here for your memory. For cursor I have like probably at least 5 or 10 different rules and you could, you know, have them. Come in. Based on. On like. What kind of files you're working on or so? I'm not sure if Claude's exactly the same way, but I think this Claude markdown. For references was. A game changer. As Cloud Code and these other coding agents have come up. So anyone? Want to talk about their favorite things to? Put into the cloud MD or how successful it is like. Here they have 76 tokens and 4K tokens which is pretty realistic. I'm not sure if anyone has bigger or smaller. Files like that. See. This is also one other thing to highlight here that was really interesting was that. He talks about constantly updating your cloud dot markdown. And when I started working with coding agents with other people in the same repo. We initially had different. Claude and cursor rules. We'd share some of them, but like. Depending on what kind of MCP tools we're using and what. Our ownership of the project was that we were kind of having our own and that means that we're kind of keeping it locally. And Boris here talks about how, hey, after every correction, like, hey, you know, you didn't ask for plan mode or something like that, update that cloud, that markdown and see if you could. If you could change that because Claude should basically every time that it makes an error for the skill that you made or you know, something that you're doing, like you use the old library rather than new one or you're like, hey, I want to use Anthropic and it's like, yeah, guess what, you get 3.5 sonnet. I'm like, bro, that is so outdated. Stop doing that. Like you could put what kind of. Like agents you want in there so it doesn't, you know, default to your GPT 4 O and people know you vibe coded that.

[00:17:04,182] Rahul Parundekar: Umm, there is a comment by Tristan in the chat which says.

[00:17:07,171] Leo Walker: Yeah.

[00:17:10,552] Rahul Parundekar: Uh, how long should the cloud code be? Etcetera. So. What should we keep our? Or remove the subfolder cloud dot MD files. Any question? Do you want to give some more context to that?

[00:17:28,247] Tristan E: Yeah, sure. It's yeah, we, I mean. Some of our larger projects we just have. Lot of context to give. And you know, when I saw the video, they're like, keep it as short as possible. And I'm like, yeah, but if. You know if we need to help. Give it context to reduce errors. Then we have to have it long, so I think we're still figuring out what. What is the most essential information it needs and and I think we don't have a good sense of. How to determine that yet?

[00:17:54,477] Leo Walker: Yeah, so I. I think like on a high level, I think the Claude Markdown and the rules is really helpful for like organizational rules and whatnot.

[00:17:56,686] Rahul Parundekar: Yeah.

[00:18:03,619] Leo Walker: And like how you go about completing things, I think the skills one works because. The the skills essentially has a short description and if it needs to read more about that skill then it can open that skill and then it will blow up its its context window. So like if you have 10 skills each description is just 200 tokens. But every skill is probably itself over 5000 tokens. With like detailed description of how to do that skill is that it could just expand that and I think that's a good way for context management. But like I said, I think cursor has. In that description you could say like. Always read this rule whenever you're working with like front end UI components or when you're working with, you know, databases and that helps to manage that. So I'm not sure if a cloud. Has anything helpful there if anyone? Has experienced something like that.

[00:19:02,177] Rahul Parundekar: So one of the things that I've faced challenge with with the advice in the tweet, which was reuse like ask. Cloud to update the cloud at MD I I do it with skills all the time, but then there's a drift of instructions, right? So every few days I have to go back and just make sure all the instructions. Uh, correct? So I think like that's my biggest concern about updating these files with, with with agents. But to your point, yeah, skills is the best probably idea to. Cram as much context as we can. I also looked into like. There's some repos that show what is the internal prompts of code code. Because we don't have access to the Cloud Code internal prompts, but they have structured the prompts very small. It's like maximum 10 lines or something, 10 paragraphs. So it's it's really, really small. So I agree with Tristan that like the advice is to keep it small, but. You need more context to. Have it follow instructions.

[00:20:03,249] Addison Klinke: Do some people see a strategy where? You're the MD itself is small, but maybe the documentation kind of dispersed throughout the code is more. Substantial that way. If Claude is good enough to. Search around and know what area it's looking in. Then it will just kind of. Or what it needs versus being overloaded for every task.

[00:20:28,358] Leo Walker: Yeah, I I think that's a. Find a great last point to make for this one. Is like. People, some people argue that you know, RAG or semantic similarity searches is dead because you could just give them like grep and like file search. So that would be really cool that within your. Claude MD or something like that. You're like hey, for these situations, open this file. For these situations, open this file and it could automatically know to like grab. You know, essentially like. That's essentially like making your own skill. Uh, is that you're just like putting that in there so. That's a great idea.

[00:21:08,034] Rahul Parundekar: But I I but I don't think like Claude is. Progressively. Learning or reading skills like only parts of the skill. It does the entire skill at once.

[00:21:18,345] Leo Walker: Right. But what I'm saying is that in the in the markdown, you could say, hey, for these scenarios, open this file and if you're ever talking with it and it runs into that scenario, it will automatically go and and read that file. So it's essentially like a skill that you're building. Not in a skill pattern, yes.

[00:21:37,149] Rahul Parundekar: Now a link to the cloud. Skills writing guide and it does say progressive disclosure. So then. Does that way of like even keeping the skills MD? Very, very organized.

[00:21:48,183] Leo Walker: Yeah, I mean. Perfect segue into skills, create custom skills and commit to git. This is what I was saying is that me and him weren't. Committing it and sharing and making sure that we're. Iterating together, but we're just iterating locally. And I think, uh. This is fantastic. Especially. Yeah, rules and skills to share with each other for sure. And I know that like Claude allows you to do organizational skills or like your own skills, which. I gave. I basically created a couple of skills that are. PMS are able to create tickets and search through the GitHub. Uh repo. To help like find bugs or identify the sources of bugs so they could fill out the tickets better. And Claude does that for them. So it's like very. Well-done ticketing. And that's skills that I share with the organization. So anyone else find any skills? I know Demetrios just shared his his brainstorming skill, but any other fire skills?

[00:23:07,519] Demetrios Brinkmann: Claude Ception, Anybody play with that?

[00:23:12,044] Rahul Parundekar: What is that, Demeter?

[00:23:12,646] Leo Walker: I haven't more.

[00:23:12,836] Demetrios Brinkmann: You know what that one is?

[00:23:14,816] Leo Walker: No.

[00:23:15,473] Demetrios Brinkmann: No, nobody's heard of it. It's uh. Basically. After. Every. Loop or task that it completes. It will go back and say can I learn a skill from this? Like did anything I do in here? Is it able to create a skill from it and if it is it will create its own skill and then add it?

[00:23:42,868] Leo Walker: I I like that RL loop.

[00:23:45,197] Justin Kellam: Do you help define?

[00:23:45,579] Leo Walker: Like self enforced?

[00:23:47,224] Justin Kellam: Do you help it like define what the criteria is for? It finding a skill that's helpful or does it just? But to find that itself.

[00:23:54,382] Demetrios Brinkmann: Yeah, I haven't gone that. Deep down it I just. Uh, installed the skill and then every once in a while I'll be like. I'll watch what it's doing and it's like, alright, now let me go find if I can make any skills running Claude Ception. And it just does it. And so I'm like, wow, that's cool, but. I'm sure you can. Guide it a little bit more, it's called Claude Ception. I'll grab the link to. For it right now and drop it in the. Chat. There it is, there we go.

[00:24:22,879] Leo Walker: Yeah, yeah, this year's. So yeah, that that's the cool thing about these is like, yes, people are going to make repos with their skills, but it's really just a markdown file and maybe some other. Like maybe some other accompanying files like resources and templates. But it's so nice that you could just basically. People could essentially share their prompts. But that this is kind of like a scalable 1 so. Cool stuff, Demetrios, Any other? Skills that people love. I'll say that like working.

[00:25:02,619] Rahul Parundekar: I I sorry I I the one thing I did recently. It's not for all my projects but the new one that I started. Was the first skill I create is create skill? And maybe the. Conception gets rid of it, but create skill is a good skill to have because you can also do the organization of the. Skill when it gets created so. The best practice link I posted has like how do you create a progressive disclosure of skills? So that's one thing, and the second one that I've noticed is plugins. And I don't know if there will be a tip for plugins, but. There's a bunch of plugins there that. You can just use linear. And all of these through clouds. Plugin marketplace, I think that's. I'm I'm I just linked to that in the chat.

[00:25:52,226] Demetrios Brinkmann: Oh my God I forgot my favorite skill of all time is the playground skill. Have you all been using that? That is wild, the stuff that you can do so. I don't know if there's like show of hands or anything. Maybe thumbs up if anybody has used it. But. I will tell you how I'm using it because it's very open-ended. It gives you a little bit of visual. Representation of the code base in ways. And so. Later I'll I'll grab some. Examples that I've done but. It's really good for a few things, at least that I've seen. One is when you want like a slider. When you when you want to like. Design things and you don't want to use words. You need to be much more precise, so you need like a slider or you need buttons to click through things. And. Or you want colors you want like a color picker. So for maybe some front end design stuff. And then the other one that I've been using in a ton for is. When I. Can't figure out a bug. And where it's coming from and why it's happening. What I'll do is, I'll say, use the playground skill to map out the whole architecture of this. Of this repo. And. Help me find a bug. In it and so. The craziest part and I'll, I'll pull it up so that I can like show you a little bit more clearly, but the craziest part is when you click around and you. Say, what's happening on the different? Maybe it's a page and this button isn't rendering properly? It gives you the. Prompt right there. So that you can go and feed it back into Claude and then tell it to like fix this bug. So you just copy paste the prompt to have it get fixed.

[00:27:52,003] Addison Klinke: Do you find that that? Kind of. Rabbit holes in the in the wrong direction less often than LMS tend to do for debugging.

[00:28:01,906] Demetrios Brinkmann: Yeah. So what it what I would say is that it. Helps me. Get hyper specific about what the problem is. Because a lot of times I. I am not able to like I see the problem but the way that I explain it is that not how the agent then goes and executes on it and I'm like. It still is a fucking problem. Fucking fix it, you know, and so. What happens here is that. I will. Have the right words and the ways to explain it. Because it uses. Sometimes it'll use. Actual code snippets it says hey there's this problem in this area. So let me pull it up. I'll give a quick demo, but I'll also link it to just give me a SEC. It it might take a while so we can move on after I'm thinking about I got to go.

[00:29:09,028] Leo Walker: Yeah, yeah, absolutely. Well, the the segues into fix bugs by itself.

[00:29:10,385] Demetrios Brinkmann: Yeah, yeah.

[00:29:13,037] Leo Walker: For sure so. You could share this at the end of it as well. But essentially this is very interesting because this kind of overlaps with skills or you know, anything other like planning is like. How do you? Just like if you have a coworker or like someone working for you like a junior developer is like how do you tell them exactly what you want? Without being so. Exact that it pigeonholes them into a single solution. Right. Like you want to give them guardrails about like what your organization is about and like how you like to skill. Or in how you fix bugs and how you debug bugs, but you don't want to just be like so prescriptive that they can't use their own. Agency to go in a different direction and that's why I like here he's like, hey, just say go fix the failing CI tests. Like I think that's a little bit too broad. But also like, I don't want to be so specific that I give it like a really. Giant prompt just to do a small. Just to have it go look for small failing tests so. Could anyone find like there's rabbit, there's like a lot of other like? Debuggers. Obviously Cloud could do it internally. Anyone else like this whole clod fix bugs by itself?

[00:30:33,433] Demetrios Brinkmann: This is the bane of my existence so I would love to hear how others are doing this.

[00:30:40,588] Rahul Parundekar: Well, I, umm. I use pre commit. And also we have tests. Every time I so. I have three skills which I use a lot. 1 is. Planet where I give it a linear ticket ID and it plans out it it. It's like I switched to plan mode. Call Planet and then the ticket. Linear ticket and it just plans out the whole thing. Different points I've asked it to. Confirm with me what it does. Second one is to actually implement it and then it goes and implements it from the. Pedantic models all the way to the database. Routes generate the open API schema. Generate the front end things. Test out the front end with agent browser. And so it does the end to end and 3rd 1 is. Punch it wherein it will actually. Open. Do the pre commit tests? Then run the code. Use Playwright MCP to test all of this out and then. Run the CI test as well. So all of these tests it is running it and then fixing it as well. So almost like. If I have a very well organized linear. Backlog. I just go in one after the other and start moving things to to to produce. So that's the kind of way I've been using it to fix bugs.

[00:32:02,051] Leo Walker: Pretty solid. Anyone else? There's a lot of startups and companies targeting this. But I would say cloud within itself is good. I'm not sure if people like using smaller models like sonnet or something like that to debug quicker. Where if people just love. Opus and was like, hey. My my work is paying for the tokens. Anyways, let's let's stick with Opus here.

[00:32:33,304] Addison Klinke: I do sometimes go for smaller models, not only on debugging but just on a. Planning. Like an initial level where? It's really cumbersome to wait. You know, umm. Minutes or more. To try to have this back and forth like I'd rather have a really instantaneous, like I'm on Slack with somebody. And then maybe later I switch it.

[00:32:57,260] Leo Walker: Yeah, I think that's that's fire. I like the same way of like using sonnet and instead of Opus debugging all of it, maybe you just send out subagents. That look at different aspects from front end, back end, infrastructure, all that jazz. So good stuff there. Umm oh, level up the prompting here. So of all of the providers? I would say that Claude or Anthropic is only one that essentially had on their page like. Help you. Improve your prompts or go there with your prompt and they'll make it better. And you can use it. And I think that this tip in here of leveling up your prompting not only speaks to prompting when you're talking to it, but also your skills, your markdown, you know, everything like that. Maybe even like. Some people like putting. Solid docstrings at the top of every file so that when any agent reviews that file that you have good. You know, context at the top of it and also good. Doctrines in your functions too, right? For agents? So I think this is fantastic. Umm. Has anyone used anything to level up their prompting or like, you know, kind of like? Change it up. I know I use AI to help rewrite my emails and that's like prompting to people. So anyone like the promptings? Who? Agents here. I'll try to pull up the console to to show what I'm talking about until anyone, uh, hops on.

[00:34:48,656] Demetrios Brinkmann: I will say that I was just talking yesterday about. How I feel like? One of the things that really. The coding agent phenomenon take off is. How? You don't have to do as much crazy prompting as you did a year ago. Like if you think about. Think about how much. Fucking prompting. Two years ago when shit came out and you had all the different, you know, like tags or the system and user and that type of thing and none of that. We really have to worry about these days.

[00:35:26,967] Rahul Parundekar: Yeah. So there was some couple of tips the other day that. I, I saw, I forget. I I I'll try to see if I can find it, but it's like you no longer have to tell the agent. You must follow this step. Blah blah blah. I think that actually doesn't work because what happens is. The agent then tries to over correct itself and starts thrashing. So instead, you know, be more gentler, but say it is like it is important at this point to blah, blah, blah. So it's like you're saying the same thing but in a much more nicer way so that the agent still has some room of flexibility because otherwise the agent. Tries to overcorrect and get stuck, so there's. What Leo is showing. Is it has been a fantastic tool for the longest time. But. I think there are some newer tips which I don't know if they have integrated into this. Prompt improvement.

[00:36:16,153] Leo Walker: It's, but they even have the evaluate here, so you could you could have it evaluate it too. And like while system prompt and user is going to be different for this step through is that we have to remember is that system prompt and things like that are wrapped in special. Tokens that agents reference those differently. For like, you know? Not. What is that called? Like not getting hacked essentially not getting prompt? Prompt engineered right? Because anything that's wrapped in a user. Token is going to be handled differently than anything's wrapped in a in a system prompt token, that is. Engineered to the front of their. Call. But yeah. Yes. Prompting has definitely changed over the past two years of what exactly you need. How long your contact window is. Oh God from like 8K back in the day. Where? You can only do so much to 32 K felt. A lot. And then 64 felt like a lot and then 200K sat around for a year or two and now we're in the milli. So. You know. A lot of ways for you to spend a lot of money.

[00:37:26,064] Demetrios Brinkmann: Dude I also thi look at this like. Optimizing the prompt and the system and user and think. How many times? I probably could have had a better prompt. But then I just fire it off anyway 'cause I'm like, well let's see if it works. Just hit enter and. Kind of hang out or go do something else. And like trying to optimize. That. For every. Prompt. Would be so much extra work.

[00:37:58,996] Leo Walker: But if you if you just do small iterations on it, right? Like just like how if you hired an intern or you hired a new coworker. Every time that you give them a task, you might have to be more explicit. Where like talk about your standards both in the giving the instructions and in reviewing. But once you get enough repetitions with that coworker is that you guys want to be able to reach others minds and like. You know, use less and less words, and I think that's where memory is. Is having a big key here and other areas of stating you know where you are or let it know who you are and whatnot too. So there's a lot of cool things happening in the frameworks in in the scaffolding to help. Reduce that explanation and that level of verification, but I think until. Those mature. That there always be some level of prompting and even if like. When I talk to my wife like. We've been together for a long time. We know we could say very little words and know exactly what they mean, but we still need to. Level set every once in a while of what we understand each other is saying. And, and maybe even just go over what our new expectations are as we go through life. And I think that's the same way with all these agents as they form. We have to be able to level set with them on what we expect from them. And sometimes it's like, oh, I need to provide more or oh, shoot, maybe I was too, too prescriptive and didn't give you enough. Freedom. To do it your own way.

[00:39:28,456] Demetrios Brinkmann: I guess we're I'm not clear as like. When do we put it into the? Prompt versus when do we make it a rule versus when do we make it a skill?

[00:39:38,308] Leo Walker: It's, it's going to be like everything else in life. It's, it's, it's dependent on the situation that you're in and the organization you're in. You know. And like the team that you're working on. I feel like a development team in any of the large tech companies and the development team in any small company. And then a development team in India. Would use completely different. Rules or subsets it's like it's like deciding what language to use or what framework to use. Like it's so like met TC on what your. Current situation is with the company. And what's the pros and cons like there will never be A1 size fits all. Just like. Tip #7 terminal and environment setup. I don't like the terminal, that's why I use cursor. Like I'm, I'm trying to use cloud code more and you know, Gemini and the IDE and open AI with codecs. Everyone seems to love the terminal and I know that like true hardcore developers love the terminal. I love my ID. I I love being able to preview markdown to be able to copy and paste text in there. But there's something so good about the the. The terminal that you can't always get away from it so. Anyone got? Best use cases or all their vibes on on terminal environment set up here. I will say that the coloring here. His fantastic to be able to go get across. That you know, changing the usage or like how errors show or anything like that could be absolutely helpful for readable cause. That's one of the reasons why I don't. Like working in cloud code in terminal as much as that. It's harder to. To break it apart. Umm, but happy to hear any other thoughts. If not a realizer, we went over on some of the other ones so we could always make up time and go across.

[00:41:47,136] Justin Kellam: Yeah, I've I've just been using like the alacrity terminal. I like it. But then sometimes I just use the Claude app or. In my VS Code environment I just pulled up on the side.

[00:41:56,945] Leo Walker: Alacrity.

[00:41:57,626] Justin Kellam: Kind of just depends on like you said, if I want to see a markdown file. I prefer the IDE as well, but. Umm I I found like some custom scripts that ran for alacrity that kind of gives you like a cool status. Code thing in the bottom so you can like see more about your current session, like what branch you're in and how many tokens you've used. Things like that that I feel like makes the terminal a little bit easier to use, but.

[00:42:20,299] Leo Walker: Can can you put that in the chat? Are the products and everyone else like?

[00:42:24,469] Justin Kellam: Gaster.

[00:42:25,839] Leo Walker: I I heard. Another co-worker talked about a terminal that he was using it that I've never heard of and he absolutely loves it. So if anyone's using a certain terminal to help with cloud code. And is not just using it in terminal and cursor like me. I'd be happy to hear what. People are using.

[00:42:44,588] Rahul Parundekar: I mean, to be honest, like isn't. Cloud code itself like a terminal. Like. I I just write, even if I have to get commit, I'll just. If I have to like get pull main, I'll just write it in Claude. It'll be slower, but I just. Use cloud as the terminal.

[00:43:00,038] Leo Walker: Because.

[00:43:01,490] Rahul Parundekar: The cloud code as the terminal in. Cloud code in terminal as the terminal. Sorry. It's more specific.

[00:43:08,984] Leo Walker: Come on, someone out there has to love their. Terminal setup. Enough to fight R Raul on this. No one.

[00:43:22,957] Burhan Qaddoumi: I won't fight, but I'll I'll mention that I, I am.

[00:43:23,605] Leo Walker: You're right.

[00:43:24,584] Demetrios Brinkmann: Yeah, I.

[00:43:25,456] Leo Walker: Yeah.

[00:43:26,655] Burhan Qaddoumi: Starting to dabble more in the terminal? I've I too am more, have been more. Focused on using BS code. Um, and kind of. Doing because it lets me. Do a little bit more while an agent is running. Doing something else I can I can be reading something else or. Or looking through other files while it's. Chugging along and so. Yeah, I have been trying some. Board terminals, umm. And yeah, but yeah, as far as optimization or set up there, I don't have much else. To add. But yeah I'm I'm trying to. Trying it out, I'm not. Not crazy about it yet.

[00:44:13,659] Demetrios Brinkmann: The thing I do like about using Claude in the terminal or Claude code is when they give you the little tips.

[00:44:14,374] Leo Walker: Hmm, fire. That is nice. We're kind of going full circle kind of back here. I think this was kind of going back towards Justin's. Comment earlier of like hey. Keep your main agent context window clean here by kicking off. You know sub agents. To go do stuff like reviews or building certain stuff. And yeah, that you could route permissions. Through to it for different hooks, so yeah. Doing a pull request or you know multiple different reviewers every time that you need to kick off like a. Slash review or back slash review in there is helpful. Anyone have any favorite sub agents or anything like that? I will be honest, I'm probably. More of a prompter and I have to like talk for 30 seconds every time that I want it to do a in depth review rather than creating a sub agent. So this is something that's on my. Do list To Do List before the next meeting is to utilize sub agents more.

[00:45:24,228] Rahul Parundekar: Let's move. Sometimes I ask it to create sub agents. So I asked Claude like, oh, I want you to do this, but because I know that it is a parallel task of multiple places. I'll just say create sub agents to do this and then execute the task and so it takes care of parallelizing it for me.

[00:45:43,872] Burhan Qaddoumi: Yeah, yeah, I do the same. I've been doing the same in VS Code. I remember the other day. I was working on. Putting together some skills for repository. And uh. I prompted prompted uh. Opus, I think to. To use subagents. To read all the files. Get summaries from the files or find relevant information and it launched 80 something. Sub agents to go through and read all the files. Because there were a lot there already. And yeah, it was. It was insane watching all of them just spawn.

[00:46:23,635] Leo Walker: That's a great way for them to do a token grab. For sure.

[00:46:29,983] Justin Kellam: Yeah, I think someone else linked the superpowers. Umm. Git plugin earlier and I've just been using that one a lot and. Since I installed that, I don't feel like I need to prompt it about sub agents anymore. It'll often. You know when to do it himself. Or sometimes it'll say. Like, here's a couple different ways we could approach this task. Which do you want to do? Either I'll create a bunch of sub agents or. You could like start this other window and do it this way or I'll make a team like there's like the Claude can make like a team of agents now, so. I'll sometimes choose the best one for this situation that I am in, but. I don't really feel like I need to tell it. Make sure you have this tool on your tool bag. It just knows when it needs to do that on bigger stuff.

[00:47:21,756] Leo Walker: Pacquiao. Umm cool cool. Anyone else for sub agents? I realize that we're running short on time here. Cloud for data analytics. I haven't used Cloud Code for this much. But. Clogged like chat, like the. Chat interface that could create artifacts for you. Has been fantastic for this that I give it MCP access to my board and to my, you know. Files that way and it creating like some kind of either a static HTML. Or using Python to generate like. You know. PNGS of graphs has been super helpful.

[00:48:01,086] Burhan Qaddoumi: Yeah, I've I've definitely done this as well. I actually made this. A part of a project I was working on, one of the workflow steps was to call it Agent, give it the code tool. And and just AA ton of data as a. Give me. You know, averages, moving averages. Or trends, you know, month-to-moth, year-to-year, quarter to quarter? Kind of analytics. Yeah, definitely, definitely put this to use.

[00:48:29,868] Addison Klinke: Tristan. Tristan, have you had any? Further developments on the Datadog profiling. Kind of stuff you were doing. The other week.

[00:48:39,806] Tristan E: Yeah, I've, I've loved the Datadog MCP a lot. Umm. It is helped. Mostly though, in analysis it can go through the code and see what. Metrics were. Sending the datadog and then go and line them as part of you know. Deciding on how to. Complete a task. I havent used it for the profiling as much. I hooked it up to our go profiler so it can profile. You know as it needs to help make decisions as well. But the Datadog MCP is in grades. Also do analysis, produce notebooks and dashboards and things like that which I've loved.

[00:49:21,310] Leo Walker: OK, guys, that's awesome.

[00:49:25,057] Demetrios Brinkmann: Yes, I've got this demo up if you guys wanna see it now.

[00:49:29,398] Leo Walker: Send it.

[00:49:30,195] Demetrios Brinkmann: And let's not keep going with the data. And analytics I will say on the data and analytics 1. Open AI put out a good blog post recently. About. How they set up their. Data Analytics or Data Analysis agent. I'll find it for you all if you want to check it out, but. Uh, for now. Let me show you. This is all right. Let me start with I'm making Horsey Ranch game with my daughter. And so this is what I was talking about where. It's like oh if you want different. Kind of like. I could say blue or more blue or whatever, but if there's a color picker, it's going to be a lot easier. Right. And then it can give you different things and so I have these different. Uh, people and I can have sliders that's. Where I and. Then when I want to implement it, it's just boom, copy prompt and bring it back. But then I was having problems with like this calendar UI. And so there's this card that was coming up. But I wanted to be able to just like see what would the playground. Give me. If I say use the playground skill to help me edit the calendar. Card as it pops up. And so then I can change like the border radius or I can there's like. It comes with already. Set options so. That's pretty cool, but then I can tweak it however I want. So that is a. That's like. That's awesome. And then I started going into what I was talking about with like the the debugging and I was having a problem with well, maybe I'll start with this one. I was trying to create like this assistant. Right, just like a simple chat assistant that could MCP into different. Tools and I was having problems and so then this is where I got to really. Dive into OK. On this part. There's this file. All right, So what does that mean? But if I look at. Only these areas then I can see. Here's how the data is flowing. Oh, all right, so then if the problem is here. Then I get a little bit more. Explanation about what's going on and then when I was like alright, let's debug. Because this was more or less like. Architecture, but then when I wanted to debug. Just by me saying hey help me debug this. It gave me 3 things that were potentially wrong and so. What did I do? I was like, alright, cool. There we go. This is. These are all problems. And then you just copy the prompt and this is. What I what I meant by? The prompt is way better. Is that I would not. Give that prompt, I don't think. You know, if it's like, hey, there's this problem or there's no tooling. I'm not giving those prompts. So that's the playground skill. You all enjoyed it. Leo, I hear you type in furiously. I imagine it's.

[00:52:37,388] Rahul Parundekar: Who is a furiously typing.

[00:52:39,849] Demetrios Brinkmann: Notes. It's notes about the playground skill. Note to self use playground skill

[00:52:42,455] Leo Walker: Yeah, right. It's it's interesting like how you like people say like a picture

[00:52:42,709] Demetrios Brinkmann: more often.

[00:52:46,721] Leo Walker: is worth 1000 words, it's worth at least 1000 tokens for sure. And how you could have that and be able to switch. Back and forth between what's more effective, like if I just screenshot this and like circle it? Or do I use another LLM to turn it into a prompt and like maybe that could describe it better like. Different versions of charades and whatnot, but. It's interesting seeing the different tools coming up. So the lab.

[00:53:18,102] Rahul Parundekar: Umm, how many skills? How, how many? How many tips do we still have remaining?

[00:53:21,843] Leo Walker: It was it was just that and learning with Claude. So that was just like having it, you know, chat with it and doing HTML so. I'm assuming everyone's been doing that. I feel like that's the OG reason for. LLMS and chatbots, So we don't necessarily have to go over that, but we have a couple more minutes if anyone would like to or if there's anything either of you would like to cover the last minutes.

[00:53:46,788] Rahul Parundekar: No, so I I just last thing I wanted to say was again this is like a weekly or bi weekly series that we are doing. I think we are doing it weekly since.

[00:53:55,377] Leo Walker: And we'll try to shoot for next Friday for sure.

[00:53:56,814] Rahul Parundekar: Yeah. And since we have a good turn out today, wanted to give like. Housekeeping, uh. Opportunity to people like. Use the chat to propose what you would like to learn. What you want to see? For the next 5 minutes, let's discuss that so that we can plan the next one much more effectively with other people. If somebody wants to demo something, I know last time we talked about show and tell. Being one of those things, umm. We wanted to do it this week, but because we didn't announce it. Um, earlier enough we didn't have the opportunity for people to volunteer. I think next time if anybody wants to like. Sign up for a demo. 5 minutes, really crisp and only about the skill or only about the learning part. We don't want to see product demos. We don't want to see pitches about startups. We just want to see like how everybody's learning what they're learning. So. Use the chat to kind of talk about what you would like to see. In the meantime, Demetrius, I have a question for you. Is the recording, uh, that we're doing also includes the chat? At the forfeit, like does it save the chat as well 'cause there's a lot of things inside the chat which are very helpful.

[00:55:06,723] Demetrios Brinkmann: Yeah, good question. I'll figure that out. I think I can get it. I'll find it. I'll try and find it.

[00:55:12,478] Rahul Parundekar: OK, because otherwise we're just. I'm just copy pasting all of this and giving it to Claude to summarize.

[00:55:18,191] Demetrios Brinkmann: Nice do that.

[00:55:18,732] Rahul Parundekar: And gradually doesn't have AI yet, right?

[00:55:22,030] Demetrios Brinkmann: No, only company. That has not.

[00:55:27,255] Rahul Parundekar: Alright, oh cool, we have some good ideas. Starting work with coding agents. Umm, how should team development culture adapt? That's a very nice one, so I think. That would be a good topic from like an engineering team perspective.

[00:55:44,436] Demetrios Brinkmann: Yeah, just that's so funny.

[00:55:44,737] Rahul Parundekar: Uh, memory is created.

[00:55:46,880] Demetrios Brinkmann: As as you were talking about that Leo about before of like, oh, do we use a prompt or a skill or a rule or whatever. That's kind of going to have to be decided by the teams. Individually And so how that adapts, I would love to like just jam on that for a little bit. Little more esoteric in a way, but.

[00:56:04,776] Leo Walker: Yeah. Yeah, absolutely. I mean every team's coding standards for what they review and their, you know. Cadence and everything is is going to be different. So I feel like the prompting and all that stuff stuff would be the way. Umm, and how much do you do you lean on it versus not? So yeah.

[00:56:31,417] Rahul Parundekar: Should we, should we do that? Then next week, earlier we can do. How do you work together as a team with skills and cloud code and all that stuff?

[00:56:40,113] Leo Walker: Yeah, yeah, for sure. Well, we'll default to that. Also in the coding agents um. Slack Channel. Go ahead and and. If you guys want to see anything there. Just like tag us, any one of us. For that, and we'll definitely look at it and maybe even put up a poll. For it or just be able to like review that as option for the next one. I know that cursor. Also has essentially their best practices, so I'll probably have that on the docket. In Case No one else comes up with anything, but really excited to hear anyone else's thoughts and we already have at least a handful of them here, so. Thank you everyone.

[00:57:26,528] Justin Kellam: Demetrius, did you already linked that playground skill? Was that like a plugin or? How did you get to that?

[00:57:33,179] Demetrios Brinkmann: Yeah, I threw the announcement in there and I remember finding it through that announcement. Uh, find it again. It's this Twitter link or X link. I'll share it again though. Before we. Log off. So click on it. Thanks, Leo. Thanks for doing this, dude. And uh. Yeah, also drop it in the coding agents. Slack Channel. No, we're getting kicked off. Alright.

[00:58:05,202] Rahul Parundekar: Goodnight, sweetness.

[00:58:05,517] Demetrios Brinkmann: I'll see you all, thanks for this.

[00:58:05,988] Tristan E: Thank you.

[00:58:07,678] Demetrios Brinkmann: Good stuff.

