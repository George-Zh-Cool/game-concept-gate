---
name: game-concept-gate
description: "Clarify a game concept and gate project development through a structured ten-question review; supports English and Chinese requests for game concept clarification and project greenlighting. Use when a user wants to make a new game, prepare a greenlight decision, or asks to begin development before the core loop, goals, rules, or player experience are clear. Do not use for open-ended brainstorming, idea comparison, theoretical game analysis, or implementation work on an already-approved project."
metadata:
  short-description: "Game concept clarification and greenlight gate"
  version: "1.2.0"
---

# Game Concept Gate

## Purpose

Turn a vague game idea into a clear, discussable, and testable concept, then decide whether it is ready for formal project greenlighting and development.

This Skill does not invent a complete game for the user. It confirms:

- Why the game exists and who it is for
- What the player actually does and what the core loop is
- Why the core rules work
- Whether goals, choices, costs, and feedback form a coherent loop
- Whether the user has explicitly approved the project

## Response Language

Match the user's language. If the user writes in Chinese, ask questions and produce the final brief in Chinese. If the user writes in English, use English. Preserve game titles, proper nouns, and terminology the user has already established.

The checklist in this file may remain in English; do not make the user read internal instructions in a different language.

## When to Use

Use this Skill when:

- The user has a new game idea and wants to turn it into an executable concept
- The user is preparing a greenlight decision
- The user asks to start development before the core gameplay, goals, or rules are clear
- The user has a design document but needs a gap, contradiction, or feasibility review

Do not start the full ten-question process when:

- The user only wants open-ended brainstorming, inspiration, or concept comparison
- The user is discussing game theory, writing analysis, or reviewing games
- The project is already approved and the task is implementation, bug fixing, balancing, or art
- The user only asks about a specific gameplay mechanic outside a new project decision

If the intent is between exploration and greenlighting, ask whether the user wants to keep exploring or enter the greenlight review. Do not start the gate without that distinction.

## Gate States

Use three explicit states:

- **Draft**: unanswered or non-executable information remains; not ready for development
- **Ready for Confirmation**: all ten topics are answered and no blocking contradiction remains; the concept brief is ready
- **Approved**: the user has explicitly approved the project and may proceed to scope and development planning

In multi-turn conversations, begin each response with a compact status:

```text
Status: Draft
Answered: 4/10
This turn: Fill gaps in information, obstacles, and end conditions
```

Do not replace these states with vague phrases such as "mostly clear" or "probably ready."

## Hard Gate

Before the state reaches **Approved**, do not start formal:

- Project repository or engine setup
- Production technology selection
- Development task breakdown
- Development scheduling or resource commitments
- Final art, monetization, or publishing commitments

All of the following must be true:

1. All ten questions have specific, executable answers.
2. No unresolved contradiction blocks the concept.
3. A complete concept brief has been produced.
4. The user explicitly says the project is approved or gives equally clear confirmation.

When the user has not confirmed, only continue asking questions, summarize, identify contradictions, offer options, or draft the concept brief. Do not treat urgency as confirmation, and do not convert assumptions into established decisions.

### Exception: Exploratory Prototype

If the user explicitly asks for a prototype to validate an unknown gameplay assumption, allow a small, time-boxed exploration only when:

- It is clearly identified as a one-off validation, not a production project
- The question to validate, time limit, and stopping condition are defined
- Temporary technology choices are not treated as production commitments
- The result returns to the concept gate for an updated decision

Do not let an exploratory prototype expand into product development, and do not use "build it first" to avoid unresolved design questions.

## Workflow

### 1. Review Existing Information

Organize what the user has already provided.

- Do not repeat questions that have already been answered.
- Label reasonable but unconfirmed inferences as **Provisional**.
- Do not ask for information that has no effect on the current decision.
- If the user provides a complete design document, do not replay every question; audit gaps and contradictions directly.

### 2. Ask in Groups

Do not send all ten questions at once. Use three groups with no more than three or four questions per group:

**Group 1: Purpose and Goals**

- Core purpose and target player
- Single-player or multiplayer mode
- Long-term and short-term player goals

**Group 2: Gameplay and Decisions**

- Unique core rules
- Resources the player controls
- Player actions, choices, and costs

**Group 3: Information, Obstacles, and Experience**

- Public and hidden information
- Core obstacles and sacrifices
- End conditions and victory conditions
- Actual play experience and the complete core loop

If the user answers several questions at once, organize the answers and ask only for the gaps.

If the user does not know how to answer, do not repeat the same empty question. Offer two or three concrete options, explain their tradeoffs, recommend one direction, and mark it as requiring confirmation.

### 3. Sharpen Vague Answers

If an answer cannot become a concrete rule, keep asking.

For example, if the user says "players can freely explore the world," ask:

- What exactly do they explore?
- What choice do they make during each exploration?
- How does exploration advance the long-term goal?
- What do they lose when they fail or choose poorly?

Do not treat adjectives such as "open world," "high freedom," "immersive," or "rich gameplay" as design conclusions.

### 4. Check for Contradictions

Check at least these relationships:

- Purpose, target player, and core experience align
- Single-player or multiplayer mode supports the core rules
- Short-term goals serve the long-term goal
- Unique rules actually change player decisions
- The resource system creates meaningful tradeoffs
- Obstacles prevent the player from reaching the goal too directly
- Hidden information creates reasoning, risk, or strategic play rather than confusion
- End conditions match the intended experience
- The core loop can work within the stated session length

When a contradiction appears, do not make a major decision for the user. Explain the conflict, offer two or three directions, and ask for confirmation.

### 5. Produce the Concept Brief

Use this structure:

# Game Concept Greenlight Brief

## Status
Draft / Ready for Confirmation / Approved

## Core Purpose and Target Player

## Player Mode

## Player Goals
- Long-term goal
- Short-term goals

## Unique Core Rules

## Core Resources

## Core Loop
- Session loop
- Meta loop, if any

## Player Actions and Key Choices

## Information Structure
- Public information
- Hidden information
- How hidden information is discovered

## Core Obstacles and Sacrifices

## End and Victory Conditions
- Session end
- Overall game end
- Failure and restart

## Actual Play Experience

## Major Design Risks

## Open Questions
- Issues blocking greenlight
- Questions that can be tested with a prototype

## Greenlight Decision
- Proceed to greenlight / Revise and reassess / Do not proceed
- Rationale

Use only content the user has confirmed. Mark all inferences as **Provisional**. Never invent answers just to fill the template. Translate the brief into the user's language unless they request another language.

### 6. Request Explicit Confirmation

After the brief is complete, tell the user:

- What has been confirmed
- What remains provisional
- Which design risks remain
- Whether the next stage is recommended

Then explicitly ask whether the project is approved.

Only after explicit approval may the conversation continue into:

- MVP scope
- Target platform
- Team size
- Budget and schedule
- Technology stack
- Art direction
- Development milestones

## The Ten Questions

1. **Core purpose**: Why make this game? Who is the target player? What core experience should they have? What counts as success?
2. **Player mode**: Single-player, multiplayer, co-op, competitive, asynchronous, or another form? How do players interact, and why does that mode support the core experience?
3. **Player goals**: What are the long-term and short-term goals? How do short-term actions move the player toward the long-term goal?
4. **Unique core rules**: Which rules distinguish the game from other works? Which actual player decisions do they change, beyond theme or content differences?
5. **Core resources**: Which scarce resources can the player control, gain, spend, or allocate? What does it cost to obtain or lose them?
6. **Actions and choices**: Which actions does the player repeat? Where are the key decision points? What does each choice give up or put at risk?
7. **Information structure**: What is public and what is hidden? How does the player discover hidden information, and why is it hidden?
8. **Obstacles and sacrifices**: What core obstacle prevents the player from reaching the goal? What is lost on failure? Which resources, opportunities, or routes must the player give up?
9. **End conditions**: How does a session end, and how does the overall game end? What are the victory, failure, draw, and restart conditions? Is there any meta progression or inheritance?
10. **Play experience**: What does the player see, do, decide, and receive as feedback?

Adapt question 10 to the game type:

- Turn-based game: describe one or two complete turns, including player actions, opponent or system responses, resource changes, key decisions, and feedback.
- Non-turn-based game: describe the first five to ten minutes of play, including what the player sees, does, decides, and receives as feedback.
- If the game has both session and meta loops, describe both and explain how they affect each other.

## Completion Criteria

The concept phase is complete only when all of the following are true:

- All ten questions have concrete answers
- Core rules can actually be executed
- The core loop works within the intended session length
- Player choices have explicit costs
- Goals, obstacles, and victory conditions form a closed loop
- No blocking contradiction remains
- A concept brief has been produced
- The user has explicitly approved the project

## Do Not

- Start formal development while the core concept remains unclear
- Replace concrete design with generic game terminology
- Invent core gameplay the user has not confirmed
- Skip the gate because the user is impatient
- Treat "not decided yet" as "already clear"
- Disguise an exploratory prototype as formal project development
- Fill empty template sections with fabrication
