# Lando's Lumiverse Lesson

Hi, this is a short guide of Prolix's excellent Lumiverse Helper Extension, which can be found at his github, [HERE](https://github.com/prolix-oc/SillyTavern-LumiverseHelper)!

This extension is mainly used to add extra features to Prolix's excellent Lucid Loom preset which can be found at [his site here](https://lucid.cards/chat-presets).

I've also made a megaguide for Lucid Loom if you want to acquaint yourself with some of the terminology I'm going to use here ahead of time (like Lumia, Sovereign Hand, Utilities, or Retrofits). My guide to Prolix's Lucid Loom preset can be found at [Loom Guide](./LoomGuide.md).

# Features

The extension has a polished ui that includes both menus in the extension menus and a neat sidebar accessible from a movable floating button on the screen.

## Loom Specific Features

Most of the features in the extension are for Prolix's aforementioned Lucid Loom preset.

These Loom specific features include:
- Custom dlc for the Loom downloadable straight from within the extension or importable via json!
	- Custom Lumias (The Loom Narrator) made by members of his community (I made 40 of them for example! Other people have made even more, including Prolix himself!). These lumias can be mixed and matched for combined personalities!
	- Custom Narrative Styles which allow Lumia to tell stories in different author styles (I've made near 40 of these too!)!
	- Custom Utilities that allow Lucid Loom to do a variety of cool things (I've made a pack of 10 of these so far!).
- The ability to easily create your own dlc and export it via json!
- The ability to host Lumias in a council (they'll work together and argue as they write the story) or combine their physical definitions into a chimera!
- The ability to add fun physical or mental quirks or rules to any Lumia combination at will!
- The ability to save the selected Lumias or Councils in presets that users can load at any time.
- A vastly improved OOC block system over the one included in Lucid Loom with configurable OOC intervals and multiple different styles for how to dress up the OOC block.
- A vastly improved Sovereign Hand that includes the ability to include the last user message in the instructions, exclude the last user message from context, and include automatically generated llm instructions for if you "skip" a sovereign hand turn.
- The ability to trim away lucid loom related tags after a configurable amount of messages.
- Macros to inject all of the above content!

## Non-Loom Specific Features

However it does have a few universally useful features for *any preset* that I'll cover here too like:

- The ability to strip old html, font, and detail tags after a configurable amount of messages.
- The ability to only send the last X amount of user messages to the LLM to save on context.
- The ability to summarize a configurable amount of messages in an easily insertable macro with options to do the summarization manually or automatically. Additionally you can use the main llm or a secondary configured one to do this summarization!
- A wide variety of useful (macros 2.0-ready) macros that include useful functionality.

Whew, that is a lot of features, which means this will be a big guide. But it'll make more sense once you get into it. A lot of the terminology for the Lucid Loom relevant parts will use Loom terminology, so check my [Loom Guide](./LoomGuide.md) for more information!

# Installing Lumiverse Extension

The easiest way to install the extension, is to do the same thing you would to install any other sillytavern extension:

1. In Sillytavern, click the Extensions icon (--Icon here--) in the top bar.
2. Click the install extension button in the top right of the resulting menu.

--Image here--

3. In the resulting menu, paste the url of Lumiverse Helper's github:
```https://github.com/prolix-oc/SillyTavern-LumiverseHelper```
4. Click install (for me or for everyone)

--image here--

5. Refresh the page
6. Enable the "Experimental Macro Engine" in user settings (--Icon here--)

--Image here--

7. Refresh the page one more time!

# Location, Location, Location

Lumiverse lives in two separate places. First, the core configuration options are in the extensions menu. Next, there's a handy sidebar built in react that lets you access functions much faster!

It's worth familiarizing yourself with both, so let's start with the extension menu, as this is where you'll have to go to install custom dlc for Loom!