---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180588"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legge una sequenza di byte a partire da una posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStartContext`  
 in Oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica la posizione in cui iniziare la lettura dei byte.  
  
 `dwCount`  
 in Numero di byte da leggere. Specifica anche la lunghezza della `rgbMemory` matrice.  
  
 `rgbMemory`  
 [in, out] Matrice compilata con i byte effettivamente letti.  
  
 `pdwRead`  
 out Restituisce il numero di byte contigui effettivamente letti.  
  
 `pdwUnreadable`  
 [in, out] Restituisce il numero di byte illeggibili. Può essere un valore null se il client non è interessato dal numero di byte illeggibili.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Se vengono richiesti 100 byte e i primi 50 sono leggibili, i 20 successivi sono illeggibili e i 30 rimanenti sono leggibili, questo metodo restituisce:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 In questo caso, poiché `*pdwRead + *pdwUnreadable < dwCount` il chiamante deve effettuare una chiamata aggiuntiva per leggere i restanti 30 byte dell'originale 100 richiesto e l'oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passato nel `pStartContext` parametro deve essere avanzato da 70.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
