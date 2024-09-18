---
title: Dokumentation

abstract: |
    Die Arbeit mit Daten erfordert eine genaue Dokumentation der Arbeitsschritte und der Arbeitsorganisation. Diese Dokumentation umfasst in der Regel die *technische Projektdokumentation*, *Labor- und Arbeitsberichte* sowie *Projektberichte*. 
    
    Die **technische Projektdokumentation** dokumentiert die Organisation und Struktur eines Projekts. 
    
    **Labor- und Arbeitsberichte** dokumentieren den Ablauf und alle Ergebnisse eines Projekts. 
    
    Ein **Projektbericht** dokumentiert die Ausgangslage, die Methode, die Ergebnisse und die Schlussfolgerungen eines Projekts. Projektberichte greifen oft auf die technische Projektdokumentation und auf Laborberichte zurück.

    Dieses Kapitel beschreibt die Anforderungen und die Funktion der Projektdokumentation.

execute: 
  echo: false
---

## Technische Projektdokumentation

Die technische Projektdokumentation dokumentiert die Organisation und Struktur eines Projekts und enthält alle relevanten Information, um die Dateien in einem `git`-Repository richtig zu interpretieren und die Arbeitsschritte zu reproduzieren. 

Eine vollständige **Projektdokumentation** enthält die folgenden Teile.

- Projekthistorie 
- Entscheidungen und Massnahmen
- Projektmotivation bzw. Ausgangslage
- Repository-Organisation
- Technische Information zur Arbeit mit dem Projekt
- Externe Bibliotheken bzw. Abhängigkeiten.
- Vertraulichkeit und Verwendungsrechte

Die Versionierungsgeschichte wird von `git` automatisch erstellt. Die **Commit-Meldungen** dokumentieren die Massnahmen, welche in der zugehörenden Version umgesetzt wurden. 

### Entscheidungen und Massnahmen

Weil die Commit-Meldungen nicht viel Platz zu dokumentation bieten, werden *Entscheidungen* in der Regels als **Issues** und *Massnamen* als **Pull-Requests** einer `git`-Hosting-Plattform dokumentiert. Dabei gilt, dass *offene* Issues oder Pull-Requests noch nicht und *geschlossene* Issues und Pull-Requests vollständig im Projekt umgesetzt wurden. Commit-Meldungen müssen dann nur noch auf die zugehörigen *Issues* referenzieren.

### Projektübersicht

Per Konvention werden in der Datei `README.md` bzw. `README` die Ausgangslage und Motivation, technische Information sowie die Repository-Organisation dokumentiert. Diese Dokumentation ist notwendig, um mit dem Projekt arbeiten zu können. Zur technischen Information gehört alles benötigte, um mit den Daten oder dem Code arbeiten zu können. 

Strukturierte Daten müssen in der Projektübersicht dokumentiert werden. Die folgende Information über die Daten sollte angegeben werden:

- die Namen von Variablen
- die Datentypen der Variablen
- die Bedeutung der Variablen

Für Code ist die Programmiersprache, eine Anleitung, um den Code laufen zu lassen, sowie ein Beispielaufruf anzugeben. Dieser Teil der Dokumentation hilft beim Aufsetzen des Projekts in einer neuen Arbeitsumgebung.

### Externe Abhängigkeiten

In Datenprojekten werden oft externe Bibliotheken, Module oder Pakete verwendet, die separat installiert werden müssen. Diese Komponenten bezeichnet man als **externe Abhängigkeiten**, die ebenfalls dokumentieren werden müssen, damit alle externen Abhängigkeiten in einer neuen Arbeitsumgebung korrekt installiert werden können. Dieser Teil der Projektdokumentation benötigt den Namen der verwendeten Bibliothek sowie die erforderliche Versionsnummer. Für meisten modernen Programmiersprachen existieren sog. *Packetmanager*, welche die externen Abhängigkeiten in einer Datei dokumentieren und installieren können.

Die folgende Tabelle zeigt Paketmanager und die Datei für externe Abhängigkeiten in ausgewählten Programmiersprachen. Diese Liste ist nicht vollständig. Die Datein für externe Abhängigkeiten erfüllen die Dokumentation der externen Abhängigkeiten und können gleichzeitig für die Installation der externen Abhängigkeiten verwendet werden.

| Programmiersprache | Paketmanager | Datei für externe Abhängigkeiten |
| ------------------ | ------------ | ----- |
| Python             | pip          | `requirements.txt` |
| R                  | renv            | `renv.lock`, `renv/settings.json` |
| R                  | pak | `pkg.lock` |
| Julia              | Pkg | `Project.toml` |
| JavaScript | npm | `package.json` |
| Java | Maven | `pom.xml` |
| PHP | composer | `composer.json` |

### Vertraulichkeit, Verwendung und Urheberschaft

Per Konvention wird die **Vertraulichkeit** und **Verwendungsrechte** in der Datei `LICENCE.md` oder `LICENSE` dokumentiert. Dabei handelt es sich um ein rechtliches Dokument, das oft von einer Organisation oder Auftraggeber vorgegeben wird oder, wie im Fall von Open Source Lizenzen, durch einen Verband erstellt wurden. Die Lizenzdatei wird in aller Regel in einem Projekt nicht oder nur sehr selten geändert. 

::: {.callout-caution}
## Achtung
Fehlt eine Lizenzdatei, ist das Projekt nicht lizenzlos, sondern unterliegt dem gesetzlichen Urheberrecht am Wohnsitz der Projektbeteiligten. Damit ein Projekt lizenzlos veröffentlicht werden kann, muss dieses explizit in der Lizenzdatei festgehalten werden. Ein Beispiel für eine solchen Vermerk ist die sog. [MIT Lizenz](https://opensource.org/license/mit/).
:::


::: {.callout-caution}
## Achtung
Die Verwendungsrechte *externer Abhängigkeiten* können die Verwendung des eigenen Projekts beeinflussen. Möglicherweise sind einzelne Module mit den Projektanforderungen nicht vereinbar und dürfen in diesen Fällen auch nicht im Projekt verwendet werden. Es ist deshlab wichtig, die Lizenzbedingungen **aller** externen Abhängigkeiten auf ihre rechtliche Kompatibilität mit dem eigenen Projekt zu prüfen.
::: 

`git`-Hosting-Plattformen bieten verschiedene Lizenzen beim Erstellen eines neuen Projekts an.


::: {.callout-caution}
## Achtung
Projekte, die mit Bezug auf die Daten und/oder die Auswertungsalgorithmen als *vertraulich* gelten, dürfen nicht in *öffentlichen* Projektrepositories verwaltet werden. In diesem Fall muss ein *privates* Repository verwendet werden. Unter Umständen ist eine Verwendung einer öffentlichen Plattform nicht möglich. In diesem Fall muss eine eigene `git`-Hosting-Plattform genutzt werden.
:::

Neben der Verwendung und Vertraulichkeit ist auch die **Urheberschaft** zu dokumentieren. Die Urheberschaft ist die Liste der Personen, die an einem Projekt mitgearbeitet haben. Traditionell wurde die Urheberschaft, in der Regel, in der Datei `AUTHORS.md` oder `AUTHORS` dokumentiert. 


::: {.callout-tip}
`git`-Hosting-Plattformen erstellen inzwischen die Autorenliste automatisch aus den Commits. Zusätzlich wird auch der Umfang der Beiträge dokumentiert.
:::

## Labor- und Arbeitsbericht

Ein Laborbericht dokumentiert den Ablauf und alle Ergebnisse eines Experiments oder einer Untersuchung. Ein Laborbericht ist eine *technische Dokumentation* einer Untersuchung oder eines Experiments. Diese Dokumentation ist der Beleg für die sachgemässe Durchführung einer Untersuchung. Bei Untersuchungen, die mehr als eine Arbeitssitzung oder -Schicht benötigen, sollten Laborberichte pro Sitzung bzw. Schicht erstellt werden.

::: {.callout-warning}
Laborberichte sind Teil von Complience-Anforderungen und werden oft von Auftraggebern oder Behörden verlangt. In diesen Anforderungen werden die zwingend zu dokumentierenden Teile festgelegt. Unterliegen bestimmte Untersuchungen einer Complience-Anforderung, dann müssen diese Anforderungen eingehalten werden, selbst wenn diese nicht explizit gefordert wurde. Stellt sich später heraus, dass ein vorliegender Laborbericht unvollständig ist oder falsche Angaben zur Durchführung enthält, dann kann dies unter Umständen als Urkundenfälschung gewertet werden.
::: 

Laborberichte sollten am Besten während oder unmittelbar nach einer Untersuchung erstellt werden. Werden regelmässig Laborberichte erstellt, bietet sich die Verwendung einer Versionierung mit `git` an. 

Bei der Verwendung von Laborberichten wird angenommen, dass undokumentierte Materialien nicht verwendet wurden und nicht dokumentierte Arbeitsschritte oder Ereignisse nicht stattgefunden haben. Ein fehlender oder unvollständiger Laborbericht entspricht einer nicht ordnungsgemäss durchgeführten Untersuchung.

Ein Laborbericht besteht aus den folgenden Teilen.

- Titel
- Beteiligte Untersuchende
- Datum, Uhrzeit und Ort
- Fragestellung bzw. Auftrag
- Materialliste
- Detaillierter Versuchsaufbau
- Versuchsdurchführung bzw. Ablauf
- Ergebnisse
- Fehlerdiskussion
- Beobachtungen
- Besondere Ereignisse

### Materialliste

Die Materialliste umfasst alle Materialien, die für die Durchführung des Experiments benötigt werden. Grundsätzlich müssen alle Materialien und Geräte, die für die Durchführung einer Untersuchtung verwendet werden, in der Materialliste aufgeführt werden müssen. Zu den Materialien gehören zum Beispiel:

- Chemikalien und Reagenzien
- Proben
- Behälter, Gefässe und Verbindungen
- Messgeräte
- Kabel und Stecker
- Werkzeuge
- Verbrauchsmaterialien
- Schutzkleidung
- Entsorgungsmaterialien

Falls eine Studie oder ein Experiment nicht in einer kontrollierten Laborumgebung durchgeführt wird, müssen auch die **Umweltbedingungen** am Untersuchungsort dokumentiert werden.

### Versuchsaufbau

Der Versuchsaufbau beschreibt die Anordnung der Materialien und Geräte bei der Durchführung eines Experiments. Dieser Abschnitt beschreibt im Detail den Aufbau eines Versuchs oder einer Untersuchung, so dass diese später genau gleich wiederholt werden kann. Für den Versuchsaufbau werden zusätzlich Skizzen und Schaltpläne angegeben. Falls der Versuchsaufbau spezielle Software für die Durchführung benötigt, sind alle Komponenten und Einstellungen ebenfalls im Versuchsaufbau zu dokumentieren. 

::: {.callout-note}
Die Software für die Auswertung ist *kein* Teil des Versuchsaufbaus.
:::

Bei wiederholten Durchführungen mit dem gleichen Versuchsaufbau kann der Versuchsaufbau in einem separaten Dokument oder in einem separaten Abschnitt dokumentiert werden. Dieses Dokument ist dann für alle Versuchsdurchführungen mit dem gleichen Versuchsaufbau gültig und muss in *allen zugehörigen Laborberichten* referenziert werden.

### Durchführung und Ablauf

Der Abschnitt Durchführung beschreibt die genaue Vorgehensweise einer Untersuchung oder eines Experiments. Dabei werden alle ***durchgeführten*** Arbeitsschritte in *chronologischer* Reihenfolge festgehalten. Die Beschreibung der Durchführung muss so genau sein, dass die Untersuchung oder das Experiment später genau gleich wiederholt werden kann.

Wenn besondere Vorsichtsmassnahmen bei der Durchführung notwendig sind, müssen diese ebenfalls im Abschnitt Durchführung dokumentiert werden.

Die **Entsorgung** von Nebenprodukten und Abfällen ist Teil der Versuchsdurchführung. Die Entsorgung von Nebenprodukten und Abfällen wird oft in einem separaten Abschnitt dokumentiert.

Bei manchen Untersuchung ist ein besonderer Rückbau des Versuchsaufbaus notwendig. Der Rückbau des Versuchsaufbaus wird ebenfalls in der Versuchsdurchführung dokumentiert.

### Ergebnisse

Alle gemessenen Ergebnisse eines Experiments oder einer Untersuchung müssen im Abschnitt *Ergebnisse* dokumentiert werden. Das gilt auch für Messwerte, die später nicht für die Auswertung verwendet werden. Die Ergebnisse werden in Tabellen *und* Diagrammen dargestellt. Die Tabellen und Diagramme müssen mit einer Nummer versehen werden und eine aussagekräftige Beschriftung haben. Die Tabellen mit den Messwerten sind immer verpflichtend. Diagramme sind *optional*.


::: {.callout-caution}
## Achtung
Die Ergebnisse müssen *vollständig* dokumentiert werden. Das bedeutet, dass alle Messwerte, die für die Auswertung nicht verwendet werden, trotzdem dokumentiert werden müssen.
:::

Weil die Messwerte später ausgewertet werden sollen, können die Tabellen in einer separaten Datei gespeichert werden. Diese Datei wird dann im Abschnitt Ergebnisse als *Anhang* referenziert. Sollte eine Untersuchung mehrere Tabellen erzeugt haben, dann sollten diese als eigenständige Anhänge geführt werden. 

### Fehlerdiskussion

Die Fehlerdiskussion eines Projektberichts umfasst die bekannten Fehlerquellen und Fehlerabschätzungen einer Studie. Dieser Teil dient zur Bestimmung der Messgüte der Einschätzung der präsentierten Ergebnisse.

In diesem Teil müssen auch methodische Fehler berichtet werden, falls diese die ordnungsgemässe Messung oder Auswertung beeinflussen. 

Messausfälle oder nicht durchgeführte Messungen sind nicht Teil der Fehlerdiskussion, sondern fallen in die Rubrik *besondere Ereignisse* und müssen dort berichtet werden. 

### Besondere Ereignisse

In einem Laborbericht werden grundsätzlich alle besonderen Ereignisse dokumentiert. Besondere Ereignisse sind Ereignisse, die nicht zum normalen Ablauf gehören oder für das Experiment nicht zu erwarten waren. Beispiele für besondere Ereignisse sind:

- Ungewöhnliche Messwerte und Messausfälle
- Ungewöhnliche Geräusche, Gerüche oder Verfärbungen
- Verzögerungen und Unterbrechungen
- Ausfall von Geräten
- Warnmeldungen
- Defekte oder fehlerhafte Geräte
- Unfälle und Verletzungen
- Unkontrolliertes oder ungeplantes Austreten von Flüssigkeiten oder Gasen

Falls keine besonderen Ereignisse aufgetreten sind, können diese Teile weggelassen werden.

### Beobachtungen und Notizen

Laborberichte sind eine wichtige Quelle für Innovation und Erkenntnisse. Deshalb sollten Beobachtungen, Erfahrungen und andere Notizen in Laborberichten festgehalten werden. Dadurch wird sichergestellt, dass dieser Teil der Dokumentation nicht von der Untersuchtung getrennt und so dekontextualisiert wird. 

## Projektbericht

Ein Projektbericht dokumentiert die Ausgangslage, die Methode, die Ergebnisse und die Schlussfolgerungen eines Projekts. 

Ein Projektbericht besteht ***immer*** aus den folgenden Teilen.

- Titel
- Autor:innen
- Zusammenfassung (Abstract)
- Einleitung und Hintergrund
- Forschungsfrage/Arbeitsauftrag
- Methode
- Ergebnisse 
- Interpretation (Diskussion)
- Ausblick
- Quellenverzeichnis

Bei längeren Projektberichten muss zusätzlich ein Inhaltsverzeichnis, ein Abbildungsverzeichnis, ein Tabellenverzeichnis und ein Abkürzungsverzeichnis sowie eine Managementzusammenfassung erstellt.

### Einleitung und Hintergrund

Die Einleitung legt den Kontext des Projekts fest. Dazu gehört die übergeordnete Problemstellung und die bekannten Fakten zum Thema. Die Problemstellung sollte so formuliert sein, dass auch interessierte Personen, die nicht mit dem Thema vertraut sind, die Ausgangslage verstehen können. Die Aufstellung der bekannten Fakten ist eine Zusammenfassung der Literatur zu dieser Problemstellung. Es kommt nicht selten vor, dass Querbezüge zu anderen Themen oder Problemstellungen hergestellt werden müssen. Auch diese Literatur muss in der Einleitung zusammengefasst werden. 

Die Literatur sollte so zusammengefasst werden, dass für die projektrelevante Aspekte, die in der Literatur identifiziert wurden, ein Absatz im Abschnitt gewidmet wird. Dabei müssen die entsprechenden Quellen referenziert werden. Falls mehrere Quellen die gleiche oder sehr ähnlich Aussagen treffen, dann können diese im gleichen Absatz zusammengefasst und gemeinsam referenziert werden.

### Forschungsfrage oder Arbeitsauftrag

Der Abschnitt Forschungsfrage oder Arbeitsauftrag legt die konkrete Motivation des Projekts fest. Diese sollte durch den Kontext der bekannten Fakten und der Problemstellung in der Einleitung sachlich begründet sein. 

Als Frage formuliert liefert der Abschnitt Ausblick die Antwort auf diese Frage. Dadurch entsteht eine rhetorische Klammer im Projektbericht. Gleichzeitigt hiflt die Formulierung der Fragestellung bei der kontinuierlichen Überprüfung, ob die durchgeführten Schritte im Projekt auch zur Beantwortung der Fragestellung beitragen. Deshalb sollten auch Arbeitsaufträge, die nicht als Frage präsentiert werden, intern als Frages umformuliert werden. 

### Methode

Die Methode beschreibt das Vorgehen bei der Erhebung und Auswertung von Daten. Die Beschreibung muss eine Wiederholung oder das systematische Nachvollziehen der Untersuchung ermöglichen. In diesem Abschnitt sind alle Arbeitsschritte zu dokumentieren, die in den Abschnitten Ergebnisse und Interpretation zu den präsentierten Ergebnissen führen. 

Die Methode umfasst nur die systematische Vorgehensweise, aber keine technische Dokumentation der Auswertung. Hierzu sollte auf die technische Projektdokumentation verwiesen werden.

### Ergebnisse

Der Abschnitt Ergebnisse fasst alle erhobenen Messungen zusammen. Dabei werden die Messwerte in Tabellen und Diagrammen dargestellt. Alle in diesem Abschnitt präsentierten Daten sollten sich direkt aus Laborberichten ableiten lassen.

Im Abschnitt Ergebnisse werden selten die gemessenen Rohdaten als Tabelle präsentiert. Sollten die Rohdaten für die Interpretation bedeutsam sein, dann sollten diese Daten in einem Anhang getrennt präsentiert werden.

Dieser Abschnitt muss alle im Abschnitt *Interpretation* bzw. *Diskussion* verwendeten Daten enthalten. Für *jede Aussage* im Abschnitt Interpretation muss ein Bezug zu den Ergebnissen möglich sein. 

Dieser Abschnitt enthält für empirischen Studien normalerweise *keine Referenzen* auf externe Quellen.

### Interpretation

Die Interpretation umfasst die *Bewertung* der Ergebnisse. Dabei werden die Ergebnisse mit den Erwartungen aus der Einleitung verglichen. In diesem Abschnitt werden die Ergebnisse in den in der Einleitung hergestellten Kontext gestellt und die Schlussfolgerungen aus der Auswertung gezogen. In diesem Abschnitt werden die Argumente für die Beantwortung der Forschungsfrage bzw. des Arbeitsauftrags vorbereitet.

Die Interpretation enthält *keine* neuen Daten, sondern nur eine *Bewertung* der Ergebnisse. Die Bewertung der Ergebnisse muss *immer* mit den Erwartungen aus der Einleitung und Fragestellung verglichen werden.

### Ausblick

Der Ausblick beantwortet die Forschungsfrage bzw. den Arbeitsauftrag. Dabei werden die Ergebnisse der Untersuchung zusammengefasst und die Schlussfolgerungen daraus gezogen. Häufig werden die Schlussfolgerungen als *Empfehlungen für die Praxis* formuliert.

Falls in einem Projekt unerwartete Ergebnisse auftraten oder Phänomene beobachtet wurde, die nicht durch as Projekt erklärt werden können, dann sollten Fragen für die weitere Forschung formuliert werden. Diese Fragen sollten als Forschungsfragen analog zum Abschnitt Forschungsfrage formuliert werden. 


::: {.callout-tip}
Falls über ein Teilprojekt berichtet wird, dann gelten die nächsten *geplanten* Projektfragen *nicht* als Fragen für die weitere Forschung.
:::

### Zitieren und Quellenverzeichnis

Das Zitieren von Quellen ist ein wichtiger Teil der wissenschaftlichen Arbeit. Das Zitieren von Quellen dient dazu, die Herkunft von Ideen, Aussagen und Ergebnissen zu dokumentieren. Das Referenzieren externer Quellen ist verpflichtend. Im Bericht wird auf die Quellen in einer Kurzform verweisen. Die vollständigen Angaben aller Quellen werden im Quellenverzeichnis aufgeführt.

Wie Quellen richtig referenziert werden, ist in sog. Zitierstandards festgelegt. Wichtige Zitierstandars sind der APA Styleguide [@american_psychological_association_publication_2020], der Chicago Styleguide [@the_university_of_chicago_press_editorial_staff_chicago_2017], der IEEE Styleguide [@ieee_ieee_2018] oder der ACM Styleguide [@rodkin_acm_2023]. In einem Projektbericht wird nur ein Zitierstandard verwendet. Es ist nicht vorgesehen, Zitierstandards zu mischen.

Eine wörtliche Übernahme einer anderen Quelle wird als Zitat bezeichnet. Zitate sollten sehr sparsam in Berichten verwendet werden. Zitate sind oft nur dann notwendig, wenn die wörtliche Übernahme einer Aussage oder eines Ergebnisses für die Argumentation erforderlich ist. 

Werden Ideen, Aussagen oder Ergebnisse aus einer externen Quelle verwendet, dann ist das eine Paraphrase und erfordert wie ein Zitat eine Referenz der Quelle. Bei Paraphrasen ist die Angabe der Seitenzahl nur dann notwendig, wenn die referenzierte Idee sich nicht direkt aus der Quelle ergibt. Das ist zum Beispiel der Fall, wenn die Quelle eine Monographie mit mehreren Studien ist und nur eine bestimmte Studie referenziert wird.


::: {.callout-caution}
## Achtung
Werden externe Quellen verwendet und *nicht referenziert*, dann handelt es sich um ein Plagiat. Plagiate sind ein schwerer Verstoss gegen die wissenschaftliche Integrität und das Urheberrecht. Bei Zertifizierungen sind Plagiate ausserdem ein Betrug. Das gilt auch für Paraphrasen ohne Referenz. 
:::

### Managementzusammenfassung

Eine Managementzusammenfassung ist eine Kurzfassung eines Projektberichts, die sich an die Entscheidungsträger richtet. Sie ist deutlich kürzer als die Zusammenfassung und enthält nur die wichtigste Information des Projektberichts. In der Regel ist die Managementzusammenfassung nicht länger als eine Seite und ist Stichpunktartig formuliert.

Eine gute Managementzusammenfassung kann direkt in einer Präsentation verwendet werden. Als Richtlinie für eine Managementzusammenfassung sind sieben Punkte. Diese Punkte sollten die folgenden Fragen beantworten.

- Was ist das Problem?
- Wie wurde gemessen? 
- Was sind die wichtigsten Ergebnisse? 
- Welche Schlussfolgerungen können gezogen werden?
- Welche Massnahmen werden empfohlen? (optional)

