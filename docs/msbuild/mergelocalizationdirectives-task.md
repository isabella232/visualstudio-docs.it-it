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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7699afeb09604a437aad091f9aaf9ce624d33e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633499"
---
# <a name="mergelocalizationdirectives-task"></a>Attività MergeLocalizationDirectives

L'attività <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> unisce gli attributi di localizzazione e i commenti di uno o più file di formato binario XAML in un singolo file per l'intero assembly.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Parametro **ITaskItem []** obbligatorio.<br /><br /> Specifica l'elenco dei file di direttive di localizzazione per i singoli file in formato binario XAML. |
| `OutputFile` | Parametro di output **String** obbligatorio.<br /><br /> Specifica il percorso di output dell'assembly compilato delle direttive di localizzazione. |

## <a name="remarks"></a>Note

È possibile aggiungere commenti e attributi di localizzazione al contenuto XAML. Con il supporto della localizzazione Windows Presentation Foundation (WPF), è possibile rimuovere i commenti e gli attributi di localizzazione e inserirli in un file con *estensione loc* separato dall'assembly generato. È possibile eseguire questa operazione mediante l'attributo **LocalizationPropertyStorage**. Per altre informazioni sui commenti e gli attributi di localizzazione e su **LocalizationPropertyStorage**, vedere [Attributi e commenti di localizzazione](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Esempio

Nell'esempio seguente i commenti di localizzazione di diversi file di formato binario XAML vengono uniti in un unico file con *estensione loc* .

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

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività MSBuild WPF](../msbuild/wpf-msbuild-task-reference.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
