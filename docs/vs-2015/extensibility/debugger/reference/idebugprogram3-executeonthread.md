---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ad46418897f4cdd2521209dd6643362e81bfcb6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529862"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProgram3::ExecuteOnThread](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram3-executeonthread).  
  
Esegue il programma di debugger. Il thread viene restituito per fornire le informazioni sui debugger thread in cui l'utente visualizza quando l'esecuzione del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
-   Eseguire: Annullare qualsiasi passaggio precedente ed eseguire fino al punto di interruzione successivo e così via.  
  
-   Passaggio: Annullare qualsiasi passaggio precedente ed eseguire fino a quando non viene completato il passaggio della nuova.  
  
-   Continuare: Eseguire di nuovo e lasciare attiva qualsiasi passaggio precedente.  
  
 Il thread passato a `ExecuteOnThread` è utile quando si decide il passaggio da annullare. Se non si conosce il thread, in esecuzione Esegui Annulla tutti i passaggi. Con una conoscenza del thread, devi solo annullare il passaggio al thread attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

