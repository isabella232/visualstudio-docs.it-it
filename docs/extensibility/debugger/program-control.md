---
title: Controllo del programma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 971eb3184fc12b9ed72675fbcd46a893981b4c9e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072955"
---
# <a name="program-control"></a>Controllo del programma
In Visual Studio esegue il debug, tutte le istruzioni seguenti e continuando le routine si verificano a livello di programma:

- Impostazione dell'istruzione successiva, vale a dire, impostazione del computer alla successiva istruzione da eseguire in un ambiente particolare fotogramma

- L'esecuzione, vale a dire, continuando a uscire dalla modalità di debug passo a passo

- L'esecuzione di istruzioni per l'istruzione successiva

- Continuare con la modalità di debug passo a passo corrente

- Sospendere i thread contenuti dal programma

- Ripresa di thread di contenuti dal programma

> [!NOTE]
>  Visualizzazione dello stack di chiamate viene implementata a livello di thread. Per enumerare le informazioni di frame quando si visualizza lo stack di chiamate per un thread, è necessario implementare tutti i metodi del [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia.

## <a name="methods-of-program-control"></a>Metodi del controllo del programma
 Nella tabella seguente sono illustrati i metodi di [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che deve essere implementata per un motore di debug dalle minime funzioni (DE) e il controllo dell'esecuzione.

|Metodo|Descrizione|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione di tutti i thread contenuti da un programma da uno stato arrestato. Obbligatorio per il controllo dell'esecuzione.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione di tutti i thread contenuti da un programma da uno stato arrestato. Obbligatorio per il controllo dell'esecuzione.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio sul thread specificato. Continua l'esecuzione di tutti gli altri thread contenuti dal programma. Obbligatorio per il controllo dell'esecuzione.|

 Per i programmi con multithreading, è necessario implementare anche il [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metodo e tutti i metodi del [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Valutazione di controllo e lo stato di esecuzione](../../extensibility/debugger/execution-control-and-state-evaluation.md)