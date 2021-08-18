---
title: Analisi dell'architettura & strumenti di modellazione
description: Progettare e modellare l'app per assicurarsi che l'app soddisfi i requisiti di architettura.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d191318172700a12552341c5bd3c7a2c03e63734
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157605"
---
# <a name="analyze-and-model-your-architecture"></a>Analizzare e modellare l'architettura

Assicurarsi che l'app soddisfi i requisiti di architettura usando Visual Studio e gli strumenti di modellazione per progettare e modellare l'app.

1. Comprendere meglio il codice del programma esistente [visualizzando la struttura,](visualize-code.md) il comportamento e le relazioni del codice con mappe codice e diagrammi delle dipendenze.
    - Vedere l'organizzazione e le relazioni del codice creando mappe **codice.** 
    - Visualizzare le dipendenze tra assembly, spazi dei nomi, classi, metodi e così via.
    - Individuare i conflitti tra il codice e la relativa progettazione creando **diagrammi delle dipendenze per** convalidare il codice.
    - Vedere la struttura e i membri della classe per un progetto specifico [creando diagrammi classi dal codice.](../ide/class-designer/designing-and-viewing-classes-and-types.md)
    - [Generare testo usando modelli T4 con blocchi](../modeling/code-generation-and-t4-text-templates.md) di testo e logica di controllo all'interno dei modelli per generare file basati su testo. 
    
1. Informare il team sulla necessità di rispettare le dipendenze dell'architettura.

1. Creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo.

Vedere [Scenario: Modificare la progettazione usando la visualizzazione e la modellazione.](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)

## <a name="code-maps"></a>Mappe codice

Le mappe codice sono un tipo di modello che consente di visualizzare l'organizzazione e le relazioni nel codice.

Usare le mappe per esaminare il codice del programma in modo da comprenderne meglio la struttura e le dipendenze, come aggiornarlo e stimare il costo delle modifiche proposte.

Altre informazioni:
- [Installare gli strumenti di codice dell'architettura](install-architecture-tools.md)
- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>Diagrammi delle dipendenze

I diagrammi delle dipendenze consentono di definire la struttura di un'applicazione come set di livelli o blocchi con dipendenze esplicite. La convalida in tempo reale mostra i conflitti tra le dipendenze nel codice e le dipendenze descritte in un diagramma delle dipendenze.

Usare i diagrammi delle dipendenze per: 
- Stabilizzare la struttura dell'applicazione apportando diverse modifiche durante il relativo ciclo di vita.
- Prima di archiviare le modifiche apportate al codice, individuare i conflitti di dipendenza non intenzionali.

Altre informazioni:
- [Installare gli strumenti di codice dell'architettura](install-architecture-tools.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>Modelli DSL (Domain-Specific Language)

Un linguaggio DSL è una notazione progettata per uno scopo specifico. In Visual Studio è in genere grafico.

Usare un linguaggio specifico di dominio per: 
- Generare o configurare parti dell'applicazione. Per sviluppare la notazione e gli strumenti sono necessarie alcune operazioni. Il risultato può essere più adatto al dominio rispetto alla personalizzazione di un modello UML.
- Per progetti di grandi dimensioni o nelle linee di prodotto in cui il ritorno sull'investimento associato allo sviluppo del linguaggio DSL e dei relativi strumenti è dato dall'uso in più progetti.

Altre informazioni:
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Supporto dell'edizione per gli strumenti di architettura e modellazione

Visual Studio è disponibile in diverse edizioni. Non tutti questi strumenti offrono supporto per gli strumenti di architettura e modellazione. La tabella seguente illustra la disponibilità di ogni strumento.

|**Funzionalità**|**Enterprise edition**|**Professional edition**|**Community edizione**|
|-|-|-|-|
|**Mappe codice**|Sì|Supporta solo la lettura delle mappe codice, il filtraggio delle mappe codice, l'aggiunta di nuovi nodi generici e la creazione di un nuovo Graph diretto da una selezione.|-|
|**Diagrammi delle dipendenze**|Sì|Supporta solo la lettura dei diagrammi delle dipendenze.|Supporta solo la lettura dei diagrammi delle dipendenze.|
|**Grafici diretti** (diagrammi DGML)|Sì|Sì|Sì|
|**Clonazione del codice**|Sì|-|-|
