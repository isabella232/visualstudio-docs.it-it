---
title: Struttura ExtendedDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575840"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Struttura ExtendedDebugPropertyInfo
Estende la struttura di `DebugPropertyInfo` con membri aggiuntivi per caratterizzare la proprietà estesa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Members  
 `dwValidFields`  
 Tipo di dati enumerato utilizzato per specificare i campi che vengono inizializzati.  
  
 `bstrName`  
 Nome della proprietà all'interno di un contesto.  
  
 `bstrType`  
 Tipo di proprietà come stringa formattata.  
  
 `bstrValue`  
 Valore della proprietà sotto forma di stringa formattata.  
  
 `bstrFullName`  
 Nome completo della proprietà.  
  
 `dwAttrib`  
 Enumerazione che specifica i flag per gli attributi della proprietà di debug.  
  
 `pDebugProp`  
 `IDebugProperty` oggetto corrispondente a questo `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 ID dispatch.  
  
 `nType`  
 Tipo di proprietà estesa.  
  
 `varValue`  
 Valore della proprietà estesa se può adattarsi alla variante.  
  
 `plbValue`  
 Byte di dati effettivi del valore della proprietà.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` oggetto corrispondente a questo `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 della [struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)    
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)    
 @No__t_1 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)