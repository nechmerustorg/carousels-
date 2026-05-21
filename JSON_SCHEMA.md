# Carousel JSON schéma (v1)

Editor (`index.html`) čte JSON v následujícím tvaru. Pole označená **(p)**
jsou povinná, ostatní mají rozumný default.

```json
{
  "_schema": "carousel-v1",
  "meta": {
    "title":  "Volitelný název projektu",
    "theme":  "zolty | forest | ocean | sunset | laven | rose",
    "design": "organic | minimal | geometric | editorial"
  },
  "slides": [ /* viz níž */ ]
}
```

## Typy slidů

### 1. `hook` — úvodní slide

```json
{
  "type": "hook",           // (p)
  "bg":   "light",          // light | dark  (default: light)
  "tag":  "VĚDĚL/A JSI?",   // krátký nadpiscový štítek
  "heading": "Hlavní věta v plné češtině s diakritikou",
  "body":    "Doprovodný text — kontext, co se v karuselu dozvíš.",
  "textAlignV": "top | center | bottom",  // default: center
  "decorativeEmoji": "🐖"   // Unicode znak (lze i název: "pig")
}
```

### 2. `photo` — slide s fotkou

```json
{
  "type": "photo",          // (p)
  "bg":   "dark",           // light | dark
  "tag":  "FLÍČEK",         // štítek nahoře
  "emoji": "🐖",            // ikonka u textu
  "heading": "Krátký nadpis",
  "body":    "1–3 věty.",
  "imgSrc": "",             // necháme prázdné — fotka se nahraje v editoru
  "posX": 50,               // 0–100, horizontální výřez (default 50)
  "posY": 35,               // 0–100, vertikální výřez (default 35)
  "textY": 215              // 140–380, kde začíná textový blok v px
}
```

### 3. `prompt` — slide s šedou škatulí (např. AI prompt ke zkopírování)

```json
{
  "type": "prompt",
  "bg":   "light",
  "tag":  "ZKUS PROMPT",
  "heading": "Kdy a jak ho použít",
  "when":   "Krátký kontext — kdy se hodí.",
  "prompt": "Vlastní text promptu, který se zobrazí ve škatuli."
}
```

### 4. `cta` — závěrečný slide

```json
{
  "type": "cta",
  "bg":   "gradient",
  "heading": "Otázka nebo výzva pro publikum",
  "body":    "Doplňující věta, případně instrukce."
}
```

## Pravidla, která musí JSON splňovat

1. **Vždy plná čeština s diakritikou.** Žádné „prasatka", vždy „prasátka".
2. **Emoji = Unicode znaky** (`🐖`, `👑`, `🧠`). Editor tolerujte i názvy
   (`"pig"`, `"crown"`, …), ale doporučený zápis je znak.
3. **`bg` střídej** mezi `light` a `dark`, ať karusel dobře rytmicky plyne.
   Hook bývá `light`, CTA `gradient`.
4. **Heading do ~70 znaků**, **body do ~180 znaků** (jinak vyleze přes
   spodní okraj při exportu 1080×1380).
5. **Tag MAJUSKULEMI** s diakritikou (`VĚDĚL/A JSI?`, `FAKT #1`).
6. **9 slidů** je sweet spot pro Instagram (1 hook + 7 obsahových + 1 CTA).

## Mapa emoji jmen → znaků (zabudovaná v editoru)

```
pig / piglet → 🐖    crown   → 👑    brain   → 🧠
sheep        → 🐑    droplet → 💧    leaf    → 🌿
ram          → 🐏    map     → 🗺️    mic     → 🎤
cow          → 🐄    sun     → ☀️    moon    → 🌙
donkey       → 🫏    flower  → 🌸    sprout  → 🌱
rabbit       → 🐇    star    → ⭐    heart   → ❤️
dog          → 🐕    fire    → 🔥    sparkles→ ✨
cat          → 🐈    bulb    → 💡    warning → ⚠️
hen/chicken  → 🐔    check   → ✅    cross   → ❌
rooster      → 🐓    duck    → 🦆    goose   → 🪿
turkey       → 🦃    dove    → 🕊️    deer    → 🦌
goat         → 🐐    horse   → 🐎    butterfly → 🦋
fox          → 🦊    wolf    → 🐺    bear    → 🐻
```

Když pošleš jméno, které v mapě není, editor ho nechá tak — zobrazí se text.
