---
# bibliography: references.bib
  
execute: 
  echo: false
---

# Daten sammeln {#sec-chapter-daten-sammeln}

Bevor Daten analysiert werden können, müssen sie zuerst gesammelt werden. Je nach dem Ziel und Quelle können Daten *unstrukturiert*, *semi-strukturiert* und *strukturiert* gesammelt werden. Das Ergebnis ist immer ein Datensatz, welcher Werte für die Datenanalyse bereitstellt. Je nach Vorgehensweise kommen unterschiedliche Werkzeuge zum automatisierten und manuellen Datensammeln in Frage.

Das Ziel des Datensammelns ist das Erstellen von *Datensätzen*. 

::: {#def-datensätze}

Ein **Datensatz** umfasst zusammengehörende Werte. 

:::

Beim Sammeln von Daten werden *Beobachtungen* erfasst und dokumentiert. Dabei entspricht ein Datensatz immer einer Beobachtung. Über den zugehörigen Datensatz sollte eine Beobachtung zu einem späteren Zeitpunkt nachvollziehbar sein. Das ist allerdings nur mithilfe der erfassten Daten möglich. 

Durch nicht erfasste Daten geht Information verloren. Dieser Informationsverlust ist grundsätzlich *unvermeidbar*, weil nicht jeder Aspekt einer Beobachtung in Daten kodiert oder erfasst wird. Manche Daten sind für die spätere Analyse von besonderer Bedeutung, weil ohne sie eine Auswertung unmöglich ist. Deshalb müssen die relevanten Daten ***vor*** der Datenerhebung bestimmt werden.

## Das Datenschema

Welche Daten in einem Datensatz erfasst wurden bzw. erfasst werden sollen,  werden in einem **Datenschema** festgehalten. Das Datenschema hat zwei Funktionen.

1. Es legt fest, welche Daten für einen Datensatz erhoben werden müssen. In dieser Funktion ist das Datenschema eine grobe Anleitung welche Daten gesammelt werden sollen.
2. Es dokumentiert, welche Daten in einem Datenssatz vorliegen. Ein Datenschema hilft so Analysten, die Daten richtig auszuwerten und zu interpretieren.

Ein Datenschema legt Felder für die Ablage der beobachteten Daten fest.

Jedes Datenfeld erhält immer einen eindeutigen **Namen** für ein Datenfeld. Über den Namen können die im Datenfeld erfassten Daten zugegriffen werden. Die Namen von Datenfeldern dienen der einfacheren Handhabung bei der digitalen Auswertung. Deshalb sollten diese Namen möglichst einfach und gleichzeitig die Daten etwas beschreiben. Damit beim Auswerten weniger Fehler passieren, sollten Namen nur die Zeichen `a-z`, `0-9` und `_` enthalten und mit einem Buchstaben beginnen.

Zusätzlich kann ein Datenfeld einen **Wertebereich** haben. Ein Wertebereich legt die zulässigen Werte für ein Datenfeld fest. Für die automatisierte Auswertung kann es hilfreich sein, auch das **Skalenniveau** (s. [@sec-skalenniveaus]) des Wertebereichs zu dokumentieren.

Falls die Daten eine **Masseinheit** haben, muss diese auch dokumentiert werden.

Es ist üblich, für jedes Datenfeld eine **Kurzbeschreibung** anzugeben. Diese Beschreibung gibt zusätzliche Hinweise über die erfassten Werte. Die Beschreibung ist rein *informativ* und richtet sich an Menschen, die Daten für das Schema erheben oder diese Daten auswerten. 

Grundsätzlich können alle Datenfelder frei bestimmt werden. Einige Datenfelder sind für fast jede Studie gegeben. Zu diesen Datenfelder gehören beispielsweise der *Zeitpunkt der Beobachtung*, der *Ort der Beobachtung*, die *beobachtende Person* und die *Dauer der Beobachtung*. Bei der technischen Datenerfassung können weitere Felder durch die verwendeten Werkzeuge automatisch bereitgestellt werden. Deshalb sollten die technischen Möglichkeiten vor einer Datenerhebung geprüft werden, um das mehrfache abfragen der gleichen Daten zu vermeiden.

## Arten von Daten

Beim Daten sammeln werden drei Arten von Daten unterschieden: 

- Unstrukturierte Daten
- Strukturierte Daten
- Semi-strukturierte Daten

### Unstrukturierte Daten

::: {#def-unstrukturierte-daten}

**Unstrukturierte Daten** haben keinen festgelegten Wertebereich.

:::

Typische unstrukturierte Daten sind Notizen, Transkripte gespochener Sprache oder Videos. Unstrukturierte Daten können Werte von Interesse enthalten, auf die jedoch nicht direkt zugegriffen werden kann.

Unstrukturierte Daten haben den Vorteil, dass sie *Ergebnisoffen* ein. Dadurch sind unstrukturierte Daten offen für neue und unvorgesehene Information. Entsprechend werden Techniken, die unstrukturierte Daten erheben auch als ***offene*** Erhebungstechniken bezeichnet. 

Diese Offenheit hat ihren Preis, denn unstrukturierte Daten sind anfällig gegenüber Rauschen und Equivokation. Ausserdem können einzelne Werte nicht direkt aus unstrukturierte Daten abgelesen werden, sondern müssen (oft umständlich) aus den Daten extrahiert werden. 

::: {.callout-note}

Unstrukturierte Daten erfordern immer zusätzliche Arbeitsschritte, bevor mit den in ihnen vorhandenen Daten gearbeitet werden kann. Diese Arbeitsschritte zusammenfassend werden **Kodieren** (engl. **coding**) genannt. Das Kodieren unstrukturierter Daten führt einheitliche Markierungen, die sog. *Annotationen*, ein, die eine Struktur über die Daten legen.
:::

Ohne vorbereitende Kodierung lassen sich unstrukturierte Daten kaum systematisch analysieren. Sehr häufig handelt es sich bei unstrukturierten Daten um Texte. Im [Kapitel @sec-chapter-zeichenketten] werden einfache Techniken zum Verarbeiten von unstrukturierten Daten beschrieben.

### Strukturierte Daten

::: {#def-strukturierte-daten}
**Strukturierte Daten** haben einen festen Wertebereich. 
::: 

Weil strukturierte Daten einen festen Wertebereich haben, ist sichergestellt, dass nur Werte innerhalb dieses *abgeschlossenen* Bereichs gültig sind. Deshalb werden Techniken, mit denen strukturierte Daten erhoben gelten auch als ***geschlossene*** Erhebungstechniken.

Strukturierte Daten basieren immer auf einer festen Wertebereich, die Information kodiert. In dieser Struktur werden die Daten nach ihrer Bedeutung und ihren zulässigen Wertebereichen organisiert. Die feste Struktur macht strukturierte Daten innerhalb der Struktur weniger anfällig gegenüber Rauschen als unstrukturierte Daten. 

Weil strukturierte Daten eine Struktur zur Informationskodierung vorgeben, lassen sich nur Informationen über diese Struktur kodieren. Das führt zu Equivokation, weil nur die Teile der Information kodiert werden können, die in den Wertebereichen zulässig sind. 

Tabellen sind typische strukturierte Daten, die in Spalten und Zeilen organisiert sind.

Strukturierte Daten sind nicht auf Tabellen beschränkt. 

```{.YAML #lst-structured-yaml lst-cap="Strukturierte Daten im YAML-Format"}
hamster: 
- name: Fred
  gewicht: 175
  zeit: 2023-04-11T10:20:30Z
- name: Frida
  gewicht: 160
  zeit: 2023-04-12T09:10:11Z
```

### Semi-strukturierte Daten

Neben diesen zwei Arten existieren noch sog. semi-strukturierte Daten. 
Semistrukturierte Daten folgen einer logischen Struktur, die allerdings nicht durchgehend strickt eingehalten wird.

::: {#def-semi-strukturierte-daten}

**Semi-strukturierte Daten** sind *unstrukturierte Daten*, die Markierungen für Werte beinhalten. 

:::

Semi-strukturierte Daten werden oft für das Einbetten  strukturierter Daten in unstrukturierte Datenfelder verwendet. 

Ein typisches Beispiel für semistrukturierte Daten sind Social-Media-Meldungen mit Hashtags und `@`-Nennungen. Mit dem Hash-Symbol (`#`) werden Themen und Inhalte hervorgehoben und mit dem `@`-Symbol werden Nutzende markiert.  Durch die beiden Symbole wird eigendlich unstrukturierten Daten eine zusätzliche Struktur gegeben, auf welche zugegriffen werden kann. Eine Social-Media-Meldung kann keine, ein oder mehrere Hashtags und keine, eine oder mehrere Nennungen enthalten. 

``` {#lst-zhaw-tweet lst-cap="Tweet mit Hashtag [@zhaw_zhaw_2023]"}
Das neue Laborgebäude auf dem ZHAW-Campus Reidbach 
in #Wädenswil wurde gestern eingeweiht. Genutzt wird der
Neubau vom Institut für Lebensmittel- und Getränkeinnovation,
wo unter einem Dach die gesamte Wertschöpfungskette von 
Lebensmitteln erforscht wird. 
https://zhaw.ch/de/ueber-uns/aktuell/news/
detailansicht-news/event-news/
lebensmittelforschung-unter-einem-dach-vereint/
```

Ein anderes Beispiel finden sich regelmässig in Bankmiteilungen im Feld "Verwendungszweck". In diesem Feld werden oft zusätzliche Daten für die Kommunikation zwischen den Beteiligten einer Transaktion hinterlegt. @lst-semistructured zeigt semistrukturierte Daten im Verwendungszweck von Banktransaktionen, diese können für eine Analyse verwendet werden.  

``` {#lst-semistructured lst-cap="Semistrukturierte Daten"}
1   PV2332 PG386.5 SV375.26 
2   PG374.23
3   Ref: 106030763221202, Knr: 783924
```

In diesem Beispiel sind einmal drei Werte, einmal ein Wert und einmal zwei Werte in einem Eintrag vorhanden. Dabei kommt die Buchstabenfolge `PG` einmal als zweiter Wert und einmal alleinstehend vor. Eine Behandlung als Tabelle dieser Werte ist wahrscheinlich nicht zielführend. 

Die Buchstabenfolgen `PV`, `PG` und `SV` sowie `Ref:` und `Knr:` erfüllen den gleichen Zweck, wie Symbole `#` und `@` in Social-Media-Meldungen. Diese Markierungen sind *Codes*, die wichtige Daten hervorheben und relativ leicht identifizieren lassen. Die Codes nehmen das Kodieren unstrukturierter Daten vorweg.  

Solche Codes sind *transaktionsspezifisch*, so dass nicht alle Codes vorkommen müssen und bestimmte Codes nur bei bestimmten Transaktionen vorkommen oder die gleichen Codes in unterschiedlichen Transaktionen andere Bedeutungen haben. Oft folgen diese Codes einem eigenen Schema. 

## Daten erheben

Die eigentliche Datensammlung kann manuell, technisch unterstützt oder automatisch erfolgen. Bei der *manuellen Datenerhebung* werden alle Daten von einer Person erfasst und festgehalten. Bei der *technisch-unterstützten Datenerhebung* helfen spezielle Erhebungswerkzeuge, die Datenerhebung zu vereinfachen, indem sie Werte überprüft werden oder automatisch erfasst werden. Bei der *automatischen Datenerhebung* werden Daten durch *Sensoren* erfasst und gespeichert.

### Manuelle Datenerhebung

In der Laborarbeit ist die Erfassung von Messwerten in Tabellen oder Listen üblich. Dabei werden die Werte von Hand direkt in eine Tabelle oder Liste eingetragen. So erfasste Tabellen oder Listen sind *strukturierte Daten*. Beim Eintragen der Daten muss darauf geachtet werden, dass die Werte an der richtigen Stelle eingetragen werden, weil solche Fehler oft unerkannt bleiben und eine nachträgliche Korrektur oft nicht möglich ist.

Die einfachste Form der manuellen Datenerfassung sind *Notizen*. Notizen sind persönliche Aufzeichnungen über die eigene Arbeit bzw. über Beobachtungen bei der Arbeit. Diese Daten sind entweder *unstrukturiert* oder *semi-strukturiert*. Sie erlauben eine grosse Flexibilität falls die Daten nicht vorstrukturiert werden können oder die Struktur weitgehend unbekannt ist. Notizen lassen sich schwer *objektivisieren*, weil sie immer einen subjektiven Anteil der Person haben, welche die Notiz verfasst hat.

::: {.callout-tip}
## Praxis
Es ist eine gute Idee, Messwerte in Tabellen zu erfassen und zusätzliche Notizen zu machen. Aus beiden ergeben sich Laborberichte, die wiederum zu Labortagebüchern wachsen. In der wissenschaftlichen Praxis sind die strukturierten Daten zwar das Hauptergebnis einer Untersuchung, aus den Notizen ergeben sich jedoch oft neue Einsichten, die sich nicht aus den strukturierten Daten herauslesen lassen. 
::: 

Neben Notizen sind *Transskripte* ein wichtiges Werkzeug der manuellen Datenerfassung. Transskripte sind eine Verschriftlichung einer anderen Aufzeichnung. Oft sind das Tonaufzeichnungen von Gesprächen oder Videoaufzeichnugen eines Experiments. Diese Aufzeichnungen liefern immer *unstrukturierte Daten*. Die ursprüngliche Aufzeichnung ist dabei *meistens* eine Primärquelle für die Daten. Das Transskript ist eine *abgeleitete Sekundärquelle* der Primärquelle. Weil beim Transskribieren die Primärquelle *neu kodiert* wird, muss beim Transskribieren besonders sorgfältig gearbeitet werden, um die usprünglichen Daten nicht zu sehr zu verfälschen. 

Inzwischen gibt es brauchbare Werkzeuge zur Transskription von Mediendateien. Diese automatisch erstellten Transkripte müssen aber immer nachkontrolliert werden. Nur so wird das Risiko reduziert, dass sich die Bedeutung der Daten durch Transskriptionsfehler ändert.

### Technisch-unterstützte Datenerhebung

Bei der technisch-unterstützten Datenerhebung soll das manuelle Datensammeln durch technische Werkzeuge vereinfacht werden, indem bestimmte Daten automatisch erfasst werden. Ein wichtiges Instrument für die technisch-unterstützte Datenerhebung sind *Formulare*. Formulare sind strukturierte Dokumente zur systematischen und wiederholten manuellen Eingabe von Daten durch Menschen.

Im Gegensatz zu Papierformularen können digitale Formulare die Eingaben überprüfen und bieten unterschiedliche Eingabeformate. Digitale Formulare können auch automatisch Daten erfassen, die nicht direkt eingegeben werden, wie beispielsweise den Zeitpunkt der Eingabe. Die populärste Art der digitalen Formulare sind inzwischen online Formulare, weil sie die grösste Flexibilität bei einer vergleichsweise niedrigen Nutzungsschwelle bieten.

Es lassen sich zwei Arten von Diensten für online Formulare unterschieden: 

1. Formulardienste, wie z.B. MS-Forms [@microsoft_office_2023] oder Google Forms [@google_google_2023].
2. Umfrage- bzw. Survey-Dienste, wie z.B. Survey Monkey oder Lime Survey.

Der wesentliche Unterschied zwischen diesen Diensten sind zusätzliche Funktionen zur Datenerhebung. Survey-Dienste bieten zusätzliche Funktionen, wie die Anonymisierung der Daten, zusätzliche Daten über die Ausführung, Fragebogendokumentation oder die Unterstützung von wiederholten Befragungen.

Alle Formulare erlauben die Eingabe von Daten mit *offenen* und *geschlossenen* Wertebereich sowie das Auslesen der Daten in tabellarischer Form. Für jedes ausgefüllte Formular wird dazu eine Zeile erstellt, wobei die Eingabefelder jeweils als eine Spalte abgebildet werden.

::: {#def-fragebogen-item}
Eine Eingabemöglichkeit eines Formulars wird als **Fragebogen-Item** oder schlicht als **Item** bezeichnet.
:::

Items mit offenen Wertebereich sind Langantworten und Dateien. Alle anderen Eingaben haben einen geschlossenen Wertebereich. Die sog. Kurzantworten erscheinen als offene Eingabefelder. Ihr Wertebereich kann aber durch Validierungsregeln eingeschränkt werden.

Bei den Items mit geschlossenen Wertebereich kann zwischen einfachen und mehrfachen Eingaben unterschieden werden. Bei einfachen Eingaben kann nur eine Antwortmöglichkeit ausgewählt werden (sog. Single-Choice). Der Wertebereich dieser Items wird über die Antwortmöglichkeiten festgelegt. 

*Skalen* sind **Single-Choice-Items** für einen *ordinalen Wertebereich*. Oft werden die Antwortmöglichkeiten mit einem Rang versehen. 

Ein Spezialfall der Skalen ist die **Likert-Skala**, bei der eine lineare Skala mit einer Bewertung zwischen zwei Extremwerten versehen wird. Die Extrem-Pole sollten möglichst weit auseinander gewählt werden. Z.B. *"trifft absolut nicht zu"* und *"trifft voll und ganz zu"* und ***nicht*** *"trifft nicht zu"* und *"trifft zu"*. Obwohl Likert-Skalen *subjketive Ansichten* messen, wird der Wertebereich meist als *intervallskalierter Wertebereich* behandlet. 

Bei mehrfachen Eingaben können mehrere Antwortmöglichkeiten ausgewählt werden. Mehrfache Eingaben werden auch als **Multiple-Choice-Items** bezeichnet. Im Gegensatz zu Single-Choice-Items haben Multiple-Choice-Items *immer* einen *binären Wertebereich*. Das bedeutet, dass jede Antwortmöglichkeit nur zwei Werte annehmen kann: *ausgewählt* oder *nicht ausgewählt*. Intern werden Multiple-Choice-Items als separate Items gespeichert und auch so tabellarisch dargestellt. Ein Multiple-Choice-Item hat deshalb immer eine *Ja/Nein*-Frage als Grundlage, wobei die fehlende Auswahl durch einen nicht vorhandenen Eintrag repräsentiert wird.

Die sog. **Grid-Items** oder **Fragebatterien** sind Items, bei denen mehrere Fragen mit der gleichen Antwortmöglichkeiten gestellt werden. Entsprechend haben diese Items den *gleichen Wertebereich*. Zu den Grid-Items sind oft als Skalen oder als Multiple-Choice-Items organisiert. Diese Items werden oft als Matrix dargestellt, wobei die Fragen als Zeilen und die Antwortmöglichkeiten als Spalten dargestellt werden. Intern werden die einzelnen Fragen von Grid-Items als separate Items gespeichert und werden auch tabellarisch so abgebildet. Dabei gelten die gleichen Regeln wie bei einfachen Single-Choice- und Multiple-Choice-Items. 

Eine Fragebatterie aus Likert-Skalen wird **Semantisches Differential** genannt. Oft handelt es sich bei den Items um *Aussagen*, die über die gleiche Skala bewertet werden. 

Ein besonderes Grid-Item ist das **Ranking** oder **Sortieren**. Bei dieser Art von Items werden mehrere Antwortmöglichkeiten in *eine* Reihenfolge gebracht. Die Antwortmöglichkeiten werden als eigene Items gespeichert, wobei der Wertebereich für jede Antwortmöglichkeit durch die möglichen Ränge festgelegt ist. Diese Items haben einen *ordialen Wertebereich*.

Eine Variante des Sortieren sind **Zuordnungs-Items**. Bei diesen Items muss jedem Wert aus einer Liste von Werten jeweils ein Wert aus einer zweiten Liste zugeordnet werden. Die Werte aus der ersten Liste werden als Items gespeichert und die Werte aus der zweiten Liste legen den Wertebereich der Items. Diese Items haben einen *nominalen Wertebereich*.

Gelegentlich werden Fotos oder Bilder angeboten und die Teilnehmenden werden gebeten, Bereiche auf diesen Bildern auszuwählen. Dabei handelt es sich um eine Variante eines **Multiple-Choice-Grids**, bei dem die Antwortmöglichkeiten als Bilder dargestellt werden.

Durch die Wahl der Fragetypen und dem Festlegen der Wertebereiche von Formular-Items werden wird die Information *kodiert*.

### Automatische Datenerhebung

Bei der automatischen Datenerhebung werden Daten automatisch erfasst und gespeichert.

Bei der automatischen Datenerhebung werden grundsätzlich drei Kategorien unterschieden:

- **Snapshots** erfassen eine Momentaufnahme eines Systems. Bei Snapshots handelt es sich immer um komplexe *strukturierte Daten*. Ein Snapshot kann beispielsweise ein Foto, ein MRI-Scan oder eine Gen-Sequenz sein. Ein Snapshot liefert einen *Datensatz*, der in der Regel sehr viele Werte umfassst. Snapshots werden oft von speziellen Geräten erfasst und gespeichert.

- **Metriken** geben Auskunft über *Zustände* zu einem bestimmten Zeitpunkt. Oft werden Metriken in regelmässigen Abständen erfasst. Bei Metriken handelt es sich immer um einfache *strukturierte Daten*. Eine Metrik kann beispielsweise die Anzahl der Besucher einer Webseite zu einem bestimmten Zeitpunkt oder die Temperatur in einem Raum sein. Eine Metrik hat üblicherweise drei Eigenschaften:

  - *Name*
  - *Wert*
  - *Zeitpunkt*

- **Logs** geben Auskunft über *Ereignisse* in einem System. Ein Log-Eintrag wird erfasst, wenn ein Ereignis eintritt. Logs sind meist *strukturierte* oder *semi-strukturierte Daten*. Ein Log-Eintrag kann beispielsweise die Anmeldung eines Benutzers an einem System oder das Öffnen einer Webseite sein. Ein Log-Eintrag ist oft über zwei Hauptmerkmale definiert:

  - *Zeitpunkt*
  - *Ereignismeldung*

  Log-Einträge werden oft chronologisch in der Reihenfolge der Ereignisse gespeichert.

Nur weil Sensoren und andere datengenerierende Instrumente verwendet werden, findet eine automatische Datenerhebung unter Umständen nicht statt. Ein entsprechendes Instrument muss über Funktionen verfügen, um Metriken und/oder Logs zu generieren und bereitzustellen.

Bei der automatischen Datenerhebung für Metriken und Logs werden meistens mehrere Systeme gemeinsam eingesetzt. Ein System erfasst die Daten und ein anderes System speichert die Daten in einer Datenbank. Die Daten werden in der Regel in einem *Datenstrom* bzw. *Zeitreihe* erfasst und gespeichert.
