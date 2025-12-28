# Lando's Lengthy Loom Lecture

So you want to use Prolix's wonderful Lucid Loom preset? There are a lot of toggles and options and a lot of models to use them with, and it might look daunting, but it's actually pretty easy with some guidance! 

Table of Contents:

About LLMs and Picking a model
About Sillytavern and setting it up
Downloading and Importing Lucid Loom
Lucid Loom's Structure and Categories
Configuring Reasoning to Work for Loom in Sillytavern
Best practices and recommended settings for each model

## What do I need to use Lucid Loom? First, pick a Model

### About LLM's

An LLM (Large Language Model) is the AI that powers the roleplay. There are a multitude of ones to choose from and a few favorites.

As for which one to use, there are a few favorites among the people in Loom chat (the discord channel that's the home of Loom). I'll talk about the two types of models and then give you the most common recommendations.

First you have to decide if you want to host your own model or remote connect to a separate one.

Lucid Loom is highly complex and **local models small enough to be able to run on your PC tend to be UNABLE to handle it.** For example, my go-to in the olden days, a 12B (12 billion parameter, that is the size of the model and how "smart" it is) model called Mistral Nemo, can NOT handle Loom properly. If you are set on local hosting, I'd recommend 70B or higher *at the minimum*.

So nearly every member instead remote connects to a remotely hosted model.

Before I go into the types there is one last thing to mention, quantizations. Quantizations (or quants) are a way to *make models smaller and less resource hungry* by making them dumber. To use a food analogy, imagine how a lunch portion is smaller and cheaper than the equivalent dinner portion of the exact same meal at a restaurant. I can, to use a local model example from earlier, run a 12B model in a quant called K4, which makes it half the size in exchange for about a "fourth" of its smarts, a stellar tradeoff. 

*When you remote connect to models, it's useful to have an idea of the quant of the model you are connecting to (FP8 is usually the standard for third party hosting), because the same model could perform wildly different depending on the quant.* I'll elaborate on this more later, but it's a potential cause for why the same model can perform different on different providers, or why a certain model can be smart one day, and moronic the next.

Now, onto the two types of models: 

#### Frontier Models

Frontier models, which are ONLY hosted by the company itself and include things you might have heard of like Claude's Sonnet and Opus, Google's Gemini, OpenAI's ChatGPT, and XAI's Grok. 

Some Pros and Cons 

The big Pro is that frontier models are the "state of the art". They receive daily stealth updates to keep them on the cutting edge, some boast parameter counts in the *trillions*, and they are connected to vast databases called RAGs (retrieval augmentated generation) to help them with looking up information. They also might have searching capabilities built right in. Plus they usually require less work out of the box to get working as they are meant for a mass audience.

Now for the Cons:
These models are hosted on the server of the company and they mass collect information on usage and actively use it to train their models. *So do not have an expectation of any privacy when direct connecting to these models.* 

Additionally, information on these models are not released, we don't know how many parameters they have, when they are updated (most of these models are tweaked daily with no changelogs or notice), and they can be dumbed down for various reasons (safety (meaning countering nsfw), other models need more compute, testing various updates) without warning.

So yeah, it's a tradeoff between performance and ease vs privacy and control.

There is another big downside, *cost*. Most frontier models cost more than the next category of model and tend to be "pay per token". Think of tokens as how much data is sent and received, 1 token is approximately 4 characters for English text. Tokens tend to be priced per million.

Now let's look at the alternative.

#### Open Weight Models

Open weight models are released by the companies and let loose onto the internet as *files you can download and run on your own hardware.* These include aforementioned local models, although the larger open weight models are too resource hungry (especially ram) to run on local PC's, tending to be run by third party server providers.

These tend to have different pros and cons compared to frontier models.

Pros:
The first major pro is VERSION CONTROL because the model file is RELEASED onto the internet. Think of it like a book edition, it's released and you get the book and you have it in your hands. The book won't magically rewrite itself. Frontier models are kept by the companies that own it and are updated all the time, as if someone else is reading the book to you from far away and they can change the details without warning. GLM 4.7 (a recently released open weight model as of December 27, 2025) is GLM 4.7. It won't change, it won't be altered, and even if GLM 4.8 comes out, GLM 4.7 will still be on the internet forever. Meanwhile, a frontier like Gemini can be lobotomized one day and you won't know when or why it happened, or an older version you like can be taken offline and you have no recourse.

The second major pro is privacy. Since it can be run outside of the main company's server, you can theoretically find a hoster that will not collect your information. *You should always assume information you send out will be accessible by the hoster anyways.* But unlike companies like Google, which have huge infrastructure ready to collect and sift through data. Third party providers might host a huge variety of models, all of which collect information in different ways. They don't have the time or compute usually to sift through all that data in an efficient way. So a lot of them don't. HOWEVER, they all CAN, so to be safe, pretend they will.

The third pro is COST. A lot of open weight models are smaller and easier to run, plus they don't have massive amounts of infrastructure and RAGs tied to them. So you can find them for pay per month subscriptions instead of pay-per-token like frontier models (I'll shill my favorite later). This is much cheaper by order of magnitudes than models on Claude or Google.

Cons:
Smaller parameters and no huge RAG infrastructure means the models are less "smart" than frontier models in general. However the biggest and most advanced open weight models (Deepseek, GLM) can punch well above their weight class. To the point where I have access to both unlimited Gemini and unlimited GLM and I prefer GLM and it seems *smarter* to me for roleplay. 

Slower releases: Since the models aren't updated on the daily without warning like front


### Frontier Model Recommendations

First up, frontier model recommendations. Remember the name of the game here: convenient, very fast, smart, no privacy, no control over updates, and expensive.

#### Google Gemini 3 Pro and 3 Flash

Google's Gemini is the most commonly used frontier model by the regulars of Lucid Loom. There are two versions, Gemini 3 Pro, and Gemini 3 Flash. The former is estimated to be a trillion parameters, but as a frontier model, Google does not release information about it. It's pretty smart, although recently (about December 22) it got a huge hit to smarts and nobody is sure why (a day after the release of the smaller model, maybe google moved limited compute over to flash).

3 Pro can handle roleplay very well, struggles with logic sometimes, and generally has a positivity bias (It'll agree with you too much, color the story more positive, Loom can naturally mitigate this with it's many "darker" toggles). It is censored and requires a jailbreak (Loom as a preset is enough of a jailbreak).

3 Flash is Pro's smaller, lighter weight deranged little brother. It's made for general use, especially on phones, as it's Android's main AI assistant. It's got a darker color, is not as smart as 3 Pro (Although it appears to have more compute dedicated to it as of December 2025, so 3 pro isn't that much smarter), and is also censored, albeit the darker coloring lets you get away with more. Not that it matters, as Loom is enough of a jailbreak for 3 Flash as well.

Native reasoning is not used for Gemini with Loom, in favor of "fake reasoning" (I'll go into this later).

Gemini is usually used through a service called AI Studio, and like most frontier models, is "pay per token". There are free trials you can abuse and plenty of guides on the internet to do it.

There is a subscription too, but I don't know the limits of usage on it. Plenty of information out there about it.

#### Claude Sonnet and Opus

Claude is considered the state of the art for roleplay and coding at the moment. Claude has two models, Opus 4.5 and Sonnet 4.5. Sonnet is smaller and equivalent to Gemini 3 Flash from earlier, Opus 4.5 is newer, larger, and comparable to 3 pro. However Sonnet is MUCH smarter than 3 flash and Opus is MUCH smarter than 3 pro.

Sonnet was originally trained up for creative pursuits, and as such is very lauded for roleplaying in particular. It struggles with logic and things like formatting. It also tends to be very token heavy, overthinking everything.

Opus 4.5 is their brand new model. It is smarter than Sonnet, but some people say that hurts roleplay a bit. However those people have not tried the brand new effort parameter. Give it a try, medium effort is supposed to be similar to Sonnet.

The downside of both of these is that not only is Claude pay per token, it's the most expensive pay per token by far.

#### Grok or GPT

Some people use Grok, I never have.

Every GPT I ever used for roleplay has been dogwater, don't use it.


### Open Weight Model Recommendations

#### ZAI's GLM 4.7-thinking

**GLM is my model of choice**, my daily driver. ZAI has two models, GLM (the big one, 355B parameters) and GLM Air (little brother, 105B parameters). They release them in an alternating fashion. Currently the latest as of December 2025 is GLM 4.7, and it's a doozy.

GLM 4.7 is a reasoning model (we use the native reasoning for Lucid Loom, unlike Gemini, because the native reasoning is GOOD). It is 355B parameters, and regularly outsmarts 1 trillion parameter models like Gemini 3 Pro. I love it to death.  It's smart enough to handle complex formatting, html tags, keep track of stories very well. The downside is that it is slower than Gemini, because third party providers and even zai don't have as much compute as google or claude do. But it's so much cheaper as a result.

GLM 4.7 air... does not exist yet. The latest air is GLM 4.5 Air. GLM 4.6 skipped air and went straight to GLM 4.6V, a vision model (this means it can interpret pictures), which hurt the roleplay/text performance. I do not recommend using GLM 4.6V as a result.

So yeah, just use GLM 4.7. How can you use it though? Since it's an open weight model you have two options, from the manufacturer or third party.

The company that makes it is Z.AI and they have a subscription plan for it. You can get GLM straight from them, however, they have been doing prompt injection lately to "clean up" the nsfw of the model. If you want to use it for smut roleplay, I do NOT recommend zai, in fact, I don't recommend ZAI at all. As a source company for the model, they have the infrastructure in place to mass collect data and sort it easily.

I recommend NanoGPT, a third party provider, due to their 8 dollar a month practically unlimited subscription, I'll give more info on it later.

#### Deepseek's Deepseek

Deepseek is probably the most well known of the chinese model makers. They have Deepseek 3.2 speciale and Deepseek 3.2 thinking. Both are larger 685 billion parameter models, but the former has more "active" parameters than the latter. That means Speciale is their model comparable to Gemini 3 Pro, while 3.2 Thinking is the one comparable to Flash. As far as I know the former is still only available direct from deepseek, which means you need to deal with the privacy issues inherent to using any model straight from the manufacturer. The latter is available from third party providers readily.

#### Kimi K2 and Qwen

Kimi K2 Thinking is used by some people in the loomchat. It tends to be problematic and fight you, I don't recommmend it.

I don't know a single person who still uses Qwen, but people used to a lot.

#### Recommended Third Party Providers for Open Weight Models

My **personal** recommendation for using open weight models is through Nano-GPT. They have an 8 dollar subscription that lets you use 60,000 message requests per month, unlimited tokens on 80+ different open weight models. They do rotate providers as the tokens are used up on their end, so sometimes you'll have a slower provider, but you can't beat 8 bucks a month for practically unlimited requests (I've never even come close to 60k chat messages per month). The subscription includes 80+ open weight third party hosted text models with things like GLM 4.7, Deepseek 3.2-Thinking, Kimi K2, Qwen, a lot of local models (including the classic TheDrummer ones like Rocinante, Cydonia, etc.), four image models (Chroma, Hidream, Juggernaut XL (animagine based), and Qwen Edit), and lots of abliterated/derestricted/finetuned versions of popular models (TheDrummer's glm 4.5 air finetune called GLM Steam comes to mind).

You can find it by googling nanoGPT, or you can help me out by using my referral link below:

https://nano-gpt.com/invite/XFjmGJg8


Other Providers include Openrouter (no subscription, pay as you go), Featherless, Infermatic, ArliAI, and Chutes (Don't... just don't, chutes is awful).


## What else do I need to use Lucid Loom? Sillytavern

Loom is built with one use case in mind. **Loading it in Sillytavern.**

Sillytavern is a roleplay focused LLM frontend. It lets you import character cards from different sources, connect to an llm either on your pc or hosted remotely, and then chat with the LLM for roleplay, while sending information about the character, the lore, your user persona, and your chat history to said LLM.

A preset determines HOW this happens and in what order. It's basically a collection of system prompts in toggles that you can switch on or off. At least Chat Completion presets are.

You might have heard about Chat Completion and Text Completion. Text completion is a much older system for talking to an LLM and it's pretty static. Chat completion is a newer model and it relies on a series of toggles to build out a huge modular system prompt! **Lucid Loom is a chat completion preset, so it will only be usable in chat completion mode!**

Thankfully Sillytavern has a pretty robust chat completion implementation, if a bit lacking in the UI front (we can fix that with an extension which I'll show to you later in this guide)!

As for using Lucid Loom in a system other than Sillytavern, like Janitor or Kobold, Lucid Loom has Sillytavern specific scripting language and a pretty robust addon by the author himself to add custom features like more lumias and better history support, summarization, and expand the response modes in Loom itself.

**This means using it outside of Sillytavern will give mixed results at best as several core features require Sillytavern.** If you use it outside of Sillytavern and come asking for help, be ready to be told "use it in sillytavern". It is what it is.

Sillytavern has pretty robust documentation for getting it up and running.

Here are guides for installation on various operating systems including Android:

https://docs.sillytavern.app/installation/

I personally recommend running it on a desktop or laptop and then connecting to it from your phone via web browser, Sillytavern has built in support for connecting to it remotely. Sillytavern is a server, so it runs as a program and then you can visit it in the same pc's web browser, or from a remote client like a cell phone or another pc.

Information for remote connections can be found here:
https://docs.sillytavern.app/usage/remoteconnections/

It's pretty easy to connect to it from the same wifi network with some simple config file tweaks listed above in the documentation.

For remote connections, I use a program called Tailscale that lets you remote connect to your local network, but other IP tunneling solutions exist.

## Getting Lucid Loom

Lucid Loom can be downloaded from Prolix's site, Lucid Cards:

https://lucid.cards

Specifically from this page:

https://lucid.cards/chat-presets

I recommend getting the base file. The "Prolix Preferred" is the same file, but comes with his preferred roleplay toggles already turned on. His setup has all the nsfw toggles turned on, so I recommend starting with the normal base purple colored one to get a lay of the land first.

Once you download it, it'll be in a json format, you can import it into sillytavern via the import button. But first, you'll have to set up your sillytavern for chat completion mode and connect to your LLM!

## Connecting to your LLM

Sillytavern has a variety of api connection points you can use to connect to your model of choice. The important thing is that you choose Chat Completion in the dropdown for API, since Lucid Loom is a chat completion preset. It will not work in text completion mode.

## Importing Lucid Loom into Sillytavern

To import it, after picking Chat Completion open the left hand panel (leftmost icon on the top bar of sillytavern) and click the imnport button and select your json! This will cause the panel below to switch to Lucid Loom.

I'll go over the best options for Loom later, but first, let's scroll down in this panel 

## Getting the lay of the loom, the categories

Lucid Loom, like most presets, relies on a category system to make things less cluttered. It might seem overwhelming at first but you'll get used to it pretty quickly.

There is an extension to allow things to collapse into nice categories, I'll go over it later. First, the categories.

### Story Primers and Core Instructions

Important things like card, user persona, and scenario information are pulled in first thing in the "Story Primers" category (Loom does not use the default Sillytavern prompts for those, hence why those are still in but off later).

Then comes the core instructions and modes for the Loom, I'll go over these later.

### Lumia Definitions and Personalities

Then Lumia definitions (physical description) and personalities. Loom's main claim to fame is that it causes the AI to assume the role of a storyteller called Lumia. There are dozens of Lumias with different personalities available through an extension I'll talk about later by the same dev of Loom. For now, you get 7 personalities built in with a custom option to allow pulling in extra lumias from the extension.

One thing to keep in mind under personalities is "Weave Lock". This helps mitigate the personality from affecting the story too much.

### Various Story and Response related Categories

Then the rest of the toggles are all things that affect the generated story, like the point of view of the storyteller, genres, narrative styles, plot progression options, response length options, text formatting, prose guidelines, dialogue options, nsfw options, and story details.

### Utilities and Trackers

Utilities and Trackers are categories that have little useful utilities like OOC commentary, time lookups, summarization utilities, and the like. Trackers are various little trackers that help Lumia keep track of what has happened thus far in the story.

### Story Details

After that is Story Details, where the only important things are World History (Lorebooks) and the optional extension summarization toggle (I'll go over this later) which is off by default. **The reason this section is full of turned off toggles is because Loom does not use them. But if you delete them, Sillytavern breaks, so we leave them here and off.**

### Chat History

This is where Chat History lives, it's the best place for it from experimentation in the past.

### Planning Effort

This helps tell your LLM how much work to put into the reasoning phase.

### CoT Selections

These are the reasoning checklists for Loom. I'll explain them in more detail in the next section.

## Reasoning or non-Reasoning? CoT?

Lucid Loom is built with reasoning in mind. It works a lot better if you are using the reasoning capabilities of an LLM.

So what do we mean by reasoning. Well reasoning is using the first part of the response of an llm to "think through" or plan the response, and then it follows it with the final actual response.

In Sillytavern, the reasoning block should be hidden in a dedicated dropdown box. If it isn't, your reasoning settings are wrong. I will be going over how to set up reasoning settings later in the guide.

The important thing is that this reasoning block is NOT sent as part of chat history. So all the planning will not clutter up your context!

### CoTs? What are those?

CoTs, or Chain of Thoughts, are a kind of checklist to guide the reasoning process of an llm. There are various kinds in Loom.

**ONLY USE ONE COT AT A TIME. THIS IS IMPORTANT.**

You'll see that the Loom CoT sections are split up into three section.

### CoT Selections (System) - The Old and Small

First one is the CoT Selections (System) category. This one includes older and smaller checklists that aren't really the focus of Loom. They can be used if you desperately need to save on token usage.

### Cot Selections (Zipbomb) - The latest and greatest

Next up is the CoT  up are the Zipbombs. These are large, detailed checklists where Lumia thinks through her reasoning in character. This is where the lion's share of Loom's dev time for CoT goes to and the CoT type I will always recommend to people.

You'll find two major types of Zipbomb. CoT Zipbomb and Reasoner Zipbomb. The former includes language for \<think\> tags in the beginning and ending. These are useful for "fake reasoning" models like Gemini where you have to start the reply with a \<think\>.

The reasoner zipbomb are for models smart enough to handle the thinking block start and stop on their own, like GLM 4.7.

Additionally you'll see that there is a subtitle of (Lumiverse Sov). This is for using the Sovereign Hand built into Lumiverse extension instead of the more primitive one that comes in base Loom. I'll go over what Sovereign Hand is later.

### CoT Selections (Assistant) - Alternate sending roles and utilities

These CoT's in here allow you to send them as assistant instead of system, something you won't be doing very often. In addition there is a /think flag that is useful in here for GLM on platforms that aren't NanoGPT.

### That's a lot of Information

Yes it is, thankfully you don't have to remember most of it. It's mostly here for you to refer back to if you have any questions.

Now that you have a better idea of what Loom looks like. Let's get to installing it!

## Configuring Lucid Loom

Okay, now that you've imported Loom and I've gone over the structure, we can configure it for proper reasoning!

Thankfully there are only a few places we'll have to look to get reasoning up and running. I'll point out the locations and what they do first, and then we'll tackle how to set them up for each model afterwards.

### Prompt Post Processing

In the API Tab underneath where you select the model is a dropdown called Prompt Post Processing. This alters the raw prompt sent out to the LLM to better help it understand which things are from the system and which are from the user.

There are several options:
- None (no processing applied) 
- Merge Consecutive (Merge consecutive messages from the same role)
- Semi-Strict (Merges Roles and Allow one optional system message)
- Strict (Merge roles and Allow one optional system message and sends a user message first)
- Single User Message (Merges all messages from all roles into a single user message)

Additionally there is tools or no tools for each of these. Tool calling lets llms interact with external systems like programming apis, web searches, etc. These have to be set up on the LLM's side and you'll probably already know if you have them on. I'd recommend picking no tools by default if you don't know what this means.

### Advanced Formatting - Context Formatting and Reasoning Formatting

In the advanced formatting tab (The A up top to the right of the API icon), you'll find that most of it is grayed out since most of these options are for text completion. However we still have a few important sections here.

To the lower left are three checkboxes under the context formatting section. These are user preference except for Trim Incomplete Sentences, you'll want this one UNCHECKED, or it can break loom tags and formatting.


On the lower right is the Reasoning formatting section.

First are three checkmarks

Auto-Parse should always be on, it enables the below section to be able to capture text into a reasoning box if the tags are correct. This is the only way "fake reasoning", which is what we use for Gemini, Claude, and GPT, can work.

Auto-Expand expands the little thinking box containing the reasoning upon each new message, this is user preference.

Show Hidden shows the reasoning time for models with hidden reasoning, I recommend you leave this on.

Below that is a **Reasoning Formatting** dropdown you can expand. This is where you set the reasoning formats.

I recommend for pretty much everything that you pick Deepseek here. Gemini uses it, Claude uses it, GLM uses it, and of course Deepseek uses it. Both fake and native reasoning models will use deepseek formatting, and if they don't, there's no harm in leaving this on deepseek anyways.

The dropdown sets the next two boxes, Prefix and Suffix, which are what will open and close the reasoning block.

Prefix for deepseek format will usually be \<think\> followed by an empty newline. If the newline is missing you can add it in by hitting "enter" after the \<think\>.

Suffix for deepseek format will usually be \</think\> preceded by an empty newline. If the newline is missing you can add it in by hitting enter BEFORE the \</think\>.

Separator is usually always empty.

Below that in miscellaneous is one box that we care about, **Start Reply With**

Start Reply With is ALWAYS empty for native reasoning models like GLM and Deepseek, and usually filled with the same thing you have in the prefix for fake reasoning models like Gemini and Claude.




 although first we need to answer, are you going to use fake reasoning or native reasoning? Both work well, don't worry. Which one you choose will depend on the model, frontier models tend to use fake reasoning, and chinese open weight reasoner models tend to use native reasoning.

For this I've collected information from all the regular users of Lucid Loom active in the channel.

### Fake Reasoning (Gemini, GPT, Claude)

For fake reasoning, we'll be "tricking"

