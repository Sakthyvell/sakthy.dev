---
author: Sakthyvell Superamaniam
pubDatetime: 2025-07-25T15:22:00Z
modDatetime: 2025-08-08T16:52:45.934Z
title: 'Freudian Rethought: My Ridiculously Simple Attempt at Measuring the Unconscious'
slug: freud-id-ego-superego
featured: true
draft: false
tags:
  - freudian
description:
  My low-tech, high-curiosity take on the id, ego, and superego.
---

Sigmund Freud, often called the father of psychoanalysis, made a bold claim: most of what we do is shaped by forces we can’t see our unconscious mind quietly pulling the strings.  
He divided mental life into three layers:

- **Conscious** – the thoughts and perceptions you’re aware of right now.  
- **Preconscious** – the stuff sitting in the back room of your mind, ready to be recalled if you go looking.  
- **Unconscious** – the deep, hidden vault of wishes, memories, and conflicts you’re not aware of but that still influence you.

Freud also described three characters constantly negotiating inside our head:

- **Id** – the inner wild child, chasing instant gratification.  
- **Ego** – the cool-headed mediator, trying to keep things reasonable.  
- **Superego** – the moral compass, reminding you of the rules and ideals you “should” live by.

Fast-forward to today, and most of psychology politely (or not-so-politely) files Freud’s theories under *pseudoscience*. Modern research prefers data-driven methods especially in cognitive psychology where mental processes can be directly observed and measured. 

Freud’s problem? Not necessarily the concepts themselves, but the fact that they’re hard to measure. The “unconscious” is slippery to turn into numbers. In data terms, this isn’t just a theory problem: it’s a *feature engineering* problem.

So instead of throwing Freud out, I’m treating his ideas as hypotheses to poke at with modern tools. My question: what if we could detect hints of the id, ego, and superego from how someone interacts with a system?  

And no, I’m not starting with brain scans or fancy sensors. I’m starting with the most low-tech, widely used tool in psychology: a questionnaire.

---

## Why questionnaire?

Even though questionnaires aren’t perfectly accurate, they’re interactive, low-friction, and easy to scale. You can get people to engage without them feeling like lab rats, which makes them perfect for quick experiments.

For this first round, I’m sticking to two rules:

1. **Don’t make the goal obvious** – If people know exactly what’s being measured, they might answer in a “socially acceptable” way instead of honestly.  
2. **No single “correct” answer** – Every option should have some weight toward id, ego, and superego, just in different proportions.

---

## How the “science” works (and yes, I’m using quotes)

Right now, my “model” is the simplest thing you can imagine: I made up three numbers for each answer—one for id, one for ego, one for superego.  
You pick your answers, I add up the numbers, and whichever total is highest “wins.”

In machine learning terms, this is the most basic kind of feature engineering:

- **Features** = id, ego, superego  
- **Weights** = me just… making them up  
- **Model** = adding them together and seeing who’s tallest in the leaderboard

It’s basically rule-based scoring with extra drama. The point isn’t to be scientifically bulletproof. It’s to see if I can design questions where the patterns actually look interesting when I stack them up.  

If they do? Cool.  
If not? I’ll tweak the numbers and try again.

---

## A taste of the questions

Here’s what one looks like in JSON form (because I’m a nerd):

```json
{
  "id": 3,
  "text": "You find a wallet with cash and cards on a park bench. It has a business card inside with a number and the owner’s name.",
  "options": [
    { "label": "Call them right away and offer to meet at a café to return it.", "weights": { "id": 0.1, "ego": 0.35, "superego": 0.55 } },
    { "label": "Drop it at the nearest police station and text that info to the number.", "weights": { "id": 0.1, "ego": 0.6, "superego": 0.3 } },
    { "label": "Hold onto it for a day and DM them later when it’s convenient for you.", "weights": { "id": 0.45, "ego": 0.4, "superego": 0.15 } }
  ]
}
```
You answer a bunch of these, I sum the weights, and voilà—you get your “dominant trait” for the day.

---

## The plan
This isn’t deep science. It’s me messing around to see if something interesting pops up when I frame questions in the right way. First version is dead simple because I’d rather get it running and tweak later than overthink it now.

If it works, I’ll try more sophisticated scoring later.
If it doesn’t, I’ll have a nice graveyard of failed ideas to look back on—and maybe steal from—for the next experiment.

Feel free to play around with my demo below and see if you can "uncover your psychic".

<div style="width:100%; height:100vh;">
  <iframe 
    src="https://freud-ego-quiz.vercel.app" 
    width="100%" 
    height="100%" 
    style="border:none;"
  ></iframe>
</div>