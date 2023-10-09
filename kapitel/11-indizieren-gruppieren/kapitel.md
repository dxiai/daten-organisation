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

Es werden drei Arten von Indizes unterschieden: 

1. Der **Primärindex**, mit dem ein einzelner Datensatz eindeutig *identifiziert* werden kann. 
2. **Sekundärindizes** erlauben *Querverweise* auf eine zweite Stichprobe (eine sog. *Indextabelle* oder engl. *Lookup-Table*).
3. **Sekundärindizes** erlauben die Identifikation von Datensätzen mit *gemeinsamen Eigenschaften*. Diese Indizes werden auch als *Gruppenindex* bezeichnet.

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

: Ausschnit der `mtcars`-Stichprobe mit Primär- und Sekundärindizes {#tbl-mtcars-index}

Der Vektor `modell` ist der **Primärindex**, weil dieser Vektor nur Werte enthält, die einen Datensatz eindeutig identifizieren.

Die Vektoren `cyl` (Zylinder), `vs` (Motortyp) und `am` (Automatikschaltung) sind *Sekundärindizes* und *Gruppenindizes*, die Modelle nach verschiedenen Kriterien zusammenfassen. 

### Fehlende Indexvektoren

Gelegentlich liegen in einer Stichprobe keine Primär- oder Sekundärindizes vor oder die vorhandenen Indizes erlauben keine Zusammenfassungen für eine konkrete Fragestellung. In solchen Fällen muss ein entsprechender Index erzeugt werden.

::: {#def-hashing-funktion}
Eine Funktion, die *Hashes* für Indexvektoren erzeugt, heisst **Hashing-Funktion**.
:::

Hashing-Funktionen werden in der Industrie als Unterstützung zur Suche von Datensätzen in Datenbanken eingesetzt. Durch die geschickte Berechnung von Hashes beschleunigen diese Funktionen die Suche einzelner Werte um ein Vielfaches, indem sie den Bereich für die Suche einschränken. Deshalb haben viele Hashing-Funktionen ein anderes **Anwendungsziel** als die hier beschriebenen Hashing-Funktionen. 


### Hashing zur Identifikation

Die einfachste Technik zur eindeutigen Indizierung ist das ***Durchnummerieren*** der Datensätze einer Stichprobe. Bei dieser Technik wird jedem Datensatz eine Nummer zugewiesen. In R verwenden wir dazu die Funktion `row_number()`. Diese Funktion ist einer *Sequenz* vorzuziehen, weil diese Funktion auch bei leeren Stichproben fehlerfrei arbeitet.

In Excel muss zum Durchnummerieren die `SEQUENZ()`-Funktion verwendet werden. Das erreichen wir mit der folgenden Operation: `=SEQUENZ(ZEILEN(StichprobenBereich))`, wobei `StichprobenBereich` eine Excel-Adresse sein muss. Weil mit Excel keine leeren Stichproben erzeugt werden dürfen, gibt es mit Excel nicht das gleiche Problem wie mit R. Wegen dieser Eigenschaft muss ein entsprechender Bereich mindestens einen Stichprobenumfang von eins haben. Diese Eigenschaft gilt auch für Tabellen, die nur aus Überschriften bestehen. 

> **Fingerübung:** Nummerieren Sie die Stichprobe `mtcars` und speichern Sie die Nummern im Vektor `nr`.


### Hashing zum Gruppieren

Beim Hashing zum Gruppieren müssen wir Werte erzeugen, die eine Zuordnung zu einer Gruppe oder einen Wert in einer anderen Stichprobe ermöglichen. Die Hashing-Funktion orientiert sich dabei an den konkreten Analyseanforderungen. 

Vier gängige Techniken können dabei unterschieden werden: 

- Kodieren (alle Datentypen)
- Reihenfolgen bilden durch Ganzzahldivision (nur Zahlen)
- Reihenfolgen bilden durch Modulo-Operation (nur Zahlen)
- Reihenfolgen durch Anfangsbuchstaben (nur Zeichenketten)

#### Beispiel Hashing zum Gruppieren.

Das folgende Beispiel bildet einen Index, um die Motorisierung der Fahrzeugtypen in der Stichprobe `mtcars` zu bestimmen. Dabei sollen die Modelle in schwach-, mittel-, stark- und sehr starkmotorisierte Typen unterschieden werden. Die Motorisierung richtet sich dabei zum einen nach der Leistung (`hp`). Zum anderen richtet sich die Motorisierung nach dem Fahrzeuggewicht (`wt`), weil für ein schweres Fahrzeug mehr Leistung zum Bewegen benötigt wird als für ein leichtes. Um beide Werte zu berücksichtigen, wird das Verhältnis der beiden Werte bestimmt. Ein Verhältnis ist eine *Division*. In diesem Fall wird das Gewicht als Nenner verwendet und die Leistung als Zähler. So ergeben sich immer Werte grösser als 1, weil die Leistung immer viel grösser als das Gewicht ist.

In diesem Beispiel besteht die Hashing-Funktion aus zwei Teilen: 

1. Das Verhältnis zwischen Leistung und Gewicht wird bestimmt und im Vektor `verhaeltnis` abgelegt. 
2. Die Leistungsklassen werden durch *Kodieren* den oben festgelegten Klassen zugewiesen und im Vektor `klasse` gespeichert.

```r
mtcars |> 
    as_tibble(rownames = "modell") |> 
    mutate(
        verhaeltnis = hp/wt, 
        klasse = case_when( 
            verhaeltnis > 60 ~ "sehr stark",
            verhaeltnis > 50 ~ "stark", 
            verhaeltnis > 40 ~ "mittel", 
            TRUE ~ "schwach") 
    )
```


> **Fingerübung:** Bestimmen Sie die Effizienz der Modelle in `mtcars` indem Sie den Verbrauch (`mpg`) und den Hubraum (`disp`) berücksichtigen. Legen Sie Effizienzklassen fest.


### Hashing für Querverweise

Beim Hashing für Querverweise gibt es zwei Stichproben. Die erste Stichprobe ist die Hauptstichprobe mit den eigentlichen Werten. Die zweite Stichprobe ist die Referenzstichprobe, die zusätzliche Informationen enthält. Ein Indexvektor für Querverweise in der ersten Stichprobe bezieht sich immer auf einen Primärindex aus der zweiten Stichprobe.

Die Hashing-Funktion muss deshalb einen Verweis zur zweiten Stichprobe herstellen. Diese Verbindung kann mit der gleichen Strategie erzeugt werden, wie beim Gruppieren. Dabei muss jedoch darauf geachtet werden, dass alle Zuordnungen des Primärvektors korrekt abgebildet sind. 

## Datensätze randomisieren

Wenn wir mit Teilstichproben arbeiten und diese mit anderen teilen, müssen wir vermeiden, dass zwei Stichproben leicht zusammengesetzt werden können und so Rückschlüsse über die Probanden möglich werden. 

::: {.callout-important}
Sobald  personenbezogene Daten statistisch ausgewertet und zur Publikation vorbereitet werden, **müssen** die Daten randomisiert werden!
:::


Dieses kleine Rezept beschreibt eine Technik zur Anonymisierung von Daten durch Mischen. Entscheidend bei dieser Technik ist, dass wir die Werte für unsere Analyse zusammenhalten möchten, sodass unsere Ergebnisse nachvollziehbar bleiben. Gleichzeitig soll es unmöglich werden, diese Daten mit anderen Teilen unserer Studien in Verbindung zu bringen.

Die Technik der Anonymisierung durch Mischen besteht aus vier Schritten: 

1. Auswahl der Vektoren, die wir in einer Publikation teilen möchten,
2. Erzeugung eines eindeutigen Vektors,
3. zufälliges Mischen,
4. Entfernen der eindeutigen Vektoren und exportieren der Daten.

#### Schritt 1: Auswahl der Vektoren

Wie üblich wählen wir die Vektoren mit der `select()`-Funktion aus. 

#### Schritt 2: Erzeugung eines eindeutigen Vektors

Alle unsere Werte müssen zusammengehalten werden, weil unsere Analyse sonst nicht mehr nachvollziehbar ist. Wir nummerieren dazu unsere Datensätze durch. 

#### Schritt 3: Mischen

Dieser Schritt greift auf die Funktion `sample()` zurück. Wir erzeugen aus den ursprünglichen Nummerierungen eine neue Nummerierung durch ``daten |> mutate( id_neu = sample(id) )``. Nach dieser neuen Nummerierung sind unsere Datensätze aber immer noch in der gleichen Reihenfolge und noch nicht gemischt. Wir müssen also die Reihenfolge so anpassen, dass die neue Nummerierung gilt. Das erreichen wir mit dem Funktionsaufruf ``daten |> arrange( id_neu )``. 

#### Schritt 4: Entfernen des eindeutigen Vektors und exportieren der Daten

Abschliessend müssen wir **unbedingt** die beiden Hilfsvektoren, die wir zum Mischen verwendet haben, aus unserer Stichprobe wieder entfernen. Das erreichen wir mit einer Vektorauswahl: ``daten |> select(-c(id, id_neu))``. 

#### Vollständige Lösung

Wir greifen hier auf eine Stichprobe zurück, die Geschlechtsinformationen, Alter und digitale Nutzungsgewohnheiten umfasst. Wir erstellen zwei getrennte Teilstichproben, von denen eine nur die Nutzungsgewohnheiten und das Geschlecht und eine nur die Nutzungsgewohnheiten und das Alter beinhaltet. 


Sie müssen die Datei vor dem Einlesen noch in `beispielstichprobe.csv` umbenennen.

```R
daten = read_delim("beispielstichprobe.csv")

# mischen Funktion aus einer Funktionskette erstellen, damit 
#    wir nicht so viel tippen müssen.
mischen = . |> 
    mutate( 
        id = row_number(), 
        id_neu = sample(id)
    ) |> 
    arrange(id_neu) |> 
    select(-c(id, id_neu))

daten |> 
    select(geschlecht, starts_with("technik")) |> 
    mischen() |> 
    write_csv("teilstichprobe_geschlecht_technik.csv")

daten |> 
    select(alter, starts_with("sozial")) |> 
    mischen() |> 
    write_csv("teilstichprobe_alter_sozial.csv")
```

Die zwei Teilstichproben lassen sich nicht mehr zusammenführen. Damit erkennen wir auch die Grenzen dieser Technik: Wenn zwei gemischte Stichproben ausreichend viele gemeinsame oder sehr detaillierte Vektoren haben, die in beiden Teilstichproben vorkommen, dann können diese Stichproben trotz mischen wieder zusammengeführt werden. 

Mit den gemischten Daten ist es nun nicht mehr möglich, die Werte mit einem anderen Teil der Stichprobe zu kombinieren und so tiefere Rückschlüsse über die Teilnehmenden (womöglich unwissend) zuzulassen. Nur noch durch den Zugriff auf die ursprünglichen Daten können diese Zusammenhänge hergestellt werden. Daher sind die ursprünglichen Daten oft besonders schützenswert und sollten ohne Randomisierung nicht weitergegeben werden. 