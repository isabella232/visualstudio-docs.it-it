---
title: Attività ResolveKeySource | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 123c45ed23743335a1c4db2000dd241cb92ce291
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810636"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource (attività)
Determina l'origine delle chiavi con nome sicuro.

## <a name="task-parameters"></a>Parametri dell'attività
 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveKeySource` .

|Parametro|Description|
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

## <a name="remarks"></a>Osservazioni
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)