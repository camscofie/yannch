---
layout: post
title: Berechenbarkeit
description: Turing-Maschinen und Berechenbarkeit
category: blogs
---

## Die Registermaschine (RAM)
---------------------
Die RAM besteht aus:
+ Ein Programm besteht aus einer Folge von Befehlen.
+ Programmzeilen sind durchnummeriert.
+ Der Befehlszähler b startet bei 1 und enthält jeweils die Nummer des nächsten auszuführenden Befehls.
![alter text](../../resources/postImage/Turingmachine/Registermaschine.jpg)

+ In den ersten Registern steht zu Beginn der Berechnung die Eingabe.
+ In den übrigen Registern steht 0.
+ Am Ende der Berechnung stehen die Ausgabedaten in vorher festgelegten Registern.
+ Den Inhalt des Registers i bezeichnen wir mit c(i).

### Kostenmodell der Registermaschine (RAM)
+ Üblicherweise wird das **uniforme** Kostenmodell verwendet.
+ Dabei kostet jede Programmzeile bis auf END eine Einheit.
+ Dieses Modell ist gerechtfertigt solange keine großen Zahlen auftreten.
+ Ansonsten ist das **logarithmische** Kostenmodell realistischer.
+ Kosten entsprechen dann der Länge der benutzten Zahlen.


## Die Turingmaschine (TM)
---------------------
Eine TM besteht aus:
+ beidseitig unendlichen Eingabe- und Rechenband
+ freibeweglichem Lese-/Schreibkopf
+ endlicher Kontrolle
![alter text](../../resources/postImage/Turingmachine/TM.jpg)

Die Kontrolle:
  + ist immer in einem von endlich vielen Zuständen
  + entspricht dem Befehlszähler der RAM

Das Eingabe- und Rechenband
  + enthält eine Folge von Symbolen (höchstens eins pro Zelle)
  + entspricht den Registern der RAM. 

### Formale Deﬁnition der Turingmaschine
Eine deterministische Turing-Maschine ((D)TM) besteht aus:
+ Q, einer endlicher Zustandsmenge
+ Σ, einem endlichen Eingabealphabet
+ ¬, einem Blanksymbol mit ¬ !∈ Σ
+ Γ, einem endlichen Bandalphabet mit Σ∪{¬} ⊆ Γ
+ s ∈ Q, einem Startzustand
+ δ: Q×Γ → Q×Γ×{L,R,N}, einer Übergangsfunktion
+ F ⊆ Q, einer Menge von Endzuständen
