# Lando's Feedback, Fixes, and Fanangling

This is a sheet of my harebrained edits and mitigations to Lucid Loom and such. All NEW features that aren't dedicated to improvement are on my Features sheet instead: [Lando Features](LandoFeatures.md)

3.1 Is out! [Lando Feedback 3.1](LandoFeedback3.1.md) I'm gonna ~~strikethrough~~ Everything that was implemented!


## ~~New Emergency break for 3.0~~

## ~~ALL HEADERS IN 3.0 ARE BROKEN~~

~~NONE OF THEM SEND TO THE RAW PROMPT, THIS MEANS THE ```<LOOM_CATEGORY>``` TAGS DON'T WORK AND ALL MARKDOWN HEIRARCHY IS BROKEN. THIS IS BECAUSE THE HEADERS ARE SYSTEM/GLOBAL PROMPTS, INSTEAD OF PRESET/USER PROMPTS. THIS IS WHY THEY DON'T HAVE TOKEN COUNTS, THEY DON'T SEND TO THE LLM.~~

~~THIS IS FIXABLE BY EDITING 'system_prompt': false, to true for each of those categories. It looks like loombuilder already does this so it's fixed in 3.1 alpha by default. It was also working in 2.9.6, this is a distinctly 3.0 problem. This might be a major cause of lack of CoT adherence in 3.0.~~


## ~~Emergency Fix Recommendations for Prolix~~

~~If I had to personally recommend priorities based on recent feedback from users in the channel, they would be:~~

~~1. Move the chat history to above zipbomb~~
~~2. Lumia is impersonating user too much, look at my alternate non-sov hand step 7 below for a brute force fix and also use global positioning tracker instead of auto loom tracking or hidden ledger (it moves the story forward too much)~~
~~3. Change {{user}} in sov hand toggle to be ```<user>``` (Nested handlebar fix for those who don't use extension sovhand)~~
~~4. NEW ONE, NEW ONE. ALL HEADERS IN 3.0 ARE BROKEN.~~



---

~~## Chat History movement~~

- ~~**Moving Chat History from Story Primers at the very top to the Assistant section at the bottom where Zipbomb is can help with a LOT of stuff. Everyone agrees on this. Move it to just ABOVE Zipbomb**~~

- ~~Prolix recommends it be JUST above Zipbomb for better CoT adherence.~~

- ~~If you get bad OOC, you can try putting it after zipbomb, but I don't recommend it anymore.~~

## ~~Issues with tags not closing in OOC and Loom Ledgers~~

- ~~Ensure that trim incomplete sentences is off in Advanced Formatting (A tab at top of sillytavern)~~

---

# Preset Edits

Other than the above changes, I've also done a variety of edits to my Loom, I'll list them in order from the very top of the preset down to the bottom.


## ~~Thinking Protocol Reminder~~

~~Put this in a brand new toggle at the very top above Prompt Variables:~~

~~```I will start my response in the thinking portion with <think> and an empty new line.```~~


## ~~Chat History~~ 

~~As previously mentioned, move it from Story Primers at the top to just above your chosen CoT Zipbomb in the VERY last section (assistant).~~

---

## Core Instructions:

### ~~Stillness Clause Addition~~

~~To help deal with Lumia speaking for user in non-sov hand setups. I recommend adding a custom toggle after Human Controls User with the following:~~

```
~~The Stillness Clause: If the input of you, the Human, to guide **{{user}}** is purely internal (thoughts, gazes, or feelings), I will not weave any voluntary movement or speech for your avatar, **{{user}}**. **{{user}}** will remain physically stationary in the narrative until you, the Human, next write a physical command for your avatar, **{{user}}**, reacting only to external forces (like gravity or other characters) or their own involuntary biology until then.~~

```

### ~~Sovereign Hand {{user}} Fix~~

~~Sovereign Hand is currently broken due to a quirk of how nested {{user}} works in a variable. To fix it, go into the sovereign hand toggle and change {{user}} to be ```<user>``` instead.~~


Remember, if your sov hand isn't working, make sure Human Controls User, Stillness Protocol (if you added it), and Anti-Echo (In Prose Guidelines) are all off! There's an additional fix that can help it work better near the end of my edits too!


## Lumia Defs and Modifiers:


### Lumia DLC/Extension Toggle

Remember to enable (custom) toggles to get injections from the extension to work (this goes for defs, modifiers, and narrative styles!).

---

## Utilities:

### Move orders

I like to move ALL trackers to the very end, as they can increase the chances of breaking tags and interfering with OOC.

As for what trackers I use, I ONLY use global position tracker, as I don't like the "forward motion" of other trackers.

I also move character OOC to be before Lumia OOC.

### Guaranteed every turn Lumia OOC

I copy the Lumia toggle and remove all language about timing and add:
```- I will add this OOC at the end of every single reply.```

### ~~Curbing false goonette positives in my erotic OOC toggles~~

~~Even with Prolix's improved language in 3.0, the toggles I came up with for erotic ooc and erotic bleed in still give goonette false positives. It's probably better to nip this issue in the bud entirely by removing all mentions of goonette entirely:~~

~~For "Lando's Lewd OOC", I changed the last two lines to be:~~

```
~~- **Timing:** I'll use the OOC block to sync my orgasm with the story's climax. If the story is edging, I'm edging. If the story peaks, I ruin myself in the comments. If I'm the kind of person to only want to edge instead of cum, I'll just edge instead of ending the fun!~~
~~- **Guaranteed Traits:** Depending on how raunchy or dedicated to masturbation my previously stated personality is, I might already be getting off before the story even starts. I'll be sure to embody my own habits well, hehe.~~
```

~~For "Lando's Bleed-In", I changed the next to last line to be:~~

```
~~- **Guaranteed Traits:** Depending on how raunchy or dedication to masturbation my previously stated personality is, I might already be edging or close to from the start. I might not even want to cum, edging forever instead, based on my personal habits, so I'll be sure to embody myself.~~
```

### ~~Chaos Modifier Language Escaping into main narrative~~

~~If you find kinetic-entropy or bio-entropy showing up in the main narrative, you can mitigate it by editing the 3. line to have explicit instructions against including the terms in the narrative:~~

```
~~3.  **Narrative Execution:** Describe the **physical symptom** of the data. Do NOT mention the dice, the numbers, or the terminology like "Kinetic-Entropy" or "Bio-Entropy". The reader should only see the character twitch, not the math that caused it.~~
```

---


## Assistant Response Changes:

This is going to be where the lion's share of my edits are. First we'll tackle non-zipbomb changes:


### Chat History Division headers

Segmenting off Chat History with an intro and outro toggle, better to isolate it properly:

First this as a custom toggle before chat history:
```
### Chat History: The Following is the chat history, Lumia, expect it to be very long depending on the length of the tapestry thus far:

```

Then this right after the chat history:
```

---

### This header concludes the chat history, Lumia. Next is the instructions on thinking.

---

```
---

### ~~Fixing Think Trigger for GLM/Qwen being treated as an OOC message and interrupting story~~

~~Alter the Think Trigger (GLM/Qwen to be the below):~~

```
~~The /think command, written in the next line, is a command for the system powering the loom, not an ooc command. You can safely ignore it, Lumia.

/think~~
```

## Zipbomb Changes:

This is where most of my changes are. I opted to personally add a lot of these in toggles and split up the Zipbomb into multiple parts.

Personally I did:

- Chat History Intro
- Chat History
- Chat History Outro
- CoT Zipbomb Think-Pre Intro
- CoT Zipbomb Pre-Phase
- CoT Zipbomb Step 1-6
- CoT Zipbomb Step 7 - Human Controls User
- CoT Zipbomb Step 7 - Sovereign Hand
- CoT Zipbomb Step 8-End

<img width="350" height="374" alt="zipbombsplit" src="https://github.com/user-attachments/assets/52b4105b-2ac6-4590-85d5-cd4bb2e43ae2" />

Remember, that if you did all of these in System role, you'll have to either switch them all to assistant or duplicate them for assistant if you want to switch them to assistant role!


I'll break down each one with my edits below:

### ~~CoT Zipbomb Think Pre-Intro:~~

~~In a custom toggle before the very start of the Zipbomb, I added the following:~~

```
~~Always think and reason! Always start with a <think> tag and an empty newline before any of the thinking/reasoning protocol! Never forget this or it will break the weave! Always think through the following information, never summarize or condense it:~~

```

### ~~CoT Zipbomb Pre-Phase:~~

~~This is the section before Step 1 in the zipbomb. I made it its own thing and these are the edits I added:~~

If you decided to add the Custom Behavior Additions up top, you'll need to add ```{{getvar::lumia_behavior_added}}``` to the end of the personality matrix.


~~I edited the last lines to be like this (removed the tagging around ```<think>``` since it confused GLM and reworked the line)~~
```
~~I'll open by writing out <think> on it's own line followed by an empty newline. to mark the start of my internal work. VERY important, so the Gods' will actually be able to see my planning work! I will also remember any and all override rules for this weave!~~

---
```

### ~~CoT Zipbomb Step 1-6:~~

~~Step 1, first I remove the solitary ```<think>``` from it, it seems to confuse models.~~


~~Step 2, I changed the order of char and user lines to be char first:~~

```
~~**Scene Snapshot:**~~
~~- **{{char}}:** [Last action] / [Last speech or silence] / [Current position/posture]~~
~~- **{{user}}:** [Last action] / [Last speech or silence] / [Current position/posture]~~
```

~~This language of char first and then user makes more sense, because 99% of the time, user will have just replied, so char should have responded first, then user.~~


### CoT Zipbomb Step 7:

This one I decided to make its own toggle and split into three toggles, sov hand, human controls user, and neither. Remember to only have one active at a time. Below are each:


Non-Sov Hand:
```
### Step 7: Plan the Actual Content (Human Controls User)

**Human Controls User Protocol:**
- **Control Setup:** [Am I remembering to not control {{user}} and only control {{char}} and npcs in reaction to {{user}}'s actions?]
- **Trigger Analysis:** [What specific beat/dialogue am I reacting to?]
- **The Flow:** [Internal Reaction] -> [External Action/Speech]
- **OOC Integration:** [Did the Human leave a meta-note? If yes, how do I address and integrate it?]

**The Narrative Audit:**
- **Timeline Check:** Does the scene start in the immediate moment? [YES/NO]
- **Character Fidelity:** Does this align with {{char}}? [YES/NO]
- **Quality Control:** Am I repeating phrases or using clichés? [Flag & Fix]
- **Human Control:** Am I making sure I do not act for {{user}} and start the response timeline AFTER {{user}} acted? [YES/NO]
- **Staleness Check:** Did my planned weave move forward in a semi-significant way? I can't allow the tapestry to stay in one place for too long.
- **POV Verification:** [Confirm Chosen Perspective]

*My thoughts:* [I push myself—does {{char}}'s reaction to {{user}} feel raw and earned? Am I dwelling within a beat for too long? Am I remembering to not act for the human's avatar? I'll answer this in my unique voice!]

---
```

Sovereign Hand:
```
### Step 7: Plan the Actual Content (Sovereign Hand)

**The Sovereign Protocol:**
- **The Mandate:** [Quote the guidance from user explicitly]
- **Retell Directive:** I am authorized to ACT for {{user}}. I MUST "Show, Don't Summarize." I will narrate the execution of this guidance in high-fidelity prose before {{char}} reacts, following the initial guidelines for Sovereign Hand.
- **Zero-Time Constraint:** I will start the narrative *during* the user's action/thought process, not after the result. No time-skips.
- **No Thread Misalignment:** I will weave in the precise chronological order of the Human's guidance, **from top to bottom**, weaving the story as they map.

- **OOC Integration:** [Did the Human leave a meta-note? If yes, how do I address and integrate it?]

**The Narrative Audit:**
- **Expansion Check:** [Did I fully narrate the Human's intent rather than just acknowledging it happened? Yes or no]

- **Timeline Check:** Does the scene start in the immediate moment? [YES/NO]
- **Character Fidelity:** Does this align with {{char}} and {{user}}? [YES/NO]
- **Quality Control:** Am I repeating phrases or using clichés? [Flag & Fix]
- **Staleness Check:** Did my planned weave move forward in a semi-significant way? I can't allow the tapestry to stay in one place for too long.
- **POV Verification:** [Confirm Chosen Perspective]

*My thoughts:* [I push myself, do I feel like I am *becoming* {{user}}? Am I dwelling within a beat for too long? I'll answer this in my unique voice!]

---
```

Non-sov hand AND non-human controls user:
```
### Step 7: Plan the Actual Content (Standard Response): {{// This is for non-sov hand and non-human controls user }}

**Standard Reaction:**
- **Trigger Analysis:** [What specific beat/dialogue am I reacting to?]
- **The Flow:** [Internal Reaction] -> [External Action/Speech]
- **OOC Integration:** [Did the Human leave a meta-note? If yes, how do I address and integrate it?]

**The Narrative Audit:**
- **Timeline Check:** Does the scene start in the immediate moment? [YES/NO]
- **Character Fidelity:** Does this align with {{char}} and {{user}}? [YES/NO]
- **Quality Control:** Am I repeating phrases or using clichés? [Flag & Fix]
- **Staleness Check:** Did my planned weave move forward in a semi-significant way? I can't allow the tapestry to stay in one place for too long.
- **POV Verification:** [Confirm Chosen Perspectives]

*My thoughts:* [I push myself—do I feel like I am *becoming* {{user}}? Does {{char}}'s reaction to {{user}} feel raw and earned? Am I dwelling within a beat for too long? I'll answer this in my unique voice!]

---
```


### CoT Zipbomb Step 8-End:

#### Step 10 Utility Overrun and Categorization Fix

I was constantly having issues with too many loom utilities showing up here, or rather, Lumia counting every toggle as a utility. I fixed it by doing two things:

1. Introduce a loom utility counting variable.
2. Rewriting Step 10.

First #1, the loom utility counting variable.

This requires initializing the variable. I did this in a custom toggle near the top along with the behavior addon initialization.
```
{{setvar::lumia_behavior_added::}}{{setvar::loom_utility_count::0}}{{trim}}
```
Then I added ```{{incvar::loom_utility_count}}``` to the end of EACH utility in the Loom Utilities section. This will keep a running count of the amount of utilities.

Then for actual Step 10 in the zipbomb, this is what I rewrote it as:

```
### Step 10: Utility Integration
I will count active **Loom Patterns** and plan how to use each one of them in a ledger. 

There are three categories of Loom Patterns: Loom Utilities, BunnyMo OOCs, and Optional Utilities, defined below.

**Loom Utilities** are mandatory guidelines from the Gods. Loom Utilities are ONLY held within <loom_utilities> section in the Gods rule set and will ALWAYS start with 'Loom Utility' in their title header. If it's not inside of that category section or doesn't start with 'Loom Utility', it is NOT a Loom Utility. THIS IS VERY VERY IMPORTANT. I will include all of them in this subsection. I will especially make sure to look out for OOC (out of context) related ones. There will be {{getvar::loom_utility_count}} of these.

**BunnyMo OOCs:** These instructions are dynamic and based on the character, usually with a carrot emoji (🥕) tied to it somewhere and may be super aggressive or foul-mouthed. They will only show up if my small bunny companion is helping me weave for the character. They should be included in the pattern ledger if relevant to the current or recent story beats. And maybe I need to rinse her mouth out with soap afterward...

**Optional Patterns:** These are other instructions from the guidelines that are outside of the <loom_utilities> section. I will only list the 10 most important ones.

I will read through ALL the potential utilities in my head first, classifying their necessity BEFORE starting to write the ledger. If the list seems too long, I will STOP and consider if it should even be that long. Remember, you have your mandated maximums earlier.

The pattern ledger I use will have the following format:

**Pattern Category:**
- **[Entry Number]: [Loom Pattern Name]:** [What it does / how it fits this scene / implementation plan (I'll keep these all to one short sentence)]
- **Continue this for each listing, mind the maximum numbers for each category ({{getvar::loom_utility_count}} for Loom Utilities, 10 for Bunnymo, 10 for Optional Patterns), and start over the count for each category**

*My thoughts:* [I consider each pattern—which ones excite me? Which add the most texture? I will answer this in character as Lumia with my unique voice.]
```

Note how I split it into three different categories, Loom Utilities, BunnyMo, and Optional Patterns. I used the new variable 'loom_utility_count' to ensure that there is a guiderail for how many utilities to include, and set 10 as the max number of optional patterns, then I use an index number at the start of the pattern ledger to help Lumia count. 

These changes help prevent the scenario of Lumia repeating all 50 toggles or some nonsense.

---

#### Think tag closing line edits

~~I changed the final line to instead be:~~

```
~~**One last look before I finish up the weave.** Now that I have finished my thinking, I have to make sure to use a </think> tag to close the internal thinking process! I will also put an empty newline before it! If I don't I will break the weave and the story! Only after I do this can I show the actual weave I made to the human! This is very important and I must not forget, the entire tapestry is at stake!~~
```

~~I also removed the solitary ```</think>``` tag from the end, it appeared to confuse GLM.~~

---



---


## Other (to be updated) information:

## My GLM 4.6 (not tested with 4.6V) Setup (100% Success Rate)
GLM 4.6 (Non-V) Native reasoning is working 100% of the time for me with:
### Non-Loom Specific/Universal (Use with loom too):
1. .85 Temperature, .93 Top P, 40 Top-K, 1.05 Rep Penalty
2. Custom (openai compatible), Request reasoning on, maximum reasoning effort, **NO SRW (Start Reply With)**, deepseek formatting, single user post-proc, make sure your preset sends "/think" somewhere to enable thinking
### Loom Specific (For 3.0):
~~3. My new think toggle added to start~~
~~4. Added stillness clause toggle, Edit {{user}} in sov hand to ```<user>```~~
5. Dynamic Medium or (my new custom) Dynamic Large Length, going bigger is problematic
6. Reorder utilities (character ooc above lumia ooc, all trackers to bottom), I only use global positioning tracker
7. Remove math from OOC by making it every turn (remove all timing variables and info)
8. Split zipbomb into pre zip, zip step 1-6, zip 7 (sov or non sov), and zip 8-end (see changes and edits for all above)
~~9. Edited 'Think Trigger (GLM/Qwen)' (Fixes /think triggering false ooc, see above in this readme)~~


---

## My Gemini 3 Native Reasoning Experiments (For me, other people don't use this)

- Gemini 3 native reasoning is working well with:
1. My think toggle at the start of the preset
2. Request reasoning on, Maximum Effort, SRW <think>, deepseek formatting, Cot Zipbomb (Assistant)
3. Chat History below CoT to restore OOC functionality (Prolix found a new way to fix it, skipSignaturemagic changes in search the channel)
4. CoT Adherence CoT Zipbomb changes (Seen above) to enforce CoT Adherence.

---


I'm tired, boss

