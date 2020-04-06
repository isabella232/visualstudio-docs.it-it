---
title: Condivizioni del debugger . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738969"
---
# <a name="debugger-contexts"></a>Contesti del debuggerDebugger contexts
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, il motore di debug (DE) funziona contemporaneamente all'interno di diversi contesti distinti, come indicato di seguito:In debugging, the debug engine (DE) operates simultaneously within several distinct contexts, as follows:

- Contesto del codice, che descrive la posizione corrente nel flusso di esecuzione di un programma.

- Contesto o posizione della documentazione, che descrive la posizione corrente all'interno di un documento di origine.

- Contesto di valutazione dell'espressione, che descrive il contesto in cui verrà eseguita la valutazione dell'espressione.

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto del codice](../../extensibility/debugger/code-context.md) Viene illustrato il contesto del codice come indirizzo nel flusso di istruzioni di un programma nelle architetture di runtime di oggi rispetto ai linguaggi non tradizionali, in cui il codice potrebbe non essere rappresentato da istruzioni, ma alcuni altri mezzi.

 [Posizione del documento](../../extensibility/debugger/document-position.md) Definisce la posizione del documento nel debug di Visual Studio tramite un'astrazione di una posizione in un file di origine come noto all'IDE.

 [Contesto del documento](../../extensibility/debugger/document-context.md) Viene illustrato il contesto del documento rappresenta nel debug di Visual Studio in relazione a un file di origine. Viene inoltre illustrato come il gestore di simboli esegue il mapping di un contesto di codice al contesto della documentazione.

 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md) Fornisce informazioni su un contesto di valutazione dell'espressione in Visual Studio. Ad esempio, un contesto di valutazione dell'espressione associato a uno stack frame fornisce il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti di debugDebug concepts](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali relativi all'architettura di debug.

 [Componenti di debug](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug di Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
