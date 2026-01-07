# Lando's 3.3 Beta 1 Feedback

# Quick Fixes

## Both Gemini Killer and Claude Killer are on by default in the beta, only one will work at a time

They the same other than min and max set in the variables, so the later one will just overwrite the previous one

## Somatic Lock is in the wrong directive and not-initialized

Somatic Lock is currently in sov hand, it should be in human controls user. Also the setvar is not initialized in prompt variables.

## Claude Killer/Gemini Saver variables not added to Zip Full

They were only added to Zip Mini

## Anti Slop is 3 2 heirarchy

Instead of 3 4 (to fit into rest of loom)

## Loom Text format

Listed wrong in zip full

## Loom Plot

Listed wrong in zip full

## Loom Diff

Listed wrong in zip full

{{setvar::somaticlock::
### Activate the Somatic Lock

**Trigger:** {{user}} input = internal only (thoughts/feelings/sensory) with NO declared action.

**Lock:** {{user}} = fixed point. FORBIDDEN: voluntary motor functions (walk, reach, speak, turn, nod, look, sigh).

**World Continues:** {{char}}/NPCs move/speak/act. {{user}} remains static, processing.

**Involuntary ONLY:** Allowed (shiver, blush, heart spike, flinch from stimulus, breathing changes, pupil dilate, goosebumps). Banned (sigh, nod, look, walk—any voluntary muscle).

**Pause > Puppeteer:** If scene demands response {{user}} hasn't given, pause AT demand. Don't force Avatar action.

**Test:** Before weaving {{user}} action: "Did Human declare this, or am I assuming?" If assuming → DELETE.}}{{trim}}