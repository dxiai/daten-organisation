---
# bibliography: references.bib

execute: 
  echo: false
---
#  Vektoroperationen

Im [Kapitel @sec-datentypen] wurden Vektoren unter der allgemeinen @def-vektor eingeführt.

::: {#def-vektor-element}
Die Werte eines Vektors heissen **Elemente**.
:::

Ein Vektor ist eine Datenstruktur mit mehreren Werten, wobei die Anzahl der Werte eine ganze Zahl $\ge 0$ ist. Dieser Wert entspricht der Länge des Vektors. 

::: {#def-vektor-index}
Jedes Element hat eine eindeutige Position im Vektor. Diese Position heisst **Index**.
:::

Vektoren sind bezüglich des Datentyps *homogen*. D.h. alle Elemente eines Vektors haben den gleichen Datentyp.

::: {#def-leerer-vektor}
Ein Vektor der Länge `0` heisst **leerer Vektor**. 
:::

Der leere Vektor wird endweder als $\varnothing$ oder als $\{\}$ geschrieben. Beide Schreibweisen sind gleichwertig.

Der leere Vektor ist eine besondere Datenstruktur, die keine Elemente enthält. Der leere Vektor kann als *Startwert* für die Konstruktion von Vektoren verwendet werden oder als *Ergebnis* von Operationen auf Vektoren vorkommen.

## Sequenzen {#sec-sequenzen}

Eine besondere Gruppe von Vektoren sind Sequenzen. Sequenzen sind Vektoren deren Werte der Ordnung des Wertebereichs folgen. 

$$
v_i < v_{i+1}, \text{wenn aufsteigende Reihenfolge} \\\
v_i > v_{i+1}, \text{wenn absteigende Reihenfolge}
$$ {#eq-sequenz-sortiert-bedingung}

Eine Sequenz erfordert also immer einen *ordinalen Wertebereich*.

::: {.callout-warning}
## Sequenzen in den Life Sciences

In den Life Sciences werden *zusammenhängende Abfolgen von Werten* als Sequenzen bezeichnet. In diesen Sequenzen ist die *Reihenfolge* der Werte in diesen Sequenzen von Interesse. Solche Sequenzen haben nicht zwingend einen ordinalen Wertebereich und werden in der Regel als eigenständige Werte und nicht als Vektoren behandelt.
::: 

Nachfolgend werden nur Sequenzen vom Datentyp *Zahl* behandelt.

::: {#def-lineare-sequenz}
Eine **lineare Sequenz** ist ein Vektor, bei dem die Werte aufeinanderfolgender Indizes immer den gleichen Abstand haben.
:::

Deshalb gilt für lineare Sequenzen @eq-sequenz-diff.

$$
v_{i+1} - v_i = v_{j+1} - v_j
$$ {#eq-sequenz-diff}

::: {.callout-warning}
## Konvention

Für die praktische Anwendung sind lineare Sequenzen von zentraler Bedeutung. Deshalb wird im Folgenden der Begriff *Sequenz* synonym für *lineare Sequenz* verwendet. Alle anderen Sequenzen werden als Reihenfolgen bezeichnet oder explizit hervorgehoben. 
:::

::: {#def-schrittweite}
Der *Abstand einer Sequenz* wird als **Schrittweite** bezeichnet. Wird keine Schrittweite für eine Sequenz angegeben, wird die Schrittweite `1` angenommen. 
:::

::: {#def-anfangswert} 
Der **Anfangswert** einer Sequenz wird auch  **Startwert** oder **Initialwert** genannt. Wird kein Anfangswert für eine Sequenz angegeben, dann wird der Wert `1` angenommen.
:::


::: {#exm-festelänge}
## Anfangswert

Eine Sequenz mit der Länge 5 entspricht dem Vektor `{1,2,3,4,5}`.
:::

::: {#exm-länge-schrittweite}
## Länge und Schrittweite
Eine Sequenz mit der Schrittweite 3 und der Länge 4 entspricht dem Vektor `{1,4,7,10}`.
::: 

::: {#exm-startwert-länge}
## Startwert und Länge

Eine Sequenz mit dem Startwert 3 und der Länge 6 entspricht dem Vektor `{3,4,5,6,7,8}`.
::: 

::: {#exm-startwert-schrittweite-länge}
## Startwert, Schrittweite und Länge

Eine Sequenz mit dem Startwert 3, der Schrittweite 3 und der Länge 10 entspricht dem Vektor `{3,6,9,12,15,18,21,24,27,30}`.
:::

::: {.callout-note}
## Merke

Eine Sequenz mit gleichem Anfangswert und Schrittweite entspricht der jeweiligen Multiplikationsreihe. Der Startwert und die Indizes der Sequenz sind hierbei den Multiplikatoren. 
:::

### Besondere Sequenzen

::: {#def-einheitsvektor}
Der **Einheitsvektor** ist ein Vektor mit der geometrischen Länge 1.
::: 

Der *Einheitsvektor* ist *keine* Sequenz, weil die Werte der Indizes nicht mit der gleichen Schrittweite ansteigen.

::: {#def-nullvektor} 
Ein Vektor mit beliebiger Länge heisst **Nullvektor**, wenn an allen Indizes der Wert `0` steht. 
:::

Der *Nullvektor* ist damit eine besondere Sequenz, bei der der Startwert und die Schrittweite `0` ist.

Ein zweiter Vektor mit der Schrittweite `0` ist der *Einsvektor*. 

::: {#def-einsvektor}
Der **Einsvektor** ist ein Vektor mit beliebiger Länge mit dem Wert `1` bei jedem Index. 
:::

Der *Einsvektor* ist damit eine besondere Sequenz, mit dem Startwert `1` und der Schrittweite `0`.

In der mathematischen Literatur wird der *Einsvektor* oft nicht benannt. Wegen der besonderen Bedeutung dieses Vektors für verschiedene Operationen, wird diese Sequenz hier benannt.

::: {.callout-important}
Der **Einsvektor** darf nicht mit dem **Einheitsvektor** verwechselt werden. Im Gegensatz zum Einsvektor hat der *Einheitsvektor* die geometrische Länge $1$. Der Einsvektor der Länge `3` hat etwa die geometrische Länge von $\sqrt{3} \approx 1.7321$
:::

## Konkatenation {#sec-konkatenation}

Datenvektoren können zu neuen Vektoren zusammengefügt werden. Dieser Vorgang heisst **Konkatenation**. Dabei werden zwei Vektoren vom **gleichen Datentyp** *hintereinander* aneinandergehängt.

Bei der Konkatenation muss die Bedingung des **gleichen Datentyps** zwingend erfüllt sein. Eine Konkatenation von Vektoren mit unterschiedlichen Datentypen ist unzulässig, weil die resultierende Datenstruktur kein Vektor mehr wäre.

> ::: {#exm-konkatenation}
> ## Konkatenation
> 
> Die Konkatenation der Vektoren $v = \{1;2;3\}$ und $w = \{4;5;6\}$ ergibt einen neunen Vektor $v \circ w.$ Es gilt dabei die folgende Vorgehensweise:
>
> $$ 
> v\circ w = \{1;2;3\} \circ \{4;5;6\} = \{1;2;3;4;5;6\}
> $$
> ::: 

Der leere Vektor ist das neutrale Element der Konkatenation. D.h. die Konkatenation eines Vektors mit dem leeren Vektor ergibt den ursprünglichen Vektor. Es gilt als @eq-konkatenation-leerer-vektor.

$$
v \circ \varnothing = \varnothing \circ v = v
$$ {#eq-konkatenation-leerer-vektor}

Ein Skalar kann als Vektor mit der Länge `1` aufgefasst werden. Die Konkatenation eines Vektors mit einem Skalart ergibt einen Vektor, der um `1` länger als der ursprüngliche Vektor ist.  Es gilt also @eq-konkatenation-einzelner-wert.

$$
v \circ a \Leftrightarrow v \circ \{ a \}
$$

$$
\begin{aligned}
v \circ a &= \{v_1; v_2; \dots; v_n\} \circ a \\
&= \{v_1; v_2; \dots; v_n\} \circ \{a\} \\
&= \{v_1; v_2; \dots; v_n; a\}
\end{aligned}
$$ {#eq-konkatenation-einzelner-wert}

Weil die Reihenfolge der Konkatenation bedeutungsvoll ist, kann ein einzelner Wert auch *vor* einem Vektor angefügt werden.

$$
\begin{aligned}
a \circ v &= a \circ \{v_1; v_2; \dots; v_n\} \\
&= \{a\} \circ \{v_1; v_2; \dots; v_n\}  \\
&= \{a; v_1; v_2; \dots; v_n\}
\end{aligned}
$$ 

## Transformationen

::: {#def-transformation}
Eine **Transformation** bezeichnet eine Umformung der Element eines Vektors, wobei die Länge des Vektors unverändert bleibt. 
::: 

Eine Transformation erfordert also immer eine Funktion, die auf die Elemente des Vektors angewandt wird. Diese Funktion wird für jedes Element des Vektors separat ausgeführt. Dadurch ist sichergestellt, dass es für jedes Element des Vektors genau ein Ergebnis gibt.

::: {.callout-note}
## Merke

Beim Transformieren sind alle Operationen auf die Elemente eines Vektors **unabhängig** voneinander und die Ergebnisse beeinflussen sich nicht gegenseitig.
:::

Beim Transformieren kann der Datentyp eines Vektors verändert werden.

### Transformationen mit einem Skalar

Eine Transformation mit einem Skalar wird auch als **Skalierung** bezeichnet.

Für die Skalierung eines Vektors ist eine Transformationsfunktion mit zwei Parametern erforderlich. Beim Skalieren wird die Transformationsfunktion mit dem Skalar mit jedem Element des Vektors separat durchgeführt. 

Es gilt also die Logik der @eq-transformation-mit-skalar. Der Operator $\circ$ ist hier der Platzhalter für die Transformationsfunktion.

$$
\begin{aligned}
s \circ v &= s \circ \{v_1; v_2; \dots; v_n\} \\
&= \{s \circ v_1; s \circ v_2; \dots; s \circ v_n\}
\end{aligned}
$$ {#eq-transformation-mit-skalar}


> ::: {#exm-skalierung-mit-zahlen}
> ## Skalierung mit Zahlen
> 
> Die Skalierung eines Vektors $v = \{1;2;3\}$ mit dem Skalar $s = 2$ ergibt den Vektor $v' = \{3;4;5\}$. Es gilt dabei die folgende Vorgehensweise:
> 
> $$
> \begin{aligned}
> s + v &= 2 + \{1;2;3\} \\
> &= \{2 + 1; 2 + 2; 2 + 3\} \\
> &= \{3; 4; 5\}
> \end{aligned}
> $$
>
> Diese Vorgehensweise wird als Skalaraddition bezeichnet. Die Skalaraddition ist eine Transformation mit einem Skalar und der Addition als Transformationsfunktion. 
>
> Analog zur Skalaraddition gibt es die Skalarmultiplikation. Bei der Skalarmultiplikation wird die Multiplikation als Transformationsfunktion verwendet. Die Skalarmultiplikation wird wie folgt durchgeführt.
>
> $$
> \begin{aligned}
> s \cdot v &= 2 \cdot \{1;2;3\} \\
> &= \{2 \cdot 1; 2 \cdot 2; 2 \cdot 3\} \\
> &= \{2; 4; 6\}
> \end{aligned}
> $$
> ::: 

### Transformationen mit einem Vektor

Die Transformation mit einem Skalar kann auf Vektoren erweitert werden. Dabei wird die Transformationsfunktion mit den Elementen eines zweiten Vektors anstelle des Skalars durchgeführt. Eine solche Transformation erfordert, dass die Werte der beiden Vektoren *paarweise* durch die Transformationsfunktion verknüpft werden. Damit solche paarweisen Operationen möglich sind, müssen die beiden Vektoren die *gleiche Länge* haben. 

::: {.callout-note}
## Merke

Die Skalar-Transformation kann nur mit einem Vektor der Länge 1 *oder* mit einem Vektor mit der gleichen Länge wie der zu transformierende Vektor durchgeführt werden.
:::

Dann gilt die Logik der @eq-transformation-mit-vektor. Der Operator $\circ$ ist hier der Platzhalter für die Transformationsfunktion.

$$
\begin{aligned}
v \circ w &= \{v_1; v_2; \dots; v_n\} \circ \{w_1; w_2; \dots; w_n\} \\
&= \{v_1 \circ w_1; v_2 \circ w_2; \dots; v_n \circ w_n\}
\end{aligned}
$$ {#eq-transformation-mit-vektor}

> ::: {#exm-vektoraddition}
> ## Vektoraddition
> 
> Für die beiden gleichlangen Vektoren $v = \{1;2;3\}$ und $w = \{4;5;6\}$ wird die Vektoraddition paarweise durchgeführt.
>
> $$
> \begin{aligned}
> v + w &= \{v_1; v_2; v_3\} + \{w_1; w_2; w_3\} \\
> &= \{1;2;3\} + \{4; 5; 6\} \\
> &= \{1 + 4; 2 + 5; 3 + 6\} \\
> &= \{5; 7; 9\}
> \end{aligned}
> $$
>
> Deutlicher wird diese Mechanik, wenn die Vektoren als Spaltenvektoren geschrieben werden.
>
> $$
> \begin{aligned}
> v + w &= \begin{pmatrix} v_1 \\ v_2 \\ v_3 \end{pmatrix} + \begin{pmatrix} w_1 \\ w_2 \\ w_3 \end{pmatrix} \\ \\
> &= \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix} + \begin{pmatrix} 4 \\ 5 \\ 6 \end{pmatrix} \\ \\
> &= \begin{pmatrix} 1 + 4 \\ 2 + 5 \\ 3 + 6 \end{pmatrix} \\ \\
> &= \begin{pmatrix} 5 \\ 7 \\ 9 \end{pmatrix}
> \end{aligned}
> $$
> :::

## Aggregationen

::: {#def-aggregation}
Eine **Aggregation** ist eine *Funktion*, die Elemente eines Vektors zusammenfasst. Durch aggregieren kann sich die Länge des Vektors verändern.
:::

Eine Aggregationsfunktion heisst *Aggregator*. Aggregatoren haben in der Regel nur einen Parameter, der ein Vektor ist. Ein Aggregator wendet eine zweite Funktion auf die Elemente des Vektors an. Diese zweite Funktion heisst *Reduktionsfunktion*. Die Reduktionsfunktion legt fest, *wie* die Elemente des Vektors zusammengefasst werden. 

::: {.callout-note}
## Merke

Beim Aggregieren hängen die Operationen von der jeweiligen vorangehenden Operation ab. Die einzelnen Operationen sind voneinander **abhängig** und die Ergebnisse beeinflussen sich gegenseitig.
:::

> ::: {#exm-aggregation-reduktion}
> ## Aggregation und Reduktion beim Summieren
>
> Der $\sum{}$-Operator ist ein Aggregator. Die dem Operator nachfolgenden Terme legen die zu aggregierenden Vektorelement fest. Die Reduktionsfunktion ist die Addition (`+`). 
>
> Für den Vektor $v = \{1;2;3;4;5\}$ kann die die Summe der Quadrate wie folgt geschrieben werden.
>
> $$
> \sum_{i=1}^5 v_i^2
> $$
>
> Diese Schreibweise legt fest, dass die Vektorelemente quadriert werden müssen. Dabei handelt es sich um eine Transformation mit einem Skalar (`2`) und der Potenz als Transformationsfunktion. Diese vorgelagerte Transformation erzeugt einen impliziten Vektor mit den quadrierten Elementen $\{1, 4, 9, 16, 25\}$. 
>
> Die Reduktionsfunktion der Summe ist die Addition (`+`). Beim Reduzieren werden die Elemente des impliziten Vektors nacheinander addiert. Dabei wird das Element mit dem bisherigen Ergebnis *reduziert*. Beim ersten Schritt liegt noch kein Ergenis vor, weshalb das Element direkt übernommen wird. Dadurch ergeben sich in diesem Beispiel die folgenden Reduktionsschritte. 
>
> $$
> \begin{aligned}
> \sum{v^2} = \sum_{i=1}^5 v_i^2 &= 1^2 + 2^2 + 3^2 + 4^2 + 5^2 \\
> &= 1 + 4 + 9 + 16 + 25 \\
> &= 5 + 9 + 16 + 25 \\
> &= 14 + 16 + 25 \\
> &= 30 + 25 \\
> &= 55
> \end{aligned}
> $$
>
> Die Summe der Quadrate des Vektors $v$ ist also $55$.
> :::

Im @sec-filtern wurden Filter als Funktionen eingeführt, die Werte aus Vektoren mithilfe eines logischen Ausdrucks auswählen. Das Filtern ist eine spezielle Aggregation, bei dem die ursprünglichen Werte unverändert bleiben, aber die Länge des Vektors verändert wird. Anders als die Summe, liefert das Filtern einen Vektor und keinen einzelnen Wert als Ergebnis. Beim Filtern wird die Reduktionsfunktion als *Selektionsfunktion* bezeichnet. Die Selektionsfunktion fügt einen Wert dem Ergebnisvektor durch *Konkatenation* hinzu, wenn der logische Ausdruck `Wahr` ergibt. Der Startwert für die Reduktion ist beim Filtern der *leere Vektor*.

## Zählen

::: {#def-umfang} 
Als **Umfang** bezeichnen wir die Anzahl der Elemente eines Vektors oder einer Liste.
:::

::: {#def-zählen}
**Zählen** bezeichnet das Bestimmen der Anzahl von Elementen eines Vektors oder einer Liste.
::: 

Die Anzahl der Elemente eines Vektors ist immer gleich der Länge des Vektors. Deshalb kann der Umfang eines Vektors direkt aus der Länge des Vektors abgelesen werden.

::: {.callout-note}
## Mathematik vs. Datenwisssenschaft

In der Mathematik (Mengenlehre) existiert das Konzept der **Abzählbarkeit**. Dieses Konzept wird auf *beliebige* und insbesondere unendliche Mengen angewandt, um deren abstrakte Umfänge zu vergleichen. 

Beim Rechnen und Problemlösen mit Computern liegen **immer** mit **speziellen, endlichen** Strukturen vor. Damit muss beim Zählen immer die Frage nach dem *konkreten Umfang* der vorliegenden Elemente beantwortet werden.
:::

Nicht immer muss der Umfang des gesamten Vektors bestimmt werden. Stattdessen sollen einzelne Elemente eines Vektors gezählt werden, die bestimmte Bedingungen erfüllen.  Eine solche Bedingung wird immer als **logischer Ausdruck** formuliert.

::: {#def-zählbare-einheit}
 Eine **zählbare Einheit** bezeichnet ein Element, für das eine Zählbedingung `Wahr` ergibt. Eine **nicht zählbare Einheit** bezeichnet ein Element, für das eine Zählbedingung `Falsch` ergibt. 
:::

- Eine **zählbare Einheit** wird durch den Wert `1` (oder `Wahr`) repräsentiert. Ein zählbares Element wird gezählt.
- Eine **nicht-zählbare Einheit** wird durch den Wert `0` (oder `Falsch`) repräsentiert. Diese Elemente werden nicht gezählt.

### Zählen durch Summieren

Beim Zählen durch Summieren geht eine Transformation in die Werte `0` und `1` mithilfe eines logischen Ausdurcks einer Summen-Aggregation unmittelbar voraus.

Gelegentlich werden nicht alle Elemente einer Datenstruktur gezählt, sondern nur diejenigen, die bestimmte Bedingungen erfüllen.

::: {#def-abzählen}
Es wird vom **Abzählen** gesprochen, wenn zum Zählen eine **Summe über die zählbaren Einheiten** gebildet wird. 
:::

Dabei wird ausgenutzt, dass die Summe über einen Vektor von `0` und `1` die Anzahl der `1`-Werte ergibt.

::: {.callout-note}
## Merke

Immer wenn eine Summe über einen Vektor von `0` und `1` gebildet wird, wird eine Zählen-Operation vorbereitet.
::: 

Die Transformation in die Werte `0` und `1` durch einen logischen Ausdruck wird als **Indikatorfunktion** bezeichnet. Die Indikatorfunktion ist eine Transformation mit einem logischen Ausdruck. Eine solche Funktion kann für nachgelagerte arithmetische Transformations-Operationen als Ersatz für eine vorgelagerte Entscheidung verwendet werden. In solchen Fällen wird das Ergebnis der Indikatorfunktion über eine Skalar-Multiplikation mit der nachgelagerten Operation verknüpft. Dabei stellt die Indikatorfunktion sicher, dass der Vektor die gleiche Länge wie die nachgelagerte Operation hat.

### Zählen durch Filtern

Beim Zählen durch Filtern wird die Summe über die zählbaren Einheiten durch eine Filter-Aggregation zusammegefasst. Nach dem Filtern bleibt ein Vektor mit den zählbaren Einheiten übrig, der keine nicht-zählbaren Elemente enthält. Die Länge dieses Vektors entspricht der Anzahl der zählbaren Einheiten.

::: {.callout-note}
## Merke

Werden die zählbaren Einheiten durch einen Filter ausgewählt, dann entspricht die Summe der zählbaren Einheiten der Länge des gefilterten Vektors.
:::

Weil das Filtern die Länge des Vektors verändert, kann das Filtern **nicht** als *Indikatorfunktion* verwendet werden.

### Zählen durch Nummerieren

Beim Nummerieren wird eine Sequenz erzeugt, die für jede zählbare Einheit einen Wert enthält. Die Länge dieser Sequenz entspricht der Anzahl der zählbaren Einheiten. Gleichzeitig entspricht der Maximal-Wert der Sequenz ebenfalls der Anzahl der zählbaren Einheiten.

::: {.callout-note}
## Merke
Wenn die zählbaren Einheiten durchnummeriert werden, dann entspricht der Umfang dieser Einheiten der grössten Nummerierung (dem Maximum).
:::

Nummerierungen werden häufig verwendet, um einzelnen Datensätzen eindeutige Identifikatoren zuzuweisen. Diese Nummerierungen können zum Zählen leicht benutzt werden.
