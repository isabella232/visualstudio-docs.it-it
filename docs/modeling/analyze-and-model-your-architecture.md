---
title: Analizzare e modellare l'architettura
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ddf7e7bf78baede7e964aeeed7484261fdab2ef7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924466"
---
# <a name="analyze-and-model-your-architecture"></a>Analizzare e modellare l'architettura

Assicurarsi che l'app soddisfi i requisiti dell'architettura usando l'architettura di Visual Studio e strumenti per progettare e modellare l'applicazione di modellazione.

* Comprendere più facilmente il codice del programma esistente tramite Visual Studio per visualizzare la struttura, il comportamento e le relazioni del codice.

* È necessario informare il team la necessità di il rispettando le dipendenze dell'architettura.

* Creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo.

Vedere [Scenario: Modificare la progettazione mediante visualizzazione e modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>A

|||
|-|-|
|**Visualizzare il codice**:<br /><br /> -Vedere organizzazione e le relazioni nel codice creando mappe codici. Visualizzare le dipendenze tra assembly, spazi dei nomi, classi, metodi e così via.<br />-Vedere la struttura di classi e membri per un progetto specifico tramite la creazione di diagrammi classi dal codice.<br />-Trovare conflitti tra il codice e la progettazione creando diagrammi delle dipendenze per convalidare il codice.|-   [Visualizzare il codice](../modeling/visualize-code.md)<br />-   [Uso di classi e altri tipi (Progettazione classi)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />-   [Video: Comprendere la progettazione dal codice con le mappe codice di Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Video: Convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definire l'architettura**:<br /><br /> : Consente di definire e applicare vincoli sulle dipendenze tra i componenti del codice creando diagrammi delle dipendenze.|-   [Video: Convalidare le dipendenze dell'architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Convalidare il sistema con i requisiti e la progettazione desiderata**<br /><br /> -Verificare le dipendenze del codice con diagrammi delle dipendenze che descrivono l'architettura desiderata e impedire le modifiche che potrebbe essere in conflitto con la progettazione.|-   [Video: Convalidare le dipendenze dell'architettura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Personalizzare modelli e diagrammi**:<br /><br /> -Creare i proprio domain-specific Language.|-   [Modeling SDK per Visual Studio - Domain-Specific Language](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generare testo usando i modelli T4**:<br /><br /> -Usare blocchi di testo e la logica di controllo all'interno dei modelli per generare file basati su testo.<br /> -Compilazione di modelli T4 con MSBuild incluso in Visual Studio|-   [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Condividere modelli, diagrammi e mappe codice usando il controllo della versione di Team Foundation**:<br /><br /> -Inserire le mappe codice, progetti e diagrammi delle dipendenze nel controllo della versione di Team Foundation in modo da poterli condividere.| |

Per informazioni su quali edizioni di Visual Studio supportano le singole funzionalità, vedere [supporto Edition per architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Tipi di modelli e usi tipici

### <a name="code-maps"></a>Mappe codice
Le mappe codice consentono di visualizzare l'organizzazione e le relazioni nel codice.

**Usi tipici:**

-   Esaminare il codice programma in modo da poterne comprendere meglio la struttura e le relative dipendenze, come aggiornarlo e come stimare il costo delle modifiche proposte.

**Vedere:**

-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
-   [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>Diagramma delle dipendenze
I diagrammi delle dipendenze consentono di definire la struttura di un'applicazione come un set di livelli o blocchi con dipendenze esplicite. È possibile eseguire la convalida per individuare i conflitti tra dipendenze nel codice e le dipendenze descritte in un diagramma delle dipendenze.

**Usi tipici:**

-   Stabilizzare la struttura dell'applicazione apportando diverse modifiche durante il relativo ciclo di vita.
-   Prima di archiviare le modifiche apportate al codice, individuare i conflitti di dipendenza non intenzionali.

**Vedere:**

-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
-   [Diagrammi delle dipendenze: Riferimento](../modeling/layer-diagrams-reference.md)
-   [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Linguaggio specifico di dominio (DSL)
Un linguaggio DSL è una notazione progettata per uno scopo specifico. In Visual Studio, è generalmente grafico.

**Usi tipici:**

-   Generare o configurare parti dell'applicazione. Per sviluppare la notazione e gli strumenti sono necessarie alcune operazioni. Il risultato può essere più appropriato per il dominio rispetto alla personalizzazione di un modello UML.
-   Per progetti di grandi dimensioni o nelle linee di prodotto in cui il ritorno sull'investimento associato allo sviluppo del linguaggio DSL e dei relativi strumenti è dato dall'uso in più progetti.

**Vedere:**

-   [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>Dove è possibile ottenere altre informazioni?

[Visual Studio Visualization and Modeling Tools Forum](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Vedere anche

- [Novità](../modeling/what-s-new-for-design-in-visual-studio.md)
- [Gestione del ciclo di vita di DevOps e delle applicazioni](/azure/devops/user-guide/devops-alm-overview)
