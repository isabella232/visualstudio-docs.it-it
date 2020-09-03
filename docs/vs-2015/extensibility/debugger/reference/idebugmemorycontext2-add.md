---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1b4b236b438d5ff94120c00952d5cd3adfd590
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164079"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aggiunge il valore specificato al contesto corrente e restituisce un nuovo contesto.  
  
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
 in Valore da aggiungere al contesto corrente.  
  
 `ppMemCxt`  
 out Restituisce un nuovo oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Un contesto di memoria è un indirizzo, quindi l'aggiunta di un valore a un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia di contesto.  
  
 Questo metodo deve sempre produrre un nuovo contesto, anche se l'indirizzo risultante è esterno allo spazio di memoria associato a questo contesto. L'unica eccezione è rappresentata dal caso in cui non sia possibile allocare memoria per il nuovo contesto o se `ppMemCxt` è un valore null (errore).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
