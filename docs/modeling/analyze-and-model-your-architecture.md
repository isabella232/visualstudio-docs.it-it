---
title: Analizzare e modellare l'architettura
ms.date: 11/04/2016
ms.topic: conceptual
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0c9bbb0e98fe717e696aa974f4af5ba29de498e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590579"
---
# <a name="analyze-and-model-your-architecture"></a>Analizzare e modellare l'architettura

Assicurarsi che l'app soddisfi i requisiti dell'architettura usando gli strumenti di architettura e modellazione di Visual Studio per progettare e modellare l'app.

* Comprendere più facilmente il codice del programma esistente tramite Visual Studio per visualizzare la struttura, il comportamento e le relazioni del codice.

* Informare il team in merito alla necessità di rispettare le dipendenze dell'architettura.

* Creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo.

Vedere [scenario: modificare la progettazione con la visualizzazione e la modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Riferimento all'articolo

|||
|-|-|
|**Visualizzare il codice**:<br /><br />-Vedere l'organizzazione e le relazioni del codice creando mappe codice. Visualizzare le dipendenze tra assembly, spazi dei nomi, classi, metodi e così via.<br />-Vedere la struttura della classe e i membri per un progetto specifico creando diagrammi classi dal codice.<br />-Individuare i conflitti tra il codice e la relativa progettazione creando diagrammi delle dipendenze per convalidare il codice.|- [Visualizzare il codice](../modeling/visualize-code.md)<br />- [uso di classi e altri tipi (Progettazione classi)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [video: informazioni sulla progettazione dal codice con le mappe codici di Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />[Video - : convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definire l'architettura**:<br /><br />-Definire e applicare vincoli sulle dipendenze tra i componenti del codice creando diagrammi di dipendenza.|[Video - : convalidare le dipendenze dell'architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Convalidare il sistema con i requisiti e la progettazione desiderata**<br /><br />-Convalidare le dipendenze del codice con i diagrammi delle dipendenze che descrivono l'architettura desiderata e impediscono le modifiche che potrebbero essere in conflitto|[Video - : convalidare le dipendenze dell'architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Personalizzare modelli e diagrammi**:<br /><br />-Creare linguaggi specifici per il dominio.|- [Modeling SDK per Visual Studio-linguaggi specifici del dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generare testo usando i modelli T4**:<br /><br />-Usare i blocchi di testo e la logica di controllo all'interno dei modelli per generare file basati su testo.<br /> -Compilazione modello T4 con MSBuild incluso in Visual Studio|- [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Condividere modelli, diagrammi e mappe codice usando il controllo della versione di Team Foundation**:<br /><br />-Inserire mappe del codice, progetti e diagrammi di dipendenza nel controllo della versione di Team Foundation in modo da poterli condividere.| |

Per informazioni sulle edizioni di Visual Studio che supportano ogni funzionalità, vedere [supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Tipi di modelli e usi tipici

### <a name="code-maps"></a>Mappe codici

Le mappe codice consentono di visualizzare l'organizzazione e le relazioni nel codice.

**Usi tipici:**

- Esaminare il codice programma in modo da poterne comprendere meglio la struttura e le relative dipendenze, come aggiornarlo e come stimare il costo delle modifiche proposte.

**Vedere:**

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Diagrammi delle dipendenze

I diagrammi di dipendenza consentono di definire la struttura di un'applicazione come un set di livelli o blocchi con dipendenze esplicite. La convalida in tempo reale Mostra i conflitti tra le dipendenze nel codice e le dipendenze descritte in un diagramma delle dipendenze.

**Usi tipici:**

- Stabilizzare la struttura dell'applicazione apportando diverse modifiche durante il relativo ciclo di vita.
- Prima di archiviare le modifiche apportate al codice, individuare i conflitti di dipendenza non intenzionali.

**Vedere:**

- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Linguaggio specifico di dominio (DSL)

Un linguaggio DSL è una notazione progettata per uno scopo specifico. In Visual Studio, si tratta in genere di un'interfaccia grafica.

**Usi tipici:**

- Generare o configurare parti dell'applicazione. Per sviluppare la notazione e gli strumenti sono necessarie alcune operazioni. Il risultato può essere più adatto al dominio rispetto alla personalizzazione di un modello UML.
- Per progetti di grandi dimensioni o nelle linee di prodotto in cui il ritorno sull'investimento associato allo sviluppo del linguaggio DSL e dei relativi strumenti è dato dall'uso in più progetti.

**Vedere:**

- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Vedere anche

- [Novità relative alla modellazione in Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [Gestione del ciclo di vita di DevOps e delle applicazioni](/azure/devops/user-guide/devops-alm-overview)
