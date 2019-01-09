---
title: Attività MergeLocalizationDirectives | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64f36cadc6ee33563f516703f3bc48e81558b8ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959939"
---
# <a name="mergelocalizationdirectives-task"></a>Attività MergeLocalizationDirectives
L'attività <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> unisce i commenti e gli attributi di localizzazione di uno o più file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario in un singolo file per l'intero assembly.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
| Parametro | Description |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica l'elenco di file delle direttive di localizzazione per i singoli file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputFile` | Parametro di output **String** obbligatorio.<br /><br /> Specifica il percorso di output dell'assembly compilato delle direttive di localizzazione. |
  
## <a name="remarks"></a>Note  
 È possibile aggiungere commenti e attributi di localizzazione al contenuto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]. Con il supporto di localizzazione [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] è possibile rimuovere i commenti e gli attributi di localizzazione e inserirli in un file con estensione *loc* separato dall'assembly generato. È possibile eseguire questa operazione mediante l'attributo **LocalizationPropertyStorage**. Per altre informazioni sui commenti e gli attributi di localizzazione e su **LocalizationPropertyStorage**, vedere [Attributi e commenti di localizzazione](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente i commenti di localizzazione di diversi file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] vengono uniti in un unico file con estensione *loc*.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)  
[Informazioni di riferimento sulle attività MSBuild WPF](../msbuild/wpf-msbuild-task-reference.md)  
[Riferimenti a MSBuild](../msbuild/msbuild-reference.md)  
[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)  
[Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
