---
title: Contesti del debugger | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b39e53ab06d3ce1633a77fc1fe324206f144dda1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793542"
---
# <a name="debugger-contexts"></a>Contesti del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug, il motore di debug (DE) opera contemporaneamente in diversi contesti di distinti, come indicato di seguito:  
  
-   Contesto del codice, che descrive la posizione corrente nel flusso di esecuzione del programma.  
  
-   Il contesto di documentazione o la posizione, che descrive la posizione corrente all'interno di un documento di origine.  
  
-   Il contesto di valutazione espressione, che descrive il contesto nel quale espressione valutazione verrà eseguita.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Contesto del codice](../../extensibility/debugger/code-context.md)  
 Descrive il contesto del codice come un indirizzo nel flusso di istruzioni del programma in fase di esecuzione le architetture oggi e lingue non convenzionale, dove codice non può essere rappresentato da istruzioni, ma altri mezzi.  
  
 [Posizione nel documento](../../extensibility/debugger/document-position.md)  
 Definisce la posizione di documento in debug mediante un'astrazione di una posizione in un file di origine come noti all'IDE di Visual Studio.  
  
 [Contesto del documento](../../extensibility/debugger/document-context.md)  
 Descrive il contesto del documento rappresenta nel debug di Visual Studio in relazione a un file di origine. Illustra anche come il gestore di simboli esegue il mapping di un contesto del codice al contesto di documentazione.  
  
 [Contesto di valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-context.md)  
 Fornisce informazioni su un contesto di valutazione di espressioni in Visual Studio. Ad esempio, un contesto di valutazione di espressioni associato a uno stack frame fornisce il contesto per la valutazione delle variabili locali, parametri del metodo e i membri della classe.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [I concetti di debug](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
 [Componenti di debug](../../extensibility/debugger/debugger-components.md)  
 Fornisce una panoramica dei componenti di debug Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.

