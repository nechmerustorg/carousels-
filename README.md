# Carousel Creator — Nech Mě Růst

Lokální nástroj pro tvorbu Instagram karuselů (1080 × 1380 px).
Pracuje přímo v prohlížeči — nepotřebuje žádný build.

## Co tu je

| Soubor                      | K čemu je                                            |
| --------------------------- | ---------------------------------------------------- |
| `index.html`                | Vlastní editor. Otevři ho v prohlížeči.              |
| `carousels/prasatka.json`   | Hotový karusel o Flíčkovi a Princezně.               |
| `prompt-template.md`        | Šablona promptu pro Claude, aby JSON generoval správně. |
| `JSON_SCHEMA.md`            | Popis schématu, který editor čte.                    |

## Jak to spustit

1. Stáhni `index.html` (nebo dvojklik přímo v repu).
2. Otevři ho v prohlížeči (Chrome / Edge / Safari).
3. Vlevo nahoře klikni **„📂 Načíst JSON"** a vyber soubor z `carousels/`.
4. Nahraj fotky (na každém slidu typu `photo` máš tlačítko **„Nahrát fotku"**).
5. Klikni **„📦 Stáhnout vše"** — editor uloží všech 9 slidů jako PNG 1080×1380.

## Jak nechat Claude napsat nový karusel

Použij `prompt-template.md`. Pošli ho Claude i s tématem, dostaneš JSON, který
stačí uložit, nahrát do editoru a doplnit fotky.

> **Důležité:** Karusely **vždy v plné češtině s diakritikou**. Emoji jako
> Unicode znaky (🐖, 👑, 🧠, …). Editor sice umí přeložit i názvy
> („pig" → 🐖), ale správný JSON má rovnou znaky.

## Časté problémy

* **„JSON se načetl, ale emoji se nezobrazuje."** → V JSONu je `"emoji": "pig"`
  místo `"🐖"`. Editor to teď tolerujte přes interní mapování, ale lepší je
  rovnou používat znaky.
* **„Text bez diakritiky."** → Buď byl JSON od AI bez diakritiky, nebo si
  diakritiku spolkl copy-paste. Otevři JSON ručně a doplň ji.
* **„Export PNG má slepená slova."** → Editor už má fix (vypíná
  `letter-spacing` před exportem). Pokud se to vrátí, zkontroluj, že máš
  čerstvý `index.html`.
* **„Carousel se rozbil po načtení JSONu."** → Zkontroluj, že JSON má pole
  `"slides"` a každý slide má `"type"` (`hook` | `photo` | `prompt` | `cta`).
