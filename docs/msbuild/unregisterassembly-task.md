---
title: Attività UnregisterAssembly | Microsoft Docs
description: Informazioni su MSBuild'attività UnregisterAssembly per annullare la registrazione di assembly specificati ai fini dell'interoperabilità COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7111c6628193f1574597e20b00fef63746de3174e24cafa29f4f6cfb930c1cd5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369644"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly (attività)

Annulla la registrazione degli assembly specificati ai fini dell'interoperabilità COM. Esegue operazioni inverse rispetto all'[attività RegisterAssembly](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `UnregisterAssembly` .

|Parametro|Descrizione|
|---------------|-----------------|
|`Assemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly di cui annullare la registrazione.|
|`AssemblyListFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Contiene informazioni sullo stato tra l'attività `RegisterAssembly` e l'attività `UnregisterAssembly`. Questo impedisce all'attività di tentare l'annullamento della registrazione di un assembly che non è riuscita nell'attività `RegisterAssembly`.<br /><br /> Se questo parametro è specificato, i parametri `Assemblies` e `TypeLibFiles` verranno ignorati.|
|`TypeLibFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Annulla la registrazione della libreria dei tipi indicata dall'assembly specificato. **Nota:** questo parametro è necessario solo se il nome dei file della libreria dei tipi non corrisponde a quello dell'assembly.|

## <a name="remarks"></a>Commenti

 Per la corretta esecuzione dell'attività non è necessario che l'assembly sia presente. Se si prova ad annullare la registrazione di un assembly inesistente, l'attività verrà comunque eseguita correttamente e verrà visualizzato un avviso. Questa situazione si verifica perché l'attività ha la funzione di rimuovere la registrazione dell'assembly dal Registro di sistema. Se l'assembly non esiste, non si trova nel Registro di sistema e l'attività viene pertanto eseguita correttamente.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> , che a sua volta eredita dalla classe <xref:System.MarshalByRefObject> . La classe `MarshalByRefObject` offre la stessa funzionalità della classe <xref:Microsoft.Build.Utilities.Task>, ma è possibile crearne un'istanza nel relativo dominio dell'applicazione.

## <a name="example"></a>Esempio

 Nell'esempio seguente l'attività `UnregisterAssembly` viene usata per annullare la registrazione dell'assembly eventualmente presente nel percorso specificato dalle proprietà `OutputPath` e `FileName`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <OutputPath>\Output\</OutputPath>
        <FileName>MyFile.dll</FileName>
    </PropertyGroup>
    <Target Name="UnregisterAssemblies">
        <UnregisterAssembly
            Condition="Exists('$(OutputPath)$(FileName)')"
            Assemblies="$(OutputPath)$(FileName)" />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [RegisterAssembly (attività)](../msbuild/registerassembly-task.md)
- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)