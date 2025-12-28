# Lando's Loom Lecture

So you want to use Prolix's wonderful Lucid Loom preset? There are a lot of toggles and options and a lot of models to use them with, and it might look daunting, but it's actually pretty easy with some guidance!

## What do I need to use Lucid Loom?

### An LLM

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
Smaller parameters and no huge RAG infrastructure means the models are less performant than frontier models in general. However the biggest and most advanced open weight models (Deepseek, GLM) can punch well above their weight class. To the point where I have access to both unlimited Gemini and unlimited GLM and I prefer GLM and it seems *smarter* to me for roleplay. 





#### Actual Model Recommendations



https://nano-gpt.com/invite/XFjmGJg8

### Sillytavern

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

Sillytavern has a variety of api connection points you can use to connect to your model of choice.

## Getting the lay of the loom

Lucid Loom, like most presets, relies on a category system to make things less cluttered.



## Reasoning or non-Reasoning?

Lucid Loom is built with reasoning in mind. It works a lot better if you are using the reasoning capabilities of an LLM.

So what do we mean by reasoning. Well reasoning is using the first part of the response of an llm to "think through" or plan the response, and then it follows it with the final actual response. 



## CoTs? What are those?

CoTs, or Chain of Thoughts, are a kind of checklist to guide the reasoning process of an llm.

