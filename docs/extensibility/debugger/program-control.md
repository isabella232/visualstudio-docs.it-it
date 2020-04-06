---
title: Controllo del programma Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738234"
---
# <a name="program-control"></a>Controllo del programma
Nel debug di Visual Studio, tutte le seguenti routine di esecuzione passo e continuazione si verificano a livello di programma:

- Impostazione dell'istruzione successiva, ovvero l'impostazione del computer sull'istruzione successiva da eseguire in un particolare ambiente frame

- Esecuzione, cioè, continuando a uscire dalla modalità di esecuzione

- Passaggio all'istruzione successiva

- Continuare con la modalità di stepping corrente

- Sospensione dei thread contenuti nel programma

- Ripresa dei thread contenuti nel programma

> [!NOTE]
> La visualizzazione dello stack di chiamate viene implementata a livello di thread. Per enumerare le informazioni sul frame durante la visualizzazione dello stack di chiamate per un thread, è necessario implementare tutti i metodi [dell'interfaccia IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Metodi di controllo del programma
 Nella tabella seguente vengono illustrati i metodi di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che devono essere implementati per un motore di debug (DE) minimamente funzionale e il controllo dell'esecuzione.

|Metodo|Descrizione|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione di tutti i thread contenuti in un programma da uno stato arrestato. Obbligatorio per il controllo dell'esecuzione.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione di tutti i thread contenuti in un programma da uno stato arrestato. Obbligatorio per il controllo dell'esecuzione.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio sul thread specificato. Continua l'esecuzione di tutti gli altri thread contenuti nel programma. Obbligatorio per il controllo dell'esecuzione.|

 Per i programmi multithreading, è necessario implementare anche il [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metodo e tutti i metodi del [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
