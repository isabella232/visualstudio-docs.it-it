---
title: IDebugEngine3 | Microsoft Docs
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
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0199483257120c374c7fe088f195df81270c91da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517299"
---
# <a name="idebugengine3"></a>IDebugEngine3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugEngine3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine3).  
  
Rappresenta un motore di debug singolo (DE) che controlla il debug di uno o più moduli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da un CRI personalizzato (se supporta i simboli) per abilitare lo stato JustMyCode. Questa interfaccia deve essere implementata dal DE se supporta JustMyCode e simboli.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) per passare alle opzioni utente per i percorsi da cui caricare i simboli. Viene inoltre chiamato per impostare il GUID del motore quando ne viene creata un'istanza (questo GUID è basato sulle metriche dal momento della registrazione del motore). Il modello SDM chiama anche questa interfaccia per impostare lo stato JustMyCode e impostare tutte le eccezioni note con il debugger a uno stato specifico.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), il `IDebugEngine3` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Imposta il percorso o i percorsi che la Germania userà per eseguire la ricerca per i simboli di debug.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carica i simboli per tutti i moduli che non sono ancora stati caricati i simboli.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Indica il DE sulle informazioni JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Imposta il GUID DE tra le metriche.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Impostare tutte le eccezioni in attesa su uno stato specifico.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

