---
title: Neues in C# 8.0 – C#-Leitfaden
description: Überblick über die neuen Funktionen von C# 8.0. Dieser Artikel ist auf dem neuesten Stand mit Vorschauversion 2.
ms.date: 02/12/2019
ms.openlocfilehash: 1aa5a200f84b35fda3c33a900655249d07000e8e
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835433"
---
# <a name="whats-new-in-c-80"></a>Neues in C# 8.0

Wir haben viele Verbesserungen an der C#-Sprache vorgenommen, die Sie bereits mit Vorschau 2 ausprobieren können. Diese neuen Funktionen wurde in Vorschauversion 2 hinzugefügt:

- [Verbesserungen am Musterabgleich](#more-patterns-in-more-places):
  * [switch-Ausdrücke](#switch-expressions)
  * [Eigenschaftsmuster](#property-patterns)
  * [Tupelmuster](#tuple-patterns)
  * [Positionsmuster](#positional-patterns)
- [using-Deklarationen](#using-declarations)
- [Statische lokale Funktionen](#static-local-functions)
- [Verwerfbare Referenzstrukturen](#disposable-ref-structs)

Die folgenden Sprachfunktionen sind erstmals in der Vorschauversion 1 von C# 8.0 erschienen:

- [Nullwerte zulassende Verweistypen](#nullable-reference-types)
- [Asynchrone Streams](#asynchronous-streams)
- [Indizes und Bereiche](#indices-and-ranges)

> [!NOTE]
> Dieser Artikel wurde zuletzt für Vorschauversion 2 von C# 8.0 aktualisiert.

Der Rest dieses Artikels beschreibt diese Funktionen kurz. Wenn ausführliche Artikel verfügbar sind, werden Links zu diesen Tutorials und Übersichten bereitgestellt.

## <a name="more-patterns-in-more-places"></a>Weitere Muster an mehr Orten

**Musterabgleich** bietet Tools zur Bereitstellung formabhängiger Funktionalität für verwandte, aber unterschiedliche Datentypen. C# 7.0 führte eine Syntax für Typmuster und konstante Muster ein, indem der Ausdruck [`is`](../language-reference/keywords/is.md) und die Anweisung [`switch`](../language-reference/keywords/switch.md) verwendet wurden. Diese Funktionen stellten die ersten vorläufigen Schritte zur Unterstützung von Programmierparadigmen dar, bei denen Daten und Funktionalität getrennt voneinander sind. Da sich die Branche immer mehr auf Mikroservices und andere Cloud-basierte Architekturen konzentriert, werden andere Sprachtools benötigt.

C# 8.0 erweitert dieses Vokabular, sodass Sie mehr Musterausdrücke an mehreren Stellen in Ihrem Code verwenden können. Berücksichtigen Sie diese Funktionen, wenn Ihre Daten und Funktionen getrennt sind. Berücksichtigen Sie den Musterabgleich, wenn Ihre Algorithmen von einer anderen Tatsache als dem Runtimetyp eines Objekts abhängen. Diese Verfahren bieten eine weitere Möglichkeit, Entwürfe auszudrücken.

Zusätzlich zu neuen Mustern an neuen Orten fügt C# 8.0 **rekursive Muster** hinzu. Das Ergebnis eines beliebigen Musterausdrucks ist ein Ausdruck. Ein rekursives Muster ist einfach ein Musterausdruck, der auf die Ausgabe eines anderen Musterausdrucks angewendet wird.

### <a name="switch-expressions"></a>switch-Ausdrücke

Häufig liefert eine [`switch`](../language-reference/keywords/switch.md)-Anweisung in jedem ihrer `case`-Blöcke einen Wert. Mit **switch-Ausdrücken** können Sie eine präzisere Ausdruckssyntax verwenden. Es gibt weniger repetitive `case`- und `break`-Schlüsselwörter und weniger geschweifte Klammern.  Betrachten Sie als Beispiel die folgende Enumeration, die die Farben des Regenbogens enumeriert:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Blue,
    Indigo,
    Violet
}
```

Sie können einen `Rainbow`-Wert in seine RGB-Werte konvertieren, indem Sie das folgende Verfahren verwenden, das einen switch-Ausdruck enthält:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Es gibt hier verschiedene Syntaxverbesserungen:

- Die Variable steht vor dem `switch`-Schlüsselwort. Die unterschiedliche Reihenfolge macht es optisch einfach, den switch-Ausdruck von der switch-Anweisung zu unterscheiden.
- Die `case`- und `:`-Elemente werden durch `=>` ersetzt. Es ist präziser und intuitiver.
- Der `default`-Fall wird durch eine `_`-Ausschlussvariable ersetzt.
- Die Textkörper sind Ausdrücke, keine Anweisungen.

Stellen Sie dies mit dem entsprechenden Code unter Verwendung der klassischen `switch`-Anweisung gegenüber:

```csharp
public static RGBColor fromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>Eigenschaftsmuster

Mit dem **Eigenschaftsmuster** können Sie die Eigenschaften des untersuchten Objekts anpassen. Denken Sie an eine eCommerce-Website, die die Umsatzsteuer auf der Grundlage der Adresse des Käufers berechnen muss. Diese Berechnung ist keine Kernaufgabe einer `Address`-Klasse. Sie wird sich im Laufe der Zeit ändern, wahrscheinlich häufiger als Adressformatänderungen. Die Höhe der Umsatzsteuer hängt von der `State`-Eigenschaft der Adresse ab. Die folgende Methode verwendet das Eigenschaftsmuster, um die Umsatzsteuer aus der Adresse und dem Preis zu berechnen:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Ein Musterabgleich erstellt eine präzise Syntax,. um diesen Algorithmus auszudrücken.

### <a name="tuple-patterns"></a>Tupelmuster

Einige Algorithmen sind von mehreren Eingaben abhängig. **Tupelmuster** erlauben Ihnen, auf Grundlage mehrerer Werte, ausgedrückt als ein [Tupel](../tuples.md), zu wechseln („switch“).  Der folgende Code zeigt einen switch-Ausdruck für das Spiel *Stein, Schere, Papier* (Schnick, Schnack, Schnuck):

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

Die Meldungen zeigen den Gewinner an. Der Fall „Verwerfen“ („case discard“) stellt die drei Kombinationen für Unentschieden oder andere Texteingaben dar.

### <a name="positional-patterns"></a>Positionsmuster

Einige Typen umfassen eine `Deconstruct`-Methode, die ihre Eigenschaften in diskrete Variablen dekonstruiert. Wenn auf eine `Deconstruct`-Methode zugegriffen werden kann, können Sie **Positionsmuster** verwenden, um Eigenschaften des Objekts zu untersuchen, und diese Eigenschaften für ein Muster verwenden.  Beachten Sie die folgende `Point`-Klasse, die eine `Deconstruct`-Methode umfasst, um diskrete Variablen für `X` und `Y` zu erstellen:

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

Die folgende Methode verwendet das **Positionsmuster**, um die Werte von `x` und `y` zu extrahieren. Dann wird mit einer `when`-Klausel der Quadrant des Punktes bestimmt:

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

Das Muster der Ausschussvariable im vorherigen Switch stimmt überein, wenn entweder `x` oder `y`, aber nicht beide, 0 ist. Ein switch-Ausdruck muss entweder einen Wert erzeugen oder eine Ausnahme auslösen. Wenn keiner der Fälle übereinstimmt, löst der switch-Ausdruck eine Ausnahme aus. Der Compiler erzeugt für Sie eine Warnung, wenn Sie nicht alle möglichen Fälle in Ihrem switch-Ausdruck abdecken.

## <a name="using-declarations"></a>using-Deklarationen

Eine **using-Deklaration** ist eine Variablendeklaration, der das Schlüsselwort `using` vorangestellt ist. Es teilt dem Compiler mit, dass die zu deklarierende Variable am Ende des umschließenden Bereichs angeordnet werden soll. Sehen Sie sich beispielsweise den folgenden Code an, der eine Textdatei schreibt:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

Im vorhergehenden Beispiel wird die Datei angeordnet, wenn die schließende Klammer für die Methode erreicht ist. Dies ist das Ende des Bereichs, in dem `file` deklariert wird. Der vorhergehende Code entspricht dem folgenden Code unter Verwendung der klassischen [using statements](../language-reference/keywords/using-statement.md)-Anweisung:


```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

Im vorhergehenden Beispiel wird die Datei angeordnet, wenn die der `using`-Anweisung zugeordnete schließende Klammer erreicht ist.

In beiden Fällen generiert der Compiler den Aufruf von `Dispose()`. Der Compiler erzeugt einen Fehler, wenn der Ausdruck in der using-Anweisung nicht verfügbar ist.

## <a name="static-local-functions"></a>Statische lokale Funktionen

Sie können nun den `static`-Modifikator zu lokalen Funktionen hinzufügen, um sicherzustellen, dass die lokale Funktion keine Variablen aus dem umschließenden Bereich erfasst (referenziert). Dadurch wird `CS8421` erzeugt, „Eine statische lokale Funktion kann keine Referenz auf <variable> enthalten.“ 

Betrachten Sie folgenden Code. Die lokale Funktion `LocalFunction` greift auf die Variable `y` zu, die im umschließenden Bereich (die Methode `M`) deklariert ist. Daher kann `LocalFunction` nicht mit dem `static`-Modifikator deklariert werden:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Der folgende Code enthält eine statische lokale Funktion. Er kann statisch sein, da er nicht auf Variablen im umschließenden Bereich zugreift:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Verwerfbare Referenzstrukturen

Ein mit dem `ref`-Modifikator deklarierter `struct` darf keine Schnittstellen und damit auch keine <xref:System.IDisposable> implementieren. Aus diesem Grund Aktivieren einer `ref struct` um verworfen werden, muss eine zugängliche `void Dispose()` Methode. Dies gilt auch für `readonly ref struct`-Deklarationen.

## <a name="nullable-reference-types"></a>Nullwerte zulassende Verweistypen

In einem Nullwerte zulassenden Anmerkungskontext, wird jede Variable eines Referenztyps als **keine Nullwerte zulassender Referenztyp** betrachtet. Wenn Sie angeben möchten, dass eine Variable Null sein kann, müssen Sie den Typnamen mit `?` ergänzen, um die Variable als **keine Nullwerte zulassenden Verweistyp** zu deklarieren.

Wenn der Verweistyp keine Nullwerte zulässt, verwendet der Compiler die Flussanalyse, um sicherzustellen, dass lokale Variablen bei der Deklaration auf einen Nicht-Null-Wert initialisiert werden. Felder müssen während der Erstellung initialisiert werden. Der Compiler erzeugt eine Warnung, wenn die Variable nicht durch einen Aufruf eines der verfügbaren Konstruktoren oder durch einen Initialisierer festgelegt wird. Darüber hinaus kann Verweistypen, die keine Nullwerte zulassen, kein Wert zugewiesen werden, der Null sein könnte.

Verweistypen, die keine Nullwerte zulassen werden nicht überprüft, um sicherzustellen, dass sie nicht mit Null belegt oder initialisiert werden. Der Compiler verwendet jedoch die Flussanalyse, um sicherzustellen, dass jede Variable eines Verweistypen, der Nullwerte zulässt, gegen null geprüft wird, bevor auf sie zugegriffen oder einem nicht Verweistypen zugewiesen wird, der Nullwerte zulässt.

Mehr über die Funktion erfahren Sie in der Übersicht der [Verweistypen, die Nullwerte zulassen](../nullable-references.md). Probieren Sie es selbst in einer neuen Anwendung in diesem [Tutorial für Verweistypen, die Nullwerte zulassen](../tutorials/nullable-reference-types.md) aus. Weitere Informationen über die Schritte zur Migration einer bestehenden Codebasis, um Verweistypen zu nutzen, die Nullwerte zulassen, finden Sie im Tutorial [Migration einer Anwendung zur Verwendung Nullwerte zulassenden Verweistypen](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Asynchrone Streams

Ab C# 8.0 können Sie Streams asynchron erstellen und nutzen. Eine Methode, die einen asynchronen Stream zurückgibt, hat drei Eigenschaften:

1. Die Deklaration erfolgte mit dem `async`-Modifikator.
1. Es wird <xref:System.Collections.Generic.IAsyncEnumerable%601> zurückgegeben.
1. Das Verfahren enthält `yield return`-Anweisungen, um aufeinanderfolgende Elemente im asynchronen Stream zurückzugeben.

Die Verwendung eines asynchronen Streams erfordert, dass Sie das Schlüsselwort `await` vor dem Schlüsselwort `foreach` hinzufügen, wenn Sie die Elemente des Streams auflisten. Das Hinzufügen des Schlüsselwortes `await` erfordert, dass die Methode, die den asynchronen Strom enumiert, mit dem Modifikator `async` deklariert wird und einen für eine `async`-Methode zulässigen Typ zurückgibt. In der Regel ist dies die Rückgabe von <xref:System.Threading.Tasks.Task> oder <xref:System.Threading.Tasks.Task%601>. Es kann auch <xref:System.Threading.Tasks.ValueTask> oder <xref:System.Threading.Tasks.ValueTask%601> sein. Eine Methode kann einen asynchronen Stream sowohl verwenden als auch erzeugen, was bedeutet, dass sie <xref:System.Collections.Generic.IAsyncEnumerable%601> zurückgeben würde. Der folgende Code erzeugt eine Sequenz von 1 bis 20 und wartet 100 ms zwischen der Generierung jeder Zahl:

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

Die Enumeration der Sequenz erfolgt mit der `await foreach`-Anweisung:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Sie können asynchrone Streams selbst in unserem Tutorial zum [Erstellen und Verwenden von asynchronen Streams](../tutorials/generate-consume-asynchronous-stream.md) ausprobieren.

## <a name="indices-and-ranges"></a>Indizes und Bereiche

Bereiche und Indizes bieten eine prägnante Syntax zur Angabe von Teilbereichen in einem Array, <xref:System.Span%601> oder <xref:System.ReadOnlySpan%601>.

Sie können einen Index  **from the end** aus angeben. Sie geben **from the end** mithilfe des `^`-Operators an. Sie kennen `array[2]`. Damit wird das Element „2 from the start“ bezeichnet. Jetzt bezeichnet `array[^2]` das Element „2 from the end“. Der Index `^0` bedeutet „das Ende“ oder der Index, der dem letzten Element folgt.

Sie können einen **Bereich** mit dem **Bereichsoperator** angeben: `..`. So gibt beispielsweise `0..^0` den gesamten Bereich des Arrays an: 0 vom Anfang bis zum Ende, aber nicht einschließlich 0 vom Ende. Jeder der beiden Operanden kann „from the start“ oder „from the end“ verwenden. Darüber hinaus kann jeder der beiden Operanden weggelassen werden. Die Standardeinstellungen sind `0` für den Startindex und `^0` für den Endindex.

Schauen wir uns einige Beispiele an. Betrachten Sie das folgende Array, kommentiert mit seinem Index „from the start“ und „from the end“:

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};
```

Der Index jedes Elements verstärkt das Konzept von „from the start“ und „from the end“, und dass Bereiche das Ende des Bereichs ausschließen. Der „start“ des gesamten Arrays ist das erste Element. Das „end“ des gesamten Arrays liegt *hinter* dem letzten Element.

Sie können das letzte Wort mit dem `^1`-Index abrufen:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Der folgende Code erzeugt einen Teilbereich mit den Worten „quick“, „brown“ und „fox“. Er enthält `words[1]` bis `words[3]`. Das Element `words[4]` gehört nicht zum Bereich.

```csharp
var brownFox = words[1..4];
```

Der folgende Code erzeugt einen Teilbereich mit „lazy“ und „dog“. Dazu gehören `words[^2]` und `words[^1]`. Der Endindex `words[^0]` ist nicht enthalten:

```csharp
var lazyDog = words[^2..^0];
```

Die folgenden Beispiele erstellen Bereiche, die am Anfang, am Ende und auf beiden Seiten offen sind:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

Sie können Bereiche auch als Variablen deklarieren:

```csharp
Range phrase = 1..4;
```

Der Bereich kann dann innerhalb der Zeichen `[` und `]` verwendet werden:

```csharp
var text = words[phrase];
```
