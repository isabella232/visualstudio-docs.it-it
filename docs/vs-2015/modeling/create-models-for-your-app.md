---
title: Creare modelli per l'app | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9f20629c39bc37ca20550c3b88d8ecb2aca470f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300250"
---
# <a name="create-models-for-your-app"></a>Creare modelli per l'app
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I diagrammi di modellazione consentono di comprendere, chiarire e comunicare le idee sul codice e i requisiti dell'utente che devono supportare il sistema software. Ad esempio, per descrivere e comunicare i requisiti utente, è possibile usare caso di utilizzo, attività, classe e diagrammi di sequenza UML (Unified Modeling Language). Per descrivere e comunicare le funzionalità del sistema, è possibile usare il componente, la classe, l'attività e i diagrammi di sequenza UML.

 Vedere [video di Channel 9: migliorare l'architettura tramite la modellazione](https://go.microsoft.com/fwlink/?LinkID=252078).

 In questa versione è possibile creare i diagrammi UML seguenti:

|**Diagramma**|**Mostra**|
|-----------------|---------------|
|[Diagrammi di attività UML: riferimento](../modeling/uml-activity-diagrams-reference.md)|Flusso di lavoro tra azioni e partecipanti in un processo di business|
|[Diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md)|Componenti di un sistema, interfacce, porte e relazioni|
|[Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)|Tipi usati per archiviare e scambiare dati nel sistema e le relative relazioni|
|[Diagrammi di sequenza UML: riferimenti](../modeling/uml-sequence-diagrams-reference.md)|Sequenze di interazioni tra oggetti, componenti, sistemi o attori|
|[Diagrammi casi d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md)|Gli obiettivi utente e le attività che supporta un sistema|

 Per individuare le versioni di Visual Studio che supportano ogni tipo di diagramma, vedere [supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Per visualizzare l'architettura di un sistema o codice esistente, creare i diagrammi seguenti:

|**Diagramma**|**Mostra**|
|-----------------|---------------|
|[Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)|Architettura di alto livello del sistema|
|Mappe codice<br /><br /> [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)|Dipendenze e altre relazioni nel codice esistente|
|Diagrammi classi generati dal codice<br /><br /> [Uso dei diagrammi classi (Progettazione classi)](../ide/working-with-class-diagrams-class-designer.md)|Tipi e relative relazioni nel codice .NET|

## <a name="common-tasks"></a>Attività comuni

|**Argomento**|**Attività**|
|---------------|--------------|
|[Creare diagrammi e progetti di modellazione UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Creare modelli** e aggiungere diagrammi.|
|[Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)|**Creare diagrammi** per modificare il modello.|
|[Definire pacchetti e spazi dei nomi](../modeling/define-packages-and-namespaces.md)|**Creare pacchetti** per dividere un modello in unità su cui possono lavorare diversi membri del team.|
|[Generare codice da diagrammi classi UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Generare C# codice dai diagrammi classi** per avviare l'implementazione.|
|[Personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Personalizzare gli elementi del modello** usando gli stereotipi, per estendere gli elementi del modello UML standard per scopi specifici.|
|[Collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md)|**Creare collegamenti tra elementi del modello ed** elementi di lavoro per tenere traccia di attività, test case, bug, requisiti, problemi o altri tipi di lavoro associati a parti specifiche del modello.|
|[Esportare diagrammi come immagini](../modeling/export-diagrams-as-images.md)|**Salvare il modello e i diagrammi** in modo da poterli condividere con altri utenti, inclusi quelli che non usano [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|

## <a name="related-tasks"></a>Attività correlate

|**Argomento**|**Attività**|
|---------------|--------------|
|[Visualizzare il codice](../modeling/visualize-code.md)|Creare mappe codice e diagrammi livello per meglio comprendere il codice non conosciuto.|
|[Modellare i requisiti utente](../modeling/model-user-requirements.md)|Usare modelli per chiarire e comunicare le esigenze degli utenti.|
|[Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|Usare i modelli per descrivere la struttura complessiva e il comportamento del sistema e per verificare che soddisfi esigenze degli utenti.|
|[Convalidare il sistema durante lo sviluppo](../modeling/validate-your-system-during-development.md)|Verificare che il software continui a essere coerente con le esigenze degli utenti e con l'architettura complessiva del sistema.|
|[Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)<br /><br /> [Usare i modelli nello sviluppo agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Usare i modelli per comprendere e modificare il sistema durante lo sviluppo.|
|[Strutturare la soluzione di modellazione](../modeling/structure-your-modeling-solution.md)|Organizzare i modelli in un progetto di medie o grandi dimensioni.|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Links**|
|------------------|---------------|
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
