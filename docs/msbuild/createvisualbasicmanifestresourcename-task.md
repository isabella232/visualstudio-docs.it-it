---
title: Attività CreateVisualBasicManifestResourceName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0afa597a11207d4e4cb843356cf36d199b460f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779324"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>Crea attività VisualBasicManifestResourceName
Crea un nome di manifesto nello stile di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] da un nome file con estensione *resx* specifico o da un'altra risorsa.

## <a name="parameters"></a>Parametri
 La tabella seguente descrive i parametri dell'[attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametro | Description |
| - | - |
| `ManifestResourceNames` | Parametro <xref:Microsoft.Build.Framework.ITaskItem> `[]` di output di sola lettura.<br /><br /> Nomi di manifesto risultanti. |
| `ResourceFiles` | Parametro `String` obbligatorio.<br /><br /> Nome del file di risorse da cui creare il nome del manifesto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. |
| `RootNamespace` | Parametro `String` facoltativo.<br /><br /> Spazio dei nomi radice del file di risorse, in genere derivato dal file di progetto. Può essere `null`. |
| `PrependCultureAsDirectory` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il nome delle impostazioni cultura viene aggiunto come nome di directory prima del nome di risorsa di manifesto. Il valore predefinito è `true`. |
| `ResourceFilesWithManifestResourceNames` | Parametro di output di sola lettura `String` facoltativo.<br /><br /> Restituisce il nome del file di risorse che include ora il nome di risorsa di manifesto. |

## <a name="remarks"></a>Osservazioni
 L'[attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina il nome di risorsa di manifesto appropriato da assegnare a un file con estensione *resx* specificato o a un altro file di risorse. L'attività fornisce un nome logico a un file di risorse e quindi lo associa a un parametro di output come metadato.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche
- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)