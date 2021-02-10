---
title: Stack frame | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un stack frame nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97adb5d453e147c45ae1f268a20a2d3091286508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960728"
---
# <a name="stack-frames"></a>Stack frame
Nell'architettura del debugger, un *stack frame*:

- È un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Un stack frame include le variabili locali della funzione e gli argomenti. Per eseguire il debug con Visual Studio, il linguaggio o l'ambiente di cui è in corso il debug deve supportare gli stack frame.

- È in grado di identificare e descrivere se stesso e può restituire il thread associato. Un stack frame può anche restituire il contesto del codice che rappresenta il puntatore all'istruzione corrente e i contesti di documentazione e di valutazione dell'espressione associati.

- Dispone di proprietà che descrivono il nome, il tipo e il valore di variabili e argomenti locali e che vengono visualizzati in diverse finestre di debug dell'IDE.

- È rappresentato da un'interfaccia [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , in genere creata da un motore di debug (de) o da una macchina virtuale come conseguenza dell'esecuzione di un thread.

## <a name="see-also"></a>Vedi anche
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
