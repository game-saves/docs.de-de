---
title: Verwenden von Strukturen – C#-Programmierhandbuch
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: fe7cf3cf1982060d22f648c5e17d002b1a695ac0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978526"
---
# <a name="using-structs-c-programming-guide"></a>Verwenden von Strukturen (C#-Programmierhandbuch)
Der `struct` -Typ eignet sich für die Darstellung von kompakten Objekten, z. B. `Point`, `Rectangle`und `Color`. Obwohl es ebenso einfach ist, einen Punkt als [Klasse](../../../csharp/language-reference/keywords/class.md) mit [automatisch implementierten Eigenschaften](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)darzustellen, kann eine [Struktur](../../../csharp/language-reference/keywords/struct.md) in verschiedenen Szenarien effizienter sein. Bei der Deklaration eines Arrays mit 1.000 `Point` -Objekten belegen Sie z. B. zusätzlichen Arbeitsspeicher, damit auf jedes Objekt verwiesen werden kann. In diesem Fall wäre eine Struktur weniger speicherintensiv. Da [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ein Objekt mit dem Namen <xref:System.Drawing.Point>enthält, wird die Struktur in diesem Beispiel stattdessen „Coords“ genannt.  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Die Definition eines (parameterlosen) Standardkonstruktors für eine Struktur verursacht einen Fehler. Auch durch die Initialisierung eines Instanzenfelds in einem Strukturtext wird ein Fehler generiert. Die extern verfügbaren Strukturmember können nur mithilfe eines parametrisierten Konstruktors, dem expliziten Standardkonstruktor, einem [Objektinitialisierer](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) oder durch jeweils einzelnen Zugriff auf die Member im Anschluss an die Deklaration der Struktur initialisiert werden. Alle privaten oder auf andere Weise gesperrten Member erfordern die ausschließliche Verwendung von Konstruktoren.
  
 Wenn Sie ein Strukturobjekt mit dem Operator [new](../../../csharp/language-reference/keywords/new.md) erzeugen, wird das Objekt erstellt und der geeignete Konstruktor gemäß der [Signatur des Konstruktors](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax) aufgerufen. Strukturen können im Gegensatz zu Klassen ohne den Operator `new` instanziiert werden. In einem solchen Fall gibt es keinen Konstruktoraufruf, sodass die Zuordnung effizienter ausgeführt werden kann. Die Felder werden jedoch nicht zugewiesen, und das Objekt kann erst verwendet werden, nachdem alle Felder initialisiert wurden. Dazu gehört die Unfähigkeit, Werte mithilfe von automatisch implementierten Eigenschaften abzurufen oder festzulegen.
 
 Wenn Sie ein Strukturobjekt unter Verwendung des parameterlosen Standardkonstruktors instanziieren, werden alle Werte gemäß ihrer [Standardwerte](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) zugeordnet.
  
 Wenn Sie einen Konstruktor mit Parametern für eine Struktur schreiben, müssen Sie alle Member explizit initialisieren. Andernfalls bleibt mindestens ein Member nicht zugewiesen, die Struktur kann nicht verwendet werden, und der Compilerfehler CS0171 wird ausgelöst.  
  
 Bei Strukturen findet keine Vererbung wie bei Klassen statt. Eine Struktur kann nicht von einer anderen Struktur oder Klasse erben, und sie kann auch nicht die Basis einer Klasse sein. Stattdessen erben Strukturen von der <xref:System.Object>-Basisklasse. Eine Struktur kann Schnittstellen implementieren. Dies geschieht auf dieselbe Weise wie bei Klassen.  
  
 Sie können keine Klasse mit dem `struct`-Schlüsselwort deklarieren. Klassen und Strukturen weisen in C# semantische Unterschiede auf. Eine Struktur ist ein Werttyp, während eine Klasse ein Referenztyp ist. Weitere Informationen finden Sie unter [Werttypen](../../../csharp/language-reference/keywords/value-types.md).  
  
 Sofern keine Semantik für Verweistypen benötigt wird, kann das System kleine Klassen effizienter verarbeiten, wenn diese als Struktur definiert werden.  
  
## <a name="example-1"></a>Beispiel 1  
  
### <a name="description"></a>Beschreibung  
 In diesem Beispiel wird die `struct` -Initialisierung sowohl unter Verwendung von Standardkonstruktoren als auch unter Verwendung von parametrisierten Konstruktoren veranschaulicht.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Beispiel 2  
  
### <a name="description"></a>Beschreibung  
 Dieses Beispiel veranschaulicht ein Feature, das ausschließlich auf Strukturen anwendbar ist. Es wird ein Coords-Objekt ohne Verwendung des Operators `new` erstellt. Wenn Sie den Begriff `struct` durch `class`ersetzen, wird das Programm nicht kompiliert.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)
- [Klassen und Strukturen](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Strukturen](../../../csharp/programming-guide/classes-and-structs/structs.md)
