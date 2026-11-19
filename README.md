# PitchSense skills for Claude

**PitchSense is AI sales roleplay: practise a sales call with an AI buyer and get a scored evaluation.** These are the open-source Claude skills for it, made by [PitchSense](https://pitchsense.ai), the company behind pitchsense.ai.

With these skills, Claude becomes a sales practice partner. You pick a roleplay, Claude prepares you, you talk to an AI buyer who pushes back like a real customer, and you get feedback on six sales competencies.

## What is in this repository

| Skill | What it does | Needs |
| --- | --- | --- |
| [`sales-roleplay-basics`](skills/sales-roleplay-basics/SKILL.md) | A typed sales roleplay in chat. Claude plays a made-up buyer, then gives feedback on six selling skills. | Nothing. No account, no connector. |
| [`sales-roleplay`](skills/sales-roleplay/SKILL.md) | The full PitchSense roleplay assessment: prep card, typed warm-up, a voice call with an AI buyer, and a debrief from the scored evaluation. | The PitchSense connector (below). |

Two commands come with them: `/roleplay` starts a roleplay and `/debrief` explains your latest result.

## The six competencies

Every PitchSense evaluation scores the same six, each out of 100:

1. **Call Structure**
2. **Rapport Building**
3. **Discovery**
4. **Objection Handling**
5. **Closing Techniques**
6. **Solution Depth**

Each competency has four criteria, and each criterion is tagged Well Done, Needs Attention or Missed Opportunity, with feedback, evidence from your call and what to improve.

## Who it is for

- **Sales reps** practising discovery, objection handling and closing before a real call.
- **Founders and business owners** practising how to pitch their own product to a busy buyer.
- **Sales managers and enablement teams** who want reps to practise inside the tool they already use.

## Install

**As a plugin (skills, commands and connector together):**

```
/plugin marketplace add pitchsense/pitchsense-skills
/plugin install pitchsense-sales-roleplay@pitchsense
```

**Skills only:** copy the folders under `skills/` into your Claude skills folder, or upload them in Claude under Settings, Capabilities, Skills.

**Connector only:** in Claude, add a custom connector with this address:

```
https://pitchsense-connector.pitchsense.workers.dev/mcp
```

## Try it

After installing, say one of these to Claude:

- "Start my roleplay assessment."
- "I'm a founder. Let me practise pitching to a busy business owner."
- "Help me rehearse a renewal call where the buyer wants a discount."
- "Debrief my last roleplay call."

## How a roleplay runs

1. **Pick.** Claude lists the roleplays and you choose one, or you describe your own call.
2. **Prepare.** Claude gives you a short prep card: who the buyer is, why they took the call, what to bring.
3. **Warm up (optional).** A few typed turns with Claude as the buyer.
4. **Call.** Claude gives you a link. You talk to the AI buyer by voice, hands-free, in your browser.
5. **Debrief.** Claude reads your evaluation and coaches you on the two weakest competencies.

## Good to know

- **Demo mode.** The connector runs as a public demo with made-up buyers, companies and products. There is no login yet, so do not put confidential deal details into it.
- **Practice, not appraisal.** Scores are for your own practice.
- **The buyer is an AI.** It is always described as one.
- **Not affiliated with Anthropic.** Claude is a product of Anthropic. These skills work with Claude; they are not made or endorsed by Anthropic.

## Links

- PitchSense: [pitchsense.ai](https://pitchsense.ai)

## Licence

[MIT](LICENSE). Contributions are welcome; see [CONTRIBUTING.md](CONTRIBUTING.md).
