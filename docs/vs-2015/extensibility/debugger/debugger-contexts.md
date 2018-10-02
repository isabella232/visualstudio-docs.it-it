---
title: Contesti del debugger | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 7f24360b29557ef767d1a9a5f91a6f116db9ec12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532042"
---
# <a name="debugger-contexts"></a>Contesti del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Debugger contesti](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-contexts).  
  
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

