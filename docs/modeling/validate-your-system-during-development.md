---
title: Convalidare il sistema durante lo sviluppo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dependency diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: "37"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: e05574ba51a690621d57b6f32017d1eb359675eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo
Visual Studio consente di mantenere la coerenza del software con i requisiti degli utenti e con l'architettura del sistema.  
  
 Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Attività principali  
 Usare le attività seguenti per convalidare il software.  
  
|**Attività**|**Argomenti correlati**|  
|---------------|---------------------------|  
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br /> È possibile usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|-   [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|  
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br /> I diagrammi di dipendenza descrivono le dipendenze desiderate tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|-   [Creare diagrammi dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Risorse esterne  
  
|**Categoria**|**Collegamenti**|  
|------------------|---------------|  
|**Video**|![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug sette: codice e la progettazione di sistema con Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: architettura di un'applicazione utilizzando un diagramma di dipendenza](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![collegamento a video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN serie di video procedurali: come convalidare il codice con i diagrammi di dipendenza](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Forum**|-   [Visual Studio Visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization and Modeling SDK (strumenti DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blog**|-   [Blog di Visual Studi ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Articoli e pubblicazioni tecniche**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Vedere anche  
 [Test dell'applicazione](https://www.visualstudio.com/en-gb/docs/test/overview)   
 [Modellare i requisiti utente](../modeling/model-user-requirements.md)   
 [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
