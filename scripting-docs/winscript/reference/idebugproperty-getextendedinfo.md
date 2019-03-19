---
title: IDebugProperty::GetExtendedInfo | Microsoft Docs
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
ms.openlocfilehash: 707474f786a8f88c0e08d887f2c2b09c8aaedc8e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144862"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Ottiene le informazioni per la proprietà estese.  
  
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
 [in] Numero di oggetti informazioni estese.  
  
 `rgguidExtendedInfo`  
 [in] Matrice di `GUID`s viene passato in modo che più elementi di informazioni estese possono essere recuperati contemporaneamente.  
  
 `pExtendedInfo`  
 [out] Restituisce una matrice di `VARIANT`che può essere utilizzato per recuperare le informazioni sulle proprietà estese.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore valido `HRESULT`, in genere `S_OK`.  
  
## <a name="remarks"></a>Note  
 Questa interfaccia ottiene estese informazioni per questo oggetto. L'API esiste solo per il recupero di informazioni che non si prestano a recuperati mediante l'utilizzo di `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)