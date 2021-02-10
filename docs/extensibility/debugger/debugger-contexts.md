---
title: Contesti del debugger | Microsoft Docs
description: "Informazioni sul funzionamento del motore di debug di Visual Studio all'interno di contesti distinti: contesto del codice, contesto della documentazione o posizione e contesto di valutazione dell'espressione."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89d2da35fb7ffa81ec9f6a882e6b35d42fc8f00c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952434"
---
# <a name="debugger-contexts"></a>Contesti del debugger
Durante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug, il motore di debug (de) opera simultaneamente in diversi contesti distinti, come indicato di seguito:

- Il contesto del codice, che descrive la posizione corrente nel flusso di esecuzione di un programma.

- Il contesto o la posizione della documentazione che descrive la posizione corrente all'interno di un documento di origine.

- Contesto di valutazione dell'espressione, che descrive il contesto in cui verrà eseguita la valutazione dell'espressione.

## <a name="in-this-section"></a>Contenuto della sezione
 [Contesto del codice](../../extensibility/debugger/code-context.md) Viene illustrato il contesto del codice come indirizzo nel flusso di istruzioni di un programma nelle architetture di runtime odierne rispetto ai linguaggi non tradizionali, in cui il codice non può essere rappresentato da istruzioni, ma in altre parole.

 [Posizione del documento](../../extensibility/debugger/document-position.md) Definisce la posizione del documento nel debug di Visual Studio per mezzo di un'astrazione di una posizione in un file di origine, come noto all'IDE.

 [Contesto del documento](../../extensibility/debugger/document-context.md) Viene descritto il contesto del documento rappresentato nel debug di Visual Studio in relazione a un file di origine. Viene inoltre illustrato come il gestore di simboli esegue il mapping di un contesto di codice al contesto della documentazione.

 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md) Fornisce informazioni su un contesto di valutazione dell'espressione in Visual Studio. Ad esempio, un contesto di valutazione dell'espressione associato a un stack frame fornisce il contesto per la valutazione di variabili locali, parametri di metodo e membri di classe.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti di debug](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i principali concetti dell'architettura di debug.

 [Componenti di debug](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug di Visual Studio, tra cui il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.
