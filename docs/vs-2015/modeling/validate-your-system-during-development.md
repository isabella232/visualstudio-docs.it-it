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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4570b8ed1afdfff2efd36dbc2f80e97cfbceecac
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698066"
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
|**Video**|![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug Seven: Comprensione del codice e progettazione di sistemi con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Progettazione di un'applicazione usando un diagramma livelli](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: Come convalidare il codice con diagrammi livello](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blog**|-   [Blog di Visual Studi ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Vedere anche  
 [Test dell'applicazione](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Modellare i requisiti utente](../modeling/model-user-requirements.md)   
 [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)
