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
ms.openlocfilehash: 9fb9810f1c212dfb881f5725676a79c6307b9cfa
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476494"
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo

Visual Studio consente di mantenere la coerenza tra i requisiti dell'utente e con l'architettura del sistema del software.

Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Attività principali

Per convalidare il software, usare le attività seguenti:

|**Attività**|**Argomenti correlati**|
|-|-|
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br />Usare i requisiti e modelli architettonici per consentono di organizzare i test di sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|- [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br />I diagrammi delle dipendenze descrivono le dipendenze previste tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|-|-|
|**Video**|![collegamento al video](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Comprensione del codice e progettazione di sistemi con Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![collegamento al video](../data-tools/media/playvideo.gif) [Channel 9: Progettazione di un'applicazione](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Forum**|- [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Extensibility di Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Vedere anche

- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Analizzare e modellare l'architettura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
