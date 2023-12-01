---
# bibliography: references.bib

execute: 
  echo: false
---
# Indizieren und Gruppieren {#sec-chapter-indizieren-gruppieren}

::: {.callout-warning}
## Work in Progress
:::

## Indizieren

::: {#def-index}
Ein **Index** bezeichnet Werte, mit denen sich ein oder mehrere Datensätze von anderen Datensätzen unterscheiden lassen.  
:::

::: {#def-indizieren}
Mit **Indizieren** wird die Arbeitsweise von Algorithmen bezeichnet, mit der Datensätze *identifiziert* werden.  
:::

::: {.callout-note}
## Merke
Indizes haben immer einen *diskreten Wertebereich*.
:::

Es werden zwei Arten von Indizes unterschieden: 

::: {#def-primaerindex}
Ein **Primärindex** enthält nur eindeutige werte, mit denen einzelne Datensätze eindeutig identifiziert werden.
:::

::: {#def-sekundaerindex}
Ein **Sekundärindex** verwenden Werte, mit denen mehrere Datensätze identifiziert werden. 
:::

::: {#def-fremdschluessel}
Ein **Fremdschlüssel** ist ein *Sekundärindex* für *Querverweise* auf eine zweite Datenstruktur (eine sog. *Indextabelle* oder engl. *Lookup-Table*).
::: 

Mithilfe von *Fremdschlüsseln* lassen sich gemeinsame Daten in eine zweite Datenstruktur auslagern. Diese Datenstruktur wird oft als Indextabelle bezeichnet.  In einer Indextabelle existiert für jeden eindeutigen Wert des Fremdschlüssels genau ein Datensatz. 

::: {.callout-note}
## Merke
Die Werte eines Fremdschlüssels bilden einen Primärschlüssel in einer Indextabelle. 
:::

::: {#def-gruppenindex}
Ein **Gruppenindex** ist ein *Sekundärindex* zur Identifikation von Datensätzen mit *gemeinsamen Eigenschaften*.
::: 

Im Gegensatz zu einem Fremdschlüssel sind diese Eigenschaften Teil des Datensatzes. 

::: {.callout-note}
## Merke
Jeder Fremdschlüssel ist gleichzeitig ein Gruppenschlüssel!
:::

Weil ein Index Werte über einen Datensatz enthält, gehört ein Index zum jeweiligen Datensatz und wird über einen *Indexvektor* in einer Stichprobe abgebildet.

::: {#def-indexvektor}
Ein **Indexvektor** bezeichnet einen Vektor, mit dessen Werten Datensätze identifiziert werden können.
:::

::: {#def-hash}
Ein **Hash** bezeichnet einen Wert in einem Indexvektor.
:::

### Existierende Indexvektoren. 

Häufig liegen Indexvektoren bereits in einer Stichprobe vor.

#### Beispiel bestehende Primär- und Sekundärindizes

|modell               |  mpg| cyl|  disp| vs| am| 
|:-------------------|----:|---:|-----:|--:|--:|
|Mazda RX4           | 21.0|   6| 160.0|  0|  1|
|Mazda RX4 Wag       | 21.0|   6| 160.0|  0|  1|
|Datsun 710          | 22.8|   4| 108.0|  1|  1|
|Hornet 4 Drive      | 21.4|   6| 258.0|  1|  0|
|Hornet Sportabout   | 18.7|   8| 360.0|  0|  0|
|Valiant             | 18.1|   6| 225.0|  1|  0|
|Duster 360          | 14.3|   8| 360.0|  0|  0|
|Merc 240D           | 24.4|   4| 146.7|  1|  0|
|Cadillac Fleetwood  | 10.4|   8| 472.0|  0|  0|
|Fiat 128            | 32.4|   4|  78.7|  1|  1|
|Honda Civic         | 30.4|   4|  75.7|  1|  1|

: Ausschnitt der `mtcars`-Stichprobe mit Primär- und Sekundärindizes {#tbl-mtcars-index}

Der Vektor `modell` ist der **Primärindex**, weil dieser Vektor nur Werte enthält, die einen Datensatz eindeutig identifizieren.

Die Vektoren `cyl` (Zylinder), `vs` (Motortyp) und `am` (Automatikschaltung) sind *Sekundärindizes* und *Gruppenindizes*, die Modelle nach verschiedenen Kriterien zusammenfassen. 

### Fehlende Indexvektoren

Gelegentlich liegen in einer Stichprobe keine Primär- oder Sekundärindizes vor oder die vorhandenen Indizes erlauben keine Zusammenfassungen für eine konkrete Fragestellung. In solchen Fällen muss ein entsprechender Index erzeugt werden.

::: {#def-hashing-funktion}
Eine Funktion, die *Hashes* für Indexvektoren erzeugt, heisst **Hashing-Funktion**.
:::

Hashing-Funktionen werden in der Industrie als Unterstützung zur Suche von Datensätzen in Datenbanken eingesetzt. Durch die geschickte Berechnung von Hashes beschleunigen diese Funktionen die Suche einzelner Werte um ein Vielfaches, indem sie den Bereich für die Suche einschränken. Deshalb haben viele Hashing-Funktionen ein anderes **Anwendungsziel** als die hier beschriebenen Hashing-Funktionen. 


### Hashing zur Identifikation

Die einfachste Technik zur eindeutigen Indizierung ist das ***Durchnummerieren*** der Datensätze einer Stichprobe. Bei dieser Technik wird jedem Datensatz eine Nummer zugewiesen. I

### Hashing zum Gruppieren

Beim Hashing zum Gruppieren müssen wir Werte erzeugen, die eine Zuordnung zu einer Gruppe oder einen Wert in einer anderen Stichprobe ermöglichen. Die Hashing-Funktion orientiert sich dabei an den konkreten Analyseanforderungen. 

Vier gängige Techniken können dabei unterschieden werden: 

- Kodieren (alle Datentypen)
- Reihenfolgen bilden durch Ganzzahldivision (nur Zahlen)
- Reihenfolgen bilden durch Modulo-Operation (nur Zahlen)
- Reihenfolgen durch Anfangsbuchstaben (nur Zeichenketten)

### Hashing für Querverweise

Beim Hashing für Querverweise gibt es zwei Stichproben. Die erste Stichprobe ist die Hauptstichprobe mit den eigentlichen Werten. Die zweite Stichprobe ist die Referenzstichprobe, die zusätzliche Informationen enthält. Ein Indexvektor für Querverweise in der ersten Stichprobe bezieht sich immer auf einen Primärindex aus der zweiten Stichprobe.

Die Hashing-Funktion muss deshalb einen Verweis zur zweiten Stichprobe herstellen. Diese Verbindung kann mit der gleichen Strategie erzeugt werden, wie beim Gruppieren. Dabei muss jedoch darauf geachtet werden, dass alle Zuordnungen des Primärvektors korrekt abgebildet sind. 

## Datensätze randomisieren

Wenn wir mit Teilstichproben arbeiten und diese mit anderen teilen, müssen wir vermeiden, dass zwei Stichproben leicht zusammengesetzt werden können und so Rückschlüsse über die Probanden möglich werden. 

::: {.callout-important}
Sobald  personenbezogene Daten statistisch ausgewertet und zur Publikation vorbereitet werden, **müssen** die Daten randomisiert werden!
:::

Dieses Rezept beschreibt eine Technik zur Anonymisierung von Daten durch Mischen. Entscheidend bei dieser Technik ist, dass wir die Werte für unsere Analyse zusammenhalten möchten, sodass unsere Ergebnisse nachvollziehbar bleiben. Gleichzeitig soll es unmöglich werden, diese Daten mit anderen Teilen unserer Studien in Verbindung zu bringen.

Die Technik der Anonymisierung durch Mischen besteht aus vier Schritten: 

1. Auswahl der Vektoren, die wir in einer Publikation teilen möchten,
2. Erzeugung eines eindeutigen Vektors,
3. zufälliges Mischen,
4. Entfernen der eindeutigen Vektoren und exportieren der Daten.

#### Schritt 1: Auswahl der Vektoren

Beim Anonymisieren müssen alle Vektoren entfernt werden, über die der Ursprung der Daten abgeleitet werden kann. Oft ist es sinnvoller, nur die Vektoren auszuwählen, die öffentlich zugänglich gemacht werden sollen.

#### Schritt 2: Erzeugung eines eindeutigen Vektors

Für die Anonymisierung müssen die Daten in eine neue Reihenfolge gebracht werden, weil die Reihenfolge der Daten Informationen über die Herkunft der Daten haben kann. So etwas kann beipielsweise vorkommen, wenn die Daten in der alphabetischen Reihenfolge von Namen sortiert sind. 

Hierzu wird als Hashing-Funktion ein *Zufallszahlengenerator* verwendet. Dabei ist es nicht notwendig einen bestimmten Wertebereich einzuhalten. Ein Zufallszahlengenerator stellt nicht sicher, dass die generierten Werte eindeutig sind. Deshalb ist der erzeugte Vektor kein Primärindex im eigentlichen Sinn. Weil dieser Index nur für die Erzeugung einer neuen Reihenfolge benötigt wird,bezeichnet man ihn als *Sortierindex*.

::: {.callout-warning}
Als Hashing-Funktion dürfen nur Zufallsgeneratoren für gleichverteilte Werte eingesetzt werden, weil nur so eine Klumpung von Werten vermieden werden kann, weil alle Werte im Erzeugungsintervall gleich wahrscheinlich sind. Es auch zu beachten, dass der Wertebereich des Zufallsgenerators viel grösser ist als die Anzahl der vorliegenden Datensätze.
:::

#### Schritt 3: Mischen

In diesem Schritt werden die Datensätze über den in Schritt 2 erzeugten Sortierindex angeordnet. Dabei wird ausgenutzt, dass ein Zufallszahlengenerator Werte in keiner bestimmten Reihenfolge erzeugt. Das Sortieren entlang dieses Index bringt die erzeugten Hashes in eine neue Reihenfolge. Dadurch werden die Werte effektiv gemischt. Die neue Reihenfolge ist wegen Schritt 2 zufällig. 

Das zufällige Mischen erzeugt Rauschen, welches Informationen überlagert, die sich aus der Reihenfolge der Daten ergeben könnten.

#### Schritt 4: Entfernen des Sortierindex und exportieren der Daten

Abschliessend muss der Indexvektor aus der Datenstruktur wieder entfernt werden, weil die Hashes Informationen über den verwendeten Zufallsgenerator enthalten.  

### Fazit

Mit den gemischten Daten ist es nun nicht mehr möglich, die Werte mit einem anderen Teil der Stichprobe zu kombinieren und so tiefere Rückschlüsse über die Teilnehmenden zuzulassen. Nur noch durch den Zugriff auf die ursprünglichen Daten können diese Zusammenhänge hergestellt werden. Daher sind die ursprünglichen Daten oft besonders schützenswert und sollten ohne Randomisierung nicht weitergegeben werden. 

::: {.callout-tip}
## Praxis
Nicht-randomisierte Rohdaten sollte immer in geschützten Repositories versioniert werden. 
:::

## Gruppieren

::: {#def-gruppieren}
Beim **Gruppieren** werden zusammengehörende Datensätze zusammengefasst, so dass nachfolgende Operationen die einzelnen Gruppen separat behandeln.
:::

Beim Gruppieren wird mindestens ein Sekundärindex benötigt, über den die Datensätze zu Gruppen zusammengefasst werden können. Eine gruppierte Operation verwendet nur die Werte innerhalb der gleichen Gruppe.  Der Vorteil einer gruppierten Operation ist, dass die Operation für alle Gruppen *gleichzeitig* ausgeführt wird. 

Damit eine gruppierte Operationen durchgeführt werden können, müssen zusammengehörende Werte identifiziert werden. Das wird durch einen Sekundärindex möglich. *Eine Gruppierung wird durch gleiche Wert im Sekundärindex gebildet.*  Gruppierungen werden verwendet, um repititive zu vermeiden. Ein weiterer Vorteil des Filterns ist, dass die Datenstruktur unverändert bleibt. Dadurch kann eine Gruppierung nach einer Operation wieder aufgehoben werden und es kann mit allen Daten weritergearbeitet werden.


Die Überlegungen des Gruppierens lassen sich auf mehrere Sekundärindizes verallgemeinern: In solchen Fällen werden die Gruppen über die Permutationen der Werte der Sekundärindizes gebildet. In der Regel werden nur die in den Daten *vorhandenen* Permutationen im Ergebnis einer gruppierten Operation berücksichtigt. Deshalb kann es notwendig sein, fehlende Permutationen nachträglich zu erzeugen, um nachgelagerte Analysen durchführen zu können.   

