---
title: Componenti del debugger - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739006"
---
# <a name="debugger-components"></a>Componenti del debugger
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger viene implementato come un VSPackage e gestisce l'intera sessione di debug. La sessione di debug comprende i seguenti elementi:

- **Pacchetto di debug:** Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger fornisce la stessa interfaccia utente indipendentemente da ciò che viene sottoposto a debug.

- **Gestione debug sessione (SDM):** Fornisce un'interfaccia a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] livello di codice coerente al Debugger per la gestione di un'ampia gamma di motori di debug. È implementato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]da .

- **Gestione debug processo (PDM):** Gestisce, per tutte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le istanze in esecuzione di , un elenco di tutti i programmi che possono essere o che sono in fase di debug. È implementato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]da .

- Motore di **debug (DE):** È responsabile del monitoraggio di un programma in fase di debug, della comunicazione dello stato del programma in esecuzione con il modello SDM e del PDM e dell'interazione con l'analizzatore di espressioni e il provider di simboli per fornire l'analisi in tempo reale dello stato della memoria e delle variabili di un programma. È implementato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da (per le lingue che supporta) e fornitori di terze parti che desiderano supportare il proprio tempo di esecuzione.

- **Valutatore di espressioni (EE):** Fornisce supporto per la valutazione dinamica di variabili ed espressioni fornite dall'utente quando un programma è stato arrestato in un determinato punto. È implementato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da (per le lingue che supporta) e fornitori di terze parti che vogliono supportare le proprie lingue.

- **Provider di simboli (SP):** Denominato anche gestore di simboli, esegue il mapping dei simboli di debug di un programma a un'istanza in esecuzione del programma in modo che possano essere fornite informazioni significative, ad esempio il debug a livello di codice sorgente e la valutazione delle espressioni. Viene implementato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da (per i simboli di Common Language Runtime [CLR] e il formato di file di simboli PDB (Program DataBase) e da fornitori di terze parti che dispongono di un proprio metodo proprietario per l'archiviazione delle informazioni di debug.

  Nel diagramma seguente viene illustrata la relazione tra questi elementi del debugger di Visual Studio.

  ![Cenni preliminari sul debug dei componentiDebugging Components Overview](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Contenuto della sezione
 [Pacchetto di debug](../../extensibility/debugger/debug-package.md) Viene illustrato il pacchetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, che viene eseguito nella shell e gestisce tutta l'interfaccia utente.

 [Gestione debug processo](../../extensibility/debugger/process-debug-manager.md) Fornisce una panoramica delle funzionalità del PDM, ovvero il gestore dei processi di cui è possibile eseguire il debug.

 [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md) Definisce il modello SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. Il sistema SDM gestisce il DE.

 [Motore di debug](../../extensibility/debugger/debug-engine.md) Documenta i servizi di debug che fornisce il DE.

 [Modalità operative](../../extensibility/debugger/operational-modes.md) Fornisce una panoramica delle tre modalità in cui l'IDE può operare: modalità di progettazione, modalità di esecuzione e modalità di interruzione. Vengono discussi anche i meccanismi di transizione.

 [Valutatore di espressioni](../../extensibility/debugger/expression-evaluator.md) Viene illustrato lo scopo di EE in fase di esecuzione.

 [Provider di simboli](../../extensibility/debugger/symbol-provider.md) Viene illustrato come, in fase di implementazione, il provider di simboli valuta variabili ed espressioni.

 [Visualizzatore di tipo e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Viene illustrato cosa sono un visualizzatore di tipi e un visualizzatore personalizzato e il ruolo dell'analizzatore di espressioni nel supporto di entrambi.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali relativi all'architettura di debug.

 [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo del DE all'interno di contesti di valutazione del codice, della documentazione e dell'espressione. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.

## <a name="see-also"></a>Vedere anche
- [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
