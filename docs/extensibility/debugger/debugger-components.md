---
title: Componenti del debugger | Microsoft Docs
description: Informazioni sugli elementi che costituiscono una sessione di debug, gestita dal debugger di Visual Studio, implementata come VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7c558d20d24acd65ece4c4df43eb8f474c20447
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094952"
---
# <a name="debugger-components"></a>Componenti del debugger
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger viene implementato come pacchetto VSPackage e gestisce l'intera sessione di debug. La sessione di debug include gli elementi seguenti:

- **Pacchetto di debug:** Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger fornisce la stessa interfaccia utente indipendentemente dall'oggetto di cui è in corso il debug.

- **Gestione debug sessione (SDM):** Fornisce un'interfaccia a livello di codice coerente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger per la gestione di un'ampia gamma di motori di debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Gestione debug processo (PDM):** Gestisce, per tutte le istanze in esecuzione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , un elenco di tutti i programmi che possono essere o di cui è in corso il debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Motore di debug (de):** È responsabile del monitoraggio di un programma di cui è in corso il debug, della comunicazione dello stato del programma in esecuzione con SDM e del PDM e dell'interazione con l'analizzatore di espressioni e il provider di simboli per fornire l'analisi in tempo reale dello stato della memoria e delle variabili di un programma. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per le lingue supportate) e da fornitori di terze parti che desiderano supportare il proprio tempo di esecuzione.

- **Analizzatore di espressioni (EE):** Fornisce supporto per la valutazione dinamica di variabili ed espressioni fornite dall'utente quando un programma è stato interrotto in un determinato punto. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per le lingue supportate) e da fornitori di terze parti che desiderano supportare le proprie lingue.

- **Provider di simboli (SP):** Detto anche gestore di simboli, esegue il mapping dei simboli di debug di un programma a un'istanza in esecuzione del programma in modo che possano essere fornite informazioni significative, ad esempio il debug a livello di codice sorgente e la valutazione dell'espressione. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per i simboli Common Language Runtime [CLR] e il formato di file di simboli del database di programma [PDB]) e da fornitori di terze parti che hanno un metodo proprietario per archiviare le informazioni di debug.

  Il diagramma seguente illustra la relazione tra questi elementi del debugger di Visual Studio.

  ![Panoramica dei componenti di debug](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Contenuto della sezione
 [Debug del pacchetto](../../extensibility/debugger/debug-package.md) Viene illustrato il pacchetto di debug, che viene eseguito nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell e gestisce tutte le interfacce utente.

 [Gestione debug processo](../../extensibility/debugger/process-debug-manager.md) Viene fornita una panoramica delle funzionalità di PDM, ovvero la gestione dei processi di cui è possibile eseguire il debug.

 [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md) Definisce SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. SDM gestisce il DE.

 [Motore di debug](../../extensibility/debugger/debug-engine.md) Documenta i servizi di debug forniti da.

 [Modalità operative](../../extensibility/debugger/operational-modes.md) Viene fornita una panoramica delle tre modalità di funzionamento dell'IDE: modalità di progettazione, modalità di esecuzione e modalità di interruzioni. Vengono inoltre illustrati i meccanismi di transizione.

 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) Viene illustrato lo scopo di EE in fase di esecuzione.

 [Provider di simboli](../../extensibility/debugger/symbol-provider.md) Viene illustrato come, in fase di implementazione, il provider di simboli valuta le variabili e le espressioni.

 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Vengono illustrati un visualizzatore di tipi e un visualizzatore personalizzato e il ruolo che l'analizzatore di espressioni svolge per supportare entrambi.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i principali concetti dell'architettura di debug.

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Spiega in che modo il DE opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.

## <a name="see-also"></a>Vedi anche
- [Operazioni preliminari](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
