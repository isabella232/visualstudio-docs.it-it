---
title: IDebugProgram2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f7dbad02632663474f62f561773aa62a8735071
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069382"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Le richieste che il programma di arresta l'esecuzione successiva ora di uno dei tentativi thread di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento viene inviato quando il programma quindi tenta di eseguire codice dopo questo metodo viene chiamato.  
  
 Questo metodo è asincrono, in quanto il metodo viene restituito immediatamente senza dover necessariamente attendere il blocco del programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)