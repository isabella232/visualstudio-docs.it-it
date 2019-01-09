---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088504"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Restituisce il DISPID e il nome per ogni evento in un intervallo specificato di eventi.  
  
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
 [in] Indice del primo evento da recuperare.  
  
 `cEvents`  
 [in] Numero di eventi da recuperare.  
  
 `prgid`  
 [out] Matrice di DISPID di valori di evento.  
  
 `prgbstr`  
 [out] Matrice di nomi di eventi.  
  
 `pcEventsFetched`  
 [out] Il numero effettivo di eventi recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`S_FALSE`|Sono stati richiesti più eventi rispetto a quelle disponibili. Non disponibile sono rappresentati con DISPID_NULL e BSTR null.|  
|`E_INVALIDARG`|Nessun elemento è stato possibile recuperare.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il DISPID e il nome per ogni evento in un intervallo specificato di eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)