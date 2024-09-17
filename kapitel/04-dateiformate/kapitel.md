---
execute: 
  echo: false
---

# Dateiformate {#sec-chapter-dateiformate}

Zum Speichern und zum Austausch von Daten spielen Dateiformate eine wichtige Rolle. Dateiformate legen fest, wie Daten serialisiert werden. Die Serialisierung von Daten ist die Grundlage für die Speicherung und den Austausch von Daten. Eine spezielle Serialisierung wird als *Datenformat* bezeichnet.

In Computern werden Daten immer als *Datenströme* abgebildet. 

::: {#def-datenstrom}
Ein **Datenstrom** ist eine Folge von binärkodierten Bits. 
::: 

Ein Datenstrom ist also immer eine Abfolge von `0` und `1` Werten. Diese Abfolgen sind eine *Datenserialisierung* (s. [Abschnitt @sec-serialisierung]). Für die Interpretation werden diese Abfolgen in Gruppen zusammengefasst. Üblich sind Gruppen von 8-Bit (dem sog. *Byte*), 16-Bit, 32-Bit oder 64-Bit. 

Datenströme können eine *feste Länge* haben. In diesem Fall wird die Länge eines Datenstroms wird *Byte* angegegeben. 

::: {#def-datei}
Eine **Datei** ist ein Datenstrom mit fester Länge, der von einem Speichermedium geladen wird.
:::

Weil eine Datei auf einem Speichermedium gespeichert ist, kann der Datenstrom aus einer Datei wiederholt abgerufen werden. Deshalb gehören Dateien zu den sog. ***persistenten Datenströmen***. Persistente Datenströme liefern also *dauerhafte Daten*. 

Nicht alle Datenströme sind persistent. Deshalb ist es wichtig, die Art eines Datenstroms zu kennen, denn bei nicht-persisten oder **flüchtigen Datenströmen** kann auf die Daten nur einmal zugegriffen werden. *Flüchtige Datenströme* sind kommen vorwiegend bei der *automatischen Datenerfassung* vor. In diesem Fällen entspricht jeder Zugriff auf den Datenstrom einer Messung, wobei es nicht möglich ist, eine Messung zu wiederholen.


## Dateien verwenden

### Importieren

::: {#def-import-data}
Das Lesen eines Datenstroms in eine Datenstruktur wird **Importieren** genannt.
:::

Das Importieren von Daten folgt immer in mehreren Schritten: 

1. *Lesen* eines Datenstroms.
2. *Zuordnung* der Werte zu den richtigen Datentypen.
3. *Auswahl* der zu verarbeitenden Daten.

#### Daten einlesen

Beim ersten Schritt werden die Symbole eines Datenstroms in eine geeignete Datenstruktur überführt. Dabei werden die gelesenen Symbole überprüft, ob es sich um Werte oder um eine Trennmarkierung handelt. Die Werte werden entsprechend ihrer Position im Datenstrom oder über Markierungen einer Datenstruktur zugeordnet.

::: {#def-import-parsing}
Die Zuordnung von Werten in einem Datenstrom zu einer Datenstruktur wird **Parsen** genannt. Eine Funktion, die einen Datenstrom in eine Datenstruktur überführt, heisst **Parser**.
:::

Jedes Dateiformat erfordert einen eigenen *Parser*. Wird ein ungeeigneter  *Parser* verwendet, dann werden die Daten nicht korrekt importiert und können nicht weiterverarbeitet werden, weil die Datenstruktur nicht die Organisation der Daten wiedergibt. Deshalb muss beim Importieren immer ein passender Parser für das vorliegende Dateiformat verwendet werden. 

::: {.callout-note}
Für die gängigsten Datenformate existieren eigene Parser. Die Entwicklung eines Parsers für ein bestimmtes Format ist nur selten notwendig. 
:::

Die Auswahl eines geeigneten Parsers liegt in der Verantwortung der Person, welche die Daten importiert. In manchen Fällen kann das Dateiformat automatisch erkannt werden. In diesen Fällen wird ein geeigneter Parser automatisch ausgewählt. Diese automatische Auswahl ist aber nicht immer korrekt. Deshalb muss das Ergebnis des Parsers immer überprüft werden.

#### Werte zuordnen

Der zweite Schritt beim Importieren ist die Zuordnung der Werte zu den richtigen Datentypen und der richtigen Struktur. Normalerweise versucht ein Parser bereits die richtigen Datentypen zu erkennen. Dabei kann es zu Fehlern kommen, wenn sich die Werte nicht eindeutig einem Datentyp zuordnen lassen oder ein spezieller Datentyp verwendet werden soll. 

Diesem Schritt umfasst auch das Erkennen und Behandeln von Markierungen, welche in internen Strukturen als Variablennamen oder benannten Datenfeldern abgebildet werden. Bei Separator-strukturierten Dateien umfasst dieser Teilschritt die Zuordnung von Überschriften. Bei Markup-Daten werden Tags und Markierungen für die interne Struktur verwendet.

Dieser Schritt umfasst oft auch die Behandlung von ungültigen oder fehlenden Werten.

#### Daten auswählen

Gelegentlich werden mehr Daten in einem Datenstrom bereitgestellt, als für die weitere Verarbeitung benötigt werden. In solchen Fällen werden nur die Daten ausgewählt, die für die weitere Verarbeitung benötigt werden. Bei diesem Schritt werden nicht benötigte Daten aus der internen Datenstruktur entfernt. 

::: {.callout-important}
Das Auswählen von Daten bezieht sich ausschliesslich auf die interne Datenstruktur. Die ursprünglichen Daten im Datenstrom dürfen nicht verändert werden.
::: 

### Exportieren

::: {#def-export-data}
Das Schreiben von Daten aus einer Datenstruktur in einen Datenstrom heisst **Exportieren**.
:::

Beim Exportieren werden die Daten aus einer Datenstruktur in einen Datenstrom *serialisiert*. Eine Funktion die eine Datenstruktur in einen Datenstrom überführt, heisst **Serialisierer**.

Ähnlich wie beim Importieren muss auch beim Exportieren existiert für jedes Datenformat ein geeigneter Serializer. Die Wahl eines Serialisierers hängt von der späteren Verwendung der Serialisierung ab. 

::: {.callout-note}
Es ist üblich, die gleichen Daten in verschiedenen Formaten zu serialisieren.
:::

Einige Dateiformat sind sehr komplex. Dadurch sind unvollständige Serialisierungen möglich. Eine unvollständige Serialisierung kann zu Datenverlusten führen. Deshalb sollte für gängige Dateiformate immer ein existierender Serializer verwendet werden.

::: {.callout-tip}
## Praxis

Beim Exportieren von Daten die vorher importiert wurde dürfen die ursprüngliche Daten nicht überschrieben werden, weil sonst Daten verloren gehen können. Stattdessen sollten Daten beim Exportieren in eine separate Datei geschrieben werden.
:::


## Textdateien

::: {#def-textformat}
Eine Textformat legt fest, dass alle Werte in einer Datei als Zeichenkettensymbole interpretiert werden müssen. 
::: 

Die Bits einer Textdatei sind nach einem festgelegten Standard kodiert (s. [@sec-zeichenkodierung]). Dadurch kann der Inhalt einer Textdatei immer zuverlässig gelesen und interpretiert werden. Inzwischen verwenden alle modernen Betriebssysteme einheitlich den Kodierungsstandard UTF-8 [@isoiec_jtc_1sc_2_information_2020; @the_unicode_consortium_unicode_2022].

Textdateien haben den grossen Vorteil, dass die Dekodierung der Bits automatisch erfolgt. Eine Programm oder eine Funktion kann also direkt auf die kodierten Symbole zugreifen. 

::: {.callout-note}
## Textkodierungen

Ältere Datenerfassungs- oder Steuerungssysteme sind noch heute im Einsatz. Einige dieser Systeme verwenden für Textdaten einen älteren Kodierungsstandard. In solchen Fällen muss beim Zugriff auf die Daten die abweichende Kodierung explizit angegeben werden. 

Eine abweichende Textkodierung wird oft an merkwürdigen Zeichenfolgen in den Daten erkannt. Nicht immer ist die verwendete Kodierung dokumentiert. Oft lässt sich die Textkodierung aus dem kulturellen Kontext der Daten ableiten. Die folgende Tabelle gibt für Europa und die USA eine Orientierung, welche Textkodierungen in welchen Zeiträumen verwendet wurden. 

| Land/Region | Zeitraum | Wahrscheinliche Kodierung |
| :--- | :---: | :-------------- |
| Weltweit | seit ca. 2012 | UTF-8 [@isoiec_jtc_1sc_2_information_2020] |
| West-Europa | 2000-2012 | iso-8859-15 [@isoiec_jtc_1sc_2wg_3_isoiec_1998] |
| USA | 2000 - 2012 |  iso-8859-1 [@isoiec_jtc_1sc_2wg_3_dis_1998] |
| West-Europa |1990 - 2000 | iso-8859-1 [@isoiec_jtc_1sc_2wg_3_dis_1998] |
| USA | vor 2000 | ANSI/ASCII [@american_national_standards_institute_code_1977] |
:::


## Festkodierung

Bei der Festkodierung werden die Werte in einer festen Reihenfolge und festen Symbol- oder Bitlängen in den Datenstrom geschrieben. Bei der Festkodierung ist die Reihenfolge der Werte und die Länge der Werte festgelegt.

Festkodierungen erlauben sehr effizientes speichern und lesen von Daten. Damit festkodierte Daten verarbeitet können müssen die Datenfelder in einem gemeinsamen Schema festgelegt sein, dass beim Kodieren und Dekodieren verwendet wird.

> ::: {#exm-festkodierung}
> ## Kodierung der IBAN
>
> Die IBAN ist ein festkodiertes Datenformat mit vier Werten. Die Kodierung ist international einheitlich festgelegt [@isotc_68sc_8_financial_2020]:
>
> - Länderkennung (2 Buchstaben)
> - Prüfzahl (2 Ziffern)
> - Bankkennung (5 Symbole)
> - Kontonummer (6-25 Symbole)
>
> Die Prüfzahl erlaubt die Überprüfung der anderen Werte. Dadurch lassen sich Zahlendreher oder fehlerhafte Eingaben erkennen.
> 
> Die Länge des letzten Felds wird durch nationale Gremien vereinheitlicht. In Deutschland ist die Kontonummer 10-stellig, in der Schweiz 9-stellig und in Österreich 8-stellig. Die restlichen Stellen bis zur Maximallänge 25 werden mit Leerzeichen aufgefüllt.
>
> Oft werden IBANs mit Leerzeichen gruppiert, um die Lesbarkeit zu erhöhen. Die Leerzeichen werden bei der Verarbeitung gelöscht.
> :::

## Zeilenbasierte Textdateien

Normalerweise sind Textdateien unstrukturiert und die verwendeten Symbole dienen nur der Anzeige und haben keine eigene Bedeutung. Das ist nicht immer praktisch, um Daten zu strukturieren. Hier greifen sog. zeilenbasierte Textformate. Diese Textformate sind eine einfache Form der Datenorganisation, wobei alle Symbole in der gleichen Zeile zusammengehören und von den Symbolen in den anderen Zeilen abzugrenzen sind. 

Zeilenbasierte Textdateien sind eine spezielle Form der *Listenkodierung*, wobei das Symbol für den Zeilenumbruch als Listentrennzeichen behandelt wird.

Eine typische Anwendung der zeilenbasierten Textkodierung sind sog. *Log-Dateien*, mit denen Systemereignisse protokolliert werden.


## Mengen und Bäume {#sec-mengen-und-baeume}

Die Werte lassen sich auf verschiedene Arten in Datenströmen kodieren. Die einfachste Form ist die **Mengenkodierung**. Bei der Mengenkodierung werden die Werte in einer festen Reihenfolge in den Datenstrom geschrieben. Dabei werden die Werte als eine zusammenhängende *Menge* behandelt.

Die verbreitesten Formen der Mengenkodierung sind die *Listenkodierung* und die *Tabellenkodierung*. Bei der Listenkodierung werden die einzelnen Werte nacheinander in den Datenstrom geschrieben. Dabei ist die Reihenfolge der Werte nicht von Bedeutung. Bei der Tabellenkodierung werden die Werte in einer tabellarisch organisiert. Dabei werden die Werte in Zeilen und Spalten organisiert, wobei jede Zeile und jede Spalte als eine Teilmenge behandelt wird. Die Reihenfolge der Zeilen und Spalten ist dabei nicht von Bedeutung, solange die Zeilen- und Spaltenteilmengen erhalten bleiben.

::: {.callout-note}
Die Mengenkodierung ist gleichzeitig die Grundlage für *Datenbanken* und *tabellarischen Dateien*. In Datenbanken werden die Werte tabellenartig in sog. *Relationen* organisiert.
:::

Die Mengenkodierung ist einfach und effizient. Sie hat aber den Nachteil, dass die Werte nicht leicht hierarchisch organisiert werden können, weil jede Hierarchieebene eine eigene Menge erfordert und damit von den anderen Ebenen abgegrenzt wäre. Dieses Problem löst die **Baumkodierung**. Die Baumkodierung kodiert Werte in einer Hierarchie. Dadurch lassen sich komplex-geschachtelte Datenstrukturen in einer Datei abbilden. 

In einer Baumkodierung werden die Werte auf einer Hierarchiestufe zusammengefasst. Eine Hierarchiestufe wird als *Knoten* bezeichnet. In einer solchen Kodierung hat jeder Knoten eine Vorgängerstufe. Diese Vorgängerstufe wird *Elternknoten* genannt. Die Knoten auf der gleichen Hierarchiestufe haben immer den gleichen Elternknoten. Diese Knoten heissen *Geschwisterknoten*. Die Knoten ohne Nachfolger nennt man *Blattknoten*. Die eigentlichen Werte finden sich nur in Blattknoten. 

Mit der Baumkodierung lassen sich beliebig komplexe Datenstrukturen abbilden. Für die Kodierung von Datenstrukturen mit *höchstens zwei* Hierarchiestufen und *vielen Werten* ist die Baumkodierung weniger effizient als die Mengenkodierung.

## Separator-strukturierte Textdateien {#sec-separator-strukturierte-textdateien}

Eine besondere Klasse der zeilenbasierten Textdateien sind die sog. "*Separator-strukturierten*" Dateien. Diese Dateiformate sind eine einfache Form der *Tabellenkodierung*, bei der die Werte in der gleichen Zeile durch ein zusätzliches *Trennzeichen* voneinander abgegrenzt werden. 

Separator-strukturierte Dateien sind zeilenbasierte Textdateien, bei denen die Werte in einer Zeile durch ein *Trennzeichen* voneinander abgegrenzt werden. Dadurch lassen sich die Werte in einer Zeile leichter als bei einer Festkodierung kodieren und dekodieren. Für die Trennung der Werte muss nur das verwendete Trennzeichen bekannt sein. Die Position und die Länge der Werte wird durch das Trennzeichen festgelegt und muss nicht vorab definiert werden.

Die verbreitetsten Separator-strukturierten Dateiformate sind: 

- *Tab-separated values* (TSV) 
- *Comma-separated values* (CSV)
- *Pipe-separated values* (PSV) 

Der Unterschied zwischen diesen Formaten ist das verwendete Trennzeichen.
TSV-Dateien werden durch ein Tabulatorzeichen getrennt, CSV-Dateien durch ein Komma und bei PSV-Dateien durch ein Pipe-Symbol.

Das einfachste Trennzeichen wäre das *Leerzeichen*. Das Leerzeichen ist als Trennzeichen nur dann geeignet, wenn es als Symbol in den Werten *nicht* vorkommen kann. Das ist bei vielen Daten nicht der Fall. Deshalb wird häufig das Tabulator-Symbol (`\t`) als Alternative zum Leerzeichen verwendet. Das Tabulator-Symbol ist ein nicht-druckbares Zeichen, das dem Leerzeichen ähnelt, aber seltener in Werten vorkommt. Dieses einfache Format wird als *Tab-separated values* (TSV) bezeichnet [@lindner_definition_1993].

::: {#exm-tsv-file}
## TSV-Daten

```csv
Name    Vorname Geburtsdatum    Geburtsort  Grösse
Müller  Hans 01.01.1990  Berlin   1.76
Untermayr Peter   01.01.1980  Wien 1.82
Osterwalder Urs    01.01.1970   Bern  1.78
```
:::

Die Basis für die meisten anderen Separator-strukturierten Dateiformate ist das standardisierte CSV-Format [@shafranovich_common_2005]. Die Trennzeichen der CSV Spezifikation sind das Komma (`,`) und der Zeilenumbruch. Zusätzlich können die Werte in Anführungszeichen gesetzt werden, um die Werte zu schützen, falls diese ein Komma enthalten. 

::: {#exm-csv-file}
## CSV-Daten

```csv
Name,Vorname,Geburtsdatum,Geburtsort,Grösse
Müller,Hans,01.01.1990,Berlin,1.76
Untermayr,Peter,01.01.1980,Wien,1.82
Osterwalder,Urs,01.01.1970,Bern,1.78
```
:::

Im deutschsprachigen Raum wird die CSV-Spezifikation oft abgewandelt. Dabei wird das Komma durch ein Semikolon (`;`) ersetzt. Dadurch kann das Komma als Dezimaltrennzeichen verwendet werden, ohne es zusätzlich durch Anführungszeichen geschützt zu werden. Diese Abwandlung wird als *Semikolon-separierte Werte* bezeichnet und ebenfalls als `CSV` abgekürzt.


::: {#exm-semikolon-csv-file}
## Semikolon-Daten

```csv
Name;Vorname;Geburtsdatum;Geburtsort;Grösse
Müller;Hans;01.01.1990;Berlin;1,76
Untermayr;Peter;01.01.1980;Wien;1,82
Osterwalder;Urs;01.01.1970;Bern;1,78
```
:::

::: {.callout-important}
## Achtung

Weil beim `CSV`-Format zwei unterschiedliche Trennzeichen verwendet werden, treten beim Importieren oft Fehler auf, weil der Parser für das falsche Trennzeichen verwendet wurde. Bei der Arbeit mit `CSV`-Dateien sollte deshalb eine Datendatei auf das verwendete Trennzeichen geprüft werden. Diese Überprüfung kann entfallen, wenn das Trennzeichen dokumentiert wurde.
:::

::: {.callout-important}
## Achtung
Beim Importieren von CSV-Dateien in der Schweiz muss zusätzlich das Dezimaltrennzeichen geprüft werden. Werden die Daten aus einer Excel-Version mit *deutschen Regionseinstellungen* exportiert, dann wird das Semikolon als Feldtrennzeichen und das Komma als Dezimaltrennzeichen verwendet. Werden die Daten aus einer Excel-Version mit *englischen Regionseinstellungen* exportiert, dann wird das Komma als Feldtrennzeichen und der Punkt als Dezimaltrennzeichen verwendet. 

In der Schweiz wird als Dezimaltrennzeichen wie im Englischen meistens ein Punkt verwendet. Werden Daten aus einer Excel-Version mit *schweizer Regionseinstellungen* werden die Trennzeichen gemischt: Als Feldtrennzeichen wird das Semikolon und als Dezimaltrennzeichen der Punkt verwendet. Das kann beim Import der Daten zu Fehlern führen, wenn das Dezimaltrennzeichen von einem Parser nicht angepasst wurde oder werden kann.
::: 


Das PSV-Format verwendet das Pipe-Symbol (`|`) als Trennzeichen. Während im CSV-Format Überschriften und Werte nicht klar unterschieden werden können, ist beim PSV-Format möglich. Dazu wird nach dem Überschriften eine Zeile mit Minuszeichen (`-`) und Trennzeichen eingefügt, um die Überschriften von den Werten abzugrenzen. Das PSV-Format wird oft als eingebettetes Format in Markdown-Dateien verwendet. 

::: {#exm-psv-file}
## PSV-Daten mit Überschriften

```csv
Name|Vorname|Geburtsdatum|Geburtsort|Grösse
----|-------|------------|----------|------
Müller|Hans|01.01.1990|Berlin|1.76
Untermayr|Peter|01.01.1980|Wien|1.82
Osterwalder|Urs|01.01.1970|Bern|1.78
```
:::

Eine Erweiterung des PSV-Formats ist das sog. *Markdown-Tabellenformat*. Dieses Format erlaubt Zellenformatierungen für die Spalten. Dazu wird im Überschriftentrenner (`-`) ein Doppelpunkt (`:`) verwendet. Die Position des Doppelpunkts legt die Ausrichtung der Spalte fest. Fehlt ein Doppelpunkt oder steht ein Doppelpunkt am Anfang der Spalte formatiert die Spalte linksbündig, ein Doppelpunkt am Ende der Spalte formatiert die Spalte rechtsbündig und ein Doppelpunkt am Anfang und Ende der Spalte formatiert die Spalte zentriert.

::: {#exm-markdown-table}
## Markdown-Tabellenformat

```csv
Name|Vorname|Geburtsdatum|Geburtsort|Grösse
:---|:---:|---:|---|---:
Müller|Hans|01.01.1990|Berlin|1.76
Untermayr|Peter|01.01.1980|Wien|1.82
Osterwalder|Urs|01.01.1970|Bern|1.78
```

Das Ergebnis wird wie folgt dargestellt.

Name|Vorname|Geburtsdatum|Geburtsort|Grösse
:---|:---:|---:|---|---:
Müller|Hans|01.01.1990|Berlin|1.76
Untermayr|Peter|01.01.1980|Wien|1.82
Osterwalder|Urs|01.01.1970|Bern|1.78
:::

## Excel-Arbeitsmappen

Excel-Arbeitsmappen (`xlsx`) fassen mehrere Tabellen zusammen. Excel-Arbeitsmappen werden als komprimiertes Dateiarchiv gespeichert. Deshalb wird das Format von EXCEL-Arbeitsmappen als *Binärformat* bezeichnet. 

Anders als bei Textdateien in denen nur die Werte und deren Struktur kodiert wird, werden bei EXCEL-Arbeitsmappen auch *komplexe Formatierungen*, *Grafiken* und die *Berechnungen* kodiert [@carpenter_ms-xlsx_2023]. Die einzelnen Arbeitsblätter werden zwar als Mengenkodierung behandelt, das eigentliche Dateiformat folgt einer Baumstruktur. 

Excel-Arbeitsmappen fassen mehrere benannte Arbeitsblätter zusammen. Ein Arbeitsblatt ist eine Struktur aus Zeilen und Spalten, die *tabellarisch* organisiert ist. Dadurch ist es möglich, dass mehrere *Tabellen* auf einem Arbeitsblatt vorhanden sind. Falls diese Tabellen nicht explizit als Datentyp `Tabelle` markiert wurden, muss diese Kodierung separat dokumentiert werden.

::: {.callout-tip}
## Praxis

Um Excel-Arbeitsmappen mit anderen Programmiersprachen zu verarbeiten muss die Struktur der Arbeitsmappe berücksichtigt werden. Daten sind immer nur über das Arbeitsblatt zugreifbar. Deshalb muss immer zuerst ein Arbeitsblatt ausgewählt werden, bevor auf die Daten zugegriffen werden kann. 

Arbeitsblätter haben immer zwei Modi: Den *Wertemodus* und den *Formelmodus*. Der gewünschte Moduls muss programmatisch festgelegt werden. 

Im Wertemodus werden die Werte der Zellen angezeigt. Im Formelmodus werden die Formeln der Zellen angezeigt. Wenn eine Zelle nur einen Wert aber keine Formel enthält, wird auch im Formelmodus der Wert bereitgestellt.
:::

## Markup-Formate

Separator-strukturierte Textdateien sind eine einfache Form der *Tabellenkodierung*. Diese Kodierung ist nur für einfache Datenstrukturen geeignet. Für komplexere Datenstrukturen reichen diese Formate nicht aus. 

Ein Ansatz zur Speicherung von komplexen Datenstrukturen als Textdateien sind die sog. *Markup-Sprachen*. Markup-Sprachen sind Textdateien, mit denen Datenstrukturen durch Markierungen beschrieben werden. Sie sind als Datenbeschreibung eine Form der *Baumkodierung*. Dadurch lassen sich beliebig komplexe Datenstrukturen abbilden.

Die zwei am häufigsten benutzten Markupsprachen sind *XML* [@bray_extensible_2008] und *HTML* [@hickson_html_nodate]. Beide Markupsprachen basieren auf dem gemeinsamen *SGML*-Standard [@isoiec_jtc_1sc_34_information_1999]. XML schränkt Datenorganisation ein, so dass Daten immer eindeutig abgebildet werden können. HTML stellt die Syntax für die Strukturierung von Webseiten bereit. Bei HTML stehen deshalb die Abbildung von Datenstrukturen nicht im Vordergrund.

Beide Formate verwenden sog. *Tags* als Markierungen im Text. Ein Tag wird durch eine öffnende spitze Klammer eingeleitet und eine schliessende spitze Klammer beendet. Das Tag hat einen Namen, welcher unmittelbar der öffnenden Klammer folgt. Tags können abgeschlossen werden, indem ein Schrägstrich (`/`) dem Tag-Namen vorangestellt wird.

::: {#exm-markup-tag}
## Markup-Tag

```xml
<tag-name></tag-name>
```
::: 

Tags können ausserdem *Attribute* enthalten. Attribute sind Schlüssel-Wert-Paare, die dem Tag zugeordnet sind. Die Werte von Attributen werden in der Regel in Anführungszeichen gesetzt.

::: {#exm-markup-tag-mit-attribut}
## Markup-Tag mit einem Attribut

```xml
<tag-name name="Wert"></tag-name>
```
::: 

Tags können *geschachtelt* werden, wobei die Schachtelung durch die Reihenfolge der Tags festgelegt wird.


::: {#exm-markup-tag-nested}
## Geschachtelte Tags

```xml
<tag-name><unter-tag>Wert</unter-tag></tag-name>
```
::: 

Beide Markup-Sprachen ignorieren Leerzeichen und Zeilenumbrüche. Dadurch können die Daten in einer Markup-Sprache beliebig formatiert werden, ohne die Bedeutung der Daten zu verändern. Entsprechend sind @exm-markup-tag-nested und @exm-markup-tag-nested-format gleichwertig.

::: {#exm-markup-tag-nested-format}
## Geschachtelte Tags mit Zeilenumbrüchen und Leerzeichen

```xml
<tag-name>
   <unter-tag>
      Wert
   </unter-tag>
</tag-name>
```
::: 

Die Flexibilität von Markup-Sprachen hat die Folge, dass sie meistens sehr komplex sind und sich nicht direkt in die Datenstrukturen von Programmiersprachen übersetzen lassen. Deshalb wird für Markup-Sprachen ein sog. *Document-Object-Model* (DOM) definiert, damit die Daten in die für Programmiersprachen üblichen Datenstrukturen übersetzt werden können.

### XML 

XML wurde als flexibles Datenbeschreibungsformat konzipiert, dass an die Anforderungen unterschiedlicher Anwendungen angepasst werden kann. XML gibt die Formatierung von Datenserialisierungen vor. Die eigentlichen Datenstrukturen müssen über ein separates Schema spezifiziert werden. Deshalb ist XML eine *Metasprache* und keine Markup-Sprache im eigentlichen Sinn.

Ein XML-Tag steht dabei für eine Datenstruktur. Bei geschachtelten Strukturen erfordert XML, das die hierarchischen Abhängigkeiten explizit im Format markiert werden. Deshalb müssen geschachtelte Tags immer in der umgekehrten Reihenfolge geschlossen werden, in der sie geöffnet wurden.

Die Namen für XML-Tags dürfen frei gewählt werden, wobei Leerzeichen im Namen von Tags und Attributen verboten sind.

XML kann Werte als *Attribut* oder als *Inhalt* eines Tags kodieren. Die Wahl der Kodierung ist abhängig vom vorgegebenen Datenschema. Für neue Datenschema hat sich eingebürgert, Werte als Inhalte in hierarchischer Form zu kodieren. 

::: {#exm-xml-format-meta-attribute}
## XML-Format einer tabellarischen Struktur in hierarchischer Form

```xml
<daten>
  <person>
   <name>Müller</name> 
   <vorname>Hans</vorname> 
   <geburtsort>Berlin</geburtsort> 
   <geburtsdatum>01.01.1990</geburtsdatum>
   <grösse>1.76</grösse>
  </person>
  <person>
   <name>Untermayr</name> 
   <vorname>Peter</vorname> 
   <geburtsort>Wien</geburtsort> 
   <geburtsdatum>01.01.1980</geburtsdatum>
   <grösse>1.82</grösse>
  </person>
  <person>
   <name>Osterwalder</name> 
   <vorname>Urs</vorname> 
   <geburtsort>Bern</geburtsort> 
   <geburtsdatum>01.01.1970</geburtsdatum>
   <grösse>1.78</grösse>
  </person>
</daten>
```
:::

Attribute sollten nur für die Kodierung von ergänzenden Daten verwendet. Zu solchen Daten gehört beispielsweise der Datentyp eines Wertes, weil XML alle Werte nur als Zeichenketten abbildet.

::: {#exm-xml-format-meta-attribute}
## XML-Format einer tabellarischen Struktur mit ergänzenden Attributen

```xml
<daten>
  <person>
   <name typ="text">Müller</name> 
   <vorname typ="text">Hans</vorname> 
   <geburtsort typ="text">Berlin</geburtsort> 
   <geburtsdatum typ="datum">01.01.1990</geburtsdatum>
   <grösse typ="zahl">1.76</grösse>
  </person>
  <person>
   <name typ="text">Untermayr</name> 
   <vorname typ="text">Peter</vorname> 
   <geburtsort typ="text">Wien</geburtsort> 
   <geburtsdatum typ="datum">01.01.1980</geburtsdatum>
   <grösse typ="zahl">1.82</grösse>
  </person>
  <person>
   <name typ="text">Osterwalder</name> 
   <vorname typ="text">Urs</vorname> 
   <geburtsort typ="text">Bern</geburtsort> 
   <geburtsdatum typ="datum">01.01.1970</geburtsdatum>
   <grösse typ="zahl">1.78</grösse>
  </person>
</daten>
```
:::

Die Kodierung von Werten als Attribute findet sich nur noch in älteren XML-Dokumenten.

::: {#exm-xml-format-werte-attribute}
## XML-Format einer tabellarischen Struktur mit Werten als Attribute

```xml
<daten>
  <person name="Müller" vorname="Hans" geburtsort="Berlin" 
          geburtsdatum="01.01.1990" grösse="1.76"></person>
  <person name="Untermayr" vorname="Peter" geburtsort="Wien" 
          geburtsdatum="01.01.1980" grösse="1.82"></person>
  <person name="Osterwalder" vorname="Urs" geburtsort="Bern" 
          geburtsdatum="01.01.1970" grösse="1.78"></person>
</daten>
```
:::

Aus den Beispielen wird deutlich, dass die Kodierung im XML-Format zwar sehr flexibel ist, aber auch sehr komplex werden kann und wenig speichereffizient ist. Das kann ein Problem werden, wenn viele Daten zwischen Rechnern übertragen werden müssen. Deshalb wird XML heute nur noch für Anwendungen verwendet, bei denen die Flexibilität der Kodierung wichtiger ist als die Speichereffizienz.

::: {.callout-note}
Eine Anwendung, die alle Daten im XML-Format speichert ist *Excel*. Diese Daten werden aber hinter den Kulissen in einem Binärformat gespeichert. Deshalb ist es nicht möglich, Excel-Arbeitsmappen direkt als XML-Dateien zu öffnen.
:::

### HTML 

HTML wurde als Format für die Strukturierung von Webseiten entwickelt. Deshalb ist HTML eine echte *Markup-Sprache*, bei der die Namen der zulässigen Tags vorgegeben ist. Bei HTML steht dabei die Strukturierung von Webseiten im Vordergrund.

HTML ist für die Datenkodierung nur von Bedeutung, wenn Daten als Webseiten dargestellt werden sollen. Tabellarische Daten können auf Webseiten leicht identifiziert werden, weil es dafür spezielle HTML-Tags gibt.

::: {#exm-html-table}
## HTML-Format einer tabellarischen Struktur

```html
<table>
  <tr>
    <th>Name</th>
    <th>Vorname</th>
    <th>Geburtsdatum</th>
    <th>Geburtsort</th>
    <th>Grösse</th>
  </tr>
  <tr>
    <td>Müller</td>
    <td>Hans</td>
    <td>01.01.1990</td>
    <td>Berlin</td>
    <td>1.76</td>
  </tr>
  <tr>
    <td>Untermayr</td>
    <td>Peter</td>
    <td>01.01.1980</td>
    <td>Wien</td>
    <td>1.82</td>
  </tr>
  <tr>
    <td>Osterwalder</td>
    <td>Urs</td>
    <td>01.01.1970</td>
    <td>Bern</td>
    <td>1.78</td>
  </tr>
</table>
```
:::

::: {.callout-tip}
## Praxis

Der Datenaustausch über HTML-Tabellen ist inzwischen vernachlässigbar. HTML-Tabellen werden fast ausschliesslich für die Darstellung von Daten innerhalb von Anwendungen verwendet. Es gibt praktische keine Datenquellen mehr, deren Daten ausschliesslich als HTML-Tabellen vorliegen. Häufig werden Mess-Daten auch nicht mehr auf Web-Seiten bereitgestellt, sondern nur über Dateien in einem effizienteren Format verlinkt.
:::


## JSON

Mit der wachsenden Popularität des WWW wurde eine effizientere Form zur Kodierung komplexer Datenstrukturen erforderlich, um die Komplexität von Markupsprachen zu umgehen. Deshalb wurde die *JavaScript Object Notation* (JSON) entwickelt. JSON ist eine einfache Form der *Baumkodierung*. JSON ist eine *Untermenge* der JavaScript-Syntax und umfasst nur die Elemente zur Beschreibung von Datenstrukturen. Ein JSON-Dokument beschreibt deshalb immer eine gültige JavaScript-Datenstruktur. Deshalb kann JSON von JavaScript-Programmen in die üblichen Datenstrukturen überführt werden. Das vereinfacht die Programmierung und die Interaktivität von Anwendungen, die in Webbrowsern ausgeführt werden.

JSON ist ein standardisiertes Datenformat [@bray_javascript_2017] und wird inzwischen von allen wichtigen Programmiersprachen unterstützt. Auch JSON ist ein *Markup-Format*, bei dem die Markierungen der JavaScript-Syntax folgen. 

JSON kennt nur sechs Datentypen, wodurch die Kodierung sehr einfach umzusetzen ist. Die Datentypen sind:

- Zahlen
- Zeichenketten
- Boole'sche Werte
- Listen
- Objekte
- `null` (undefiniert)

Zeichenketten müssen immer durch doppelte Anführungszeichen (`"`) eingeleitet und abgeschlossen werden.

Der Listendatentyp wird durch Block-Klammern (`[` und `]`) markiert. 

Der Objekt-Datentyp gibt dem Format seinen Namen. Objekte werden durch geschweifte Klammern (`{` und `}`) markiert und sind eine *Menge* von *Schlüssel-Wert-Paaren*. Die Schlüssel sind Zeichenketten, wobei jeder Schlüssel nur einmal pro Objekt vorkommen darf. Die Werte können von beliebigen JSON-Datentypen sein. Schlüssel und Werte sind immer durch einen Doppelpunkt getrennt.

Tabellarische Strukturen lassen sich in JSON auf zwei Arten abbilden: 

- Als Liste von Objekten
- Als Objekt mit Listen

Die erste Variante ist die gebräuchlichste, weil beim die Bedeutung der zusammenhängenden Werte durch die Schlüssel meistens einfacher verarbeitet werden kann.

::: {#exm-json-liste-von-objekten}
## Tabellenstruktur im JSON-Format als Liste von Objekten

```json
[
    {
        "name": "Müller",
        "vorname": "Hans",
        "geburtsdatum": "01.01.1990",
        "geburtsort": "Berlin",
        "grösse": 1.76
    },
    {
        "name": "Untermayr",
        "vorname": "Peter",
        "geburtsdatum": "01.01.1980",
        "geburtsort": "Wien",
        "grösse": 1.82
    },
    {
        "name": "Osterwalder",
        "vorname": "Urs",
        "geburtsdatum": "01.01.1970",
        "geburtsort": "Bern",
        "grösse": 1.78
    }
]
```
:::

Die Objekt-mit-Listen Strukturierung eignet sich, wenn die Vektorstruktur der Daten im Vordergrund steht. In diesem Fall werden die Werte in einer Liste zusammengefasst und die Schlüssel werden als Index verwendet.

::: {#exm-json-objekt-mit-listen}
## Tabellenstruktur im JSON-Format als Objekt mit Listen

```json
{
    "name": ["Müller", "Untermayr", "Osterwalder"],
    "vorname": ["Hans", "Peter", "Urs"],
    "geburtsdatum": ["01.01.1990", "01.01.1980", "01.01.1970"],
    "geburtsort": ["Berlin", "Wien", "Bern"],
    "grösse": [1.76, 1.82, 1.78]
}
```
:::

::: {.callout-warning}
Die Objekt-mit-Listen-Strukturierung ist weniger verbreitet, weil diese Strukturierung den Erhalt der Zusammenhänge zwischen den Werten nicht sicherstellt. Es wäre also denkbar, die Werte einer Liste in einer anderen Reihenfolge neu anzuordnen, ohne dass über die Positionen zusammenhängenden Werte ebenfalls angepasst werden. 

Dieses Problem besteht bei der Liste-von-Objekten-Strukturierung nicht.
:::

## YAML

In den letzten Jahren findet eine weitere Formatierung immer häufigere Verwendung: YAML [@ben-kiki_yaml_2021]. YAML ist eine einfache "menschenfreundliche" Formatierung, die auf der Einrückung von Textblöcken basiert. YAML ist ein Obermenge von JSON und deshalb ist jedes JSON-Format gleichzeitig ein gültiges YAML-Format. Das Ziel des YAML-Formats ist das vereinfachte Erstellen und Bearbeiten von strukturierten Datendokumenten durch Menschen. 

YAML hat die gleichen Datentypen wie JSON und folgt den gleichen Prinzipien zur Datenkodierung. Dadurch hat YAML die gleichen Vorteile wie JSON. YAML erlaubt zusätzlich die Verwendung von Kommentaren, die in JSON nicht vorgesehen sind. Solche Kommentare dienen nur der Dokumentation für die menschliche Interaktion und werden beim Laden eines YAML-Dokuments ignoriert. 

Der Auffälligste Unterschied zwischen YAML und JSON ist die Verwendung von Einrückungen zur Strukturierung von Daten. Dadurch ist YAML für Menschen etwas leichter lesbar und verständlich. Auch müssen Zeichenketten meistens nicht explizit markiert werden. YAML legt Regeln zur automatischen Erkennung des Datentyps fest. So müssen nur in Ausnahmefällen Zeichenketten explizit markiert werden, was bspw. zur Unterscheidung von Wahrheitswerten und Zeichenketten müssen Zeichenketten explizit markiert werden, wenn eine Zeichenkette nur aus einem Schlüsselwort für einen Boole'schen Wert besteht. Zeichenketten müssen auch mit doppelten Anführungszeichen (`"`) markiert werden, wenn die Zeichenkette einen Doppelpunkt enthält.

::: {#exm-yaml-format-specialstring}
## Zeichenkettenmarkierung in YAML

```YAML
# Zeichenkette mit Doppelpunkt
- "Müller: Hans"
# Objekt mit Schlüssel "Müller" und Wert "Hans"
- Müller: Hans
# Zeichenkette mit Wahrheitswert
- "true"
- "no"
# Wahrheitswerte werden intern in Wahr und Falsch umgewandelt
- true
- no
```
:::


Weil YAML die Objektstruktur visuell unterstützt, erfolgt eine Datenkodierung von tabellarischen Strukturen in der Regel über Listen von Objekten.

::: {#exm-yaml-liste-von-objekten}
## Tabellenstruktur im YAML-Format als Liste von Objekten

```YAML
- name: Müller
  vorname: Hans
  geburtsdatum: 01.01.1990
  geburtsort: Berlin
  grösse: 1.76
- name: Untermayr
  vorname: Peter
  geburtsdatum: 01.01.1980
  geburtsort: Wien
  grösse: 1.82
- name: Osterwalder
  vorname: Urs
  geburtsdatum: 01.01.1970
  geburtsort: Bern
  grösse: 1.78
```
:::

## Dateiformate und Versionierung

Bei der Versionierung von Daten spielt das Dateiformat eine zentrale Rolle.

Daten in separator-strukturierte Textdateien oder im YAML-Format lassen sich besonders einfach versionieren, weil sie als zeilenorientierte Formate direkt von den Versionierungssystemen unterstützt werden.

Bei XML- und JSON-Daten ist die Situation etwas komplexer: Diese Formate sind nicht zeilenorientiert und die gleiche Struktur kann auf unterschiedliche Arten im gleichen Format serialisiert werden. Dadurch wird die Versionierung dieser Dateiformate erschwert. 

Die Versionierung von Binärformaten ist noch komplexer, weil Versionierungssystem diese Formate nicht auf der Inhaltsebene unterstützen. Deshalb ist es üblich, Daten in diesem Formaten vor der Versionierung in ein zeilenorientiertes Format überführt werden. Das betrifft sehr häufig Excel-Arbeitsmappen, weil sich die Binärdaten bei jedem *Zugriff* ändern, ohne dass die Daten selbst verändert wurden. 

::: {.callout-tip}
## Praxis

Es ist üblich Daten anstatt in Excel-Arbeitsmappen in CSV-Dateien zu speichern, um die Daten versionieren zu können. Die CSV-Dateien werden dann in Excel als externe Daten importiert.
:::
