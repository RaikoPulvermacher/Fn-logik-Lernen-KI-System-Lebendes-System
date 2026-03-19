# datei03: KI-Architektur ohne Floats (Technisches Manifest)

## 1. Das Problem: Gleitkommazahlen als logische Reibung

Moderne KI-Systeme basieren auf Gleitkommazahlen (Floats) für die Gewichtung neuronaler Netze[^1]. Jede Float-Operation erzeugt Rundungsfehler, die sich als **thermische Emission** (Abwärme) manifestieren — ein systemischer Verlust von ca. 89 % der eingesetzten Energie[^2].

* **Euler-Widerstand**: Der klassische Ansatz quadriert Zeit ($e^{iωt}$) und erzeugt damit irrationale Zwischenwerte, die gerundet werden müssen.
* **Kaskadierender Fehler**: In tiefen Netzen multipliziert sich dieser Fehler mit jeder Schicht, bis das Modell instabil wird oder enorme Rechenkapazität zur Fehlerkorrektur benötigt[^1].

## 2. Die Lösung: Ganzzahl-Integrität (Wurzel-Redundanz)

Die Fn-Logik ersetzt Float-Gewichte durch **ganzzahlige additive Zustände**[^1]:

$$\text{Gewicht}_{n} = \text{Gewicht}_{n-1} + \text{Gewicht}_{n-2}$$

Kein Runden. Kein Extrahieren. Keine Abwärme.

| Klassische KI (Float) | Fn-KI (Ganzzahl) |
|-----------------------|------------------|
| Gewichte als irrationale Dezimalzahlen | Gewichte als additive Fn-Zustände |
| Rundungsfehler bei jeder Operation | Exakte Ganzzahl-Integrität |
| ~89 % thermischer Verlust | Nahezu null Wärmeentwicklung |
| Erfordert Kühlung | Läuft kalt |

## 3. Effizienz-Sprung: Faktor 1000

Durch den Wegfall irrationaler Operationen ($\sqrt{x}$, $e^x$, Division) und deren Ersatz durch reine Addition ergibt sich[^2]:

* **Rechengeschwindigkeit**: Ganzzahl-Addition ist auf Prozessoren die schnellste mögliche Operation — Faktor ~1000 gegenüber Float-Arithmetik.
* **Speichereffizienz**: Fn-Zustände benötigen weniger Bits als IEEE-754-Floats.
* **Thermische Emission**: Annäherung an null, da keine Wärme durch Rundungsoperationen entsteht[^1].

## 4. Trennung von Kern und Schablone

Die Architektur teilt sich in zwei klar getrennte Ebenen[^1][^2]:

* **Back-End (Kern)**: Rechnet ausschließlich in Fn-Ganzzahlen. Verlustfrei, kalt, präzise. Entspricht dem biologischen Zellkern.
* **Front-End (Schablone)**: Skaliert die Ergebnisse des Kerns für menschliche Lesbarkeit (z. B. Dezimaldarstellung, Visualisierung). Erzeugt kontrollierte Reibung nur an der Ausgabeschicht.

```
[Eingabe] → [Fn-Kern (Ganzzahl-Addition)] → [Schablone (Skalierung)] → [Ausgabe]
     ↑                   ↑                             ↑
  Impuls           Verlustfreie               Menschenlesbare
                  Verarbeitung                Darstellung
```

---

**Bezugsdokumente & Quellen:**

[^1]: Fn-Logik: Die Mathematik des Prozesses — DOI: [10.5281/zenodo.19100374](https://doi.org/10.5281/zenodo.19100374)
[^2]: Energie-Revolution 8911: Die Überwindung des Euler-Widerstands — DOI: [10.5281/zenodo.18778354](https://doi.org/10.5281/zenodo.18778354)

---
*Lizenz: Pulvermacher Open Research License (PORL) v1.0*

