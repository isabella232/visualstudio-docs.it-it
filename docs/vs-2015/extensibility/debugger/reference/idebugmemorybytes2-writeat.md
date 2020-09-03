---
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2479ac3948f81769ba2e73c746fd1811652aa239
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180565"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Scrive il numero di byte di memoria specificato, a partire dall'indirizzo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStartContext`  
 in Oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che specifica la posizione in cui iniziare a scrivere i byte.  
  
 `dwCount`  
 [in] Numero di byte da scrivere.  
  
 `rgbMemory`  
 in Byte da scrivere. Si presuppone che questa matrice abbia una dimensione di almeno `dwCount` byte.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` se non tutti i byte possono essere scritti o restituisce un codice di errore (in genere `E_FAIL` ).  
  
## <a name="remarks"></a>Osservazioni  
 Se l'indirizzo iniziale non si trova all'interno della finestra di memoria rappresentata da questo oggetto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , non viene eseguita alcuna operazione di scrittura e viene restituito un codice di errore, `E_FAIL` anche se la quantità da scrivere si sovrappone allo spazio di memoria.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
