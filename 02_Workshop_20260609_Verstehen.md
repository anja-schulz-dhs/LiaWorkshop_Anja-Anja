<!--
author:   Sebastian Zug, André Dietrich, Anja Hawlitschek und Anja Schulz

email:    sebastian.zug@informatik.tu-freiberg.de

version:  0.1.0

language: de

narrator: Deutsch Male

mode:     Presentation

date:     22/05/2026

comment:  Phase 3 ("Verstehen") des Workshops "Lehre interaktiv gestalten mit LiaScript" (09.06.2026).
          Idee und Konzepte hinter LiaScript - 15 Minuten.

repository: https://github.com/LiaPlayground/Bibliocon2026

import:    https://raw.githubusercontent.com/LiaTemplates/LiveEdit-Embeddings/refs/tags/0.0.1/README.md

attribute: "Idee und Konzepte hinter LiaScript"
           von Sebastian Zug, André Dietrich,
           Anja Hawlitschek und Anja Schulz
           ist lizenziert unter [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

link:     ../style.css

-->

[![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)]()

# Idee und Konzepte hinter LiaScript

> <h2>Phase 3 ("Verstehen") des Workshops "Interaktive Lehre mit LiaScript</h2>
>
> <div style="height: 2.5em;"></div>
>
> <h4>Prof. Dr. Sebastian Zug, TU Bergakademie Freiberg</h4>
> <h4>Dr. Anja Hawlitschek, Otto-von-Guericke-Universität Magdeburg</h4>
> <h4>Dr. Anja Schulz, Hochschuldidaktik Sachsen</h4>
>
> <h4>09.06.2026</h4>

--------------------------------------------

## Worum geht es in diesen 15 Minuten?

Sie haben in [Phase 0](https://liascript.github.io/course/?https://raw.githubusercontent.com/anja-schulz-dhs/LiaWorkshop_Anja-Anja/refs/heads/main/README.md#1) einiges davon aus Lernendenperspektive kennengelernt, *was* mit LiaScript möglich ist — Quizze, eingebundene Videos, Tabellen, alles in *einer* Seite. Später haben Sie die Möglichkeit alles das - und wenn Sie es wollen noch mehr (z.B. Einbindung von ausführbarem Code, eingebettete Diagramme) - selber umzusetzen. Jetzt geht es jedoch erstmal um das *Warum*:

- Welches Problem löst LiaScript eigentlich?
- Warum reicht ein Lernmanagementsystem (Moodle, OPAL, ILIAS) nicht aus?
- Und was ist der **eine** technische Kern, der alles zusammenhält?

## Ausgangspunkt

>  <!-- Style="color:green" -->__Lehrende möchten motivierende, interaktive Lehr-Lernmaterialien anbieten — und mit Kolleginnen und Kollegen anderer Hochschulen und mit ihren Studierenden teilen.__

                  {{0-1}}
********************************************

**Aber in der Praxis ...**

+ Die individuelle Umsetzung ist **aufwändig und zeitintensiv**.
+ Für verschiedene Formate (Text, Video, Quiz, Daten) braucht es **unterschiedliche Werkzeuge** — H5P hier, LearningApps dort, PowerPoint daneben.
+ Bestehende Inhalte sind **nicht auf das eigene Haus zugeschnitten** — und lassen sich nur schwer anpassen.
+ Materialien aus Moodle/OPAL lassen sich **kaum aus dem System lösen** und in andere Kontexte überführen.

> Welche weiteren Hemmnisse kennen Sie aus Ihrer Lehrpraxis?

********************************************

{{1}}
```ascii

      Wunsch nach                                            Wunsch nach
  einfacher Umsetzung  -----------> Konflikt <----------- interaktiven Elementen
                                                              im Material
```

### OER als Lösungsansatz — die 5V-Freiheiten

           {{0-1}}
**************************************

Das Konflikt-Paar löst sich auf, wenn Materialien **geteilt, angepasst und weiterentwickelt** werden können — statt jedes Mal bei Null anzufangen. Genau das beschreibt der OER-Gedanke:

>  **Open Educational Resources** ... teaching, learning and
> research materials in any medium, digital or otherwise, that reside in the
> **public domain** or have been released under an open license that permits
> no-cost access, use, **adaptation** and **redistribution** by others.
>
> -- UNESCO 2002 Forum on the Impact of Open Courseware [(Link)](https://unesdoc.unesco.org/ark:/48223/pf0000128515)

**************************************

           {{1}}
**************************************

| 5V-Freiheit                  | Bedeutung                                  |
| ---------------------------- | ------------------------------------------ |
| `verwahren/vervielfältigen ` | Download, Speicherung, Vervielfältigung    |
| `verwenden`                  | Nutzung im Schulungskontext                |
| `verarbeiten`                | Umgestaltung und Adaption                  |
| `vermischen`                 | Kombination und Extraktion                 |
| `verbreiten`                 | (digitale) Publikation                     |


*„5 V-Freiheiten für Offenheit" von Jöran Muuß-Merholz und Jörg Lohrer für [open-educational-resources.de](https://open-educational-resources.de)*

> **Die entscheidende Frage:** In welchem *Format* speichere ich meine Materialien, damit alle fünf V-Freiheiten technisch überhaupt möglich sind?

**************************************

### Warum nicht einfach Wikipedia-Wikitext?

Wikipedia zeigt eindrucksvoll, dass kollaborative Inhalte in einem einfachen **Textformat** funktionieren — und genau diese textuelle Quelle ist der Schlüssel zur Nachnutzbarkeit:

```markdown     Ausschnitt aus dem Wikipedia-Artikel "Bibliothek"
Eine '''Bibliothek''' (von [[Altgriechische Sprache|altgriechisch]]
{{lang|grc|βιβλιοϑήκη}} ''bibliothḗkē'' „Büchersammlung") ist eine
[[Dienstleistung]]seinrichtung, die ihren Benutzern den Zugang zu
[[Information]] vermittelt.
```

Für **Lehr-Lernmaterial** hat Wikitext aber entscheidende Schwächen:

+ keine **Interaktivität** (keine Quizze, kein ausführbarer Code, keine Lernstandserfassung),
+ keine **Lernpfad-Strukturen** (Animationen, gestufte Aufdeckung, Selbsttests),
+ keine einfache **Einbettung in Lernmanagementsysteme** (SCORM, xAPI),
+ Fokus liegt auf Enzyklopädie-Artikeln, nicht auf didaktischer Sequenzierung.

> **Die Lücke:** Wir brauchen ein Format, das *so einfach wie Wikitext* ist — aber Interaktion, Lernpfade und LMS-Anschluss von Haus aus mitbringt.

## LiaScript — die Kernidee in einem Satz

> [!IMPORTANT]
> **LiaScript ist Markdown — erweitert um genau die Elemente, die für interaktive Lehre fehlen.**

Markdown kennen Sie wahrscheinlich schon aus GitHub-READMEs, aus der Nextcloud, aus Obsidian oder aus dem Wikipedia-Editor. LiaScript nimmt diese vertraute Textsprache und ergänzt sie um **drei Kernkonzepte**.

### Konzept 1 — Trennung von Inhalt und Darstellung

> __Alles, was geht, wird als reiner Text geschrieben. Wie es am Ende aussieht, entscheidet der Player — nicht der Autor.__

```markdown @embed.style(height: 600px; min-width: 100%; border: 1px black solid)
# Vom Text zur Darstellung

__Formatierter Text__

**Kognitive Aktivierung** ist eine zentrale Voraussetzung für den Lernerfolg.

__Lernerfolg__ — einfach in `$Lernerfolg$` setzen:

Die Lernwirksamkeit einer Lehrveranstaltung ist
$L = \frac{\text{lernrelevante Aktivität}}{\text{gesamte Aktivität}}$

__Tabellen__ — wie in Markdown gewohnt:

| Lehr-Lernform                      | Besonders lernwirksam für ...      |
| ---------------------------------- |:----------------------------------:|
| direkte Instruktion                | Lernende mit wenig Vorwissen  |
| konstruktivistische Methoden       | Lernende mit viel Vorwissen   |

---

> [!NOTE]
> **Warum das für OER zentral ist:** Wer den Quelltext hat, hat alles. Es gibt keine proprietäre Datei, kein Layout, das beim Export verloren geht — der Markdown-Text *ist* das Material.

### Konzept 2 — Interaktion gehört zum Inhalt

> __Quizze, Animationen, Selbsttests sind keine Plugins — sie sind Teil der Auszeichnungssprache selbst.__

Im [Selbstlernkurs in Phase 0](https://liascript.github.io/course/?https://raw.githubusercontent.com/anja-schulz-dhs/LiaWorkshop_Anja-Anja/refs/heads/main/README.md#1) haben Sie bereits das MC-Quiz-Format ausprobiert. Im Quelltext sind das **wenige Zeilen Markdown** — keine Plugin-Installation, keine ID-Vergabe, keine Datenbank.

```markdown @embed.style(height: 600px; min-width: 100%; border: 1px black solid)
# Lehre lebt von Interaktion

__Quiz mit Erklärung__

Welches sind relevante Faktoren, um den Lernerfolg Ihrer Studierenden zu fördern?
- [[ ]]Studierende merken sich Inhalte aus Vorträgen besonders schlecht, besser für den Lernerfolg ist es, wenn sie Dinge tun können.
- [[X]]die Aktivierung des Vorwissens unterstützt Studierende bei der kognitiven Verarbeitung.
- [[X]]je nach Vorwissen benötigen Studierende unterschiedlich viel didaktische Unterstützung.
**************
Sehr gut, Sie haben einen Lernmythos richtig identifiziert!
**************

__Animationsstufen__

Klicken Sie sich durch:

{{1}} Erst kommt diese Zeile,
{{2}} dann diese,
{{3}} und schließlich diese.

---

> [!NOTE]
> **Vergleich zum LMS-Ansatz:** Ein Moodle-Quiz lebt *in* Moodle. Verlassen Sie das System, ist die Aufgabe weg. Ein LiaScript-Quiz lebt im Markdown-Text — und reist überall mit.

### Konzept 3 — Der Browser ist die Laufzeitumgebung

> __Was der Browser kann, kann LiaScript. Und der Browser kann heute erstaunlich viel.__

Sie lehren in einem Studiengang, in dem auch Programmierfähigkeiten wichtig sind bzw. sind selber programmieraffin? Auch Code lässt sich in LiaScript ausführen — im Browser, ohne Installation, ohne Server. Das ist kein LiaScript-Feature im engeren Sinn, sondern moderner Browser-Standard (WebAssembly, Pyodide). LiaScript bindet diese Fähigkeiten nur konsequent ein:

+ **Code ausführen** — Python, JavaScript, C++, R, SQL, ...
+ **Sprachausgabe** — Texte vorlesen lassen (Barrierearmut)
+ **Daten persistieren** — Lernstand im Browser speichern
+ **3D-Modelle, Simulationen, Notenschrift, Schaltkreise** — über Templates erweiterbar

```markdown @embed.style(height: 600px; min-width: 100%; border: 1px black solid)
# Der Browser als Plattform

__Sprachausgabe__ — einfach per Tag:

> {{|> Deutsch Female}}
> Willkommen zur Einführungsveranstaltung!

__Templates__ 

??[ear model](https://sketchfab.com/3d-models/familienschacht-freiberg-germany-7c7d30506c554385a4a4321366e2e601)
```

## Und was ist mit Moodle, OPAL, ILIAS?

Wie funktioniert das aber technisch? Ein LiaScript-Kurs als Dokument wird von einem **Player** im Browser ausgeführt. Der Player ist eine Art Interpreter, der den Markdown-Text liest und in eine interaktive Seite umsetzt. Das heißt:

1. **Es gibt keinen „LiaScript-Server"** — der Kurs läuft komplett im Browser, ohne Installation, ohne Server, ohne Internet (nach dem ersten Laden).
2. **Der Kurs ist eine einzelne Markdown-Datei** — keine Datenbank, kein proprietäres Format, keine versteckten Metadaten. Alles, was der Kurs ist, steht im Text.
3. **Der Interpreter ist Open Source** — jeder kann ihn herunterladen, anpassen, erweitern. Es gibt keine „Black Box", die den Kurs unzugänglich macht.

Das bedeutet, es ist für die Ausführung keine IT-Infrastruktur nötig.

> [!IMPORTANT]
> **LMS und LiaScript stehen nicht in Konkurrenz — sie arbeiten auf verschiedenen Ebenen.**

           {{0-1}}
**************************************

| Ebene                  | Verantwortlich für                                   | Typische Vertreter        |
| ---------------------- | ---------------------------------------------------- | ------------------------- |
| **Inhalt**             | Was wird vermittelt? Wie wird es dargestellt?        | **LiaScript**, H5P        |
| **Distribution / LMS** | Wer sieht was wann? Kursverwaltung, Noten, Zugriff   | Moodle, OPAL, ILIAS       |

**************************************

           {{1}}
**************************************

Konkret heißt das: Ein LiaScript-Kurs lässt sich **als SCORM- oder xAPI-Paket exportieren** und in jedes gängige LMS einspielen. Das LMS übernimmt dann Anmeldung, Tracking, Notenvergabe — der eigentliche *Inhalt* bleibt aber im offenen Markdown-Format erhalten und kann jederzeit aus dem LMS herausgelöst, angepasst und woanders wiederverwendet werden.

> **Das ist der entscheidende Unterschied zu „nativen" LMS-Inhalten:** Eine Moodle-Lektion ist *in* Moodle. Ein LiaScript-Kurs *läuft* in Moodle — aber wohnt nicht dort. Genau das macht ihn zur echten OER.

**************************************

## Zusammengefasst

> [!TIP]
> 1. **Format:** LiaScript ist erweitertes Markdown — ein offenes, textuelles Quellformat.
> 2. **Interaktion:** Quizze, Code, Animationen sind Teil der Sprache, nicht Plugins eines Systems.
> 3. **Plattform:** Der Browser führt aus — kein Server, keine Installation.
> 4. **LMS-Anschluss:** SCORM/xAPI-Export macht den Kurs LMS-kompatibel, ohne dass das LMS den Inhalt „besitzt".
>
> **Die OER-Pointe:** Wer den Quelltext hat, kann alle fünf V-Freiheiten umsetzen — *verwahren, verwenden, verarbeiten, vermischen, verbreiten*. Das gilt mit LiaScript für *interaktive* Materialien genauso wie für reinen Text.

In der nächsten Phase bauen Sie diesen Quelltext selbst — Schritt für Schritt.
