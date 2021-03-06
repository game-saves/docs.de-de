---
title: Varianz in generischen Schnittstellen (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: b713cb4f2b13c54a4a60c522bbef492a5962cdc3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601791"
---
# <a name="variance-in-generic-interfaces-c"></a>Varianz in generischen Schnittstellen (C#)
In .NET Framework 4 wurde die Varianzunterstützung für mehrere vorhandene generische Schnittstellen eingeführt. Die Varianzunterstützung lässt eine implizite Konvertierung von Klassen zu, die diese Schnittstellen implementieren. Die folgenden Schnittstellen sind jetzt variant:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T ist kovariant)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T ist kovariant)  
  
-   <xref:System.Linq.IQueryable%601> (T ist kovariant)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` und `TElement` sind kovariant)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T ist kontravariant)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T ist kontravariant)  
  
-   <xref:System.IComparable%601> (T ist kontravariant)  
  
 Kovarianz ermöglicht einer Methode, stärker abgeleitete Rückgabetypen zu verwenden, als durch die generischen Typparameter der Schnittstelle definiert sind. Betrachten Sie diese generischen Schnittstellen zur Veranschaulichung der Kovarianzfunktionen: `IEnumerable<Object>` und `IEnumerable<String>`. Die Schnittstelle `IEnumerable<Object>` wird nicht von der Schnittstelle `IEnumerable<String>` geerbt. Allerdings erbt der Typ `String` den Typ `Object`. In einigen Fällen können Sie vielleicht auch die Objekte dieser Schnittstellen einander zuweisen. Dies wird im folgenden Codebeispiel gezeigt.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 In früheren Versionen des .NET Frameworks verursacht dieser Code einen Kompilierfehler mit `Option Strict On` in C#. Jetzt können Sie aber `strings` anstelle von `objects` verwenden, wie im vorherigen Beispiel gezeigt wurde, da die <xref:System.Collections.Generic.IEnumerable%601>-Schnittstelle kovariant ist.  
  
 Kontravarianz ermöglicht einer Methode, Argumenttypen zu verwenden, die weniger stark abgeleitet sind als durch die generischen Parameter der Schnittstelle angegeben. Nehmen Sie zur Veranschaulichung der Kontravarianz an, dass Sie eine `BaseComparer`-Klasse zum Vergleich von Instanzen der `BaseClass`-Klasse erstellt haben. Die `BaseComparer`-Klasse implementiert die `IEqualityComparer<BaseClass>`-Schnittstelle. Da die Schnittstelle <xref:System.Collections.Generic.IEqualityComparer%601> jetzt kontravariant ist, können Sie `BaseComparer` verwenden, um Instanzen von Klassen zu vergleichen, die die Klasse `BaseClass` erben. Dies wird im folgenden Codebeispiel gezeigt.  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 Weitere Beispiele finden Sie unter [Using Variance in Interfaces for Generic Collections (C#) (Verwenden von Varianz in Schnittstellen für generische Auflistungen (C#))](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Varianz in generischen Typparametern wird nur für Referenztypen unterstützt. Werttypen unterstützen keine Varianz. Beispielweise kann `IEnumerable<int>` nicht implizit in `IEnumerable<object>` konvertiert werden, da Ganzzahlen durch Werttypen dargestellt werden.  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 Es ist auch wichtig zu beachten, dass Klassen, die variante Schnittstellen implementieren, trotzdem noch invariant sind. Obwohl <xref:System.Collections.Generic.List%601> beispielsweise die kovariante Schnittstelle <xref:System.Collections.Generic.IEnumerable%601> implementiert, können Sie `List<Object>` implizit in `List<String>` konvertieren. Dies wird im folgenden Codebeispiel veranschaulicht.  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>Siehe auch

- [Using Variance in Interfaces for Generic Collections (C#) (Verwenden von Varianz in Schnittstellen für generische Auflistungen (C#))](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Creating Variant Generic Interfaces (C#) (Erstellen von varianten generischen Schnittstellen (C#))](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Generische Schnittstellen](../../../../standard/generics/interfaces.md)
- [Variance in Delegates (C#) (Varianz bei Delegaten (C#))](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
