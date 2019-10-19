---
title: 'IDebugProperty:: GetExtendedInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562398"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Ottiene le informazioni estese per la proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cInfos`  
 in Conteggio degli oggetti informazioni estese.  
  
 `rgguidExtendedInfo`  
 in Viene passata una matrice di `GUID`s in modo che sia possibile recuperare contemporaneamente più elementi di informazioni estese.  
  
 `pExtendedInfo`  
 out Restituisce una matrice di `VARIANT`s che può essere utilizzata per recuperare le informazioni sulle proprietà estese.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un `HRESULT` valido, in genere `S_OK`.  
  
## <a name="remarks"></a>Note  
 Questa interfaccia ottiene informazioni estese per questo oggetto. L'API esiste solo allo scopo di recuperare le informazioni che non si prestano a essere recuperate dall'uso di `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)