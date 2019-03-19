---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
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
ms.openlocfilehash: 1b5824f945ad25f177fc169b58157377bf53bcce
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145239"
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