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


### Missing Loom Council Instructions

{{loomCouncilInst}} is missing from:

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