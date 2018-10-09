---
title: IDebugProcess3::Continue | Microsoft Docs
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
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2cda72271a7a4654280a93e7fa7150c0dd295405
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527324"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProcess3::Continue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess3-continue).  
  
Continua l'esecuzione di questo processo da arrestare. Qualsiasi stato di esecuzione precedente (ad esempio, un passaggio) viene mantenuto, e il processo viene avviato l'esecuzione anche in questo caso.  
  
> [!NOTE]
>  Questo metodo deve essere usato al posto di [continuazione](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread di proseguire.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su questo processo indipendentemente da quanti processi sono in fase di debug o processo che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio, un passaggio) e l'esecuzione continua come se non aveva mai arrestato prima di completare l'esecuzione precedente. Vale a dire, se un thread in questo processo stava eseguendo un'operazione dell'istruzione / routine ed è stato arrestato perché è stato arrestato un altro processo e quindi `Continue` è stato chiamato, l'oggetto specificato thread deve completare l'operazione originale dell'istruzione / routine.  
  
 **Avviso** non invia un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
