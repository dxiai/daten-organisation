---
# bibliography: references.bib
execute: 
  echo: false
---

# Matrix-Operationen {#sec-chapter-matrix-operationen}

Matrizen sind für die Datenwissenschaften eine besondere Datenstruktur. In diesem Kapitel wird @def-matrix-structure erweitert, um die wichtigsten Matrixoperationen zu behandeln.

Für Matrizen gelten etwas andere Regeln als für einzelne Werte. Bei genauer Betrachtung lässt sich feststellen, dass es sich dabei um Verallgemeinerungen der bekannten Rechenregeln handelt. 

Dazu stellen wir uns vor, dass ein einzelner Wert auch als eine 1x1-Matrix dargestellt werden kann. 1x1-Matrizen sind gleichzeitig die kleinsten quadratischen Matrizen.

::: {.callout-note}
Für alle Rechenregeln muss beachtet werden, dass die Grösse aller verwendeten Matrizen für die jeweilige Operation entscheidend ist. 
:::

## Grundbegriffe

::: {#def-matrix-hauptdiagonale}
Die **Hauptdiagonale** einer Matrix sind alle Positionen mit gleichen Zeilen- und Spaltenindizes.
::: 

::: {#def-symmetrische-matrix}
Eine **symmetrische Matrix** ist eine quadratische Matrix, die bezüglich der Hauptdiagonalen symmetrisch ist.
:::

Daraus folgt, dass die Werte einer symmetrischen Matrix an einer Position $(i, j)$ gleich den Werten an der Position $(j, i)$ sind.

::: {#exm-symmetrische-matrix}
## Symmetrische Matrix

$$
\begin{bmatrix}
1 & 0 & 6 & 4 & 9 \\
0 & 2 & 2 & 6 & 14 \\
6 & 2 & 3 & 7 & 8 \\
4 & 6 & 7 & 4 & 9 \\
9 & 14 & 8 & 9 & 5
\end{bmatrix}
$$ 
:::

::: {#def-diagonalmatrix}
Eine **Diagonalmatrix** hat nur Werte auf der Hauptdiagonalen. Alle anderen Werte sind `0`.
::: 

::: {#def-einheitsmatrix}
Die **Einheitsmatrix** ist eine Diagonalmatrix mit `1` entlang der Hauptdiagonalen.
:::

::: {#exm-einheitsmatrix-3-6}
## Einheitsmatrix mit 3 Zeilen und 6 Spalten

$$
\begin{bmatrix}
1 & 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0
\end{bmatrix}
$$
:::

::: {#def-identitaetsmatrix}
Die **Identitätsmatrix** ist eine quadratische Einheitsmatrix.
:::

Die Identitätsmatrix wird in Formeln als $I$ gekennzeichnet.

::: {#exm-identitätsmatrix}
## Identitätsmatrix

$$
\begin{bmatrix}
1 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$ 
:::

::: {#def-dreiecksmatrix}
Eine **Dreiecksmatrix** ist eine Matrix, die nur Werte unterhalb oder oberhalb der Hauptdiagonalen hat.
:::

Die Hauptdiagonale einer Dreiecks-Matrix wird nicht immer zum Wertebereich hinzugezählt. Je nach Anforderung, muss dieser Wertebereich entsprechend ein- oder ausgeschlossen werden.

::: {#exm-untere-dreiecksmatrix}
## Untere Dreiecksmatrix

$$
\begin{bmatrix}
1 & 0 & 0 & 0 & 0 \\
11 & 2 & 0 & 0 & 0 \\
6 & 2 & 3 & 0 & 0 \\
4 & 6 & 7 & 4 & 0 \\
9 & 14 & 8 & 9 & 5
\end{bmatrix}
$$ 
:::

::: {#exm-obere-dreiecksmatrix}
## Obere Dreiecksmatrix

$$
\begin{bmatrix}
1 & 11 & 6 & 4 & 9 \\
0 & 2 & 2 & 6 & 14 \\
0 & 0 & 3 & 7 & 8 \\
0 & 0 & 0 & 4 & 9 \\
0 & 0 & 0 & 0 & 5
\end{bmatrix}
$$ 
:::


::: {#def-sparse-matrix}
Eine **dünnbesetzte Matrix** (oder *Sparse Matrix*) ist eine Matrix, die überwiegend `0`-Werte enthält.
:::

::: {#exm-sparse-matrix}
## Sparse Matrix

$$
\begin{bmatrix}
0 & 1 & 0 & 0 & 9 \\
0 & 0 & 2 & 6 & 0 \\
6 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 7 & 0 \\
0 & 4 & 0 & 3 & 0
\end{bmatrix}
$$ 
:::


::: {#def-transponierte-matrix}
Eine Matrix, welche die Werte einer anderen Matrix $A$ mit vertauschten Zeilen- und Spaltenindizes enthält, wird **transponierte Matrix** von $A$ genannt.
:::

Für die *transponierte Matrix von $A$* wird $A^T$ geschrieben.

::: {#exm-transponierte-matrix}
## Transponierte Matrix

$$
\begin{aligned}
A &= \begin{bmatrix}
1 & 0 \\
0 & 2 \\
6 & 2  \\
4 & 6  \\
9 & 7 
\end{bmatrix} \\\
\\
A^T &= \begin{bmatrix}
1 & 0 & 6 & 4 & 9 \\
0 & 2 & 2 & 6 & 7
\end{bmatrix}
\end{aligned}
$$ 
:::

Wir beachten, dass per Konvention der Zeilenindex immer als Erstes und der Spaltenindex immer als Zweites angegeben wird. Anstelle der mathematischen Schreibweise trennen wir die beiden Indizes. Auf diese Weise können wir auf jeden Wert in einer Matrix zugreifen. 

## Matrixaddition

Die Matrizenaddition addiert die Elemente zweier Matrizen *paarweise*. Damit die Addition funktioniert, muss es für jeden Wert in Matrix A einen Partnerwert in Matrix B mit gleichem Zeilenindex i und Spaltenindex j geben. Daraus folgt direkt, dass die Matrixaddition nur für Matrizen mit gleichen Dimensionen m und n definiert ist.

##  Vektoraddition

Die Vektoraddition funktioniert etwas anders als die Matrixaddition. In diesem Fall liegt uns eine m x n-Matrix und ein m-Vektor vor. 

Die Vektoraddition ist nur dann definiert, wenn die Matrix und der Vektor die gleiche Anzahl an Zeilen haben. 

Bei der Vektoraddition wird der Vektor zu jeder Spalte in der Matrix addiert. Dabei werden die Werte *paarweise* zusammengezählt. 

::: {#exm-matrix-vektoraddition}
## Vektoraddition eines 2-Vektor und eine 2 x 3-Matrix.

$$
\begin{aligned}
v + M &= \begin{bmatrix}
v_{1}  \\
v_{2} 
\end{bmatrix} + \begin{bmatrix}
m_{11} & m_{12}  & m_{13}  \\
m_{21} & m_{22} & m_{23}  
\end{bmatrix} \\\
\\
&= \begin{bmatrix}
v_1 + m_{11} & v_1 + m_{12}  & v_1 + m_{13}  \\
v_2 + m_{21} & v_2 + m_{22} & v_2 + m_{23}  
\end{bmatrix}
\end{aligned}
$$


## Skalarmultiplikation (Punktprodukt)

Die Skalarmultiplikation oder das Punktprodukt multipliziert einen Wert a mit einer Matrix (oder Vektor) M. Dabei wird \\( a \\) als **Skalar** bezeichnet, weil dieser alle Werte um den gegebenen Wert *skaliert*.  Bei der Skalarmultiplikation wird jeder Wert in der Matrix mit dem Skalar multipliziert. 

$$
\begin{aligned}
a \cdot M &= a \cdot \begin{bmatrix}
m_{11} & m_{12}  & m_{13}  \\
m_{21} & m_{22} & m_{23}  
\end{bmatrix} \\\ \\\ 
&= \begin{bmatrix}
a \cdot m_{11} & a \cdot m_{12}  & a \cdot m_{13}  \\
a \cdot m_{21} & a \cdot m_{22} & a \cdot m_{23}  
\end{bmatrix}
\end{aligned}
$$

Dieses Konzept lässt sich auf Vektoren übertragen. Dabei ist der Skalar a ein Vektor mit der gleichen Anzahl an Zeilen für den Vektor und die Matrix. Danach funktioniert die Skalarmultiplikation analog zur Vektoraddition. 

$$
\begin{aligned}
a \cdot M &= \begin{bmatrix}
a_1\\
a_2 
\end{bmatrix} \cdot \begin{bmatrix}
m_{11} & m_{12}  & m_{13}  \\
m_{21} & m_{22} & m_{23}  
\end{bmatrix} \\\ \\\
&= \begin{bmatrix}
a_1 \cdot m_{11} & a_1 \cdot m_{12}  & a_1 \cdot m_{13}  \\
a_2 \cdot m_{21} & a_2 \cdot m_{22} & a_2 \cdot m_{23}  
\end{bmatrix}
\end{aligned}
$$

## Matrixmultiplikation/ Kreuzprodukt

Das Kreuzprodukt ist eine andere Variante zwei Matrizen zu multiplizieren. Dabei werden zwei Matrizen A und B über Kreuz multipliziert. Dazu muss gegeben sein, dass die Matrix A gleich viel Spalten hat, wie Matrix B Zeilen. Es muss also gelten, dass wir eine m x n-Matrix mit einer n x p-Matrix multiplizieren, wobei n für beide Matrizen gleich sein muss. Sind diese Voraussetzungen nicht erfüllt, kann das Kreuzprodukt nicht gebildet werden.

Das Kreuzprodukt ist wie folgt definiert: 

$$
\begin{aligned}
A \times B &= \begin{bmatrix} 
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn} \\
\end{bmatrix} 
\times
\begin{bmatrix} 
b_{11} & b_{12} & \cdots & b_{1p} \\
b_{21} & b_{22} & \cdots & b_{2p} \\
\vdots & \vdots & \ddots & \vdots \\
b_{n1} & b_{n2} & \cdots & b_{np} \\
\end{bmatrix} \\\
\\\
&= \begin{bmatrix} 
\sum_{i=1}^{n}{a_{1i} \cdot b_{i1}} & \sum_{i=1}^{n}{a_{1i} \cdot b_{i2}} & \cdots & \sum_{i=1}^{n}{a_{1i} \cdot b_{ip}} \\
\sum_{i=1}^{n}{a_{2i} \cdot b_{i1}} & \sum_{i=1}^{n}{a_{2i} \cdot b_{i2}} & \cdots & \sum_{i=1}^{n}{a_{2i} \cdot b_{ip}} \\
\vdots & \vdots & \ddots & \vdots \\
\sum_{i=1}^{n}{a_{mi} \cdot b_{i1}} & \sum_{i=1}^{n}{a_{mi} \cdot b_{i2}} & \cdots & \sum_{i=1}^{n}{a_{mi} \cdot b_{ip}} \\
\end{bmatrix} 
\end{aligned}
$$

Das Ergebnis eines Kreuzprodukts ist immer eine Matrix mit m-Zeilen und p-Spalten.

Aus der Definition des Kreuzprodukts zeigt sich, dass die Operanden beim Kreuzprodukt nur vertauscht werden können, wenn beide Matrizen quadratisch sind. Dabei gilt für beliebige Matrizen ausserdem @eq-kreuzprodukt-nicht-kommutativ.

$$
A \times B \ne B \times A
$$ {#eq-kreuzprodukt-nicht-kommutativ}

Das Kreuzprodukt hat ein *neutrales Element*: Die **Identitätsmatrix** $I$.  Die Identitätsmatrix ist eine quadratische Matrix, die an den Positionen der abfallenden Diagonalen den Wert 1 und sonst den Wert 0 hat. 

::: {#exm-3d-id-matrix}
## 3-dimensionale Einheitsmatrix

$$
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$
:::

Für die Identitätsmatrix gilt @eq-id-matrix-kreuzprodukt.

$$
A \times I = I \times A = A
$$ {#eq-id-matrix-kreuzprodukt}

### Kreuzprodukt für Vektoren

Aus der Anforderung für das Kreuzprodukt folgt direkt das Kreuzprodukt für Vektoren, die wir als m x 1- sowie als 1 x p-Matrizen verstehen können. Es gilt also: n = 1. Deshalb mussten wir für das Einmaleins-Beispiel den zweiten Vektor *transponieren*. Dadurch vereinfacht sich die komplizierte Formel des Kreuzprodukts auf die paarweise-überkreuzte Multiplikation. 

### Inverse Matrix

::: {#def-inverse-matrix}
Die **inverse Matrix** $A^{-1}$ ist die Matrix, die mit der Matrix $A$ multipliziert die Identitätsmatrix $I$ ergibt. Es gilt also @eq-inverse-matrix.
:::

$$
A \times A^{-1} = A^{-1} \times A = I
$$ {#eq-inverse-matrix}

Die inverse Matrix kann nicht für beliebige Matrizen gebildet werden, sondern ist nur für bestimme quadratische Matrizen definiert. Die Inverse Matrix wird für verschiedene Anwendungen benötigt und wird deshalb von den meisten Softwarepaketen bereitgestellt. Es ist deshalb selten notwendig, eine inverse Matrix selbst zu berechnen.

### Anwendungen des Kreuzprodukts

#### Zeilen- und Spaltensummen berechnen

Für Zeilen- bzw. Spaltensummen werden drei Eigenschaften ausgenutzt: 

1. Vektoren lassen sich als $1 \times n$- bzw. $n \times 1$-Matrizen verstehen.
2. Das Ergebnis des Kreuzpodukts ist immer eine Matrix mit $m \times p$-Dimensionen. 
3. Das neutrale Element der Multiplikation ist `1`.

Weil für jede Ergebnisposition des Kreuzprodukts @eq-pos-summe-matrixprod gilt. 

$$
\sum_{i=1}^{n}{a_{ji} \cdot b_{ik}}
$$ {#eq-pos-summe-matrixprod}

Wird einer der beiden Parameter $a_{ji}$ oder $b_{ik}$ eins, dann reduziert sich dieser Term auf eine einfache Summe entsprechend @eq-pos-summe-matrixprod-eins.

$$
\sum_{i=1}^{n}{a_{ji} \cdot b_{ik}} = \sum_{i=1}^{n}{a_{ji} \cdot 1} = \sum_{i=1}^{n}{a_{ji}}
$$ {#eq-pos-summe-matrixprod-eins}

Für die Spalten- bzw. Zeilensumme soll jeweils ein Vektor bestimmt werden, der die Summe der Werte in der jeweiligen Zeile bzw. Spalte enthält. Dazu wird die Matrix mit einem geeigneten Einsvektor multipliziert.

Für die Spaltensumme, muss dieser Einsvektor die Länge der Anzahl der Zeilen haben. Für die Zeilensumme muss der Einsvektor die Länge der Anzahl der Spalten haben.

::: {#exm-spalten-summe}
## Spaltensumme für eine $3 \times 4$-Matrix
$$
\begin{bmatrix}
1 & 1 & 1
\end{bmatrix}
\times \begin{bmatrix}
3 & 6 & 2  &1 \\
4 & 3 & 2 & 1 \\
1 & 2 & 3 & 4 
\end{bmatrix} = 
\begin{bmatrix}
8 & 11 & 7 & 6
\end{bmatrix}
$$
:::

::: {#exm-zeilen-summe}
## Zeilensumme für eine $3 \times 4$-Matrix
$$
\begin{bmatrix}
3 & 6 & 2  &1 \\
4 & 3 & 2 & 1 \\
1 & 2 & 3 & 4 
\end{bmatrix} \times \begin{bmatrix}
1 \\
1 \\
1 \\
1
\end{bmatrix}= 
\begin{bmatrix}
12 \\ 10 \\ 10
\end{bmatrix}
$$
:::


#### Vorgänger- und Nachfolgersummen

Wird ein Vektor mit einer Dreiecks-Matrix multipliziert, dann werden die Vorgänger- bzw. Nachfolgerwerte addiert. 

::: {#exm-nachfolger-summe}
## Nachfolgersumme für einen Vektor der Länge 4

$$
\begin{bmatrix}3 &6 &2 &1\end{bmatrix} \times \begin{bmatrix}
1 & 0 & 0 & 0 \\
1 & 1 & 0 & 0 \\
1 & 1 & 1 & 0 \\
1 & 1 & 1 & 1
\end{bmatrix} = \begin{bmatrix}12 & 9 & 3 & 1\end{bmatrix}
$$
::: 

Diese Logik lässt sich auch auf Matrizen erweitern. Dabei werden die Vorgänger- bzw. Nachfolgerwerte für jede Zeile berechnet.

::: {#exm-nachfolger-summe}
## Nachfolgersumme für eine $2 \times 4$-Matrix

$$
\begin{bmatrix}
3 & 6& 2  &1 \\
4 & 3 & 2 & 1
\end{bmatrix} 
\times \begin{bmatrix}
1 & 0 & 0 & 0 \\
1 & 1 & 0 & 0 \\
1 & 1 & 1 & 0 \\
1 & 1 & 1 & 1
\end{bmatrix} = 
\begin{bmatrix}
12& 9& 3 &1 \\
10 & 6 & 3 & 1
\end{bmatrix}
$$
:::

## Das äussere Matrixprodukt

Bei den Vektoren und Matrizen haben wir bereits das Kreuzprodukt kennengelernt, mit dem wir aus zwei Vektoren eine Matrix konstruieren können. Das Kreuzprodukt ist allerdings nur für die Multiplikation als paarweiser Operator definiert. Neben dem Kreuzprodukt gibt es noch eine zweite und flexiblere Möglichkeit, um aus zwei Vektoren eine Matrix zu generieren: Das sog. äussere Produkt. 

Beim **äusseren Produkt** oder *dyadischen Produkt* werden die Werte zweier *Vektoren* *paarweise* miteinander verknüpft, wodurch eine Matrix erzeugt wird, bei der die Anzahl der Zeilen entsprechend der Länge des linken und die Anzahl der Spalten mit der Länge des rechten Vektors übereinstimmt.

Wenn also zwei Vektoren x mit der Länge m und y mit der Länge n gegeben sind, dann können wir das äussere Produkt wie folgt schreiben: 

$$
x \otimes y = M^{m \times n }
$$

Das Ergebnis des äusseren Produkts ist also immer eine Matrix. Wir beachten, dass die Definition nur eine Verknüpfung fordert, aber nicht festlegt, welche Verknüpfung verwendet werden soll. Wir können also *beliebige Operationen* zur Verknüpfung verwenden. 

Wird als Verknüpfungsoperator für das äussere Produkt die Multiplikation gewählt, dann entspricht das Ergebnis des äusseren Produkts für zwei Vektoren dem Kreuzprodukt zwischen Vektoren.

Anders als beim Kreuzprodukt, können beim äusseren Matrixprodukt beliebige Operatoren verwendet werden. In der Praxis werden sehr oft Vergleichsoperatoren für die Verknüpfung verwendet. 

> ::: {#exm-dreiecks-matrix-erzeugen}
> ## Eine Dreiecks-Matrix mit dem äusseren Produkt erzeugen.
>
> Eine Dreiecks-Matrix eine wichtige Matrix, weil durch die `0` ober- bzw. unterhalb der Hauptdigonalen bei der Matrixmultiplikation viele Rechenoperationen eingespart werden können. Diese Einsparung kommt in der Praxis immer dann zum Tragen, wenn nur Vorgänger- oder Nachfolgerwerte berücksichtigt werden müssen. Dafür ist es oft sinnvoll, eine Dreiecks-Matrix zu erzeugen, die nur die Werte `1` und `0` enthält.
>
> Eine Dreiecksmatrix lässt sich mit dem äusseren Produkt aus zwei Sequenzen erzeugen. Dazu wird in zwei Schritten vorgegangen.
>
> 1. Eine Sequenz wird mit der gewünschten Länge erzeugt.
> 2. Die Sequenz wird mit sich selbst multipliziert. Als Operator wird ein Vergleichsoperator verwendet, der die Werte der Sequenz paarweise vergleicht.
>
> Eine Dreiecks-Matrix entsteht, wenn ein grösser- oder kleiner-Vergleich durchgeführt wird. Soll die Hauptdiagonale einbezogen werden, dann jeweils ein grösser-oder-gleich- bzw. kleiner-oder-gleich-Vergleich durchgeführt werden.
>
> Um eine $3\times 3$-Matrix zu erzeugen, wird eine Sequenz mit der Länge 3 benötigt.
>
> $$
> \{1;2;3\}
>$$
>
> Diese Sequenz wird mit sich selbst multipliziert. Als Operator wird ein grösser-Vergleich verwendet.
>
> $$
> \{1;2;3\} \otimes_{>} \{1;2;3\} = \begin{bmatrix}
> 0 & 0 & 0 \\
> 1 & 0 & 0 \\
> 1 & 1 & 0
\end{bmatrix} 
> $$
>
> ::: 

Weil das äussere Produkt beliebige Operatoren erlaubt, lassen sich mit der gleichen Technik wie für die Dreiecks-Matrix auch andere Strukturen systematisch erzeugen. Falls dabei komplexe logische Ausdrücke verwendet werden, ist es sinnvoll, diese in einer Funktion zu kapseln.

> ::: {#exm-komplex-structure-erzeugen}
> ## Eine komplexe Struktur mit dem äusseren Produkt erzeugen.
> 
> Es soll eine $6 \times 6$-Matrix erzeugt werden, die entlang Hauptdiagonalen und der direkt benachbarten Nebendiagonalen den Wert `1` enthält. Alle anderen Werte sollen `0` sein.
> 
> Dazu wird Sequenz der Länge `6` als Basis für das äussere Produkt verwendet. 
> 
> $$
> \{1;2;3;4;5;6\}
> $$
> 
> Weil diese Struktur nicht durch einen direkten Vergleich erzeugt werden kann, wird eine Funktion $f$ für den logischen Ausdruck erstellt. Daraus ergibt sich das folgende äussere Produkt.
> 
> $$ 
> \{1;2;3;4;5;6\} \otimes_{f} \{1;2;3;4;5;6\}
> $$
> 
> Um die gewünschte Struktur zu erzeugen, bedarf es eines komplexen logischen Ausdrucks mit zwei Vergleichen. Zum einen muss für die Struktur der eine Index kleiner oder gleich dem um eins erhöhten anderen Index sein. Zum anderen darf die Differenz zwischen den beiden Indizes nicht grösser als eins sein. Daraus ergibt sich die folgende Definition für die Funktion $f$.
> 
> $$
> f(i, j) \to (i \le j+1) \land (j - i \le 1)
> $$
> 
> Das Ergebnis des äusseren Produkts mit dieser Funktion als Operator ist die gewünschte Matrix.
> 
> $$
> \begin{bmatrix}
> 1 &  1 &  0 &  0 &  0 &  0 \\
> 1 &  1 &  1 &  0 &  0 &  0 \\
> 0 &  1 &  1 &  1 &  0 &  0 \\
> 0 &  0 &  1 &  1 &  1 &  0\\
> 0 &  0 &  0 &  1 &  1 &  1 \\
> 0 &  0 &  0 &  0 &  1 &  1 
> \end{bmatrix}
> $$
> 
> :::

Das äussere Produkt erlaubt beliebige Operatoren für die Multiplikation und ist deshalb sehr flexibel. Weil Operatoren nur spezielle Funktionen sind, lassen sich komplexe Operatoren z.B. mittels logischer Ausdrücke erzeugen.

> ::: {#exm-werte-markieren}
> ## Werte in einem Vektor markieren
> 
> Häufig ist es notwendig, bestimmte Werte in einem Vektor zu markieren, damit sie von nachfolgenden Matrix-Operationen berücksichtigt werden können. Ein typisches Beispiel für solche Markierungen ist das Markieren der einzelnen Werte eines diskreten Wertebereichs. 
> 
> Dazu wird zuerst ein Hilfsvektor erstellt, der alle (vorkommenden) Werte des Wertebereichs enthält. Anschliessend wird das äussere Produkt zwischen dem originalen Vektor und dem Hilfsvektor mit einem Vergleichsoperator durchgeführt.
> 
> Hier soll der Wertebereich die Werte 1 bis 5 enthalten. Daraus ergibt sich der Hilfsvektor $v_h = \{1;2;3;4;5\}$. Der Vektor $v$ soll markiert werden. Dieser Vektor enthält die Werte $\{1;3; 2; 3; 4; 5; 3; 2; 4; 4; 5; 1; 4\}$.
> 
> Als Vergleichsoperator wird die Gleichheit verwendet, um die Werte zu markieren. Das Ergebnis ist die folgende Matrix.
> 
> $$
> v \otimes_{=} v_h = \begin{bmatrix}
> 1 & 0 & 0 & 0 & 0 \\
> 0 & 0 & 1 & 0 & 0 \\
> 0 & 1 & 0 & 0 & 0 \\
> 0 & 0 & 1 & 0 & 0 \\
> 0 & 0 & 0 & 1 & 0 \\
> 0 & 0 & 0 & 0 & 1 \\
> 0 & 0 & 1 & 0 & 0 \\
> 0 & 1 & 0 & 0 & 0 \\
> 0 & 0 & 0 & 1 & 0 \\
> 0 & 0 & 0 & 1 & 0 \\
> 0 & 0 & 0 & 0 & 1 \\
> 1 & 0 & 0 & 0 & 0 \\
> 0 & 0 & 0 & 1 & 0
> \end{bmatrix}
> $$
>
> Nun lässt sich bspw. die Spaltensumme entsprechend von @exm-spalten-summe mithilfe eines Einsvektors $v_1$ der Länge `13` berechnen, um die Häufigkeit der einzelnen Werte zu bestimmen.
>
> $$
> v_1 \times \begin{bmatrix}
> 1 & 0 & 0 & 0 & 0 \\
> 0 & 0 & 1 & 0 & 0 \\
> 0 & 1 & 0 & 0 & 0 \\
> 0 & 0 & 1 & 0 & 0 \\
> 0 & 0 & 0 & 1 & 0 \\
> 0 & 0 & 0 & 0 & 1 \\
> 0 & 0 & 1 & 0 & 0 \\
> 0 & 1 & 0 & 0 & 0 \\
> 0 & 0 & 0 & 1 & 0 \\
> 0 & 0 & 0 & 1 & 0 \\
> 0 & 0 & 0 & 0 & 1 \\
> 1 & 0 & 0 & 0 & 0 \\
> 0 & 0 & 0 & 1 & 0
> \end{bmatrix} = \begin{bmatrix} 2 & 2 & 3 & 4 & 2 \end{bmatrix}
> $$
> :::

## Co-Occurence-Matrizen erzeugen

Co-Occurance Matrizen helfen beim Feststellen der Häufigkeiten des gemeinsamen Auftretens von Werten in zwei Vektoren. Das Ergebnis zeigt an den einzelnen Positionen jeweils die Anzahl steht mit der die korrespondierenden Werte der jeweiligen Spalte bzw. Zeilen gleichzeitig vorkommen. Bei der Erstellung einer Co-Occurrence-Matrix müssen zuerst die zählbaren Elemente identifiziert werden. Das wird durch das äussere Produkt erreicht. Das erfolgt in drei Schritten.

1. Es werden zwei Vektoren erstellt, in dem die Werte aus den Vektoren genau einmal vorkommen. 
2. Es werden zwei Matrizen über das äussere Produkt des jeweiligen original Vektors und dem zugehörigen eindeutigen Vektor aus Schritt 1 erstellt. Der Operator für das äussere Produkt ist in diesem Fall der Gleichheitsoperator.
3. Mit den beiden Matrizen aus Schritt 2 wird das Kreuzprodukt gebildet. Dazu muss eine der beiden Matrizen transponiert werden. Dieses Kreuzprodukt ist immer zulässig, weil beide Matrizen die gleiche Anzahl an Zeilen haben, wenn sie aus dem gleichen Datenrahmen gebildet wurden.

Die Schritte 1 und 2 sind eine direkte Anwendung von @exm-werte-markieren.

Das Ergebnis ist eine Matrix mit der Anzahl der gemeinsamen Vorkommen der Werte aus den beiden eindeutigen Vektoren aus Schritt ein. Die Werte lassen sich über das Kreuzprodukt zuordnen: 

- Die Spalten entsprechen den eindeutigen Werten der linken (nicht transponierten) Matrix.
- Die Zeilen entsprechen den eindeutigen Werten der rechten (transponierten) Matrix.

Alternativ zur Position der Werte kann auch ein *Sekundärindex* (s.[Kapitel @sec-chapter-indizieren-gruppieren]) für das äussere Produkt verwendet werden.

Eine Co-occurance-Matrix ist immer symmetrisch. Durch eine Skalarmultiplikation mit einer Dreiecks-Matrix aus @exm-dreiecks-matrix-erzeugen kann die Matrix in eine untere oder obere Dreiecksmatrix umgewandelt werden.
