---
title: Classe di base TaskExtension | Microsoft Docs
description: Informazioni sui parametri che la classe di base Microsoft.Build.Tasks.TaskExtension aggiunge alle attività che ereditano da essa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 56bdde67acb9432cb02e89735a137ca3f094d6cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142767"
---
# <a name="taskextension-base-class"></a>Classe di base TaskExtension

Molte attività ereditano dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Questa catena di ereditarietà aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

 Nella tabella seguente vengono descritti i parametri delle classi di base.

|Parametro|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine2> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.<br /><br /> Questa è una proprietà che consente agli autori di attività che ereditano da questa classe di non dovere eseguire il cast da `IBuildEngine` a `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine3> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione fornita dall'host.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parametro <xref:Microsoft.Build.Framework.ITaskHost> facoltativo.<br /><br /> Specifica l'istanza dell'oggetto host (può essere null). Il motore di compilazione imposta questa proprietà se l'IDE host ha associato un oggetto host a questa particolare attività.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Parametro di sola lettura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facoltativo.<br /><br /> Ottiene un oggetto `TaskLoggingHelperExtension` che contiene metodi di registrazione delle attività.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)
