---
title: Convalidare il sistema durante lo sviluppo
description: Scopri in che modo Visual Studio può garantire la coerenza del software con i requisiti degli utenti e con l'architettura del sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a803b2fb7eb7c682e29ae0d17698ef673927d751
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361404"
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo

Con Visual Studio è possibile garantire la coerenza del software con i requisiti degli utenti e con l'architettura del sistema.

Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Attività principali

Per convalidare il software, utilizzare le seguenti attività:

|**Attività**|**Argomenti correlati**|
|-|-|
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br />Usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|- [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br />I diagrammi di dipendenza descrivono le dipendenze desiderate tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|- [Creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|-|-|
|**Video**|![collegamento a video ](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: comprensione del codice e progettazione di sistemi con Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![collegamento a video ](../data-tools/media/playvideo.gif) [Channel 9: progettazione di un'applicazione](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application)|
|**Forum**|- [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Estendibilità di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Vedi anche

- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Analizzare e modellare l'architettura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
