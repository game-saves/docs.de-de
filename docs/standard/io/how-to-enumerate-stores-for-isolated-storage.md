---
title: 'Vorgehensweise: Auflisten von Speichern für isolierten Speicher'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f14259afe4ee296d930b042d9e9ef069a81e65f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591759"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Vorgehensweise: Auflisten von Speichern für isolierten Speicher
Sie können alle isolierten Speicher für den aktuellen Benutzer mit der statischen <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>-Methode auflisten. Diese Methode nimmt einen <xref:System.IO.IsolatedStorage.IsolatedStorageScope>-Wert entgegen und gibt einen <xref:System.IO.IsolatedStorage.IsolatedStorageFile>-Enumerator zurück. Zum Auflisten von Speichern benötigen Sie die <xref:System.Security.Permissions.IsolatedStorageFilePermission>-Berechtigung, die den <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>-Wert angibt. Beim Aufrufen der <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>-Methode mit dem <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>-Wert wird ein Array von <xref:System.IO.IsolatedStorage.IsolatedStorageFile>-Objekten zurückgegeben, die für den aktuellen Benutzer definiert sind.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden ein Speicher abgerufen, der nach Benutzer und Assembly isoliert ist, einige Dateien erstellt und diese Dateien mit der <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>-Methode abgerufen.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Isolierter Speicher](../../../docs/standard/io/isolated-storage.md)
