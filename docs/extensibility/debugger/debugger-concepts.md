---
title: Concetti relativi al debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1d9905281c83287b8b54f57a233c2056462226f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345927"
---
# <a name="debugger-concepts"></a>Concetti relativi al debugger
Per compilare il pacchetto di debug di Visual Studio, è necessario avere familiarità con i concetti dell'architettura usati durante la progettazione del pacchetto.

## <a name="in-this-section"></a>Contenuto della sezione
 [Sessione di debug](../../extensibility/debugger/debug-session.md) viene illustrato il ruolo di una sessione nell'architettura di debug.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) definisce quali un server sia in termini di architettura, il debug in termini fisici sia astratti.

 [Porta suppliers](../../extensibility/debugger/port-suppliers.md) definisce quali un fornitore di porte sia in termini di architettura di debug.

 [Porte](../../extensibility/debugger/ports.md) definisce quale una porta è in termini di architettura di debug.

 [Processi](../../extensibility/debugger/processes.md) definisce quali un processo è in termini di architettura di debug.

 [I nodi di programma](../../extensibility/debugger/program-nodes.md) definisce un nodo di programma in termini di architettura, inclusi come in grado di identificare se stesso e il processo è in esecuzione nel debug.

 [Programmi](../../extensibility/debugger/programs.md) definisce un programma in termini di architettura di debug.

 [Thread](../../extensibility/debugger/threads.md) definisce le caratteristiche di thread in termini di architettura di debug.

 [Stack frame](../../extensibility/debugger/stack-frames.md) definisce uno stack frame in termini di architettura di debug. Uno stack frame è un'astrazione di un oggetto stack che fornisce il contesto di esecuzione di un thread.

 [I moduli](../../extensibility/debugger/modules.md) definisce un modulo, in termini di architettura, come un contenitore fisico di codice, ad esempio un file eseguibile o una DLL di debug.

 [I punti di interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) definisce tre tipi di punti di interruzione, in sospeso, associazione e di errore, in termini di architettura di debug.

## <a name="related-sections"></a>Sezioni correlate
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) spiega come il motore di debug (DE) funziona contemporaneamente all'interno di contesti di valutazione di codice, documentazione ed espressione. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) fornisce una panoramica dei componenti di debug in Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Eseguire il debug di attività](../../extensibility/debugger/debugging-tasks.md) contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.