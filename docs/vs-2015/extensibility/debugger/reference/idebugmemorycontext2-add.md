---
title: IDebugMemoryContext2::Add | Microsoft Docs
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
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 47fe65ae76f60026f08d18ce17fc48e22885e042
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519111"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugMemoryContext2::Add](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorycontext2-add).  
  
Aggiunge il valore specificato per il contesto corrente e restituisce un nuovo contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCount`  
 [in] Il valore da aggiungere al contesto corrente.  
  
 `ppMemCxt`  
 [out] Restituisce un nuovo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un contesto in memoria è un indirizzo, quindi aggiunge un valore a un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia contesto.  
  
 Questo metodo deve produrre sempre un nuovo contesto, anche se l'indirizzo risulta è all'esterno dello spazio di memoria associato al contesto. L'unica eccezione è se non può essere allocata nessuna memoria per il nuovo contesto o se `ppMemCxt` è un valore null (ovvero un errore).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
