# Age of Warriors: External Main Menu Hub & Strategic Combat Systems

Transform **Age of Warriors** with a full-fledged, professional **External Main Menu Hub** matching standard top-tier strategy games (dedicated Play button, settings, masteries skill tree, upgrades, unit runes armory, and dungeon), alongside the **Universal Mastery Skill Tree** and **Unit Rune Cards** progression systems.

---

### User Review & Critical Decisions

> [!IMPORTANT]
> The following revisions have been incorporated into this design:
> - **External Main Menu Hub**: The game launches into a standalone, full-featured Main Menu Hub instead of directly into the battle view.
> - **Primary Actions**:
>   - Central **⚔️ BATTLE (PLAY)** primary button to deploy onto the battlefield.
>   - **⚡ Masteries (شجرة المهارات)**: 3-branch cross-era passive skill tree.
>   - **🃏 Runes (بطاقات القوات)**: Archetype cards leveling system.
>   - **🛠️ Upgrades (الترقيات)**: Food generators, storage capacity, and fortress defense.
>   - **🏛️ Evolve (تطور العصور)**: Timeline era advancement with architectural previews.
>   - **💀 Dungeon (الزعيم والتحديات)**: Boss raid challenges with gem rewards.
>   - **⚙️ Settings (الإعدادات)**: Audio volume sliders, sound toggles, and statistics.
> - **Seamless Navigation**: In-battle pause/exit button to return to the Main Menu at any moment, and a direct "Menu" CTA on Victory/Defeat dialogs.

---

## 1. Overview & Core Concept

Currently, the game presents a pre-battle card overlay atop the active arena. To deliver a true AAA mobile gaming feel, we introduce a **dedicated Game Hub (Main Menu Screen)** that serves as the central command headquarters:
1. **Main Menu Screen (View State: `MENU`)**: An atmospheric hub displaying the player's current fortress and commander, currency balances (Gold, Gems, Mastery Stars), and quick-access feature buttons.
2. **Battlefield Screen (View State: `BATTLE`)**: The intense 2.5D combat arena entered only when the player taps "BATTLE / PLAY".
3. **Universal Mastery Skill Tree**: Permanent perks across Offense, Defense, and Logistics.
4. **Unit Rune Cards System**: Leveling up Melee, Ranged, Heavy, and Hero archetypes across all 6 eras.

---

## 2. User Experience & Visual Design

### Screen Flow & State Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                        MAIN MENU HUB (Screen 1)                        │
│                                                                        │
│   [Era: Bronze Age]      [🪙 1,240]   [💎 45]   [⭐ 8]      [⚙️ Settings]│
│                                                                        │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │               🏰 Current Fortress & Commander 👑               │   │
│   │           "Spartan Temple Citadel • King Leonidas"             │   │
│   └────────────────────────────────────────────────────────────────┘   │
│                                                                        │
│                    ┌───────────────────────────────┐                   │
│                    │     ⚔️ PLAY / BATTLE ⚔️      │                   │
│                    │         (ابدأ المعركة)         │                   │
│                    └───────────────────────────────┘                   │
│                                                                        │
│   ┌──────────────┬──────────────┬──────────────┬───────────────────┐   │
│   │ ⚡ Masteries │   🃏 Runes   │ 🛠️ Upgrades │ 🏛️ Era Evolution  │   │
│   │  شجرة المهارات │  بطاقات القوة │    الترقيات   │     تطور العصور    │   │
│   └──────────────┴──────────────┴──────────────┴───────────────────┘   │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Taps "PLAY"
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                        BATTLEFIELD (Screen 2)                          │
│                                                                        │
│   [Base HP Bar]                                          [Enemy HP Bar]│
│   [🏠 Menu / Exit]       [⏸️ Pause]      [Speed: 1x/2x]    [🔊 Sound]   │
│                                                                        │
│   ~~~~~~~~~~~~~~~~~~~~ 2.5D Animated Arena ~~~~~~~~~~~~~~~~~~~~~~~~~~  │
│   (Player Units)       ─────────► Clash ◄─────────       (Enemy Units) │
│                                                                        │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │ [👑 Hero Ult] [💣 Bomb] | [🍖 Food Gauge: 14/20 (+1.8/s)]      │   │
│   │ [Unit 1]      [Unit 2]     [Unit 3]     [👑 Hero Commander]    │   │
│   └────────────────────────────────────────────────────────────────┘   │
└────────────────────────────────────────────────────────────────────────┘
```

### Visual Styling & Theme
- **Theme**: Epic, warm hand-drawn ink and parchment aesthetic with clean M3 container elevations.
- **Main Battle Button**: Large, energetic golden-amber gradient (`linear-gradient(135deg, #f59e0b, #d97706)`) with subtle breathing animation (`@keyframes pulseCta`).
- **Hub Feature Cards**: 4-column balanced grid dock at the bottom of the Main Menu, styled with dark slate containers (`#1e293b`), crisp hand-drawn borders, and clear bilingual typography.
- **Accessibility & Safe Areas**:
  - Full support for `enableEdgeToEdge()` with safe padding around the camera cutout and Android navigation bar.
  - Interactive components strictly adhere to minimum 48dp touch targets.

---

## 3. Detailed Feature Breakdown

### A. Dedicated External Main Menu Hub
- **Game Title Banner**: Polished header with historical era subtitle and animated particles.
- **Top Resource Bar**: Displays Coins (🪙), Gems (💎), and Mastery Stars (⭐), with a quick settings gear.
- **Centerstage Showcase**: Interactive 2.5D visual card previewing the current fortress architecture and unlocked Hero Commander with their active ultimate skill.
- **Big Play Button**: Direct launch trigger that initializes the battle, starts era-specific musical accompaniment, and transitions seamlessly into the arena.
- **Hub Navigation Grid**:
  1. `⚡ Masteries`: Opens the full constellation skill tree.
  2. `🃏 Runes`: Opens the unit cards collection and leveling screen.
  3. `🛠️ Upgrades`: Opens the base HP, food generator, and storage upgrade dialog.
  4. `🏛️ Evolve`: Opens the timeline era progression and fortress preview.
  5. `💀 Dungeon`: Enters the colossal boss challenge.

### B. Universal Mastery Skill Tree (شجرة المهارات)
Three permanent branches accessible from the menu:
1. **Iron Legion (الهجوم والقوة)**:
   - *Primal Might*: +5% unit damage per rank (max 5).
   - *Critical Surge*: +4% critical strike chance & +25% crit damage (max 5).
   - *Cleave Impact*: +12% melee splash cleave radius (max 3).
2. **Aegis Bastion (الدفاع والتحصينات)**:
   - *Fortified Walls*: +350 Base Max HP per rank (max 5).
   - *Guardian Shield*: Deployed units start with an energy shield of +50 HP (max 3).
   - *Spiked Barricades*: 15% damage reflection to melee attackers (max 3).
3. **Supply Logistics (الإمداد والاقتصاد)**:
   - *Abundant Harvest*: +0.20 food/s production rate (max 5).
   - *Scavenger Gold*: +15% gold reward per defeated enemy (max 5).
   - *Tactical Agility*: -10% cooldown on unit and hero deployments (max 3).

### C. Unit Rune Cards System (بطاقات القوات)
- 4 core archetype cards:
  - **Melee Rune Card**: Boosts HP and frontal resistance for all melee units across eras.
  - **Ranged Rune Card**: Increases attack range and projectile speed for all ranged units.
  - **Heavy/Siege Rune Card**: Grants armor defense and knockback resistance.
  - **Hero Commander Rune Card**: Enhances ultimate skill duration and reduces energy cost.
- Level-up mechanics: Spend duplicate cards and gold to increase card levels from Level 1 to 10 with visual rarity borders (Common ➔ Legendary).

---

## 4. Technical Implementation & Data Strategy

### Architecture & DOM State Structure
- **View Controller State in `GameEngine2D`**:
  ```javascript
  this.appScreen = 'MENU'; // 'MENU' | 'BATTLE'
  ```
- **DOM Container Toggling**:
  - `#screen-main-menu`: Fully styled fullscreen hub container (shown when `appScreen === 'MENU'`).
  - `#screen-battlefield`: Combat arena and spawner dock (shown when `appScreen === 'BATTLE'`).
- **State Additions in `StateManager`**:
  ```javascript
  {
    masteryStars: 5,
    masteries: { /* 9 skill nodes */ },
    runeCards: {
      melee: { level: 1, count: 5, target: 10 },
      ranged: { level: 1, count: 3, target: 10 },
      heavy: { level: 1, count: 2, target: 10 },
      hero: { level: 1, count: 1, target: 5 }
    }
  }
  ```
- **Android Persistence**:
  - Saved seamlessly to SharedPreferences via `AndroidBridge.saveGameState()`.
  - Preserves sound/music toggles, masteries, and card levels across app restarts.

---

## 5. Verification & Testing Checklist

- [ ] **Screen Transitions**: Verify tapping "BATTLE / PLAY" smoothly transitions from Main Menu to Battlefield without canvas flicker.
- [ ] **Menu Navigation**: Verify tapping "Return to Menu" from battlefield, pause, or victory/defeat dialogs returns cleanly to the Main Menu.
- [ ] **Modals Accessibility**: Confirm Skill Tree, Upgrades, Runes, Evolve, and Settings modals open and close smoothly from the Main Menu.
- [ ] **Offline Persistence**: Verify unlocked skill points and upgraded rune levels persist across battles and app relaunch.
- [ ] **Build Validation**: Verify clean compilation using `compile_applet`.
