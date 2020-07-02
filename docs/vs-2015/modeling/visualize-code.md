---
title: Visualizza codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 665dc76126eac964f405be06605c40b5b30cc9a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532938"
---
# <a name="visualize-code"></a>Visualizzare il codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare gli strumenti di visualizzazione e modellazione di Visual Studio per comprendere più facilmente il codice esistente e descrivere l'applicazione. In questo modo è possibile avere un'indicazione visiva dell'impatto che le modifiche potrebbero avere sul codice e valutare il lavoro e i rischi risultanti da tali modifiche. Ad esempio:

- Per comprendere le relazioni nel codice, eseguire visivamente il mapping di tali relazioni.

- Per descrivere l'architettura del sistema e mantenere il codice coerente con la progettazione, creare diagrammi livello e convalidare codice rispetto a questi diagrammi.

- Per descrivere le strutture delle classi, creare diagrammi classi.

- Per modellare e comunicare i vari aspetti del sistema, creare diagrammi UML (Unified Modeling Language). Ad esempio, è possibile modellare componenti, tipi, interazioni e processi di un sistema.

  Questi strumenti facilitano anche la comunicazione con le persone coinvolte nel progetto. Ad esempio, è possibile usare diagrammi classi UML per creare un glossario comune per discutere il sistema con parti interessate, utenti e membri del team di progetto.

  Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Per saperne di più

|Scenario|Articoli|
|-|-|
|**Analizzare il codice e le relative relazioni:**<br /><br /> Eseguire il mapping delle relazioni tra parti di codice specifiche.<br /><br /> Ottenere una panoramica delle relazioni nel codice per l'intera soluzione.<br /><br /> **Nota**: in questa versione di Visual Studio, il termine *mappa codice* è usato al posto di *grafico dipendenze*.|-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usare le mappe codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Trovare problemi potenziali usando gli analizzatori di mappe codice](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Comprendere le strutture delle classi:**<br /><br /> Visualizzare la struttura delle classi in un progetto mediante la creazione di diagrammi classi dal codice.|[Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Descrivere la progettazione di alto livello del sistema e convalidare il codice rispetto a tale progettazione:**<br /><br /> Descrivere la progettazione di alto livello del sistema e le dipendenze previste mediante la creazione di diagrammi livello. Convalidare il codice rispetto a tale progettazione per garantire che le dipendenze nel codice rimangano coerenti con la progettazione.|-   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)<br />-   [Diagrammi livello: linee guida](../modeling/layer-diagrams-guidelines.md)<br />-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|
|**Comunicare i requisiti utente e l'architettura:**<br /><br /> Modellare i requisiti utente e l'architettura del sistema software creando i diagrammi UML seguenti: di attività, dei componenti, classi, di sequenza e caso di utilizzo.|-   [Creare modelli per l'app](../modeling/create-models-for-your-app.md)<br />-   [Requisiti utente del modello](../modeling/model-user-requirements.md)<br />-   [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|------------------|---------------|
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blog**|[Blog di Visual Studi ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Articoli e pubblicazioni tecniche**|[Forum sull'architettura MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Vedere anche
 [Scenario: modificare la progettazione usando la visualizzazione e la modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [architettura di analisi e modellazione](../modeling/analyze-and-model-your-architecture.md) [creare modelli per i](../modeling/create-models-for-your-app.md) [requisiti degli utenti del modello](../modeling/model-user-requirements.md) di app [modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md) [usare i modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)
