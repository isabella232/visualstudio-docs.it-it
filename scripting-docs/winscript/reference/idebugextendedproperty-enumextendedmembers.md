---
title: IDebugExtendedProperty::EnumExtendedMembers | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e14d1bc8937221960d938f1bbfae8e307830f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946145"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Enumera i membri di una proprietà estesa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Specifica le costanti EX_DBGPROP_INFO_FLAGS che determinano che i campi in enumerati estesi strutture delle proprietà di debug che sono da compilare.  
  
 `nRadix`  
 [in] Radice da utilizzare nell'interpretare le informazioni numeriche.  
  
 `ppeepi`  
 [out] Restituisce il `IEnumDebugExtendedPropertyInfo` interfaccia che enumera le proprietà dei membri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [Struttura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)