---
title: Attività CreateVisualBasicManifestResourceName | Microsoft Docs
description: Usare l MSBuild'attività CreateVisualBasicManifestResourceName per creare un nome di manifesto di tipo Visual Basic da un nome di file resx specificato o da un'altra risorsa.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e9611741e03d58ca1550af81e026f74a6ec87a04
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054821"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>Crea attività VisualBasicManifestResourceName

Crea un Visual Basic di manifesto di tipo diverso da un nome di file *resx* specificato o da un'altra risorsa.

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri [dell'attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametro | Descrizione |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`Parametro di sola lettura di output.<br /><br /> Nomi di manifesto risultanti. |
| `ResourceFiles` | Parametro `String` obbligatorio.<br /><br /> Nome del file di risorse da cui creare il nome di manifesto Visual Basic. |
| `RootNamespace` | Parametro `String` facoltativo.<br /><br /> Spazio dei nomi radice del file di risorse, in genere derivato dal file di progetto. Può essere `null`. |
| `PrependCultureAsDirectory` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il nome delle impostazioni cultura viene aggiunto come nome di directory prima del nome di risorsa di manifesto. Il valore predefinito è `true`. |
| `ResourceFilesWithManifestResourceNames` | Parametro di output di sola lettura `String` facoltativo.<br /><br /> Restituisce il nome del file di risorse che include ora il nome di risorsa di manifesto. |

## <a name="remarks"></a>Commenti

 [L'attività CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina il nome della risorsa di manifesto appropriato da assegnare a un determinato file *resx* o a un altro file di risorse. L'attività fornisce un nome logico a un file di risorse e quindi lo associa a un parametro di output come metadato.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
