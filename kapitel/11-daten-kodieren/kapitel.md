---
# bibliography: references.bib

execute: 
  echo: false
---

# Daten kombinieren und kodieren {#sec-daten-kodieren}


Oft unterscheiden sich die Werte von denen, die zur Bestimmung der Kennzahlen verwendet werden müssen. Das betrifft oft erhobene Werte, die als Zeichenketten vorliegen. Damit Kennzahlen bestimmt werden können müssen diese Werte vor der Analyse angepasst werden. Dieser Schritt wird als *Kodieren* bezeichnet. 

Eine Möglichkeit zum Kodieren wird durch die *Kombination* mehrerer Stichproben erreicht. Das Kombinieren ist jedoch nicht auf das Kodieren beschränkt, sondern eine zentrale Aufgabe beim Zusammenführeren meherer Datenquellen. 

## Kombinieren

::: {#def-daten-kombinieren}
**Kombinieren** von Daten bedeutet die Verknüpfung von Daten aus verschiedenen Quellen zu einer Datenstruktur.
:::

Beim Kombinieren von Daten werden die Daten aus verschiedenen Quellen zu einer gemeinsamen Datenstruktur zusammengeführt. Es gibt verschiedene Arten von Kombinationen, die sich in der Art der Verknüpfung unterscheiden.

### Kombinationsarten

- Zeilenweise Konkatenation

Bei der zeilenweisen Konkatenation wird davon ausgegangen, dass beide Quellen genau die gleichen Merkmale haben. Die Daten werden dann einfach aneinandergehängt. Die Reihenfolge der Datensätze bleibt dabei erhalten.

Bei der zeilenweisen Konkatenation sollte darauf geachtet werden, dass die Datensätze den ursprünglichen Stichproben zugeordnet weden können. Es ist üblich die einzelnen Stichproben mittels einer Skalarverknüpfung um einen konstanten Wert zu erweitern. Dabei muss dieser Wert für die einzelnen Stichproben verschieden sein. Werden anschliessend die Stichproben zusammengeführt, lassen sich die einzelnen Datensätze klar unterscheiden.

- Vereinigung (union/ outer join)

Bei der Vereinigung werden alle Werte aus beiden Quellen über ein gemeinsames Merkmal kombiniert. Das Ergebnis enthält anschliessend Datensätze mit allen Merkmalen aus beiden Quellen. Gibt es für Datensätze in einer Quelle keine Entsprechung in der anderen, werden die fehlenden Werte mit einem speziellen Wert (z.B. *undefinierte Werte*) aufgefüllt.

**Spaltenkonkatenation ist eine spezielle Form der Vereinigung** 

Für eine Spaltenkonkatenation müssen beide Stichproben den gleichen Umfang haben. Meistens fehlen jedoch gemeinsame Merkmale für die Vereinigung. In diesem Fall wird die Vereinigung über einen *gedachten Wert* durchgeführt. Dieser Wert ist die Zeilennummer: Dazu werden alle Datensätze in beiden Quellen *durchnummeriert*. Diese Nummer wird dann als gemeinsames Merkmal verwendet. Anschliessend wird die Nummerierung aus dem Ergebnis entfernt.

- Partielle Vereinigung (partial union)

Die partielle Vereinigung kombiniert nur Werte, die in beiden Quelle ein gemeinsames Merkmal teilen. Das Ergebnis enthält anschliessend nur noch Datensätze mit allen Merkmalen aus beiden Quellen für die es eine Entsprechung für die gemeinsamen Merkmale gibt. Dadurch entfallen alle Datensätze, die nur in einer der beiden Stichproben repräsentiert sind. 

- Schnittmenge (intersection/inner join)

Die Schnittmenge kombiniert nur Werte, die in beiden Quellen vorkommen. Die Schnittmenge ist also immer eine Teilmenge der Vereinigung.

- Differenz (difference)

Bei der Differenz werden alle Datensätze mit einer Entsprechung von gemeinsamen Merkmalen in beiden Quellen aus dem Ergebnis entfernt. Das Ergebnis umfasst also nur Datensätze, die in der ersten Quelle vorkommen, aber nicht in der zweiten Quelle.

Die *Differenz* entspricht einen Filter mit einem oder mehreren $\notin$-Vergleichen.

## Kodieren

::: {#def-daten-kodieren}
**Kodieren** von Daten bedeutet die Umwandlung von Daten in ein anderes Format oder einen anderen Wertebereich.
:::

Beim Kodieren wird eine **Kodierungsfunktion** verwendet, die jeden Wert des ursprünglichen Wertebereichs einem Wert des gewünschten Wertebereichs zuordnet. Dabei ist es nicht notwendig, dass alle ursprünglichen Werte eindeutig zugewiesen werden. Das heisst, dass mehrere Werte des ursprünglichen Wertebereichs dem gleichen Wert des neuen Wertebereichs zugeordnet werden können.

Sehr häufig werden Kodierungsfunktionen als **Entscheidungsbäume** (s. @def-entscheidungsbaum) umgesetzt. Dabei werden logische Ausdrücke für die Zuweisung der Ergebniswerte verwendet. Die logischen Ausdrücke werden dabei der Reihe nach geprüft. Die erste zutreffende Entscheidung, bestimmt den Ergebniswert.

::: {.callout-tip}
## Praxis
In Berichten und Protokollen müssen Kodierungsfunktionen im Methodenteil dokumentiert werden. 
:::


### Kodierungstabellen

Eine besondere Technik des Kodierens ist die Verwendung von Kodierungstabellen. Solche Tabellen bilden Entscheidungsbäume tabellarisch ab. Eine Umsetzung eines Entscheidungsbaums kann dann mit einer Kombination von zwei Datenrahmen gleichgesetzt werden.

::: {#def-kodierungstabelle}
Eine **Kodierungstabelle** ist eine Tabelle, die jedem Wert eines Wertebereichs einen Wert eines anderen Wertebereichs zuordnet.
:::

Eine Kodierungstabelle ist eine *Variante* einer *Indextabelle*.

Die *Kodierungsfunktion* ist in diesem Fall die Vereinigung oder eine partielle Vereinigung der Stichprobe mit der Kodierungstabelle.

::: {.callout-tip}
## Praxis
Kodierungstabellen sollten immer für die Kodierung von nominal- oder ordinalskalierten Wertebereichen verwendet werden, weil sie die Kodierungsfunktion explizit machen und gleichzeitig die Kodierung *dokumentieren*.
:::

::: {.callout-tip}
## Praxis
Für Kodierungstabellen kommt normalerweise eine der Kombinationsarten als Kodierungsfunktion zum Einsatz. In solchen Fällen muss nur dir Kombination in Berichten genannt werden und nicht ihre Funktionsweise imm Detail.
:::
