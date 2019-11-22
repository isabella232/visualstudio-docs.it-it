---
title: Convalidare il sistema durante lo sviluppo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301345"
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio consente di mantenere la coerenza del software con i requisiti degli utenti e con l'architettura del sistema.

 Per informazioni sulle versioni di Visual Studio che supportano ciascuna di queste funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Attività principali
 Usare le attività seguenti per convalidare il software.

|**Attività**|**Argomenti correlati**|
|---------------|---------------------------|
|**Verificare che il modello sia coerente:**<br /><br /> A seconda del modo in cui il progetto usa e interpreta i modelli, può essere utile non consentire alcune combinazioni di elementi. Ad esempio, si possono limitare le classi UML in modo che abbiano sempre nomi conformi con [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. È possibile definire vincoli come questi nelle estensioni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [convalidare il modello UML](../modeling/validate-your-uml-model.md)<br />-   [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)|
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br /> È possibile usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|-   [sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br /> I diagrammi livello descrivono le dipendenze desiderate tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|-   [creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Risorse esterne

|**Category**|**Links**|
|------------------|---------------|
|**Videos**|![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug Seven: comprensione del codice e progettazione del sistema con Visual Studio 2010](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: progettazione di un'applicazione tramite un diagramma livello](https://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") sulle serie di informazioni su [MSDN: come convalidare il codice con diagrammi livello](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**Forums**|-   [Visual Studio Visualization and Modeling Tools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blog**|-   [Blog di Visual Studi ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Vedere anche
 [Test dell'applicazione](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md) [modellare i requisiti degli utenti](../modeling/model-user-requirements.md) [analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)
