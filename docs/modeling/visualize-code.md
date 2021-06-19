---
title: Visualizzare il codice
description: Informazioni su come usare gli strumenti di visualizzazione e modellazione in Visual Studio per comprendere il codice esistente e descrivere l'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90c180bf9d910227013c2e089001ce5332cd1bd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388347"
---
# <a name="visualize-code"></a>Visualizzare il codice

È possibile usare gli strumenti di visualizzazione e modellazione di Visual Studio per comprendere più facilmente il codice esistente e descrivere l'applicazione. In questo modo è possibile avere un'indicazione visiva dell'impatto che le modifiche potrebbero avere sul codice e valutare il lavoro e i rischi risultanti da tali modifiche. Ad esempio:

- Per comprendere le relazioni nel codice, eseguire visivamente il mapping di tali relazioni.

- Per descrivere l'architettura del sistema e mantenere il codice coerente con la progettazione, creare diagrammi delle dipendenze e convalidare il codice in base a questi diagrammi.

- Per descrivere le strutture delle classi, creare diagrammi classi.

Questi strumenti facilitano anche la comunicazione con le persone coinvolte nel progetto.

Per vedere quali edizioni di Visual Studio supportano ogni funzionalità, vedere Supporto [dell'edizione](../modeling/analyze-and-model-your-architecture.md#VersionSupport) per gli strumenti di architettura e modellazione

## <a name="what-do-you-want-to-do"></a>Per saperne di più

|Scenario|Articoli|
|-|-|
|**Analizzare il codice e le relative relazioni:**<br /><br /> Eseguire il mapping delle relazioni tra parti di codice specifiche.<br /><br /> Ottenere una panoramica delle relazioni nel codice per l'intera soluzione.|- [Eseguire il mapping delle dipendenze tra le soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />- [Usare le mappe codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Individuare potenziali problemi con gli analizzatori della mappa codice](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Eseguire il mapping dei metodi nello stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Comprendere le strutture delle classi:**<br /><br /> Visualizzare la struttura delle classi in un progetto mediante la creazione di diagrammi classi dal codice.|[Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Descrivere la progettazione di alto livello del sistema e convalidare il codice rispetto a tale progettazione:**<br /><br /> Descrivere la progettazione di alto livello del sistema e le relative dipendenze tramite la creazione di diagrammi delle dipendenze. Convalidare il codice rispetto a tale progettazione per garantire che le dipendenze nel codice rimangano coerenti con la progettazione.|- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagrammi delle dipendenze: informazioni di riferimento](../modeling/layer-diagrams-reference.md)<br />- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)<br />- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Vedi anche

- [Installare gli strumenti di codice dell'architettura](install-architecture-tools.md)
- [Scenario: modificare la progettazione mediante gli strumenti di visualizzazione e modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizzare e modellare l'architettura](../modeling/analyze-and-model-your-architecture.md)
- [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)
- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
