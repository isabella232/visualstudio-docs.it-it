---
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8553ae1c75bd8b5716182485f0b0dc8d77da14f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147725"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce il successivo set di elementi dall'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugThread2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugThread2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Numero di elementi da recuperare. Specifica inoltre la dimensione massima della `rgelt` matrice.  
  
 `rgelt`  
 [in, out] Matrice di elementi [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) da compilare.  
  
 `pceltFetched`  
 out Restituisce il numero di elementi effettivamente restituiti in `rgelt` .  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è possibile che venga restituito un numero di elementi inferiore al numero richiesto; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
