---
layout: post
title: Access Control
description: Bell-LaPadula-Modell and Chinese-Wall-Modell
category: blogs
---

## Bell LaPadula 
------------------
**A state machine model used for enforcing access control in government and military applications.**

### Definition
+ eine Menge S von Subjekten
+ eine Menge O von Objekten
+ eine Menge A = {read, write, append, excute} von Zugriﬀsoperation
+ eine halbgeordnete Menge L von Sicherheitsleveln, auf der ein eindeutiges Maximum deﬁniert ist
+ B ⊆ S × O × A die Menge aller aktuellen Zugriﬀe ist
+ M = m(i,j)(i=..,j=...),die Zugriﬀskontrollmatrix ist, deren Eintrag m(i,j) ⊆ A die erlaubten Zugriﬀe des Subjektes i auf das Objekt j beschreibt
+ F = (f s , f c , f o ) ein Funktionstripel:
  * f s : S → L weist jedem Subjekt ein maximales Sicherheitslevel zu
  * f c : S → L weist jedem Subjekt sein aktuelles Sicherheitslevel zu
  * f o : O → L weist jedem Objekt ein Sicherheitslevel zu

![alter text](/resources/postImage/AccessControl/Xnip2019-07-30_17-20-32.jpg)

### Discretionary-Security/ds-Eigenschaft
+ user's action is what it has predefined

∀(s, o, a) ∈ B : a ∈ m(s,o) 

### Simple-Security/ss-Eigenschaft
+ No Read-up

∀(s, o, read) ∈ B : f s (s) ≥ f o (o)

### Star Property
+ No Write-down

∀ (s, o, {write, append}) ∈ B : f o (o) ≥ f c (s)

### Nachteile des Bell-LaPadula-Modells
* Eie aktuellen Sicherheitslevel werden nie herabgesetzt
* Subjekte dürfen auf Objekte höheren Sicherheitslevels schreibend zugreifen 

## Chinese-Wall-Modell (Brewer-Nash-Modell)
-----------------------

### Definition
+ eine Menge C von Firmen
+ eine Menge S von Beratern
+ eine Menge O von Objekten
+ eine Menge A = {read, write} von Zugriﬀsoperationen
+ eine Funktion y: O → C, die jedem Objekt seine eindeutige Firma zuweist
+ eine Funktion x: O → P(C), die jedem Objekt die Menge an Firmen zuweist, mit denen es in Konﬂikt steht
  
### Simple-Security/ss-Eigenschaft

**all Anfrage** to object o:
+ the berater hasn't done anything with any object o', which is not from another Firma or
+ the Berater has not **read/write** any o', which has conflicts with o
  
y(o)=y(o') ∨ y(o)!∈ x(o')

### Star Property

a **write Anfrage** to oject o: 
+ the berater hasn't **read** any object o', which is not from another Firma or
+ all the o' the berater has **read** any o', but o' has no conflicts with anything

y(o)=y(o') ∨ x(o')=∅ 


[Yange]:    http://camscofie.github.io  "Yange"
