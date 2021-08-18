---
title: Concetti relativi al debugger | Microsoft Docs
description: Informazioni sui concetti relativi all'architettura usati nella progettazione Visual Studio pacchetto di debug per facilitare la compilazione in base a tale pacchetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: af9349492bbedc9bcf87af5eda58b19f571fa7e6cac6dcc5c6b89f05ce42ca9e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343182"
---
# <a name="debugger-concepts"></a>Concetti relativi al debugger
Per eseguire la compilazione Visual Studio pacchetto di debug, è necessario avere familiarità con i concetti relativi all'architettura usati nella progettazione del pacchetto.

## <a name="in-this-section"></a>Contenuto della sezione
 [Sessione di debug](../../extensibility/debugger/debug-session.md) Viene illustrato il ruolo di una sessione nell'architettura di debug.

 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md) Definisce che cos'è un server in termini di architettura di debug, sia in termini astratti che fisici.

 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md) Definisce che cos'è un fornitore di porte in termini di architettura di debug.

 [Porte](../../extensibility/debugger/ports.md) Definisce che cos'è una porta in termini di architettura di debug.

 [Processi](../../extensibility/debugger/processes.md) Definisce che cos'è un processo in termini di architettura di debug.

 [Nodi di programma](../../extensibility/debugger/program-nodes.md) Definisce un nodo di programma in termini di architettura di debug, incluso il modo in cui può identificarsi e il processo in cui è in esecuzione.

 [Programmi](../../extensibility/debugger/programs.md) Definisce un programma in termini di architettura di debug.

 [Thread](../../extensibility/debugger/threads.md) Definisce le caratteristiche dei thread in termini di architettura di debug.

 [Stack frame](../../extensibility/debugger/stack-frames.md) Definisce un stack frame in termini di architettura di debug. Un stack frame è un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread.

 [Moduli](../../extensibility/debugger/modules.md) Definisce un modulo, in termini di architettura di debug, come contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

 [Punti di interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definisce i tre tipi di punti di interruzione, in sospeso, associati ed errori, in termini di architettura di debug.

## <a name="related-sections"></a>Sezioni correlate
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo del motore di debug all'interno di contesti di codice, documentazione e valutazione delle espressioni. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti Visual Studio debug di , che includono il motore di debug (DE), l'analizzatore di espressioni (edizione Enterprise) e il gestore dei simboli (SH).

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
