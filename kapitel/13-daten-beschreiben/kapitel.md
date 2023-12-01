---
# bibliography: references.bib

abstract: ""

execute: 
  echo: false
---
# Daten beschreiben {#sec-chapter-deskriptve-statistik}

::: {.callout-warning}
## Work in Progress
:::

> Die Anwendung statistischer Verfahren setzt voraus, dass quantitative Informationen über den jeweiligen Untersuchungsgegenstand bekannt sind. [@bortz_statistik_2010, S. 25]

::: {#def-deskriptive-statistik}
Die **deskriptive Statistik** bezeichnet die Vorgehensweisen und die erforderlichen Kennzahlen zum Beschreiben von Daten. 
:::

> Die Aufgabe der Deskriptivstatistik ist es, Daten prägnant zusammenzufassen. 
>
> @sauer_moderne_2019, S. 103

Die deskriptive Statistik ist ein wichtiger Schritt beim *Dekodieren* von Daten, weil sie Kennwerte liefert, oft als Grundlage für nachfolgende Arbeitsschritte dienen.

Die *deskriptive Statistik* beschreibt Messungen von sog. *Zufallsvariablen*, die in Stichproben zusammengefasst wurden. Die *Zufallsvariablen* sind die gemessenen *Merkmale* und eine *Stichprobe* entspricht 

::: {.callout-tip}
## Praxis
In der Praxis entsprechen **Zufallsvariablen** den *gemessenen Merkmalen* und eine **Stichprobe** entspricht einen Datenrahmen mit allen Vektoren der gemessenen Merkmale.
:::

Eine Stichprobe enthält also alle zusammengehörenden Datensätze einer Untersuchung.

## Umfänge 

::: {#def-umfang}
Ein **Umfang** bezeichnet die Anzahl von *gültigen Daten* vom gleichen Datentyp. 
:::

::: {#exm-vektor-umfang}
## Vektorumfang
Der Umfang ähnelt der Länge eines Vektors, mit dem Unterschied, dass bei der Länge einer Datenstruktur auch ungültige Werte mitgezählt werden können. Wurden alle ungültigen Werte aus einem Vektor entfernt, dann ist der Umfang des Vektors gleich dessen Länge. 
:::

::: {.callout-tip}
## Konvention
Umfänge werden in wissenschaftlichen Arbeiten in der Regel mit dem Buchstaben `n` gekennzeichnet.
:::

::: {.callout-note}
## Merke
Die Bestimmung von Umfängen ist immer ein **(Ab-) Zählproblem**. 
:::

### Universelle Kennzahlen

Zwei spezielle Umfänge ist der **Stichprobenumfang** und die **Anzahl der Variablen**. Weil sich diese beiden Werte für *alle Stichproben* bestimmen lassen, handelt es sich bei diesen beiden Umfängen um *universelle Kennzahlen* von Stichproben. 

::: {#def-universelle-kennzahlen} 
Mit **universellen Kennzahlen** sind abgeleitete Werte gemeint, die sich für *alle* Stichproben bestimmen lassen. 
:::

![Universelle Stichprobenkennwerte](figures/stichprobenkennwerte.png){#fig-stichprobenkennwerte}

::: {.callout-note}
## Merke
In **jeder** (wissenschaftlichen) Arbeit, in der Daten präsentiert werden, **müssen** die beiden universellen Kennwerte angegeben werden. Fehlen diese Kennwerte, dann ist die Arbeit *unvollständig*.
:::

Der **Stichprobenumfang** entspricht der Anzahl der Datensätze einer Stichprobe. Oft wird der Stichprobenumfang **zwei Mal** berichtet. Zuerst wird der unbereinigte Stichprobenumfang berichtet. Diese beinhalte alle Datensätze der Stichprobe, was der Anzahl der durchgeführten Messungen entspricht. Anschliessend werden alle ungültigen Datensätze entfernt und die verbleibenden Datensätze nocheinmal gezählt. Sind beide Werte gleich, dann darf der Stichprobenumfang nur einmal berichtet werden.

::: {.callout-important}
## Achtung

Jeder entfernte Datensatz entfernt gleichzeitig Information aus den Daten. Es sollten nur Datensätze entfernt werden, die sich eindeutig auf Messfehler zurückführen lassen.
:::

Typische Messfehler sind: 

- Leere Datensätze, 
- Doppelte Datensätze, die durch doppeltes Abspeichern entstehen,
- Abgebrochene Eingaben oder Übertragungen sowie
- Datensätze mit Werten, die eindeutig ausserhalb der gültigen Wertebereiche liegen.

::: {.callout-tip}
## Praxis
Die Bedingungen mit denen Datensätze zur Analyse aus einer Stichprobe entfernt werden, **müssen** dokumentiert und berichtet werden.

Die unkorrigierten Daten sollten auf keinen Fall gelöscht oder überschrieben werden, um sicherzustellen, dass fehlerhafte Korrekturen zu keinem Datenverlust führen!
::: 

Für die **Anzahl der Variablen** könnte prinzipiell auf die Dokumentation einer Stichprobe zurückgegriffen werden. Trotzdem sollten *beide* Kennzahlen bestimmt werden, um sicherzustellen, dass wirklich alle Variablen in einer Stichprobe berichten und nicht versehentlich Variablen unterschlagen, die in der Dokumentation ausgelassen wurden festgehalten werden.

::: {.callout-warning}
Weil automatisch generierte sequentielle Vektoren keine Zufallsvariablen sind, werden sie nicht zur Anzahl der Variablen hinzugezählt. Solche Vektoren sollten im Datenschema entsprechend markiert werden. 
:::

::: {.callout-tip}
## Konvention
In **Fragebogenstudien** wird die Anzahl der Vektoren als Anzahl der **Items** bezeichnet. Damit sind die unabhängig festgehaltenen Antwortmöglichkeiten gemeint. 
:::

::: {.callout-tip}
## Konvention
In **technischen Studien** wird die Anzahl der Vektoren als Anzahl der *Parameter*, *Vektoren* **oder** *Variablen* bezeichnet. Damit sind die voneinander unabhängig gemessenen Merkmale gemeint.
:::

Beim **Stichprobenumfang** bestimmen wir die Anzahl der Datensätze. Für die **Anzahl der Variablen** müssen wir die Vektoren zählen. 

::: {.callout-note}
## Merke
Stichproben sind immer **rechteckig**. Alle Variablen sind immer in allen Datensätzen vorhanden (horizontaler Umfang bzw. Anzahl der Variablen) und alle Datensätze haben für jede Variable einen Wert (vertikaler Umfang bzw. Stichprobenumfang).  Die Kennwerte lassen sich deshalb durch horizontales und vertikales zählen ermitteln.
:::

### Variablenumfang

Wenn Statistiker von Stichprobenumfang sprechen, dann verweist das Wort *Stichprobe* sehr häufig auf die gerade behandelten Vektoren und *nicht unbedingt* auf alle gemeinsam gemessenen Merkmale. Deshalb muss für jede Variable auch der **Variablenumfang** bestimmt werden.

::: {#def-variablenumfang}
Der **Variablenumfang** bezeichnet die Anzahl der gültigen Werte eines Vektors bzw. Merkmals.
:::

Zur Bestimmung des Variablenumfangs müssen alle fehlenden Werte aus dem entsprechenden Vektor entfernt werden, bevor der Umfang ermittelt wird. Deshalb ist es nicht unüblich, dass die einzelnen Merkmale voneinander und vom Stichprobenumfang abweichende Umfänge haben.
 
Weil in den Entsprechend müssen fehlende Werte vor der Bestimmung des Variablenumfangs aus dem Vektor entfernt werden. Es ist normal, dass sich der Stichprobenumfang und die Variablenumfänge unterscheiden. Diese Unterschiede entstehen dadurch, dass nicht alle Messungen erfolgreich verlaufen. Zum Beispiel passiert es häufig, dass Teilnehmende bei einem Fragebogen nicht alle Fragen beantworten oder beantworten können. In solchen Fällen ist der Stichprobenumfang grösser als die jeweiligen Variablenumfänge. So kommt es regelmässig vor, dass verschiedene Variablenumfänge sich ebenfalls unterscheiden. 

Die deskriptive Statistik muss daher **immer** den Stichprobenumfang **und** die Variablenumfänge anführen.

## Skalenniveaus und Lagemasse

Für Variablen wurden im @sec-datentypen die folgenden Skalenniveaus eingeführt, um Daten nach den Beziehungen zwischen den Werten des Wertebereichs zu kategorisieren. Dabei wurden die folgenden Kategorien eingeführt: 

1. Nominalskalierte Daten
2. Ordinalskalierte Daten
3. Metrisch-skalierte Daten (Intervall- oder Varianzskaliert)

Ein wichtiges Merkmal der Skalenniveaus sind die zulässigen Operationen über die Daten. 

Nominalskalierte Daten lassen sich nur über die Ungleichheit unterscheiden. Gleiche Werte dieser Datenkategorie dürfen nur gezählt werden.

Ordinalskalierte Daten lassen sich sortieren, so dass für jeden Wert eines Wertebereichs Grösser-Kleiner-Beziehungen zu allen anderen Werten festgelegt werden können. Entsprechend lassen sich die Werte auf eine Weise nummerieren, so dass die Nummerierung der Reihenfolge der Werte im Wertebereich widerspiegelt.



Die Skalenniveaus unserer Variablen müssen wir den Vektoren zuordnen können. Dazu müssen wir sowohl die Variablen und Vektoren unserer Stichprobe kennen. Diese Information erschliesst sich nicht aus den Daten, sondern ist in der Regel separat dokumentiert. 

Unsere Beispielstichprobe hat 53 Vektoren. Diese Vektoren sind vier Variablengruppen zugeordnet. Eine Variablengruppe sind unterschiedliche Merkmalsausprägungen mit dem gleichen Skalennivau, die wir in Beziehung setzen. Das Beispiel umfasst die folgenden Variablengruppen und Skalenniveaus: 

1. `q1` ist ein Indikator
2. `q3`, `q4` und `q16` sind nominalskalierte Variablen
  * `q3` hat die Skalierung von `F`, `M`, `X` und `O`. 
  * `q4` hat die Skalierung von `A`, `G`, `L`, `N`, `P`, `S`, `T` und `W`. 
  * `q16` hat die Skalierung von `0` und `1`. 
3. `q10` sind ordinalskalierte Variablen mit der Skalierung von `0`-`10` in ganzzahligen Schritten. Die Messungen stammen von sog. Likert-Skalen.

::: {.callout-tip}
## Übung 
Bestimmen Sie alle Vektorennamen in der Beispielstichprobe.
:::

Für die Variable `q10` es 6 Untermerkmale und für die Variable `q16` gibt es 19 Untermerkmale. Für alle Merkmale in `q10` und `q16` wurden jeweils zwei Aspekte (`0` und `1`) erhoben. Diese Aspekte können für das jeweilige Untermerkmal direkt verglichen werden. Wir haben also im Vektor `q16_13_1` den zweiten Aspekt des 13. Untermerkmals der Variable q16 erfasst. 

### Lagemasse für nominale Skalenniveaus

Für nominale Variablen dürfen wir als Lagemass für die Verteilung nur den *Modus* bestimmen. Damit ist die am häufigsten auftretende Merkmalsausprägung gemeint. 

Das zweite "Lagemass" sind die Häufigkeiten der tatsächlich auftretenden Skalenwerte. Beide Kennwerte erschliessen sich über die *Häufigkeiten* der vorkommenden Werte.

::: {.callout-tip}
## Praxis
Der Modus wird in der Regel zugunsten des zweiten "Lagemasses" für nominalskalierte Daten *nicht berichtet*, weil der Modus nur eine Merkmalsausprägung berücksichtigt und alle anderen Merkmalsausprägungen ignoriert.
:::

Die Häufigkeiten der tatsächlich auftretenden Merkmalsausprägungen werden durch abzählen (@sec-chapter-vektoren) bestimmt. 

Dazu bestimmen wir die Häufigkeit des Auftretens einer Merkmalsausprägung in unserer Stichprobe. Das bestimmen der Häufigkeiten ist eine Abzählaufgabe, bei der wir vorher die gleichen Merkmalsausprägungen gruppiert haben. 

Das folgende Beispiel zwei Varianten für das Feststellen der Häufigkeiten von nominalskalierten Variablen. Die erste Variante ist die direkte Umsetzung des gerade beschriebenen Algorithmus. 
```R
stichprobe |> 
    group_by(q3) |> 
    summarise(n = n())
```

<table border="1">
<thead>
	<tr><th scope=col>q3</th><th scope=col>n</th></tr>
	<tr><th scope=col>&lt;chr&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><td>F</td><td>10</td></tr>
	<tr><td>M</td><td>17</td></tr>
</tbody>
</table>

Die zweite Variante verwendet die `count()`-Funktion, um das gleiche Ziel zu erreichen. Die Variante mit `count()` ist etwas leichter zu lesen, weil wir *explizit* klarstellen, dass wir die Merkmalsausprägungen *abzählen*. 

```R
stichprobe |> 
    count(q4)
```

<table border="1">
<thead>
	<tr><th scope=col>q4</th><th scope=col>n</th></tr>
	<tr><th scope=col>&lt;chr&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><td>N</td><td>17</td></tr>
	<tr><td>P</td><td>10</td></tr>
</tbody>
</table>

Wir können an diesem Beispiel erkennen, dass in unserer Stichprobe nicht alle Ausprägungen der jeweiligen Skalierung in unseren Variablen vorkommen. Uns fällt auch auf, dass die Häufigkeiten für die gemessenen Merkmalsausprägungen der Variablen gleich sind. 

Neben den absoluten Häufigkeiten interessieren uns ebenfalls die *relativen Häufigkeiten*. Diese **müssen** bei der Beschreibung von nominalskalierten Variablen mit angegeben werden. 

Relative Häufigkeiten sind nichts anderes als die prozentualen Anteile der absouluten Häufigkeit in der Gesamtstichprobe. Wir können die relativen Häufigkeiten leicht aus den absoluten Häufigkeiten bestimmen.

```R
stichprobe |> 
    count(q4) |>
    mutate(
        prozent = n / sum(n)
    )
``` 

Damit erhalten wir die prozentualen Anteile für alle beobachteten Merkmalsausprägungen. 

::: {.callout-warning}
## Achtung
Beachten Sie hier, dass `n` den Vektor `n` bezeichnet, der durch den Aufruf der `count()`-Funktion erzeugt wird. Sie dürfen diesen Vektor nicht mit der Funktion `n()` verwechseln! Die `n()`-Funktion liefert die Anzahl der Datensätze einer Stichprobe. Nachdem wir `count()` aufgerufen haben, ist das Ergebnis von `n()` in diesem Beispiel gleich `2`. 
:::

Wir können nun leicht den **Modus** der Variable mit Hilfe der `max`-Aggregation bestimmen. Anstelle der `summerise()`-Funktion verwenden wir jedoch besser die `filter()`-Funktion, um auch das zugehörige Skalenniveau zu erhalten.

```R
# Bestimmen des Modus von q3
stichprobe |> 
    count(q3) |>
    filter(n == max(n))
```

<table border="1">
<thead>
	<tr><th scope=col>q3</th><th scope=col>n</th></tr>
	<tr><th scope=col>&lt;chr&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><td>M</td><td>17</td></tr>
</tbody>
</table>

::: {.callout-tip}
Der **Modus** ist in der deskriptiven Statistik  nur in Ausnahmefällen von Bedeutung. Eine solche Ausnahme liegt vor, wenn aus mehreren Merkmalsausprägungen der Modus den stark überwiegenden Anteil in der Stichprobe ausmacht. Dieser Anteil ist ungefähr ab einer relativen Häufigkeit von `.75` oder grösser gegeben. In solchen  Fällen sollten Sie trotzdem die Häufigkeiten der anderen Merkmalsausprägungen berichten.
:::

### Lagemasse für metrische Skalenniveaus

Die grundlegenden Kennwerte für  metrische Skalenniveaus sind die *Bandbreite*, die sich aus dem kleinsten (*Minimum*) und grössten gemessenen Wert (*Maximum*) ergibt. 

Für metrischskalierte Variablen können wir immer den Median und Quantile bestimmen, wobei wir uns in der Regel auf die *Quartile* beschränken. Bei der Beschreibung der Quartile geben wir immer den *Interquartilsabstand* mit an. Dieser ist das Gegenstück zur Bandbreite und zeigt uns zwischen welchen Ausprägungen die Hälfte der gemessenen Variablenwerte liegen.

Das folgende Beispiel zeigt die Berechnung der relevanten Kennwerte für die Variable `q10_1_0`. Diese Berechnung entspricht der `favstats` der in Sauer (2019) beschriebenen `mosaic`-Bibliothek

```R
stichprobe |>
    select(q10_1_0) |>
    drop_na() |>
    summarise(
        n = n(),
        min = min(q10_1_0),
        max = max(q10_1_0),
        bw = max - min,
        
        iqr = IQR(q10_1_0), # berücksichtigt ausreisser!
        
        q1 = quantile(q10_1_0, .25),
        # q2 = quantile(q10_1_0, .5), # der Median ist die zweite Quartilsgrenze
        md = median(q10_1_0), 
        q3 = quantile(q10_1_0, .75),
        # q4 = quantile(q10_1_0, 1) , # Das Maximum ist die vierte Quartilsgrenze.

        mad = mad(q10_1_0, constant = 1) 
    )
```

::: {.callout-note}
## Merke
Diese Ergebnisse werden nicht interpretiert! 
:::

::: {.callout-note}
## Merke
Es handelt sich bei diesen Ergebnisse um sog. **á priori Fakten**. Es sind Fakten, die sich direkt aus den Messungen und der Definition der Lagemasse ergeben und keiner weiteren Begründung bedürfen.
:::

### Lagemasse für ordinale Skalenniveaus

Im Unterschied zu den metrischen Skalenniveaus ist der Mittelwert und die Standardabweichung für *ordianle Skalenniveaus* **nicht definiert**. Ausserdem werden Quartilsgrenzen und die davon abhängigen Variablen *etwas* anders berechnet als bei metrischskalierten Variablen. Damit wir keine Folgefehler für die spätere Analyse erhalten müssen wir für ordinalskalierte Variablen die entsprechenden Kennwerte richtig berechnen. 

::: {.callout-warning}
## Achtung
In vielen Fällen ergeben die verschiedenen Berechnungsarten die *gleichen Ergebnisse*. Das bedeutet nicht, dass die Ergebnisse in *allen* Fällen gleich und damit austauschbar sind!
:::

> Die Berechnungsart wird mit dem Parameter `type` festgelegt. Dieser Parameter können wir die Ganzzahlen von `1` bis `8` übergeben. Der Standardwert für diesen Parameter ist `7`. Die Werte `1`, `2` und `3` sind für die Berechnung bei ordinalen Skalenniveaus gedacht. Die anderen Werte beschreiben verschiedene Varianten für metrische Skalenniveaus. 

::: {.callout-note}
Verwenden Sie nur die Werte `1` für ordinale Skalenniveaus und `7` für metrische Skalenniveaus. Weil `7` der Vorgabewert ist, wird dieser bei metrischen Skalenniveaus einfach weggelassen. 
:::

Alle anderen Werte für den `type`-Parameter sind für besondere Fälle, wenn Ergebnisse aus anderen Quellen kontrolliert werden müssen. 

Das folgende Codesegment zeigt Berechnung der statistischen Kennwerte für ordinale Skalenniveaus. 

```R
stichprobe |>
    select(q10_1_0) |>
    drop_na() |>
    summarise(
        n = n(),
        min = min(q10_1_0),
        max = max(q10_1_0),
        bw = max - min,
        
        iqr = IQR(q10_1_0, type = 1), # berücksichtigt ausreisser!
        
        q1 = quantile(q10_1_0, .25, type = 1),
        # q2 = quantile(q10_1_0, .5, type = 1), # der Median ist die zweite Quartilsgrenze
        md = median(q10_1_0, type = 1), 
        q3 = quantile(q10_1_0, .75, type = 1),
        # q4 = quantile(q10_1_0, 1, type = 1) , # Das Maximum ist die vierte Quartilsgrenze. 

       mad = mad(q10_1_0, constant = 1)
    )
```

#### Mittlere absolute Abweichung vom Median

Der Interquartilsabstand (IQR) ist ein Standardmass, dass sich aus den Quartilsgrenzen ergibt. Der IQR gibt aber nur über einen Teil der Stichprobe Auskunft, nämlich genau über die Hälfte der Stichprobe. Das liegt daran, dass der IQR in den Grenzen des 2. und 3. Quartils definiert ist. Weil jedes Quartil genau ein Viertel einer Stichprobe umfasst, decken 2 Quartile die Hälfte der Stichprobe ab. Für ordianalskalierte Daten ist dieser Wert als Streumass weniger aussagekräftig, als die Varianz bei metrisch-skalierten Daten, weil der IQR die Hälfte der Werte ignoriert.

Damit wir die gesamte Stichprobe beschreiben können, wünschen wir uns ein Mass für die Streuung über die gesamte Stichprobe. Dieses Mass ist die sog. **Mittlere absolute Abweichung vom Median** (MAD).  Wie der IQR oder die Standardabweichung ist dieses Mass ein Kennwert für die Varianz einer Stichprobe. 

Dazu berechnen wir die Abstände der jeweiligen Merkmalsausprägung von Median. Weil sich aus der Definition des Medians ergibt, dass 50% unserer Werte unterhalb und 50% oberhalb des Medians liegen müssen wir darauf achten, dass sich die Differenzen nicht aufheben. Deshalb berechnen wir den Absolutbetrag der Differenzen. Damit erhalten für jede gemessene Merkmalsausprägung einen Wert für den Abstand zum Median. Für diese Werte bilden wir das arithmetische Mittel.

Das Ergebnis zeigt uns die zentrale Tendenz für alle Werte unserer Stichprobe in Bezug auf den Median. Ist der Wert klein, dann weist das auf insgesamt dicht zusammenliegende Werte hin. Ist dieser Wert gross, dann weist das auf eine breit gestreute Werte hin. 

Das folgende Beispiel stellt das Mittlere absolute Abweichung vom Median (`mad`) und den IQR für das Variablepaar `q10_1`  gegenüber.


```R
stichprobe |>
    pivot_longer(starts_with("q10_1"), names_to = "variable", values_to = "werte") |> 
    select(variable, werte) |>
    drop_na() |>
    group_by(variable) |>
    summarise(
        n = n(),
        md = median(werte), 
        iqr = IQR(werte),

        mad_haendisch = (werte - md) |> abs() |> median(),
        mad = mad(werte)
    )
```

<table border="1">
<thead>
	<tr><th scope=col>variable</th><th scope=col>n</th><th scope=col>md</th><th scope=col>iqr</th><th scope=col>mad_haendisch</th><th scope=col>mad</th></tr>
	<tr><th scope=col>&lt;chr&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th></tr>
</thead>
<tbody>
	<tr><td>q10_1_0</td><td>27</td><td>7</td><td>3.5</td><td>1.8888889</td><td>1.8888889</td></tr>
	<tr><td>q10_1_1</td><td>27</td><td>9</td><td>1.5</td><td>0.8888889</td><td>0.8888889</td></tr>
</tbody>
</table>
