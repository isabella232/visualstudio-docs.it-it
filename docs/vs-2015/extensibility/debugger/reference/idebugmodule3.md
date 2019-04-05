---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 923bdb2811a1200b7f638fc2f5727e2d1dbe83b8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967735"
---
# <a name="idebugmodule3"></a>IDebugModule3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un modulo che supporta una posizione alternativa di simboli e JustMyCode stati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per supportare le posizioni alternative di simboli e lavorare con gli stati JustMyCode (vedere la [glossario del Debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) per una definizione di "JustMyCode").  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) restituisce questa interfaccia. L'invia DE il [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) interfaccia per la gestione di debug di sessione (SDM) usando la [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo). Inoltre, una chiamata a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) in un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Restituisce un elenco di percorsi cercati i simboli e i risultati di ogni percorso di ricerca.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carica e inizializza i simboli per il modulo corrente.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Restituisce flag che specifica se il modulo rappresenta il codice utente.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Specifica se il modulo deve essere considerato codice utente o No.|  
  
## <a name="remarks"></a>Note  
 Visual Studio è il consumer tipici di questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
