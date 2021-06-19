---
title: Convalidare il sistema durante lo sviluppo
description: Informazioni su Visual Studio per mantenere il software coerente con i requisiti dell'utente e con l'architettura del sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae85c7f98aab3e852a810976cc1cecbd83b65307
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388373"
---
# <a name="validate-your-system-during-development"></a>Convalidare il sistema durante lo sviluppo

Visual Studio possibile mantenere il software coerente con i requisiti utente e con l'architettura del sistema.

Per individuare le versioni di Visual Studio che supportano le singole funzionalità, vedere [Version support for architecture and modeling tools](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="key-tasks"></a>Attività principali

Usare le attività seguenti per convalidare il software:

|**Attività**|**Argomenti correlati**|
|-|-|
|**Verificare che il software soddisfi i requisiti degli utenti**:<br /><br />Usare i requisiti e i modelli architetturali per organizzare i test del sistema e dei relativi componenti. Questa procedura consente di verificare che vengano testati i requisiti importanti per gli utenti e per altre parti interessate e di aggiornare rapidamente i test quando cambiano i requisiti.|- [Sviluppare test da un modello](../modeling/develop-tests-from-a-model.md)|
|**Verificare che il software rimanga coerente con la progettazione desiderata del sistema:**<br /><br />I diagrammi delle dipendenze descrivono le dipendenze tra i componenti dell'applicazione. Durante lo sviluppo, è possibile verificare che le dipendenze effettive nel codice siano conformi alla progettazione desiderata.|- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Risorse esterne

|**Categoria**|**Collegamenti**|
|-|-|
|**Video**|![collegamento al video ](../data-tools/media/playvideo.gif) [Channel 9: Doug Seven: Code Understanding and Systems Design with Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![collegamento al video ](../data-tools/media/playvideo.gif) [Channel 9: Architecting an Application ( Progettazione di un'applicazione)](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application)|
|**Forum**|- [Visual Studio Visualization and Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio estendibilità](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Vedi anche

- [Modellare i requisiti utente](../modeling/model-user-requirements.md)
- [Analizzare e modellare l'architettura](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
