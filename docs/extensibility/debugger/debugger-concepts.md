---
title: Concetti relativi al debugger Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738991"
---
# <a name="debugger-concepts"></a>Concetti del debuggerDebugger concepts
Per basarsi sul pacchetto di debug di Visual Studio, è necessario avere familiarità con i concetti dell'architettura utilizzati nella progettazione del pacchetto.

## <a name="in-this-section"></a>Contenuto della sezione
 [Sessione di debug](../../extensibility/debugger/debug-session.md) Viene illustrato il ruolo di una sessione nell'architettura di debug.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) Definisce che cos'è un server in termini di architettura di debug, sia in termini astratti che fisici.

 [Fornitori portuali](../../extensibility/debugger/port-suppliers.md) Definisce il valore di un fornitore di porte in termini di architettura di debug.

 [Porte](../../extensibility/debugger/ports.md) Definisce che cos'è una porta in termini di architettura di debug.

 [Processi](../../extensibility/debugger/processes.md) Definisce che cos'è un processo in termini di architettura di debug.

 [Nodi di programma](../../extensibility/debugger/program-nodes.md) Definisce un nodo di programma in termini di architettura di debug, incluso il modo in cui può identificare se stesso e il processo in cui è in esecuzione.

 [Programmi](../../extensibility/debugger/programs.md) Definisce un programma in termini di architettura di debug.

 [Filettature](../../extensibility/debugger/threads.md) Definisce le caratteristiche dei thread in termini di architettura di debug.

 [Stack frame](../../extensibility/debugger/stack-frames.md) Definisce uno stack frame in termini di architettura di debug. Uno stack frame è un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread.

 [Moduli](../../extensibility/debugger/modules.md) Definisce un modulo, in termini di architettura di debug, come contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

 [Punti di interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definisce i tre tipi di punti di interruzione, in sospeso, associati ed errore, in termini di architettura di debug.

## <a name="related-sections"></a>Sezioni correlate
 [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo del motore di debug (DE) all'interno di contesti di valutazione del codice, della documentazione e delle espressioni. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
