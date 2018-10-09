---
title: IDebugPortNotify2 | Microsoft Docs
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
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 703e42c0b0717761816ed8ca11f42e7f22650517
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519109"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugPortNotify2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportnotify2).  
  
Questa interfaccia nei registri o Annulla la registrazione di un programma che è possibile eseguire il debug con la porta in cui viene eseguito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare l'aggiunta e rimozione di programmi dalla porta. Viene in genere implementato nello stesso oggetto che implementa il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nel `IDebugPort2` interfaccia restituisce questa interfaccia. Inoltre, una chiamata a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) restituisce questa interfaccia. Un motore di debug è possibile visualizzare questa interfaccia come parametro per [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortNotify2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programma che è possibile eseguire il debug con la porta in cui viene eseguito.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annulla la registrazione di un programma che è possibile eseguire il debug dalla porta di che cui è in esecuzione.|  
  
## <a name="remarks"></a>Note  
 A meno che una porta di debug è un modo per sapere quando i programmi vengono caricati o scaricati, un fornitore di porte personalizzato deve implementare questa interfaccia. Tutti i programmi che vengono caricati per l'esecuzione del debug attraverso una porta specifica vengono rilevati tramite questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
