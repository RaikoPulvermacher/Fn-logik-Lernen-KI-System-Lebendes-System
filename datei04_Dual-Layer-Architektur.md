# datei04: Dual-Layer-Architektur (Ganzzahl-Standard & Maskierung)

## 1. Das Prinzip der Skalierung: Weg mit dem Komma
In herkömmlichen Systemen entstehen Rundungsfehler, weil versucht wird, die Realität in Dezimalstellen (Kommazahlen) zu pressen. Die Fn-Logik nutzt stattdessen die **Atomare Ganzzahl-Ebene**.

* **Der Trick**: Anstatt $127,53$ Meter zu berechnen (was Floats erfordert), rechnet das System im Hintergrund mit Femtometern ($10^{-15}$).
* **Der Wert**: $127.530.000.000.000.000$ Femtometer.
* **Der Vorteil**: Eine reine Ganzzahl (Integer). Es gibt keine "halben" Einheiten, nur diskrete Takte.

## 2. Die zwei Ebenen des Systems

### A. Der Kern (Back-End: Atomare Ebene)
Hier findet die eigentliche "Intelligenz" statt. Der Kern arbeitet ausschließlich mit der Fn-Additionslogik auf der kleinstmöglichen physikalischen Skala.
* **Einheit**: Femtometer / Plancktakt.
* **Logik**: Reine Ganzzahl-Addition.
* **Eigenschaft**: 100% verlustfrei, keine thermische Emission (kalt), absolute Präzision.

### B. Die Maske (Front-End: Makro-Ebene)
Die Maske ist das Interface für den Menschen. Sie "übersetzt" die gigantischen Ganzzahlen des Kerns in lesbare Formate.
* **Funktion**: Verschiebung des Dezimalpunktes für die Anzeige.
* **Beispiel**: Der Kern liefert den exakten Ganzzahl-Wert des Vakuum-Falls, die Maske zeigt uns "127,53 m".
* **Trennung**: Die Maske darf "runden" oder "schätzen" für das Auge, aber der Kern darf niemals runden, um die Integrität des Prozesses zu wahren.



## 3. Warum Computer damit besser laufen
Wenn eine KI heute "lernt", verliert sie Information durch die Float-Konvertierung. In der Dual-Layer-Architektur passiert das nicht:
1.  **KI-Training**: Findet im Kern statt. Jedes "Gewicht" ist eine exakte Position auf der atomaren Skala.
2.  **Keine Reibung**: Da der Kern niemals dividiert oder Wurzeln zieht, gibt es keinen Datenstau und keine Hitze.
3.  **Unendliche Tiefe**: Man kann neuronale Netze mit Millionen von Schichten bauen, ohne dass die Präzision abnimmt, da Ganzzahlen nicht "ausleiern".

## 4. Beispiel: Der Vakuum-Fall (127,53 m)
* **Euler-Computer**: Rechnet mit $9,81 \times 5^2 / 2 = 122,625$. Er muss Floats verwalten, was Hitze erzeugt.
* **Fn-Computer (Kern)**: Addiert 13 Takte in der atomaren Skala. Das Ergebnis ist eine exakte Ganzzahl in Femtometern.
* **Fn-Computer (Maske)**: Setzt das Komma für den User bei 127,53 m. 

---

**Bezugsdokumente:**
* [1] Fn-Logik: Die Mathematik des Prozesses | DOI: [10.5281/zenodo.18757232](https://doi.org/10.5281/zenodo.18757232)
* [2] IT-Logik: Der Ganzzahl-Prozessor | (In Vorbereitung)

---
*Lizenz: Pulvermacher Open Research License (PORL) v1.0*
