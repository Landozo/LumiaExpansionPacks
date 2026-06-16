# Lando's Lumiverse Frontend Feedback/Requests

# Point of View/User Profile

I tend to use LLM chats primarily from my mobile phone, connecting to a remote PC Client. I use Android 16/One UI 8.5 on a Samsung S25+, via Chromium based browsers.

I have 8.5k+ characters and 300+ groups. So it's good for stress testing and use cases for mass uses.

---

# UI Positive/Non-Request/ Feedback

## Performance - It zooms

The feedback and responsiveness of the UI flies, even with 8.5k characters and a vast combination of different filters, positive and negative (thanks for adding negative filters so quickly after I requested it, Prolix!). You all NAILED IT with the database schema and performance. I still have yet to test vectorization, but I'm sure it'll be just as fast.

## Migration - It Works Great

Migration works perfectly for characters, lorebooks, tags, and it worked pretty well for groups. I'd maybe suggest a hover tooltip showing how to gen the tag import json in ST, or a link to the guide page for it.

Groups had a few issues with groups not showing up at all unless you searched for them. There was an issue with updated at timestamps being earlier than created at timestamps, but Prolix fixed that already (thanks)! I'll keep doing an investigation and once I nail down specific cases and exact replication steps, I'll post up issues as necessary.

Potential optimizations I can see is to look at the favorites in Sillytavern and mark characters as favorites in Lumiverse, but if I, with hundreds of favorites in Sillytavern, don't mind doing it again in Lumiverse, I imagine most other people wouldn't mind either. Out with the old, in with the new!

## Side Panel/Modals - Excellent Design

The ability to customize tabs is excellent, and I love that settings is always pinned to the right for easy access. Everything is very accessible on mobile and you all did a bang up job.

I like the collapsing of single Lumias and Councils into the same tab, it makes sense from an optimization perspective.

The duplicate option on the connections page is awesome and it makes switching painless.

The option to link presets states to connection profiles is very intuitive and easy to understand, you nailed it from a new user perspective.

## Chat Panel - Really intuitive

I love that the group controls are available right there at the top of the group and you don't have to keep the side panel open to manually send a message from a character or mute.

Hold and tap based controls on mobile is highly intuitive, good job.

---

# UI Requests/Constructive Feedback

## Main Panel

### Option for hiding Recent Chat Thumbnails from Landing Screen

Request: Option to show a text list based recent chat screen on the landing page

Current Behavior: All your previous recent characters/chats show complete with pictures on your main page when loading lumiverse or closing a page.

Purpose: To not get flashbanged by degeneracy on UI load.

Notes: If it's not enough of an issue for most other people to have a use case for adding, I might just make an extension to edit the main page.

## Side Panel

### Profile Pane/Character Edit Screen

#### Profile/Character Edit Add to Favorites Button

Request: An add to favorites button in the details/profile side modal and/or character edit screen.

Purpose: If you are using a character search mode like shuffle and you like the character, when you open up the character search to favorite it, it's long gone due to the shuffle and you have to search to find it again. A star button on the details tab would fix this.

### Character Search

#### Option to keep favorites visible in character search tab

Request: An option to allow characters to remain in the main search even after they are favorited.

Current Behavior: When you favorite a character it disappears from the main tab and moves to the favorites tab only.

Purpose: I usually have hundreds of starred favorites, so I like to be able to keep searching them in the main UI.

#### Option to sort characters by most/least amounts of chats per character

Request: Sillytavern-like

No currently available character sorting by most/least number of chats per character (like in ST) to see the most commonly used characters for familiar use, or the least used for trying new ones.

Notes: Unsure how much query strain this would add/if it's viable while retaining the current lightning speed of the character search panel. Speed beats convenience here imo.


## Chat UI

### Ability to be able to type while previous message is still generating

Request: The ability to type in the grayed out chat box while the previous message is still generating. Typing only, no sending, naturally.

Currently: Message box is grayed out until previous message is 100% done generating.

Purpose: For Lucid Loom based presets, at the end of the previous message, the llm will be churning out end of response trackers, ooc comments, and hidden details, which can take quite a bit on slower llms. During that time, I would usually start typing a response, which is not possible in Lumiverse due to the grayed out box. It makes sense to not allow *sending* a new message while the previous one is genning, but being able to just *prepare/type* a message in the meantime, without allowing the user to hit send, would not seemingly cause any harm. That way the user can simply hit send when the red stop box turns to green.

---

# Loom/Preset Feedback

None Yet! Experimenting with it! I like the structure changes! Old custom edits I made appear to be plug and play, which is nice. Chuckling at level 4: dead dove being enabled by default when imported from Lumihub. Old Prolix habits die hard.

## Implemented

### Negative/Exclusion Filtering for Tags

There is no way to exclude a filter from the character search.

Implemented by Prolix the second I mentioned it, the madman. Tested thoroughly and works great!

## Personal Extension Ideas

### Custom Front Page

I want a text based front page option, if there's no interest, I'll make an extension for it.

### Chub AI Importer

Chub AI importer that uses the API and you can filter out already installed characters. I'll model it after character library probably.

### Dupe checker with customizable sentence similarity slider and A/B Comparisons

I'll model it after character library's or dupe checker addons for ST.