---
title: Concetti relativi al debugger | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738991"
---
# <a name="debugger-concepts"></a>Concetti relativi al debugger
Per compilare il pacchetto di debug di Visual Studio, è necessario acquisire familiarità con i concetti dell'architettura utilizzati per la progettazione del pacchetto.

## <a name="in-this-section"></a>Contenuto della sezione
 [Sessione di debug](../../extensibility/debugger/debug-session.md) Viene illustrato il ruolo di una sessione nell'architettura di debug.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) di Definisce ciò che un server è in termini di architettura di debug, sia in termini astratti che fisici.

 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md) Definisce ciò che un fornitore di porte è in termini di architettura di debug.

 [Porte](../../extensibility/debugger/ports.md) di Definisce l'elemento di una porta in termini di architettura di debug.

 [Processi](../../extensibility/debugger/processes.md) Definisce l'elemento di un processo in termini di architettura di debug.

 [Nodi del programma](../../extensibility/debugger/program-nodes.md) Definisce un nodo di programma in termini di architettura di debug, incluso il modo in cui può identificarsi e il processo in cui è in esecuzione.

 [Programmi](../../extensibility/debugger/programs.md) Definisce un programma in termini di architettura di debug.

 [Thread](../../extensibility/debugger/threads.md) Definisce le caratteristiche dei thread in termini di architettura di debug.

 [Stack frame](../../extensibility/debugger/stack-frames.md) Definisce un stack frame in termini di architettura di debug. Un stack frame è un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread.

 [Moduli](../../extensibility/debugger/modules.md) di Definisce un modulo, in termini di architettura di debug, come contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

 Punti di [interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definisce i tre tipi di punti di interruzione, in sospeso, associato ed errore, in termini di architettura di debug.

## <a name="related-sections"></a>Sezioni correlate
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Viene illustrato come il motore di debug (DE) opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug di Visual Studio, tra cui il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.
