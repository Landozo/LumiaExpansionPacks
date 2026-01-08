# Lando's Lengthy Loom Lecture

So you want to use Prolix's wonderful Lucid Loom preset? There are a lot of toggles and options and a lot of models to use them with, and it might look daunting, but it's actually pretty easy with some guidance! 

This is an UNOFFICIAL Guide to Lucid Loom by me, Landozo. I am NOT Prolix, the dev of Lucid Loom. If you have any feedback on this guide or questions, you can find me on the Lucid Loom Thread on the AI Presets discord (Link [here](#where-to-go-for-help)).

This Loom guide is current as of 3.2 release (December 30, 2025)!

The latest release is 3.2 from https://lucid.cards/chat-presets

Warning: 3.2 Last Call is a BETA release from BEFORE 3.2. Upgrade to 3.2 if you still use it! 

Best Settings for Each Model are [Here](#best-settings-for-each-model)

## Table of Contents:

- [About LLMs and Picking a model](#what-do-i-need-to-use-lucid-loom-first-pick-a-model)
	- [About LLMs](#about-llms)
	- [Frontier Models](#frontier-models)
	- [Open Weight Models](#frontier-models)
	- [Frontier Model Recommendations](#frontier-model-recommendations)
	- [Open Weight Model Recommendations](#open-weight-model-recommendations)
	- [My Third Party Provider Recommendation (NanoGPT)](#my-recommended-third-party-provider-for-open-weight-models)
- [About Sillytavern and setting it up](#what-else-do-i-need-to-use-lucid-loom-sillytavern)
- [Downloading and Importing Lucid Loom](#getting-lucid-loom)
- [Lucid Loom's Structure and Categories](#getting-the-lay-of-the-loom-the-categories)
- [Reasoning](#reasoning-or-non-reasoning-cot)
	- [Reasoning or Non-Reasoning](#reasoning-or-non-reasoning-cot)
	- [What is a CoT](#cots-what-are-those)
	- [The kinds of Loom CoTs](#cot-selections-zipbomb---the-latest-and-greatest)
- [Reasoning Options in Sillytavern - Configuring Lucid Loom](#configuring-lucid-loom)
	- [Prompt post processing](#prompt-post-processing)
	- [Reasoning Formatting](#advanced-formatting---context-formatting-and-reasoning-formatting)
	- [Request Model Reasoning and Reasoning Effort](#chat-completion-reasoning-settings)
    - [Zipbomb Choices](#zipbomb-choice)
- [Non-Reasoning Related Options](#non-reasoning-related-options)
	- [Context Size and Max Response](#non-reasoning-related-options)
	- [Streaming](#non-reasoning-related-options)
	- [Most commonly changed samplers (Temp, Top P, and Top K)](#non-reasoning-related-options)
- [Best Settings for each model (For Loom 3.2 Release)](#best-settings-for-each-model)
	- [Fake Reasoning](#fake-reasoning-models-gemini-claude)
		- [Gemini 3 Pro/Flash (CoT Zipbomb)](#google-gemini-3-pro--flash-25-pro--flash)
		- [Claude Sonnet/Opus (CoT Zipbomb)](#claude-sonnet-and-opus-1)
	- [Native Reasoning](#native-reasoning-models-glm-deepseek---common-settings)
		- [GLM 4.7 (Reasoning Zip)](#zai-glm-47)
		- [GLM 4.6 (Fallback, CoT Zipbomb)](#zai-glm-46)
		- [Deepseek 3.2 Thinking](#deepseek-32-thinking)
- [Where to Ask for Help! Loom Chat](#where-to-go-for-help)
- [Appendix](#appendix)
	- [What is Sov Hand?](#what-is-sovereign-hand-sov-hand)
	- [What is Regex?](#what-is-regex)
	- [Lumiverse Helper Extension](#lumiverse-helper-extension)
	- [Nemo Preset Extension](#nemo-preset-extension-better-organization-for-prompts)
	- [My Sillytavern Extension Recommendations](#recommended-extensions-my-personal-favorites)

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

### Frontier Models

Frontier models, which are ONLY hosted by the company itself and include things you might have heard of like Claude's Sonnet and Opus, Google's Gemini, OpenAI's ChatGPT, and XAI's Grok. 

Some Pros and Cons 

The big Pro is that frontier models are the "state of the art". They receive daily stealth updates to keep them on the cutting edge, some boast parameter counts in the *trillions*, and they are connected to vast databases called RAGs (retrieval augmentated generation) to help them with looking up information. They also might have searching capabilities built right in. Plus they usually require less work out of the box to get working as they are meant for a mass audience.

Now for the Cons:
These models are hosted on the server of the company and they mass collect information on usage and actively use it to train their models. *So do not have an expectation of any privacy when direct connecting to these models.* 

Additionally, information on these models are not released, we don't know how many parameters they have, when they are updated (most of these models are tweaked daily with no changelogs or notice), and they can be dumbed down for various reasons (safety (meaning countering nsfw), other models need more compute, testing various updates) without warning.

So yeah, it's a tradeoff between performance and ease vs privacy and control.

There is another big downside, *cost*. Most frontier models cost more than the next category of model and tend to be "pay per token". Think of tokens as how much data is sent and received, 1 token is approximately 4 characters for English text. Tokens tend to be priced per million.

Now let's look at the alternative.

### Open Weight Models

Open weight models are released by the companies and let loose onto the internet as *files you can download and run on your own hardware.* These include aforementioned local models, although the larger open weight models are too resource hungry (especially ram) to run on local PC's, tending to be run by third party server providers.

These tend to have different pros and cons compared to frontier models.

Pros:
The first major pro is VERSION CONTROL because the model file is RELEASED onto the internet. Think of it like a book edition, it's released and you get the book and you have it in your hands. The book won't magically rewrite itself. Frontier models are kept by the companies that own it and are updated all the time, as if someone else is reading the book to you from far away and they can change the details without warning. GLM 4.7 (a recently released open weight model as of December 27, 2025) is GLM 4.7. It won't change, it won't be altered, and even if GLM 4.8 comes out, GLM 4.7 will still be on the internet forever. Meanwhile, a frontier like Gemini can be lobotomized one day and you won't know when or why it happened, or an older version you like can be taken offline and you have no recourse.

The second major pro is privacy. Since it can be run outside of the main company's server, you can theoretically find a hoster that will not collect your information. *You should always assume information you send out will be accessible by the hoster anyways.* But unlike companies like Google, which have huge infrastructure ready to collect and sift through data. Third party providers might host a huge variety of models, all of which collect information in different ways. They don't have the time or compute usually to sift through all that data in an efficient way. So a lot of them don't. HOWEVER, they all CAN, so to be safe, pretend they will.

The third pro is COST. A lot of open weight models are smaller and easier to run, plus they don't have massive amounts of infrastructure and RAGs tied to them. So you can find them for pay per month subscriptions instead of pay-per-token like frontier models (I'll shill my favorite later). This is much cheaper by order of magnitudes than models on Claude or Google.

Cons:
Smaller parameters and no huge RAG infrastructure means the models are less "smart" than frontier models in general. However the biggest and most advanced open weight models (Deepseek, GLM) can punch well above their weight class. To the point where I have access to both unlimited Gemini and unlimited GLM and I prefer GLM and it seems *smarter* to me for roleplay. 

Slower releases: Since the models aren't updated on the daily without warning like front


## Frontier Model Recommendations

First up, frontier model recommendations. Remember the name of the game here: convenient, very fast, smart, no privacy, no control over updates, and expensive.

### Google Gemini 3 Pro and 3 Flash

Google's Gemini is the most commonly used frontier model by the regulars of Lucid Loom. There are two versions, Gemini 3 Pro, and Gemini 3 Flash. The former is estimated to be a trillion parameters, but as a frontier model, Google does not release information about it. It's pretty smart, although recently (about December 22) it got a huge hit to smarts and nobody is sure why (a day after the release of the smaller model, maybe google moved limited compute over to flash).

3 Pro can handle roleplay very well, struggles with logic sometimes, and generally has a positivity bias (It'll agree with you too much, color the story more positive, Loom can naturally mitigate this with it's many "darker" toggles). It is censored and requires a jailbreak (Loom as a preset is enough of a jailbreak).

3 Flash is Pro's smaller, lighter weight deranged little brother. It's made for general use, especially on phones, as it's Android's main AI assistant. It's got a darker color, is not as smart as 3 Pro (Although it appears to have more compute dedicated to it as of December 2025, so 3 pro isn't that much smarter), and is also censored, albeit the darker coloring lets you get away with more. Not that it matters, as Loom is enough of a jailbreak for 3 Flash as well.

Native reasoning is not used for Gemini with Loom, in favor of "fake reasoning" (I'll go into this later).

Gemini is usually used through a service called AI Studio, and like most frontier models, is "pay per token". There are free trials you can abuse and plenty of guides on the internet to do it.

There is a subscription too, but I don't know the limits of usage on it. Plenty of information out there about it.

### Claude Sonnet and Opus

Claude is considered the state of the art for roleplay and coding at the moment. Claude has two models, Opus 4.5 and Sonnet 4.5. Sonnet is smaller and equivalent to Gemini 3 Flash from earlier, Opus 4.5 is newer, larger, and comparable to 3 pro. However Sonnet is MUCH smarter than 3 flash and Opus is MUCH smarter than 3 pro.

Sonnet was originally trained up for creative pursuits, and as such is very lauded for roleplaying in particular. It struggles with logic and things like formatting. It also tends to be very token heavy, overthinking everything.

Opus 4.5 is their brand new model. It is smarter than Sonnet, but some people say that hurts roleplay a bit. However those people have not tried the brand new effort parameter. Give it a try, medium effort is supposed to be similar to Sonnet.

The downside of both of these is that not only is Claude pay per token, it's the most expensive pay per token by far.

### Grok or GPT

Some people use Grok, I never have.

Every GPT I ever used for roleplay has been dogwater, don't use it.

## Open Weight Model Recommendations

### ZAI's GLM 4.7-thinking

**GLM is my model of choice**, my daily driver. ZAI has two models, GLM (the big one, 355B parameters) and GLM Air (little brother, 105B parameters). They release them in an alternating fashion. Currently the latest as of December 2025 is GLM 4.7, and it's a doozy.

GLM 4.7 is a reasoning model (we use the native reasoning for Lucid Loom, unlike Gemini, because the native reasoning is GOOD). It is 355B parameters, and regularly outsmarts 1 trillion parameter models like Gemini 3 Pro. I love it to death.  It's smart enough to handle complex formatting, html tags, keep track of stories very well. The downside is that it is slower than Gemini, because third party providers and even zai don't have as much compute as google or claude do. But it's so much cheaper as a result.

GLM 4.7 air... does not exist yet. The latest air is GLM 4.5 Air. GLM 4.6 skipped air and went straight to GLM 4.6V, a vision model (this means it can interpret pictures), which hurt the roleplay/text performance. I do not recommend using GLM 4.6V as a result.

So yeah, just use GLM 4.7. How can you use it though? Since it's an open weight model you have two options, from the manufacturer or third party.

The company that makes it is Z.AI and they have a subscription plan for it. You can get GLM straight from them, however, they have been doing prompt injection lately to "clean up" the nsfw of the model. If you want to use it for smut roleplay, I do NOT recommend zai, in fact, I don't recommend ZAI at all. As a source company for the model, they have the infrastructure in place to mass collect data and sort it easily.

I recommend NanoGPT, a third party provider, due to their 8 dollar a month practically unlimited subscription, I'll give more info on it later.

### Deepseek's Deepseek

Deepseek is probably the most well known of the chinese model makers. They have Deepseek 3.2 speciale and Deepseek 3.2 thinking. Both are larger 685 billion parameter models, but the former has more "active" parameters than the latter. That means Speciale is their model comparable to Gemini 3 Pro, while 3.2 Thinking is the one comparable to Flash. As far as I know the former is still only available direct from deepseek, which means you need to deal with the privacy issues inherent to using any model straight from the manufacturer. The latter is available from third party providers readily.

### Kimi K2 and Qwen

Kimi K2 Thinking is used by some people in the loomchat. It tends to be problematic and fight you, I don't recommmend it.

I don't know a single person who still uses Qwen, but people used to a lot.

## My recommended Third Party Provider for Open Weight Models

My **personal** recommendation for using open weight models is through Nano-GPT. They have an 8 dollar subscription that lets you use 60,000 message requests per month, unlimited tokens on 80+ different open weight models. They do rotate providers as the tokens are used up on their end, so sometimes you'll have a slower provider, but you can't beat 8 bucks a month for practically unlimited requests (I've never even come close to 60k chat messages per month). The subscription includes 80+ open weight third party hosted text models with things like GLM 4.7, Deepseek 3.2-Thinking, Kimi K2, Qwen, a lot of local models (including the classic TheDrummer ones like Rocinante, Cydonia, etc.), four image models (Chroma, Hidream, Juggernaut XL (animagine based), and Qwen Edit), and lots of abliterated/derestricted/finetuned versions of popular models (TheDrummer's glm 4.5 air finetune called GLM Steam comes to mind).

You can find it by googling nanoGPT, or you can help me out by using my referral link below:

https://nano-gpt.com/invite/XFjmGJg8

If you use Nano GPT with the subscription, you can access a subscription model only endpoint by entering the following as your custom (openAI-compatible) endpoint:

https://nano-gpt.com/api/subscription/v1

This will give you only the subscription models so you run 0 risk of accidentally spending money!

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

<img width="390" height="411" alt="image" src="https://github.com/user-attachments/assets/529be64e-5648-4983-8a2d-c19bc5af49a3" />

## Importing Lucid Loom into Sillytavern

To import it, after picking Chat Completion open the left hand panel (leftmost icon on the top bar of sillytavern) and click the imnport button and select your json! This will cause the panel below to switch to Lucid Loom.

<img width="641" height="335" alt="image" src="https://github.com/user-attachments/assets/7c623dd5-0251-4c56-8ed9-1772e4d942eb" />

I'll go over the best options for Loom later, but first, let's scroll down in this panel 

## Getting the lay of the loom, the categories

Lucid Loom, like most presets, relies on a category system to make things less cluttered. It might seem overwhelming at first but you'll get used to it pretty quickly.

There is an extension to allow things to collapse into nice categories, I'll go over it later. First, the categories.

### Prompt Variables (EDIT ME PLEASE)

This toggle allows you to edit some variables and choose how long the "Custom Response Length" toggle makes your reply, change the LLM's main output language, or change how often OOC happens (unless you use the extension, that one works better, more on that in the appendix).

### Story Primers and Core Instructions

Important things like card, user persona, and scenario information are pulled in first thing in the "Story Primers" category (Loom does not use the default Sillytavern prompts for those, hence why those are still in but off later).

<img width="390" height="411" alt="image" src="https://github.com/user-attachments/assets/bbd25b89-6c13-4d77-98d0-1c0502cf1584" />

Then comes the core instructions and modes for the Loom. Human Controls User and Sov Hand are the two options here. The former limits control of {{user}} to only you, the Human. The latter is more complex, see the appendix for details on Sov Hand.

### Lumia Definitions and Personalities

Then Lumia definitions (physical description) and personalities. Loom's main claim to fame is that it causes the AI to assume the role of a storyteller called Lumia. There are dozens of Lumias with different personalities available through an extension I'll talk about later by the same dev of Loom. For now, you get 7 personalities built in with a custom option to allow pulling in extra lumias from the extension.

<img width="371" height="695" alt="image" src="https://github.com/user-attachments/assets/3a73edcd-f4bf-42db-ac50-5e5db1149e26" />

One thing to keep in mind under personalities is "Weave Lock". This helps mitigate the personality from affecting the story too much.

<img width="354" height="80" alt="image" src="https://github.com/user-attachments/assets/4463b626-368d-45bc-b658-916c6da99229" />

### Various Story and Response related Categories

Then the rest of the toggles are all things that affect the generated story, like the point of view of the storyteller, genres, narrative styles, plot progression options, response length options, text formatting, prose guidelines, dialogue options, nsfw options, and story details.

<img width="394" height="616" alt="image" src="https://github.com/user-attachments/assets/da56a4ad-53b5-4847-b6c7-7a0e91b11048" />

### Utilities and Trackers

Utilities and Trackers are categories that have little useful utilities like OOC commentary, time lookups, summarization utilities, and the like. Trackers are various little trackers that help Lumia keep track of what has happened thus far in the story.

### Story Details

After that is Story Details, where the only important things are World History (Lorebooks) and the optional extension summarization toggle (I'll go over this later) which is off by default. **The reason this section is full of turned off toggles is because Loom does not use them. But if you delete them, Sillytavern breaks, so we leave them here and off.**

<img width="397" height="486" alt="image" src="https://github.com/user-attachments/assets/95a48010-88ba-4822-809d-cd32aac611b4" />

Keep these off except for World Info (Before and After). Lumiverse summary can be turned on if you use the extension.

### Chat History

This is where Chat History lives, it's the best place for it from experimentation in the past.

### Planning Effort

This helps tell your LLM how much work to put into the reasoning phase. Some models ignore this. I recommend keeping it on extreme.

<img width="377" height="150" alt="image" src="https://github.com/user-attachments/assets/aa70b5ec-8d4e-4b92-8c7c-eb1e03ff4c7a" />

### CoT Selections

These are the reasoning checklists for Loom. I'll explain them in more detail in the next section.

<img width="383" height="315" alt="image" src="https://github.com/user-attachments/assets/717dda8a-64b1-4cb0-9db8-fcb85fecc1ac" />

## Reasoning or non-Reasoning? CoT?

Lucid Loom is built with reasoning in mind. It works a lot better if you are using the reasoning capabilities of an LLM. If you don't want to use Reasoning, I'll have a section at the end for you.

So what do we mean by reasoning. Well reasoning is using the first part of the response of an llm to "think through" or plan the response, and then it follows it with the final actual response.

In Sillytavern, the reasoning block should be hidden in a dedicated dropdown box. If it isn't, your reasoning settings are wrong. I will be going over how to set up reasoning settings later in the guide.

The important thing is that this reasoning block is NOT sent as part of chat history. So all the planning will not clutter up your context!

### CoTs? What are those?

CoTs, or Chain of Thoughts, are a kind of checklist to guide the reasoning process of an llm. There are various kinds in Loom.

**ONLY USE ONE COT AT A TIME. THIS IS IMPORTANT.**

You'll see that the Loom CoT sections are split up into four sections.



### Cot Selections (Zipbomb) - The latest and greatest

First up in the CoT sections are the Zipbombs. These are large, detailed checklists where Lumia thinks through her reasoning in character. This is where the lion's share of Loom's dev time for CoT goes to and the CoT type I will always recommend to people.

You'll find two major types of Zipbomb. CoT Zipbomb and Reasoner Zipbomb. The former includes language for \<think\> tags in the beginning and ending. These are useful for "fake reasoning" models like Gemini where you have to start the reply with a \<think\>.

The reasoner zipbomb are for models smart enough to handle the thinking block start and stop on their own, like GLM 4.7.

<img width="383" height="177" alt="image" src="https://github.com/user-attachments/assets/60490687-b9cb-498d-9fd2-a315a815b036" />


### CoT Selections (Lumiverse)

If you use the Lumiverse Helper Extension (See Appendix) at all, you should pick your Zipbomb from here. This means if you use custom Lumias or the Extensions Summary or Sov Hand function you NEED to pick your zipbomb from here if you want it to work.

You will pick the same zipbomb you'd pick in the above section, just picking down here instead of the above.

<img width="377" height="186" alt="image" src="https://github.com/user-attachments/assets/0e5681f2-aba5-40ae-9edb-21f6a5608ffe" />

### CoT Selections (System) - The Old and Small

Third is the CoT Selections (System) category. This one includes older and smaller checklists that aren't really the focus of Loom. They can be used if you desperately need to save on token usage.


### CoT Selections (Assistant) - Alternate sending roles and utilities

Lastly, these CoT's in here allow you to send them as assistant instead of system, something you won't be doing very often. In addition there is a /think flag that is useful in here for GLM on platforms that aren't NanoGPT.

### That's a lot of Information

Yes it is, thankfully you don't have to remember most of it. It's mostly here for you to refer back to if you have any questions.

Now that you have a better idea of what Loom looks like. Let's get to installing it!

## Configuring Lucid Loom

Okay, now that you've imported Loom and I've gone over the structure, we can configure it for proper reasoning!

Thankfully there are only a few places we'll have to look to get reasoning up and running. I'll point out the locations and what they do first, and then we'll tackle how to set them up for each model afterwards. There are only three locations to set, prompt post processing, reasoning formatting, and chat completion settings. After that you just pick the right zipbomb, set your samplers to your flavor, and you are good to go!

### Prompt Post Processing

In the API Tab underneath where you select the model is a dropdown called Prompt Post Processing. This alters the raw prompt sent out to the LLM to better help it understand which things are from the system and which are from the user.

<img width="343" height="333" alt="image" src="https://github.com/user-attachments/assets/5b458d0a-d147-4761-9a7d-a3f012664b17" />

There are several options:
- None (no processing applied) 
- Merge Consecutive (Merge consecutive messages from the same role)
- Semi-Strict (Merges Roles and Allow one optional system message)
- Strict (Merge roles and Allow one optional system message and sends a user message first)
- Single User Message (Merges all messages from all roles into a single user message)

Additionally there is tools or no tools for each of these. Tool calling lets llms interact with external systems like programming apis, web searches, etc. These have to be set up on the LLM's side and you'll probably already know if you have them on. I'd recommend picking no tools by default if you don't know what this means.

### Advanced Formatting - Context Formatting and Reasoning Formatting

In the advanced formatting tab (The A up top to the right of the API icon), you'll find that most of it is grayed out since most of these options are for text completion. However we still have a few important sections here.

<img width="36" height="34" alt="image" src="https://github.com/user-attachments/assets/21d92c67-aca6-42ea-85df-f37ec03ac215" />

To the lower left are three checkboxes under the context formatting section. These are user preference except for Trim Incomplete Sentences, you'll want this one UNCHECKED, or it can break loom tags and formatting.

<img width="287" height="236" alt="image" src="https://github.com/user-attachments/assets/b84ef3e0-a4c2-4920-be27-463a5098041b" />

On the lower right is the Reasoning formatting section.

First are three checkmarks:

Auto-Parse should ALWAYS be on, it enables the below section to be able to capture text into a reasoning box if the tags are correct. This is the only way "fake reasoning", which is what we use for Gemini, Claude, and GPT, can work.

Auto-Expand expands the little thinking box containing the reasoning upon each new message, this is user preference.

Show Hidden shows the reasoning time for models with hidden reasoning, I recommend you leave this on.

Below that is a **Reasoning Formatting** dropdown you can expand. This is where you set the reasoning formats.

<img width="427" height="553" alt="image" src="https://github.com/user-attachments/assets/519bd64b-c947-4f65-8eb0-58c7cb04cc26" />

I recommend for pretty much everyone that you pick Deepseek here. Gemini uses it, Claude uses it, GLM uses it, and of course Deepseek uses it. Both fake and native reasoning models will use deepseek formatting, and if they don't, there's no harm in leaving this on deepseek anyways.

The dropdown sets the next two boxes, Prefix and Suffix, which are what will open and close the reasoning block.

Prefix for deepseek format will usually be \<think\> followed by an empty newline. If the newline is missing you can add it in by hitting "enter" after the \<think\>.

Suffix for deepseek format will usually be \</think\> preceded by an empty newline. If the newline is missing you can add it in by hitting enter BEFORE the \</think\>.

Separator is usually always empty.

Below that in miscellaneous is one box that we care about, **Start Reply With**

<img width="193" height="92" alt="image" src="https://github.com/user-attachments/assets/ee23890f-8ca3-42bb-be44-3a6b72bce3e7" />

Start Reply With is ALWAYS empty for native reasoning models like GLM and Deepseek, and usually filled with the same thing you have in the prefix for fake reasoning models like Gemini and Claude.

This is important! If your reasoning doesn't work, Start Reply With is the first place you should check.

These reasoning models save with your API settings, so hit SAVE on the api page after editing them (yes, they save with the api profile, not with the preset settings).

<img width="315" height="190" alt="image" src="https://github.com/user-attachments/assets/24d63f36-6f64-4d26-91fa-35f5bb39b996" />

### Chat Completion Reasoning Settings

In the left hand Chat Completion menu above where the loom toggles are and below the sampler sliders is a little dropdown called Chat Completion Settings.

In there is a toggle option call "Squash System Messages". This can be used for some prompt post processing options like None, but unless directed to, I'd recommend you leave this UNCHECKED.

The important sectino is below that. Two options both related to Reasoning.

Request Model Reasoning affects the ability of Sillytavern to show incoming native/non-fake reasoning at all. If you are using native reasoning, this checkbox MUST BE ON (you'll still receive reasoning without it on, but sillytavern will not show it, meaning you just wasted tokens for no reason).

Next is Reasoning Effort, this one is important for every model. For native reasoning models like Deepseek or GLM, you want it on Maximum. 

<img width="373" height="165" alt="image" src="https://github.com/user-attachments/assets/37f54d62-8518-4184-b361-6fd318bbe90a" />

For models where you don't want to use the reasoning and instead want to use "Fake" reasoning, you want it on minimum or auto (sometimes auto means off, your mileage may vary).

<img width="376" height="171" alt="image" src="https://github.com/user-attachments/assets/4526df98-e604-4f85-90b9-c0158278861b" />

So it's ON / Maximum for GLM and Deepseek, OFF / Minimum for Gemini and Claude!

To save these you hit the save button by the preset dropdown up top:

<img width="369" height="157" alt="image" src="https://github.com/user-attachments/assets/3158b8ca-68bf-4aa6-9fea-fcb90b98936f" />

### Zipbomb Choice

I'll go over this in more detail in the per model best options, but typically you want CoT zipbombs for fake reasoning models (Gemini, Claude), and reasoner zipbomb for native reasoning models (GLM, Deepseek).

<img width="375" height="188" alt="image" src="https://github.com/user-attachments/assets/07f4b597-a27a-484c-993a-6cecd6ef3b60" />

CoT Zipbomb for Gemini, Claude, or GLM 4.6

<img width="379" height="191" alt="image" src="https://github.com/user-attachments/assets/11ed54ca-4575-46af-8b8b-d493f13347bb" />

Reasoner Zipbomb for GLM 4.7 or Deepseek

As for what "Mini" means, they are new zipbombs rewritten to use language that is lighter on tokens. Try either or, they should work the same.

If you use the lumiverse extension, you should pick the Zipbombs from the CoT Selections (Lumiverse) category instead. Custom Lumias and Extension Sov Hand will NOT work without it!

<img width="378" height="180" alt="image" src="https://github.com/user-attachments/assets/630362e8-c1b4-48b0-a9e8-9facf1a3d532" />

A flowchart of which CoT to pick (More details in the sections below!)

```mermaid
flowchart TD
    A(Reasoning: Yes) --> B{Planning Effort}
    B --> C(Low/High/Extreme)
    C --> D{Reasoning Type}
    D -->|Gemini/Claude| E[Fake Reasoning]
    D -->|GLM/DS/Kimi| F[Native Reasoning]
    E --> G(Lumiverse?)
    F --> H(Lumiverse?)
    G -->|Yes| I(CoT Zipbomb/Zip Mini #lpar;Lumiverse#rpar;)
    G -->|No| J(CoT Zipbomb/Zip Mini #lpar;System#rpar;)
    H -->|Yes| K(Reasoner Zipbomb/Zip Mini #lpar;Lumiverse#rpar;)
    H -->|No| L(Reasoner Zipbomb/Zip Mini #lpar;System#rpar;)   
```

## Non-Reasoning Related Options

There are some universally useful options for every model.

Context Size is how big the context is. Every model has a different value (GLM is 200k, Gemini is 1 million). Sometimes setting it to 2/3's the max context provides better results (I follow this rule as a law).

Max Response Length is how big the response you can get back is. I suggest 16384 or 32768.

Streaming On or Off. Streaming off means you won't get any reply until the entire reply is posted. Loom works perfectly with it on, so turn it on so you can see the thinking in realtime!

Samplers are the sliders that determine how creative or non-creative a model is. There are typically three samplers we play around with:

Temperature. Temperature determines how "whacky" the output of the model is. Higher temp = more whacky. Lower temp = less creative. Every model has a happy medium.

Top K. Top K determines how many of the most likely option is taken. Let's say I meet someone and I want to say hi. When I open my mouth, the most common thing I might say is Hello, followed by Hi, or Heyo, or what's up, for example. Top K's value takes those most common values and cuts them off. So a Top K of 40 means only the 40 most likely values are kept and the rest are discarded.

Top P. Top P is a way to make the least likely value more likely. It works like a curve in test grading. Everyone gets the benefit of the curve, and it hurts the top/most likely response the most while benefitting the lowest one the most.

These are the main three samplers people play around it, the rest are to user's taste more often. Top K might be missing from your options, you can send it with additional parameters or the custom sliders extension if so (not that important).

To save these you also hit the preset save button up top.

<img width="369" height="157" alt="image" src="https://github.com/user-attachments/assets/3158b8ca-68bf-4aa6-9fea-fcb90b98936f" />

So which setting is best for each model? The following is collected from the common users of the Lucid Loom discord chat.

## Best Settings for each model 

These best settings are current as of Lucid Loom 3.2 (December 30, 2025).



## Fake Reasoning Models (Gemini, Claude)

For all fake reasoning models like Gemini 3 Pro/Flash and Claude Sonnet/Opus we want the following settings in common:

Reasoning Formatting (Advanced Formatting Tab, lower left):

Deepseek in the dropdown. \<think\> (followed by a newline) Prefix and \</think\> (preceded by a newline) suffix.

Start Reply With: \<think\> followed by an empty newline.

<img width="427" height="560" alt="image" src="https://github.com/user-attachments/assets/63d6f764-51dc-4e96-a24a-dcc547d8a207" />

Hit save on your api profile after this since it's saved there.

Chat Completions Reasoning Section:

Request Model Reasoning should be OFF/Unchecked

Model Reasoning Effort is PER MODEL.

<img width="376" height="171" alt="image" src="https://github.com/user-attachments/assets/4526df98-e604-4f85-90b9-c0158278861b" />

Hit save on the preset panel after setting the above.

### Google Gemini 3 Pro / Flash, 2.5 Pro / Flash

Prompt Post Processing: Semi-strict or Merge

Hit save on the api profile to save the above after setting it.

Model Reasoning Effort is Minimum!

CoT Choice in Loom: CoT Zipbomb (System) or CoT Zipbomb Mini [Lumiverse if using extension]

Context and Samplers:
Context Size 600k-1000k
Response Size: 32762
Streaming ON
Temperature: 1
Top K: 255
Top P: .96

<img width="368" height="183" alt="image" src="https://github.com/user-attachments/assets/62970b4d-43d6-4c43-a1b8-630ae305c0c6" />

Hit save in the profile preset after setting these.

### Claude Sonnet and Opus

Prompt Post Processing: Semi-strict or Merge

Hit save on the api profile to save the above after setting it.

Model Reasoning Effort is Auto!

CoT Choice in Loom: CoT Zipbomb (System) or CoT Zipbomb Mini  [Lumiverse if using extension]

Context and Samplers:
Context Size 120k-200k
Response Size: 32762
Streaming ON
Temperature: 1
Top P: 1

<img width="368" height="183" alt="image" src="https://github.com/user-attachments/assets/62970b4d-43d6-4c43-a1b8-630ae305c0c6" />

Hit save in the profile preset after setting these.

## Native Reasoning Models (GLM, Deepseek) - COMMON SETTINGS

For all native reasoning models like GLM and Deepseek we want the following settings in common:

Reasoning Formatting (Advanced Formatting Tab, lower left):

Deepseek in the dropdown. \<think\> (followed by a newline) Prefix and \</think\> (preceded by a newline) suffix.

Start Reply With: *EMPTY, ALWAYS EMPTY FOR EVERY CHINESE REASONING MODEL*

<img width="405" height="98" alt="image" src="https://github.com/user-attachments/assets/a3840793-962e-412c-9762-3b2cf688bb54" />

Hit save on your api profile after this since it's saved there.

Chat Completions Reasoning Section:

Request Model Reasoning should be ON/Checked

Model Reasoning Effort should be MAXIMUM.

<img width="383" height="174" alt="image" src="https://github.com/user-attachments/assets/fb983139-bb22-4887-8086-0a57b0d3fddc" />

Hit save on the preset panel after setting the above.

### ZAI GLM 4.7

Prompt Post Processing: Semi-Strict

Hit save on the api profile to save the above after setting it.

CoT Choice in Loom: CoT Reasoner Mini or CoT Reasoner Mini [Lumiverse if using extension]

Global Think Trigger: OFF (The one at the start of the preset)

GLM Think Trigger: Off (This is at the bottom of the CoT section). This is not necessary if you pick GLM "thinking" models on NanoGPT (*IF you pick GLM 4.7:thinking* on nano, it will send this for you, so pick the thinking model option). But otherwise you want it on for other providers.

Context and Samplers:
Context Size 128k-200k
Response Size: 16384
Streaming ON
Temperature: .85-1
Top K: 40 (Optional, Additional Parameters or Custom Slider to add it)
Top P: .93

<img width="369" height="185" alt="image" src="https://github.com/user-attachments/assets/b827f070-a0ac-4313-afca-792f60f30fa9" />

Hit save in the profile preset after setting these.

If these don't work you can use the below settings as a fallback.

### ZAI GLM 4.6

Prompt Post Processing: Single User

Hit save on the api profile to save the above after setting it.

Global Think Trigger: ON (The one at the very start of the preset)

GLM Think Trigger: On (This is at the bottom of the CoT section). This is not necessary if you pick GLM "thinking" models on NanoGPT (It will send this for you). But otherwise you want it on for other providers.

CoT Choice in Loom: CoT Zipbomb Mini or CoT Zipbomb (System) [Lumiverse if using extension]

Context and Samplers:
Context Size 128-200k
Response Size: 16384
Streaming ON
Temperature: .85-1
Top K: 40 (Optional, Additional Parameters or Custom Slider to add it)
Top P: .93

<img width="384" height="196" alt="image" src="https://github.com/user-attachments/assets/d2f30046-bd54-461f-8e69-d8253b9de83b" />

Hit save in the profile preset after setting these.

### Deepseek 3.2 Thinking

Prompt Post Processing: Semi-Strict or Merge

Global Think Trigger: OFF (The one at the start of the preset)

Hit save on the api profile to save the above after setting it.

CoT Choice in Loom: Reasoner Zip Mini or Reasoner Zipbomb (System) [Lumiverse if using ext]

Context and Samplers:
Context Size 128k
Response Size: 16384
Streaming ON
Temperature: 1-1.5
Top K: 0 (Might not support it)
Top P: .95

<img width="369" height="185" alt="image" src="https://github.com/user-attachments/assets/71c70080-8c22-4c6b-9df7-2b8ffda41ac1" />

Hit save in the profile preset after setting these.

### Settings for not using reasoning at all

For people who don't want reasoning, be aware that Loom is designed for reasoning and it has no reminder handrails for non-reasoning use (I'll be coming up with some soon and pushing them at Prolix). The below are settings for 

Reasoner Formatting Settings:

Doesn't matter, but you need to make sure START REPLY WITH is EMPTY.

Prompt-Post Processing: Refer back to your model's settings up top.

Hit save to lock these in.

Chat Completion Settings:

Request Model Reasoning should be UNCHECKED.
Model Reasoning Effort should be set to Auto for Claude and Minimum for Gemini.

Global Think Trigger at the top of Loom: TOGGLED OFF

CoT Selection: 
Ensure no CoT is selected at all, check all 4 sections in loom to ensure none are on.

Think Trigger (GLM/Qwen) in Assistant section: TOGGLED OFF

You should be good to go with no reasoning now.

# Where to Go for Help!

In the AI Presets discord:

https://discord.gg/y6JPs948

There is a Lucid Loom Channel in said discord:

https://discordapp.com/channels/1357259252116488244/1414663352428396574

I hang out there, as well as other regulars.

---


# Appendix

## What is Sovereign Hand (Sov Hand)?

Sovereign Hand is a feature pioneered by Easy and endlessly iterated on by Prolix. What it does is take your input on what {{user}} is doing in the message you send, and then in the next AI sent reply, it will rewrite and expand upon what you wrote into full prose with additional detail.

So for example if you wrote {{user}} opened the door. It will write about {{user}} seeing the door, walking up to it, feeling the doorknob, opening it, etc.

This means it echoes (repeats) the last response, meaning you need to TURN OFF ANTI-ECHO DIALOGUE SEAL in the Core Instructions section (it's there in 3.2, in prose in older ones).

It also means Lumia controls User, which means you need to TURN OFF HUMAN CONTROLS USER toggle in the same section.

## What is Regex?

Regex is short for Regular Expression, it's a scripting language that allows you to find text and either replace it or get rid of it. The most common use of it is ST is to trim out old tags. Loom has some custom regexes you can turn on if you want, but I would not recommend using them, instead I recommend using:

## Lumiverse Helper Extension

This is an extension by Prolix, the same dev of Lucid Loom that can be found here:

https://github.com/prolix-oc/SillyTavern-LumiverseHelper

Features:

- Import custom Lumias straight from the extension (I've pushed 40 Lumias there as of December 2025, and Prolix and Jun have pushed many of their own!)
- Import custom narrative styles (I've pushed nearly 20 allowing Lumia to write from famous authors throughout history)
- Import custom utilities (I'm about to push a pack!)
- Better Sovereign Hand (Sov Hand that allows inserting the user message, trimming old context, and lots of other stuff)
- Chat History Cleaning Features (Trim old Loom specific tags or any html from old replies, replacing the need for Regex)
- Summarization (A summarization engine that supports alternate LLMs other than your main)

## Nemo Preset Extension (Better organization for Prompts)

This extension by Nemo allows you to have the categories nest in dropdowns in the prompt manager, saving your scroll finger and your sanity. Link here:

https://github.com/NemoVonNirgend/NemoPresetExt

It also has a bunch of other ui overhauls and features.

Some important changes to make, Turn off "Unified Reasoning Section", it can occasionally break reasoning settings. Also I recommend changing Section Dropdown Style to Accordion List for your own sanity.

## Recommended Extensions (My Personal Favorites)

Essentials for Loom:
- Lumiverse Helper (Custom Loom Features)

https://github.com/prolix-oc/SillyTavern-LumiverseHelper
- Nemo Preset Extension (Make Loom Categories easier to navigate)

https://github.com/NemoVonNirgend/NemoPresetExt


THE GOATS:
- Guided Generations (Lets you send next reply guidance to the LLM without having to send a reply)

https://github.com/Samueras/GuidedGenerations-Extension
- Moonlit Echoes Theme (Theme so ubiquitous, nearly everyone uses it, be sure to use glimmer)

https://github.com/RivelleDays/SillyTavern-MoonlitEchoesTheme
- Presence (allows you to set groupchat members to only see the scenes where they are present)

https://github.com/lackyas/SillyTavern-Presence

UI Improvements:
- Custom Sliders (Add in missing sliders, like top k into openai)

https://github.com/SillyTavern/Extension-CustomSliders

To make your chats better
- Silly Sim Tracker (Also by Prolix, the maker of Loom, a fancy tracker that can track stats, relationships, and loads of other stuff, works well with Loom!)

https://github.com/prolix-oc/SillyTavern-SimTracker
- Group SendAs (Send a message as a group member in a chat with an easy button)

https://github.com/SillyTavern/SillyTavern-GroupSendAs
- Timelines (Visual Novel Timeline based navigation for Branching Chat Histories)

https://github.com/SillyTavern/SillyTavern-Timelines

Better Memories:
- Memory Books (Allows saving entire segments of multiple messages to lorebooks for cross chat recall)

https://github.com/aikohanasaki/SillyTavern-MemoryBooks
- World Info Recommender (Guided event creation from messages for lorebooks)

https://github.com/bmen25124/SillyTavern-WorldInfo-Recommender

Better Characterization:

- BunnyMo (Lorebooks that allow smart insertion of character traits)

https://github.com/Coneja-Chibi/BunnyMo
- Carrotkernel (Automates the above)

https://github.com/Coneja-Chibi/CarrotKernel

Vectorization (A way to save context on messages, lorebooks, etc.):
- Vecthare (Alternate Vectorization Storage Engine)

https://github.com/Coneja-Chibi/VectHare
- BananaBread (A vectorization/embedding server, you'd use the above to connect to it)

https://github.com/prolix-oc/BananaBread


# FUTURE MEMES (References for future versions)

## 3.3 Beta 1 Settings flowchart:

```mermaid
flowchart TD
    A(Reasoning: Yes) --> B{Planning Effort}
    B --> C(Low/High/Extreme) & D(Custom)
    C --> E{Reasoning Type}
    D -->|Set token vars| E{Reasoning Type}
    E -->|Gemini/Claude| F[CoT Triggers]
    E -->|GLM/DS/Kimi| G[Reasoner Triggers]
    F & G--> H{Unified Zip Type}
    H --> I(Zip Full) & J(Zip Mini)
```


flowchart TD
    A(Reasoning: Yes) --> B{Planning Effort}
    B --> C(Low/High/Extreme)
    C --> D{Reasoning Type}
    D -->|Gemini/Claude| E[Fake Reasoning]
    D -->|GLM/DS/Kimi| F[Native Reasoning]
    E --> G(Lumiverse?)
    F --> H(Lumiverse?)
    G -->|Yes| I(CoT Zipbomb #lpar;Lumiverse#rpar;) & J(CoT Zip Mini #lpar;Lumiverse#rpar;)
    G -->|No| K(CoT Zipbomb #lpar;System#rpar;) & L(CoT Zip Mini #lpar;System#rpar;)
    H -->|Yes| M(Reasoner Zipbomb #lpar;Lumiverse#rpar;) & N(Reasoner Zip Mini #lpar;Lumiverse#rpar;)
    H -->|No| O(Reasoner Zipbomb #lpar;System#rpar;) & P(Reasoner Zip Mini #lpar;System#rpar;)


