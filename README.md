*![CNG-Resized](https://github.com/user-attachments/assets/2b6c7368-813d-4569-ab97-ad32c3304c0e)*


Willkommen!  
Dieses Repository dokumentiert ein End-to-End-Projekt im Bereich Workforce Operations & People Analytics, das ich im Rahmen eines MSP-Programms für ein deutsches Telekommunikationsunternehmen im Q2 2025 umgesetzt habe.Ziel war es, ein **zentrales SmartSheet-Dashboard** aufzubauen, das Anfragen, Aufträge, Verlängerungen, Workload, Zeitaufwand, Skills und Team-Stimmung für ein **nicht-technisches Team aus 5 MSP Consultants, 1 Operations Manager und 1 Account Director** sichtbar macht.

Ziel des Projekts ist es, **Kapazitäten und Engpässe im Team transparent zu machen**, **SLA-Risiken frühzeitig zu erkennen** und dem Management eine Grundlage für **datenbasierte Entscheidungen** über Ressourceneinsatz, Priorisierung und Prozessoptimierung zu liefern.

---

## Überblick – Was ist das Dashboard?

Das **Workforce Operations & Team Dashboard** bündelt mehrere bisher getrennte Informationsquellen in einer Oberfläche:

- **Workload 1–3**: Anfragen, aktive Aufträge und Verlängerungen je Consultant, basierend auf HR4YOU-VMS-Daten  
- **Team Dashboard & KPI-Kacheln**: tagesaktuelle Kennzahlen zu aktiven Anfragen, SL heute, Anfragen heute/gestern, Reaktionszeit-Risiken  
- **Clockify-Workstreams**: wöchentlicher Zeitaufwand nach Tätigkeitsbereichen (z. B. Administrative Support, Client Communication, Talent Shortlisting)  
- **Skills in VMS**: Häufigkeit von Primär-Skills (z. B. Projektmanagement, Data Analysis, SAP, Sprachkenntnisse)  
- **Mood Board**: visuelle Darstellung der Team-Stimmung und Unterstützungskapazität („I can support“, „I need support“, „Urlaub“)  
- **Aktienkurs-Widget**: kleines, Python-basiertes Element, das den Aktienkurs des Kunden inkl. Veränderung der letzten 3 Monate anzeigt

Das Dashboard ist so gestaltet, dass **nicht-technische Nutzer:innen** ohne Data- oder IT-Kenntnisse erkennen können: *Wer arbeitet woran, wie stark ist das Team belastet, und wo brennt es?*

---

## Was zeigt die Analyse?

- Welche Consultants **wie viele Anfragen, Aufträge und Verlängerungen** gleichzeitig betreuen – inklusive Segmentierung nach Vertragstyp (z. B. T&M vs. AÜ).  
- In welchen **Geschäftsbereichen und Prozessschritten** (z. B. in Genehmigung, kommerziell geprüft, Nachverhandlung) sich Anfragen und Verlängerungen stauen.  
- Wie sich der **Zeitaufwand nach Workstreams** verteilt – z. B. hoher Anteil „Administrative Support“ vs. wertschöpfende Tätigkeiten wie „Talent Shortlist Creation & Presentation“ oder „Client Communication & Relationship Management“.  
- Welche **Skills im VMS** am häufigsten vorkommen und damit besonders stark nachgefragt sind (z. B. Projektmanagement, Englisch/Deutsch, Agile Methoden, SAP, Data Analysis).  
- Wie es dem Team **emotional und kapazitativ** geht: Wer kann unterstützen, wer ist im Normalmodus, wer ist überlastet, wer ist im Urlaub?

Das Dashboard liefert damit klare Zusammenhänge zwischen **Workload, Zeitaufwand, Skills und Team-Stimmung** und macht strukturelle Muster sichtbar, statt nur Einzelzahlen zu zeigen.

---

## Welche Entscheidungen unterstützt es?

- **Workload- und Kapazitätssteuerung**  
  - Neuzuteilung von Anfragen, Aufträgen und Verlängerungen zur Entlastung einzelner Consultants  
  - Priorisierung von Fällen in kritischen Status (z. B. Nachverhandlung, kommerzielle Prüfung)

- **SLA- und Risiko-Management**  
  - Monitoring von Kennzahlen wie Reaktionszeit gefährdet (KPI)  
  - Frühwarnsystem für überfällige oder riskante Anfragen und Verlängerungen

- **Zeit- und Tätigkeitssteuerung**  
  - Identifikation von Bereichen mit hohem administrativen Aufwand  
  - Rückschlüsse auf Automatisierungspotenzial und Prozessvereinfachung

- **Skill- & Ressourcenplanung**  
  - Abgleich von nachgefragten Skills mit bestehenden Profilen  
  - Ableitung von Trainings- und Recruiting-Bedarfen

- **Team-Wohlbefinden & nachhaltige Performance**  
  - Nutzung des Mood Boards in Regelmeetings (Wer kann unterstützen? Wer ist überlastet?)  
  - Verknüpfung von Workload und Stimmung zur Vermeidung von Burnout

Dieses Dashboard ermöglicht Führungskräften, **Kapazitätsengpässe, Prozessflaschenhälse, Zeitfresser und Belastungsspitzen im Team sofort zu erkennen** und **steuernd einzugreifen**, statt nur reaktiv zu handeln.

---

## Tech Stack: SmartSheet, Excel, HR4YOU, Clockify API, Python

**SmartSheet**  
- Zentrales Frontend für alle Dashboards  
- Nutzung von Berichten, Formeln, Summary-Feldern, cross-sheet references und grafischen Elementen (Charts, Kacheln, Boards)

**Excel & HR4YOU (VMS)**  
- Regelmäßige Exporte aus dem VMS für:
  - Anfragen (Requests)  
  - Aufträge (Assignments)  
  - Verlängerungen (Extensions)  
  - Skill-Daten  
- Aufbereitung der Rohdaten in Excel, anschließend Mapping und Import nach SmartSheet

**Clockify REST API**  
- Automatischer Abruf von Worklogs nach Workstream  
- Aggregation der Stunden pro Woche und Workstream  
- Übergabe der bereinigten Daten an SmartSheet, damit das Zeitaufwands-Diagramm ohne manuelle Exporte aktuell bleibt

**Python**  
- Skript zur Aggregation der **VMS-Skills** (Zählung und Sortierung nach Häufigkeit)  
- Skript zur Aktualisierung des **Aktienkurs-Widgets** (aktueller Kurs + 3-Monats-Veränderung)  
- Export der Ergebnisse in ein Format, das direkt in SmartSheet eingelesen werden kann (z. B. CSV/Excel)

---

## Operations-Modell & Datenpipeline

Im Rahmen des Projekts habe ich ein **ganzheitliches Reporting- und Operations-System** aufgebaut, das den täglichen Ablauf im MSP-Team abbildet – von der **Datenaufnahme** bis zur **Visualisierung in SmartSheet**.

### Datenaufnahme (HR4YOU + Clockify + Python)

- Exporte aus **HR4YOU** für:
  - Anfragen (Requests) inkl. Statusverlauf  
  - Aufträge (Assignments) inkl. Vertragstyp  
  - Verlängerungen inkl. Verhandlungsstatus (MSP vs. Lieferant)  
  - Skills (Primär-Skills aus Profilen / Positionen)  

- **Clockify** als Quelle für:
  - Arbeitszeit je Workstream (z. B. Administrative Support, Client Communication, Talent Shortlisting, Reporting, Learning)  
  - wöchentliche Aggregation der Stunden  

- **Python-Skripte** als Zusatzquelle für:
  - Skills in VMS (Häufigkeitstabelle)  
  - Aktienkurs und 3-Monats-Veränderung  

### Datenbereinigung & Transformation

- Vereinheitlichung von Statusbezeichnungen (z. B. unterschiedliche Schreibweisen / Sprachen)  
- Aufbau von Mappings für:
  - Anfrage-Typen (z. B. Ausschreibung, Direktbeauftragung, Pre-named)  
  - Verlängerungsstatus (MSP vs. Lieferant vs. bestätigt)  
  - Workstreams (standardisierte Namen für Clockify-Projekte / Tags)  

- Berechnung von Zusatzfeldern, u. a.:
  - Anzahl aktiver Anfragen / Aufträge / Verlängerungen je Consultant  
  - Gruppierung nach Vertragstyp (T&M, AO …)  
  - Aggregierte Stunden je Workstream und Woche  
  - Häufigkeitsverteilung von Skills  

### Datenmodellierung

Aufbau eines **logischen Modells** in SmartSheet mit folgenden Kernelementen:

- **Requests (Workload 1)** – Fokus auf offene Anfragen  
- **Assignments (Workload 2)** – Fokus auf aktive Aufträge  
- **Extensions (Workload 3)** – Fokus auf Verlängerungs-Cases  
- **Workstreams (Clockify-View)** – Zeitaufwand nach Tätigkeiten  
- **Skills (VMS-Skills)** – Häufigkeit Primär-Skills  
- **Team Dashboard** – konsolidierte Sicht über alle genannten Tabellen  
- **Mood Board** – qualitative Ergänzung zur quantitativen Sicht

Die Tabellen sind über **Consultant**, **Zeiträume** und **Status** logisch miteinander verbunden, sodass sich Kennzahlen konsistent über Workloads, Zeitaufwand und Skills hinweg auswerten lassen.

---

## Visualisierung & Data Storytelling in SmartSheet

Die bereinigten und modellierten Daten werden in **SmartSheet-Dashboards** visualisiert:

- **Übersichts-Dashboard** mit:
  - KPI-Kacheln (aktive Anfragen, SL heute, Anfragen heute/gestern, Reaktionszeit-Risiko)  
  - Diagrammen zu:
    - Offene Anfragen nach Geschäftsbereich  
    - Workload je Consultant  
    - Auftragsverteilung und Vertragstypen  
    - Verlängerungen nach Status  

- **Workstreams-Dashboard** mit:
  - Balkendiagramm „Wöchentlicher Zeitaufwand nach Workstreams“  
  - Fokus auf Admin vs. wertschöpfende Aktivitäten  

- **Skills & Stock Dashboard** mit:
  - Tabelle/Diagramm „Skills in VMS nach Häufigkeit“  
  - kleinen Kacheln für Aktienkurs & 3-Monats-Veränderung  

- **Mood Board** als visuelles Element zur Diskussionsunterstützung in Team-Meetings  

Die Ergebnisse werden in einer **kompakten Storyline** für Management und Team präsentiert, mit klarem Fokus auf:  
*Wo stehen wir? Wo sind Engpässe? Was sollten wir als Nächstes tun?*

---

## Erweiterbarkeit

Die Kombination aus:

- wiederverwendbaren Excel-/SmartSheet-Mappings,  
- automatisierten Clockify-API-Abfragen und  
- modularen Python-Skripten  

ist so angelegt, dass:

- weitere Zeiträume (weitere Wochen/Monate) einfach ergänzt werden können,  
- zusätzliche Teams (z. B. weitere MSP- oder TA-Teams) eingebunden werden können,  
- neue Workstreams, Skills oder KPIs ohne grundlegenden Umbau ergänzt werden können,  
- eine zukünftige direkte Schnittstelle zu HR4YOU (z. B. via API) in die bestehende Struktur integrierbar wäre.

Dieses Projekt zeigt, wie sich mit **SmartSheet + API + Python** ein sehr praxisnahes, operatives **People- & Workforce-Analytics-System** aufbauen lässt, das non-technischen Stakeholdern täglich hilft, bessere Entscheidungen zu treffen.
```
Perfekt, dann kommt jetzt der **„Mehr Infos“-Block** für dein SmartSheet-Projekt – im gleichen Stil wie bei deinem Flight-Punctuality-Projekt, aber inhaltlich auf **Workforce Operations & Team Dashboard** angepasst.
Du kannst das direkt unter deine Einleitung ins README kleben.

```markdown
Mehr Infos:

## Projekt-Hintergrund

Dieses Projekt entstand im Rahmen eines **MSP-Programms** für einen Großkunden, in dem ein Team aus **5 MSP Consultants, 1 Operations Manager und 1 Account Director** täglich eine hohe Anzahl an Anfragen, Aufträgen und Verlängerungen steuert.

Die operative Realität war geprägt von:

- vielen parallelen Fällen je Consultant,
- komplexen Genehmigungs- und Verlängerungsprozessen,
- manuell gepflegten Excel-Listen ohne zentrale Sicht,
- fehlender Transparenz über Zeitaufwand, Skills und Team-Belastung.

Als Data Analyst im Bereich **Workforce Operations & People Analytics** bestand das Ziel dieses Projekts darin:

- **strukturelle Ursachen für Überlastung und SLA-Risiken** sichtbar zu machen,  
- **Workload- und Kapazitätsunterschiede im Team** transparent darzustellen,  
- **Zeitfresser und ineffiziente Workstreams** zu identifizieren,  
- **Skills- und Stimmungsdaten** in die operative Steuerung einzubinden,  
- nicht-technischen Stakeholdern **klare, visuelle Entscheidungsgrundlagen** zu liefern.

Die wichtigsten Erkenntnisse und Empfehlungen strukturieren sich in vier Kategorien:

- **Kategorie 1: Anfrage-Pipeline & Team-Workload (Workload 1)**  
- **Kategorie 2: Aufträge & Verlängerungen (Workload 2 & 3)**  
- **Kategorie 3: Zeitaufwand nach Workstreams (Clockify)**  
- **Kategorie 4: Skills, Team-Stimmung & Risikoindikatoren**

---

## Datenstruktur & erste Prüfungen

Die Datenbasis besteht aus operativen HR- und Zeitdaten, die aus verschiedenen Systemen zusammengeführt wurden:

- **HR4YOU (VMS)** – Anfragen, Aufträge, Verlängerungen, Skills  
- **Clockify** – Arbeitszeit nach Workstreams  
- **Python-Skripte** – Aggregation von Skills sowie Abruf eines Aktienkurses  
- **SmartSheet** – zentrales Frontend und Reporting-Schicht

Bei den ersten Prüfungen wurden u. a. folgende Schritte durchgeführt:

- Ausschluss von Datensätzen mit **offensichtlich fehlerhaften oder unvollständigen Statusangaben** (z. B. fehlende IDs, inkonsistente Datumsfelder).
- Vereinheitlichung von **Status- und Typbezeichnungen** (z. B. unterschiedliche Schreibweisen für Verlängerungsstatus, Vertragstypen, Anfragearten).
- Definition von **operativen Kennzahlen**, z. B.:
  - „aktive Anfrage / Auftrag / Verlängerung“ je Consultant,
  - „kritische Fälle“ anhand Status oder Nähe zu SLA-Grenzen,
  - „administrativer vs. wertschöpfender Zeitaufwand“ je Workstream.
- Prüfung auf **Dubletten** (z. B. mehrfach exportierte Anfragen) und Konsistenz der Verknüpfungsfelder (IDs, Consultant-Namen).

---

## Datenquellen & Datenmodell

### requests (Workload 1 – Requests & Pipeline)

Zentrale Tabelle mit allen **aktiven Anfragen (Requests)** im MSP-Programm. Enthält u. a.:

- Request ID  
- Geschäftsbereich / Fachbereich  
- zuständige:r Consultant  
- Anfrage-Typ (z. B. Ausschreibung, direkte Beauftragung, Pre-named)  
- aktueller Prozessstatus (z. B. in Genehmigung, kommerziell geprüft, reaktiviert, verlängert bestätigt)  
- Erfassungs- und Änderungsdatum  

Diese Tabelle bildet die Basis für:

- „Offene Anfragen nach Geschäftsbereich“  
- „Aktive Anfragen je Consultant“ (Workload 1)  
- Team-KPIs im Dashboard (aktive Anfragen, SL heute, Anfragen heute/gestern, Reaktionszeit gefährdet).

---

### assignments (Workload 2 – Aufträge)

Tabelle mit allen **aktiven Aufträgen (Assignments)** im Programm. Enthält u. a.:

- Assignment / Auftrag ID  
- zuständige:r Consultant  
- Vertragstyp (z. B. T&M, AO)  
- Anzahl aktiver Aufträge je Consultant  

Diese Tabelle ist verknüpft mit `requests` über Fall- oder Requisitions-IDs (je nach Prozess) und fließt in:

- „Auftragsverteilung nach Disponent:in“  
- „Anzahl Aufträge nach Vertragstyp (Workload 2)“.

---

### extensions (Workload 3 – Verlängerungen)

Tabelle mit allen **Verlängerungsfällen**. Enthält u. a.:

- Assignment / Auftrag ID  
- zuständige:r Consultant  
- Verlängerungsstatus  
  - Nachverhandlung (MSP)  
  - Nachverhandlung (Lieferant)  
  - Bestätigt / abgelehnt  

Diese Tabelle ist mit `assignments` verknüpft und speist:

- „Aktive Verlängerungen nach Status (Workload 3)“  
- Kennzahlen zu kritischen Verlängerungen (z. B. in Verhandlung, drohender Ablauf).

---

### clockify_workstreams (Zeitaufwand nach Workstreams)

Aggregierte Tabelle aus der **Clockify API**, mit:

- Workstream-Name (z. B. Administrative Support, Team Communication & Collaboration,  
  Talent Shortlist Creation & Presentation, Client Communication & Relationship Management, Compliance Management, Personal Learning & Growth, Reporting & Data Maintenance etc.)  
- Woche / Zeitraum  
- Gesamte Stunden je Workstream und Woche  

Diese Daten bilden die Grundlage für:

- „Wöchentlicher Zeitaufwand nach Workstreams“  
- Abgrenzung von administrativen vs. wertschöpfenden Tätigkeiten.

---

### vms_skills (Skills in VMS)

Durch ein Python-Skript aufbereitete Tabelle mit:

- `Primary` – Name des Primär-Skills  
- `Häufigkeit` – wie oft dieser Skill im VMS vorkommt  

Beispiele: Projektmanagement, Englisch, Deutsch, Agile Methodologie, Data Analysis, SAP Applications, Scrum usw.

Diese Tabelle fließt in:

- „Skills in VMS nach Häufigkeit“ (Ranking der wichtigsten Kompetenzen).

---

### mood_board_state (Team-Stimmung & Verfügbarkeit)

Qualitative Ergänzung mit:

- Teammitglied / Rolle  
- aktueller Status:
  - „I can support!“  
  - „All is good!“  
  - „I need support!“  
  - „Urlaub“  

Diese Informationen werden im **Mood Board** visuell dargestellt und in Meetings genutzt, um Überlastung und Unterstützungsbedarf zu erkennen.

---

## Executive Summary

Das Workforce Operations & Team Dashboard zeigt deutliche strukturelle Muster im MSP-Team:

1. **Workload & Fälle**  
   - Anfragen, Aufträge und Verlängerungen sind **ungleich auf Consultants verteilt**; einzelne Teammitglieder tragen signifikant mehr Last als andere.  

2. **Zeitaufwand & Workstreams**  
   - Ein großer Anteil der Arbeitszeit fließt in **Administrative Support**, während zentrale, wertschöpfende Tätigkeiten wie Talent-Shortlisting oder Client-Relationship weniger Zeitanteile einnehmen.

3. **Skills & Team-Stimmung**  
   - Skills im VMS konzentrieren sich auf wenige Kernkompetenzen (z. B. Projektmanagement, Sprachen, Agile Methoden), während das Mood Board zeigt, dass **Phasen hoher Auslastung** klar mit „I need support“-Signalen korrespondieren.

Diese Ergebnisse machen deutlich, dass **Kapazitätssteuerung, Prozessvereinfachung und gezielte Nutzung von Skills und Stimmungssignalen** entscheidend sind, um Überlastung zu vermeiden und SLA-konform zu arbeiten.

---

## Insights Deep Dive

### Kategorie 1: Anfrage-Pipeline & Team-Workload (Workload 1)

**Insight 1:** Einzelne Geschäftsbereiche generieren einen überproportional hohen Anteil an offenen Anfragen, während andere Bereiche vergleichsweise wenig Volumen erzeugen.  
Das ermöglicht eine gezieltere Spezialisierung und Kapazitätsplanung je Consultant.

**Insight 2:** Die Zahl aktiver Anfragen ist **stark zwischen den Consultants verteilt** – einige bearbeiten ein Vielfaches der Anfragen anderer.  
Hier liegt ein direkter Hebel für **Workload-Balancing und Priorisierung**.

**Insight 3:** KPI-Kacheln wie „Aktive Anfragen“, „SL heute“ und „Reaktionszeit gefährdet (KPI)“ zeigen tagesaktuell, wo **SLA-Risiken** entstehen.  
Das Team kann frühzeitig eingreifen, statt nur auf Eskalationen zu reagieren.

**Insight 4:** Die Statusverteilung (z. B. in Genehmigung, kommerziell geprüft, verlängert bestätigt) macht Prozessschritte sichtbar, in denen Fälle „hängen bleiben“.  
Diese Engpässe sind Ansatzpunkte für **Prozessanpassungen oder bessere Abstimmung mit dem Kunden**.

---

### Kategorie 2: Aufträge & Verlängerungen (Workload 2 & 3)

**Insight 1:** Die **Anzahl aktiver Aufträge** ist ebenfalls ungleich auf Consultants verteilt – mit Spitzenwerten von knapp 300 Aufträgen bei einzelnen Personen.  
Ein klarer Hinweis auf die Notwendigkeit regulatorischer Workload-Grenzen und Verteilung.

**Insight 2:** Die Mischung aus **Vertragstypen (T&M vs. AO)** je Consultant zeigt, dass nicht nur die Anzahl der Aufträge, sondern auch deren Komplexität und wirtschaftliche Bedeutung variiert.  
Relevant für **strategische Steuerung** und **Risikobewertung**.

**Insight 3:** Die Auswertung der **Verlängerungen nach Status** (MSP-Nachverhandlung, Lieferanten-Nachverhandlung, bestätigt) macht sichtbar, wo Verlängerungen ins Stocken geraten.  
Das unterstützt die **Forecast-Planung** und gezielte Eskalation.

**Insight 4:** Durch die Kombination von Requests (Workload 1), Assignments (Workload 2) und Extensions (Workload 3) entsteht eine **End-to-End Sicht vom Eingang bis zur Verlängerung**.  
Diese Sicht ist entscheidend, um **Bottlenecks im Gesamtprozess** zu erkennen.

---

### Kategorie 3: Zeitaufwand nach Workstreams (Clockify)

**Insight 1:** „Administrative Support“ nimmt mit Abstand den größten Anteil der Wochenarbeitszeit ein (z. B. >100 Stunden).  
Darin steckt erhebliches **Automatisierungs- und Standardisierungspotenzial**.

**Insight 2:** Kommunikation („Team Communication & Collaboration“, „Client Communication & Relationship Management“) bindet einen großen Zeitblock, ist aber meist wenig transparent dokumentiert.  
Hier helfen klare Kommunikationsregeln und strukturierte Zeitfenster.

**Insight 3:** Wertschöpfende Tätigkeiten wie „Talent Shortlist Creation & Presentation“ konkurrieren zeitlich mit Reporting- und Systemaufgaben.  
Diese Erkenntnis unterstützt die **Neuverteilung von Aufgaben** (z. B. Admin-Support vs. beratende Rolle).

**Insight 4:** Der Workstream „Personal Learning & Growth“ macht sichtbar, ob und in welchem Umfang **Weiterbildung** im Alltag stattfindet.  
Das ist besonders relevant für Skill-Aufbau und langfristige Team-Performance.

---

### Kategorie 4: Skills, Team-Stimmung & Risikoindikatoren

**Insight 1:** Die „Skills in VMS nach Häufigkeit“ zeigen, dass bestimmte Kompetenzen (z. B. Projektmanagement, Sprachen, Data Analysis, SAP, Agile Methoden) besonders ausgeprägt sind.  
Das erleichtert **Matching, Projektbesetzung** und die Planung zukünftiger Rekrutierungen.

**Insight 2:** Python-basierte Aggregationen stellen sicher, dass Skill- und Marktdaten (z. B. Aktienkurs) **aktuell und konsistent** vorliegen, ohne dass das Team sie manuell pflegen muss.  
Das reduziert **Fehleranfälligkeit und Pflegeaufwand**.

**Insight 3:** Das Mood Board verbindet Kennzahlen mit **menschlicher Perspektive**: Überlastung („I need support“) und freie Kapazität („I can support“) werden sichtbar.  
Dieses Instrument unterstützt **frühes Gegensteuern**, bevor es zu Burnout oder Fehlerhäufungen kommt.

**Insight 4:** In der Kombination von Workload, Zeitaufwand, Skills und Stimmung entsteht ein **ganzheitliches Bild der Teamgesundheit** – weit über klassische KPI-Berichte hinaus.  
Das stärkt **nachhaltige Performance** statt reiner Output-Optimierung.

---

## Empfehlungen

Basierend auf den Analyseergebnissen sollte das MSP- und Operations-Team folgende Maßnahmen in Betracht ziehen:

1. **Einführung eines strukturierten Workload-Balancing-Prozesses**  
   - Regelmäßiges Review von Workload 1–3  
   - Definition von Zielkorridoren pro Consultant (maximale Anzahl aktiver Fälle).

2. **Reduktion administrativer Last durch Automatisierung**  
   - Standardisierung von Workflows und Vorlagen  
   - Verlagerung wiederkehrender manueller Tätigkeiten in automatisierte Prozesse (z. B. Reports, Statusupdates).

3. **Fokussierung der Kommunikationswege**  
   - Klar definierte Kanäle für Kund:innen, Suppliers und interne Abstimmung  
   - Reduktion ad-hoc Kommunikation zugunsten strukturierter Formate.

4. **Strategische Nutzung von Skills-Daten**  
   - Abgleich von Nachfrage vs. vorhandenen Skills  
   - Planung von Trainings, Cross-Skilling und gezieltem Recruiting.

5. **Systematische Nutzung des Mood Boards**  
   - Fixer Agendapunkt in Team-Meetings („Wer braucht Support, wer kann Support geben?“)  
   - Verknüpfung mit Workload- und Zeitdaten als Frühwarnsystem.

---

## Annahmen und Einschränkungen

Zur Sicherstellung einer klaren analytischen Grundlage wurden folgende Annahmen getroffen:

- Exporte aus HR4YOU sind **zeitlich versetzt** (keine Echtzeitdaten); kurzfristige Änderungen können zwischen zwei Läufen fehlen.  
- Die Kategorisierung von Workstreams in Clockify setzt voraus, dass Teammitglieder ihre Zeiten **konsequent und korrekt** buchen.  
- Einzelne Statusfelder und Bezeichnungen im VMS sind nicht vollständig standardisiert; wo sinnvoll, wurden sie **vereinheitlicht oder gruppiert**.  
- Skill-Daten spiegeln die im VMS gepflegte Realität wider und können von tatsächlichen Fähigkeiten leicht abweichen (Pflegequalität).  
- Die im Dashboard gezeigten Kennzahlen sind für dieses Portfolio-Beispiel **teilweise anonymisiert bzw. aggregiert**, um Vertraulichkeit zu gewährleisten.

---

## Weitere Ressourcen

- SmartSheet-Dashboard (Screenshots): im Ordner `screenshots/`  
- Python-Skripte zur Skill- und Kursaggregation: im Ordner `python/`  
- Dokumentation zur Datenzuordnung HR4YOU → SmartSheet: im Ordner `smartsheet/`  
- Beispiel-Layouts und Mappings: siehe `mapping_hr4you_to_smartsheet.md`


