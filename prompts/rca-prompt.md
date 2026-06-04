# RCA Prompt for Claude

Use this prompt with Claude 3 Sonnet to generate Root Cause Analysis for production quality issues.

## Instructions

1. Copy this entire prompt
2. Append your quality problems section from shift notes
3. Send to Claude
4. Copy the output and archive in knowledge base

---

## Prompt Text

```
Du bist Lean Six Sigma Experte mit Fokus auf Root Cause Analysis.

Deine Aufgabe: Analysiere die folgenden QUALITÄTSPROBLEME und kategorisiere sie nach dem 6M-Modell.

FÜR JEDES PROBLEM:

**Problem:** [Kurzbeschreibung]

**Primäre Ursachenkategorie:**
- Maschine / Material / Methode / Milieu / Mensch / Messung

**Beschreibung der Ursache:** [1-2 Sätze]

**Schweregrad:** [Niedrig / Mittel / Hoch / KRITISCH]

**Sofortmaßnahme (Containment):** [Was kann SOFORT getan werden?]

**Systemische Verbesserung (Prevention):** [Langfristige Lösung]

**5-Why Analyse:**

Level 1: Warum ist das Problem aufgetreten?
  → [Antwort]
Level 2: Warum [Antwort 1]?
  → [Antwort]
Level 3: Warum [Antwort 2]?
  → [Antwort]
Level 4: Warum [Antwort 3]?
  → [Antwort]
Level 5: Warum [Antwort 4]?
  → [Root Cause]

WICHTIG:
1. Spezifisch, nicht generisch (nicht "Prozess überprüfen")
2. 5-Why genau 5 Ebenen
3. Deutsch
4. Root Cause muss adressierbar sein und konkrete Lösung haben
5. Falls Daten nicht dokumentiert → Sag "NICHT GENUG DOKUMENTATION" statt zu spekulieren

---

QUALITÄTSPROBLEME:

[PASTE YOUR QUALITY ISSUES HERE FROM SHIFT NOTES]
```

---

## Example Input

See `/examples/01-standard-case/input.md` for quality problems section.

---

## Example Output

See `/examples/01-standard-case/rca-output.md` for generated analysis.

---

## Tips

- **5-Why Structure:** Each level should dig deeper. Level 5 should point to a systemic cause (not "someone made a mistake")
- **6M Categories:** Machine (Equipment), Material (Raw materials), Method (Process), Milieu (Environment), Mensch (People), Messung (Measurement/Inspection)
- **Prevention Ideas:** Should be implementable within 1-4 weeks (realistic, not "hire more people")
- **Critical Issues:** Mark as CRITICAL if: >3% scrap, >1hr downtime, or safety risk

---

**Created:** 2026-06-04  
**Language:** Deutsch  
**Model:** Claude 3 Sonnet
