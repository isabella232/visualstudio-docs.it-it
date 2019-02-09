---
title: Convalidare il sistema durante lo sviluppo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98cde01932d2e0d73fdae1dad0ef4e5b3e659f34
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970374"
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo
Visual Studio consente di mantenere la coerenza del software con i requisiti degli utenti e con l'architettura del sistema.

 Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Attività principali
 Usare le attività seguenti per convalidare il software.

|**Attività**|**Argomenti correlati**|
|-|-|
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br /> È possibile usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|-   [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br /> I diagrammi delle dipendenze descrivono le dipendenze previste tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|-|-|
|**Video**|![collegamento al video](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Comprensione del codice e progettazione di sistemi con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![collegamento al video](../data-tools/media/playvideo.gif) [Channel 9: Progettazione di un'applicazione usando un diagramma delle dipendenze](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![collegamento al video](../data-tools/media/playvideo.gif) [MSDN How Do I Series: Come convalidare il codice usando i diagrammi delle dipendenze](http://go.microsoft.com/fwlink/?LinkID=214405)|
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blog**|-   [Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)|
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Vedere anche

- [Test dell'applicazione](/azure/devops/test/overview?view=vsts)
- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
