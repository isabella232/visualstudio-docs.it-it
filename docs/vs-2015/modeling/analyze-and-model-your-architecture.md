---
title: Analizzare e modellare l'architettura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e00735a180ec951a8afced0f5c74f7a9466e50b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534095"
---
# <a name="analyze-and-model-your-architecture"></a>Analizzare e modellare l'architettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Assicurarsi che l'app soddisfi i requisiti usando gli strumenti di architettura e modellazione di Visual Studio per progettare e modellare l'applicazione. Comprendere più facilmente il codice del programma esistente tramite Visual Studio per visualizzare la struttura, il comportamento e le relazioni del codice.

 Creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo. Tenere traccia di requisiti, attività, test case, bug e altre operazioni associate ai modelli collegando gli elementi del modello agli elementi di lavoro di Team Foundation Server e al piano di sviluppo. Vedere [scenario: modificare la progettazione con la visualizzazione e la modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="to"></a>Per

|Scenario|Articoli|
|-|-|
|**Visualizza codice**:<br /><br /> -Vedere l'organizzazione e le relazioni del codice creando mappe codice. Visualizzare le dipendenze tra assembly, spazi dei nomi, classi, metodi e così via.<br />-Vedere la struttura della classe e i membri per un progetto specifico creando diagrammi classi dal codice.<br />-Individuare i conflitti tra il codice e la relativa progettazione creando diagrammi livello per convalidare il codice.<br /><br /> **Nota**: in questa versione di Visual Studio, il termine *mappa codice* è usato al posto di *grafico dipendenze*. Il termine *grafico* , quando viene usato da solo, fa riferimento in genere a un grafico orientato o a un diagramma (o documento) DGML. Le mappe codice rappresentano un tipo specializzato di diagramma DGML.|-   [Visualizza codice](../modeling/visualize-code.md)<br />-   [Uso di classi e altri tipi (Progettazione classi)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: comprendere le dipendenze del codice tramite la visualizzazione (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)<br />-   [Video: visualizzare l'effetto di una modifica (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)|
|**Descrivere e comunicare i requisiti dell'utente**:<br /><br /> -Chiarire le storie utente, le regole di business e altri requisiti e garantirne la coerenza creando diagrammi UML come casi d'uso, attività e diagrammi classi.|-   [Creare modelli per l'app](../modeling/create-models-for-your-app.md)<br />-   [Requisiti utente del modello](../modeling/model-user-requirements.md)<br />-   [Video: migliorare l'architettura tramite la modellazione (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)|
|**Definire l'architettura**:<br /><br /> : Modellare la struttura su larga scala del sistema software e i modelli di progettazione mediante la creazione di diagrammi di sequenza, componente, classe e componente UML.<br />-Definire e applicare vincoli sulle dipendenze tra i componenti del codice tramite la creazione di diagrammi livello.|-   [Creare modelli per l'app](../modeling/create-models-for-your-app.md)<br />-   [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)<br />-   [Video: migliorare l'architettura tramite la modellazione (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)<br />-   [Video: usare i diagrammi livello per progettare e convalidare l'architettura (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Convalidare il sistema con i requisiti e la progettazione desiderata**<br /><br /> -Definire i test di accettazione o i test di sistema in base ai modelli di requisiti. Questo crea una forte relazione tra i test e i requisiti degli utenti e consente di aggiornare il sistema più facilmente quando cambiano i requisiti.<br />-Convalidare le dipendenze del codice con i diagrammi livello che descrivono l'architettura desiderata ed evitare modifiche che potrebbero essere in conflitto con la progettazione.|-   [Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)<br />-   [Video: usare i diagrammi livello per progettare e convalidare l'architettura (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Condividere modelli, diagrammi e mappe codice usando il controllo della versione di Team Foundation**:<br /><br /> -Inserire le mappe del codice, i progetti di modellazione, i diagrammi UML e i diagrammi livello nel controllo della versione di Team Foundation in modo da poterli condividere.|Se sono presenti più utenti che usano questi elementi nel controllo della versione di Team Foundation, attenersi a queste linee guida per evitare problemi di controllo della versione:<br /><br /> -   [Gestire modelli e diagrammi nel controllo della versione](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generare o configurare parti dell'applicazione da linguaggi UML o specifici di dominio**:<br /><br /> -Rendere la progettazione più reattiva alle modifiche dei requisiti e facilmente variabile in una linea di prodotti.|-   [Generare e configurare l'app da modelli](../modeling/generate-and-configure-your-app-from-models.md)|
|**Personalizzare modelli e diagrammi**:<br /><br /> -Adattare i modelli al modo in cui vengono usati dal progetto definendo proprietà aggiuntive per gli elementi UML, vincoli di convalida per assicurarsi che i modelli siano conformi alle regole business e comandi di menu aggiuntivi e elementi della casella degli strumenti.<br />-Creare linguaggi specifici per il dominio.|-   [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [SDK di modellazione per Visual Studio-linguaggi specifici del dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generare testo usando i modelli T4**:<br /><br /> -Usare i blocchi di testo e la logica di controllo all'interno dei modelli per generare file basati su testo.|-   [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Tipo di modelli e relativi usi

|**Tipo di modello e usi tipici**|
|-------------------------------------|
|**Mappe codice**<br /><br /> Le mappe codice consentono di visualizzare l'organizzazione e le relazioni nel codice.<br /><br /> Usi tipici:<br /><br /> -Esaminare il codice del programma per comprendere meglio la struttura e le relative dipendenze, come aggiornarla e stimare il costo delle modifiche proposte.<br /><br /> Vedere:<br /><br /> -   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usare le mappe codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Trovare problemi potenziali usando gli analizzatori di mappe codice](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagramma livello**<br /><br /> I diagrammi livello consentono di definire la struttura di un'applicazione come un set di livelli o blocchi con dipendenze esplicite. È possibile eseguire la convalida per trovare conflitti tra le dipendenze nel codice e le dipendenze descritte in un diagramma livello.<br /><br /> Usi tipici:<br /><br /> -Stabilizzare la struttura dell'applicazione attraverso numerose modifiche al suo ciclo di vita.<br />-Individuare i conflitti di dipendenza non intenzionali prima di archiviare le modifiche al codice.<br /><br /> Vedere:<br /><br /> -   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|
|**modello UML**<br /><br /> Un modello UML include varie visualizzazioni, tra cui diagrammi di classi, componenti, casi d'uso e sequenza. È possibile personalizzare un modello UML per adattarlo al dominio dell'applicazione. Ad esempio, è possibile associare tag, informazioni aggiuntive e vincoli agli elementi del modello. È anche possibile definire gli strumenti che operano sui modelli. Vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md).<br /><br /> Usi tipici:<br /><br /> -Descrivere i requisiti e la progettazione. È possibile applicare rapidamente il modello UML allo sviluppo di qualsiasi applicazione. Vedere [usare i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md).<br />-Generare o configurare test o parti di un'applicazione. Sono necessarie alcune operazioni per personalizzare la notazione e sviluppare i modelli di generazione o l'applicazione configurabile. Vedere [generare e configurare l'app da modelli](../modeling/generate-and-configure-your-app-from-models.md).<br />-Per la descrizione generale e per la generazione o la configurazione di codice in progetti più piccoli.|
|**Linguaggio specifico di dominio (DSL)**<br /><br /> Un linguaggio DSL è una notazione progettata per uno scopo specifico. In Visual Studio, è generalmente grafico.<br /><br /> Usi tipici:<br /><br /> -Generare o configurare parti dell'applicazione. Per sviluppare la notazione e gli strumenti sono necessarie alcune operazioni. Il risultato può essere più adatto al dominio rispetto alla personalizzazione di un modello UML.<br />-Per i progetti di grandi dimensioni o per le linee di prodotti in cui l'investimento per lo sviluppo del linguaggio DSL e dei relativi strumenti viene restituito dal relativo utilizzo in più di un progetto.<br /><br /> Vedere:<br /><br /> -   [SDK di modellazione per Visual Studio-linguaggi specifici del dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Dove è possibile ottenere ulteriori informazioni?

|Risorsa|Collegamenti|
|-|-|
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Vedere anche

- [Novità relative alla modellazione in Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [Gestione del ciclo di vita di DevOps e delle applicazioni](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
