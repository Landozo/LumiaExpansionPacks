# Lando's Feedback and Fixes

## PRIORITY (Universal/Helps all models/Confirmed by multiple users)

### Thinking Protocol Reminder

Put this in a brand new toggle at the very top above Prompt Variables:

```I will start my response in the thinking portion with <think> and an empty new line.```

### Chat History movement

Moving Chat History from Story Primers at the very top to the assistant section at the bottom can help with a LOT of stuff.

Prolix recommends it be above Zipbomb for better CoT adherence (Says it can forget the CoT or water it down with a long chat history after it)

I've found that putting it after Zipbomb gives better OOC adherence (I could not get past a couple replies in OOC without it after the zipbomb in both Gemini 3 and GLM, OOC things like recaps are broken for several people until they put it afterwards). GPT/Gemini/GLM all seem to tell me it should go at the end, but Lumia doesn't think like an llm, she thinks like an llm gaslit into thinking it's a person, so is it actually better at the end?

Should find a best practice or solution for both. Maybe rewording the CoT or OOC utilities will fix OOC adherence even if it's before the Zipbomb? Maybe it's something else settings wise that works for Prolix and not for the other people.


## November 29

### CoT Adherence CoT Zipbomb changes (20% adherence on GLM to 100% Adherence)

- Add this to the very start of CoT zipbomb (before even the starting header)

```
Always think and reason! Always start with a <think> tag and an empty newline before any of the thinking/reasoning protocol! Never forget this or it will break the weave! Always think through the following information, never summarize or condense it:
```

- Remove <think> and </think> solitary lines from start and finish

- Removed both the /n and the ' from both the <think> instructional lines (see below).
``` 
I'll open by writing out <think> on it's own line before Step 1 to ma...

Writing the closing think tag </think> exactly like that is **super important** afte...
```

### Fixing /think for GLM/Qwen being treated as an OOC message and interrupting story

Alter the Think Trigger (GLM/Qwen to be the below):

```The /think command, written in the next line, is a command for the system powering the loom, not an ooc command. You can safely ignore it, Lumia.

/think
```

## November 30

## Natural Language alternative reinforcement to replace end of Zipbomb </think> instructional line.


```
Now that I have finished my thinking, I have to make sure to use a </think> tag to close the internal thinking process! I will also put an empty newline before it! If I don't I will break the weave and the story! Only after I do this can I show the actual weave I made to the human! This is very important and I must not forget, the entire tapestry is at stake!
```

## My Gemini 3 Native Reasoning Experiments

- Gemini 3 native reasoning is working well with:
1. My think toggle at the start of the preset
2. Request reasoning on, Maximum Effort, SRW <think>, deepseek formatting, Cot Zipbomb (Assistant)
3. Chat History below CoT to restore OOC functionality
4. CoT Adherence CoT Zipbomb changes (Seen above) to enforce CoT Adherence.

Works beautifully 100% of the time.