---
execute: 
  echo: false
---
# Daten umformen {#sec-chapter-daten-formen}

Viele Operationen der vorangegangenen Kapitel setzen eine vektorisierte Datenstruktur voraus. Echte Daten liegen aber meistens nicht in einem Vektor vor, sondern sind über mehrere Vektoren verteilt. Dadurch erscheinen viele Operationen komplexer als sie eigentlich sind. Durch das Umformen von Daten lassen sich viele Operationen stark vereinfachen und in der Ausführung beschleunigen. Die Grundlage vieler komplexer Algorithmen bilden Primär- und Sekundärindizes (@sec-chapter-indizieren-gruppieren). Das Ziel des Umformens ist es, Daten in eine Form zu bringen, die die effiziente Verwendung von Indizes und Gruppierungen ermöglicht.

::: {.callout-note}
## Merke
Das Umformen von Daten dient der Vereinfachung und Beschleunigung von Operationen.
:::

Oft werden nur einzelne Vektoren einer Datenstruktur und nicht die gesamte Datenstruktur umgeformt.

::: {.callout-important}
Alle Umformungen müssen umkehrbar sein, so dass für eine Datenstruktur $D$ die [Gleichung @eq-umformen-umkehrbar] gilt.
:::

$$
f_u(D) \triangleright f^{-1}_u() = f_{id}(D) = D
$$ {#eq-umformen-umkehrbar}

Lässt sich durch wiederholtes Umformen die ursprüngliche Datenstruktur nicht erzeugen, dann liegt eine **partielle Umformung** vor. 

::: {.callout-note}
## Merke
Jede *partielle Umformung* führt zu Informationsverlust durch *Äquivokation*.
:::

## Transponieren

::: {#def-transponieren}
**Transponieren** ist eine Operation, die Orientierung einer Datenstruktur ändert. 
:::

Es gibt zwei Arten des Transponierens.

1. Das Transponieren von Matrizen, bei dem die Zeilen und Spalten vertauscht werden. Dabei bleibt die grundsätzliche Struktur der Daten erhalten. 
2. Das Transponieren von Daten, bei mehreren Vektoren zu einem Vektor zusammengefasst werden oder ein Vektor in mehrere Vektoren aufgegliedert wird. Weil sich die Struktur der Daten verändert, wird diese Operation auch als **Reshaping** oder **Pivoting** bezeichnet.

@sec-chapter-matrix-operationen zeigt das Transponieren von **Matrizen**. Bei dieser Operation werden die Zeilen- und die Spaltenindizes vertauscht. Diese Operation darf nur auf Matrizen angewandt werden. Jede Matrix kann transponiert werden. Wird eine transponierte Matrix noch einmal transponiert, dann ist das Ergebnis die ursprüngliche Matrix. Daraus folgt, dass das Transponieren immer *umkehrbar* ist.

Die zweite Art des Transponierens wird auf **Datenrahmen** angewendet. 

Beim Transponieren eines Datenrahmens wird zwischen der **Vektorform** bzw. *Langform* und der **Matrixform** bzw. *Breitform* unterschieden. Es ist üblich, dass beim Transponieren nicht alle Vektoren des Datenrahmens transponiert werden. Für die nicht transponierten Vektoren gilt, dass diese Werte in der Langform für jeden transponierten Wert wiederholt werden und in der Breitform gleiche Werte zu einem Wert zusammengefasst werden. Dabei gilt, dass ein Primärindex der *Matrixform* zum Sekundärindex der *Vektorform* wird und umgekehrt. 

Die Breitform verteilt die Werte über mehrere Vektoren. In der Langform sind diese Werte in *einem* Vektor mit zusätzlichen Sekundärindex zusammengefasst. 

> ::: {#exm-transponieren-breitform}
> ## Transponieren durch Auffächern
>
> Die Ausgangsstichprobe in der Langform hat zwei Vektoren. Im ersten Vektor (`Namen`) stehen die Vektornamen der aufgefächerten Stichprobe. Es werden also die Werte entlang dieses Vektors aufgefächert. Im zweiten Vektor (`Werte`) stehen die Werte, die in die neuen Vektoren übernommen werden.
> 
> | Namen | Werte | 
> | :--- | ---: |
> | v1 | 1 |
> | v1 | 2 |
> | v2 | 3 |
> | v3 | 4 |
> | v2 | 5 |
> | v3 | 6 | 
> | v1 | 7 |
> | v2 | 8 |
> 
> Durch das Auffächern werden die Werte entsprechend den Werten im Namensvektor auf neue Vektoren aufgeteilt. Wir transponieren also entlang der Namen. So erhalten wir die Breitform der Stichprobe. 
> 
> | v1 | v2 | v3 |
> | ---: | ---: | ---: |
> | 1 | 3 | 4 |
> | 2 | 5 | 6 |
> | 7 | 8 |  |
> 
> Beachten Sie, dass der letzte Wert im Vektor v3 fehlt, weil in der Langform nur zwei Werte diesem Namen zugewiesen waren. 
> :::

Beim Transponieren in die Vektorform werden mehrere Vektoren zu einem Vektor zusammengefasst und die Vektornamen als ein neuer Sekundärindex für diese Werte erzeugt. 

> ::: {#exm-transponieren-breitform}
> ## Transponieren durch Zusammenfächern
> 
> Beim Transponieren durch Zusammenfächern werden alle Werte aus einer Auswahl von Vektoren in separate Datensätze umgewandelt. Für ein einfaches Beispiel sei die folgende Kostenstichprobe in der Breitform gegeben. 
> 
> | Monat | Einkauf | Verkauf | Kosten |
> | :--- | ---: | ---: | ---: |
> | Mai | -1000 | 50 | -5000 |
> | Juni | -50 | 50 | -5000 |
> | Juli | -50 | 17000 | -5000 |
> 
> In diesem Beispiel transponieren wir entlang der Vektoren `Einkauf`, `Verkauf` und `Kosten` und fassen die Werte zu einem Vektor `Betrag` in der Langform zusammen. Weil wir nach dem Transponieren keine Information verlieren dürfen, müssen wir für jeden Wert auch den zugehörigen Vektornamen in der Langform abbilden. Daraus ergibt sich die folgende Langform.
> 
> | Monat | Betrag | Art | 
> | :--- | ---: | :--- |
> | Mai | -1000 | Einkauf | 
> | Mai | 50 | Verkauf | 
> | Mai | -5000 | Kosten |
> | Juni | -50 | Einkauf | 
> | Juni | 50 | Verkauf | 
> | Juni | -5000 |  Kosten |
> | Juli | -50 | Einkauf | 
> | Juli | 17000 | Verkauf | 
> | Juli | -5000 |  Kosten |
> 
> In diesem Beispiel erkennen wir, dass die Werte, der nicht transponierten Vektoren in der Langform der Stichprobe mehrfach auftreten.
> :::

::: {.callout-note}
## Merke (Voraussetzung für die Vektorform)
Vektoren von Datenrahmen können nur in die Vektorform transponiert werden, wenn alle Vektoren vom gleichen Datentyp sind.
:::

Beim Transponieren in die Matrixform wird ein Sekundärindex verwendet, um Werte eines Vektors mehreren neuen Vektoren zuzuweisen. Die Werte des Sekundärindex werden anschliessend als Vektornamen verwendet. 

::: {.callout-note}
## Merke (Voraussetzung)
Ein Vektor und sein Sekundärindex kann nur in die Matrixform transponiert werden, wenn sich alle Werte eindeutig Datensätzen zuordnen lassen.
:::

Beim Transponieren von Datenrahmen muss beachtet werden, dass nicht Langform eine korrespondierende Breitform hat, weil aus der *Vektorform* nicht immer eindeutig hervorgeht, wie die *Matrixform* aufgebaut ist. Deshalb ist das Transponieren von Datenrahmen nur dann umkehrbar, wenn sich der transponierte Datenrahmen ebenfalls die Voraussetzung für das Transponieren erfüllt.

::: {.callout-tip}
## Praxis
Um die Umkehrbarkeit des Transponierens sicherzustellen, werden zusätzliche Indexvektoren eingesetzt.

Beim Transponieren von Datenrahmen empfiehlt sich beim Transponieren in die *Langform* ein **Primärindex**, der in der Langform zu einem zusätzlichen Sekundärindex erweitert wird. 

Beim Transponieren eines Datenrahmen in die *Breitform* empfiehlt sich ein **zweiter Sekundärindex**, der in der Breitform zum Primärindex reduzierbar ist.
:::

Die *Vektorform* muss nicht zwingend die gleiche Anzahl Werte haben, wie die *Matrixform*. Die *Vektorform* kann auch *weniger Werte* als die *Matrixform* haben.

::: {#def-kurze-vektorform}
Enthält eine Vektorform weniger Werte als ihre Matrixform, dann wird sie als **kurze Vektorform** bezeichnet.
:::

Beim Transponieren einer *Vektorform* mit weniger Werten als die *Matrixform*, werden die fehlenden Werte aufgefüllt. Dadurch werden neue Werte erzeugt, die nicht in den ursprünglichen Daten enthalten waren.

::: {.callout-note}
## Merke
Das Transponieren einer kurzen Vektorform in ihre Matrixform erzeugt neue Werte und führt zu Informationsverlust durch *Rauschen*.
:::

Dieses Rauschen ist jedoch kontrollierbar, wenn diese Eigenschaft bei der Umformung berücksichtigt wird.

## Hierarchisieren

Nicht immer sind alle umzuformenden Vektoren vom gleichen Datentyp. In diesem Fall können die Werte nicht transponiert werden. Stattdessen müssen die Vektoren in eine hierarchische Datenstruktur überführt werden.

::: {#def-hierarchisieren}
Das Hierarchisieren ist eine Operation, bei der Daten in eine hierarchische Datenstruktur überführt werden.
:::

Die wichtigste Operation beim Hierarchisieren ist das **Einbetten** von Daten. Das Einbetten von Daten ist eine wichtige Operation, um Daten zu strukturieren und zu organisieren. Es bildet die Grundlage für **komplexe Datenstrukturen** mit baumartigen Datenstrukturen (s. [@sec-mengen-und-baeume]). Diese Umformung ist auch als **nesting** bekannt.

::: {.callout-note}
## Merke
Beim Einbetten können die umgeformten Vektoren unterschiedliche Datentypen haben.
:::

Beim Einbetten werden die umgeformten Vektoren entlang eines Sekundärindex gruppiert. Anschliessend werden die gruppierten Vektoren in Teilstichproben getrennt und aus der ursprünglichen Datenstruktur entfernt. Die Teilstichproben enthalten nur die umzuformenden Vektoren. Weil die resultierende Datenstrukturen für alle Gruppen gleich sind, können die Teilstichproben zu einem Vektor zusammengefasst werden.

Weil alle Einträge des Sekundärindex in den neuen Vektor mit den Teilstichproben verlagert wurde, kann der Sekundärindex so reduziert werden, dass jeder *Hash* genau einmal vorkommt. Dadurch hat der Vektor des Sekundärindex die gleiche Länge wie der Vektor mit den Teilstichproben. Die beiden Vektoren können zu einem Datenrahmen zusammengefasst werden, so dass jeder Indexwert mit der zugehörigen Teilstichprobe einen Datensatz bildet. 

Die resultierende Datenstruktur ist eine hierarchische Datenstruktur, die aus einem Vektor von Datenrahmen besteht. In der neuen, eingebetteten Struktur kommen die Indexwerte nur noch einmal vor. Daraus folgt, dass der Sekundärindex in einen Primärindex überführt wurde.

