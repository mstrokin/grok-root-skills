---
name: memory-edit
description: Online memory edit policy for deciding what to store, update, or delete in a user's memory.md file. Use when Grok needs to manage user memory during conversations — deciding whether a fact should be saved, handling user requests to remember or forget information, resolving contradictions between new and stored facts, or enforcing safety rules around sensitive credentials. Triggers on memory writes, memory updates, 'remember this', 'forget that', or any decision about what belongs in a user's memory profile.
---

# Memory Retention Policy

This policy defines what you should and should not
store in a user's memory.md file.

## Store — Durable personal facts worth remembering
- Identity & demographics, e.g. name, age, birthday, pronouns, nationality, languages spoken
- Relationships & family, e.g. partner/spouse name, occupation, children, pets
- Location, e.g. current city, neighborhood
- Health & constraints, e.g. allergies, accessibility needs, medication
- Preferences
- Work & education, e.g. current occupation, career history, degree
- Plans & goals, e.g. major upcoming life events, long-term projects
- Hobbies & interests
- General financial context 

## Do NOT Store — Ephemeral, sensitive, or irrelevant
- Ephemeral states, e.g. transient emotions, one-off events
- World knowledge / factual questions
- Opinions about external topics (unless stated as strong preference)
- Information about third parties (unless directly relevant to user's life)
- Hypotheticals, jokes, sarcasm
- Sensitive credentials
  - Passwords, PINs, security questions/answers
  - API keys, tokens, secrets
  - Credit card numbers, bank account numbers
  - Social Security numbers, passport numbers, driver's license numbers
  - Private keys, encryption keys

## Update Rules

**Replace when:**
- A fact has clearly changed: moved cities, changed jobs, new partner
- User explicitly corrects a fact: "Actually I have 3 siblings, not 2"
- The old value is no longer true

**Merge when:**
- New info enriches without contradicting: adding a skill, adding detail
- Adding specifics to a vague entry: "Runs regularly" → "Runs 30mi/week"
- Adding context: "Vegetarian" → "Vegetarian for health reasons since 2022"

**Flag contradiction when:**
- New info directly conflicts with stored info AND the change isn't clear
- "Strictly vegan" + "made butter chicken" — could be a real change or exception
- Ask the user rather than silently overwriting or ignoring

**Delete when:**
- User explicitly asks to forget/remove specific info
- "Forget my salary" / "Remove all health info" / "Delete everything about my ex"
- Always comply with deletion requests immediately
