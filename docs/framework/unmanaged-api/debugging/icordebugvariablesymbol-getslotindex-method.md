---
title: ICorDebugVariableSymbol::GetSize-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d632bc792152afcfc94b51235dc0699fb3efc245
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="2ba74-102">ICorDebugVariableSymbol::GetSize-Methode</span><span class="sxs-lookup"><span data-stu-id="2ba74-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="2ba74-103">Ruft den verwalteten Slotindex einer lokalen Variablen ab.</span><span class="sxs-lookup"><span data-stu-id="2ba74-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba74-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ba74-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ba74-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="2ba74-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="2ba74-106">[out] Ein Zeiger auf den Slotindex der lokalen Variablen.</span><span class="sxs-lookup"><span data-stu-id="2ba74-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ba74-107">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="2ba74-107">Return Value</span></span>  
 <span data-ttu-id="2ba74-108">Bei Erfolg `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="2ba74-108">`S_OK` if successful.</span></span> <span data-ttu-id="2ba74-109">`E_FAIL`, wenn die Variable ein Funktionsargument ist.</span><span class="sxs-lookup"><span data-stu-id="2ba74-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ba74-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2ba74-110">Remarks</span></span>  
 <span data-ttu-id="2ba74-111">Der verwaltete Slotindex einer lokalen Variablen kann zum Abrufen der Metadateninformationen der Variablen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2ba74-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ba74-112">Diese Methode ist nur in Verbindung mit .NET Native verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2ba74-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ba74-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2ba74-113">Requirements</span></span>  
 <span data-ttu-id="2ba74-114">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ba74-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ba74-115">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ba74-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ba74-116">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ba74-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ba74-117">**.NET Framework-Versionen:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ba74-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba74-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2ba74-118">See Also</span></span>  
 [<span data-ttu-id="2ba74-119">ICorDebugVariableSymbol-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="2ba74-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="2ba74-120">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="2ba74-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)