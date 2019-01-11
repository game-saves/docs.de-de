---
title: SqlStreamChars.IsNull-Eigenschaft (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 79ebb9ec54185a94cb95dfd0fb2929e61cf513ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152623"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="ea196-102">SqlStreamChars.IsNull-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ea196-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="ea196-103">Ruft beim Überschreiben in einer abgeleiteten Klasse ruft einen Wert, der angibt, ob der Datenstrom ist `null`.</span><span class="sxs-lookup"><span data-stu-id="ea196-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="ea196-104">Die Assembly, die diese Eigenschaft enthält, verfügt über eine Friend-Beziehung SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="ea196-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ea196-105">Es ist für die Verwendung durch SQL Server vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="ea196-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ea196-106">Verwenden Sie für andere Datenbanken Hostingmechanismus, die von dieser Datenbank bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ea196-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea196-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea196-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="ea196-108">Eigenschaftswert</span><span class="sxs-lookup"><span data-stu-id="ea196-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="ea196-109">`true` Wenn der Stream `null`ist, andernfalls `false`.</span><span class="sxs-lookup"><span data-stu-id="ea196-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea196-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ea196-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ea196-111">Die `SqlStreamChars.IsNull` -Eigenschaft ist privat und nicht direkt in Ihrem Code verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ea196-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ea196-112">Microsoft unterstützt nicht die Verwendung dieses Felds in einer produktionsanwendung unter keinen Umständen.</span><span class="sxs-lookup"><span data-stu-id="ea196-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea196-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ea196-113">Requirements</span></span>

<span data-ttu-id="ea196-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ea196-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ea196-115">**Assembly:** System.Data (in "System.Data.dll")</span><span class="sxs-lookup"><span data-stu-id="ea196-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ea196-116">**.NET Framework-Versionen:** Verfügbar seit 2.0.</span><span class="sxs-lookup"><span data-stu-id="ea196-116">**.NET Framework versions:** Available since 2.0.</span></span>