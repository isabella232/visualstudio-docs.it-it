---
title: Componenti del debugger | Microsoft Docs
description: Informazioni sugli elementi che costituiscono una sessione di debug, gestita dal debugger Visual Studio, implementata come VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 8c246bc00ee4f6fcead8404b3174da39f7b5ca2d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903983"
---
# <a name="debugger-components"></a>Componenti del debugger
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger viene implementato come vspackage e gestisce l'intera sessione di debug. La sessione di debug include gli elementi seguenti:

- **Pacchetto di debug:** Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger fornisce la stessa interfaccia utente indipendentemente da ciò che si sta debugndo.

- **Gestione debug sessione (SDM):** Fornisce un'interfaccia programmatica coerente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger per la gestione di un'ampia gamma di motori di debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Process Debug Manager (PDM):** Gestisce, per tutte le istanze in esecuzione di , un elenco di tutti i programmi che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono essere o di cui è in corso il debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Motore di debug (DE):** È responsabile del monitoraggio di un programma in fase di debug, della comunicazione dello stato del programma in esecuzione con SDM e PDM e dell'interazione con l'analizzatore di espressioni e il provider di simboli per fornire l'analisi in tempo reale dello stato della memoria e delle variabili di un programma. Viene implementato da (per i linguaggi supportati) e da fornitori di terze parti che vogliono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supportare la propria fase di esecuzione.

- **Analizzatore di espressioni (EE):** Fornisce il supporto per la valutazione dinamica di variabili ed espressioni fornite dall'utente quando un programma è stato arrestato in un determinato punto. Viene implementato da (per le lingue supportate) e da fornitori di terze parti che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vogliono supportare le proprie lingue.

- **Provider di simboli (SP):** Chiamato anche gestore di simboli, esegue il mapping dei simboli di debug di un programma a un'istanza in esecuzione del programma in modo che sia possibile fornire informazioni significative, ad esempio il debug a livello di codice sorgente e la valutazione delle espressioni. Viene implementato da (per i simboli Common Language Runtime [CLR] e il formato di file di simboli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program DataBase [PDB]) e da fornitori di terze parti che hanno un proprio metodo proprietario di archiviazione delle informazioni di debug.

  Il diagramma seguente illustra la relazione tra questi elementi del debugger Visual Studio.

  ![Cenni preliminari sul debug dei componenti](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Contenuto della sezione
 [Pacchetto di debug](../../extensibility/debugger/debug-package.md) Viene illustrato il pacchetto di debug, che viene eseguito nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell e gestisce tutta l'interfaccia utente.

 [Gestione debug processi](../../extensibility/debugger/process-debug-manager.md) Fornisce una panoramica delle funzionalità di PDM, ovvero la gestione dei processi di cui è possibile eseguire il debug.

 [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md) Definisce SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. SDM gestisce de.

 [Motore di debug](../../extensibility/debugger/debug-engine.md) Documenta i servizi di debug forniti da DE.

 [Modalità operative](../../extensibility/debugger/operational-modes.md) Viene fornita una panoramica delle tre modalità in cui l'IDE può operare: modalità di progettazione, modalità di esecuzione e modalità di interruzione. Vengono illustrati anche i meccanismi di transizione.

 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) Viene illustrato lo scopo di EE in fase di esecuzione.

 [Provider di simboli](../../extensibility/debugger/symbol-provider.md) Viene illustrato come, in fase di implementazione, il provider di simboli valuta variabili ed espressioni.

 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Descrive che cosa sono un visualizzatore di tipi e un visualizzatore personalizzato e il ruolo dell'analizzatore di espressioni nel supporto di entrambi.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali dell'architettura di debug.

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo di DE all'interno di contesti di codice, documentazione e valutazione delle espressioni. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.

## <a name="see-also"></a>Vedere anche
- [Operazioni preliminari](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
