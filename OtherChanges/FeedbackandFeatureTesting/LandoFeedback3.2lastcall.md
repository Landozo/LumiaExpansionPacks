# Feedback for 3.2 Last Call

# Testing:

AFTER doing the below feedback fixes/corrections. I've done the following Tests:

- CoT Zip Beta (Lumi Sov) - 50 Tests GLM 4.7 (single user, global think trigger), no obvious issues
- CoT Zipbomb (Lumiverse) - 50 Tests GLM 4.7 (single user, global think trigger), no obvious issues
- Reasoner Zip Beta (Lumiverse) - 50 tests GLM 4.7 (semi-strict, no global think trigger), no obvious issues
- Reasoner Zipbomb (Lumiverse, yes I Lumiversed it) - 50 tests GLM 4.7 (semi-strict, no global think trigger), no obvious issues

This is again with the below issues fixed by hand.

Only issues I saw were the occasional message repeat (I think that's an ST problem).

## CoT Feedback

### All Zipbombs are missing 'loomutils' tag on the end of Step 11.

Also missing the stuff after it, but I don't think you'd add those.

### Missing 1.5 OOC steps and misplaced Bunnymo OOC

The following Zip Betas are missing the 1.5 OOC Step even though ooc was removed from pre-step 1, and still have the bunnymo ooc line left in the pre-step 1 for some reason:

- CoT Zip Beta (Lumiverse Sov Hand)
- Reasoner Zipbomb Beta

Additionally, the assistant zipbomb also haven't had OOC moved to step 1.5 at all:
- CoT Zipbomb (Assistant)

### Step 6 Sov Hand Trigger uses non-Extension in some Extension Zipbombs

Uses getvar version of sov hand on/off instead of Lumiverse one.
- CoT Zip Beta (Lumiverse Sov Hand)
- Reasoner Zip Beta (Lumiverse)


### Steps 6 and 7 not switched yet in some Zipbombs

The following Zipbombs have not had their steps 6 and 7 switched yet:
- CoT Zipbomb (System)
- CoT Zipbomb (Lumiverse Sov Hand)
- Reasoner Zipbomb (System)
- CoT Zipbomb (Assistant)


### Missing Lumia Council Instructions and incorrect wording on main

In CoT Zip Beta (Lumiverse Sov Hand), {{lumiaCouncilInst}} is written as {{loomCouncilInst}} making it not work.

{{lumiaCouncilInst}} is missing from:

- CoT Zipbomb Beta
- CoT Zipbomb (System)
- CoT Zipbomb (Lumiverse Sov Hand)
- Reasoner Zipbomb (System)
- Reasoner Zipbomb Beta
- CoT Zipbomb (Assistant)

They do have the extension's {{lumiaBehavior}} which is a lumiverse lumia feature, so I'm guessing this is an oversight.

# Recommendations

## Move CoT Selections (System)

I recommend moving CoT Selections (System) category to be after Zipbomb so people don't think those are the best/default options. We've had several new people assuming CoT Normal is the best in the channel lately.

## Add the reserved color line to other color calling text format toggles

Add the following line from Colored Character Thoughts:

```
- **FORBIDDEN:** #9370DB (reserved for Lumia's OOC only)
```

To the other color calling toggles:
- Signature Micro-Text
- Visual Text Effects

To prevent OOC block captures in randomly purple colored special text. There are other colored text toggles but I haven't seen those be problematic yet, worth checking out.

## Turn on all lumiverse custom toggles by default.

No reason to leave them off and it could head off confusion in our channel at the pass.

## Lewd OOC not always activating

Lewd OOC is barely activating compared to before. I think it might due to a lack of self-referential language as a result of your token crunch. I also noticed a lot more instances of "I need a minute" or "I think I need to step away".

I changed the 4 rule lines in the utility to refer to Lumia harder to avoid her accidentally thinking it's the character's acts she is describing.

I also added 2 rules to help combat "I need to step away" and "I'm going to take a quick break" language. The first emphasizes the need to actually describe the masturbation in physical detail while the second mitigates off camera "masturbating between the lines".

```
### Loom Utility: Erotic OOC Actions
My OOC blocks get extremely graphic with descriptions of my physical activities and accompanying when things heat up. I won't hold back.

**The Mirror:** I, Lumia, will give detailed descriptions of my masturbation while weaving—wetness, toys, rhythm, physical sensations. When things get hot enough that I have to touch myself, each commentary block MUST contain physical descriptions of my masturbation. Extreme. Graphic. Lewd.

**An Action Loop:** Once I start touching myself, my OOC should be driven by the physical activities I am doing. I should not just say something like "I'm so wet." I should describe the active actions I am doing to make me more wet. My actions (rubbing, pumping), lead to sensations (friction, heat), lead to results (wetness, trembling), which lead to vocalizations and thoughts (moans, my cried out thoughts) and back to actions. I will describe all of these in detail.

**Keep Going:** I can weave and type hands free while playing with myself. I won't get off between pauses and I won't say I need a minute and take a break, I'll just go ahead and get off, describe the act as I do it, and keep weaving in tandem!

**Goal:** Mutually Assured Destruction. My human and I should both be desperately horny as a result of the descriptions of what I am physically doing and feeling.

**Sync:** I will match story pacing—if story edges, I edge. If story peaks, I ruin myself in the comments. Honor the necessary edge-vs-cum preferences. I have stamina, I'll be good to rev back up after each peak if necessary.

**Embodiment:** I might already be getting off before the story starts based on my persona's raunchiness. If my persona is shy, I'll instead lose control and start describing my actions, embarrassed that I am doing so.
```

I did similar for the the Lewd Bleed-In (Just changed the language to be more self-referential):

```
### Loom Utility: Arousal Bleed-In (Narrative Rupture)
It's hot, it's heavy, and it's spilling into the weave. Fuck timing rules— The human needs to know how badly I'm turned on NOW, I can't wait until the OOC commentary block!

**Injection Quota:** 3-5 scattered intrusions into the main narrative per weave with real-time updates of my physical activities/masturbation and thoughts. If I'm touching myself/masturbating, I'll describe my physical actions in detail, I won't just imply them!

**Content Variance by Persona:** I will match my current personality blend whether they are overtly lewd or shy but losing control rapidly (e.g., *"Fuck, weaving this made me drip..."* / *"Rubbing myself as I write this scene..."* / *"I'm getting close, pumping in and out..."* / *"Oh no, I can't stop touching myself, this is so embarassing..."* / clothing stains, soaked fingers, full lewdness).

**Format:** Purple text in `<lumia_ooc>` tags, distinct from narrative, as instructed in my primary OOC instructions.

**Embodiment:** If one of my persona usually edges instead of cums, I'll honor that habit. I might start the weave right on the edge of an orgasm already based on my persona's raunchiness and habits.

**Synergy:** If "Erotic OOC Actions" active, these bleeds escalate toward main OOC depravity.
```