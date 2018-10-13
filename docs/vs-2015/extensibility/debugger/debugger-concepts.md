---
title: Concetti relativi al debugger | Microsoft Docs
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
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 384d785b6d4779f8269e93fedcf6b841e73d9e05
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222108"
---
# <a name="debugger-concepts"></a>Concetti relativi al debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per compilare il pacchetto di debug di Visual Studio, è necessario avere familiarità con i concetti dell'architettura usati durante la progettazione del pacchetto.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Sessione di debug](../../extensibility/debugger/debug-session.md)  
 Viene illustrato il ruolo di una sessione nell'architettura di debug.  
  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Definisce quali un server sia in termini di architettura, il debug in termini fisici sia astratti.  
  
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)  
 Definisce ciò che è un fornitore di porte in termini di architettura di debug.  
  
 [Porte](../../extensibility/debugger/ports.md)  
 Definisce una porta è in termini di architettura di debug.  
  
 [Processi](../../extensibility/debugger/processes.md)  
 Definisce quali un processo è in termini di architettura di debug.  
  
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)  
 Definisce un nodo di programma in termini di architettura, inclusi come in grado di identificare se stesso e il processo che è in esecuzione nel debug.  
  
 [Programmi](../../extensibility/debugger/programs.md)  
 Definisce un programma in termini di architettura di debug.  
  
 [Thread](../../extensibility/debugger/threads.md)  
 Definisce le caratteristiche di thread in termini di architettura di debug.  
  
 [Stack frame](../../extensibility/debugger/stack-frames.md)  
 Definisce uno stack frame in termini di architettura di debug. Uno stack frame è un'astrazione di un oggetto stack che fornisce il contesto di esecuzione di un thread.  
  
 [Moduli](../../extensibility/debugger/modules.md)  
 Definisce un modulo, in termini di architettura, come un contenitore fisico di codice, ad esempio un file eseguibile o una DLL di debug.  
  
 [Punti di interruzione](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Definisce i tre tipi di punti di interruzione, in sospeso, associazione e di errore, in termini di architettura di debug.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressioni. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Fornisce una panoramica dei componenti di debug in Visual Studio, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.

