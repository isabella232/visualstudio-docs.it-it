---
title: Introduzione con estensibilità del debugger | Microsoft Docs
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
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152704"
---
# <a name="getting-started-with-debugger-extensibility"></a>Introduzione all'estendibilità del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Fornisce le informazioni necessarie per creare e personalizzare i componenti del debugger utilizzati per eseguire il debug dei programmi dall'interno dell' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il debug ha aggiunto miglioramenti derivati dall'ampio test di usabilità eseguito nei [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger precedenti. È possibile utilizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il debug per eseguire un'applicazione multilingua oppure implementare modifiche immediate delle variabili durante il debug di applicazioni e soluzioni multilingue.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il debug viene eseguito out-of-process con il programma di cui è in corso il debug ed è quindi meno intrusivo nello spazio di processo dell'applicazione. Di conseguenza, è più facile scrivere componenti che interagiscono con il debugger senza influire sul programma di debug.  
  
 Per usare al meglio [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , è necessario avere familiarità con quanto segue:  
  
- Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE)  
  
- Linguaggio di programmazione C++  
  
- COM ATL  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Guida di orientamento per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descrive il processo di implementazione del debug nel prodotto, a seconda del compilatore e del relativo output.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componenti di debug, tra cui il motore di debug (de), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).  
  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come il motore di debug (DE) opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.
