---
title: ISimpleConnectionPoint::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571816"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Restituisce il DISPID e il nome per ogni evento in un intervallo di eventi specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `iEvent`  
 in Indice del primo evento da recuperare.  
  
 `cEvents`  
 in Numero di eventi da recuperare.  
  
 `prgid`  
 out Matrice di valori DISPID dell'evento.  
  
 `prgbstr`  
 out Matrice di nomi di evento.  
  
 `pcEventsFetched`  
 out Numero effettivo di eventi recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`S_FALSE`|Sono stati richiesti più eventi di quelli disponibili. Gli eventi non disponibili sono rappresentati con DISPID_NULL e un BSTR NULL.|  
|`E_INVALIDARG`|Non è stato possibile recuperare gli elementi.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il DISPID e il nome per ogni evento in un intervallo di eventi specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)