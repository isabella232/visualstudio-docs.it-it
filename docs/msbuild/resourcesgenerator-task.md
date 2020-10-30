---
title: Attività ResourcesGenerator | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività ResourcesGenerator per incorporare una o più risorse in un file con estensione resources.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 288d83cd16b9faebc9c6826a08da7c11811663d5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048483"
---
# <a name="resourcesgenerator-task"></a>Attività ResourcesGenerator

L' <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> attività incorpora una o più risorse ( *jpg* , *ico* , *BMP* , XAML in formato binario e altri tipi di estensione) in un file con estensione *Resources* .

## <a name="task-parameters"></a>Parametri dell'attività

|Parametro|Descrizione|
|---------------|-----------------|
|`OutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso della directory di output. Se il percorso non è assoluto, verrà trattato come percorso relativo alla directory di progetto radice.|
|`OutputResourcesFile`|Parametro di output **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file con *estensione resources* generato. Se il percorso non è assoluto, il file *resources* verrà generato come percorso relativo alla directory di progetto radice.|
|`ResourcesFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica una o più risorse da incorporare nel file con *estensione resources* generato.|

## <a name="example"></a>Esempio

 Nell'esempio seguente viene generato un file con *estensione resources* con una singola risorsa *BMP* . La risorsa *BMP* viene generata in una directory relativa alla directory radice del progetto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)