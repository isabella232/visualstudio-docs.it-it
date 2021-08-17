---
title: Attività FileClassifier | Microsoft Docs
description: Usare l MSBuild'attività FileClassifier per classificare un set di risorse di origine che verranno incorporate in un assembly.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: df4d07364f0f1b707ed4f4f95aca9a90de484f0da40eab9a369fc28cde398090
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428068"
---
# <a name="fileclassifier-task"></a>Attività FileClassifier

L'attività <xref:Microsoft.Build.Tasks.Windows.FileClassifier> classifica un insieme di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.

## <a name="task-parameters"></a>Parametri dell'attività

|Parametro|Descrizione|
|---------------|-----------------|
|`CLREmbeddedResource`|Non utilizzato.|
|`CLRResourceFiles`|Non utilizzato.|
|`CLRSatelliteEmbeddedResource`|Non utilizzato.|
|`Culture`|Parametro **String** facoltativo.<br /><br /> Specifica le impostazioni cultura per la compilazione. Questo valore può essere **null** se la compilazione non è localizzabile. Se **null**, il valore predefinito corrisponde al valore minuscolo restituito da **CultureInfo.InvariantCulture**.|
|`MainEmbeddedFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Specifica le risorse non localizzabili incorporate nell'assembly principale.|
|`OutputType`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di file in cui incorporare i file di origine specificati. I valori validi sono **exe**, **winexe** e **library**.|
|`SatelliteEmbeddedFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Specifica i file localizzabili incorporati nell'assembly satellite per le impostazioni cultura specificate dal parametro **Culture**.|
|`SourceFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica l'elenco di file da classificare.|

## <a name="remarks"></a>Commenti

Se il parametro **Culture** non è impostato, tutte le risorse specificate usando il parametro **SourceFiles** non sono localizzabili. In caso contrario, sono localizzabili a meno che non vengano associate a un attributo **Localizable** impostato su **false**.

## <a name="example"></a>Esempio

Nell'esempio seguente un singolo file di origine viene classificato come risorsa e incorporato in un assembly satellite per le impostazioni cultura Francese-Canadese (fr-CA).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <ItemGroup>
    <Resource Include="Resource1.bmp" />
  </ItemGroup>
  <Target Name="FileClassifierTask">
    <FileClassifier
      SourceFiles="Resource1.bmp"
      Culture="fr-CA"
      OutputType="exe" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
