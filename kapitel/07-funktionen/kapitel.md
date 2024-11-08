---
# bibliography: references.bib

title: Funktionen

abstract: ""

execute: 
  echo: false
---

> **Merke**:  Funktionen und Operatoren bilden die Grundlage für die Programmierung in einer Programmierumgebung bzw. einer Programmiersprache. Sie legen fest, welche Arbeiten wir in Algorithmen ausdrücken können.


> **Definition:** Eine Funktion erzeugt aus Eingaben Ergebnisse. Eine mathematisch korrekte Funktion erzeugt für die gleichen Eingaben **immer** die gleichen Ergebnisse. 


> **Definition:** Eine Funktion, die für jede Eingabe immer den gleichen Ergebniswert $e$ erzeugt, wird als **konstante Funktion** bezeichnet.


Für konstante Funktionen gilt die folgende Eigenschaft: 

$$
f(x) \to e
$$

Das bedeutet, dass unabhängig von der Eingabe immer der Wert von $e$ als Ergebnis folgt. 

> **Definition:** Die Eingabe einer Funktion wird als **Parameter** bezeichnet. Eine Funktion kann mehrere Parameter haben. Eine Funktion **akzeptiert** diese Parameter als Eingabe. 


Per Konvention werden die Parameter einer Funktion in Klammern nach dem Funktionsnamen dargestellt. 

> **Definition:** Eine Funktion, die keine Parameter akzeptiert, wird als **parameterlose Funktion** bezeichnet.


Eine parameterlose Funktion akzeptiert keine Eingaben. Folgen wir der Definition für *konstante Funktionen*, dann müssten parameterlose Funktionen ebenfalls konstante Funktionen sein. In Programmiersprachen gibt es aber parameterlose Funktionen, die für jeden Aufruf unterschiedliche Ergebnisse liefern. Ein Beispiel für diese Funktionen ist die Funktion `ZUFALLSZAHL()` von Excel. Diese Funktion erfüllt die Kriterien für eine mathematisch korrekte Funktion *nicht*. 

Sie können diesen Gedankengang für parametrische Funktionen weiterführen, die für die gleichen Eingaben nicht immer das gleiche Ergebnis erzeugen. 

## Operationen, Operatoren und Operanden 

> **Definition:** Eine **Operation** bezeichnet die eine Folge von Operanden und Operatoren, die ein Ergebnis erzeugen.
 

> **Definition:** Ein **Operator** ist ein Symbol (oder Symbolfolge), das festlegt, wie ein Operand oder mehrere Operanden miteinander verknüpft werden sollen.

- Es gibt unäre Operatoren, die genau einen Operanden haben. 
- Es gibt binäre Operatoren, die genau zwei Operanden haben.

Operatoren mit mehr als zwei Operanden haben für uns keine Relevanz und sollten grundsätzlich vermieden werden.

> **Definition:** Ein **Operand** wird ein Wert oder Platzhalter bezeichnet, der mit einem Operator verknüpft wird.


Steht der Operand auf der linken Seite des Operators, dann wird dieser Operand als links-seitiger Operand bezeichnet. Steht der Operand auf der rechten Seite des Operators, dann wird dieser als rechts-seitiger Operand bezeichnet.

#### Beispiele für unäre Operatoren

Fakultätsoperator (`!`):  $5!$ 

Negationsoperator (`-`): $-3$

Klammeroperator (`( ... )`):  $3 \cdot ( 1 + 2 )$

#### Beispiele für binäre Operatoren

Additionsplus (`+`): $1 + 2$

Subtraktionsminus (`-`): $2 - 1$

### Kommutativität

Wir bezeichnen einen binären Operator als **kommutativ**, wenn der links-seitige und der rechts-seitige Operand vertauscht werden können, ohne dass sich das Ergebnis der Operation ändert. 

### Die Identitätsfunktion

Beim Computational Thinking hat *eine Funktion* eine besondere Bedeutung: Die **Identitätsfunktion**. 

> Die **Identitätsfunktion** oder kurz **Identität** ist als die Funktion definiert, die für einen beliebigen Eingabewert diesen Wert als Ergebnis liefert. 

Diese Eigenschaft können wir wie folgt schreiben: 

$$ f_{ID}(x) \to x $$

Diese Funktion ist das *neutrale Element* der Funktionsverkettung. Das bedeutet, dass wir die Identitätsfunktion beliebig oft in eine Funktionskette einfügen können, ohne das Ergebnis der Funktionskette zu beeinflussen. 

> Die Identitätsfunktion hat in **Excel** die besondere Bedeutung, dass mit ihr Werte *kopiert* werden. Weil die Funktion die Eingabe als Ausgabe hat, fehlt eine explizite Funktion in Excel. Sie werden deshalb *keine* Funktion im Menüband `Formeln` finden. Stattdessen müssen wir uns jedes Mal eine implizite Identitätsfunktion vorstellen, wenn Adressen oder Adressbereiche in einer Funktion angegeben werden. 

In **R** existiert eine Funktion `identity()` mit der Eigenschaft der Identitätsfunktion. Diese Funktion verwenden wir in der Regel nicht, sondern denken uns diese Funktion mit. 

#### Chaining in Excel 

> Excel kennt keinen Verkettungsoperator. Die Funktionsverkettung erreichen wir in Excel durch die Gliederung von einfacheren Funktionen auf mehrere Zellen auf einem Arbeitsblatt. Die Verkettung erzeugen wir durch den Verweis auf die vorangehende Zelladresse. 

> In Excel können wir uns Funktionsketten mit den Befehlen `Spur zum Nachfolger` und `Spur zum Vorgänger` aus dem Menüband `Formeln` anzeigen lassen.

<a href="https://github.com/dxiai/ct-resourcen/blob/main/bilder/funktionen/excel_chaining_verfolgen.png?raw=true"><img src="https://github.com/dxiai/ct-resourcen/blob/main/bilder/funktionen/excel_chaining_verfolgen.png?raw=true" width="600"></a>

#### Chaining in R

> Modernes R stellt den Operator `%>%` zur einfachen Funktionsverkettung bereit. Dieser Operator ist für Sie erst dann verfügbar, *nachdem* Sie die Bibliothek `tidyverse` mit `library(tidyverse)` in Ihre Arbeitsumgebung eingebunden haben.
> 
> Der Operator `%>%` verkettet das Ergebnis einer vorangehenden Operation mit dem *ersten Parameter* der nachfolgenden Operation.

Sie können sich den Chaining-Operator als Anzeige für den Datenfluss Ihres Programms vorstellen. Ihre Daten fliessen in Pfeilrichtung von einem Funktionsschritt zum nächsten.

> Es ist eine gute Praxis, wenn Sie in den ersten Zeilen Ihres R-Codes die von Ihnen benötigten Bibliotheken in Ihre Arbeitsumgebung laden. In einem Notebook sollten alle Aufrufe von `library()` in der ersten Code-Zelle stehen. 

> In Base R können wir eine Funktionsverkettung ausschliesslich mit Hilfsvariablen oder geschachtelten Funktionsaufrufen realisieren. Dadurch wird der resultierende R-Code schnell unübersichtlich.


## Funktionen in Excel

Excel Funktionen bestehen aus einem Funktionsnamen, einer Parameterliste und einem Ergebnis. Die Funktionsnamen können wir aus dem Menüband `Formeln` ableiten. Bei der Eingabe einer Funktion wird Ihnen eine Schnellübersicht zu den Parametern einer Funktion angezeigt. 

Excel kennt nur die eingebauten Funktionen. Sie finden alle verfügbaren Funktionen und eine detaillierte Beschreibung über das Menüband `Formeln`. In diesem Bereich sind alle verfügbaren Funktionen nach Kategorien sortiert aufgeführt. Über die Funktionsleiste oder den Formeleditor haben Sie Zugang zur vollständigen Dokumentation für diese Funktionen. In der Praxis müssen Sie geeignete Funktionen für eine konkrete Aufgabenstellung finden können. 

> Die meisten Aufgaben können nicht durch einen einzigen Funktionsaufruf gelöst werden. In den meisten Fällen **müssen** Sie mehrere Funktionen zu komplexen Operationen *kombinieren*!


Die Parameter von Excel-Funktionen haben eine bestimmte Reihenfolge. Diese Reihenfolge **muss** eingehalten werden, weil Excel sonst eine Fehlermeldung erzeugt. In der deutschsprachigen Excel-Fassung werden die Parameter durch Semikola getrennt. Gelegentlich sind bestimmte Parameter von Excel-Funktionen *optional*. Optional bedeutet, dass diese Werte nur bei Bedarf angegeben werden müssen. In allen anderen Fällen verwendet Excel einen geeigneten Wert für die jeweiligen Parameter.

> Achten Sie darauf, dass Sie die Parameterliste der aktuellen Funktion jeweils mit einer schliessenden Klammer beenden. Verlassen Sie sich nicht darauf, dass Excel schon weiss, was Sie machen möchten. Gerade in komplexen Formeln führt die "automatische Korrektur" einer Formel zu unerwarteten Effekten.


## Funktionen in R

In R bilden Funktionen den zentralen Kern der Programmiersprache. Im Gegensatz zu Excel wird in R nicht zwischen Operatoren und Funktionen unterschieden. Das bedeutet, dass jeder R-Operator über eine Funktion definiert ist.

In R sind Funktionen immer über drei Eigenschaften definiert: 

1. Die Parameterliste 
2. Die Ergebnisse
3. Die Überführungslogik

Die **Parameter** einer Funktion werden in R durch Kommata getrennt. Die Parameter von R-Funktionen sind immer benannt und können über diese Namen gezielt angesprochen werden.

R-Funktionen haben immer genau ein Datenobjekt als **Ergebnis**. Das können Stichproben, Listen, Vektoren oder auch einzelne Werte sein.

Der **Funktionskörper** legt fest, wie die Parameter in ein Ergebnis überführt werden. Es ist nicht ungewöhnlich, dass ein Funktionskörper eine oder mehrere andere Funktionen aufruft.

Auch R-Funktionen haben Namen. Diese Funktionsnamen sind aber nichts anderes als Variablen, in denen wir auch Daten speichern würden. Auf diese Weise können wir bestehenden Funktionen einen neuen Namen geben.

Das folgende Beispiel illustriert das: 

```R
lese_csv_datei = read_csv   # Beachten Sie, dass hier keine Klammern nach read_csv stehen!
``` 

Anschliessend können wir diesen neuen Namen für Funktionsaufrufe verwenden. 

```R
csvDaten = lese_csv_datei("beispieldaten.csv")
```

Weil R-Operatoren auch Funktionen sind, können wir auch diese umbenennen und als Funktionen verwenden. Weil aber die Operatoren von R als besondere Symbole erkannt werden, müssen wir die Operatoren "schützen", damit wir den Namen des Operators und nicht den Operator selbst aufrufen können. Mit dem Akzent-Zeichen (Backtick, `` ` ``) können wir ein Symbol davor schützen, dass R es "wie gewohnt" ausführt. Wir können also den `+`-Operator wie folgt in eine Funktion mit dem Namen `plus` umwandeln:

```R
plus = `+`
```

Weil der `+`-Operator ein binärer Operator ist, erwartet diese neue Funktion zwei Parameter. Einen für den linken und einen für den rechten Operanden. Jetzt können wir zwei Zahlen wie folgt addieren: 

```R
plus(1, 2)     # ergibt 3
```

> Achten Sie darauf, dass Sie Funktionen aufrufen, indem Sie dem Funktionsnamen eine öffnende und eine schliessende runde Klammer für die Parameterliste anfügen. 
Die Klammern sind auch bei parameterlosen Funktionen verpflichtend. Lassen Sie die Klammern weg, wird der Funktionskörper angezeigt, aber *nicht* ausgeführt.

Es ist bei R-Funktionen üblich, dass bestimmte Parameter sog. *Vorgabewerte* haben. Diese Werte werden angenommen, wenn ein Parameter nicht explizit übergeben wird. In der Dokumentation erkennen wir diese Vorgaben durch ein Gleichheitszeichen nach dem Parameternamen. 

> In R sind Parameter benannt. Beim Aufruf einer Funktion können wir so festlegen, welche Werte welchem Parameter zugewiesen werden, ohne die Position des Parameters zu berücksichtigen. 

Beispiel: Die Funktion `read_delim()` akzeptiert den Parameter `file`. Dieser Parameter wird als erster Parameter der Funktion angenommen. Durch die Benennung des Parameters können wir die Reihenfolge der Parameter nach unseren Bedürfnissen bzw. zur besseren Lesbarkeit umsortieren. Dadurch sind die folgenden beiden Operationen identisch.

```R
# Operation 1
read_delim("beispiel.csv", FALSE)

# Die nächste Operation ist gleichwertig zu Operation 1
read_delim(col_names = FALSE, file = "beispiel.csv")
``` 

> **Konvention:** In der R-Dokumentation sehen Sie, welche Parameter zwingend übergeben werden müssen. Diese Parameter haben in der Dokumentation kein Gleichheitszeichen. Für diese Parameter behalten Sie in aller Regel die Position bei der Parameterübergabe bei.


Im Gegensatz zu Excel können in R auch neue Funktionen erstellt werden. Dadurch kann die Sprache von R erweitert und modernisiert werden. Wir nutzen diese Möglichkeit *meistens*, indem wir Funktionen aus *Funktionsbibliotheken* (oder Paketen) mit der `library()`-Funktion in unsere Arbeitsumgebung laden. 

# Funktionsketten in Excel und R

Wir können Funktionen aufrufen und das Ergebnis an eine andere Funktion übergeben. So können wir komplexe Funktionen als Kombination einfacherer Funktionen verstehen. Dieses Kombinieren kennen wir aus der Mathematik und haben es im Zusammenhang mit der KEPS-Regel bereits besprochen. Wir kombinieren zwei Funktionen, indem wir das Ergebnis der vorangehenden Funktion als Parameter der nachfolgenden Funktion übergeben. 

Nehmen wir zum Beispiel eine fiktive ein-parametrische Funktion $h(x)$ an, die wir aus der Kombination der Funktionen $f(x)$ und $g(x)$ erhalten, wobei zuerst die Funktion $g$ ausgeführt werden soll. Wir können die Funktion $h(x)$ dann wie folgt definieren: 

$$
h(x) = f(g(x))
$$

Bei dieser Notation müssen wir beachten, dass die Funktion $g(x)$ **vor** der Funktion $f(x)$ ausgeführt werden muss. 


> **Definition:** Eine Kombination von Funktionen, bei der Resultate vorangehender Funktionen als Parameter nachfolgender Funktionen verwendet werden, wird als **Funktionskette** bezeichnet. 

In der *Mathematik* wird als *Verkettungsoperator* das Symbol $\circ$ verwendet. Wir können also die Funktionskette aus dem Beispiel auch wie folgt schreiben: 

$$
h(x) = (g \circ f)(x)
$$

In dieser Notation ist deutlich, welche der Funktionen als erstes aufgerufen wird. 

> **Merke:** Um praktische Aufgaben zu lösen, strukturieren wir diese Aufgaben *immer* in einfachere, weniger komplexe Teilaufgaben, die wir anschliessend verketten. Die Funktionsverkettung ist das Leitprinzip der **Problemzerlegung**.

> *Exkurs:* Funktionsketten sind ein Konstrukt des sog. *Lambda-Kalküls*. Dabei handelt es sich um eine mathematische Theorie zur Untersuchung von komplexen Funktionen. 
>
> In dieser Lehrveranstaltung müssen Sie nur das Konzept der *Funktionsverkettung* verstehen und anwenden können. 

### Chaining: Funktionsketten in Excel und R 

> **Konvention:** In der Programmierung wird die Funktionsverkettung als **function chaining** oder kurz als **chaining** bezeichnet. Alle modernen Programmiersprachen unterstützen dieses Konzept. 
