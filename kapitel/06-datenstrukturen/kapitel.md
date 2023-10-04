---
# NOT USED
execute: 
  echo: false
---

## Datenstrukturen {#sec-chapter-datenstrukturen}

Aus fundamentalen Datentypen können *komplexe Datentypen* zusammengesetzt werden, um mehrere Werte zusammenzufassen. Komplexe Datentypen können ausserdem wiederum komplexe Datentypen enthalten. So lassen sich komplexe Strukturen bilden.

::: {#def-datenstruktur}
Eine **Datenstruktur** ist ein Datentyp, in dem mehrere Werte zusammengefasst werden können.
:::

Weil eine Datenstruktur ebenfalls ein Datentyp ist, lässt sie sich wie ein einzelner Wert behandeln. Dadurch haben Datenstrukturen eine Reihe von Vorteilen: 

- Datenstrukturen können als *Einheit* behandelt werden.
- Datenstrukturen können *verschachtelt* werden, um noch komplexere Strukturen zu bilden.
- Datenstrukturen können als Sammlung von Einzelwerten betrachtet werden, welche getrennt verarbeitet werden können.

Durch diese Eigenschaften sind Datenstrukturen besonders gut für die Datenorganisation geeignet. 

*Datenfelder* (engl. *arrays*) sind eine besondere Datenstruktur. Datenfelder fassen Werte so zusammen, dass jeder Wert eine *eindeutige Position* hat. Die Position eines Wertes wird durch einen *Index* angegeben. Die Anzahl der Werte in einer Datenstruktur ist deren **Länge**. Die Länge und die Idizes einer Datenstruktur sind natürliche Zahlen.

Über die zusammengefassten Datentypen lassen sich zwei Arten von Datenfeldern unterscheiden.

::: {#def-vektor}
**Vektoren** sind Datenfelder mit Werten vom *gleichen Datentyp*. 
:::

Weil alle Werte in einem Vektor vom gleichen Datentyp sind, sind Vektoren *homogene Datenstrukturen*.

::: {#def-liste}
**Listen** sind Datenfelder mit Werten mit *beliebigen Datentypen*.
:::

Weil die Datentypen der Listenwerte nicht festgelegt sind, sind Listen *heterogene Datenstrukturen*.

## Mehrdimensionale Datentypen: Geschachtelte Listen, Stichproben und Matrizen

Die Logik der komplexen Datentypen erlaubt es, Listen und Vektoren zu noch komplexeren Strukturen zu verknüpfen. 

::: {#def-geschachtelte-liste}
Eine **geschachtelte Liste** ist eine Liste, die aus beliebigen anderen Datenfeldern (d.h. Listen oder Vektoren) besteht, wobei die eingebetteten Datenfelder *unterschiedliche Längen* haben können.
:::

Ein **Spezialfall** der verschachtelten Liste sind **Listen, die Vektoren mit *gleicher Länge* schachteln**. Diese Spezialfälle haben besondere Namen: 

::: {#def-liste-komplex}
Eine **Datenrahmen** (engl. *data frame*) verknüpft mehrere gleichlange Vektoren mit *unterschiedlichen Datentypen*. 
:::

Ein Datenrahmen kann als eine Liste von Vektoren mit gleicher Länge verstanden werden. Diese Datenstruktur muss eine Liste sein, weil die einzelnen Vektoren unterschiedliche Datentypen haben können. Entsprechend gelten Datenrahmen ebenfalls als *hetreogene Datenstrukturen*.

::: {#def-matrix-structure}
Eine **Matrix** verknüpft mehrere gleichlange Vektoren vom Datentyp *Zahlen*. Die Länge der Vektoren einer Matrix muss mindestens 1 sein.
:::

Weil alle Vektoren in einer Matrix vom gleichen Datentyp sind, sind Matrizen *homogene Datenstrukturen*. 

Eine Matrix hat eine Höhe (oft als *m* Zeilen gekennzeichnet) und eine Breite (oft als *n* Spalten gekennzeichnet). Die Anzahl der Zeilen und Spalten müssen natürliche Zahlen sein. Daraus folgt, dass nur Matrizen existieren, für die m und n > 0 gilt. 

Eine Matrix mit m Zeilen und n Spalten wird als $m \times n$-Matrix bezeichnet. Die Anzahl der Zeilen und Spalten einer Matrix sind ihre *Dimensionen*.

::: {.callout-note}
Die *Dimensionen* einer Matrix müssen beide $>0$ sein, aber sie müssen genau nicht gleich sein. Weil *m* und *n* einer Matrix grösser als `0` sein müssen, folgt daraus: **Vektoren** sind *spezielle Matrizen* mit m-Zeilen und *einer Spalte* (n = 1).
:::

::: {#def-quadratische-matrix}
Eine Matrix mit gleich vielen Spalten und Zeilen wird als **quadratische Matrix** bezeichnet. 
:::

Für eine quadratische Matrix gilt immer $m = n$.

Der Wert an einer Position in einer Matrix ist durch den Zeilen- und Spaltenindex eindeutig identifiziert.

$$
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\\
a_{21} & a_{22} & \cdots & a_{2n} \\\
\vdots & \vdots  & \ddots & \vdots \\\
a_{m1} & a_{m2} &  \cdots &  a_{mn}  
\end{bmatrix}
$$ 
