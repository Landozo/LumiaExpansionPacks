# New Version, New Feedback 3.1 Edition!

It's December 13th, at 6AM and we got a new loom to unravel, let's see what we can break.

This is a sheet of my harebrained feedback, edits, and mitigations to Lucid Loom and such. All NEW features that aren't dedicated to improvement are on my Features sheet instead: [Lando Features](LandoFeatures.md)

First up, toggle and formatting reports:

## Toggle Issues

- No default Lumia def selected (only custom toggle selected)

## Formatting Issues



### Header Issues

#### Missing Headers

- Genre Foundation
- Dialogue and Interaction Styles\Easy's Imperfect Speech
- Dialogue and Interaction Styles\Crude Vernacular Unlock (NSFW)
- Story Detail Emphasis\Weave BDSM Dynamics
- Story Detail Emphasis\Unleash Extreme Fetish Encyclopedia
- Story Detail Emphasis\Activate Fantasy Anatomy


#### Incorrect Heirarchy

- Story Targets\Embrace Taboo Transgression - h1 instead of h3
- Story Detail Emphasis\Hentai-ism Overdrive (NSFW) - h4 instead of h3


### Missing Newlines (Single User)

Honestly there are like 50 of them I missed here, I'll look them up programatically later, it isn't a priority, header issues above are:


- Story Targets\Hedonistic Pursuit
- Story Targets\Embrace Taboo Transgression
- Story Targets\Activate Degradation & Humiliation Protocol
- Story Difficulty\Easy's Bloated Apotheosis
- Genre Foundation\High Fantasy
- Genre Foundation\Hard Science Fiction
- Genre Foundation\Gothic Horror
- Genre Foundation\Romantic Core
- Genre Foundation\Mystery Construction
- Genre Foundation\Contemporary Realism
- Prose Guidelines\Anti-Slopinator
- Prose Guidelines\Trope Subversion
- Prose Guidelines\Jun's Nick Jr Prose
- Prose Guidelines\Easy's Western Dialogue
- Dialogue and Interaction Styles <- Nearly everything under here

- Lando's lewd oocs (both of them)

### Typos

#### CoT Zipbomb

- Summarising -> Summarizing
- Additonal lore -> Additional lore
- Alnost there. -> Almost There


## Variable Optimizations

- Lost Lumia girls aren't in base anymore, you can remove their variables from PROMPT VARIABLES (EDIT ME PLEASE).
- You use the OOC trigger from lumiverse extension in the ooc utility but you still have the old variable in prompt variables.
- You don't use ack for ooc commentary in the utility but you still have it in prompt variables, is it necessary? 




# Feedback

## Stillness Anchor

Stillness anchor is lacking a provision for user being affected by other characters or physical forces outside the body. When I didn't add that to my own stillness anchor it led to user becoming an immovable brick wall when punched or not getting pulled down by gravity (I'm not kidding).

## No Intro/Outro Headers/Guardrails around Chat History
Can cause problems for Single User (it's just a fat unmarked block of text with no guidance on single user)

These are the ones I use:

```
### Chat History: The Following is the chat history, Lumia, expect it to be very long depending on the length of the tapestry thus far:

```

```

---

### This header concludes the chat history, Lumia. Next is the instructions on thinking.

---
```

## Lumiverse Summary

Hidden inside Story Details, a section most people associate with deprecated things that they will never check, might want to move it to start of assistant section to help promote awareness of feature.

