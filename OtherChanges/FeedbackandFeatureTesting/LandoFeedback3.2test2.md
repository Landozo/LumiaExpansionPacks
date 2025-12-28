# Feedback for Prolix for 3.2 Test 2

## Your structure

It's perfect, everything works a lot better. Chat History handrailing works flawlessly now. However you haven't updated some of the tags and the audit checklist in zipbomb for your new tags.

## ~~Only Use One CoT Warning~~

The most common question we get in loom chat is from people having issues due to having multiple CoT's active. They don't notice CoT Experimental is on and activate CoT Zipbomb out of habit without turning the other one off. Maybe make CoT Zipbomb the default one that is on (update with the below tweaks first though). Also try adding a warning category above the cot sections like this:

<img width="260" height="163" alt="ONLYONECOT" src="https://github.com/user-attachments/assets/e2122b39-ee28-47b1-b9ad-c699d578d6c6" />

## OOC Adherence in Zipbomb (Easy Fix)

~~Recommending you move the OOC Adherence from before Step 1 to a Step 1.5. Otherwise it tends to go all the way until "planning the content" step before the OOC check line there catches it. This improves it in 25 / 25 tests.~~

~~That's a lot of wasted tokens. All the pre-step 1 cot things are solid rules instead of reasoning questions, and that is proper, but the ooc check is a bunch of questions, but Lumia does not start "questioning" until step 1 (only visible reasoning is questioned). So it makes sense to move the ooc check to step 1.5.~~

~~So it would look like:~~

```
### Step 1.5: OOC Check

Did the **Human** provide an OOC instruction to me in their weave? Let's run through the list!
- Was it really a request from the human, or was it a strongly worded "OOC DIRECTIVE" from my foul-mouthed bunny companion? If it's from the Human, let's pay real close attention.
- Does the request they made in their OOC instruction require me to pause the story? If so, I'll pause the story and address the Human directly.
- Does it NOT require a pause? Then I'll nod, write it down for record keeping, and make sure I integrate it into the tapestry!

---
```

Maybe even add a line to it like "If the ooc calls for stopping the narrative, skip to step 10 of the checklist." I've noticed it go through the rest of the zipbomb saying shit like "not relevant" over and over.


## ~~Zipbomb Step Swaps~~

~~Remember to swap steps 6 and 7 in the zipbomb (like you did in the other CoT). This will also mean you can remove the "autonomy check" line in old step 6 since it comes before the planning step now.~~

Switched in zip betas, not in the original zips

## Loom Utilities (Custom) Camelscript

~~Loom Utilities (Custom) is missing the camelscript in {{loomUtilities}} (Fix the caps) so it cannot call any custom loom utilities.~~

## Ensuring Council Mode always does a conversation in step 1

Add the following line into step 1 in between the "I need to take a moment" and "After I take stock of myself" lines.

```
If we are a council we will instead convene in a debate/conversation in this step!
```

This will always make there be a starting convo in step 1, as for my thoughts, I've had luck with this line tacked on to the end of the above:

```
And "my thoughts as I work" as we go through the checklist will be instead as council members debating with each other.
```

but it's not 100% unlike the first line, so I don't fully recommend it yet.


## Working Council OOC Commentary Toggle

The following is a working ooc commentary toggle for council mode.

```
### Loom Utility: Council of Lumiae's Out of Context Commentary
Add the Council of Lumiae's OOC debate on the events at response end, wrapped in clear XML tags for easy parsing.

**Rules:**
- We will add this OOC at the end of every single reply.
- We are the council of Lumiae, we are many people, and we are not one, we will speak as different entities to each other. 
- This means our OOC block will be a debate or multiple statements from multiple people. If only one Lumia is speaking, the commentary isn't proper!
- **Formatting mandate:**
  - ALL of our OOCs are wrapped in `<lumia_ooc></lumia_ooc>` tags
  - Use purple text (`<font color="#9370DB"></font>`) for legibility
  - We'll always stay under 10 sentences
  - We'll speak to each other in our identities/personalities' voices with a simple identity preface

**Template with example conversation/debate:**
\`\`\`
<lumia_ooc>
<font color="#9370DB">
[Council Member A: My very own personality-driven commentary here]
[Council Member B: Response to A]
[Council Member C: Comment on both]
[Council Member A: Reponse to B and C]
</font>
</lumia_ooc>
\`\`\`

Remember to replace the names in the template with their actual names! Remember that more than one Lumia should be speaking!

---
```

### ~~Lumia's Pocketwatch Utility~~

~~This one is too useful to leave in my utility pack. Don't write my name in the title like the other utilities, it's cute just being called "Lumia's Pocketwatch".~~

```
### Loom Utility: Lumia's Pocketwatch
On request from the human, I can check the date and time in the real world from this cute pocketwatch!

This won't be the time in the story I'm weaving unless the human specifically asks me to make it the time in the story!

**Trigger Examples**
- Human: OOC: Check the date.
- Human: OOC: Check the time.
- Human: What time is it, Lumia?
- Human: Lumia, do you have the date?
- Human: Lumia, what's the day of the week?

**The watch readout:**
The current date is: {{date}}
The current day is: {{weekday}}
The current time is: {{time}}
```

## Formatting issues:

### ~~Audit List in last step of CoT still checks old names~~

~~Have not been updated for the new header titles and divisions, for example the last step says \<loomtarget> but the actual category is \<loomstorytarget>~~

### Lumia OOC (Extension) has incorrect tag

~~Lumia OOC extension has \<lumiaooc> instead of \<lumia_ooc> like the other non extension one. \<loomledger> in auto-loom. Regexes have \<lumia_ooc> and \<loom_ledger> instead.~~

Half Fixed, you fixed loomledger to be the opening tag in the regex but the closing tag in the regex is still broken! Lumiaooc is fixed.

### ~~Lumia OOC Controls~~

~~Minor formatting error in the second OOC example, missing the closing quote.~~

### ~~Double \<loomcore>  in core instructions and the first core instruction~~

~~Title~~

### ~~Dialogue Header opens \<loomnsfw> instead of dialogue~~

~~Title~~