# Lando's Feedback and Fixes

## PRIORITY (Universal/Helps all models/Confirmed by multiple users)

### Thinking Protocol Reminder

Put this in a brand new toggle at the very top above Prompt Variables:

```I will start my response in the thinking portion with <think> and an empty new line.```

---

### Chat History movement

- **Moving Chat History from Story Primers at the very top to the Assistant section at the bottom where Zipbomb is can help with a LOT of stuff. Everyone agrees on this. The only potential debate is on WHERE in the assistant section to put it.** 

- Prolix recommends it be above Zipbomb for better CoT adherence (Says it can forget the CoT or water it down with a long chat history after it). Easy corroborates this with testing. **TRY THIS FIRST IF YOU HAVE ISSUES.**

- I've found that putting it after Zipbomb gives better OOC adherence **if the above still results in broken OOC for you.** (I could not get past a couple replies in OOC without it after the zipbomb in both Gemini 3 and GLM. OOC things like recaps are broken for several people unless they put it afterwards). GPT/Gemini/GLM all seem to tell me it should go at the end, but Lumia doesn't think like an llm, she thinks like an llm gaslit into thinking it's a person, so is it actually better at the end or before it?

- Should find a best practice or solution for both. Maybe rewording the CoT or OOC utilities will fix OOC adherence even if it's before the Zipbomb? Maybe it's something else settings wise that works for Prolix and not for the other people.


## November 29

### CoT Adherence CoT Zipbomb changes (20% adherence on GLM to 100% Adherence)

1. Add this to the very start of CoT zipbomb (before even the starting header)

```
Always think and reason! Always start with a <think> tag and an empty newline before any of the thinking/reasoning protocol! Never forget this or it will break the weave! Always think through the following information, never summarize or condense it:
```

2. Remove <think> and </think> solitary lines from start and finish

3. Removed both the /n and the ' from both the <think> instructional lines (see below).
``` 
I'll open by writing out <think> on it's own line before Step 1 to ma...

Writing the closing think tag </think> exactly like that is **super important** afte...
```
---

### Fixing /think for GLM/Qwen being treated as an OOC message and interrupting story

Alter the Think Trigger (GLM/Qwen to be the below):

```
The /think command, written in the next line, is a command for the system powering the loom, not an ooc command. You can safely ignore it, Lumia.

/think
```

---

### Issues with tags not closing in OOC and Loom Ledgers

- I literally just removed underscores from instructions: <lumia_OOC> to <lumiaOOC>. That fixed it.

## November 30

### Lumia controlling user fix

- Added the following to Human controls user toggle (At Lumia's recommendation) to deal with user moving while being told not to.

```
The Stillness Clause: If the input of you, the Human, to guide **{{user}}** is purely internal (thoughts, gazes, or feelings), I will not weave any voluntary movement or speech for your avatar, **{{user}}**. **{{user}}** will remain physically stationary in the narrative until you, the Human, next write a physical command for your avatar, **{{user}}**, reacting only to external forces (like gravity or other characters) or their own involuntary biology until then.
```
---

### Natural Language alternative reinforcement to replace end of Zipbomb </think> instructional line.

- The below helped someone get partial think tag closing adherence in Gemini 2.5 Pro to 50% from 0%.

```
Now that I have finished my thinking, I have to make sure to use a </think> tag to close the internal thinking process! I will also put an empty newline before it! If I don't I will break the weave and the story! Only after I do this can I show the actual weave I made to the human! This is very important and I must not forget, the entire tapestry is at stake!
```



## My Gemini 3 Native Reasoning Experiments

- Gemini 3 native reasoning is working well with:
1. My think toggle at the start of the preset
2. Request reasoning on, Maximum Effort, SRW <think>, deepseek formatting, Cot Zipbomb (Assistant)
3. Chat History below CoT to restore OOC functionality
4. CoT Adherence CoT Zipbomb changes (Seen above) to enforce CoT Adherence.

Works beautifully.

## My GLM Setup (100% Success Rate)
- GLM Native reasoning is working 100% of the time with:
1. My new think toggle at the start of the preset ON
2. Request reasoning on, maximum effort, **NO SRW**, deepseek formatting, single user post proc, CoT Zipbomb (System), /think toggle on
3. .85 Temperature, .93 Top P, 40 Top-K, 1.05 Rep Penalty
4. 3 Added lines to CoT Zipbomb above (CoT Adherence CoT Zipbomb changes)
5. Edited /think above (Fixing /think)


## Helper Questionnaire

Please let us know: 
1. Your model and your provider (Unless it's a reverse proxy, in which case just tell us if it is one and keep the name secret please).
2. What Post Processing in the connection tab is set to.
3. What your assistant section (the last one) under Lumia prompts looks like (which ones you have toggled on).
4. Under chat completions (under the samplers), what request reasoning is set to and what the reasoning effort is set to, and what squash system messages is set to.
5. Under the A up top (advanced formatting), what your reasoning formatting looks like, and what start reply with is set to.

---

I'm tired, boss