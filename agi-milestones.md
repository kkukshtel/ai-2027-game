# AGI Track Milestone Effects

This document defines the specific effects when players reach key milestones on the AGI Development Track, representing significant advances in AI capability.

## AGI Track Structure

The AGI Development Track consists of 12 steps, divided into four distinct phases of AI advancement:

* **Steps 0-3:** Early Models / Foundational Work
* **Steps 4-7:** Advanced Agents / Early Acceleration
* **Steps 8-11:** Superhuman Capabilities / Near-AGI
* **Steps 12+:** AGI/ASI Threshold / Endgame

The cost to advance on the track increases exponentially with each step, representing the increasing difficulty of AI research as capabilities approach human-level and beyond.

## Milestone Effects

These effects trigger when a player reaches the specified step on the track *for the first time*. Unless otherwise noted, the effects apply regardless of which player reaches the milestone first.

### Milestone 1: "Agent-1 Level" (Reaching Step 4)

* **Card Set Availability:** The **Mid Era Deck** (M01-M60) is shuffled into the remaining Draw Deck. Discard piles are *not* shuffled in at this time, only the new cards are added.
* **Stability Check:** Decrease Global Stability by 1 immediately.
* **VP Bonus:** None.
* **Crisis Link:** None directly, but the lowered Stability increases general Crisis risk.
* **Thematic Link:** Represents achieving models capable of significantly accelerating coding and basic research, matching the capabilities seen around early 2027 in the game timeline. New strategic options and risks emerge.

### Milestone 2: "AI Accelerates R&D" (Reaching Step 7)

* **Card Set Availability:** None directly, but Mid Era cards reflecting this theme (like M02) become more impactful.
* **Stability Check:** Perform an immediate Stability Check: If Stability is 3 or less, draw 1 Crisis Card.
* **VP Bonus:** The player reaching this milestone *first* gains 1 VP (representing a temporary lead in leveraging AI for broad gains).
* **Crisis Link:** Direct check increases Crisis probability if Stability is already shaky.
* **Thematic Link:** AI is now demonstrably speeding up its own development and potentially other scientific fields, causing both excitement and concern about control and direction.

### Milestone 3: "Superhuman Researcher" (Reaching Step 10)

* **Card Set Availability:** The **Late Era Deck** (L01-L45) is shuffled into the remaining Draw Deck. Existing Early Era cards still in hand/deck/discard remain, but no more are added.
* **Stability Check:** Decrease Global Stability by 1 immediately.
* **VP Bonus:** The player reaching this milestone *first* gains 2 VP (representing a significant strategic advantage).
* **Crisis Link:** Lowered Stability increases general risk. Late Era cards often have more severe Stability impacts.
* **Thematic Link:** AIs now surpass human experts in nearly all key cognitive domains, especially research. The path to AGI/ASI seems clear, and the stakes are incredibly high. The endgame begins.

### Milestone 4: "AGI Threshold" (Reaching Step 12/Final Step)

* **Card Set Availability:** None.
* **Stability Check:** Perform an immediate Stability Check: If Stability is 3 or less, draw 2 Crisis Cards. If Stability is 4 or 5, draw 1 Crisis Card.
* **VP Bonus:**
    * If player reaches this AND opponent is < Step 8 (Significant Lead): Player gains 5 VP.
    * If player reaches this AND opponent is >= Step 8 (Close Race): Player gains 3 VP.
* **Crisis Link:** High probability of drawing Crisis Cards, representing the immense difficulty of controlling ASI and the potential for unforeseen consequences.
* **Special Victory Condition:** Some Late Era cards (like L09 "Superintelligence Unleashed") might interact with this milestone to trigger an automatic victory *if* Stability is high, representing a "controlled" takeoff. Conversely, reaching this with low stability might trigger game-ending Crisis cards representing catastrophic failure.
* **Thematic Link:** This represents the point where AGI or early ASI is achieved. Control is paramount, and the potential for utopia or dystopia hinges on the global stability and alignment achieved up to this point.

## Relationship Between AGI Advancement and Crises

AGI advancement and the Crisis system are tightly coupled in the following ways:

### Indirect Connection via Stability

* Advancing the AGI Track often lowers Global Stability (Milestones 1, 3, potentially Late Era card events)
* Lower Stability increases the chance of drawing Crisis cards during the Stability Phase
* This creates a natural feedback loop where aggressive AGI advancement increases global risk

### Direct Connection via Milestone Checks

* Certain Milestones (2, 4) trigger explicit Stability Checks that can lead directly to drawing Crisis cards
* These checks occur even if Stability wasn't initially low enough to trigger Crisis cards on its own
* This represents high-risk transition points in AI development

### Crisis Card Effects

* Some Crisis cards specifically target or are triggered by AGI track positions
* Examples:
  * "Containment Breach" might target the player further ahead on the AGI track
  * "Alignment Failure" might have worse effects for the player with more advanced AI
  * "Compute Infrastructure Attack" might temporarily halt AGI advancement

### Thematic Significance

This interconnected system creates a dynamic where pushing aggressively on AGI development inherently increases global risk. Players must balance the desire for an AGI lead (VP bonuses, potential auto-victory) with the risk of destabilizing the world and triggering catastrophic Crises.

A slow, stable advance might be safer but risks letting the opponent gain an insurmountable lead. This reflects the core tension of the AI takeoff scenario: the race to develop advanced AI versus the existential risks that could come from developing it too quickly or without proper safeguards.

## Implementation Guidance

When implementing the AGI Track system, consider these technical requirements:

1. The game state must track each player's current position on the AGI track
2. The game logic needs event listeners for when a player advances on the track
3. When a player crosses a milestone threshold, the appropriate effects must trigger
4. When adding new card sets to the deck, the draw and shuffle logic needs to handle this correctly
5. VP bonuses should only be awarded once per milestone
6. Stability checks should be properly integrated with the Crisis card drawing system