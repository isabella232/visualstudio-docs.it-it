---
title: Modalità di interruzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182256"
---
# <a name="entering-break-mode"></a>Attivazione della modalità di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo che si verifica quando viene rilevato un punto di interruzione dopo l'esecuzione di una funzione, l'esecuzione alla riga di codice sorgente che contiene il cursore di o in esecuzione in un punto di interruzione.  
  
## <a name="break-mode-process"></a>Processo della modalità di interruzione  
  
1. Il motore di debug (DE) Invia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), o qualsiasi altro evento di arresto per causare l'IDE attivare la modalità di interruzione.  
  
2. Il modello SDM Ottiene le informazioni sullo stack di chiamata dal thread, come indicato di seguito:  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere le informazioni sul codice sorgente  
  
    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) per ottenere il nome del file  
  
    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) per ottenere l'intervallo di istruzioni  
  
    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) per ottenere informazioni sulla memoria  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
