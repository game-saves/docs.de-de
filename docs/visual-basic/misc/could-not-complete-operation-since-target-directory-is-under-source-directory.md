---
title: Der Vorgang konnte nicht abgeschlossen werden, da sich das Zielverzeichnis unterhalb des Quellverzeichnisses befindet.
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 39373cd368282f3b109b450189561366b9e74484
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200571"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Der Vorgang konnte nicht abgeschlossen werden, da sich das Zielverzeichnis unterhalb des Quellverzeichnisses befindet.
Ein zyklischer Vorgang ist fehlgeschlagen. Ein zyklischer Vorgang wird zyklisch ausgeführt und kann daher nicht abgeschlossen werden. Beispielsweise könnte Objekt A versuchen, von Objekt B zu erben, das wiederum versucht, von Objekt A zu erben.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Wenn geerbt wird, müssen Sie sicherstellen, dass keine zyklischen Verweise vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch
- [Fehlertypen](../../visual-basic/programming-guide/language-features/error-types.md)
- [Verwenden von Haltepunkten in Visual Studio-debugger](/visualstudio/debugger/using-breakpoints)
