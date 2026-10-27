# game-concept-gate

English | [简体中文](README.zh-CN.md)

A Codex Skill for game concept clarification and project greenlight gating.

It uses a structured ten-question review to turn a vague game idea into a clear, discussable, and testable concept. It prevents formal development from starting before the core gameplay, goals, rules, and player experience are clear and the user has explicitly approved the project.

## Why This Exists

One of the most common game-development failures is starting to code, choose a technology stack, or schedule work before the player's goals, the core loop, and the key decisions are clear.

This Skill turns "clarify the idea before building" into an executable workflow:

- Asks questions in small groups instead of dumping all ten at once
- Converts vague adjectives into concrete, executable rules
- Checks whether goals, choices, costs, and feedback form a coherent loop
- Produces a consistent Game Concept Greenlight Brief
- Blocks formal project development until the user explicitly approves it
- Allows tightly scoped exploratory prototypes without weakening the gate
- Responds in the user's language, including English and Chinese

## Workflow

```text
Draft → Ready for Confirmation → Approved
```

1. **Draft**: information is incomplete or the rules are not executable.
2. **Ready for Confirmation**: all ten topics are answered, no blocking contradiction remains, and the brief is ready.
3. **Approved**: the user has explicitly approved the project and may proceed to MVP, technology, and development planning.

## Installation

Clone the repository into the Codex personal Skill directory:

```bash
git clone https://github.com/George-Zh-Cool/game-concept-gate.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/game-concept-gate"
```

After installation, use it in a new task. If Codex does not discover the Skill immediately, create a new task and try again.

You can also download the repository ZIP and place the directory containing `SKILL.md` at:

```text
~/.codex/skills/game-concept-gate
```

The final directory should look like:

```text
game-concept-gate/
├── SKILL.md
├── README.md
├── README.zh-CN.md
├── .gitignore
├── LICENSE
└── agents/
    └── openai.yaml
```

## Usage

Describe your game idea directly. Codex can select the Skill based on its `description`:

```text
I want to make a single-player turn-based wuxia roguelite, but I have not figured out the core loop yet.
```

You can also invoke it explicitly:

```text
$game-concept-gate I want to make a...
```

## Output

After clarification, the Skill produces:

- Core purpose and target player
- Player mode
- Long-term and short-term goals
- Unique core rules
- Core resources
- Session and meta core loops
- Player actions and key choices
- Public and hidden information
- Core obstacles and sacrifices
- Session and overall end conditions
- Actual play experience
- Major design risks
- Open questions
- Greenlight decision

The final brief is written in the user's language unless they request another language.

## Scope

Use it for:

- New game concept greenlighting
- Gameplay clarification before development
- Gap reviews for an existing design document
- Deciding whether an idea is worth further investment

Do not use it for:

- Open-ended brainstorming or inspiration
- Theoretical comparison of multiple game concepts
- Local implementation work on an approved project
- Bug fixes, balancing, or art changes

## Design Principles

- Do not replace concrete rules with phrases such as "open world," "high freedom," or "immersive."
- Do not present unconfirmed inferences as decisions.
- Do not invent content just to fill a template.
- Do not treat prototype validation as a substitute for a greenlight decision.
- Do not start formal project development before explicit user approval.
- Match the user's language when asking questions and producing the brief.

## Validation

Run the Codex Skill Creator validator:

```bash
python3 "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-creator/scripts/quick_validate.py" \
  "${CODEX_HOME:-$HOME/.codex}/skills/game-concept-gate"
```

A valid Skill prints:

```text
Skill is valid!
```

## Contributing

Issues and pull requests are welcome.

Before submitting a change:

- Keep the Skill's trigger scope precise
- Avoid turning general advice into mandatory rules
- Run `quick_validate.py`
- Test the change against a realistic game idea

## License

This project is licensed under the [MIT License](LICENSE).

You may use, copy, modify, merge, publish, distribute, sublicense, and sell copies of this project, provided that the original copyright and license notices are retained.
