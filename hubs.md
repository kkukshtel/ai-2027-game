# Hub and Influence Rules

## I. Hub Connections

1. **Explicit Links:** Hubs are connected only if an explicit line is drawn between them on the game board's SVG map. These connections are predefined and stored in the hub's data (in the `hubs` table, the `connections` array lists the `hub_unique_id`s it connects to).

2. **Adjacency:** Two hubs are "adjacent" if they are directly connected by one of these explicit links.

3. **No Implied Connections:** Geographic proximity on the abstract map does *not* imply a connection unless a line is present. Connections do not wrap around the map edges unless explicitly drawn.

4. **Domain/Region Irrelevance:** Connections are independent of Domain or Region boundaries unless a specific card or rule states otherwise.

## II. Influence Placement Rules & Cost Calculation

Placing influence represents exerting effort (political, economic, technological, social, or military) to gain sway in a particular hub. The cost is paid in Influence Operations Points (🔵).

### Placement Requirements (Adjacency Rule)

* A player may normally place influence in a target hub **only if** they already have influence marker(s) present in at least one **adjacent** hub at the start of their Action.

* **Exceptions:**
  * **Superpower Adjacency:** A player may always place influence in hubs directly connected to their conceptual "Superpower Space" (specific starting hubs for each player that always count as adjacent for placement).
    * **USA:** Washington D.C., US East Coast Research, Silicon Valley Cluster
    * **China:** Beijing Central Policy, Beijing/Tsinghua Hub, Shenzhen Innovation Zone
  * **Card Events:** Specific card events may explicitly allow placing influence in a hub regardless of adjacency.
  * **Empty Hubs:** Adjacency is required even for empty hubs unless an exception applies.

### Calculating the Cost to Place 1 Influence Point

1. **Step 1: Determine Base Cost:**
   * If the target hub is **Uncontrolled** or **Friendly Controlled**: Base Cost = **1 Op**.
   * If the target hub is **Enemy Controlled**: Base Cost = **2 Ops**.

2. **Step 2: Apply Modifiers from Card Events / Persistent Effects:**
   * Check the `gameState.activeEffects` and any effects from the card being played for Ops.
   * Add or subtract Ops cost based on applicable effects.
   * Example Effects: "+1 Cost to place Influence in Compute Hubs for USA", "-1 Cost for China to place Influence adjacent to controlled Military Hub"

3. **Step 3: Determine Final Cost:**
   * Sum the Base Cost and all applicable modifiers.
   * The final cost to place one point of influence can **never be less than 1 Op**, regardless of modifiers.

### Placing Multiple Influence Points

* When playing a card for Ops, a player can place multiple influence points in one or more eligible hubs.
* The cost for each individual point is calculated separately at the moment it is placed.
* **Important:** Placing influence can change the control status of a hub mid-action. If placing the first point causes a hub to switch from Enemy Controlled to Uncontrolled, the next point placed in that same hub during the same action costs only 1 Op (plus modifiers), not 2 Ops.

#### Example Cost Calculation

* USA plays a 3 Influence Ops (🔵) card.
* Target: 'EU AI Center' (Stability 3). Currently China controls it with 4 Influence, USA has 0.
* Legality: Assume USA has influence in an adjacent hub. Placement is legal.
* *Placing 1st point:* Hub is Enemy Controlled. Base Cost = 2 Ops. No modifiers. Final Cost = 2 Ops. USA spends 2 Ops. State: USA 1, China 4. China still controls.
* USA has 1 Op remaining. Target: Same hub ('EU AI Center').
* *Placing 2nd point:* Hub is still Enemy Controlled (4 vs 1, margin is 3, equals stability). Base Cost = 2 Ops. USA only has 1 Op left, cannot place this point here unless they use Debt/Treaty Points or a card provides more Ops.

*Alternative Scenario:* Target: 'EU AI Center' (Stability 3). China: 3 Inf, USA: 0 Inf. China just meets control threshold. USA plays 3 Ops card.
* *Placing 1st point:* Enemy Controlled. Cost = 2 Ops. State: USA 1, China 3. Hub becomes Uncontrolled.
* USA has 1 Op remaining. Target: Same hub.
* *Placing 2nd point:* Hub is now Uncontrolled. Base Cost = 1 Op. USA spends 1 Op. State: USA 2, China 3. Hub remains Uncontrolled.

## III. Control Thresholds

Control represents having dominant sway within a hub, sufficient to leverage its resources or deny them to the opponent.

### Control Conditions

A player controls a hub if **BOTH** of the following are true:

1. **Sufficient Presence:** The player's total Influence points in the hub are greater than or equal to the hub's `initial_stability` value (the number printed on the hub).

2. **Dominance Margin:** The player's total Influence points in the hub exceed the opponent's total Influence points in that hub by an amount greater than or equal to the hub's `initial_stability` value.
   * Formula: `(Player Influence) - (Opponent Influence) >= Hub Stability`

### Additional Control Rules

* **Uncontrolled:** If neither player meets both conditions, the hub is Uncontrolled.
* **No Shared Control:** A hub can only be controlled by one player at a time.
* **Hub Type Irrelevance:** The conditions for control are the same regardless of the hub's Domain. The hub's `initial_stability` value reflects its inherent resistance to being controlled.
* **State Update:** After any action that adds or removes influence from a hub, the Game Engine must immediately re-evaluate the control status for both players and update the `gameState.influenceMap[hubId].controlledBy` field ('USA', 'China', or `null`).

#### Example Control Determination

Hub: 'Silicon Valley' (Stability 4)
* USA: 4 Inf, China: 0 Inf → USA Controls (4 ≥ 4 AND 4-0 ≥ 4)
* USA: 5 Inf, China: 1 Inf → USA Controls (5 ≥ 4 AND 5-1 ≥ 4)
* USA: 5 Inf, China: 2 Inf → Uncontrolled (USA meets presence, but 5-2=3, which is < 4 margin needed)
* USA: 3 Inf, China: 0 Inf → Uncontrolled (USA fails presence: 3 < 4)
* USA: 7 Inf, China: 3 Inf → USA Controls (7 ≥ 4 AND 7-3 ≥ 4)
* USA: 7 Inf, China: 4 Inf → Uncontrolled (USA meets presence, but 7-4=3, which is < 4 margin needed)

## IV. Hub List by Domain

### Domain: R&D (Research & Development)

1. **Silicon Valley Cluster (SVC)**
   * Region: North America
   * Stability: **4**
   * Notes: Core US private AI labs, Stanford/Berkeley influence
   * Connections: US East Coast Research, US Chip Design, Washington D.C., US Coastal Media

2. **US East Coast Research Hub (ECR)**
   * Region: North America
   * Stability: **3**
   * Notes: MIT, CMU, NYC AI labs, Toronto Vector Institute influence
   * Connections: Silicon Valley, Washington D.C., UK AI Research, NATO AI

3. **Beijing/Tsinghua Hub (BTH)**
   * Region: East Asia
   * Stability: **4**
   * Notes: Top Chinese universities, state-linked labs, close to policy center
   * Connections: Shenzhen Innovation, CHN Central Policy, CHN State Media, PLA Central AI

4. **Shenzhen Innovation Zone (SIZ)**
   * Region: East Asia
   * Stability: **3**
   * Notes: Major Chinese tech companies (Tencent, Huawei), hardware/AI integration focus
   * Connections: Beijing/Tsinghua, CHN Domestic Semiconductor, CHN Social Media, Taiwan Semiconductor

5. **UK AI Research (UKR)**
   * Region: Europe
   * Stability: **3**
   * Notes: Oxbridge, London labs (DeepMind origins), Gov AI initiatives
   * Connections: US East Coast Research, Continental EU Research, Brussels EU Regulation, NATO AI

6. **Continental EU Research Hub (CER)**
   * Region: Europe
   * Stability: **3**
   * Notes: Franco-German AI labs, ETH Zurich, other key EU research centers
   * Connections: UK AI Research, Brussels EU Regulation, Netherlands Lithography

7. **Tel Aviv / Israel AI (TIA)**
   * Region: RoW (Middle East)
   * Stability: **2**
   * Notes: Strong startup culture, specialized AI (cyber, vision)
   * Connections: Silicon Valley, Continental EU Research

### Domain: Compute & Hardware

8. **US Cloud Infrastructure (USC)**
   * Region: North America
   * Stability: **4**
   * Notes: AWS, Azure, GCP dominance in North America
   * Connections: Silicon Valley, US Chip Design, Washington D.C.

9. **US Chip Design Hub (USD)**
   * Region: North America
   * Stability: **4**
   * Notes: Nvidia, Intel, AMD, other fabless design leaders
   * Connections: Silicon Valley, US Cloud Infra, Taiwan Semiconductor, South Korea Memory

10. **China Cloud Infrastructure (CHC)**
    * Region: East Asia
    * Stability: **4**
    * Notes: Alibaba Cloud, Tencent Cloud, Baidu Cloud, etc. State influence
    * Connections: Beijing/Tsinghua, CHN Domestic Semiconductor, CHN Central Policy

11. **CHN Domestic Semiconductor Hub (CDS)**
    * Region: East Asia
    * Stability: **3**
    * Notes: SMIC and other Chinese efforts to build indigenous chip manufacturing
    * Connections: Shenzhen Innovation, CHN Cloud Infra, Beijing Central Policy

12. **Taiwan Semiconductor Hub (TSH)**
    * Region: East Asia
    * Stability: **5**
    * Notes: TSMC dominance, critical node in global supply chain. Highly contested
    * Connections: US Chip Design, Shenzhen Innovation, Netherlands Litho, South Korea Memory

13. **South Korea Memory/Logic (SKM)**
    * Region: East Asia
    * Stability: **4**
    * Notes: Samsung, SK Hynix - leaders in memory and advanced logic
    * Connections: US Chip Design, Taiwan Semiconductor, Beijing/Tsinghua

14. **Netherlands Lithography Hub (NLH)**
    * Region: Europe
    * Stability: **5**
    * Notes: ASML - crucial bottleneck for advanced chip manufacturing
    * Connections: Taiwan Semiconductor, Continental EU Research, US Chip Design, South Korea Memory

### Domain: Policy & Governance

15. **Washington D.C. Policy (WDC)**
    * Region: North America
    * Stability: **4**
    * Notes: US Congress, White House, Regulatory agencies
    * Connections: Silicon Valley, US Cloud Infra, Pentagon/DARPA, Brussels EU Regulation, US Coastal Media

16. **Beijing Central Policy (BCP)**
    * Region: East Asia
    * Stability: **5**
    * Notes: CCP Politburo, State Council, MIIT. Top-down control
    * Connections: Beijing/Tsinghua, CHN Cloud Infra, PLA Central AI, CHN State Media

17. **Brussels EU Regulation (BER)**
    * Region: Europe
    * Stability: **3**
    * Notes: European Commission, Parliament - focus on regulation (AI Act)
    * Connections: Continental EU Research, UK AI Research, Washington D.C., Global Standards

18. **Global Standards Body (GSB)**
    * Region: RoW (Global)
    * Stability: **2**
    * Notes: International bodies like ITU, ISO, potentially UN AI bodies
    * Connections: Washington D.C., Beijing Central Policy, Brussels EU Regulation

### Domain: Public Opinion

19. **US Coastal Media Hub (UCM)**
    * Region: North America
    * Stability: **3**
    * Notes: Major US media outlets, tech journalism, cultural influence centers
    * Connections: Silicon Valley, Washington D.C., US Heartland Opinion

20. **US Heartland Opinion (UHO)**
    * Region: North America
    * Stability: **3**
    * Notes: Sentiment outside major tech/policy centers, potential Luddite reaction
    * Connections: US Coastal Media, Washington D.C.

21. **CHN State Media Apparatus (CSM)**
    * Region: East Asia
    * Stability: **4**
    * Notes: CCTV, Xinhua, etc. Top-down narrative control within China
    * Connections: Beijing Central Policy, CHN Social Media Sphere

22. **CHN Social Media Sphere (CSS)**
    * Region: East Asia
    * Stability: **2**
    * Notes: Weibo, WeChat - represents domestic online discourse (subject to censorship)
    * Connections: CHN State Media, Shenzhen Innovation

23. **Major EU Public Opinion (EPO)**
    * Region: Europe
    * Stability: **3**
    * Notes: Dominant public sentiment in key EU countries (Germany, France)
    * Connections: Brussels EU Regulation, Continental EU Research

### Domain: Military Integration

24. **Pentagon/DARPA Complex (PDC)**
    * Region: North America
    * Stability: **5**
    * Notes: US DoD leadership, advanced research funding, integration efforts
    * Connections: Washington D.C., US East Coast Research, US INDOPACOM AI, NATO AI

25. **PLA Central Command AI (PCA)**
    * Region: East Asia
    * Stability: **5**
    * Notes: Chinese military high command, strategic AI deployment, cyber warfare units
    * Connections: Beijing Central Policy, CHN Military R&D Zone, CHN Cloud Infra

26. **NATO AI Integration Hub (NAT)**
    * Region: Europe
    * Stability: **3**
    * Notes: Collaborative defense AI efforts among NATO allies
    * Connections: Pentagon/DARPA, Brussels EU Regulation, UK AI Research, Continental EU Research