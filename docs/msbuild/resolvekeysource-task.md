---
title: Attività ResolveKeySource | Microsoft Docs
description: Informazioni sui parametri dell'attività ResolveKeySource MSBuild, che determina l'origine della chiave con nome sicuro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 897e4482d45c5f191df8e60b091782bce467e1ba10d6d2c595856d77ad8d470e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427587"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource (attività)

Determina l'origine delle chiavi con nome sicuro.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveKeySource` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Parametro `Int32` facoltativo.<br /><br /> Ottiene o imposta la quantità di tempo in secondi durante i quali visualizzare il messaggio del conto alla rovescia.|
|`AutoClosePasswordPromptTimeout`|Parametro `Int32` facoltativo.<br /><br /> Ottiene o imposta la quantità di tempo di attesa, in secondi, prima di chiudere la finestra di dialogo di richiesta della password.|
|`CertificateFile`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta il percorso del file di certificato.|
|`CertificateThumbprint`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta l'identificazione personale del certificato.|
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta il percorso del file della chiave.|
|`ResolvedKeyContainer`|Parametro di ouput facoltativo `String`.<br /><br /> Ottiene o imposta il contenitore di chiavi risolte.|
|`ResolvedKeyFile`|Parametro di ouput facoltativo `String`.<br /><br /> Ottiene o imposta il file di chiave risolto.|
|`ResolvedThumbprint`|Parametro di ouput facoltativo `String`.<br /><br /> Ottiene o imposta l'identificazione personale del certificato risolta.|
|`ShowImportDialogDespitePreviousFailures`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, visualizza la finestra di dialogo di importazione indipendentemente dagli errori precedenti.|
|`SuppressAutoClosePasswordPrompt`|Parametro `Boolean` facoltativo.<br /><br /> Ottiene o imposta un valore booleano che specifica se la finestra di dialogo di richiesta della password non dovrebbe chiudersi automaticamente.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
