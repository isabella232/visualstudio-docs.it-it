---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3733d6582559f8042ec1e7d5d8d8814a0a555c20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857301"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Questo metodo recupera un elenco di alias dal programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `uRequest`  
 [in] Il numero massimo di alias da restituire (specifica la lunghezza della matrice passato nel `ppAliases`).  
  
 `ppAliases`  
 [in, out] Matrice da riempire con alias (se si tratta di un valore null e `uRequest` è 0, verrà restituito il conteggio degli alias che possono essere restituiti da `puFetched`).  
  
 `puFetched`  
 [out] Restituisce il numero di alias ottenuti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)