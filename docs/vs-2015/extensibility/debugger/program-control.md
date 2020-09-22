---
title: Controllo programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839611"
---
# <a name="program-control"></a>Controllo del programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nel debug di Visual Studio, tutte le routine di esecuzione e continuazione seguenti si verificano a livello di programma:  
  
- Impostazione dell'istruzione successiva, ovvero l'impostazione del computer sull'istruzione successiva da eseguire in un particolare ambiente frame  
  
- In esecuzione, ovvero continuando a uscire dalla modalità di avanzamento  
  
- Esecuzione dell'istruzione successiva  
  
- Continuazione della modalità di esecuzione in corso  
  
- Sospensione dei thread contenuti nel programma  
  
- Ripresa dei thread contenuti nel programma  
  
> [!NOTE]
> La visualizzazione dello stack di chiamate è implementata a livello di thread. Per enumerare le informazioni sul frame quando si visualizza lo stack di chiamate per un thread, è necessario implementare tutti i metodi dell'interfaccia [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  
  
## <a name="methods-of-program-control"></a>Metodi di controllo del programma  
 La tabella seguente illustra i metodi di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che devono essere implementati per un motore di debug con funzionalità minime (de) e un controllo di esecuzione.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione di tutti i thread contenuti in un programma da uno stato interrotto. Obbligatorio per il controllo dell'esecuzione.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione di tutti i thread contenuti in un programma da uno stato interrotto. Obbligatorio per il controllo dell'esecuzione.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio sul thread specificato. Continua l'esecuzione di tutti gli altri thread contenuti nel programma. Obbligatorio per il controllo dell'esecuzione.|  
  
 Per i programmi multithread, è necessario implementare anche il metodo [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) e tutti i metodi dell'interfaccia [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
