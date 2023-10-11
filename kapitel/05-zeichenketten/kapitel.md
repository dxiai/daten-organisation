---
execute: 
  echo: false
---

# Zeichenketten {#sec-chapter-zeichenketten}

Neben Zahlen gehören Zeichenketten zu den wichtigsten Datentypen für die Datenanalyse. Bei Zeichenketten werden als erstes Worte oder Sätze assoziiert. Im [@sec-zeichenkodierung] wurde die Kodierung von Symbolen als Zahlen vorgestellt und [Kapitel @sec-datentypen] hat Zeichenketten als fundamentalen Datentyp eingeführt. Diese Ideen werden in diesem Kapitel erweitert und durch die wichtigsten Operationen für Zeichenketten ergänzt.

::: {#def-zeichenkette}
Eine Zeichenkette ist eine beliebige Kette von Textsymbolen. Textsymbole können Buchstaben, Ziffern, Satzzeichen sowie nicht-druckbare Zeichen sein.
:::

Zeichenkette sind immer **diskrete Daten**.

Aus dieser Definition folgt, dass Zeichenketten eine Länge haben müssen.

::: {#def-zeichenkette-länge}
Die **Länge** einer Zeichenkette entspricht der Anzahl aller enthaltenen Symbole.
:::

Zeichenketten sind also *Werte* und haben gleichzeitig die Eigenschaften eines Vektors. 


## Nicht-druckbare Zeichen
::: {#def-nicht-druckbare-zeichen-zeichenkette}
**Nicht-druckbare Zeichen** sind Symbole, die bei der Darstellung einer Zeichenkette nicht angezeigt werden können. Die nicht-druckbaren Zeichen zählen zur Länge einer Zeichenkette und verändern den Inhalt einer Zeichenkette.
:::

Beispiel: Die Zeichenkette `Hallo` unterscheidet sich von der Zeichenkette `Hal<0x08>lo`. 

Zu den nicht-druckbaren Zeichen gehören auch Leerzeichen, Tabulatoren und Zeilenumbrüche. Diese speziellen nicht-druckbaren Zeichen sind nur dann zu erkennen, wenn sie von druckbaren Zeichen umgeben sind.

> ::: {#exm-nichtdruckbare-zeichen}
> Deutlich wird das an den folgenden Zeichenketten: 
>
> * `Hallo`
> * `Hal<0x07>lo`, wobei das Symbol `0x07` für einen Piepton steht
> * `Hal<0x08>lo`, wobei das Symbol `0x08` für einmal Rückwärtslöschen steht.
>
> Die erste Zeichenkette hat die Länge 5, die zweite Zeichenkette hat die Länge 6 und die dritte Zeichenkette hat ebenfalls die Länge 6.
> :::

## Die leere Zeichenkette

::: {#def-leere-zeichenkette}
Eine Zeichenkette der Länge 0 enthält keine Symbole. Diese Zeichenkette heisst die **leere Zeichenkette**. 
:::

In einigen Umgebungen lässt sich die leere Zeichenkette nicht leicht von Zeichenketten unterscheiden, die aus nicht-druckbaren Zeichen bestehen. Für viele Funktionen ist die leere Zeichenkette problematisch oder als Wert nicht zulässig. In solchen Fällen muss die leere Zeichenkette über die Länge einer Zeichenketten-Variablen explizit kontrolliert werden.

## Symbolvektoren

In einer Zeichenkette sind die Symbole angeordnet, so dass jedes Symbol über dessen Position angesprochen werden kann. 

Wird eine Zeichenkette in die einzelnen Symbole gegliedert, dann ergibt sich in den meisten modernen Programmiersprachen ein *Zeichenkettenvektor* mit Zeichenketten der Länge `1`.

## Texttrennung 

Damit Zeichenketten getrennt werden können wird eine spezielle Funktion benötigt. Diese Funktion wird als *Texttrennung* (engl. *split*) bezeichnet. Die Funktion hat zwei Parameter: Die Zeichenkette und ein Trennsymbol. Das Trennsymbol ist eine Zeichenkette, die zwei Teile einer Zeichenkette trennt. Beispiele für solche Trennsymbole wurden im [Kapitel @sec-chapter-dateiformate] vorgestellt. 

Die Texttrennung teilt eine Zeichenkette so auf, dass für alle Vorkommnisse des Trennsymbols in der Zeichenkette der Teil vor dem Trennsymbol und der Teil nach dem Trennsymbol als zwei separate Zeichenketten vorliegen. Das Trennsymbol wird entfernt. Das Ergebnis der Texttrennung ist ein Zeichenkettenvektor mit den getrennten Zeichenketten. 

::: {.callout-note}
## Merke

Die Länge des Vektors nach der Texttrennung entspricht der Anzahl der Vorkommnisse des Trennsymbols in der Zeichenkette plus 1.
:::

::: {#def-tokens}
Die durch die Texttrennung entstehenden Zeichenketten heissen *Token*.
:::

Token können Sätze, Worte oder auch einzelne Buchstaben sein. Ein Token muss nicht zwingend sprachlich sinnvoll sein.

::: {#def-tokenvektor}
Ein Vektor der Tokens enthält heisst *Token-Vektor*.
::: 

Die Texttrennung hat also einen *Token-Vektor* als Ergebnis. 

Um die einzelnen Symbole einer Zeichenkette zu erhalten, muss etwas um die Ecke gedacht werden, um die Zeichenkette zu erkennen, die zwischen jedem Symbol steht: Der Abstand zwischen zwei Symbolen in einer Zeichenkette ist immer genau 1. Weil Zeichenketten *diskrete Daten* sind, muss die Zeichenkette zwischen zwei Symbolen eine Länge von `0` haben. Die Zeichenkette mit der Länge `0` ist nach @def-leere-zeichenkette die leere Zeichenkette.

Entsprechend enthält der Token-Vektor nach der Texttrennung mit der leeren Zeichenkette den einzelnen Symbolen der ursprünglichen Zeichenkette.

## Textverkettung

Die Texttrennung ist umkehrbar. Die Umkehrfunktion der Texttrennung ist die Textverkettung. Die Textverkettung fügt mehrere Zeichenketten zu einer neuen Zeichenkette zusammen.

Die Textverkettung ist eine spezielle Form der Konkatenation von Vektoren (s. [Kapitel @sec-konkatenation]).

Die Textverkettung hat zwei Parameter: 

- Einen Token-Vektor
- Ein Trennsymbol

Die Textverkettung fügt alle Zeichenketten des Token-Vektors zusammen, indem die erst das vorangehende Token, dann das Trennsymbol und zuletzt die nachfolgende Zeichenkette zusammengefügt werden. Das Ergebnis ist eine neue Zeichenkette.

Wird der Token-Vektor einer Texttrennung mit dem gleichen Trennsymbol wieder verkettet, dann ist das Ergebnis die ursprüngliche Zeichenkette.

Die leere Zeichenkette ist das neutrale Element der Textverkettung.

## Normalisierung

::: {#def-normalisierung-zeichenkette}
Das Entfernen und Vereinheitlichen von Leerzeichen und nicht-druckbaren Zeichen aus einer Zeichenkette heisst **Normalisieren von Zeichenketten**. 
:::

Eine *normalisierte Zeichenkette* enthält keine führenden oder nachfolgenden Leerzeichen, keine nicht-druckbaren Zeichen und keine aufeinanderfolgenden Leerzeichen. 

Die Operation des Normalisieren ist das Suchen und Ersetzen. Beim Suchen und Ersetzen werden Zeichenketten durch andere Zeichenketten ersetzt. Die Basis-Funktion des Suchens und Ersetzens hat drei Parameter: 

- Die Zeichenkette, in der gesucht werden soll
- Die gesuchte Zeichenkette (das *Suchmuster*)
- Die Ersetzungszeichenkette

Die Funktion sucht in der Zeichenkette nach dem Suchmuster und ersetzt das Suchmuster durch die Ersetzungszeichenkette. Das Ergebnis ist eine neue Zeichenkette, in der das Suchmuster durch die Ersetzungszeichenkette ersetzt wurde. 

Wird als Ersetzung die leere Zeichenkette verwendet, dann wird das Suchmuster aus der Zeichenkette entfernt.

Wenn das Ergebnis einer Suchen-und-Ersetzen-Funktion die ursprüngliche Zeichenkette ist, wurde keine Ersetzung durchgeführt.

Beim *Normalisieren* von Zeichenketten werden Suchen-und-Ersetzen-Funktionen solange angewendet, bis keine Ersetzung mehr vorgenommen wird. Die Zeichenkette ist dann normalisiert.

Weil das Normalisieren von Zeichenketten eine sehr häufige Operation ist, gibt es dafür spezielle Funktionen. Die wichtigsten dieser Funktionen sind: 

- Die Bereinigung von Leerzeichen am Anfang und Ende einer Zeichenkette (engl. *trim*)
- Die Bereinigung von aufeinanderfolgenden Leerzeichen.

::: {.callout-tip}
## Praxis

Oft müssen Zeichenketten auch von anderen Symbolen bereinigt werden. Dabei handelt es sich um Erweiterungen des Normalisierens.
:::

## Gross- und Kleinschreibung

Zeichenketten können in der Gross- oder Kleinschreibung variieren. Die Gross- und Kleinschreibung ist ein *semantisches Merkmal* von Zeichenketten, kann aber auch auf Tippfehler zurückgehen. Um Varianten der Gross- und Kleinschreibung zu ignorieren, werden alle Symbole einer Zeichenkette in Gross- oder in Kleinbuchstaben umgewandelt, falls es sich um Buchstaben handelt. Alle anderen Symbole bleiben unverändert. 

Die Umwandlung von Gross- in Kleinbuchstaben ist leicht umzusetzen, weil Kleinbuchstaben in der Zeichenkodierung immer um den gleichen Wert (`0x20`)grösser sind als Grossbuchstaben. Die Umwandlung wird in der Regel mit einer entsprechenden Funktion durchgeführt und muss nicht selbst implementiert werden.

Satzzeichen, Zahlen und viele Schriften verfügen über keine grossen und kleinen Buchstaben. Die entsprechen Symbole werden nicht umgewandelt.
