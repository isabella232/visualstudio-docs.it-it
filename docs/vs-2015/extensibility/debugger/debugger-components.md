---
title: Componenti del debugger | Microsoft Docs
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
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b1b8f12a8bfa15a352f38d021a64a6f9f8b9244
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525574"
---
# <a name="debugger-components"></a>Componenti del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [i componenti del Debugger](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-components).  
  
Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger viene implementato come un pacchetto VSPackage e gestisce la sessione di debug intero. La sessione di debug è costituito dai seguenti elementi:  
  
-   **Pacchetto di debug:** il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger fornisce la stessa interfaccia utente indipendentemente da ciò che viene eseguito il debug.  
  
-   **Gestione del debug sessione (SDM):** offre un'interfaccia coerente a livello di codice per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger per la gestione di numerosi motori di debug. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   **Gestione debug del processo (PDM):** gestisce, per tutte le istanze in esecuzione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], un elenco di tutti i programmi che possono essere o sottoposti a debug. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   **Eseguire il debug del motore (DE):** è responsabile del monitoraggio di un programma in fase di debug, comunica lo stato del programma in esecuzione per il modello SDM e PDM e l'interazione con l'analizzatore di espressioni e provider di simboli per fornire analisi in tempo reale del stato della memoria e variabili del programma. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (per i linguaggi supportati) e fornitori di terze parti che desiderano supportare le proprie fase di esecuzione.  
  
-   **L'analizzatore di espressioni (EE):** fornisce il supporto per la valutazione in modo dinamico di variabili ed espressioni fornite dall'utente quando un programma è stato arrestato un momento particolare. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (per i linguaggi supportati) e fornitori di terze parti che desiderano supportare la propria lingua.  
  
-   **Provider di simboli (SP):** l'acronimo di un gestore di simboli, esegue il mapping di simboli di debug di un programma per un'istanza in esecuzione del programma in modo che è possibile fornire informazioni significative (ad esempio, la valutazione di debug e l'espressione di livello di codice sorgente). Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (per Common Language Runtime [Common Language Runtime] simboli e il DataBase di programma [in] simbolo formato file) e da fornitori di terze parti che hanno il proprio metodo proprietario di archiviare le informazioni di debug.  
  
 Il diagramma seguente mostra la relazione tra questi elementi del debugger di Visual Studio.  
  
 ![Panoramica dei componenti di debug](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>In questa sezione  
 [Pacchetto di debug](../../extensibility/debugger/debug-package.md)  
 Viene illustrato il pacchetto di debug, che viene eseguito nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] della shell e provvede a tutto l'interfaccia utente.  
  
 [Gestione del debug dei processi](../../extensibility/debugger/process-debug-manager.md)  
 Viene fornita una panoramica delle funzionalità di PDM, ovvero la gestione dei processi che è possibile eseguire il debug.  
  
 [Gestione del debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)  
 Definisce il modello SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. Il modello SDM gestisce il DE.  
  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)  
 Documenta i servizi di debug che fornisce la Germania.  
  
 [Modalità operative](../../extensibility/debugger/operational-modes.md)  
 Viene fornita una panoramica delle tre modalità in cui può operare nell'IDE: progettare la modalità, modalità di esecuzione e la modalità di interruzione. Vengono illustrati anche i meccanismi di transizione.  
  
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)  
 Viene illustrato lo scopo dell'analizzatore di Espressioni in fase di esecuzione.  
  
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)  
 Viene illustrato come fare, al momento dell'implementazione, il provider di simbolo valuta variabili ed espressioni.  
  
 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Vengono illustrate le caratteristiche sono un visualizzatore di tipi e Visualizzatore personalizzato e quale ruolo svolge l'analizzatore di espressioni nel supporto di entrambi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come la Germania agisce contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressioni. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

