---
description: Fetch the result of your latest PitchSense roleplay call and explain it
---

Debrief my latest roleplay call.

Follow step 5 of the `sales-roleplay` skill. Use the attempt id of the most recent call started in this conversation. If there is none, ask me for the call link and take the id from its last path segment. Call `get_call_result`. If the call is not scored yet, say so and offer to check again. If it is scored, give the full debrief.
