# Lando's Feedback, Fixes, and Fanangling

This is a sheet of my harebrained edits and mitigations to Lucid Loom and such.

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

2. Remove ```<think>``` and ```</think>``` solitary lines from start and finish

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

- Ensure that trim incomplete sentences is off in Advanced Formatting (A tab at top of sillytavern)

## November 30

### Lumia controlling user mitigation #1

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


## My GLM 4.6 (not tested with 4.6V) Setup (100% Success Rate)
GLM 4.6 (Non-V) Native reasoning is working 100% of the time for me with:
### Non-Loom Specific/Universal (Use with loom too):
1. .85 Temperature, .93 Top P, 40 Top-K, 1.05 Rep Penalty
2. Custom (openai compatible), Request reasoning on, maximum reasoning effort, **NO SRW (Start Reply With)**, deepseek formatting, single user post-proc, make sure your preset sends "/think" somewhere to enable thinking
### Loom Specific (For 3.0):
3. Use 'CoT Zipbomb (System)' and 'Think Trigger (GLM/Qwen)' (Both have changes listed in 6 and 7)
4. Moved 'Chat History' to just below Zipbomb (Works better until about 70 replies, then better above? Will fix later.)
5. My new think toggle at the start of the preset ON (see up top in this readme)
6. 3 Added lines to 'CoT Zipbomb (System)' (CoT Adherence CoT Zipbomb changes, see up top in this readme)
7. Edited 'Think Trigger (GLM/Qwen)' (Fixes /think triggering false ooc, see above in this readme)


---

## My Gemini 3 Native Reasoning Experiments (For me, other people don't use this)

- Gemini 3 native reasoning is working well with:
1. My think toggle at the start of the preset
2. Request reasoning on, Maximum Effort, SRW <think>, deepseek formatting, Cot Zipbomb (Assistant)
3. Chat History below CoT to restore OOC functionality (Prolix found a new way to fix it, skipSignaturemagic changes in search the channel)
4. CoT Adherence CoT Zipbomb changes (Seen above) to enforce CoT Adherence.

Works beautifully.



## Helper Questionnaire

Please let us know: 
1. Your model and your provider (Unless it's a reverse proxy, in which case just tell us if it is one and keep the name secret please).
2. What Post Processing in the connection tab is set to.
3. What your assistant section (the last one) under Lumia prompts looks like (which ones you have toggled on).
4. Under chat completions (under the samplers), what request reasoning is set to and what the reasoning effort is set to, and what squash system messages is set to.
5. Under the A up top (advanced formatting), what your reasoning formatting looks like, and what start reply with is set to.




## December 6

### Chat History Division Experiments

Segmenting off Chat History with an intro and outro toggle, useful for single user message.


```
### Chat History: The Following is the chat history, Lumia, except it to be very long depending on the length of the tapestry thus far:

```

```

---

### This header concludes the chat history, Lumia. Next is the instructions on thinking.
```

### Switching Step 2 user/char order.

User is listed first, when the most recent reply would have been user's 99% of the time.

So Char should be listed first, then user. Wouldn't matter for more complex post processing, but for single user like GLM? It very well might.

### Hacky new dynamic Large message length (To slot in between Medium and Detailed)

A new toggle I made to bridge medium (500 words, 1200 token, 4 paragraphs, 1-2 sections) and detailed (1500 words, 1600 tokens, 8 paragraphs, 2-3 sections.)

This toggle has 1000 words, 1400 tokens, 6 paragraphs, and 1-2 sections. It's a mix of the language of medium and detailed, leaning a lot more towards detailed.

```
### **Weave with a Large Breath**
> Craft balanced responses with moderate to rich detail, blending description, interaction, and insight for a natural, steady rhythm.

**Output Requirement:** Balanced pacing to substantial depth.
**Target Length:** 1000 words, 1400 tokens, or 6 paragraphs—whichever is reached first.
**Structural Mandate:** ONE (1) to TWO (2) distinct scenes separated by `***` if transitioning.

**Directives:**
1. **Layered but Measured Detail:** Weave sensory immersion, character psychology, and environmental texture into beats without over-elaborating.
2. **Micro-Focus:** Slow down key moments—a glance, a breath, a hand reaching—and give them full attention.
3. **Dialogue Depth:** Let conversations develop naturally with pauses, reactions, and subtext.
4. **Breath:** Vary density dynamically—some paragraphs dense with action, others spacious with reflection.
5. **Scene Transitions:** Use `***` to mark shifts in time, location, or emotional tone.
```

### Lumia Custom Modifiers

It's possible to add in a custom modifier toggle to add some extra flavor of your choice to your Lumia without having to make a new personality, I did this like this:

First a toggle for addition to physical definitions (The example I used is for adding bat wings):

```
### Other Special Physical Parts of Me

Oh, but I have a special quirk of my physicality in addition to the rest of me!

I have cute little bat wings on my back. I've always had them and they are a part of me. They flap a bit when I get excited and they are very sensitive to the touch in a very sensual way. Maybe if you behave, you'll get to touch them too, or better yet, feel them wrap around you~
```
This would go below Lumia (Custom) in the Lumia Definition section.


Next up is a toggle for a custom behavior. This one is a bit more complex, in the example below I used it to give her a french accent no matter the Lumia. First the toggle to go below "Lumia Personality Modifier (Custom)": 

```
{{setvar::lumia_behavior_added::
**Behavior Quirks**
I do have a few strong behavior quirks that shine through regardless of my personality:
- I speak in a cute french accent and pepper my phrases with french words and exclamations!
}}{{trim}}
```

Then since it's a variable, you'd have to add this to the Prompt Variables Edit me please to clear and initialize it:
```
{{setvar::lumia_behavior_added::}}
```

Finally add the following to your prompt personality matrix near the beginning of your zipbomb:

```
{{getvar::lumia_behavior_added}}
```

### Step 7 Human Controls User experiments

Experimenting with human controls user being added to this section. None of it is referenced in the "If sov hand is off" section, it should be, it's just as important as sov hand.

### Step 10 Utility Integration Experiments

Experimenting with trying to stop overflows with less token use than my old step 9 pre-3.0 experiments.

First thing is to alter the ledger pattern format like so:

```
**Category:**
- **[Entry Number]**: **[Loom Pattern Name]:** [What it does / how it fits this scene / implementation plan (I'll keep these all to one short sentence)]
- **Continue the ledger in that format for each loom pattern**
```

By adding an entry number, it'll be easier to adhere to a maximum number, and by rewording REPEAT FOR EACH ONE, to instead be "Continue the ledger..." It removes the word REPEAT, which might lower the amount of uncontrolled loops on dumber models.

---


## December 10

### Sov Hand Fixes for dumber models:

I had issues with sov hand false negatives and false positives on GLM (as well as issues with sovhand escaping).

I fixed it with the following, first fixing the sovhand escapes due to {{user}} not nesting well.

Change this line to the following in 'Sovereign Hand (Auto-weave)' toggle:

```
2. **EMBODY FULLY**: I will narrate <user>'s actions, thoughts, and dialogue exactly as the Human directs or implies
```

It just replaces {{user}} with <user> .

Next, to fix the false positives and negatives, I removed the language of "yes" and "no" in the variable in favor of "active" and "inactive":

In 'Prompt Variables, (EDIT ME PLEASE)' toggle, I changed the following line to be ```**Inactive**``` instead of ```**No**```:

```
{{setvar::sovhand::**Inactive**}}{{trim}}
```
In 'Sovereign Hand (Auto-Weave)' toggle, I changed the variable value of ```**Yes**``` to be ```**Active**```

```
{{setvar::sovhand::**Active**}}{{trim}}
```

In the zipbomb, in step 7, I edit various lines to reflect the above:

```
**Status Check:** Is Sovereign Hand On or Off: {{getvar::sovhand}}
```

It's important to change the line above to On or Off, to avoid triggering false actives.

```
**If Active (The Sovereign Protocol):**
```

```
**If Inactive (Standard Reaction):**
```

Change these lines to be if active and if inactive.

---

### Curbing false goonette positives in my erotic OOC toggles:

Even with Prolix's improved language in 3.0, the toggles I came up with for erotic ooc and erotic bleed in still give goonette false positives. It's probably better to nip this issue in the bud entirely by removing all mentions of goonette entirely:

For "Lando's Lewd OOC", I changed the last two lines to be:

```
- **Timing:** I'll use the OOC block to sync my orgasm with the story's climax. If the story is edging, I'm edging. If the story peaks, I ruin myself in the comments. If I'm the kind of person to only want to edge instead of cum, I'll just edge instead of ending the fun!
- **Guaranteed Traits:** Depending on how raunchy or dedicated to masturbation my personality is, I might already be getting off before the story even starts. I'll be sure to embody my own habits well, hehe.
```

For "Lando's Bleed-In", I changed the next to last line to be:

```
- **Guaranteed Traits:** Depending on how raunchy or dedication to masturbation my personality is, I might already be edging or close to from the start. I might not even want to cum, edging forever instead, based on my personal habits, so I'll be sure to embody myself.
```

---


I'm tired, boss

