---
title: Zuordnungstyp
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 3b01e053a1d61e2ce413ae6683d350b77c402fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714593"
---
# <a name="association-type"></a>Zuordnungstyp
Ein *Zuordnungstyp* (auch als Zuordnung bezeichnet) ist der wesentliche Baustein zum Beschreiben von Beziehungen im Entity Data Model (EDM). In einem konzeptionellen Modell stellt eine Zuordnung eine Beziehung zwischen zwei [Entitätstypen](../../../../docs/framework/data/adonet/entity-type.md) (z. B. `Customer` und `Order`). In einer Anwendung stellt eine Instanz einer Zuordnung eine bestimmte Zuordnung dar (z. B. eine Zuordnung zwischen einer Instanz von `Customer` und einer Instanz von `Order`). Zuordnungsinstanzen werden logisch gruppiert, eine [Zuordnungssatz](../../../../docs/framework/data/adonet/association-set.md).  
  
 Eine Zuordnungsdefinition enthält die folgenden Informationen:  
  
-   Eine eindeutige Bezeichnung. (erforderlich)  
  
-   Zwei [Zuordnungsenden](../../../../docs/framework/data/adonet/association-end.md), eine für jeden Entitätstyp in der Beziehung. (erforderlich)  
  
    > [!NOTE]
    >  Eine Zuordnung kann keine Beziehung zwischen mehr als zwei Entitätstypen darstellen. Eine Zuordnung kann jedoch eine Selbstbeziehung definieren, indem der gleichen Entitätstyp für beide Zuordnungsenden angegeben wird.  
  
-   Ein [Einschränkung der referenziellen Integrität](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (Optional)  
  
 Geben Sie jedes Zuordnungsende muss eine [zuordnungsendes](../../../../docs/framework/data/adonet/association-end-multiplicity.md) , der die Anzahl der Instanzen eines Entitätstyps, die an einem Ende der Zuordnung angibt. Die Multiplizität eines Zuordnungsendes kann über einen Wert von eins (1), null oder eins (0..1) oder n (*) verfügen. Auf Entitätstypinstanzen an einem Ende einer Zuordnung können Sie über zugreifen [Navigationseigenschaften](../../../../docs/framework/data/adonet/navigation-property.md) oder Fremdschlüssel, wenn sie für einen Entitätstyp verfügbar gemacht werden. Weitere Informationen finden Sie unter [Entity Data Model: Fremdschlüssel](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Beispiel  
 Die unten stehende Abbildung zeigt ein konzeptionelles Modell mit zwei Zuordnungen: `PublishedBy` und `WrittenBy`. Die Zuordnungsenden für die `PublishedBy`-Zuordnung sind die Entitätstypen `Book` und `Publisher`. Die Multiplizität des `Publisher`-Endes ist eins (1), und die Multiplizität des `Book`-Endes ist n (*), wodurch angegeben wird, dass ein Verleger viele Bücher veröffentlicht und ein Buch von einem Verleger veröffentlicht wird.  
  
 ![Beispielmodell](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Die [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) verwendet eine domänenspezifische Sprache (DSL) Bezeichnung konzeptionelle Schemadefinitionssprache ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)), konzeptionelle Modelle zu definieren. Die folgende CSDL definiert die in der Abbildung oben gezeigte `PublishedBy`-Zuordnung:  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Siehe auch
- [Schlüsselkonzepte im Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
