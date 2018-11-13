---
title: Zahlen in C# – Einführung in das C#-Tutorial
description: Machen Sie sich mit C# vertraut, indem Sie numerische Typen, ihre Eigenschaften und Methoden erkunden.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 52feb91fc011902f1e30f6b747512a7e0908bfbf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197456"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="a63bd-103">Bearbeiten von Ganzzahlen und Gleitkommazahlen in C#</span><span class="sxs-lookup"><span data-stu-id="a63bd-103">Manipulate integral and floating point numbers in C#</span></span> #

<span data-ttu-id="a63bd-104">Dieses interaktive Tutorial erläutert die numerischen Typen in C#.</span><span class="sxs-lookup"><span data-stu-id="a63bd-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="a63bd-105">Sie schreiben einen Teil des Codes, kompilieren diesen und führen ihn aus.</span><span class="sxs-lookup"><span data-stu-id="a63bd-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="a63bd-106">Das Tutorial enthält eine Reihe von Lektionen, in denen Zahlen und mathematische Vorgänge in C# untersucht werden.</span><span class="sxs-lookup"><span data-stu-id="a63bd-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="a63bd-107">In diesen Lektionen lernen Sie die Grundlagen der Programmiersprache C# kennen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="a63bd-108">Für dieses Tutorial benötigen Sie einen Computer, den Sie für die Entwicklung nutzen können.</span><span class="sxs-lookup"><span data-stu-id="a63bd-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a63bd-109">Das .NET-Thema [Erste Schritte in 10 Minuten](https://www.microsoft.com/net/core) umfasst Anweisungen zum Einrichten Ihrer lokalen Entwicklungsumgebung auf einem Mac-, Windows- oder Linux-PC.</span><span class="sxs-lookup"><span data-stu-id="a63bd-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="a63bd-110">Einen schnellen Überblick über die Befehle, die Sie verwenden werden, finden Sie im Artikel [Einführung in Entwicklungstools](local-environment.md), der Links zu weiteren Ressourcen enthält.</span><span class="sxs-lookup"><span data-stu-id="a63bd-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="a63bd-111">Erkunden von arithmetischen Operationen mit ganzen Zahlen</span><span class="sxs-lookup"><span data-stu-id="a63bd-111">Explore integer math</span></span>

<span data-ttu-id="a63bd-112">Erstellen Sie ein Verzeichnis mit dem Namen **numbers-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="a63bd-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="a63bd-113">Machen Sie dieses Verzeichnis zum aktuellen Verzeichnis, und führen Sie `dotnet new console -n NumbersInCSharp -o .` aus.</span><span class="sxs-lookup"><span data-stu-id="a63bd-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="a63bd-114">Öffnen Sie **Program.cs** in Ihrem bevorzugten Editor, und ersetzen Sie die Zeile `Console.Writeline("Hello World!");` durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a63bd-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="a63bd-115">Führen Sie diesen Code aus, indem Sie `dotnet run` in Ihr Befehlsfenster eingeben.</span><span class="sxs-lookup"><span data-stu-id="a63bd-115">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="a63bd-116">Sie haben soeben eine der grundlegenden arithmetischen Operationen mit ganzen Zahlen kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="a63bd-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="a63bd-117">Der `int`-Typ steht für **integer**, d.h. eine positive oder negative ganze Zahl.</span><span class="sxs-lookup"><span data-stu-id="a63bd-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="a63bd-118">Sie verwenden zum Addieren das `+`-Symbol.</span><span class="sxs-lookup"><span data-stu-id="a63bd-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="a63bd-119">Zu den anderen häufig verwendeten arithmetischen Operationen für ganze Zahlen zählen Folgende:</span><span class="sxs-lookup"><span data-stu-id="a63bd-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="a63bd-120">`-` zur Subtraktion</span><span class="sxs-lookup"><span data-stu-id="a63bd-120">`-` for subtraction</span></span>
- <span data-ttu-id="a63bd-121">`*` zur Multiplikation</span><span class="sxs-lookup"><span data-stu-id="a63bd-121">`*` for multiplication</span></span>
- <span data-ttu-id="a63bd-122">`/` zur Division</span><span class="sxs-lookup"><span data-stu-id="a63bd-122">`/` for division</span></span>

<span data-ttu-id="a63bd-123">Erkunden Sie zunächst die anderen Operationen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-123">Start by exploring those different operations.</span></span> <span data-ttu-id="a63bd-124">Fügen Sie diese Zeilen nach der Zeile hinzu, die den Wert von `c` schreibt:</span><span class="sxs-lookup"><span data-stu-id="a63bd-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="a63bd-125">Führen Sie diesen Code aus, indem Sie `dotnet run` in Ihr Befehlsfenster eingeben.</span><span class="sxs-lookup"><span data-stu-id="a63bd-125">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="a63bd-126">Wenn Sie möchten, können Sie auch experimentieren, indem Sie mehrere arithmetische Operationen in der gleichen Zeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="a63bd-127">Testen Sie zum Beispiel `c = a + b - 12 * 17;`.</span><span class="sxs-lookup"><span data-stu-id="a63bd-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="a63bd-128">Das Kombinieren von Variablen und konstanten Zahlen ist erlaubt.</span><span class="sxs-lookup"><span data-stu-id="a63bd-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="a63bd-129">Bei Ihren ersten Schritten mit C# (oder einer anderen Programmiersprache) kann es zu Fehlern kommen, wenn Sie Codes schreiben.</span><span class="sxs-lookup"><span data-stu-id="a63bd-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="a63bd-130">Der **Compiler** findet diese Fehler und meldet diese.</span><span class="sxs-lookup"><span data-stu-id="a63bd-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="a63bd-131">Sollte die Ausgabe Fehlermeldungen enthalten, sehen Sie sich den Beispielcode und den Code in Ihrem Fenster an, um festzustellen, was behoben werden muss.</span><span class="sxs-lookup"><span data-stu-id="a63bd-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="a63bd-132">Durch diese Übung lernen Sie die Struktur eines C#-Codes kennen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-132">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="a63bd-133">Sie haben den ersten Schritt abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-133">You've finished the first step.</span></span> <span data-ttu-id="a63bd-134">Bevor Sie mit dem nächsten Abschnitt beginnen, verschieben wir den aktuellen Code in eine separate Methode.</span><span class="sxs-lookup"><span data-stu-id="a63bd-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="a63bd-135">Dies erleichtert das Arbeiten mit einem neuen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="a63bd-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="a63bd-136">Benennen Sie Ihre `Main` -Methode in `WorkingWithIntegers` um, und schreiben Sie eine neue `Main`-Methode, die `WorkingWithIntegers` aufruft.</span><span class="sxs-lookup"><span data-stu-id="a63bd-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="a63bd-137">Anschließend sollte der Code wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-137">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="a63bd-138">Erkunden der Reihenfolge der Operationen</span><span class="sxs-lookup"><span data-stu-id="a63bd-138">Explore order of operations</span></span>

<span data-ttu-id="a63bd-139">Kommentieren Sie den Aufruf von `WorkingWithIntegers()` aus.</span><span class="sxs-lookup"><span data-stu-id="a63bd-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="a63bd-140">Dadurch wird die Ausgabe weniger überladen, wenn Sie in diesem Abschnitt arbeiten:</span><span class="sxs-lookup"><span data-stu-id="a63bd-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="a63bd-141">Mit `//` wird ein **Kommentar** in C# begonnen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="a63bd-142">Kommentare sind Texte, die Sie in Ihrem Quellcode beibehalten, jedoch nicht als Code ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="a63bd-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="a63bd-143">Der Compiler generiert keinen ausführbaren Code über die Kommentare.</span><span class="sxs-lookup"><span data-stu-id="a63bd-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="a63bd-144">Die Programmiersprache C# definiert anhand von Regeln, die Sie aus der Mathematik kennen, die Rangfolge verschiedener arithmetischer Operationen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="a63bd-145">Multiplikation und Division haben gegenüber der Addition und Subtraktion Vorrang.</span><span class="sxs-lookup"><span data-stu-id="a63bd-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="a63bd-146">Überprüfen Sie das, indem Sie den folgenden Code Ihrer `Main`-Methode hinzufügen und `dotnet run` ausführen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="a63bd-147">Die Ausgabe zeigt, dass vor der Addition die Multiplikation ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="a63bd-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="a63bd-148">Sie können eine andere Operationsreihenfolge erzwingen, indem Sie die Operation bzw. die Operationen, die zuerst ausgeführt werden soll bzw. sollen, mit Klammern umschließen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="a63bd-149">Fügen Sie die folgenden Zeilen hinzu, und führen Sie sie aus:</span><span class="sxs-lookup"><span data-stu-id="a63bd-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="a63bd-150">Machen Sie sich damit vertraut, indem Sie viele verschiedene Operationen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="a63bd-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="a63bd-151">Fügen Sie eine Zeile hinzu, die ungefähr den folgenden Zeilen am Ende Ihrer `Main`-Methode entspricht.</span><span class="sxs-lookup"><span data-stu-id="a63bd-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="a63bd-152">Testen Sie erneut `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="a63bd-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="a63bd-153">Vielleicht haben Sie bereits ein interessantes Verhalten bei den ganzen Zahlen bemerkt.</span><span class="sxs-lookup"><span data-stu-id="a63bd-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="a63bd-154">Bei der Division ganzer Zahlen kommt immer ein ganzzahliges Ergebnis heraus, selbst wenn Sie als Ergebnis einen Dezimal- oder Bruchteil erwarten würden.</span><span class="sxs-lookup"><span data-stu-id="a63bd-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="a63bd-155">Wenn Sie dieses Verhalten noch nicht beobachtet haben, testen Sie den folgenden Code am Ende Ihrer `Main`-Methode:</span><span class="sxs-lookup"><span data-stu-id="a63bd-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="a63bd-156">Geben Sie erneut `dotnet run` ein, um die Ergebnisse anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="a63bd-157">Bevor Sie fortfahren, kopieren Sie den gesamten Code, den Sie in diesem Abschnitt geschrieben haben, und fügen ihn in eine neue Methode ein.</span><span class="sxs-lookup"><span data-stu-id="a63bd-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="a63bd-158">Rufen Sie die neue Methode `OrderPrecedence` auf.</span><span class="sxs-lookup"><span data-stu-id="a63bd-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="a63bd-159">Das Ergebnis sollte ungefähr wie im folgenden Code aussehen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-159">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="a63bd-160">Erkunden der Genauigkeit und Grenzwerte ganzer Zahlen</span><span class="sxs-lookup"><span data-stu-id="a63bd-160">Explore integer precision and limits</span></span>
<span data-ttu-id="a63bd-161">Im vorherigen Beispiel haben Sie gesehen, dass das Ergebnis bei der Division ganzer Zahlen abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="a63bd-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="a63bd-162">Sie erhalten den Restwert **remainder** mithilfe des **Modulo**-Operators, dem `%`-Zeichen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="a63bd-163">Testen Sie den folgenden Code in Ihrer `Main`-Methode:</span><span class="sxs-lookup"><span data-stu-id="a63bd-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="a63bd-164">Der integer-C#-Typ unterscheidet sich noch in einem weiteren Punkt von einer mathematischen ganzen Zahl: Der `int`-Typ ist mit minimalen und maximalen Grenzwerten versehen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="a63bd-165">Fügen Sie diesen Code zu Ihrer `Main`-Methode hinzu, um die jeweiligen Grenzwerte zu sehen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-165">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="a63bd-166">Wenn bei einer Berechnung ein Wert herauskommt, der diese Grenzwerte überschreitet, liegt eine **Unterlauf-** oder **Überlaufbedingung** vor.</span><span class="sxs-lookup"><span data-stu-id="a63bd-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="a63bd-167">Die Antwort gibt dann den Bereich der Grenzwerte an.</span><span class="sxs-lookup"><span data-stu-id="a63bd-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="a63bd-168">Fügen Sie die folgenden zwei Zeilen zu Ihrer `Main`-Methode hinzu, um ein Beispiel zu sehen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="a63bd-169">Beachten Sie, dass die Antwort sehr nah an der minimalen (negativen) ganzen Zahl liegt.</span><span class="sxs-lookup"><span data-stu-id="a63bd-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="a63bd-170">Sie entspricht `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="a63bd-170">It's the same as `min + 2`.</span></span> <span data-ttu-id="a63bd-171">Die Additionsoperation hat die zulässigen Werte für ganze Zahlen **überlaufen**.</span><span class="sxs-lookup"><span data-stu-id="a63bd-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="a63bd-172">Die Antwort enthält eine sehr große negative Zahl, da ein Überlauf den größtmöglichen ganzzahligen Wert bis zum kleinstmöglichen Wert umschließt.</span><span class="sxs-lookup"><span data-stu-id="a63bd-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="a63bd-173">Wenn der `int`-Typ nicht Ihren Anforderungen entspricht, so gibt es verschiedene numerische Typen mit anderen Grenzwerten und Genauigkeitsgraden, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a63bd-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="a63bd-174">Werfen wir im Folgenden einmal einen Blick auf diese.</span><span class="sxs-lookup"><span data-stu-id="a63bd-174">Let's explore those next.</span></span>

<span data-ttu-id="a63bd-175">Fügen Sie den Code, den Sie in diesem Abschnitt geschrieben haben, wieder in eine separate Methode ein.</span><span class="sxs-lookup"><span data-stu-id="a63bd-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="a63bd-176">Nennen Sie es `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="a63bd-176">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="a63bd-177">Arbeiten mit dem Double-Typ</span><span class="sxs-lookup"><span data-stu-id="a63bd-177">Work with the double type</span></span>

<span data-ttu-id="a63bd-178">Der numerische Typ `double` stellt eine Gleitkommazahl mit doppelter Genauigkeit dar.</span><span class="sxs-lookup"><span data-stu-id="a63bd-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="a63bd-179">Falls Ihnen diese Benennungen nichts sagen, beachten Sie die folgenden Erläuterungen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-179">Those terms may be new to you.</span></span> <span data-ttu-id="a63bd-180">Eine **Gleitkommazahl** wird verwendet, um sehr große oder sehr kleine Zahlen, die keine ganzen Zahlen sind, darzustellen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="a63bd-181">**Doppelte Genauigkeit** bedeutet, dass diese Zahlen mit einer höheren Genauigkeit gespeichert werden als mit **einfacher Genauigkeit**.</span><span class="sxs-lookup"><span data-stu-id="a63bd-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="a63bd-182">Bei modernen Computern werden häufiger Zahlen mit doppelter Genauigkeit verwendet statt mit einfacher Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="a63bd-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="a63bd-183">Sehen wir uns dies einmal genauer an.</span><span class="sxs-lookup"><span data-stu-id="a63bd-183">Let's explore.</span></span> <span data-ttu-id="a63bd-184">Fügen Sie den folgenden Code hinzu, und zeigen Sie das Ergebnis an:</span><span class="sxs-lookup"><span data-stu-id="a63bd-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="a63bd-185">Beachten Sie, dass die Antwort die Dezimalzahl des Quotienten enthält.</span><span class="sxs-lookup"><span data-stu-id="a63bd-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="a63bd-186">Testen Sie einen etwas komplizierteren Ausdruck mit Werten vom Typ „double“:</span><span class="sxs-lookup"><span data-stu-id="a63bd-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="a63bd-187">Der Bereich eines Werts vom Typ „double“ ist weitaus größer als bei ganzzahligen Werten.</span><span class="sxs-lookup"><span data-stu-id="a63bd-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="a63bd-188">Fügen Sie den folgenden Code unter dem Code hinzu, den Sie bereits geschrieben haben:</span><span class="sxs-lookup"><span data-stu-id="a63bd-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="a63bd-189">Diese Werte werden in der wissenschaftlichen Schreibweise ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="a63bd-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="a63bd-190">Die Zahl links von `E` ist die Mantisse.</span><span class="sxs-lookup"><span data-stu-id="a63bd-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="a63bd-191">Die Zahl rechts ist der Exponent als Potenz von 10.</span><span class="sxs-lookup"><span data-stu-id="a63bd-191">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="a63bd-192">Wie bei Dezimalzahlen in der Mathematik können double-Werte in C# Rundungsfehler aufweisen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="a63bd-193">Testen Sie den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="a63bd-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="a63bd-194">Denken Sie daran, dass `0.3` nicht exakt `1/3` entspricht.</span><span class="sxs-lookup"><span data-stu-id="a63bd-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="a63bd-195">***Übung***</span><span class="sxs-lookup"><span data-stu-id="a63bd-195">***Challenge***</span></span>

<span data-ttu-id="a63bd-196">Testen Sie für den `double`-Typ andere Berechnungen mit großen und kleinen Zahlen sowie mit Multiplikation und Division.</span><span class="sxs-lookup"><span data-stu-id="a63bd-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="a63bd-197">Testen Sie kompliziertere Berechnungen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-197">Try more complicated calculations.</span></span>

<span data-ttu-id="a63bd-198">Nachdem Sie sich nun einige Zeit lang mit der Übung auseinander gesetzt haben, kopieren Sie den von Ihnen geschriebenen Code, und fügen Sie ihn in eine neue Methode ein.</span><span class="sxs-lookup"><span data-stu-id="a63bd-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="a63bd-199">Vergeben Sie einen Namen für die neue Methode `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="a63bd-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="a63bd-200">Arbeiten mit Festkommatypen</span><span class="sxs-lookup"><span data-stu-id="a63bd-200">Work with fixed point types</span></span>

<span data-ttu-id="a63bd-201">Sie haben die grundlegenden numerischen Typen in C# – „integer“ und „double“ – kennengelernt.</span><span class="sxs-lookup"><span data-stu-id="a63bd-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="a63bd-202">Es gibt einen weiteren Typ, den Sie kennen sollten: den `decimal`-Typ.</span><span class="sxs-lookup"><span data-stu-id="a63bd-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="a63bd-203">Der `decimal`-Typ weist einen kleineren Bereich als `double` auf, aber eine höhere Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="a63bd-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="a63bd-204">Die Benennung **Festkomma** bedeutet, dass die Position des Dezimalkommas (hier Dezimalpunkts bzw. Binärpunkts) unveränderlich ist.</span><span class="sxs-lookup"><span data-stu-id="a63bd-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="a63bd-205">Sehen wir uns das einmal genauer an:</span><span class="sxs-lookup"><span data-stu-id="a63bd-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="a63bd-206">Beachten Sie, dass der Bereich kleiner ist als beim `double`-Typ.</span><span class="sxs-lookup"><span data-stu-id="a63bd-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="a63bd-207">Sie können sehen, dass die Genauigkeit beim Typ „decimal“ höher ist, wenn Sie den folgenden Code testen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="a63bd-208">Mit dem Suffix `M` neben einer Zahl geben Sie an, dass eine Konstante den `decimal`-Typ verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="a63bd-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="a63bd-209">Beachten Sie, dass der aus dieser arithmetischen Operation resultierende Wert vom Typ „decimal“ rechts neben dem Dezimalpunkt mehr Ziffern enthält.</span><span class="sxs-lookup"><span data-stu-id="a63bd-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="a63bd-210">***Übung***</span><span class="sxs-lookup"><span data-stu-id="a63bd-210">***Challenge***</span></span>

<span data-ttu-id="a63bd-211">Nachdem Sie nun die verschiedenen numerischen Typen kennengelernt haben, schreiben Sie Code, der den Flächeninhalt eines Kreises mit einem Radius von 2,5 cm berechnet.</span><span class="sxs-lookup"><span data-stu-id="a63bd-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="a63bd-212">Denken Sie daran, dass der Flächeninhalt eines Kreises durch das Quadrat des Radius multipliziert mit Pi gebildet wird.</span><span class="sxs-lookup"><span data-stu-id="a63bd-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="a63bd-213">Hinweis: .NET bietet eine Konstante für Pi (<xref:System.Math.PI?displayProperty=nameWithType>), die Sie für die Berechnung dieses Werts verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a63bd-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="a63bd-214">Sie sollten eine Antwort zwischen 19 und 20 erhalten.</span><span class="sxs-lookup"><span data-stu-id="a63bd-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="a63bd-215">Sie können Ihre Antwort anhand des [fertig gestellten Beispielcodes auf GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) prüfen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="a63bd-216">Wenn Sie möchten, testen Sie andere Formeln.</span><span class="sxs-lookup"><span data-stu-id="a63bd-216">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="a63bd-217">Sie haben den Schnellstart „Zahlen in C#“ abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a63bd-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="a63bd-218">Sie können mit dem Schnellstart [Branches und Schleifen](branches-and-loops-local.md) in Ihrer eigenen Entwicklungsumgebung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="a63bd-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="a63bd-219">Weitere Informationen zu Zahlen in C# finden Sie auch unter folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="a63bd-219">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="a63bd-220">[Tabelle ganzzahliger Typen](../../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="a63bd-220">[Integral Types Table](../../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="a63bd-221">[Tabelle für Gleitkommatypen](../../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="a63bd-221">[Floating-Point Types Table](../../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="a63bd-222">[Tabelle integrierter Typen](../../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="a63bd-222">[Built-In Types Table](../../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="a63bd-223">[Tabelle für implizite numerische Konvertierungen](../../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="a63bd-223">[Implicit Numeric Conversions Table](../../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="a63bd-224">Tabelle für explizite numerische Konvertierungen</span><span class="sxs-lookup"><span data-stu-id="a63bd-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)