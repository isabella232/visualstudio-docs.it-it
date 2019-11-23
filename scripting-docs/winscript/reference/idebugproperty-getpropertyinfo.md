---
title: 'IDebugProperty:: GetPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562332"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Ottiene il valore di un `IDebugProperty` che descrive un metodo o una proprietà indicizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 in Specifica le costanti `DBGPROP_INFO_FLAGS` che determinano i campi da compilare nella struttura di `DebugPropertyInfo`.  
  
 `nRadix`  
 in Radice da usare per la formattazione di qualsiasi informazione numerica.  
  
 `pPropertyInfo`  
 out Restituisce la struttura di `DebugPropertyInfo` che descrive la proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un `HRESULT`valido, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)