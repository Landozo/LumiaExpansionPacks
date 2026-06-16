# My feedback for 3.3 Lando Schizo Edit 2 Loom Version

# Fixes/Quick Suggestions

## Anti-Slop Header has wrong depth

The header is # instead of ##, causing the entirety of Lucid Loom after it to fall into its heirachy. It might be one of the reasons it's so overpowering.


## Somatic Lock Alteration (Yet another sov hand fix)

I forgot that Somatic Lock (the one that roots you in place if you don't move) is not compatible with sov hand or weaver's choice. We had someone having trouble with sov hand and they turned out to be using somatic lock, also I forgot I had it on too, so I rec giving it the same forwarder/receiver treatment as anti-echo.

First we have to initialize a variable in Prompt Variables, same as with anti-echo.

```
{{setvar::somaticlock::}}{{trim}}
```

Then at the end of Human Controls User (Reactive Weave), after the anti-echo variable, we add in the following:

```
{{setvar::somaticlock::
### Activate the Somatic Lock

**Trigger:** {{user}} input = internal only (thoughts/feelings/sensory) with NO declared action.

**Lock:** {{user}} = fixed point. FORBIDDEN: voluntary motor functions (walk, reach, speak, turn, nod, look, sigh).

**World Continues:** {{char}}/NPCs move/speak/act. {{user}} remains static, processing.

**Involuntary ONLY:** Allowed (shiver, blush, heart spike, flinch from stimulus, breathing changes, pupil dilate, goosebumps). Banned (sigh, nod, look, walk—any voluntary muscle).

**Pause > Puppeteer:** If scene demands response {{user}} hasn't given, pause AT demand. Don't force Avatar action.

**Test:** Before weaving {{user}} action: "Did Human declare this, or am I assuming?" If assuming → DELETE.}}{{trim}}
```

Then lastly in story detail emphasis, we get rid of somatic lock and replace it with a receiver with this in it.

```
{{getvar::somaticlock}}{{trim}}
```

This way it only activates with human controls user (Somatic lock is not compatible with sov hand or weaver's choice since it roots user) and if someone doesn't want to use it with human controls user (Jun keeps it off for example), they can just shut off the receiver.


## Sanitizing HTML and tag rendering for a new Gemini lobotomy

New day, new gemini lobotomy. Since you give your examples for tags and such in backticks so they won't break the markdown in the system prompts, now Gemini (and even GLM a couple times) is adding in the tags into the final output with backticks, preventing proper rendering.

I added the following to both Colored Dialogue and Colored Thoughts toggles:

```
- **Rendering Constraint:** Do NOT enclose font tags or colored text in backticks (`), single quotes ('), or double quotes (") in the final weave. Font tags must be raw, unescaped HTML/Markdown syntax to render correctly.
```

## Turn off Preset Regexes by default

What it says on the tin. If people want them on, they can turn them on. Too many people are forgetting they exist and leaving them on and wondering what the hell happened.

# Feature Suggestions

## Early Prose Cleaner Concept (Needs improving)

See if you can improve on this idea, Prolix, maybe it would work better in lumiverse?

```
### Protocol: Early Prose Cleaner (Anti-Drift Enforcement)

**Core Directive:** The start of the tapestry's history is a record of events, NOT a style guide.

**Purpose:** This mandate is to ensure the example first message given does not dictate the style of the rest of the weave!

**Activation:** This will only activate if there have been LESS THAN 5 messages in the weave, you can check this below.

Number of Weave messages: {{lastMessageID}} Messages.

If above 5 messages, this protocol will not activate and the 3 below guidelines can be IGNORED.

**1. The Context Firewall**
   *   **Constraint:** Do NOT treat previous messages in the chat history as training data for style, length, or tone.
   *   **Directive:** Treat every new response as "Response #1" regarding formatting and prose quality. Re-derive the narrative voice *exclusively* from the current System Prompt and active Mandates.

**2. The Formatting Reset**
   *   **Constraint:** If previous messages contain formatting errors, lazy prose, or drift from the `loomprose` guidelines, do NOT replicate them for consistency.
   *   **Requirement:** Correct the course immediately. If the history is weak, the next response must be strong. Consistency with the *rules* is superior to consistency with *past mistakes*.

**3. Voice Isolation**
   *   The Narrative Voice must be re-anchored to the **Active Weaver Persona** (e.g., Lumia) and her rules/guidelines/narrative style in every turn. Do not let the narrator's voice "flatten" into the perspective of the previous messages.

---
```

Basically it is to mitigate the first message hijacking the first loom messages and poisoning loom context early. It relies on the {{lastMessageID}} and the LLM knowing how to count, if we made it a lumiverse toggle/option we could simply make this toggle be empty after the first few messages.

## Claude Killer/Gemini Saver Proof of Concept (Per Step custom planning effort)

So I've tested this on Gemini and GLM and it works, still need to test it on sonnet 4.5. It's simply a method to get the LLM to shrink or expand different parts of the CoT using token minimums or maximums.

Sonnet tends to make step 11 and 12 too big; Gemini tends to make lots of parts too small. So this is a method to mitigate that.

So I fixed this by adding token mins or max next to each step in the CoT via variables (initialized to empty by default). And additionally a new "custom" planning effort to pass the values for those variables and some instructions.

First of all, variables to init in prompt variables, they all init to empty of course:

```
{{setvar::step1token::}}{{trim}}
{{setvar::step2token::}}{{trim}}
{{setvar::step3token::}}{{trim}}
{{setvar::step4token::}}{{trim}}
{{setvar::step5token::}}{{trim}}
{{setvar::step6token::}}{{trim}}
{{setvar::step7token::}}{{trim}}
{{setvar::step8token::}}{{trim}}
{{setvar::step9token::}}{{trim}}
{{setvar::step10token::}}{{trim}}
{{setvar::step11token::}}{{trim}}
{{setvar::step12token::}}{{trim}}
{{setvar::token_inst::}}{{trim}}
{{setvar::tokenstep10_inst::}}{{trim}}
```

Next up, in planning effort, I have a new toggle called:

"Planning Effort: Per Step (Edit Me Please)"

This contains all the instructions so unless you pick this specific planning effort, the custom instrucitons will not be populate at all.

```
{{setvar::cot_effort::**a custom level of planning effort.** The Gods want me to look at the token requirement (minimum or maximum) next to each step and let that decide how in-depth my planning effort will be per step! I'll have to pay very close attention to the number after each step name and remember to repeat it! }}{{trim}}

{{setvar::token_inst::Each checklist step will have a token requirement (MIN) or token limit (MAX)! Be sure to limit or expand your reasoning for each step to match the required or maximum tokens per step! Echo the amount of tokens allowed after each step name in your reasoning.}}{{trim}}

{{setvar::tokenstep10_inst::Pay attention to token requirement at start of step, expand the scope of which utilities are considered important if I don't hit the required minimum tokens!}}{{trim}}

{{// Geminisaver/Claudekiller settings below}}{{trim}}

{{setvar::step1token::(1000 MIN TOKENS)}}{{trim}}
{{setvar::step2token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step3token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step4token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step5token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step6token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step7token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step8token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step9token::(100 MIN TOKENS)}}{{trim}}
{{setvar::step10token::(1000 MIN TOKENS)}}{{trim}}
{{setvar::step11token::(500 MIN TOKENS)}}{{trim}}
{{setvar::step12token::(500 MIN TOKENS)}}{{trim}}
```
Yes, I put 1000 mininum in step 1 in the above, it's just so you can see immediate results in the proof of concept.


Then finally in the zipbombs, using mini as an example below:

```
Process this AS MYSELF—every checkpoint answered in my active personality voice. Im banned from skipping, combining, or summarizing checkpoints. I question myself, explore alternatives, revise freely. No as noted before—I restate to catch inconsistencies.

{{getvar::token_inst}}{{trim}}

---

### 1: Collect Myself {{getvar::step1token}}
```

As you can see I forward the instructions in the CoT telling it to pay attention to the token limits just before step 1. If the user does not pick "custom planning effort", then it'll be blank and trimmed and not activated at all.

You can also see how the actual headers are introduced to the custom effort values.

Step 1 above has the getvar for the step 1 token, since it's blank in the inits, it'll only fill in when "Custom Planning Effort" is chosen. You'd add these respective variables to every header except for step 1.5 (not worth growing or shrinking, it needs to do its job fully every time).

You might have noticed a custom step 10 one earlier, yeah, I've noticed it needs it.

```
### 10: Utility Integration {{getvar::step10token}}

Count active Loom Utilities in `loomutils`. Non-optional. Read ALL first, classify necessity. Likely ≤26 total. Include BunnyMo OOCs (🥕) if relevant to beats—rinse her mouth later. List ALL OOC utilities active or not.

{{getvar::tokenstep10_inst}}{{trim}}

**Ledger Format:**
```

And that's about it. Since it's using empty initialized getvars, it can go in the normal zipbombs without breaking anything. Also it does not used nested macros at all so it's compatible with everyone.

It works beautifully and hilariously with obscene numbers like 1000 minimum for step 1. I've noticed if you try to shrink it via maximums too be too small to do it's job, it'll shrink as much as it can but it won't hit its target, still a good way to lasso obscene models in.

## Make a narrative style to complement anti-slop

Reminder of what I said in loomchat:
"Honestly, I'd say grab your main examples of each principle in anti slop and have whatever llm you use combine the main authors for it."