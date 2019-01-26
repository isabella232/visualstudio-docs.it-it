---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cbe007afc111d1638775471e9412a5d30743850
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070877"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Esegue il programma di debugger. Il thread viene restituito per fornire le informazioni sui debugger thread in cui l'utente visualizza quando l'esecuzione del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Esistono tre modi diversi, che un debugger può riprendere l'esecuzione dopo l'arresto:  
  
- Eseguire: Annullare qualsiasi passaggio precedente ed eseguire fino al punto di interruzione successivo e così via.  
  
- Passaggio: Annullare qualsiasi passaggio precedente ed eseguire fino a quando non viene completato il passaggio della nuova.  
  
- Continuare: Eseguire di nuovo e lasciare attiva qualsiasi passaggio precedente.  
  
  Il thread passato a `ExecuteOnThread` è utile quando si decide il passaggio da annullare. Se non si conosce il thread, in esecuzione Esegui Annulla tutti i passaggi. Con una conoscenza del thread, devi solo annullare il passaggio al thread attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)