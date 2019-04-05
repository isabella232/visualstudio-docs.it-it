---
title: Introduzione a estendibilità del Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12701abf66d49a3b462502700b3b57933369b6e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955604"
---
# <a name="getting-started-with-debugger-extensibility"></a>Introduzione all'estendibilità del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] vengono fornite le informazioni necessarie per creare e personalizzare i componenti del debugger per eseguire il debug di programmi dall'interno di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug ha aggiunti miglioramenti derivati dall'usabilità completa test eseguiti nel precedente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger. È possibile usare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug con il passaggio attraverso un'applicazione in più lingue oppure è possibile implementare in immediatamente la modifica delle variabili durante il debug di applicazioni e soluzioni in più lingue.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il debug viene eseguita out-of-process con il programma sottoposto a debug e pertanto è meno intrusivo nello spazio di processo dell'applicazione. Di conseguenza, risulta più semplice scrivere i componenti che interagiscono con il debugger senza influenzare il programma di debug.  
  
 Per usare al meglio il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], è necessario avere familiarità con il codice seguente:  
  
-   Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE)  
  
-   Il linguaggio di programmazione C++  
  
-   COM ATL  
  
## <a name="in-this-section"></a>In questa sezione  
 [Guida di orientamento per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descrive il processo di implementazione del prodotto, a seconda del compilatore e l'output di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il debug di componenti, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).  
  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressioni. Viene descritto, per ognuno dei tre contesti di, il percorso, posizione o valutazione pertinente a esso.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.
