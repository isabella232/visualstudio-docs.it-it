---
title: Struttura DebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575073"
---
# <a name="debugpropertyinfo-structure"></a>Struttura DebugPropertyInfo
Descrive un oggetto di una natura gerarchica con nome, tipo e valore. Viene usato per descrivere le proprietà di debug di variabili locali, parametri, espressioni di controllo e espressioni e registri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Members  
 dwValidFields  
 Tipo di dati enumerato utilizzato per specificare i campi che vengono inizializzati.  
  
 bstrName  
 Nome della proprietà all'interno di un contesto.  
  
 bstrType  
 Tipo di proprietà, come stringa formattata.  
  
 bstrValue  
 Valore della proprietà, come stringa formattata.  
  
 bstrFullName  
 Nome completo della proprietà.  
  
 dwAttrib  
 Enumerazione che specifica i flag per gli attributi della proprietà di debug.  
  
 pDebugProp  
 `IDebugProperty` descritta dalle informazioni contenute in questa struttura di `DebugPropertyInfo`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)