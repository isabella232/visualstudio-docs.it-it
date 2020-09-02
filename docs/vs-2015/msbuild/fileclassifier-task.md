---
title: Attività FileClassifier | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2077b1df6d6362c924527e296d36c041e7bd9929
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693789"
---
# <a name="fileclassifier-task"></a>Attività FileClassifier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.FileClassifier> classifica un insieme di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Non utilizzato.|  
|`CLRResourceFiles`|Non utilizzato.|  
|`CLRSatelliteEmbeddedResource`|Non utilizzato.|  
|`Culture`|Parametro **stringa** facoltativo.<br /><br /> Specifica le impostazioni cultura per la compilazione. Questo valore può essere **null** se la compilazione non è localizzabile. Se **null**, il valore predefinito corrisponde al valore minuscolo restituito da **CultureInfo.InvariantCulture**.|  
|`MainEmbeddedFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Specifica le risorse non localizzabili incorporate nell'assembly principale.|  
|`OutputType`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di file in cui incorporare i file di origine specificati. I valori validi sono **exe**, **winexe** e **library**.|  
|`SatelliteEmbeddedFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Specifica i file localizzabili incorporati nell'assembly satellite per le impostazioni cultura specificate dal parametro **Culture**.|  
|`SourceFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica l'elenco di file da classificare.|  
  
## <a name="remarks"></a>Osservazioni  
 Se il parametro **Culture** non è impostato, tutte le risorse specificate usando il parametro **SourceFiles** non sono localizzabili. In caso contrario, sono localizzabili a meno che non vengano associate a un attributo **Localizable** impostato su **false**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente un singolo file di origine viene classificato come risorsa e incorporato in un assembly satellite per le impostazioni cultura Francese-Canadese (fr-CA).  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
