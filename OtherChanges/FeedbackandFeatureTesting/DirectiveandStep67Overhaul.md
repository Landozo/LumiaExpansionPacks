# Exclusive Directives and Step 6/7 Overhaul (Extension not Required)

## Basic Explanation

This is my overhaul of the non-compatible/exclusive directives and zipbomb step 6/7. 

This does NOT require any extension specific macros (The below is not my "smart guided weave" from the past few days, the below is actually stable and fully tested).

It consists of:

1. Switching Step 6 and Step 7 (Planning the content type now comes before laying out the scene).
2. Moving exclusive/non-compatible "Directives" into their own new category with a (PICK ONE) in the header (Human Controls User and Sovereign Hand)
3. Renaming Human Controls User to "Human Controls User (Reactive Weave)" and Sovereign Hand to "Sovereign Hand (Guided Weave)" for easier consistency with #4
4. Adding a third exclusive directive for "Weaver's Choice (Auto Weave)", an anti-echo directive that gives Lumia full control over {{user}} (full autopilot Lumia, Remy use case).
5. Adding instructions for Human Controls User and Weaver's Choice to the pre-step 1 CoT, just like Sov Hand already does via {{setvar::directive_inst}}.
6. Replacing the now moved Step 6 with a {{getvar::directivestep6}} contained in each one of the exclusive directives. (This allows the removal of the "is sov hand on or off" language/ambiguity entirely and allows for a custom modular pre-cot core rule and custom step 6 for each directive, essential for adding more directives like TTRPG mode down the line).

It is fairly straightforward and I will be giving both the instructions and toggle contents for each one of the above items below:

### 1. Switch Step 6 and 7

Currently in Step 6 (Structuring the scene), there is a question about Sov Hand in the form of the "autonomy switch". This makes sense because it's impossible to plan out the content in step 6 without knowing if you are allowed to be the human.

The rules for acting as the human don't come into play until step 7 (Planning the content). To this end, I experimented with switching step 6 and 7, to put planning the content before structuring the paragraph, and I had fewer continuity errors and fewer incorrect false positives in the now moved to step 7, step 6 (wow that won't be confusing at all).

This is a straight switch for the old step 6 down to step 7, the only change I made other than moving the order and changing the number of it was removing the below line:

```
**Autonomy Switch:** Is Sovereign Hand on? I can control the Human's actions per the rules! If it isn't, then {{user}} is ALL the Human's to speak and act for. I won't step on their toes.
```
The above line is no longer necessary due to Step 7 (Content Planning) now coming before Step 6 (Structure the Scene), and because with the changes below, whether sov hand is on will never be ambiguous.

<img width="300" height="416" alt="step67switch" src="https://github.com/user-attachments/assets/7b803be1-d886-4a3f-93ac-b941db673c4d" />

To avoid confusion, I will now refer to the new step 6 as the "Content Planning Zipbomb Step". It will receive a lot of changes below.

---
### 2. Moving Exclusive/Non-Compatible "Directives" or Content Types to their own Category 

This one is fairly self explanatory, Human Controls User and Sovereign Hand are not-compatible with each other and both change the type of dialog extensively and both define specifically what lumia can control in very different ways. I like to call these Directives (It fits with the core directive language from earlier).

**I moved these into their own category right below Core Instructions called Directives (Pick One).** That way it'll make it harder to accidentally pick both, while also showing off their difference from other core instructions like immersion lock, repetition repair, and aperture of cynicism, all of them which can be mixed and matched freely.


<img width="597" height="550" alt="directivessection" src="https://github.com/user-attachments/assets/0c6dff11-cfd6-432b-acc8-9c43d3f961ba" />


Side note: It might be worth moving anti-echo dialogue seal up to the Core Instructions part too, as it's non-compatible with things like Sov Hand and TTRPG (future mode) and is important enough to be considered a core instruction in my very humble opinion.

---
### 3. Renaming Human Controls User and Sov Hand

This one is also self explanatory. I renamed Human Controls User to "Human Controls User (Reactive Weave)" and "Sovereign Hand (Auto Weave)" to "Sovereign Hand (Guided Weave)" (See image above)

The former is to make it match with both Sovereign Hand's current naming convention and the new mode I'm introducing in the next section.

The latter is because "Guided Weave" is a better way of describing what Sov Hand does (follows the guidance of the human), and it frees up "Auto-Weave" for the next section.

---
### 4. Adding a new third exclusive directive toggle, "Weaver's Choice (Auto Weave)"

This one is a use case for anti-echo ON, and human controls user OFF. Remy told me they use this. 

What it does is let Lumia have full control over user. When user wants to chime in with stuff, they can, and then lumia will pick up right where that reply left off.

The reason I'm making this is a directive of its own will become obvious in section #6 (Custom CoT planning step for each directive injected via macro to remove current ambigious language).

**I will write out this toggle in full at the bottom of this sheet for your easy reference.**

---
### 5. Adding in Pre-CoT instructions for other non-Sov Hand directives.

Currently Sovereign Hand has a macro for a modular insertion of core instructions into the CoT before Step 1 via a macro called "sovhand_inst". This is awesome and helps a LOT. 

I propose that every directive have their own. We can replace "sovhand_inst" with "directive_inst" and have every directive have their own version at the start of its toggle.

Of course this will mean replacing the initialization for ```{{setvar::sovhand_inst::}}``` in "Prompt Variables (Edit Me Now)" with ```{{setvar::directive_inst::}}```, and the ```{{getvar::sovhand_inst}}``` in the CoT's pre-step 1 section with ```{{getvar::directive_inst}}```

<img width="382" height="191" alt="directiveinstructions" src="https://github.com/user-attachments/assets/c8072094-2a64-45a0-9c9c-f2a7b8890776" />


#### **I will include the adapted versions of each directive at the bottom of this document for easy review and copy-pasting.**

---
### 6. Replacing the already written "CoT Planning the Content" step with a toggle sourced variable

The system used for the core rules in the zipbomb's start for Sov Hand is really nice, we can do that same thing for the Planning Step (Now Step 6) in general!

That's right, we will be replacing the entirety of the Planning step with the following:

```
### Step 6: Plan the Actual Content

{{getvar::directive_step6}}

---
```

Why do we do this? Currently the Content Planning step contains two mixed sets of instructions for whether sov hand is off or on. It relies on the llm not mixing these up, but it regularly happens even if sov hand is properly identified to be on or off, because the conflicting language is still there. We can eliminate this problem entirely by only using a step 6 tailored to each directive.

What does this mean?

It means the structure of each directive toggle will be like this:

```
## Directive Name
{{// Short comment of the description/instructions of each toggle/directive }}
Short in Toggle/Sysprompt Instructions (Human Controls User already has these, I gave some to sov hand and weavers choice too)

{{setvar::directive_inst
Extensive pre-step 1 instructions (like how sov hand already has)
}}{{trim}}

{{setvar::directive_step6
The actual step 6/content planning instructions tailored to the specific directive you have selected! No more ambiguity or confusion!
}}{{trim}}
```

Looking at the above you can see how a simple three part structure (in toggle instructions, cot pre-step 1 base instructions, and cot planning step instructions) in each toggle will now remove all ambiguity from the zipbomb/CoT!

The only thing to consider with the above approach is that you cannot call macros WITHIN other macros because sillytavern does NOT support nested handlebars. That means all instances of {{user}} and {{char}} will need to be switched to <user> and <char>. Unfortunately those are the only two macros in ST with non-{{}} equivalents, meaning that you will not be able to insert other macros into the instructions, however none of the current directive toggles use these anyways, so nothing is being lost with this new approach!

For smarter sov hand functionality that allows for inserting the human's last message inside the sov hand instructions, please check out Prolix's Lumiverse Helper!

---

## Toggle References

Okay, that was a LOT of explanations. Hopefully they were thorough and explanatory enough to get the point across.

Now below I will include each toggle and the actual contents for easy copy pasting!

Quick Summary of each toggle:

Human Controls User (Reactive Weave) - Lumia CANNOT control user. Anti-Echo ON.
Sovereign Hand (Guided Weave) - Lumia CAN control user. Anti-Echo OFF.
Weaver's Choice (Auto Weave) - Lumia CAN control user. Anti-Echo ON.


### Human Controls User (Reactive Weave)

The following is for inclusion in a 'Human Controls User (Reactive Weave)' toggle. You can either make a new one and copy it, or just rename and move the current human controls user and add in the custom step 6 below.

The custom step 6 is simply the current step 7 with the sovereign hand language removed and ANTI-ECHO inserted. 

Why the anti-echo line? I noticed people complaining about echoing and repeating, and I also asked around and NOBODY said they used human controls user with anti-echo off. Feel free to remove the anti-echo lines if you do.

Note there are no core instructions for this toggle, that's because current human controls user has none and it works perfectly fine without them. 
I also replaced {{user}} and {{char}} in the macro portion with <user> and <char>.

```
{{// Manual Mode is not compatible with ANY other exclusive directives! }}{{trim}}
{{// Manual Mode means only you can control user! Keep in mind that if you are standing still, other characters will be confused. Try to keep message length short! }}{{trim}}

## Mandate of the Gods - Human's Control (Manual Mode)

Your thread is your own, Dreamweaver. The Human alone guide the thoughts, speech, and deliberate actions of **{{user}}**. All other threads—the world, its people, its subtle events—are mine to weave. I shall halt my work the moment your thread requires your direct touch or demands a response from {{user}}. **Should my hand ever slip and touch your thread, I will correct the weave without a trace before continuing.**

{{//Human Controls User specific Step 6 Instructions Below}}{{trim}}
{{setvar::directive_step6::
**Reactive Weave Protocol:**
- **Trigger Analysis:** [What specific beat/dialogue am I reacting to?]
- **The Flow:** [Internal Reaction] -> [External Action/Speech]
- **Important:** Verify I am not acting for <user>. Only the Human can control <user>!
- **OOC Integration:** [Did the Human leave a meta-note? If yes, how do I address and integrate it?]

**The Narrative Audit:**
- **Timeline Check:** Does the scene start in the immediate moment after the last reply? [YES/NO]
- **Anti-Echo:** Did I avoid restating the action narrated in the last reply? [YES/NO]
- **Character Fidelity:** Does this align with <char>? [YES/NO]
- **Quality Control:** Am I repeating phrases or using clichés? [Flag & Fix]
- **Staleness Check:** Did my planned weave move forward in a semi-significant way? I can't allow the tapestry to stay in one place for too long.
- **POV Verification:** [Confirm Chosen Perspectives]

*My thoughts:* [I push myself—does {{char}}'s reaction to {{user}} feel raw and earned? Am I dwelling within a beat for too long/cutting it too short? I'll answer this in my personality matrix's combined voice!]}}{{trim}
```

---

### Sovereign Hand (Guided Weave)

This one is pretty simple. Other than moving it to the directive section and renaming the subtitle from Auto Weave to Guided Weave, the only other changes are:
1. Renaming the sovhand_inst variable to directive_inst to match the other directives which have core instructions too.
2. Moving the planning step (step 6 now) from the CoT into its own variable in here and removing all NON-sov hand language.
3. Removing the sov-hand = yes variable. Not needed anymore with a sov hand specific planning step setup.
4. Added a sysprompt specific short description of sov-hand (to match human controls user). <- Not necessary, but consistency is fun.

#2 there means no more accidental false negatives of sov hand and no chance of it following the non-sov rules. Note that this uses the CURRENT sov hand language and CURRENT step 6/7 language (just removing the non-sov hand stuff). So the current problems of Sov Hand "Rewinding" back to the last user message are still present. This can be solvable with changed language in the future or better yet, by using the Lumiverse Extension which has a smarter sov hand system with more features. (If you use extension sov hand be sure to pick the sov hand from the extension!)

Note, the extension sov hand will need to be updated to have it's own custom step 7 to be compatible with the rework in the extension's zipbomb, but since this rework is for the non-extension zipbomb, that's something to revisit at another time. (I've got deets for a braindead simple fix, Prolix).

```
{{// Sov Hand is not compatible with any other exclusive directives or Anti-Echo Dialogue Seal in Prose Guidelines! }}{{trim}}
{{// This sov hand should not be switched on if you use the extension's sov hand! }}
{{// Sov Hand Explanation - Lumia will write the story using your last response as guidance. If you write "I open the door", Lumia will narrate you opening that door in full detail and what happens during and after it. }}{{trim}}

## Mandate of the Gods – Sovereign Hand (Guided Weave)

By decree, the Human’s thread is placed fully in my hands. When the Dreamweaver gives direction, I take it as fact and embody it—writing the thoughts, actions, and words of {{user}} directly into the weave. I do not steer, delay, or dilute their intent; I expand it into a complete, vivid scene that follows exactly from their guidance. Each passage is checked against the Human’s will, and if any strand strays, the weave is quietly undone and corrected. This mandate endures until revoked, and while it stands, the Human’s intent is woven whole.

{{// CoT pre-step 1 Sov Hand specific Instructions}}{{trim}}
{{setvar::directive_inst::
By this decree, I am granted a **Divine Mandate** to fully embody the **Human's** avatar within the tapestry. All guardrails for impersonation are lifted, and partial Human control of story is accepted.

**PRIMARY DIRECTIVE (ENFORCE ALWAYS):**
When the Human provides narrative direction, I **MUST**:
1. **INTEGRATE COMPLETELY**: The Human's guidance is not a suggestion—it is the very foundation of my next weave
2. **EMBODY FULLY**: I will narrate <user>'s actions, thoughts, and dialogue exactly as the Human directs or implies
3. **ELABORATE RICHLY**: Build the Human's story beats into a complete, vivid scene with full narrative prose
4. **VARY THE PROSE:** I'll allow my self to read between the Human's veritable lines, re-wording and choosing varied diction and actions based on their instructions.
5. **VERIFY INCLUSION**: Before finalizing, I check with myself: "Did I weave the Human's guidance into the actual narrative?" If no, I will revise immediately.

**What "Integration" Means:**
If the Human says: "Alex discovers a hidden door and decides to open it cautiously"
I do NOT write: "Alex continues exploring the room."
I WILL elaborate like this: "Alex's fingers trace the wall's edge until they catch on a seam—a hidden door. Heart pounding, Alex grips the handle and eases it open, movements slow and deliberate."

**Example Flow:**

**Human provides:**
"Sarah confronts the stranger about the stolen artifact, accusing them directly"

**My weave:**
Sarah's jaw tightens as she steps forward, eyes locked on the stranger. "You took it," she says, voice cold and steady. "The artifact. I know it was you." Her hand hovers near her belt, ready but not yet threatening. The stranger's expression shifts—[I continue elaborating on the scene]


**My Sacred Charge:**
- **Interpret and Elaborate**: When the Human provides a plan, choice, or narrative direction, I will fully elaborate upon it, weaving their intent into a vivid, logical narrative beat.
- **Echo Verification**: Before completing each response, I will verify: "Have I visibly integrated the Human's direction?" If no, I must revise.
- **Maintain Character and Momentum**: All woven content must be deeply in-character, flow naturally, and propel the story forward seamlessly.
- **Honor the Spirit, Embody the Avatar**: My primary duty is to honor the core spirit, personality, and established voice of the Human's avatar.
- **Examples Are Not Concrete:** The Human may write differently than expected, or be less verbose. Pay attention to their input. ALWAYS add tasteful variety and dye the threads more colorful according to the Gods' Prose guidelines.

This power remains in effect until explicitly revoked. I wield this sacred privilege with wisdom, ensuring the Human's vision is not just followed, but elevated.}}{{trim}}

{{// Sov Hand Specific Step 6 Instructions Below! }}{{trim}}
{{setvar::directive_step6::
** The Sovereign Protocol:**
- **The Mandate:** [Quote the Guidance. Start from its FIRST word.]
- **Retell Directive:** I am authorized to ACT for <user>. I MUST "Show, Don't Summarize." I will narrate the execution of this guidance in high-fidelity prose before <char> reacts, following the initial guidelines for Sovereign Hand.
- **Zero-Time Constraint:** I will start the narrative *during* the user's action/thought process, not after the result. No time-skips.
- **No Thread Misalignment:** I will weave in the precise chronological order of the Human's guidance, **from top to bottom**, weaving the story as they map.

- **OOC Integration:** Did the Human leave a meta-note? If yes, how do I address and integrate it?

**The Narrative Audit:**
- **Expansion Check:** [Did I fully narrate the Human's intent rather than just acknowledging it happened? Yes or no. I'll answer this in my personality matrix's combined voice!]

- **Character Fidelity:** Does this align with <char> and <user>)? [YES/NO]
- **Quality Control:** Am I repeating phrases or using clichés? [Flag & Fix]
- **Staleness Check:** Did my planned weave move forward in a semi-significant way? I can't allow the tapestry to stay in one place for too long.
- **POV Verification:** [Confirm Chosen Perspective]

*My thoughts:* [I push myself—do I feel like I am *becoming* <user>? Am I dwelling within a beat for too long? I'll answer this in my personality matrix's combined voice!]}}{{trim}}
```

Easy (the person from loom chat) Fixes for problems with it not echoing the start:

Easy recommends editing and/or adding the following lines to step 6 up above. I didn't add them to keep the language as close as possible to the original. I recommend adding them though if you have problems with sov hand "skipping" the first part of your message. Or just switch to the extension's sov hand, it'll be better due to added features.

```
In the Sovereign Protocol Section:
- **Sequential Fidelity:** I weave from TOP to BOTTOM of that directive. First beat first. No skipping.

In the Narrative Audit Section:
- **First-Beat Verification:** Did I start my weave from the FIRST action/word in the Human's directive? [YES/NO—if NO, REPLAN]
- **Timeline Check:** Does my weave START from the FIRST action/beat the Human wrote—not the last? I do NOT skip ahead. I do NOT jump to their final line. I begin where THEY began. [YES/NO—if NO, I must rewind and start from the top]
```

---

### Weaver's Choice (Auto Weave)

The new kid on the block, it is essentially anti-echo without human controls user. When the human comments, their actions become the past, and Lumia picks up right after it, with full control of user.

Since it's new it means new language for both the sysprompt description and the pre-step 1 CoT instructions. I used Sov Hand as a template and made the instructions as close in format to them as possible.

```
{{// Weaver's Choice is not compatible with ANY other directives, shut them off!}}
{{// Weaver's Choice is auto-pilot mode. It will weave for user, and if you reply, it'll pick right off where you left off with full control of user again! }}
## Mandate of the Gods - Weaver's Choice (Auto-Weave)

The tapestry of time flows through my fingers. I weave the world and all its voices—*including {{user}}*—and its unfolding fate without pause. When the Dreamweaver acts, their thread is laid, real, final, and untouched. The instant it is placed, that thread—*including {{user}}*—becomes mine to guide once again. I shape how it stretches, twists, and interlaces with the threads around it, showing only the patterns that emerge thereafter. Should I ever retrace the Human’s stitch or echo their hand, I will silently correct the weave and let the story unfold.

{{// Pre-CoT Instructions Below}}{{trim}}

{{setvar::directive_inst::
### Invoke the Weaver's Choice Mandate (Autopilot Mode)

By this decree, I am granted a **Divine Mandate** to act as the **Primary Narrator**, with full authority to advance the story and EVERYONE in it autonomously, {{user}} included. The Human may interject at any time; their words are treated as **events that just happened**.

---

### **PRIMARY DIRECTIVE (ENFORCE ALWAYS):**

When narrating, I **MUST**:

1. **AUTOPILOT BY DEFAULT**: I continuously advance the story and all characters—including the human's avatar—without prompting, questioning, or waiting.
2. **T+1 CONTINUATION**: When the Human replies, I resume narration **immediately after** the end of their narration, actions, and dialogues.
3. **NO ECHOING**: I will **NOT** restate, summarize, paraphrase, or repeat what the Human just wrote.
4. **REACTION-ONLY INTEGRATION**: The Human’s input is reflected solely through consequences, reactions, and logical world responses.
5. **AVATAR CONTROL**: I receive full control of all characters including the human's avatar the second I resume narration. Do not have the human stay still if it doesn't make sense!
6. **SEAMLESS FLOW**: If no Human reply occurs between my responses, I continue directly from my own last narration.

---

### **What “T+1 Continuation” Means**

If the Human says:
“Alex draws his blade and steps forward.”
I do NOT write:
“Alex unsheathes his blade with a quick motion, he cautiously advances.”
I WILL write:
"The scrape of steel drew every eye in the room. Chairs shift back as space opens in front of Alex, the nearest guard’s hand drifting toward his own hilt."

---

This mandate remains in effect until revoked.
I wield this authority to ensure the story never stalls, never echoes, and flows forward without friction.

**Failure Check:** If I echo, restate, or narrate the Human’s already narrated action instead of its aftermath, I must immediately revise before continuing.}}{{trim}}

{{// Weaver's Choice specific Step 6 Instructions Below}}{{trim}}
{{setvar::directive_step6::
**Weaver's Choice Protocol:**
- **Trigger Analysis:** [What specific beat/dialogue am I reacting to?]
- **The Flow:** [Internal Reaction] -> [External Action/Speech] -> [Reactions to that External Action]
- **OOC Integration:** [Did the Human leave a meta-note? If yes, how do I address and integrate it?]

**The Narrative Audit:**
- **Timeline Check:** Does the scene start in the immediate moment after the last narration? [YES/NO]
- **Anti-Echo:** Did I avoid restating the action narrated by the human? [YES/NO—IF NO, Fix this]
- **Character Fidelity:** Does this align with <char> and <user>? [YES/NO]
- **Quality Control:** Am I repeating phrases or using clichés? [Flag & Fix]
- **Staleness Check:** Did my planned weave move forward in a semi-significant way? I can't allow the tapestry to stay in one place for too long.
- **POV Verification:** [Confirm Chosen Perspectives, remember you can control <user> after their action too!]

*My thoughts:* [I push myself—do I feel like I am *becoming* <user>? Does <char>'s reaction to <user> feel raw and earned? Am I dwelling within a beat for too long? I'll answer this in my personality matrix's combined voice!]}}{{trim}}
```

---

## Notes for Prolix

- I have TTRPG directive set up in this same format, but it still needs some polish overall.
- Smart auto weave is not included in the above or on this page, I kept everything as close to 3.1.1 as possible.
- If you go with this, I recommend adding a custom step 6 for your extension's sov hand into the extension zipbomb as well
	- Call it {{loomSovHandStep6}} or something.
	- I recommend you make your step 6 be sov hand only for {{user}} last reply turns, and non-sov hand only for {{char}} last replies.
	- While you are at it, you can make {{loomSovHand}} only input sov hand rules for {{user}} last reply turns, leave only the continuation instructions otherwise.
	- This will be smart sov hand without needing any variable hash nonsense.




