# Random Sov Hand Shit for Prolix (3.1.1 Edition)


## Sov Hand vs Continuation Mode (Extension Edition)

Right now in the extension you have two modes for Sov Hand, regular (user last reply) and continuation (char last reply).

Both send out the full sov hand instructions via {{loomSovHand}}. The continuation mode then sends out this blurb about continuation under the sov hand instructions:

<img width="781" height="150" alt="continuationmode" src="https://github.com/user-attachments/assets/c0f4a549-9b35-4b94-9f28-07d642f2c38a" />

These continuation mode instructions are at odds with the instructions sent just before them.

Sov Hand instructions are mostly about echoing human input and elaborating on it.

Continuation mode instructions are about continuing after the previous reply without echoing the last input. If you refer back to human input you risk it traveling back up the chain to the last human input.

This can be solved in a pretty easy way:

**Do not send regular sov hand instructions via {{loomSovHand}} in Continuation mode since they don't apply**

**Only send continuation mode instructions via {{loomSovHand}}**

This way you ensure it only follows continuation mode instructions 100% of the time for continuation mode!

The only thing left to decide is then what it should be able to do in continuation mode, for this there are two options, which I will cover in the next section.



## Should Lumia have control over {{user}} in a continuation turn?

What the title says.

If she has control over {{user}}, like she already does in sov hand, she'll be able to continue to naturally weave their responses to the situation.

If she doesn't, the {{user}} will sit there immobile while everyone around them comments on how they have brain damage and are a mute (This is how successive character replies in human controls user works).

I obviously see that as a problem:

<img width="444" height="784" alt="userbraindead" src="https://github.com/user-attachments/assets/8f8115b1-d9ca-4adb-990f-92d3843ec9e1" />

But do other people see it as a problem? Junigiri suggested polling the sov hand users.

Polling of Sov Hand Users:

<img width="653" height="192" alt="prolixpoll" src="https://github.com/user-attachments/assets/de90f4fa-bcd0-434f-b8d1-94b1e29c3a47" />


People who never use continuation mode at all so it doesn't apply:
- Easy

<img width="311" height="386" alt="easyresponse" src="https://github.com/user-attachments/assets/734ab9c0-ad45-4bb2-a623-bd18ac056f2f" />


People who agree that Lumia should still have control over {{user}} in continuation mode:
- Lando (Hey that's me! Obviously I know what I want! Lumia should be able to have her way with me!)
  
- Eleisea

<img width="476" height="121" alt="eleisearesponse" src="https://github.com/user-attachments/assets/66902985-21c9-444b-841d-f7d299f1816c" />


- Prolix

<img width="350" height="89" alt="prolixresponse" src="https://github.com/user-attachments/assets/3a5b39ac-4732-4dbe-9cb3-d4b248a65127" />

- Suban

<img width="395" height="280" alt="subanreply" src="https://github.com/user-attachments/assets/fa8da080-0bc1-4259-8331-ddbb0928775b" />

- Sezam

<img width="474" height="217" alt="sezamresponse" src="https://github.com/user-attachments/assets/c94080b0-29ef-4172-b1e9-82f1999cf691" />

-Quack

<img width="833" height="124" alt="quackresponse" src="https://github.com/user-attachments/assets/4e58e0f7-138f-4209-a105-fbe8fa72151b" />

- Killpiss

<img width="372" height="82" alt="killpissresponse" src="https://github.com/user-attachments/assets/0e469119-6a42-4afc-95a3-37e960c79359" />


People who said they don't want Lumia controlling user in continuation turns:

- Nobody thus far.



## Smart Changes to Step 7 (Planning Step) for Extension Sov

Currently, step 7 (Planning step, might soon move to step 6 if Prolix goes with my modular suggestion), has ambiguous/conflicting instructions for sov hand and non-sov-hand.

If you were to make a {{loomSovHand_step6}}, or something of the like, you could output a sov hand only planning step for last user replies and a continuation mode/auto weave only planning step for last char replies.

For examples of what specific sovhand and non sov hand planning steps would look like, refer to my step67 and directive overhaul doc, where I give sov hand and auto weave specific planning steps for your perusal.

## Condensing the extension zipbomb and non-extension zipbomb down into a single zipbomb

Right now there is a zipbomb for non-extension sov and a zipbomb for extension sov.

These can be collapsed down into a single zipbomb with a single clever trick.

With my new directive overhaul, it's already obvious that you are only supposed to pick one directive.

<img width="586" height="221" alt="directives" src="https://github.com/user-attachments/assets/f5537788-ac1c-4f69-84f7-714df3a27e36" />


So simply have a Sov Hand (Extension only) toggle that is empty with the following:

```
{{// THIS IS EMPTY, THE EXTENSION HANDLES IT FOR YOU }}{{trim}}
{{// This only exists so you won't pick a directive that has a directive_inst or directive_step6 setvar }}{{trim}}
```

Why add this? To avoid the user leaving the non-extension sov hand on, and thus avoid them filling the vars.

Why would this be a problem with a single zipbomb?

Well to make a single zipbomb, you have to account for both extension and non-extension sovhand, this is pretty easily, simply add the extension sov hand macro after the regular macro in the standard zipbomb *(You already do this for the Lumia part of lumiverse extension in the zipbomb personality matrix, so it's not a new technique)*:

```
**The Rule:** Every checkpoint I process must sound like *me* (or the blended me) having a thought about the story, never like a formal answer to a formal question from the teachers or the Gods'!

{{getvar::directive_inst}}{{loomSovHand}}

### Ground Rules
```

See how it has the sovhand_inst (directive_inst in this case) before the loomsovhand? That means that it will account for both non-extension and extension sovhand.

By having a dedicated extension only sovhand toggle that is actually empty, directive_inst will never be filled and thus only loomSovHand will be inserted.

Viola, one zipbomb, both extension and non-extension!

As for the planning step, if you follow what I said in the previous section (the one about an adaptive planning step/6/7, and use my modular overhaul (see other doc), you can do the same for that.

The entirety of the planning step would become the below:

```
### Step 6: Plan the Actual Content

{{getvar::directive_step6}}{{loomSovHand_step6}}

---
```

Since when the extension toggle is selected, directive_step6 will not be filled, it'll only be loomSovHand. And when the non-extension toggle is filled and sovhand is off in the extension, only directive_step6 will be filled. Ezpz.
