---
title: 'IDebugProperty:: EnumMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562415"
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
 in Specifica le costanti `DBGPROP_INFO_FLAGS` che determinano i campi nelle strutture delle proprietà di debug enumerate da compilare.  
  
 `nRadix`  
 in Radice da usare per interpretare le informazioni numeriche.  
  
 `refiid`  
 in Questo IID viene passato per filtrare l'enumeratore. L'IID è uno dei `IDebugPropertyEnumType` interfacce che ereditano da `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 out Restituisce l'interfaccia `IEnumDebugPropertyInfo` che enumera le proprietà del membro.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un `HRESULT` valido, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)    
 @No__t_1 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)  
 [Interfaccia IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)    
 [Interfaccia IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)