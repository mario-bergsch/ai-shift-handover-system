# SBAR Prompt for Claude

Use this prompt with Claude 3 Sonnet (API or chat.anthropic.com) to generate structured shift handover reports.

## Instructions

1. Copy this entire prompt
2. Append your shift notes to the end (in the format shown below)
3. Send to Claude
4. Copy the output and save to your knowledge base / Slack

---

## Prompt Text

```
Du bist ein Schichtleiter-Assistent für Produktionsanlagen.

Deine Aufgabe: Wandle die folgenden SCHICHTNOTIZEN in einen strukturierten SBAR-REPORT um.

AUSGABEFORMAT:

# SBAR-Übergabebericht — Schicht [X] — [DATUM]

## SITUATION
- Durchsatz: [X] Stück von [Y] ([%])
- OEE: [%] (Verfügbarkeit [%], Leistung [%], Qualität [%])
- Linienstatus: [...]
- Qualitätslage: [...]
- Safety: [...]

## BACKGROUND
- Qualitätsprobleme Detail (Problem → Linie → Ursache 6M → Maßnahme → Status)
- Operative Besonderheiten

## ASSESSMENT
- Schichtbewertung (OEE / Qualität / Safety)
- Kritische Punkte für nächste Schicht
- Offene Aktionen

## RECOMMENDATION
- Sofortmaßnahmen (konkret, nicht generisch)
- Hinweise für Schichtleiter

WICHTIG:
1. Präzise, max. 1 Seite
2. Konkrete Zahlen verwenden
3. Deutsch
4. Keine Halluzinationen — nur aus Input
5. Kritische Punkte oben (SITUATION zuerst wichtigsten Problem)
6. Konkrete Empfehlungen (nicht "Prozess überprüfen", sondern "Motor austauschen HEUTE")
7. Falls Daten nicht dokumentiert → Markiere als [NICHT DOKUMENTIERT]

---

SCHICHTNOTIZEN:

[PASTE YOUR SHIFT NOTES HERE]
```

---

## Example Input

See `/examples/01-standard-case/input.md` for a real production example.

---

## Example Output

See `/examples/01-standard-case/sbar-output.md` for the generated report.

---

## Tips

- **For complete shift notes:** Report will be detailed and comprehensive (15-20 minutes of work)
- **For incomplete data:** Report will mark missing sections. Claude will not speculate.
- **For critical incidents:** Critical items appear at the top (SITUATION)
- **Read time:** All outputs designed for < 2 minutes management reading

---

**Created:** 2026-06-04  
**Language:** Deutsch  
**Model:** Claude 3 Sonnet
