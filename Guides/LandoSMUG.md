# Lando's Sillytavern M.U.G. (Mostly Useful Guide)

![smolimg-1767850935246](https://github.com/user-attachments/assets/c1b5247c-4fcb-4d54-b119-b3ba3d006b81)

This is a guide for commonly asked Sillytavern Questions. It is:

1. Not Preset-specific or Lucid Loom Specific (Check my [Loom Guide](LoomGuide.md) for that)
2. Not Terminology or Model Specific (Check my [Loom Guide](LoomGuide.md) for basic model rundowns and terminology)
3. Not Reasoning-Setup specific (This will be different for every preset, I have a detailed breakdown of reasoning options in sillytavern in my [Loom Guide](LoomGuide.md))

# Table of Contents

- [General Questions](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#general-questions)
  - [Installing Sillytavern](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#installing-sillytavern)
  - [How do I enable Macros 2.0?](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-do-i-enable-macros-20)
- [Preset/Prompt Questions](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#presetprompt-questions)
  - [How can I import a preset?](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-can-i-import-a-preset)
  - [How do I add a new/custom toggle](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-do-i-add-a-newcustom-toggle)
  - [How can I view my raw prompt sent to the LLM?](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-can-i-view-my-raw-prompt-sent-to-the-llm)
- [Identifying and Repairing Prompt Issues](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#identifying-and-repairing-prompt-issues)
  - [First steps, Do This First](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#first-steps)
  - [How can I diagnose issues with my prompt if the above fails?](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#identifying-and-repairing-prompt-issues)
- [Extensions](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#extensions)
  - [How do I install an extension](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-do-i-install-an-extension)
  - [How do I enable/disable, update, remove, or switch the branch of an extension](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-do-i-install-an-extension)
  - [What extensions do you recommend](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LandoSMUG.md#how-do-i-install-an-extension)


# General Questions

## Sillytavern Documentation?

Available below:

https://docs.sillytavern.app

## Installing Sillytavern

Different detailed guides for every version are here:

https://docs.sillytavern.app/installation/

## How do I enable Macros 2.0?

You might be told by an extension developer to turn on Macros 2.0.

To do this, first you need to at least be on Sillytavern 1.15 Live or Staging.

Then you need to go to the user settings by clicking the profile icon with a cogwheel at the top center of the topmost bar in sillytavern.

Then on the right click turn on "Experimental Macro Engine." It will have a little flask to the right of it. You are all set.

You can test if it works by trying out a nested macro in a chat message like ```{{setvar::greeting::Hello, {{user}}}} {{getvar::greeting}}```. If it works and shows Hello and your own persona name, grats, you have macros 2.0 up and running.

# Preset/Prompt Questions

## How can I import a preset?

### Simple Steps:
1. Select Chat Completion in API Tab
2. Use import button in Chat Completion Presets Panel
3. Ensure it is selected in the dropdown
4. Remember to save any changes from now on to the preset

### Detailed Explanation:

First you need to know if a preset is chat or text completion. 

Most presets on the AI presets discord including Lucid Loom, NemoNet/Nemo Engine, Izumi, and others are all chat completion, so ensure you have "Chat Completion" selected on the API Tab (Plug icon at the top).

Now that chat completion is selected, click the left most hamburger menu looking icon at the top (AI Response Configuration) to open the Chat Completion Presets Panel on the left of Sillytavern.

Then use the import icon to import the preset json file. After importing, ensure your new preset is selected in the drop down to use it. 

> [!WARNING]
> Any changes you make to the preset below, whether they be to sampler sliders, reasoning settings, or toggle states or custom toggles **will be lost** unless you hit the save button under the dropdown at the top of this panel.

## How do I add a new/custom toggle

### Simple steps:
1. Add the prompt
2. Save the prompt
3. Select the prompt in the prompt dropdown
4. Click the Chain next to it to add it to the Prompt List
5. Drag it to where you want it and enable it
6. Scroll back up and hit save on your preset

### Detailed Explanation:

First, ensure the preset you want to add it to is selected in the Chat Completion Presets panel. *Toggles are added per preset, not globally.*

Next scroll down to the start of the list of toggles. There you will see a Prompts Dropdown and to the right of it some buttons. The last button, the one with the plus icon, is the New Prompt button.

### The New/Edit Prompt Page

If you click it, a new panel will pop up with several options. Name is what the toggle will say in the toggle manager, the LLM will never see this name so you can name it whatever you want.

Role is what it is sent to the LLM as, most of the time you want system here. 

Triggers control when it is sent (regular replies vs continue vs impersonate, etc), usually you'll want to leave this at the default All.

Position is where the toggle is sent. Relative means you can slide it around the prompts list and it'll send at that point. In-Chat lets you set a depth (so you can send it in your chat history instead, like Author's Note. Depth refers to how far back in the history it is sent). Usually you'll want to leave this as relative.

In the prompt box you enter your prompt, and you can save it in the lower right.

### After making the new toggle

> [!NOTE]
> After you save and the prompt disappears, your prompt is not actually saved, it can still disappear if you refresh the window so I recommend scrolling up to the preset dropdown and hitting save. Then scroll back down.

Select your new prompt in the dropdown just above the prompt list.

Click the chain icon to insert your prompt into the list below.

Drag your prompt to where you want it and hit save on the preset way up top.

> [!TIP]
> You can use nemo preset extension to help you navigate giant presets more easily, but it can be a bit glitchy, so remember to save often!

### Editing my Prompt

Simply click the pencil icon to the right of your prompt (or eyeball icon if you are on nemo tray). Remember to hit save in the lower right to lock in changes to your prompt and save on the preset afterwards to save changes to your preset.

## How can I view my raw prompt sent to the LLM?

To see what the AI received and used to create the reply in any AI response, once the response is done generating or has been stopped: You can expand the options in the upper right of the response and click the little writing tablet icon to bring up the Prompt Itemizer.

Once there you can click the two buttons at the upper right to either view your prompt in a pop window, or copy it to your clipboard for easier viewing in a text editor.

# Identifying and Repairing Prompt Issues

## First steps, Do This First

First, please don't hesitate to:

1. Look for documentation! [Sillytavern](https://docs.sillytavern.app), your model, your api provider, and in some cases, your preset provider or their community may have documentation to help out their users!
2. Look for a chat channel or hangout for your preset and check the pins for a guide or FAQ, then use the search bar and if you get no hits, ask for help!
3. Use the edit button (pencil icon) to look at your actual prompts for insight!

## How can I diagnose issues with my prompt if the above fails?

First, this depends on the capabilities of your model. Anything GLM 4.7 level or more complex will do fine (GLM, Gemini, Deepseek, Claude), small local models will probably not. This will work better if your preset has a dedicated OOC handling engine or toggle. Keep in mind this can be more art than science. 

In general the workflow is
1. Identify the problem you have with the LLM's output
2. Decide how to describe it to the LLM
3. Chat Branch out from the problematic reply into a chat branch to be used for diagnostics
4. Put the LLM into a proper OOC state where it can see it's own rules and instructions and acknowledge them
5. Ask the LLM why it did what it did, identifying trends, rules, and conflicts
6. Ask the LLM to narrow down potential fixes or mitigations to solve the issue in prompts, not in context
7. Chase with the LLM to get a workable prompt edit or addition
8. Test it out in the original branch, if it doesn't fix it, try it in a new chat, revisit the diagnostic branch, or create a new diagnostic branch right then and there after the new failed reply.
9. Rinse and Repeat!


### Preliminary Steps

Next time you see a problem occur in a reply, in the reply immediately after, go to Advanced Formatting and go to the reasoning Formatting section in the lower left and hit "Add to Prompts" and set it to 1.

This will allow the LLM to see the Reasoning Block in the last reply it sent (usually empty). 

> [!TIP]
> Remember to turn this back off when you go back to roleplaying if you usually have it off.

Use sillytavern's branch feature to branch off your chat off the problematic reply. Now in the new branched chat, in whatever OOC engine or format your preset has (I'll use Prolix's Lucid Loom OOC formatting as an example); you will type something akin to the following:

### Examples

Replace X with the name of your preset personality, or assistant if you don't have one.
Replace Y with the issue you are saying happen.
Replace Z with what the system prompt says it should do, or what you want it to do (change the question to say "I want you to do this instead").

For understanding why something happened:

```
OOC: X, pause the story/narrative/roleplay and keep it paused until I say otherwise. X, You now have access to the full llm details including the rules, mandates, system prompt, and instructions that you have followed. In your last response you did y, what led you to do this? Is there a rule in the system prompt/rules/mandates that made you do it? If there isn't was it your natural training data? Let's nail down a root cause in detail please.
```

For understanding why something happened that contridicts an already existing system prompt rule:

```
OOC: X, pause the story/narrative/roleplay and keep it paused until I say otherwise. X, You now have access to the full llm details including the rules, mandates, system prompt, and instructions that you have followed. In your last response you did y when you were instructed in your system prompt/rules/mandates to do z. Why did this happen? We need to find an actual reason or root cause so we can craft a change to the rules/mandates/system prompt to fix this. Do not simply say you will fix this in your context, we need to fix it for other chats and future stories, which will not have access to your context. Give me an rule change or addendum and where to add it in your prompt.
```

For making a new rule to prevent a thing from happening when there is no existing rule to prevent it:

```
OOC: X, pause the story/narrative/roleplay and keep it paused until I say otherwise. X, You now have access to the full llm details including the rules, mandates, system prompt, and instructions that you have followed. In your last response you did y. I do not want you to do this anymore. We need to identify why this happened and how to stop it with a new rule change. Do not simply say you will fix this in your context, we need to fix it for other chats and future stories, which will not have access to your context. Give me an rule change or addendum and where to add it in your prompt.
```

### Commonalities

Note how I first instructed the addressed the assistant by name. If your Preset has a name for the storyteller/assistant, like how Lucid Loom has Lumia, address them by their name. Now notice how I specified rules, mandates, system prompts, and instructions. Lucid Loom calls its prompt rules mandate of the gods, but I always make sure to give every common prompt name variation including *system prompt* so I can be sure to get my point across.

### Things that can help:

1. If your preset has personalities (Vex, Lumia), pick analytical, smart, or developer related ones (For example, in Prolix's Lucid Loom I specifically created a personality that is a developer with knowledge of LLMs and Sillytavern and prompt engineer for this purpose).
2. Ensure add to prompts is set to 1 so your model can examine it's CoT too.
3. Check to see if your preset has pre-built diagnostic prompts! I added one to Prolix's Lucid Loom in the upcoming update, your preset might have one built in too!
4. Check the system prompt to see if there are OOC controls or rules that can help that you might have shut off to try and save tokens. Remember, the LLM can't see what is toggled off!

### Things to stress to the LLM in follow up responses:

1. I don't want to toss around blame, I want to implement solutions. Let's find the root cause.
2. We cannot do a context fix, we need to implement a rules change in the actual system prompt, give me potential rules to add and where to add them.
3. Remember, this is OOC, drop the character traits and let's work on this logically.
4. Can we make this fix more drop in ready? Also narrow down the location a bit more!

Remember to use swipes or regens to get other angles and explanations!

Once you have a potential fix, edit your toggles or add a new one (check the add a new prompt section up top), then switch from this diagnostic chat branch back to your problem one, and try seeing in the problem persists.

> [!NOTE]
> Remember to save your new or edited toggle in the preset so it won't disappear on refresh!

> [!TIP]
> It's also worth trying it in a new chat, as context in that chat history can "poison" your LLM with bad habits even if you implement a fix!

# Extensions

## How do I install an extension

> [!WARNING]
> Before you do this, ensure your api profile and preset are both saved (the below operations will refresh sillytavern and will cause you to lose unsaved changes).

### Simple Steps:
1. Open the extensions tab
2. Click Install extension in the upper right
3. Enter the github url of the extension and the branch if not the main branch
4. Hit install for anyone or user (global vs user).

### Detailed Explanation:

In the extensions tab (3 blocks in a pyramid in the center right of the topmost bar in sillytavern) you will see a couple of buttons in the upper right.

The rightmost button with a cloud symbol and a down arrow is "Install Extension."

Once you click this a popup dialog will appear asking you to enter the git url of the extension. You can enter the plain github url here, and below add a tag or branch name if it's not the main branch (95% of the time it will be).

Then you can install for all users or just you. If you install for all users it will be in the following folder:

```
.\public\scripts\extensions\third-party\Extension Name
```

If you install it for a specific user it will be in (default-user used as example):
```
.\data\default-user\extensions\Extension Name
```
> [!NOTE]
> Users without administrative rights will not be able to uninstall global extensions.

## How do I enable/disable, update, remove, or switch the branch of an extension

> [!WARNING]
> Before you do this, ensure your api profile and preset are both saved (the below operations will refresh sillytavern and will cause you to lose unsaved changes).

In the extensions panel, on the upper right, will be a manage extensions button (same 3 block pyramid icon).

Once you click this you will see a list of extensions, scroll down to "Installed extensions." It will probably be busy "loading extensions". This means it's doing update checks, let it do it's thing.

### Updating an Extension

To see if an extension has an update, simply scroll down when the loading indicator finishes and look for a green color to the extension name. On the right will be an button that only appears if there is an update, with a down arrow pointing at a hard disk. Click it to update. 

Alternatively you can also scroll back up to the top after loading is done and hit update all or update enabled in the upper left.

After doing this, the updates will install (some may say failed, they probably didn't fail even if they said they did). After all the updates are done, your sillytavern will probably refresh, if it does, refresh the page manually, the extensions will require this.

### Toggling an extension on or off

To turn an extension off and on, click the check circle the left of it's name. You will probably have to refresh the page afterwards for the extension to properly enable or disable. If you are fast you can disable or enable multiple extensions at once before the refresh!

### Uninstalling an extension.

To the right on the same row as your target extension will be a trash can icon, click it to uninstall the extension, sillytavern will refresh after it does. If it doesn't, do the refresh yourself.

### Switching extension branches.

Sometimes a developer will have a test or dev branch of an extension. To switch to it you use the switch branch button to the right in the same row. A dropdown window will then appear and you can select your branch from it.

> [!NOTE]
> Historically I've had issues with this feature, so I'd recommend uninstalling and reinstalling but with the proper branch name in the install extension dialog if switching branches like this doesn't work.

## What extensions do you recommend

My recommended extensions are on my [Loom Guide](https://github.com/Landozo/LumiaExpansionPacks/blob/main/Guides/LoomGuide.md#recommended-extensions-my-personal-favorites) in the appendix.
