---
title: Übergeben von Werttypparametern – C#-Programmierhandbuch
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: c02526c41e7aabb1d443765d047cdae052b48985
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964243"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Übergeben von Werttypparametern (C#-Programmierhandbuch)
In einer [Werttypvariablen](../../../csharp/language-reference/keywords/value-types.md) sind die Daten direkt enthalten, während eine [Verweistypvariable](../../../csharp/language-reference/keywords/reference-types.md) einen Verweis auf die Daten enthält. Wenn eine Werttypvariable als Wert an eine Methode übergeben wird, bedeutet dies die Übergabe einer Kopie der Variablen an die Methode. Alle Änderungen am Parameter, die innerhalb der Methode erfolgen, haben keine Auswirkung auf die ursprünglichen Daten, die in der Argumentvariable gespeichert sind. Wenn Sie möchten, dass mit der aufgerufenen Methode der Wert des Parameters geändert wird, müssen Sie ihn als Verweis übergeben, unter Verwendung des Schlüsselworts [ref](../../../csharp/language-reference/keywords/ref.md) oder [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md). Sie können auch das Schlüsselwort [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) verwenden, um einen Wertparameter pro Verweis zu übergeben, um einerseits zwar eine Kopie zu vermeiden, andererseits aber zu garantieren, dass der Wert nicht verändert wird. Der Einfachheit halber wird im folgenden Beispiel `ref` verwendet.  
  
## <a name="passing-value-types-by-value"></a>Übergeben von Werttypen als Wert  
 Im folgenden Beispiel wird gezeigt, wie Werttypparameter als Wert übergeben werden. Die Variable `n` wird als Wert an die `SquareIt`-Methode übergeben. Alle Änderungen, die innerhalb der Methode vorgenommen werden, wirken sich nicht auf den ursprünglichen Wert der Variablen aus.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Die Variable `n` ist eine Werttypvariable. Sie enthält Daten, den Wert `5`. Beim Aufruf von `SquareIt` werden die Inhalte von `n` in den Parameter `x` kopiert, der in der Methode quadriert wird. In `Main` ist der Wert von `n` jedoch auch nach dem Aufruf der `SquareIt`-Methode derselbe wie zuvor. Die Änderung, die innerhalb der Methode stattfindet, wirkt sich nur auf die lokale Variable `x` aus.  
  
## <a name="passing-value-types-by-reference"></a>Übergeben von Werttypen als Verweis  
 Das folgende Beispiel entspricht dem vorhergehenden Beispiel, mit dem Unterschied, dass das Argument als `ref`-Parameter übergeben wird. Der Wert des zugrunde liegenden Arguments, `n`, wird geändert, wenn `x` in der Methode geändert wird.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 In diesem Beispiel wird nicht der Wert von `n`, sondern ein Verweis auf `n` übergeben. Der Parameter `x` ist kein [int](../../../csharp/language-reference/keywords/int.md), sondern ein Verweis auf `int` – in diesem Fall ein Verweis auf `n`. Beim Quadrieren von `x` innerhalb der Methode wird deshalb tatsächlich das Element quadriert, auf das `x` verweist: `n`.  
  
## <a name="swapping-value-types"></a>Austauschen von Werttypen  
 Ein allgemeines Beispiel zum Ändern der Werte von Argumenten ist eine swap-Methode, bei der Sie zwei Variablen an die Methode übergeben und die Methode deren Inhalte austauscht. Sie müssen die Argumente als Verweis an die swap-Methode übergeben. Andernfalls tauschen Sie lokale Kopien der Parameter innerhalb der Methode aus, und es erfolgt keine Änderung in der aufrufenden Methode. Im folgenden Beispiel werden ganzzahlige Werte getauscht.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Wenn Sie die `SwapByRef`-Methode aufrufen, verwenden Sie das Schlüsselwort `ref` im Aufruf, wie im folgenden Beispiel gezeigt.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)
- [Übergeben von Parametern](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
- [Übergeben von Verweistypparametern](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
