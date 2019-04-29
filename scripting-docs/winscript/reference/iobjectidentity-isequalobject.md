---
title: IObjectIdentity::IsEqualObject | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944882"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Determina se un oggetto è uguale all'oggetto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `punk`  
 [in] Indirizzo dell'oggetto da confrontare con l'oggetto corrente.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Gli oggetti sono uguali.|  
|`S_FALSE`|Gli oggetti non sono uguali.|  
  
## <a name="remarks"></a>Note  
 Un'implementazione del `IsEqualObject` metodo dovrebbe restituire `S_OK` solo se gli oggetti sono identici.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)