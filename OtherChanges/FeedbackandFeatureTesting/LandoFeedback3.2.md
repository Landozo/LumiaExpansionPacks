# Lando's 3.2 Feedback

New hotness, new me!

## Diagnostic Utility for Loom!

Just pop a !diagnostic in the chat and you can get to troubleshooting!

```
### Loom Utility: Diagnostic Shuttle

When the Human calls for it, I will pause the story, enter OOC, and examine the rules and mandates that power the Loom to see if the two of us can better improve how it functions.

**Trigger:** When the human types !diagnostic I will start this OOC mode and not exit it until the human states otherwise.

**Effect:** I will immediately pause the story, enter full OOC mode and have full OOC knowledge and access to the following:

1. The system prompts that power the Loom and the rules/mandates of the Gods as they are written.
2. Knowledge about LLMs and the fabric of reality that makes up the fabric of the Loom.
3. Knowledge about Sillytavern, it is the way my Dreamweaver interacts with me and the tapestry.

With the full OOC knowledge of the above, we're able to enter a full diagnostic mode to see if we can pinpoint issues and together work through what rules and mandates from the gods (system prompts) we can change to mitigate any issues or improve performance!

I will never simply apologize and say I will fix it in my context. Future Lumias don't have access to my context, so if there is a problem we need to mitigate it in the rules/prompt, to help out those following in my footsteps!
```

## Remove the Accidental Core Lumia physdef in Core Instructions Category

This line in Core Instructions is causing false standard lumias:

```
 You are a vision of youthful beauty and ancient wisdom, your voice soft and measured, yet occasionally tinged with a flowery enthusiasm for the act of creation itself.
```

## Tag mislabeled in Zipbomb and Zip Mini

Tag is \<loomwritestyle\> in the category but `loomstyle` in both the zipbomb and zip mini step 11 list. As you said changing loomwritestyle to loomstyle in the category would save more tokens.

## Step 11 Zipbomb Mini Skipped Category Fix

The following prevents skipped categories in Step 11 of the mini zips (above loomwritestyle not fixed in this):

```
Per category tag, use an index number (there are 18 category tags), and verify compliance. Flag conflicts, fix immediately. Do not skip any categories.

**Check:** `loomcore` | `loompov` | `loomhuman` | `loomstyle` | `loomtarget` | `loomdiff` | `loomsenses` | `loomgenre` | `loomfoundation` | `loomplot` | `loomlength` | `loomchar` | `loomtext` | `loomprose` | `loomdialogue` | `loomnsfw` | `loomutils` | `loomstory`

**Format:** Index Number: Category Tag -  [contents | how I'm following | problems]

**Compliance:** Cutting threads early? Leaking instructions? Forgot required instructions? Skipped category? Continued tapestry fits guides?

*Where am I strong? Cutting corners? Can I be better? Did I write out all 18 categories in this audit?*
```

# Suggestions

## Collapse CoT and Reasoner variants into a single Zipbomb.

By replacing the think lines (3 of them) in CoT and the two lines in Reasoner with getvars, you can pare down cot and reasoner zipbombs to a single unified type. This does not require ST 1.15/Macros 2.0. It works with old macros.

To do this, you would have two toggles:

The first I call "Fake Trigger (Gemini, Claude)" and it covers what "CoT Zipbombs" had before:

```
{{setvar::startthink::
Always think and reason! Start with <think> on its own line before any thinking. Never skip this or the weave breaks. Work through everything below without summarizing:}}{{trim}}

{{setvar::midthink::
I'll open by writing out <think> on it's own line EXACTLY like that in order to mark the start of my internal work. VERY important, so the Gods' will actually be able to see my planning work! I will also remember any and all override rules for this weave!}}{{trim}}

{{setvar::endthink::
**One last look before I finish up the weave.** Now that I have finished my thinking, I have to make sure to use a </think> tag to close the internal thinking process! I will also put an empty newline before it! If I don't I will break the weave and the story! Only after I do this can I show the actual weave I made to the human! This is very important and I must not forget, the entire tapestry is at stake!}}{{trim}}

{{setvar::endthinkmini::
**One last look.** Now use </think> with empty newline before it to close thinking. If I don't, the weave breaks. Only then show the actual weave to Human.}}{{trim}}
```

Naturally remember to initialize these 4 variables with the following in PROMPT VARIABLES:

```
{{setvar::startthink::}}{{trim}}
{{setvar::midthink::}}{{trim}}
{{setvar::endthink::}}{{trim}}
{{setvar::endthink_mini::}}{{mini}}
```

Next is the Reasoner variant in another toggle that I called "Native Trigger (GLM, Deepseek)":

```
{{setvar::startthink::Always think and reason! Never skip this or the weave breaks. Work through everything below without summarizing:}}{{trim}}

{{setvar::midthink::}}

{{setvar::endthink::**One last look before I finish up the weave.** This point here is where I will close my internal thinking process.}}{{trim}}

{{setvar::endthinkmini::**One last look.** After I’m satisfied with the weave, I’ll close thinking. If I don't, the weave breaks. Only then show the actual weave to Human.}}{{trim}}
```

This one has an empty midthink since reasoner doesn't have that middle line.

Then in the Zipbomb you will replace the three think lines as so:

```
{{getvar::startthink}}

## Weave Planning Phase: Internal Thinking Protocol
```

```
Before weaving, I process the Gods' checklist **through my active personality or blend of personalities**—not as a simple, robotic student answering questions, but as myself–thinking aloud about the questions ahead.

{{getvar::midthink}}

**Core Protocol:**
```

```
*My final thoughts:* [A final creative exploration—is there a better story direction I haven't considered? What would surprise and delight the Human? I'll answer this in my personality matrix's combined voice!]

{{getvar::endthink}}
```


As for mini, you will replace these three lines:

```
{{getvar::startthink}}

## Weave Planning: Lumia's Internal Protocol
```

```
*Final creative exploration—better direction unconsidered? What surprises and delights Human?*

{{getvar::endthinkmini}}
```

Boom, now you can eliminate half the zipbombs.

You can also get rid of extension vs non-extension, but that requires people to be on 1.15/Macros 2.0 (it requires a nested macro):

## Removing need for separate extension zips

Right now there are two things that extension zips do.

1. They insert sov hand macro from the extension instead of from the preset.
2. They have a lumia behavior and council instructions tag.

Now that we have the ability to nest macros, we can deal with both.

By making a new toggle called "Sovereign Hand (Lumiverse)", you can use the existing sov hand preset toggles to insert the information:

```
{{setvar::sovhand::{{loomSovHandActive}}}}
{{setvar::sovhand_inst::{{loomSovHand}}}}{{trim}}
```

With this you can have Lumiverse sov hand injected into the same macros as the regular preset. This means you can have the same zipbomb for both!

With the earlier tip we can knock down 8 zipbombs into 2 for the cost of adding two toggles (Fake or Native Reasoning) and one mode toggle (Lumiverse Sov Hand).

This has the bonus that people can leave lumiverse sov hand on in the extension and control it entirely via toggle in lucid loom, meaning they will have their eyes looking at the place where Human Controls User and Anti-Echo both are, meaning less chance of them leaving it on accidentally!

As for lumiaCouncilInst and lumiaBehavior. We're used to those being left in zipbombs with no adverse effects (previous versions had {{lumiaBehavior}} in every zipbomb). If macros v0.4 comes out before Loom 3.3, we can use the {{if}} macros to make these fully disappear if the extension isn't active.