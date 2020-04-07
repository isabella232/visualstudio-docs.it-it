---
title: Stack frames Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712847"
---
# <a name="stack-frames"></a>Stack frame
Nell'architettura del debugger, uno *stack frame*:

- È un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Uno stack frame contiene le variabili locali della funzione e gli argomenti ad essa. Per eseguire il debug con Visual Studio, il linguaggio o l'ambiente sottoposto a debug deve supportare gli stack frame.

- Può identificare e descrivere se stesso e può restituire il thread associato. Uno stack frame può anche restituire il contesto di codice che rappresenta il puntatore all'istruzione corrente e i contesti di valutazione della documentazione e dell'espressione associati.

- Dispone di proprietà che descrivono il nome, tipo e valore di variabili e argomenti locali e che vengono visualizzati in varie finestre di debug dell'IDE.

- È rappresentato da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, in genere creato da un motore di debug (DE) o macchina virtuale come conseguenza dell'esecuzione di un thread.

## <a name="see-also"></a>Vedere anche
- [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
