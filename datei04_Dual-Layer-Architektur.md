# datei04: Dual-Layer-Architektur (Ganzzahl-Standard & Maskierung)

## 1. Das Prinzip der Skalierung: Weg mit dem Komma

In herkömmlichen Systemen entstehen Rundungsfehler, weil versucht wird, die Realität in Dezimalstellen (Kommazahlen) zu pressen. Die Fn-Logik nutzt stattdessen die **Atomare Ganzzahl-Ebene**[^1].

* **Der Trick**: Anstatt $127{,}53$ Meter zu berechnen (was Floats erfordert), rechnet das System im Hintergrund mit Femtometern ($10^{-15}\ \text{m}$).
* **Der Wert**: $127.530.000.000.000.000$ Femtometer — eine reine Ganzzahl.
* **Der Vorteil**: Es gibt keine "halben" Einheiten, nur diskrete Takte. Die gesamte Präzision ist strukturell garantiert, nicht numerisch approximiert[^2].

| Klassische Architektur (Float) | Fn-Dual-Layer-Architektur (Ganzzahl) |
| :--- | :--- |
| Rechnet intern mit Dezimalstellen | Rechnet intern mit Femtometer-Ganzzahlen |
| Rundungsfehler bereits im Kern | Kern ist 100 % verlustfrei |
| Anzeige ≈ Rechengrundlage | Anzeige (Maske) ist vom Kern strikt getrennt |
| Hitze durch irrationale Operationen | Kalt, da keine Division oder Wurzel im Kern |

## 2. Die zwei Ebenen des Systems

```
[Eingabe / Impuls]
        │
        ▼
┌───────────────────────────────────┐
│  KERN  (Back-End: Atomare Ebene)  │
│  • Einheit: Femtometer / Plancktakt│
│  • Logik:   Reine Ganzzahl-Addition│
│  • Qualität: verlustfrei, kalt,    │
│             absolute Präzision     │
└───────────────┬───────────────────┘
                │  exakte Ganzzahl
                ▼
┌───────────────────────────────────┐
│  MASKE  (Front-End: Makro-Ebene)  │
│  • Funktion: Dezimalpunkt setzen  │
│  • Erlaubt: Runden für das Auge   │
│  • Verboten: Rückschreiben in Kern│
└───────────────┬───────────────────┘
                │
                ▼
     [Ausgabe für den Menschen]
       z. B. "127,53 m"
```

### A. Der Kern (Back-End: Atomare Ebene)
Hier findet die eigentliche Intelligenz statt. Der Kern arbeitet ausschließlich mit der Fn-Additionslogik auf der kleinstmöglichen physikalischen Skala[^1].

* **Einheit**: Femtometer / Plancktakt.
* **Logik**: Reine Ganzzahl-Addition — kein Teilen, kein Wurzelziehen.
* **Eigenschaft**: 100 % verlustfrei, keine thermische Emission (kalt), absolute Präzision.

### B. Die Maske (Front-End: Makro-Ebene)
Die Maske ist das Interface für den Menschen. Sie "übersetzt" die gigantischen Ganzzahlen des Kerns in lesbare Formate[^1].

* **Funktion**: Verschiebung des Dezimalpunktes für die Anzeige.
* **Beispiel**: Der Kern liefert $127.530.000.000.000.000\ \text{fm}$, die Maske zeigt "$127{,}53\ \text{m}$".
* **Einweg-Prinzip**: Die Maske darf runden oder schätzen für das Auge — der Kern darf niemals runden, um die Integrität des Prozesses zu wahren. Korrekturen fließen als neuer Impuls zurück in den Kern, niemals als direktes Überschreiben.

## 3. Konvergenz mit dem biologischen Modell

Die Dual-Layer-Architektur ist keine rein technische Entscheidung — sie spiegelt das Bauprinzip lebender Systeme wider[^1][^2]:

| Biologisches System | Dual-Layer-Architektur |
| :--- | :--- |
| **Zellkern** — DNA, exakte Replikation, kalt | **Fn-Kern** — Ganzzahl-Addition, verlustfrei |
| **Zellmembran** — Kommunikation nach außen | **Maske** — Skalierung für menschliche Lesbarkeit |
| Interne Prozesse laufen bei 37 °C stabil | Kern erzeugt keine Abwärme durch Rundung |
| Membran filtert: nicht alles gelangt nach innen | Maske schreibt nicht zurück in den Kern |

Biologische Zellen erreichen ihren Sättigungspunkt nach exakt $F_{11} = 89$ Takten[^2]. In der Dual-Layer-Architektur entspricht dies dem Moment, in dem ein vollständiger Lern-Zyklus im Kern abgeschlossen ist und das Ergebnis an die Maske übergeben wird — nicht früher.

## 4. Warum KI damit besser lernt

Wenn eine KI heute "lernt", verliert sie Information durch Float-Konvertierung bei jedem Schicht-Übergang. In der Dual-Layer-Architektur passiert das nicht[^1][^2]:

1. **KI-Training im Kern**: Jedes "Gewicht" ist eine exakte Position auf der atomaren Skala — keine Approximation.
2. **Keine Reibung zwischen Schichten**: Da der Kern niemals dividiert oder Wurzeln zieht, gibt es keinen Datenstau und keine Wärmeentwicklung.
3. **Unendliche Netztiefe**: Man kann neuronale Netze mit Millionen von Schichten bauen, ohne dass die Präzision abnimmt — Ganzzahlen behalten ihre Genauigkeit vollständig[^1].
4. **Stabile Rückkopplung**: Korrekturen (z. B. Backpropagation) werden als neue Impulse addiert, nicht als Float-Gradienten multipliziert — der Fn-Rhythmus U-U-G bleibt erhalten[^3].

## 5. Beispiel: Der Vakuum-Fall ($127{,}53\ \text{m}$)

* **Euler-Computer**: Rechnet mit $9{,}81 \times 5^2 / 2 = 122{,}625\ \text{m}$. Floats erfordern Rundungsoperationen — das erzeugt Wärme und einen Messfehler von ca. 5 m gegenüber dem realen Ergebnis[^2].
* **Fn-Computer (Kern)**: Addiert exakt 13 Takte in der atomaren Skala. Das Ergebnis ist $127.530.000.000.000.000\ \text{fm}$ — eine exakte Ganzzahl, kein Approximationsfehler.
* **Fn-Computer (Maske)**: Setzt den Dezimalpunkt für den User: $127{,}53\ \text{m}$.

Die Differenz von ca. $5\ \text{m}$ zwischen dem Euler-Modell und dem Fn-Modell ist kein Messfehler — sie ist der Beweis, dass das klassische Modell strukturell unvollständig ist[^2].

---

**Bezugsdokumente & Quellen:**

[^1]: Fn-Logik: Die Mathematik des Prozesses — DOI: [10.5281/zenodo.18757232](https://doi.org/10.5281/zenodo.18757232)
[^2]: Energie-Revolution - Preprint — DOI: [10.5281/zenodo.18778354](https://doi.org/10.5281/zenodo.18778354)
[^3]: Tensor-Realitäten (TdR) — DOI: [10.5281/zenodo.18727529](https://doi.org/10.5281/zenodo.18727529)

---
*Lizenz: Pulvermacher Open Research License (PORL) v1.0*
