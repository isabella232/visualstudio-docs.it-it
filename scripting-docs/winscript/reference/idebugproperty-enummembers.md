---
title: IDebugProperty::EnumMembers | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7edf2d2f94519146a81cf94b3bf30946af59bbe9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097032"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera i membri di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 [in] Specifica il `DBGPROP_INFO_FLAGS` costanti che determinano quali campi nelle strutture di proprietà di debug enumerati sono da compilare.  
  
 `nRadix`  
 [in] Radice da utilizzare nell'interpretare le informazioni numeriche.  
  
 `refiid`  
 [in] Questo IID viene passato per il filtro dell'enumeratore. IID è uno dei `IDebugPropertyEnumType` interfacce da cui ereditare `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Restituisce il `IEnumDebugPropertyInfo` interfaccia che enumera le proprietà dei membri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Interfaccia IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)