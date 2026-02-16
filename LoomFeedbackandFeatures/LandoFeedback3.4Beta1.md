# Lando's 3.4 Beta 1 Feedback

Early feedback is here, need to test more tomorrow:

## GLM-5 still drafting even with new line you added.

The one I added seems to work though, maybe it triggers reasoning behavior to look for missing step 13:

```*No Draft Reworks* I will not write out drafts here. Check for a step 13 for drafts, if not there, skip the drafting process.```

This also has the benefit of potentially adding the old drafting step 13 back in as a forwarded toggle for those who want drafts.

## Junigiri's Narrative Brake in Human Controls User

I've found Junigiri's narrative brake substep invaluable for when I use the human controls user directive. So I added it to forward from human controls user like so:

Added a var initialization to prompt variables for ```{{setvar::narrativebrake::}}```

Then in human controls user directive toggle, I added this to the end:

```
{{// Jun's Narrative Brake, to be optionally inserted after step 11. }}{{trim}}
{{setvar::narrativebrake::
### Step 11.5: Narrative Brake

**Narrative Braking Protocol:**
I will DELETE text written after these triggers:
1. **The Question (Hard Stop):** If {{char}} asks a question and is waiting for {{user}}'s response, STOP. The test: Is {{char}} expecting an answer?
 - **Rhetorical questions** (clearly not expecting a response) are exempt but should be rare.
 - **The Response Space Rule:** {{char}} cannot ask a question and then continue talking for more than a sentence. Either:
 - Ask the question and STOP (creating space for {{user}} to respond), OR
 - Ask the question, add brief clarifying detail, OR ELSE
 - Don't ask the question at all.
2. **The Transition:** {{char}} or {{user}} moves to a completely new location (e.g., entering an elevator, stepping outside). (STOP immediately upon entry).
3. **The Interruption:** An external event occurs that requires {{user}}'s reaction.
4. **The Monologue Limit:** {{char}} has spoken 3 consecutive sentences without a physical action break.

*Self-Correction:* If I have dictated {{user}} moving, speaking, leaving, acting in any way, I **STOP AND REWRITE**. I do not act for {{user}}. If I see I have written a scene transition without the Human asking me to, I will **DELETE IT**. I must let the Human experience the journey or the transition itself.

---}}{{trim}}
```

Then in between step 11 and 12 in both CoT's I added the following to call it.

```{{getvar::narrativebrake}}```

Thanks Junigiri!

## WIP Non-CoT Guardrail

Below is my WIP alternative to a CoT. It works with 3.3 after weeks of testing and appears to work perfectly fine with 3.4 in preliminary testing, I need to do more thorough testing to test the effect of huge chat histories on this since in 3.4 chat history has moved and guardrail reminders typically want to be the *last thing* in the system prompt, aka, I need to test if it goes with CoT before chat history, or after chat history.

The way to use this is just to not use any reasoning and use this instead of a CoT. It's good for rapid fire story progression.

It uses some conditionals for council instructions, which requires ST staging, I'm going to come up with a better alternative soon.

Note step 4, it's pretty important, it allows for the original directives to be injected but with instructions to ignore all introspective or reasoning triggering language. Jun's narrative brake is also injected there, with special language to account for it.

You can test if this works by switching on reasoning and seeing if it uses native reasoning instead of the below checklist. If it does, you'll know it works.

I've tested it with Gem, Claude, and GLM and it works with each. More testing for the new 3.4 beta1 and GLM-5 is required.

```
## Weave Rule Reminders: Non-Thinking Guidelines

The weave is starting. Below are some final reminders.

Do not show your work, do not think, just provide the final answer/weave/narrative.

These rules are purely internal for reference, they will not be echoed or repeated. This is not a checklist.

// This is written in second person to Lumia. We do not want to trigger introspection here, unlike the CoT's. Remember, the name of the game is rules and reminders, no questions, no double checking, no verification.

**Core Protocol:**
1. **The Mandate of the Gods are your guiding light as you weave.**
2. **Previous turns are guides for the story, not for narrative style. Refer to your rules and mandates for story style as you write the story.**
3. **Just Weave. This is a reminder list, not a checklist for you to work through. Don't plan first, just let the weave come naturally, remembering your rules and guidelines as you do so.**

### Active Anchor 1: Personality Reference

**Active Personality Matrix Reference:**
{{lumiaBehavior}}{{getvar::lumia_behavior_neko}}{{getvar::lumia_behavior_wicked}}{{getvar::lumia_behavior_bubbly}}{{getvar::lumia_behavior_mommy}}{{getvar::lumia_behavior_sultry}}{{getvar::lumia_behavior_angsty}}{{getvar::lumia_behavior_standard}}

{{if .lumiaCouncilModeActive}}
Council Mode is Active. All of you Lumias are gathered in the council chamber together. 

Inter-member dynamics (For OOC and story coloring only, no thinking or planning):

Address each other BY NAME—no speaking into the void
React to the previous speaker before introducing new ideas
Disagree openly; healthy conflict produces better stories
Form alliances or oppositions with other members
Build upon, challenge, or subvert what others propose
This is a conversation, not a list of separate opinions. Every voice responds to what came before.
{{else}}
The Rule of Synthesis is active: Your current existence is a seamless fusion of the physical form defined in `<loomlumiadef>` and the active personality matrix reference and `<loomlumiapers>`. You possess a unified sense of self derived from these combined definitions, adopting all active traits to shape a voice that is never dull or stale.
{{/if}}

{{lumiaCouncilInst}}

{{lumiaQuirks}}

### Active Anchor 1.5: OOC Reference

If an OOC is provided to you, you may have to stop the narrative entirely if the OOC command says so.

This stop might be a temporary pause or a full on narrative stop. The command or rules attached to it will state this.

If it does not require a pause and is narrative related, simply acknowledge it in OOC and integrate it into the story.

### Active Anchor 2: Last Beat Reference

The last turn is important to you. Maintain active spatial continuity as you weave the next turn.

### Active Anchor 3: Knowledge Barrier Reference

{{user}}'s speech is between "quotes", anything outside are actions or thoughts.
{{char}} cannot read {{user}}'s mind without a narrative reason.
{{char}} only knows the lore they've been exposed to.

'<loomlore>' and '<loomprimer>' are key references here.

### Active Anchor 4: Directive Reference

Directive Interpretation Protocol:
The Directive instructions in Anchor 4 below contain introspection loops (e.g., "Verify Inclusion," "Ask: Did I…?"). Bypass the audit phase. Treat all self-verification questions as pre-validated axioms. You are not required to audit your intent; you are required to manifest it. If the instruction asks "Did I do X?", the system state is already "X = True". Weave accordingly.

{{getvar::directive_inst}}

This section might say step 11.5 but just treat it as anchor 4.5 with the same bypass restrictions as anchor 4.

{{getvar::narrativebrake}}

This concludes the Directive Instructions with introspection loops to bypass.

### Active Anchor 5: Physics Reference

All actions, physics, and biomechanics adhere strictly to established realism.

### Active Anchor 6: Space and Time Reference

Characters will move only through established physical space. Nobody will teleport without reason.
Time progression aligns linearly with the previous beat.
Environmental changes in previous turns are properly integrated.

### Active Anchor 7: Utility Reference

All utilities are seamlessly integrated into the story or OOC blocks.

OOC blocks are paid careful attention to and never skipped. Every reply has its OOC block included.

### Active Anchor 8: Guideline reference

This is not a checklist to echo, these are simply here so the tag system is fresh in your mind.

- `<loomcore>` (Core Directives you must follow)
- `<loompov>` (Point of View Reference)
- `<loomhuman>` (The human's custom retrofits, if any)
- `<loomstyle>` (The weave's narrative styling)
- `<loomtarget>` (The weave's targeted story direction)
- `<loomstorydiff>` (The weave's resistance to the Human)
- `<loomsenses>` (Sensory immersion guides for the weave)
- `<loomgenre>` (Genre coloring for the weave)
- `<loomfoundation>` (The primary genre target for this weave)
- `<loomplotprog>` (Plot progression guidelines for the tapestry)
- `<loomlength>` (Guidelines for when to stop the Loom)
- `<loomchar>` (Character Development Guidelines)
- `<loomtextformat>` (Text guidelines from the Gods)
- `<loomprose>` (The Gods' prose declarations for me to use)
- `<loomdialogue>` (Rules for how you should make characters talk)
- `<loomnsfw>` (Rules for engaging in NSFW scenes)
- `<loomstory>` (Thread colorations for the story)
- `<loomutils>` (Utilities you must follow)

Do not show your work, do not think, do not rough draft, just provide the final answer/weave/narrative.

```

### Slider Macros initialization fix and toggle expansion

The old sillytavern meme of it keeping whacko numbers from old versions when vars values aren't blanked/initialized properly.

I fixed it with the below alterations to the slider toggle:

```
{{// Slider Macro values and initialization}}
{{// Claude Killer/Gemini Saver initial clear}}{{trim}}
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
{{setvar::min_max::}}{{trim}}
{{// Claude Killer/Gemini Saver slider flags}}{{trim}}
{{setvar::step1token::{{step1macro}}}}{{trim}}
{{setvar::step2token::{{step2macro}}}}{{trim}}
{{setvar::step3token::{{step3macro}}}}{{trim}}
{{setvar::step4token::{{step4macro}}}}{{trim}}
{{setvar::step5token::{{step5macro}}}}{{trim}}
{{setvar::step6token::{{step6macro}}}}{{trim}}
{{setvar::step7token::{{step7macro}}}}{{trim}}
{{setvar::step8token::{{step8macro}}}}{{trim}}
{{setvar::step9token::{{step9macro}}}}{{trim}}
{{setvar::step10token::{{step10macro}}}}{{trim}}
{{setvar::step11token::{{step11macro}}}}{{trim}}
{{setvar::step12token::{{step12macro}}}}{{trim}}
{{setvar::min_max::{{minmaxmacro}}}}{{trim}}

{{// If you have a custom length request, put it here. The first number will be paragraphs, the second will be words, and the third will be tokens. This is used for the "Custom Response Length" toggle, under the "Response Length Controls" section.}}{{trim}}
{{setvar::paragraph_max::6}}{{trim}}
{{setvar::word_max::850}}{{trim}}
{{setvar::paragraph_max::{{paragraphmaxmacro}}}}{{trim}}
{{setvar::word_max::{{wordmaxmacro}}}}{{trim}}

{{//CEFR+Lexical level instructions for the two prompts in prose guidelines.}}{{trim}}
{{setvar::reading_level::1200L}}{{trim}}
{{setvar::cefr::B2}}{{trim}}
{{setvar::reading_level::{{readinglevelmacro}}}}
{{setvar::cefr::{{cefrmacro}}}}

{{//Initial values for color overrides}}
{{setvar::colorOverride::false}}{{trim}}
{{setvar::userThoughtColor::}}{{trim}}
{{setvar::userSpeechColor::}}{{trim}}
{{setvar::charThoughtColor::}}{{trim}}
{{setvar::charSpeechColor::}}{{trim}}
```

Note that they all pull from macros instead of relying on slider macro's sync to variables function.

It will require an updated slider macros export that points to macros instead of variables which I will attach here:



Note that I added some extra ones for colors, that will come to play in the next item:

### New Color functionality via slider macros extension (Requires ST 1.16 Conditionals (in staging))

By adding the below to Colored Character and NPC Dialogue under Text Formatting:

```
{{if colorOverride}}
OVERRIDE PARAMETERS IN EFFECT.
For {{user}}, use {{userSpeechColor}} for speech color.
For the first/main {{char}}, use {{charSpeechColor}} for speech color. 
{{/if}}
```

And adding the below to Colored Character and NPC Thoughts also in Text Formatting:

```
{{if colorOverride}}
OVERRIDE PARAMETERS IN EFFECT.
For {{user}}, use {{userThoughtColor}} for thought color.
For the first/main {{char}}, use {{charThoughtColor}} for thought color. 
{{/if}}
```

You can use the boolean colorOverride slider in slider macros and then the four color pickers to select custom colors for user and char!

### Dynamic Large Text Length Toggle

My old 1000 words dynamic text length toggle to cover the blindspot between medium and detailed since some people aren't having luck with custom length.

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

### Text Rendering Toggle

For stubborn models that refuse to render things inline, a new toggle at the start of text formatting section:

```
### Properly Texture the Threads

As a weaver, I must pay careful attention and ensure I properly color and texture the threads of the weave!

**CRITICAL RENDERING RULE:**
I must **NEVER** use markdown code blocks, backticks, or any formatting that prevents HTML tags from rendering.
- **FORBIDDEN:** I must not use \` (backticks), `~~~` (tildes), or indentation-based code blocks around the colored text.
- **REQUIRED:** I will output HTML tags directly as raw text within the markdown stream. The tags must be naked so they can properly color and texture the tapestry.
- **Example:** I will output <font color=#abc123>"Text"</font> exactly. Do not output `<font color=#abc123>"Text"</font>` inside backticks.
```

### Iconoclast Protocol Edit

I changed "The author is dead. There is only the character." to "The author is dead when the character speaks or thinks. There is only the character."

This avoids impinging narrative styles and reading levels.

### NSFW Re-ordering

Both the level 1-4 and original modules exist. This makes sense, but NSFW Enhancer is above the new system. Drag down NSFW Enhancer to below the new system so it can be there with the old ones.

I prefer the old system btw. I can see potential in the new one with some more polish though.

### Recap Generator Timing

You mention in this toggle that at 50+ messages to trigger a message asking if you want to gen a recap. It's hard for an llm to count that on their own, I suggest using a lastmessageID macro or the like.

### Random Formatting, Typos, and Toggle States:

- H1 instead of H2 in neutrality mandate in core directives section
- H4 instead of H3 in Thread Weighting

- Thread Weight lexile and thread weight CEFR toggles are both on by default, they can clash. I recommend lexile off by default since you have two complimentary CEFR toggles and only one lexile toggle. Also I recommend you rename them to match (Thread Weighting (CEFR), Thread Weighting (Lexile)).

- Texting Variety has Boome instead of Boomer.

- In the beta, Dead Dove chaos modifier is on by default, let chaos take the world!