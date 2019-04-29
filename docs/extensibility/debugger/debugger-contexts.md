---
title: Contesti del debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fc77e24a1a9ca72d6f689247f0de6a9e0bf26cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889994"
---
# <a name="debugger-contexts"></a>Contesti del debugger
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, il motore di debug (DE) opera contemporaneamente in diversi contesti di distinti, come indicato di seguito:

- Contesto del codice, che descrive la posizione corrente nel flusso di esecuzione del programma.

- Il contesto di documentazione o la posizione, che descrive la posizione corrente all'interno di un documento di origine.

- Il contesto di valutazione espressione, che descrive il contesto nel quale espressione valutazione verrà eseguita.

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto codice](../../extensibility/debugger/code-context.md) contesto del codice esamina come un indirizzo nel flusso di istruzioni del programma in fase di esecuzione le architetture oggi e lingue non convenzionale, dove codice non può essere rappresentato da istruzioni, ma altri mezzi.

 [Posizione del documento](../../extensibility/debugger/document-position.md) definisce documento posizione nel debug di Visual Studio per mezzo di un'astrazione di una posizione in un file di origine come noti all'IDE.

 [Contesto del documento](../../extensibility/debugger/document-context.md) esamina il contesto del documento rappresenta nel debug di Visual Studio in relazione a un file di origine. Illustra anche come il gestore di simboli esegue il mapping di un contesto del codice al contesto di documentazione.

 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md) vengono fornite informazioni su un contesto di valutazione di espressioni in Visual Studio. Ad esempio, un contesto di valutazione di espressioni associato a uno stack frame fornisce il contesto per la valutazione delle variabili locali, parametri del metodo e i membri della classe.

## <a name="related-sections"></a>Sezioni correlate
 [Eseguire il debug concetti](../../extensibility/debugger/debugger-concepts.md) vengono descritti i principali concetti dell'architettura di debug.

 [Eseguire il debug di componenti](../../extensibility/debugger/debugger-components.md) offre una panoramica del debug di componenti, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH) di Visual Studio.

 [Eseguire il debug di attività](../../extensibility/debugger/debugging-tasks.md) contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.