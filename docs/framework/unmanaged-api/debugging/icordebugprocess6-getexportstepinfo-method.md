---
title: ICorDebugProcess6::GetExportStepInfo-Methode
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b60bad75cb6286bda026e5b67e0a4fa8e2347dd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487160"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo-Methode
Enthält Informationen über die exportierten Laufzeitfunktionen, welche dabei helfen, den verwaltetem Code schrittweise durchzugehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parameter  
 pszExportName  
 [in] Der Name einer Laufzeit-Exportfunktion wie in der PE-Exporttabelle angegeben.  
  
 invokeKind  
 [out] Ein Zeiger auf ein Mitglied der [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) Enumeration, die beschreibt, wie die exportierte Funktion verwalteter Code aufgerufen wird.  
  
 invokePurpose  
 [out] Ein Zeiger auf ein Mitglied der [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) Enumeration, die beschreibt, warum die exportierte Funktion verwalteter Code aufgerufen wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Diese Methode kann die in der folgenden Tabelle aufgeführten Werte zurückgeben.  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|`S_OK`|Der Methodenaufruf war erfolgreich.|  
|`E_POINTER`|`pInvokeKind` oder `pInvokePurpose` ist **null**.|  
|Andere fehlerhafte `HRESULT`-Werte.|Gegebenenfalls.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]
>  Diese Methode ist nur mit .NET Native verfügbar.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [ICorDebugProcess6-Schnittstelle](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debuggen von Schnittstellen](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
