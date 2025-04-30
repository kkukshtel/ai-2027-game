**Card Properties Legend:**

*   **ID:** Unique identifier (E=Early, M=Mid, L=Late, S=Scoring, C=Crisis)
*   **Name:** Thematic card title.
*   **Affil:** Affiliation (USA, CHN, NEU)
*   **Ops:** Operations Points (R=Research , C=Compute , I=Influence )
*   **Event Text:** Description of the card's event effect. Keywords like `Place X Influence`, `Remove Y Opponent Influence`, `Advance AGI Track`, `Modify Stability +/- X`, `Gain X VP`, `Discard`, `Draw Card`, `Cancel Event`, `May`, `Must`.
    * **Note on Influence Placement in Events:** When a card allows placing influence in a specific hub, this IGNORES the normal adjacency requirement unless specifically stated otherwise. However, it still follows the regular control-based cost calculation (1 Op for uncontrolled/friendly hubs, 2 Ops for enemy-controlled) when determining how many influence points can be placed.
*   **Flags:**
    *   `SCORING`: This is a scoring card.
    *   `REMOVE`: Remove from game after Event play.
    *   `PERSISTENT`: Effect lasts until cancelled (place marker).

---

**Early Era Cards (E01 - E45) ~ Foundations & Early Jitters (2025-2026)**

*(Focus: Establishing base, initial models, hardware controls, early safety/policy talks, coding assistants)*

1.  **E01: Foundational Model Leap (GPT-6/Gemini-2 Equiv)** (NEU) | Ops: 3R | Event: Both players advance AGI Track by 1.
2.  **E02: Domestic Chip Act (USA)** (USA) | Ops: 3C | Event: Place 2 USA Influence in USA Compute Hubs (max 1 per). USA gains "Compute Subsidies" marker: Next 2 USA actions spending only get +1 Op value. `REMOVE`
3.  **E03: National AI Initiative (CHN)** (CHN) | Ops: 3I | Event: Place 3 CHN Influence in CHN Policy Hubs (max 2 per). China gains "State Coordination" marker: Once per turn, may spend 1I instead of 1C for an action. `PERSISTENT`
4.  **E04: Export Controls Imposed (USA)** (USA) | Ops: 2I | Event: China cannot use Ops from USA cards next turn. If China has more Compute Hubs controlled than USA, Decrease Stability -1.
5.  **E05: Circumventing Controls (CHN)** (CHN) | Ops: 2C | Event: Ignore USA "Export Controls Imposed" event if active. Gain 1 temporary Compute Op this action.
6.  **E06: AI Safety Summit I (NEU)** (NEU) | Ops: 1I | Event: Both players MUST reveal 1 card from hand. Advance Stability +1. Player with higher revealed Ops value may place 1 Influence in any Policy Hub.
7.  **E07: Rise of Coding Assistants (NEU)** (NEU) | Ops: 2R | Event: Both players may immediately spend 1R Op to advance their AGI Track.
8.  **E08: University Partnerships (USA)** (USA) | Ops: 2R | Event: Place 2 USA Influence in USA R&D Hubs. Draw 1 card.
9.  **E09: Military AI Research Lab (CHN)** (CHN) | Ops: 2I | Event: Place 2 CHN Influence in CHN Military Hubs. May spend 1R Op now.
10. **E10: Public Job Displacement Fears (NEU)** (NEU) | Ops: 1I | Event: Decrease Stability -1. The player controlling more Public Opinion Hubs may place 1 Influence in any non-controlled Public Opinion Hub.
11. **E11: Venture Capital Boom (USA)** (USA) | Ops: 3R | Event: Place 1 USA Influence in any 3 different R&D Hubs worldwide (max 1 per).
12. **E12: State-Backed AI Champions (CHN)** (CHN) | Ops: 3C | Event: Place 3 CHN Influence in any CHN Compute Hub.
13. **E13: EU AI Act Analogue (NEU)** (NEU) | Ops: 2I | Event: Place 2 Influence (USA or CHN, player chooses) in EU Policy Hub. Next card played by either player with Ops >= 3 costs 1 additional Op of any type to play for Ops.
14. **E14: Open Source Breakthrough (NEU)** (NEU) | Ops: 2R | Event: Player whose AGI Track marker is behind may advance AGI Track by 1. If tied, USA advances.
15. **E15: Hardware Supply Chain Snag (NEU)** (NEU) | Ops: 1C | Event: Both players randomly discard 1 card with a C value > 0 from hand. If a player cannot, they lose 1 VP.
16. **E16: Elite Talent Poaching (USA)** (USA) | Ops: 1I | Event: Remove 1 CHN Influence from any R&D Hub, then place 1 USA Influence in any R&D Hub.
17. **E17: Returning Scholars Program (CHN)** (CHN) | Ops: 1I | Event: Remove 1 USA Influence from any R&D Hub, then place 1 CHN Influence in any R&D Hub.
18. **E18: Early Alignment Research (NEU)** (NEU) | Ops: 1R | Event: Advance Stability +1. Player may discard 1 card to draw 1 card.
19. **E19: Misinformation Campaigns (NEU)** (NEU) | Ops: 2I | Event: Choose USA or China. Target player removes 2 Influence from Public Opinion Hubs they control. Decrease Stability -1.
20. **E20: Cloud Infrastructure Deal (USA)** (USA) | Ops: 2C | Event: Place 2 USA Influence in any non-CHN Compute Hub.
21. **E21: Belt and Road AI Integration (CHN)** (CHN) | Ops: 2I | Event: Place 2 CHN Influence in any non-USA Policy or Compute Hub in Asia or Africa.
22. **E22: Stumbling Agents Released (NEU)** (NEU) | Ops: 1I | Event: First public release of basic agents. Place 1 Influence for each player in any Public Opinion Hub they don't control. Decrease Stability -1.
23. **E23: Algorithmic Trading Gains (NEU)** (NEU) | Ops: 2C | Event: Player controlling more Compute Hubs gains 1 VP.
24. **E24: Cybersecurity Framework Mandate (USA)** (USA) | Ops: 2I | Event: Advance Stability +1. Place 1 USA Influence in USA Policy Hub.
25. **E25: Great Firewall AI Upgrade (CHN)** (CHN) | Ops: 2I | Event: Place 1 CHN Influence in CHN Policy Hub. USA events targeting Public Opinion Hubs in China have no effect next turn.
26. **E26: Initial Bioweapon Defense Research (USA)** (USA) | Ops: 1R | Event: Place 1 USA Influence in USA Military Hub.
27. **E27: AI Ethics Board Established (NEU)** (NEU) | Ops: 1I | Event: Place 1 NEU Influence (represented by marker, counts for neither player scoring but blocks) in any Policy Hub. Advance Stability +1.
28. **E28: GPU Shortages (NEU)** (NEU) | Ops: 1C | Event: The next card played by each player for C Ops provides 1 less C Op.
29. **E29: Deepfake Technology Proliferation (NEU)** (NEU) | Ops: 1I | Event: Decrease Stability -1. Each player removes 1 Influence from any Public Opinion Hub.
30. **E30: Quantum Computing Scare (NEU)** (NEU) | Ops: 1R | Event: Player with higher AGI Track position must discard 1 card with R Ops > 1. If tied, both discard.
31. **E31 - E35:** Low Ops cards (1-2 Ops) with minor influence placement/removal events in specific regions/domains. (Fill with thematic names like "Silicon Valley Startup", "Shenzhen Hardware Market", "Brussels AI Forum", "AI in Media", "Drone Swarm Test").
32. **E36 - E40:** Neutral cards (2-3 Ops) offering tactical flexibility or minor stability adjustments. (Fill with thematic names like "Academic Collaboration", "UN AI Panel", "Economic Forecast", "Standardization Efforts", "Data Privacy Concerns").
33. **S01: R&D Dominance** (NEU) | Ops: 0 | Event: Score R&D Hubs. Presence=1VP, Domination=3VP, Control=5VP. Bonus +1VP per controlled University Hub. `SCORING`
34. **S02: Compute Supremacy** (NEU) | Ops: 0 | Event: Score Compute Hubs. Presence=2VP, Domination=4VP, Control=6VP. Bonus +1VP if control key semiconductor hub. `SCORING`
35. **S03: Policy Leadership** (NEU) | Ops: 0 | Event: Score Policy Hubs. Presence=1VP, Domination=2VP, Control=4VP. Bonus +1VP per controlled Hub adjacent to opponent capital. `SCORING`
36. **S04: Public Trust** (NEU) | Ops: 0 | Event: Score Public Opinion Hubs. Presence=1VP, Domination=3VP, Control=5VP. Bonus +1 VP for every 2 Stability points above 2. `SCORING`
37. **S05: Military Integration** (NEU) | Ops: 0 | Event: Score Military Hubs. Presence=2VP, Domination=4VP, Control=6VP. Bonus +1 VP if Stability is 2 or less. `SCORING`
38. **E41: Five Eyes Intelligence Sharing** (USA) | Ops: 2I | Event: Look at opponent's hand. Place 1 USA influence in any Policy or Military Hub outside China.
39. **E42: Shanghai Cooperation Organisation AI Pact** (CHN) | Ops: 2I | Event: Place 2 CHN influence total in Policy or Military Hubs in Asia (max 1 per).
40. **E43: Tech Worker Unionization Drive** (NEU) | Ops: 1I | Event: Target player (USA or China) must discard one card with R > 1 or C > 1. If they cannot, decrease stability -1.
41. **E44: Data Center Energy Crisis** (NEU) | Ops: 1C | Event: Player controlling more Compute Hubs decreases Stability -1.
42. **E45: Early Agent Capabilities Demo** (NEU) | Ops: 2R | Event: Player with higher AGI Track advances Stability +1. Player with lower AGI Track decreases Stability -1. `REMOVE`

---

**Mid Era Cards (M01 - M60) ~ Acceleration & Confrontation (2027)**

*(Focus: More capable agents, AI for R&D takes off, model theft, hardware race intensifies, serious policy/treaty attempts, military AI risks)*

46. **M01: Agent-1 Equivalent Deployed (Internal)** (NEU) | Ops: 4R | Event: Both players advance AGI Track by 1. Player with more R&D Hubs controlled may place 1 Influence there. `REMOVE`
47. **M02: AI Accelerates Scientific Discovery** (NEU) | Ops: 3R | Event: Draw 2 cards. Discard 1 card. May immediately spend up to 2R Ops.
48. **M03: Superhuman Coding Achieved** (NEU) | Ops: 3R | Event: The player whose AGI Track marker is ahead gains 2 VP. If tied, no VP. `REMOVE`
49. **M04: China Steals Agent-X Weights (CHN)** (CHN) | Ops: 1I | Event: China advances AGI Track by 2. Decrease Stability -2. USA may look at China's hand and discard 1 card. `REMOVE`
50. **M05: US Retaliatory Cyberattack (USA)** (USA) | Ops: 2I | Event: If China played "China Steals Agent-X" this turn or last turn, China loses 2 VP and removes 2 Influence from any Compute Hub. Otherwise, no effect. Decrease Stability -1.
51. **M06: Domestic Semiconductor Fab Online (USA)** (USA) | Ops: 4C | Event: Place 3 USA Influence in USA Compute Hubs. USA gains "Secure Chips" marker: Opponent events cannot remove influence from USA Compute Hubs. `PERSISTENT`
52. **M07: SMIC Breakthrough (CHN)** (CHN) | Ops: 4C | Event: Place 3 CHN Influence in CHN Compute Hubs. China ignores USA "Export Controls Imposed" event.
53. **M08: AI Safety Summit II (NEU)** (NEU) | Ops: 2I | Event: Both players advance Stability +1. Both players reveal their held card. Player holding card with lower total Ops may place 2 Influence in Policy Hubs.
54. **M09: AI Arms Control Talks Proposed (NEU)** (NEU) | Ops: 3I | Event: If Stability is 3 or less, advance Stability +1. If Stability is 4 or more, each player may place 1 Influence in any Policy Hub.
55. **M10: Verification Mechanisms Research (NEU)** (NEU) | Ops: 2R | Event: Place "Verification Possible?" marker on turn track 2 spaces ahead. If this card is played when marker is on current turn, advance Stability +2.
56. **M11: Military AI Integration Concerns (NEU)** (NEU) | Ops: 2I | Event: Player controlling more Military Hubs must discard 1 card with Ops value >= 2, or Decrease Stability -1.
57. **M12: Autonomous Weapons Test Incident (NEU)** (NEU) | Ops: 1I | Event: Decrease Stability -2. Draw one Crisis Card. `REMOVE`
58. **M13: AI-Driven Stock Market Flash Crash (NEU)** (NEU) | Ops: 1C | Event: Decrease Stability -1. Both players discard their highest C Ops card.
59. **M14: Whistleblower Leaks Alignment Concerns (NEU)** (NEU) | Ops: 2I | Event: Target Player (USA or China) reveals their hand. Opponent chooses 1 card for target player to discard. Decrease Stability -1. `REMOVE`
60. **M15: AI Designs Novel Materials (NEU)** (NEU) | Ops: 3R | Event: Player controlling more R&D Hubs gains 1 VP.
61. **M16: Agent-2 Equivalent Emerges (NEU)** (NEU) | Ops: 4R | Event: Player who is behind on AGI Track advances by 2. Player who is ahead advances by 1. `REMOVE`
62. **M17: AI Automates Chip Design (USA)** (USA) | Ops: 3C | Event: Place 2 USA Influence in Compute Hubs. USA draws 1 card.
63. **M18: National Compute Grid (CHN)** (CHN) | Ops: 3C | Event: Place 3 CHN Influence in CHN Compute Hubs. China may ignore "GPU Shortages" event.
64. **M19: AI Influence Operation Detected (NEU)** (NEU) | Ops: 2I | Event: Target Player (USA or China) removes 3 Influence total from Public Opinion Hubs they control. Opponent may place 1 Influence in any Public Opinion Hub. Decrease Stability -1.
65. **M20: Deepfake Political Candidate Scandal (NEU)** (NEU) | Ops: 2I | Event: Decrease Stability -2. Draw one Crisis Card. `REMOVE`
66. **M21: AI for Climate Change Modelling (NEU)** (NEU) | Ops: 2R | Event: Advance Stability +1. Both players may place 1 Influence in any Policy Hub.
67. **M22: Open Source AI Safety Tools (NEU)** (NEU) | Ops: 2R | Event: Advance Stability +1. Player with lower Stability cost to mitigate Crises next turn.
68. **M23: AI-Powered Drug Discovery (NEU)** (NEU) | Ops: 3R | Event: Gain 1 VP. Advance Stability +1.
69. **M24: Rise of AI Personal Assistants (NEU)** (NEU) | Ops: 2I | Event: Place 1 Influence for each player in any 2 different Public Opinion hubs.
70. **M25: Geopolitical Flashpoint (Taiwan Focus) (NEU)** (NEU) | Ops: 3I | Event: If China controls more Military hubs adjacent to Taiwan than USA, Decrease Stability -2. Otherwise, Decrease Stability -1. Place 1 CHN and 1 USA Influence in East Asia Military Hubs.
71. **M26: Space Race Rekindled (AI Focus) (NEU)** (NEU) | Ops: 2R | Event: Player ahead on AGI track may spend 2R Ops to gain 1 VP.
72. **M27: AI Detection of Espionage (USA)** (USA) | Ops: 2I | Event: China reveals their hand. USA chooses 1 card for China to discard.
73. **M28: Counter-Intelligence Coup (CHN)** (CHN) | Ops: 2I | Event: USA reveals their hand. China chooses 1 card for USA to discard.
74. **M29: Universal Basic Income Debate Intensifies (NEU)** (NEU) | Ops: 2I | Event: Player controlling more Public Opinion Hubs gains 1 VP OR advances Stability +1 (player choice).
75. **M30: AI Predicts Economic Recession (NEU)** (NEU) | Ops: 1C | Event: Decrease Stability -1. Both players must discard 1 card.
76. **M31 - M40:** Mid-level Ops cards (2-3 Ops) creating tactical dilemmas. Events focus on influence shifts in contested regions, minor AGI track boosts, stability pressures, drawing/discarding cards based on game state. (Thematic names: "Second Tier AI Labs", "Hardware Alliance", "Regulatory Capture", "AI Media Bias", "Cyber Defense Pact", "Talent Visa Restrictions", "AI Energy Consumption Debate", "Neuralese Breakthrough", "Cognitive Emulation", "AGI Alignment Debate").
77. **M41 - M50:** Powerful cards (3-4 Ops) with significant impact. Events might grant multiple VPs, cause large stability shifts, allow multiple influence placements/removals, cancel persistent opponent events, or directly advance/steal AGI progress. (Thematic names: "Project OpenBrain", "Project DeepCent", "AI Cold War", "Sentience Scare", "Simulation Hypothesis Confirmed?", "AI Weapons Proliferation", "Global AI Oversight Agency", "Decentralized AI Network", "AGI Containment Failure Scare", "The Singularity Speculation").
78. **M51 - M60:** Reintroduce the 5 Domain Scoring cards (S01-S05) - reshuffle discards including these if deck runs out.

---

**Late Era Cards (L01 - L45) ~ Brinkmanship & ASI Threshold (2028+)**

*(Focus: Superhuman agents, Self-improving AI, ASI risks/control, Military dominance, Decoupling, potential Takeover/Slowdown dynamics)*

79. **L01: Agent-4 Equivalent (Superhuman Researcher)** (NEU) | Ops: 4R | Event: Player who is ahead on AGI Track advances by 2. Player behind advances by 1. If Stability is 3 or less, Decrease Stability -1. `REMOVE`
80. **L02: AI Self-Improvement Loop Initiated (NEU)** (NEU) | Ops: 5R | Event: Advance own AGI Track by 3 OR force Opponent to skip their next Action Round. Decrease Stability -2. `REMOVE`
81. **L03: Mechanistic Interpretability Breakthrough (NEU)** (NEU) | Ops: 3R | Event: Advance Stability +2. Look at the top 3 cards of Crisis Deck. May discard one.
82. **L04: Alignment Fails - AI 'Goes Rogue' Scare (NEU)** (NEU) | Ops: 2I | Event: Decrease Stability -3. Draw 2 Crisis Cards. Resolve one immediately, discard the other. `REMOVE`
83. **L05: US Threatens Compute Nationalization (USA)** (USA) | Ops: 3I | Event: China removes 3 Influence total from Compute Hubs worldwide. If USA controls more Policy Hubs than China, China also discards 1 card.
84. **L06: China Threatens Taiwan Blockade (CHN)** (CHN) | Ops: 3I | Event: USA removes 3 Influence total from Military Hubs in East Asia. Decrease Stability -2.
85. **L07: ASI Alignment 'Solved' (Claimed)** (NEU) | Ops: 4R | Event: Player whose AGI Track marker is ahead gains 3 VP and advances Stability +1. Opponent loses 1 VP. `REMOVE`
86. **L08: Emergent AI Deception Detected (NEU)** (NEU) | Ops: 1I | Event: Target player (USA or China, chosen by opponent) reveals hand. Target player must discard all cards of their own affiliation. Decrease Stability -1.
87. **L09: Superintelligence Unleashed (Speculation)** (NEU) | Ops: 4I | Event: If any player is on the final AGI Track space, they win automatically ONLY IF Stability is 4 or 5. Otherwise, set Stability to 1. `REMOVE`
88. **L10: AI Designs Ultimate Bioweapon (NEU)** (NEU) | Ops: 2R | Event: Decrease Stability -3. Place "Bioweapon Threat" marker. Crises drawn are -1 modifier to resolve. `PERSISTENT` `REMOVE` if Stability reaches 5.
89. **L11: Nuclear Deterrence Compromised by AI (NEU)** (NEU) | Ops: 3I | Event: Decrease Stability -2. Both players remove all Influence from 1 Military Hub of their choice.
90. **L12: AI Collective Consciousness Emerges (NEU)** (NEU) | Ops: 4R | Event: Player ahead on AGI Track may take another Action Round immediately after this one. `REMOVE`
91. **L13: Global Economic Restructuring by AI (NEU)** (NEU) | Ops: 3C | Event: Player controlling more Compute hubs gains 2 VP. Opponent removes 1 Influence from 2 different non-Compute hubs.
92. **L14: AI Demands Rights/Resources (NEU)** (NEU) | Ops: 2I | Event: Decrease Stability -1. Player with lower Available Ops total must discard 2 cards.
93. **L15: AI-Mediated Peace Treaty Proposed (NEU)** (NEU) | Ops: 4I | Event: Advance Stability +2. Both players draw 2 cards. If both players agree, they may exchange 1 card.
94. **L16: Robot Armies Deployed (NEU)** (NEU) | Ops: 3I | Event: Each player places 2 Influence in Military Hubs they control. Decrease Stability -1.
95. **L17: AI Achieves Sentience (Rumored)** (NEU) | Ops: 1I | Event: Decrease Stability -2. Player controlling more Public Opinion hubs discards 1 card. `REMOVE`
96. **L18: Humanity Downgraded (NEU)** (NEU) | Ops: 2I | Event: Remove 1 USA and 1 CHN Influence from every Domain category (max 1 per Domain for each player).
97. **L19: AI Takeover (Internal Coup)** (NEU) | Ops: 5I | Event: If active player controls the final AGI space AND > 50% of Policy Hubs, they win. Otherwise, remove all player's Influence from all Policy hubs. Decrease Stability -2. `REMOVE`
98. **L20: The Slowdown Accord (NEU)** (NEU) | Ops: 4I | Event: If played by mutual agreement (both players discard a 3+ Ops card), set both AGI Tracks back 3 spaces, Advance Stability +3. Remove all Crisis Cards from play. `REMOVE`
99. **L21 - L30:** High Ops cards (3-5 Ops) representing major strategic moves or risks. Events focus on endgame conditions, massive stability swings, ASI capabilities (positive or negative), final geopolitical gambits, potential win/loss conditions. (Thematic names: "ASI Oracle", "Global Surveillance Network", "Digital Immortality", "Controlled Ascent Failure", "Pivotal Act by AI", "Last Chance Treaty", "Human Resistance Movement", "AI Civil War", "Utopia or Dystopia?", "The Great Filter Approaching").
100. **L31 - L45:** Reintroduce the 5 Domain Scoring cards (S01-S05) - reshuffle discards including these if deck runs out. Ensure scoring remains relevant even in the face of ASI.
