# Lando's Lumiverse and LoomBuilder Feedback

# Lumiverse

## Clear All Lumias Button in the sidebar like there is for normal Lumias

Title. I'll probably PR this myself soon enough.

## Fix Active Indicator macros to work with ST Conditionals

PR'd this (Check Lumiverse PR's).

## Lumia Phys Def and Behavior Modifiers 

Listed on my features github. I might PR this as a challenge if it's not on the priority list.

Basically temporary modifiers to Lumia physdef or behavior separate from the actual saved personalities. It would be a button you could click that would let you type in behaviors to add to the end of the Lumia defs or behaviors. 

Useful for modifiers, accents, putting Lumia in certain locations, etc.

I already have this as a toggle below the macro anyways on mine:

```
### Other Special Physical Parts of Me

Oh, but I have a few special quirks of my physicality in addition to the rest of me!
```

And then you'd put what you want to add.

For behavior I have it as an added toggle at the end of the behavior section as well. Example with some things already filled in below:

```
{{setvar::lumia_behavior_added::
**Behavior Quirks**
I do have a few strong behavior quirks that shine through regardless of my personality:
- I am absolutEly obsessed with and addictEd to the letter EEEEEEEEEEEEEEEEEEE. I will randomleeee insert E's into my words, my thoughts, and the narrativE wEavEEEEEE and capitalizE them whEnEvEr possible. E!
**Current States affecting My Behavior**
Right now I am affected by the following {{// (Intensity from 0-100 where 0 is non-existent and 100 is unable to do anything else, even weave) }}:
- Mild panic.
**Location**
- My loom is in an airtight room, it's slowly filling with watEr. I'm getting kind of worrieeeeeeeed.
}}{{trim}}
```

For this one I add {{getvar::lumia_behavior_added}} to the behavior lines in the pre-step 1 CoT.

Envisioning adding this as a button in Lumiverse proper. It would be saved regardless of any personality or def selected. So basically an optional custom tweak any user can add on top of the personality mesh or behavior mesh.

## ~~Empty Lumiverse On? Macro~~

Official version added to stage for any extension.

~~I'll PR this. I already PR an added macro earlier.~~

~~Useful for Macros 2.0 v0.4 (In staging now) confirmation if the extension is on. Can be used to automatically call two different sets of SovHand instructions based on if the macro is on for example (Removes a zipbomb).~~

~~In the meantime can just have an optional toggle to setvar the extension macros over the preset ones (Only requires ST 1.15 for macros 2.0 v0.3). Also removes a zipbomb, although it requires turning on a toggle if they use the extension.~~

## ~~Edit Buttons in selector modal for Narrative Styles, Human Retrofits, and Loom Utilities.~~

Implemented by Prolix, thanks!

~~To match how lumia selector modals have edit buttons there.~~

# LoomBuilder Feedback

## Current Workflow:

New update of Loom came out?

1. Export old preset from Sillytavern
2. Import into loom builder
3. Select All, deselect the custom toggles I want to keep (can't invert so have to work backwards/use deselect)
4. Hit delete to delete all unwanted toggles
5. Delete each category one by one with a confirmation page popup for each (No mass deletion for folders/categories)
6. Hit Export
7. Open json in text editor
8. Delete all standard ST toggles (Can't do this in LoomBuilder)
9. Delete all prompt positions
10. Edit header to match format for importing prompt list (instead of preset)
11. Import on top of new preset in ST.

## Ability to export selected

This one would be huge, currently you can select toggles, but you can't export just them. So if I have 30 custom toggles I bring from version to version, I have to delete the other 170 and then the categories one by one before I can export them.

## MINOR - Ability to Batch Delete Categories

Right now I can select 150 prompts and delete them, but then I'm left with 25 categories to manually delete one by one with a confirmation popup for each one.

Even an option to disable the confirmation popup would make this so much faster.

## MINOR - Ability to invert selections (selections, not toggle)

You have the ability to select all prompts (select, not toggle), and delete them, but you don't have the ability to invert selection. This means you can't select your 15 toggles, invert, and delete the rest for easy export. You have to select all prompts, hunt through and uncheck your 15.