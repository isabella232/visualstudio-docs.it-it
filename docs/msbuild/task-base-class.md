---
title: Classe di base Task | Microsoft Docs
description: Informazioni sui parametri aggiunti dalla classe di base Microsoft. Build. Utilities. Task alle attività che ereditano da esso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41557eb7df3da8a6322a3951520918ffb158b57a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047997"
---
# <a name="task-base-class"></a>Classe di base Task

Molte attività ereditano dalla classe <xref:Microsoft.Build.Utilities.Task>. Questa classe aggiunge diversi parametri alle attività che ne derivano. Questi parametri sono elencati in questo documento.

## <a name="parameters"></a>Parametri

 Nella tabella seguente vengono descritti i parametri di questa classe di base.

|Parametro|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine2> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione disponibile per le attività. Il motore di compilazione imposta automaticamente questo parametro per consentire alle attività di richiamarlo.<br /><br /> Questa è una proprietà che consente agli autori di attività che ereditano da questa classe di non dovere eseguire il cast da `IBuildEngine` a `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine3> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione fornita dall'host.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parametro <xref:Microsoft.Build.Framework.ITaskHost> facoltativo.<br /><br /> Specifica l'istanza dell'oggetto host (può essere null). Il motore di compilazione imposta questa proprietà se l'IDE host ha associato un oggetto host a questa particolare attività.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Parametro di sola lettura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facoltativo.<br /><br /> Oggetto helper della registrazione.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)
