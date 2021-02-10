---
title: Thread | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un thread nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec3c427e722739f17984866b8756d606ecb57813
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965460"
---
# <a name="threads"></a>Thread
Nell'architettura del debugger, un *thread*:

- È l'unità di calcolo fondamentale. Un thread esegue in modo sequenziale le istruzioni all'interno del contesto di un singolo stack di chiamate, passando da un contesto di codice a quello successivo.

- Consente di identificare se stesso e il programma in cui è in esecuzione. I thread possono essere denominati, sospesi e ripresi. Un thread può anche enumerare gli stack frame associati e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di un stack frame, un thread può restituire il thread logico associato, se presente. Un thread ha proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzate nella finestra **thread** dell'IDE.

- È rappresentato da un'interfaccia [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) , in genere creata da un motore di debug (de) o da una macchina virtuale come conseguenza dell'esecuzione di un programma.

## <a name="see-also"></a>Vedi anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
