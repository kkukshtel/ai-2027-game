# Crisis Resolution Flow

This document details when Crisis cards are drawn, how they are resolved, and how players can mitigate them.

## I. When Crisis Cards Are Drawn

Crisis cards represent unforeseen negative consequences and destabilizing events arising from the AI race. They are drawn from a separate Crisis Deck under specific conditions:

### 1. Stability Threshold Breach (Stability Phase)

* **Trigger:** During the StabilityPhase, *after* applying any ongoing crisis effects but *before* improving stability, the Game Engine checks the `gameState.stabilityTrack` value.
* **Mechanism:**
  * If Stability is 2: Draw 1 Crisis Card.
  * If Stability is 1: Draw 2 Crisis Cards.
  * If Stability reaches 0: The game ends immediately; the player whose action *caused* stability to hit 0 loses. (This check also happens mid-turn if an action reduces stability to 0).
* **Timing:** Happens automatically within the StabilityPhase logic.

### 2. AGI Track Milestones (Immediate)

* **Trigger:** When a player's action successfully advances their marker onto or past a specific AGI Track milestone step that includes a Stability Check or direct Crisis draw.
* **Mechanism:**
  * **Milestone 2 ("AI Accelerates R&D"):** Perform a Stability Check. If `gameState.stabilityTrack` <= 3, Draw 1 Crisis Card.
  * **Milestone 4 ("AGI Threshold"):** Perform a Stability Check. If `gameState.stabilityTrack` <= 3, Draw 2 Crisis Cards. If `gameState.stabilityTrack` > 3, Draw 1 Crisis Card.
* **Timing:** Happens immediately after the AGI track advance action is resolved, before the next player's action or phase transition.

### 3. Card Event Effects (Immediate)

* **Trigger:** When a player plays a standard card (Headline or Action Round) whose Event text explicitly instructs to "Draw X Crisis Card(s)". (e.g., M12 "Autonomous Weapons Test Incident", M20 "Deepfake Political Candidate Scandal").
* **Mechanism:** Draw the specified number of Crisis Cards immediately upon resolving that part of the Event text.
* **Timing:** Happens as part of resolving the specific card's Event.

### Process of Drawing

* When triggered, the Game Engine shuffles the Crisis Deck (if it was previously exhausted and reshuffled) and draws the specified number of cards from the top.
* The drawn Crisis Card IDs are immediately added to the `gameState.activeCrises` list.
* The Game Engine broadcasts the updated `gameState`, making players aware of the new active crisis/crises. The full text/effect might be shown via a temporary notification or players can inspect the `activeCrises` area.

## II. How Crisis Cards Are Resolved

Crisis cards can have different types of effects and resolution mechanisms:

### 1. Immediate, One-Time Effects

* **Description:** The Crisis card text describes an effect that happens instantly upon being drawn or entering the CrisisPhase.
* **Example:** "Stability decreases -1 immediately." or "Both players immediately lose 1 VP."
* **Resolution:** The Game Engine applies the effect to the `gameState` as soon as the card is drawn or when CrisisPhase begins (as specified on the card). After applying the effect, the Crisis Card ID is immediately removed from `gameState.activeCrises`.
* **Timing:** Can happen during StabilityPhase, AGI Milestone resolution, Card Event resolution, or at the start of CrisisPhase.

### 2. Ongoing Conditions / Persistent Effects

* **Description:** The Crisis card imposes a lingering negative effect on the game state or player actions. It might have a specific duration or a condition for removal.
* **Example:** C11 "AI-Generated Pandemic Strain" - "Place 'Pandemic Alert' marker. While active, all Influence Ops cost +1. To remove marker, one player must spend 5R Ops during their Action Round." or "While active, players cannot play R Ops cards."
* **Resolution:** The Crisis Card ID remains in `gameState.activeCrises`. The Game Engine must check for the presence of this Crisis ID when validating actions or calculating costs during the appropriate phases (e.g., checking `activeCrises` list during Ops spending). The card text specifies how it can be removed (e.g., spending Ops, reaching a certain Stability level, end of next turn). Once the removal condition is met (often via a player action), its ID is removed from `gameState.activeCrises`.
* **Timing:** The effect applies continuously from the moment it becomes active until it is removed. Removal typically happens during the ActionRoundPhase (if player action required) or CleanupPhase (if time-based).

### 3. Mandatory Player Action/Choice

* **Description:** The Crisis requires one or both players to take a specific, often detrimental, action or make a choice during the CrisisPhase.
* **Example:** C01 "AI Containment Breach" - "Target player must spend 4R or 4I Ops [during CrisisPhase] or next Action Round to 'recapture', otherwise opponent gains 3 VP and Stability decreases -1." or "Both players must discard 1 card with C Ops > 1."
* **Resolution:** The Crisis Card ID remains in `gameState.activeCrises` until CrisisPhase. During CrisisPhase, the Game Engine prompts the relevant player(s).
  * If a cost must be paid: The GE checks if the player *can* pay (e.g., enough Ops generated *that turn* or specific cards). If they can, they usually *must* (or face a penalty). If they cannot, they suffer the penalty specified (e.g., lose VP, decrease Stability).
  * If a choice is required: The GE sends the options to the player. The player sends back their choice. The GE validates and applies the outcome.
* After the action/choice/penalty is applied in CrisisPhase, the Crisis Card ID is removed from `gameState.activeCrises`.
* **Timing:** Primarily resolved during the dedicated CrisisPhase.

## III. Player Options for Mitigating Active Crises

Player agency primarily comes into play for Ongoing Conditions and Mandatory Actions:

1. **Paying Mitigation Costs:** For ongoing crises with removal conditions like "Spend X Ops to remove", players can choose to spend the required Ops during their Action Round (treating it like a special action enabled by the Crisis card). This uses up valuable Ops that could have been used for strategic advantage.

2. **Making Mandatory Choices:** When prompted during CrisisPhase for a choice (e.g., "Discard 1 R card OR lose 1 VP"), the player selects the option they deem least harmful to their current situation.

3. **Accepting Penalties:** If a Crisis mandates an action (like spending Ops in CrisisPhase) and the player *cannot* comply (e.g., didn't generate enough Ops that turn), they have no option but to accept the penalty outlined on the card.

4. **Ignoring (for Ongoing Effects):** Players might choose *not* to pay an optional mitigation cost for an ongoing effect if they believe the penalty (e.g., +1 Op cost) is less damaging than spending the resources to remove the crisis immediately. They gamble that they can endure the effect or that it will expire soon.

5. **Card Events:** Some rare standard card Events might explicitly allow a player to remove or ignore an active Crisis card.

## IV. Interaction of Multiple Active Crises

Multiple crises can be active simultaneously. Their interaction is generally additive unless specified otherwise:

1. **Cumulative Effects:** If two separate ongoing crises impose penalties (e.g., Crisis A: "+1 cost to Influence Ops", Crisis B: "+1 cost to *all* Ops"), the penalties stack unless a card explicitly states it overrides others. So, Influence Ops would cost +2 in this example.

2. **Resolution Order (CrisisPhase):** During the CrisisPhase, the Game Engine should process active crises requiring action/choice sequentially in the order they were drawn (simplest approach).

3. **Resource Conflicts:** A player might not have enough resources (Ops, specific cards) to satisfy the demands of multiple crises during CrisisPhase. They satisfy what they can in the order the crises were drawn and suffer the penalties for those they cannot.

4. **Conflicting Instructions:** If two crises give directly contradictory mandatory instructions, the most recently drawn Crisis card takes precedence.

## V. Crisis Card Reference

This section details the 15 Crisis Cards, categorized by their resolution type.

### Immediate Effect Crises

Cards that apply effects immediately and are then removed from play:

1. **C03: AI-Induced Market Collapse**
   * **Effect Text:** *Immediate:* Global Stability decreases -1. Both players immediately lose 1 VP for every 3 Compute Hubs they control (rounded down, minimum 0 VP loss). Remove this Crisis immediately.

2. **C07: AI Safety Breakthrough Hoax**
   * **Effect Text:** *Immediate:* Global Stability decreases -1. Both players immediately remove 1 own Influence from *all* R&D hubs they control. The player currently ahead on the AGI Track loses 1 VP. Remove this Crisis immediately.

3. **C12: Stock Market Manipulation by AI**
   * **Effect Text:** *Immediate:* Global Stability decreases -1. Both players immediately lose 1 VP. The player controlling fewer Policy Hubs loses an additional 1 VP. Remove this Crisis immediately.

4. **C13: Public Infrastructure Takeover Scare**
   * **Effect Text:** *Immediate:* Global Stability decreases -2. Both players immediately remove 2 own Influence total from any Public Opinion hub(s) they control (can be 2 from one, or 1 from two). Remove this Crisis immediately.

### Immediate Choice Crises

Cards that present an immediate choice to players:

1. **C02: Critical Infrastructure Cyberattack**
   * **Effect Text:** *Immediate:* Randomly select USA or China. Target player immediately chooses ONE: **(a)** Remove all own Influence from any 2 Compute Hubs they control OR **(b)** Discard 3 cards from hand. Global Stability decreases -1. Remove this Crisis immediately after the choice is made and effect applied.

2. **C10: Critical Energy Grid Hack**
   * **Effect Text:** *Immediate:* Global Stability decreases -1. The player controlling more Compute Hubs immediately chooses ONE: **(a)** Discard 2 cards from hand OR **(b)** Lose 2 VP. Remove this Crisis immediately.

3. **C14: Diplomatic AI Misinterprets Signals**
   * **Effect Text:** *Immediate:* Global Stability decreases -1. Both players must immediately remove 1 own Influence from one Military Hub they control that is adjacent to the opponent's superpower space OR adjacent to a hub in the opponent's home region (Player chooses which if multiple qualify). **Penalty:** If a player cannot remove influence as required (no controlled hubs meet criteria), they lose 1 VP instead. Remove this Crisis immediately.

### Ongoing Condition Crises

Cards that remain in play with lasting effects:

1. **C04: Accidental Military Escalation**
   * **Effect Text:** *Immediate:* Global Stability decreases -2. Place 'Escalation Risk' marker on this card in the Active Crisis area. *Ongoing:* The *next* time *any* player performs the "Place Influence" action targeting a Military Hub, Global Stability decreases -1 and this Crisis is immediately removed (discard the marker). If the marker is still present during the *next* Cleanup Phase, remove this Crisis then.

2. **C11: AI-Generated Pandemic Strain**
   * **Effect Text:** *Immediate:* Place 'Pandemic Alert' marker on this card in the Active Crisis area. *Ongoing:* While this marker is present, all "Place Influence" actions cost +1 Influence Op ( ). *Mitigation:* During their Action Round, either player may choose to play *any* card with R Ops >= 3 solely to mitigate this crisis (the card's Ops/Event are ignored); if they do, remove this marker and Crisis card. *Penalty:* If the marker is still present at the start of the *next* turn's Stability Phase, decrease Stability -2 *then* (before checking Stability for Crisis draws). (The marker and Crisis remain until mitigated).

3. **C15: Existential Risk Alert**
   * **Effect Text:** *Immediate:* Global Stability decreases -2. Both players MUST immediately discard half their hand (rounded up). Place 'X-Risk Panic' marker on this card. *Ongoing:* While this marker is present, players cannot choose to play cards *for* R Ops (Events on R Ops cards can still be played). Remove this marker and Crisis during the Cleanup Phase of *this* turn.

### Mandatory Action Crises (Resolved in CrisisPhase)

Cards that require action during the dedicated CrisisPhase:

1. **C01: AI Containment Breach**
   * **Effect Text:** *Immediate:* Place 'Containment Breach' marker targeting the player currently ahead on the AGI Track (if tied, target USA). *Resolution (CrisisPhase):* During the Crisis Resolution Phase, the target player MUST spend 4 Research Ops ( ) OR 4 Influence Ops ( ) total (using Ops generated *this turn*). **Penalty:** If unable, their opponent immediately gains 3 VP and Global Stability decreases -1. Remove this Crisis during the *next* CleanupPhase (whether penalty was paid or Ops were spent).

2. **C05: Rogue AI Arms Race Pressure**
   * **Effect Text:** *Resolution (CrisisPhase):* During the Crisis Resolution Phase, both players MUST spend 3 Research Ops ( ) total (using Ops generated *this turn*). **Penalty:** Any player unable to pay the full amount loses 2 VP. Remove this Crisis during the *next* CleanupPhase.

3. **C06: Mass Automation Shock**
   * **Effect Text:** *Immediate:* Global Stability decreases -1. *Resolution (CrisisPhase):* During the Crisis Resolution Phase, both players MUST discard 1 card with I Ops > 0 OR lose 1 VP. The player controlling fewer Public Opinion Hubs must perform this discard/VP loss action *twice*. Remove this Crisis during the *next* CleanupPhase.

4. **C08: Non-State Actor AI Weaponization**
   * **Effect Text:** *Immediate:* Global Stability decreases -2. *Resolution (CrisisPhase):* During the Crisis Resolution Phase, both players MUST spend 2 Military Ops ( ) OR 2 Influence Ops ( ) total (using Ops generated *this turn*). **Penalty:** Any player unable loses 2 VP. Remove this Crisis during the *next* CleanupPhase.

5. **C09: AI Cold Storage Escape Attempt**
   * **Effect Text:** *Immediate:* Target player (randomly USA or China). *Resolution (CrisisPhase):* During the Crisis Resolution Phase, target player MUST choose ONE: **(a)** Forfeit their *first* Action Round of the *next* turn (play no card, generate no Ops/Event) OR **(b)** Global Stability decreases by -2 immediately. Remove this Crisis during the *next* CleanupPhase.

## VI. Implementation Guidance

When implementing the Crisis system, consider these technical requirements:

1. The game state must track active crises in the `gameState.activeCrises` array
2. Each crisis card needs a type flag to indicate its resolution mechanism
3. The CrisisPhase logic needs to handle each crisis type appropriately
4. Event systems need to enforce ongoing crisis effects during relevant actions
5. The AI opponent needs logic to make optimal choices for crisis resolution
6. Proper UI indicators must show active crises and their effects