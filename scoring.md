# Scoring Mechanics

This document details the scoring system for AGI Race: Brinkmanship, including concrete conditions for Presence, Domination, and Control levels.

## Scoring Process Overview

* Scoring is triggered only when a player plays a Domain Scoring card (S01-S05) during their Action Round.
* When a Scoring card is played, the Game Engine evaluates the state of *only* the Hubs belonging to that specific Domain.
* The evaluation determines if each player achieves Presence, Domination, or Control within that Domain.
* VP awards are calculated based on these levels, plus any bonuses.
* The *net* difference in VP is applied to the VP Track.

## I. Conditions for Presence, Domination, and Control

These conditions are evaluated *per Domain* when its scoring card is played:

### 1. Presence

* **Condition:** A player has Presence in a Domain if they **Control** at least **one (1) Hub** within that Domain.
* **Rationale:** Simply having influence isn't enough; you need actual control of at least one key point to be considered a significant player in that domain.

### 2. Domination

* **Condition:** A player achieves Domination in a Domain if they meet **ALL** of the following conditions:
  * **(A) More Controlled Hubs:** They Control more Hubs in that Domain than their opponent.
  * **(B) Presence:** They must also have Presence (Control at least one Hub).
* **Rationale:** Domination signifies a clear, but not total, advantage. Controlling more centers of influence gives a player the upper hand.

### 3. Control

* **Condition:** A player achieves Control of a Domain if they meet **ALL** of the following conditions:
  * **(A) Controls ALL Critical Hubs:** They Control all Hubs within that Domain that have a Stability value of 4 or higher.
  * **(B) More Controlled Hubs:** They Control more Hubs in that Domain than their opponent.
  * **(C) Presence:** They must also have Presence.
* **Rationale:** Complete Control represents near-total dominance, locking down the most resilient and important centers within that sphere of influence.

## II. Victory Point Awards per Level

VPs awarded are based on the highest level achieved by each player in the scored Domain.

| Level Achieved | VP Award |
|----------------|----------|
| **Presence**   | 1 VP     |
| **Domination** | 3 VP     |
| **Control**    | 6 VP     |

* **Mutual Levels:** If both players achieve the same level (e.g., both have Presence but neither Dominates), they both get the VP for that level.
* **Higher Level Prevails:** If one player Dominates and the other only has Presence, the Dominating player gets Domination VP, and the other gets Presence VP. A player achieving Control automatically achieves Domination and Presence, but only scores the VP for Control.

## III. Calculating Net VP Change

1. Calculate USA VPs based on their highest achieved level in the Domain + Bonuses.
2. Calculate China VPs based on their highest achieved level + Bonuses.
3. Calculate `Net Change = China VPs - USA VPs`.
4. Adjust the `gameState.vpTrack` by the `Net Change`. (Positive moves towards China win, negative moves towards USA win).

### Example Scoring Calculation

* **S02: Compute Supremacy** is played. There are 7 Compute Hubs.
  * USA Controls: USC (Stab 4), USD (Stab 4). Total: 2 Hubs.
  * China Controls: CHC (Stab 4), CDS (Stab 3). Total: 2 Hubs.
  * Uncontrolled: TSH (Stab 5), SKM (Stab 4), NLH (Stab 5).

* **Evaluation:**
  * **USA Presence:** Yes (Controls ≥ 1 Hub).
  * **USA Domination:** No (Controls 2, same as China).
  * **USA Control:** No (Does not control all Hubs with Stability ≥ 4).
  * **China Presence:** Yes (Controls ≥ 1 Hub).
  * **China Domination:** No (Controls 2, same as USA).
  * **China Control:** No (Does not control all Hubs with Stability ≥ 4).

* **VP Awards (Before Bonuses):**
  * USA: 1 VP (for Presence).
  * China: 1 VP (for Presence).

* **Bonuses:** Assume USA controls USD which is designated a key semiconductor hub. Bonus +1 VP for USA.

* **Total VPs:**
  * USA: 1 (Presence) + 1 (Bonus) = 2 VP.
  * China: 1 (Presence) + 0 (Bonus) = 1 VP.

* **Net Change:** `China VPs - USA VPs` = `1 - 2` = **-1 VP**.

* **Result:** Move the VP marker 1 space towards the USA side.

## IV. Bonus VP Conditions

These are specific conditions listed on the Scoring cards themselves, adding thematic flavor and strategic targets:

### S01: R&D Dominance
* **Base VPs:** Presence=1VP, Domination=3VP, Control=6VP
* **Bonus:** +1 VP per controlled R&D Hub designated as a "Major University Center" (SVC, ECR, BTH, UKR, CER)

### S02: Compute Supremacy
* **Base VPs:** Presence=1VP, Domination=3VP, Control=6VP
* **Bonus:** +1 VP if player controls the "Critical Lithography Hub" (NLH)
* **Bonus:** +1 VP if player controls the "Leading Foundry Hub" (TSH)

### S03: Policy Leadership
* **Base VPs:** Presence=1VP, Domination=3VP, Control=6VP
* **Bonus:** +1 VP per controlled Policy Hub directly connected to the opponent's "Superpower Space" Hubs

### S04: Public Trust
* **Base VPs:** Presence=1VP, Domination=3VP, Control=6VP
* **Bonus:** +1 VP for every 2 full points the Global Stability Track is above 2 (max +1 VP)
* **Alternative Bonus:** +1 VP per controlled "Major Media Hub" (UCM, CSM)

### S05: Military Integration
* **Base VPs:** Presence=1VP, Domination=3VP, Control=6VP
* **Bonus:** +1 VP if Global Stability is 2 or less
* **Bonus:** +1 VP if player controls more Military Hubs adjacent to opponent-controlled hubs than the opponent does