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
ms.openlocfilehash: 99208626b41f2463178bccecf73c21a1d15fa765
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955263"
---
# <a name="debugpropertyinfo-structure"></a>Struttura DebugPropertyInfo
Descrive un oggetto di natura gerarchica con nome, tipo e valore. Viene usato per descrivere le proprietà di debug di variabili locali, parametri, controllare variabili ed espressioni e registra.  
  
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
  
## <a name="members"></a>Membri  
 dwValidFields  
 Tipo di dati enumerato consente di specificare quali campi vengono inizializzati.  
  
 bstrName  
 Il nome della proprietà all'interno di un contesto.  
  
 bstrType  
 Tipo di proprietà, come stringa formattata.  
  
 bstrValue  
 Il valore della proprietà come stringa formattata.  
  
 bstrFullName  
 Nome completo della proprietà.  
  
 dwAttrib  
 Enumerazione che specifica i flag per gli attributi della proprietà di debug.  
  
 pDebugProp  
 Il `IDebugProperty` descritto dalle informazioni in questo `DebugPropertyInfo` struttura.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)