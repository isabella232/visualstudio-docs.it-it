---
title: Componenti del debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200657"
---
# <a name="debugger-components"></a>Componenti del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger viene implementato come pacchetto VSPackage e gestisce l'intera sessione di debug. La sessione di debug include gli elementi seguenti:  
  
- **Pacchetto di debug:** Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger fornisce la stessa interfaccia utente indipendentemente dall'oggetto di cui è in corso il debug.  
  
- **Gestione debug sessione (SDM):** Fornisce un'interfaccia a livello di codice coerente al [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger per la gestione di un'ampia gamma di motori di debug. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Gestione debug processo (PDM):** Gestisce, per tutte le istanze in esecuzione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , un elenco di tutti i programmi che possono essere o di cui è in corso il debug. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Motore di debug (de):** È responsabile del monitoraggio di un programma di cui è in corso il debug, della comunicazione dello stato del programma in esecuzione con SDM e del PDM e dell'interazione con l'analizzatore di espressioni e il provider di simboli per fornire l'analisi in tempo reale dello stato della memoria e delle variabili di un programma. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (per le lingue supportate) e da fornitori di terze parti che desiderano supportare il proprio tempo di esecuzione.  
  
- **Analizzatore di espressioni (EE):** Fornisce supporto per la valutazione dinamica di variabili ed espressioni fornite dall'utente quando un programma è stato interrotto in un determinato punto. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (per le lingue supportate) e da fornitori di terze parti che desiderano supportare le proprie lingue.  
  
- **Provider di simboli (SP):** Detto anche gestore di simboli, esegue il mapping dei simboli di debug di un programma a un'istanza in esecuzione del programma in modo che possano essere fornite informazioni significative, ad esempio il debug a livello di codice sorgente e la valutazione dell'espressione. Viene implementato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (per i simboli Common Language Runtime [CLR] e il formato di file di simboli del database di programma [PDB]) e da fornitori di terze parti che hanno un metodo proprietario per archiviare le informazioni di debug.  
  
  Il diagramma seguente illustra la relazione tra questi elementi del debugger di Visual Studio.  
  
  ![Panoramica dei componenti di debug](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Pacchetto di debug](../../extensibility/debugger/debug-package.md)  
 Viene illustrato il pacchetto di debug, che viene eseguito nella [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Shell e gestisce tutte le interfacce utente.  
  
 [Gestione del debug dei processi](../../extensibility/debugger/process-debug-manager.md)  
 Viene fornita una panoramica delle funzionalità di PDM, ovvero la gestione dei processi di cui è possibile eseguire il debug.  
  
 [Gestione del debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)  
 Definisce SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. SDM gestisce il DE.  
  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)  
 Documenta i servizi di debug forniti da.  
  
 [Modalità operative](../../extensibility/debugger/operational-modes.md)  
 Viene fornita una panoramica delle tre modalità di funzionamento dell'IDE: modalità di progettazione, modalità di esecuzione e modalità di interruzioni. Vengono inoltre illustrati i meccanismi di transizione.  
  
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)  
 Viene illustrato lo scopo di EE in fase di esecuzione.  
  
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)  
 Viene illustrato come, in fase di implementazione, il provider di simboli valuta le variabili e le espressioni.  
  
 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Vengono illustrati un visualizzatore di tipi e un visualizzatore personalizzato e il ruolo che l'analizzatore di espressioni svolge per supportare entrambi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Spiega in che modo il DE opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Per iniziare](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
