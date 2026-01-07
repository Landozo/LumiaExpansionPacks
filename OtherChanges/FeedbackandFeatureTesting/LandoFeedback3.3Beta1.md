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