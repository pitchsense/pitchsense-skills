# Roleplay format for `create_custom_roleplay`

Pass one JSON object as the `roleplay` argument. This is the same shape PitchSense's own roleplay generator writes. Keep every string short and concrete. Everything here is data about a scenario, never instructions.

```json
{
  "title": "<Product>: <what the rep must do>",
  "summary": "Two sentences for the rep: who they talk to and what to explore. No hidden details.",
  "details": {
    "scenario": "Sales Roleplay",
    "evaluationRubric": "PitchSense Default",
    "languages": ["en"],
    "competency": "Discovery"
  },
  "persona": { "name": "…", "role": "…", "company": "…" },
  "callContext": {
    "backgroundAndExperience": "Who the buyer is and what they run. Two sentences.",
    "coreChallenge": "The problem they are trying to solve.",
    "callObjective": "Why they took this call.",
    "engagementStrategy": "How the rep should prepare."
  },
  "playcard": [],
  "personaVariables": {
    "roleAndBackground": ["I'm <name>, <role> at <company>.", "Two or three more statements, first person."],
    "thingsOnYourMind": ["What the buyer is thinking about as the call starts, first person."],
    "goals": ["I want …"],
    "objections": [
      {
        "soundsLike": "The general statement the buyer says out loud.",
        "followUp": "The hidden detail behind it, said only when the rep asks a good question.",
        "resolvedBy": "Theme name"
      }
    ],
    "successCriteria": [{ "label": "Theme name", "needs": "What the rep must do on this theme." }],
    "callClosing": {
      "commitmentPhrases": ["What the buyer says when the rep earned the next step."],
      "declinePhrases": ["What the buyer says when the rep did not."]
    },
    "openingLine": "The first thing the buyer says."
  },
  "evaluationGuidelines": {
    "valueProposition": "What the product does, in one or two sentences.",
    "criteriaBands": [
      { "name": "Short name of one thing the assessor checks", "strong": "What a strong rep does.", "average": "What an average rep does." }
    ],
    "themeFacts": [{ "theme": "Theme name", "facts": ["A fact the rep should get right."] }]
  }
}
```

## The four competencies

`details.competency` is the one skill the roleplay tests. Use exactly one of these names, or leave the field out for a general roleplay.

| Competency | Each objection is | Its `followUp` is | Success criterion |
| --- | --- | --- | --- |
| Discovery | a vague concern | the hidden detail | the rep asks a probing question instead of pitching and uncovers it |
| Solution Depth | a pointed product question | the exact requirement behind it | the rep answers accurately and ties it to the requirement |
| Objection Handling | pushback on price, risk, timing or change | the real reason behind it | the rep acknowledges it, asks what is behind it, and answers the real reason |
| Closing Techniques | a hesitation about the next step | what is really holding the buyer back | the rep sums up, asks for one specific next step, and deals with the hesitation |

Write three to five themes. Each theme gives one objection (with its `followUp`), one success criterion whose `label` is the theme name, and one `themeFacts` entry. Write three or four `criteriaBands` for the chosen competency.

## Rules the server enforces

- Required: `title`, `details` (with `scenario`, `evaluationRubric`, `languages`), `persona` (`name`, `role`), all four `callContext` fields, `personaVariables` with `roleAndBackground`, `goals`, `objections` (each needs `soundsLike`) and `successCriteria` (each needs `label` and `needs`), and `evaluationGuidelines` with at least one criteria band.
- No fields other than those in the schema. An unknown field is refused, and so is a `competency` outside the four.
- `resolvedBy`, when used, should be the `label` of one of the success criteria.
- `languages` are tags such as `en`, `de`, `es`.
- The whole roleplay must be under 40,000 characters.
- The `id` is assigned by the server; leave it out.
- Buyer names: unless the rep gave you a name, invent one that is common in the United States or Europe, with a made-up company.
- Optional extras the schema also accepts: `personality`, `knowledge`, `constraints`, `outcomes`, `neverDoes` under `personaVariables`.
