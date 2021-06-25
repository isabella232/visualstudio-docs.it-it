---
title: Controllo del programma | Microsoft Docs
description: Informazioni sulle routine in Visual Studio debug che si verificano a livello di programma, ad esempio l'esecuzione, l'esecuzione di istruzioni, la continuazione e la sospensione/ripresa di thread.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900713"
---
# <a name="program-control"></a>Controllo del programma
Nel Visual Studio debug, tutte le routine di esecuzione e continuazione seguenti si verificano a livello di programma:

- Impostazione dell'istruzione successiva, ad esempio l'impostazione del computer sull'istruzione successiva da eseguire in un particolare ambiente frame

- Esecuzione in corso, che continua a uscire dalla modalità di esecuzione delle istruzioni

- Passaggio all'istruzione successiva

- Continuare con la modalità di esecuzione delle istruzioni corrente

- Sospensione dei thread contenuti nel programma

- Ripresa dei thread contenuti nel programma

> [!NOTE]
> La visualizzazione dello stack di chiamate viene implementata a livello di thread. Per enumerare le informazioni sui frame quando si visualizza lo stack di chiamate per un thread, è necessario implementare tutti i metodi [dell'interfaccia IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Metodi di controllo del programma
 Nella tabella seguente vengono illustrati i metodi di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che devono essere implementati per un motore di debug e un controllo di esecuzione con funzionalità minime.

|Metodo|Descrizione|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione di tutti i thread contenuti in un programma da uno stato arrestato. Obbligatorio per il controllo dell'esecuzione.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione di tutti i thread contenuti in un programma da uno stato arrestato. Obbligatorio per il controllo dell'esecuzione.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio sul thread specificato. Continua l'esecuzione di tutti gli altri thread contenuti nel programma. Obbligatorio per il controllo dell'esecuzione.|

 Per i programmi multithreading, è necessario implementare anche il metodo [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) e tutti i metodi [dell'interfaccia IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
