---
title: Skip-Klausel (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 8441e619cdbd18545be72fd701c2cc9b1cf495d9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971236"
---
# <a name="skip-clause-visual-basic"></a>Skip-Klausel (Visual Basic)
Überspringt eine festgelegte Anzahl von Elementen in einer Auflistung und gibt anschließend die übrigen Elemente zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Teile  
 `count`  
 Erforderlich. Ein Wert oder ein Ausdruck, der die Anzahl der Elemente der Sequenz zu überspringenden ergibt.  
  
## <a name="remarks"></a>Hinweise  
 Die `Skip` -Klausel bewirkt, dass eine Abfrage Elemente am Anfang einer Ergebnisliste zu umgehen und die übrigen Elemente zurückgegeben. Die Anzahl der zu überspringenden Elemente wird durch identifiziert die `count` Parameter.  
  
 Können Sie die `Skip` -Klausel mit der `Take` -Klausel, um einen Bereich von Daten aus jedem Segment einer Abfrage zurückgeben. Dazu übergeben Sie den Index des ersten Elements des Bereichs, der die `Skip` -Klausel und die Größe des Bereichs, der die `Take` Klausel.  
  
 Bei Verwendung der `Skip` -Klausel in einer Abfrage, Sie müssen auch sicherstellen, dass die Ergebnisse in der Reihenfolge zurückgegeben werden, mit denen die `Skip` -Klausel, um die gewünschten Ergebnisse zu umgehen. Weitere Informationen zum Sortieren von Abfrageergebnissen finden Sie unter [Order By-Klausel](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Sie können die `SkipWhile` Klausel, um anzugeben, dass nur bestimmte Elemente, je nach einer angegebenen Bedingung ignoriert werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die `Skip` -Klausel zusammen mit den `Take` -Klausel zur Rückgabe von Daten aus einer Abfrage in Seiten. Die `GetCustomers` Funktion verwendet die `Skip` -Klausel, um die Kunden in der Liste zu umgehen, bis die angegebenen Wert und verwendet die `Take` -Klausel, um eine Seite mit Kunden, die von diesem Indexwert zurück.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Siehe auch
- [Einführung in LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Abfragen](../../../visual-basic/language-reference/queries/index.md)
- [Select-Klausel](../../../visual-basic/language-reference/queries/select-clause.md)
- [From-Klausel](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By-Klausel](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While-Klausel](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take-Klausel](../../../visual-basic/language-reference/queries/take-clause.md)
