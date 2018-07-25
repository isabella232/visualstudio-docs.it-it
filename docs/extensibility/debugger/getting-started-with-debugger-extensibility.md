---
title: Introduzione a estendibilità del Debugger | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1a812575d14ef6595d58cc3ecc5d9f94b8f5635
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231288"
---
# <a name="get-started-with-debugger-extensibility"></a>Introduzione all'estendibilità del debugger
Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] vengono fornite le informazioni che occorre per creare e personalizzare i componenti del debugger per eseguire il debug di programmi dall'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug ha aggiunti miglioramenti derivati dall'usabilità completa test eseguiti nel precedente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger. È possibile usare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug con il passaggio attraverso un'applicazione in più lingue oppure è possibile implementare in immediatamente la modifica delle variabili durante il debug di applicazioni e soluzioni in più lingue.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug viene eseguita out-of-process con il programma sottoposto a debug e pertanto è meno intrusivo nello spazio di processo dell'applicazione. Di conseguenza, risulta più semplice scrivere i componenti che interagiscono con il debugger senza influenzare il programma di debug.  
  
 Per usare al meglio il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], è necessario avere familiarità con gli elementi seguenti:  
  
-   Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE)  
  
-   Il linguaggio di programmazione C++  
  
-   COM ATL  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Guida di orientamento per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descrive il processo di implementazione del prodotto, a seconda del compilatore e l'output di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug di componenti, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).  
  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressioni. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.