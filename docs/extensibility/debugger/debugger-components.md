---
title: Componenti del debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28afdd7f12e7d83b042f5c705c85fa567fdbb979
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345887"
---
# <a name="debugger-components"></a>Componenti del debugger
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger viene implementato come un pacchetto VSPackage e gestisce la sessione di debug intero. La sessione di debug è costituito dai seguenti elementi:

- **Eseguire il debug del pacchetto:** Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger fornisce la stessa interfaccia utente indipendentemente da ciò che viene eseguito il debug.

- **Gestione sessioni di debug (SDM):** Fornisce un'interfaccia coerente a livello di codice per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger per la gestione di numerosi motori di debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Gestione di debug di processi (PDM):** Consente di gestire, per tutte le istanze in esecuzione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un elenco di tutti i programmi che possono essere o sottoposti a debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Eseguire il debug del motore (DE):** È responsabile del monitoraggio di un programma in fase di debug, comunica lo stato del programma in esecuzione per il modello SDM e PDM e l'interazione con l'analizzatore di espressioni e i provider di simboli per fornire analisi in tempo reale dello stato della memoria del programma e variabili. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per i linguaggi supportati) e fornitori di terze parti che desiderano supportare le proprie fase di esecuzione.

- **Analizzatore di espressioni (EE):** Fornisce il supporto per la valutazione in modo dinamico di variabili ed espressioni fornite dall'utente quando un programma è stato arrestato un momento particolare. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per i linguaggi supportati) e fornitori di terze parti che desiderano supportare la propria lingua.

- **Provider di simboli (SP):** Anche chiamato un gestore di simboli, esegue il mapping i simboli di debug di un programma per un'istanza in esecuzione del programma in modo che è possibile fornire informazioni significative (ad esempio debug a livello di codice sorgente e valutazione delle espressioni). Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per Common Language Runtime [Common Language Runtime] simboli e il DataBase di programma [in] simbolo formato file) e da fornitori di terze parti che hanno il proprio metodo proprietario di archiviare le informazioni di debug.

  Il diagramma seguente mostra la relazione tra questi elementi del debugger di Visual Studio.

  ![Panoramica dei componenti di debug](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Contenuto della sezione
 [Eseguire il debug del pacchetto](../../extensibility/debugger/debug-package.md) illustra il pacchetto di debug, che viene eseguito nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] della shell e provvede a tutto l'interfaccia utente.

 [Gestione debug del processo](../../extensibility/debugger/process-debug-manager.md) offre una panoramica delle funzionalità di PDM, ovvero la gestione dei processi che è possibile eseguire il debug.

 [Gestione del debug sessione](../../extensibility/debugger/session-debug-manager.md) definisce il modello SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. Il modello SDM gestisce il DE.

 [Motore di debug](../../extensibility/debugger/debug-engine.md) documenta i servizi di debug che fornisce la Germania.

 [Modalità operative](../../extensibility/debugger/operational-modes.md) offre una panoramica delle tre modalità in cui può operare nell'IDE: progettare la modalità, modalità di esecuzione e la modalità di interruzione. Vengono illustrati anche i meccanismi di transizione.

 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) spiega lo scopo dell'analizzatore di Espressioni in fase di esecuzione.

 [Provider di simboli](../../extensibility/debugger/symbol-provider.md) viene illustrato come fare, al momento dell'implementazione, il provider di simbolo valuta variabili ed espressioni.

 [Digitare visualizzatore e il visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) esamina quali un visualizzatore di tipi e Visualizzatore personalizzato sono e quale ruolo svolge l'analizzatore di espressioni nel supporto di entrambi.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) vengono descritti i principali concetti dell'architettura di debug.

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) viene spiegato come la Germania agisce contemporaneamente all'interno di contesti di valutazione di codice, documentazione ed espressione. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione pertinente a esso.

 [Eseguire il debug di attività](../../extensibility/debugger/debugging-tasks.md) contiene collegamenti alle varie attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.

## <a name="see-also"></a>Vedere anche
- [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)