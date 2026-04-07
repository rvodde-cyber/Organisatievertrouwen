# PROJECT VERTROUWEN — Sessielog & Vervolgkaart
**Aangemaakt:** april 2026  
**Versie:** v4.0  
**Doel:** Dit document zorgt dat een volgende Claude-sessie precies weet wat er gebouwd is, welke keuzes gemaakt zijn, en hoe verder te gaan.

---

## Hoe dit project te hervatten

**Stuur Claude dit bericht aan het begin van een nieuwe sessie:**

> "Ik werk verder aan Project Vertrouwen. Lees SESSIELOG.md en de bestanden in deze map. Geef een samenvatting van de huidige stand en vraag wat ik wil doen."

Upload daarna alle bestanden uit deze map, zodat Claude de volledige context heeft.

---

## Wat er gebouwd is (volledig overzicht)

### De Vertrouwensmeter v4.0 — `vertrouwensmeter_v4.html`

Uitbreiding van v3.0: van **1 vraag per dimensie** naar **3 wetenschappelijk onderbouwde Likert-items per dimensie** (12 vragen totaal).

#### Nieuw in v4.0
- **3 Likert-vragen per dimensie** (S1–S3, I1–I3, M1–M3, B1–B3)
- **Dimensiegemiddelde live** zichtbaar naast elke dimensietitel (bijv. "Gem: 3.7")
- **Voortgangsbalk** bovenaan het invulformulier (bijv. "7 / 12 vragen ingevuld")
- **ABI-tag** per dimensie zichtbaar (Ability / Integrity / Benevolence)
- **Dim-block** visuele groepering per dimensie (card-stijl met header)
- Voorbeelddata aangepast: scores zijn nu gemiddelden van 3 items (floats)

#### Vragenset v4.0 (wetenschappelijk gekaderd in ABI-model)

| Code | Dimensie       | ABI          | Vraag |
|------|----------------|--------------|-------|
| S1   | Toekomst       | Ability      | "Ik heb vertrouwen in het succes van de organisatie over 5 jaar." |
| S2   | Toekomst       | Ability      | "De organisatie heeft een duidelijke en geloofwaardige strategie." |
| S3   | Toekomst       | Ability      | "De beslissingen die worden genomen passen bij de langetermijndoelen." |
| I1   | Systemen       | Integrity    | "Onze interne procedures zijn eerlijk en transparant." |
| I2   | Systemen       | Integrity    | "Afspraken en regels worden consequent nageleefd door iedereen." |
| I3   | Systemen       | Integrity    | "Wanneer iets misgaat, wordt dat open en eerlijk besproken." |
| M1   | Management     | Ability      | "De leiding is oprecht over de staat van de organisatie." |
| M2   | Management     | Ability      | "Leidinggevenden hebben de kennis en expertise om goede beslissingen te nemen." |
| M3   | Management     | Benevolence  | "Mijn leidinggevende heeft oprecht oog voor mijn welzijn." |
| B1   | Medewerkers    | Benevolence  | "Mijn collega's steunen mij als het werk zwaar wordt." |
| B2   | Medewerkers    | Benevolence  | "Ik voel me veilig om mijn mening te geven, ook als die afwijkt." |
| B3   | Medewerkers    | Benevolence  | "Er is een cultuur van wederzijds respect en samenwerking." |

---

## Ontwikkelhistorie

| Versie | Wat toegevoegd |
|--------|----------------|
| v1     | Basisschuifregelaars, ABI-verdeling, conditional theming |
| v2     | Meerdere respondenten, dashboard, trendlijn, export |
| v2b    | Anonieme modus, e-mailfunctie |
| v2c    | Standalone kantoorscène animatie |
| v3.0   | Alles geïntegreerd in één app met sticky kantoorscène |
| **v4.0** | **3 Likert-items per dimensie, voortgangsbalk, dim-blocks** |

---

## Technische keuzes en afspraken

- **formScores** is nu `{s:[3,3,3], y:[3,3,3], m:[3,3,3], w:[3,3,3]}`
- **onSlider(el, key, idx)** neemt nu een index mee (0/1/2)
- **saveResponse()** berekent per dimensie `avg(formScores[d])` voor opslag
- Voorbeelddata gebruikt float-gemiddelden (bijv. `s:4.0, y:3.3`)
- **touchedSliders** Set bijhoudt welke van de 12 sliders zijn aangeraakt

---

## Wat er nog niet is (mogelijke volgende stappen)

### Prioriteit 1 — Functioneel
- [ ] **Persistente opslag**: localStorage zodat data bewaard blijft bij sluiten browser
- [ ] **Echte Claude API-koppeling**: AI-knoppen sturen direct naar `/v1/messages`
- [ ] **Meerdere organisaties/perioden**: switcher bovenaan

### Prioriteit 2 — Inhoudelijk
- [ ] **Open tekstveld**: kwalitatieve toelichting per respondent
- [ ] **Normtabel**: vergelijk scores met branchegemiddelden
- [ ] **Demografische filters**: dashboard filteren op afdeling, niveau, periode
- [ ] **Omgekeerde items**: bijv. "Ik voel me soms niet gehoord" (reverse scoring)

### Prioriteit 3 — Design
- [ ] **Mobiele versie**: kantoorscène onder tabs
- [ ] **Printfriendly rapport**: CSS @media print
- [ ] **Meer kantoorpersonages**

### Prioriteit 4 — Technisch
- [ ] **GitHub + deployment** (GitHub Pages of Netlify)
- [ ] **localStorage**: data bewaard na sluiten browser
- [ ] **Google Sheets export**

---

## Wetenschappelijk kader

### ABI-model (Mayer, Davis & Schoorman, 1995)
- **Ability** → S1, S2, S3, M1, M2
- **Benevolence** → M3, B1, B2, B3
- **Integrity** → I1, I2, I3

### 7S-framework (McKinsey)
Vertrouwen als **Shared Value** — Strategy (S), Style (M), Systems (I), Staff (B)

---

## Bronnen (APA 7)

Mayer, R. C., Davis, J. H., & Schoorman, F. D. (1995). An integrative model of organizational trust. *Academy of Management Review*, *20*(3), 709–734.

Luhmann, N. (1979). *Trust and power*. Wiley.

Peters, T. J., & Waterman, R. H. (1982). *In search of excellence*. Harper & Row.

McAllister, D. J. (1995). Affect- and cognition-based trust as foundations for interpersonal cooperation. *Academy of Management Journal*, *38*(1), 24–59.

