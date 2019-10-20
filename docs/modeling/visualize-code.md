---
title: Visualizzare il codice
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 073a91e9bafca41192a12a20a7c06ff89644085f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663706"
---
# <a name="visualize-code"></a>Visualizzare il codice

È possibile usare gli strumenti di visualizzazione e modellazione di Visual Studio per comprendere più facilmente il codice esistente e descrivere l'applicazione. In questo modo è possibile avere un'indicazione visiva dell'impatto che le modifiche potrebbero avere sul codice e valutare il lavoro e i rischi risultanti da tali modifiche. Esempio:

- Per comprendere le relazioni nel codice, eseguire visivamente il mapping di tali relazioni.

- Per descrivere l'architettura del sistema e assicurare la coerenza del codice con la progettazione, creare diagrammi di dipendenza e convalidare il codice rispetto a questi diagrammi.

- Per descrivere le strutture delle classi, creare diagrammi classi.

Questi strumenti facilitano anche la comunicazione con le persone coinvolte nel progetto.

Per informazioni sulle edizioni di Visual Studio che supportano ogni funzionalità, vedere [supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Selezionare l'operazione da eseguire.

|||
|-|-|
|**Comprendere il codice e le relative relazioni:**<br /><br /> Eseguire il mapping delle relazioni tra parti di codice specifiche.<br /><br /> Ottenere una panoramica delle relazioni nel codice per l'intera soluzione.|- [mappare le dipendenze tra le soluzioni](../modeling/map-dependencies-across-your-solutions.md)<br />- [usare le mappe codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [individuare problemi potenziali usando gli analizzatori della mappa del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Informazioni sulle strutture delle classi:**<br /><br /> Visualizzare la struttura delle classi in un progetto mediante la creazione di diagrammi classi dal codice.|[Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Descrivere la progettazione di alto livello del sistema e convalidare il codice rispetto a questa progettazione:**<br /><br /> Descrivere la progettazione di alto livello del sistema e le dipendenze desiderate creando diagrammi di dipendenza. Convalidare il codice rispetto a tale progettazione per garantire che le dipendenze nel codice rimangano coerenti con la progettazione.|- [creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [diagrammi delle dipendenze: riferimento](../modeling/layer-diagrams-reference.md)<br />- [diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)<br />- [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Vedere anche

- [Scenario: modificare la progettazione mediante gli strumenti di visualizzazione e modellazione](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizzare e modellare l'architettura](../modeling/analyze-and-model-your-architecture.md)
- [Modellare l'architettura dell'app](../modeling/model-your-app-s-architecture.md)
- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
