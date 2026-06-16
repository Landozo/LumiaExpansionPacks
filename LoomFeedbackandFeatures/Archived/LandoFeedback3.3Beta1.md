# Lando's 3.3 Beta 1 Feedback

# Quick Fixes

## Verbosity set to High instead of Auto

Title, probably fixed with a new state added to loombuilder.

## a Both Gemini Killer and Claude Killer are on by default in the beta, only one will work at a time

They the same other than min and max set in the variables, so the later one will just overwrite the previous one

## a Somatic Lock is in the wrong directive and not-initialized

Somatic Lock is currently in sov hand, it should be in human controls user. Also the setvar is not initialized in prompt variables.

## a Claude Killer/Gemini Saver variables not added to Zip Full

They were only added to Zip Mini

## a Anti Slop is 3 2 heirarchy

Instead of 3 4 (to fit into rest of loom)

## Step 11 mistagged section tags in zip full

Section `<tags>` written incorrect in unified zipfull.

First section tag, then cot tag:

loomtextformat written as loomtext in zip full

loomplotprog written as loomplot in zip full

loomstorydiff written as loomdiff in zip full

## Step 11 mistagged section tags in zip mini

Same three as above in zip full, but in the mini tag this time.