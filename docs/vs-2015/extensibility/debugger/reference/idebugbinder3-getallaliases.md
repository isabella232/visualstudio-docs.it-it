---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e88ed8a93d77910d76cefefc0ee97c01f88de15b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531151"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugBinder3::GetAllAliases](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-getallaliases).  
  
Questo metodo recupera un elenco di alias dal programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
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

