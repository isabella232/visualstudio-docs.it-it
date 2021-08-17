---
title: Contesto del debugger | Microsoft Docs
description: "Informazioni sul funzionamento del Visual Studio di debug all'interno di contesti distinti: contesto del codice, contesto o posizione della documentazione e contesto di valutazione delle espressioni."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2d4df19ac3287788010a9db54cd1f237aaf13089b16e418068cbcd334dfc2cb3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343279"
---
# <a name="debugger-contexts"></a>Contesti del debugger
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, il motore di debug (DE) opera contemporaneamente all'interno di diversi contesti distinti, come indicato di seguito:

- Contesto del codice, che descrive la posizione corrente nel flusso di esecuzione di un programma.

- Contesto o posizione della documentazione, che descrive la posizione corrente all'interno di un documento di origine.

- Contesto di valutazione dell'espressione, che descrive il contesto in cui verrà valutata l'espressione.

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto del codice](../../extensibility/debugger/code-context.md) Il contesto del codice viene illustrato come indirizzo nel flusso di istruzioni di un programma nelle architetture di run-time attuali rispetto ai linguaggi non differenziali, in cui il codice potrebbe non essere rappresentato da istruzioni, ma da altri mezzi.

 [Posizione del documento](../../extensibility/debugger/document-position.md) Definisce la posizione del documento Visual Studio debug tramite un'astrazione di una posizione in un file di origine come noto all'IDE.

 [Contesto del documento](../../extensibility/debugger/document-context.md) Illustra il contesto del documento rappresentato Visual Studio debug in relazione a un file di origine. Viene inoltre illustrato come il gestore di simboli esegue il mapping di un contesto di codice al contesto della documentazione.

 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md) Fornisce informazioni su un contesto di valutazione dell'espressione in Visual Studio. Ad esempio, un contesto di valutazione dell'espressione associato a un stack frame fornisce il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debug](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali dell'architettura di debug.

 [Eseguire il debug dei componenti](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti Visual Studio di debug, tra cui il motore di debug (DE), l'analizzatore di espressioni (edizione Enterprise) e il gestore di simboli (SH).

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
