---
title: Attività ResourcesGenerator | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63ee00754683156dad2bd34a93ff43f820eb37c7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518375"
---
# <a name="resourcesgenerator-task"></a>Attività ResourcesGenerator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività ResourcesGenerator](https://docs.microsoft.com/visualstudio/msbuild/resourcesgenerator-task).  
  
  
L'attività <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incorpora una o più risorse (jpg, ico, bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] in formato binario e altri tipi di estensione) in un file con estensione resources.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`OutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso della directory di output. Se il percorso non è assoluto, verrà trattato come percorso relativo alla directory di progetto radice.|  
|`OutputResourcesFile`|Parametro di output **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file con estensione resources generato. Se il percorso non è assoluto, verrà trattato come percorso relativo alla directory di progetto radice.|  
|`ResourcesFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica una o più risorse da incorporare in un file con estensione resources generato.|  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come generare un file con estensione resources con una sola risorsa con estensione bmp. La risorsa con estensione bmp viene generata in una directory relativa alla directory radice del progetto.  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



