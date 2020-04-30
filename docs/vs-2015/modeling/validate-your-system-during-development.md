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
ms.openlocfilehash: a1beeef572282a642e4a989086ac0fd228409fec
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586274"
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio consente di mantenere la coerenza del software con i requisiti degli utenti e con l'architettura del sistema.

 Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Attività principali
 Usare le attività seguenti per convalidare il software.

|**Attività**|**Argomenti correlati**|
|---------------|---------------------------|
|**Verificare che il modello sia coerente:**<br /><br /> A seconda del modo in cui il progetto usa e interpreta i modelli, può essere utile non consentire alcune combinazioni di elementi. Ad esempio, si possono limitare le classi UML in modo che abbiano sempre nomi conformi con [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. È possibile definire vincoli come questi nelle estensioni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|-   [Convalidare il modello UML](../modeling/validate-your-uml-model.md)<br />-   [Definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)|
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br /> È possibile usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|-   [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br /> I diagrammi livello descrivono le dipendenze desiderate tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|-   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|------------------|---------------|
|**Video**|![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug Seven: comprensione del codice e progettazione del sistema con Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: progettazione di un'applicazione tramite un diagramma livello](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") sulle serie di informazioni su [MSDN: come convalidare il codice con diagrammi livello](https://msdn.microsoft.com/vstudio/gg501755)|
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blog**|-   [Blog di Visual Studi ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Vedi anche
 [Test dell'applicazione](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md) [modellare i requisiti degli utenti](../modeling/model-user-requirements.md) [analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)
