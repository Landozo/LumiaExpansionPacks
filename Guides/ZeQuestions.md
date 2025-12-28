# If you want help with reasoning, you will probably be asked.... ZE QUESTIONS

## What is this for?

These are the five most commonly asked questions to  help with enabling proper thinking/reasoning in the Lucid Loom channel. However the first four are universally useful for ANY preset if you are trying to enable reasoning!

Alternately, if one of us have settings that already work for your model, we might just tell you what to enter for the below question sections!

## What is thinking/reasoning (in this context)?

It is the thinking box that appears that lets your model "think" things through using extra tokens. This is unique to each reply and is not passed onto your chat history (unless you enable a rarely used setting). This means your model can give you more advanced replies without cluttering up your chat history with the thinking process!

In Sillytavern this shows up under a box at the top of each reply with thinking enabled that says "Thinking..." and then when it's done it says "Thought for x seconds/minutes" That you can click to expand or close.

A lot of state of the art presets use thinking with checklists they provide called CoT (Chain of Thought) which is a thinking guide to ensure it adheres to the "ideal" thinking structure for the preset. Lucid Loom has various CoT's of different sizes (Although most people use the largest and most well developed one, called Zipbomb.). 

## So What are ze questions?

Question 1: What is your model, provider, and api connection type?

Question 2: What is your prompt post processing set to?

Question 3: What are your 'request model reasoning', 'reasoning effort', and 'squash system messages' settings in chat completion set to?

Question 4: What are your reasoning settings and start reply with in advanced formatting set to?

Question 5: What is your assistant prompts section in Lucid Loom set to?

Wow, those look like more than five questions? Well it's because they are split up into grouped sections. Everything for 3 will be right next to each other, everything for 4 will be right next to each other, you get the idea. Below are the details of each question if you want to know more!

## Ze Questions in Detail


### Question 1: What is your model, provider, and api connection type?

This is the most important question and can usually instantly let people know how best to help you.

Also let us know the API Method you use to connect to it. (Official API? Google AI Studio? OpenAI v1 custom? Etc)

*This can be found in your API Connections tab (Plug icon)!*

**If your provider is a reverse proxy, just let us know that it *is* one, don't tell us what the proxy is! Keep your sauce secret!**


<img width="632" height="770" alt="image" src="https://github.com/user-attachments/assets/2fba0e6b-f183-44ca-8e6d-94c42b32fcd7" />


---

### Question 2: What is your prompt post processing set to?

*Can be found in the api tab RIGHT BELOW the stuff from question one!*

This is very important as nearly every model will want a different setting and it can break everything if set to the wrong one!

One thing that is for sure is that if you have a choice between two of the same options with the only difference being "tools" and "no tools", you will want to pick "no tools" for RP. Sometimes models even charge extra if you accidentally call a tool, better safe than overcharged!

---

### Question 3: What are your 'request model reasoning', 'reasoning effort', and 'squash system messages' settings in chat completion set to?

*In the top nav bar of Sillytavern, the hamburger sliders icon will open the chat completions preset panel!*

<img width="34" height="27" alt="image" src="https://github.com/user-attachments/assets/1361c5be-d537-487e-a11b-d6bebdec11dd" />

*In the left hand chat completions preset panel, if you go under the samplers, there is a dropdown called chat completions. Below you will find several options that are important.*

<img width="414" height="677" alt="image" src="https://github.com/user-attachments/assets/982559ac-bc25-4523-895a-2fb178b18387" />

The first is 'squash system messages'. This is important to know if you have on or off depending on your answer to #2. Some prompt post-processing choices, like 'None', can use this to help out with the input into the llm.

A couple settings under that there is an checkbox option called 'Request model reasoning'. This is on if you want to see the incoming 'native reasoning' from a model in Sillytavern. This is useful for native reasoning models like GLM and Qwen. For other models you want it set to off, so it is important you tell us what you have this set to if you have problems.

Underneath that is 'reasoning effort', this is usually set to either auto (especially if you have the previous option unchecked) or maximum (if you want full native reasoning). Another essential thing for you to tell us.

---

### Question 4: What are your reasoning settings and start reply with (SRW) in advanced formatting set to?

*In the top nav bar of sillytavern, there is an "A" icon. This will take you to the advanced formatting tab.*

<img width="36" height="32" alt="image" src="https://github.com/user-attachments/assets/397079f2-acaa-45a4-9ba1-9ea52ea9826b" />

This tab will be nearly entirely grayed out, since nearly all of it is used for text completion, and you are using a chat completion preset if you are using something like Lucid Loom. *However if you scroll down on the right there is a VERY important section for reasoning. It is, strangely enough, called reasoning.*

<img width="470" height="614" alt="image" src="https://github.com/user-attachments/assets/b9df8c52-2a8d-4449-8b33-f71c4ab09e09" />


Under this section are multiple checkboxes. First is "Auto-Parse." This will enable this section to work entirely and is important to be turned on if you are using this section at all. Next is "Auto-Expand", this will simply auto expand the reasoning block. Show hidden is usually always on. Add to prompts lets you add previous reasoning blocks to your chat history, you usually always want this OFF for regular RP.

Below is a dropdown toggle called reasoning formatting. This is VERY important.

Here you have a dropdown menu that provides you with different reasoning formats in the prefix and suffix field. The most commonly used one is DeepSeek, which fills those fields with a ```<think>``` and ```</think>```. Basically what this does is tell Sillytavern (not the model), "if I see a ```<think>``` tag prefix in the output from the llm, I will start a reasoning block, and if I see a "</think>" tag suffix I will close the reasoning block. By doing this even "non-thinking" models can access a fake form of "thinking" that actually works pretty well (Gemini 2.5 for example does this).

One important thing to keep in mind is that sometimes you won't just have a tab, you'll also have a newline until it, so ```<think>``` and then an enter in that box. This ensures that only the tag by itself followed by a new line will trigger the prefix parsing. This stops accidental tags in the CoT from prematurely ending your reasoning!

Separator is always left empty.

Below that is the Start Reply With (commonly abbreviated to SRW) field at the very bottom. This is a way to brute force reasoning into working by telling your llm to start it's response with whatever you enter in that field (usually the same thing as your prefix earlier). That way it'll always start with a thinking block! This is very useful for most "non-thinking" models, but can seriously break reasoning models, so it's always one of the things we'll ask you to tell us!

---

### Question 5. What is your assistant prompts section in Lucid Loom set to?

This is the first Lucid Loom specific question! Yes, that means the first 4 are universally useful if you want to find out about fixing reasoning settings!

*The assistant setting can be found in the left hand chat completions prefix window. It's the section all the way at the very bottom of the prompt manager.*

<img width="399" height="578" alt="image" src="https://github.com/user-attachments/assets/5e75b08a-9604-466c-a0f3-93b56cced33d" />
*The most common setup for CoT's can be seen above.*


Under there you will find all the CoT checklists for Lumia (the guidelines of what she is thinking through). It's very important for us to know what you have toggled on down here to know how your Lumia is thinking. This means, what CoT you have on (Cot Zipbomb? Reasoner Zipbomb? CoT Normal? Assistant or System?). You will only want to have one CoT on at a time, and which one you have on is essential for whether your model will work properly, hence we will usually ask you what you have on or just tell you which one to turn on.

*Additionally for 3.0, we will want to know if you dragged Chat History down here from the first section (Story Primers). A lot of problems can be fixed in v3.0 by dragging down chat history to just above your chosen CoT!*

Lastly for a couple models (GLM and Qwen), there is an optional /think toggle that enables thinking. If you want to ask about those two models, make sure it's on, otherwise, make sure it's off.

---

## What next?

After you tell us these settings, somebody may point out settings you should change, if you do, I do suggest you write them down somewhere and then SAVE your current settings and maybe duplicate your preset to make changes to a new copy. If you are feeling too lazy to do that, just try and remember what your old one was just in case you want to go back. If your old ones never worked, then you don't have to bother saving them, naturally!

Any changes you make will not "stick" until you hit the SAVE button by the preset name up top in the preset tab. Unless you hit save, any changes you make will instantly go away if you refresh the sillytavern page, handy for temporary testing you want to quickly undo but bad if you forget to save the changes that made your preset finally work right with your model!

## Any other questions?

Don't hesitate to ask in the Lucid Loom channel for help, the more questions we answer, the more future people we get to help us experiment when Google/Cohee/Sillytavern/Level3/Mercury in Retrograde break something else later and we have to scramble to fix it!

## Why did you make this?

I have a problem.
