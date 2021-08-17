---
title: Stack frame | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un stack frame nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dc6c10f00f12d1ee8df9918530a3b04d6ba5ef4e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102857"
---
# <a name="stack-frames"></a>Stack frame
Nell'architettura del debugger, un *stack frame*:

- Astrazione di uno stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Un stack frame contiene le variabili locali della funzione e gli argomenti a essa. Per eseguire il debug con Visual Studio, il linguaggio o l'ambiente in fase di debug deve supportare stack frame.

- Può identificare e descrivere se stesso e può restituire il thread associato. Un stack frame può anche restituire il contesto del codice che rappresenta il puntatore all'istruzione corrente e i contesti di valutazione della documentazione e dell'espressione associati.

- Dispone di proprietà che descrivono il nome, il tipo e il valore delle variabili e degli argomenti locali e che vengono visualizzate in diverse finestre di debug IDE.

- È rappresentato da [un'interfaccia IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) in genere creata da un motore di debug (DE) o da una macchina virtuale come conseguenza dell'esecuzione di un thread.

## <a name="see-also"></a>Vedi anche
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
