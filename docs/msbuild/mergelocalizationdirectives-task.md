---
title: Attività MergeLocalizationDirectives | Microsoft Docs
description: Informazioni su MSBuild usa l'attività MergeLocalizationDirectives per unire gli attributi di localizzazione e i commenti dei file di formato binario XAML in un unico file.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 13d052402196126c53f327fd1cc2033f99da548b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069029"
---
# <a name="mergelocalizationdirectives-task"></a>Attività MergeLocalizationDirectives

L'attività unisce gli attributi di localizzazione e i commenti di uno o più file di formato binario <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> XAML in un unico file per l'intero assembly.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica l'elenco di file di direttive di localizzazione per singoli file in formato binario XAML. |
| `OutputFile` | Parametro di output **String** obbligatorio.<br /><br /> Specifica il percorso di output dell'assembly compilato delle direttive di localizzazione. |

## <a name="remarks"></a>Commenti

È possibile aggiungere attributi e commenti di localizzazione al contenuto XAML. Con Windows Presentation Foundation di localizzazione di Windows Presentation Foundation (WPF), è possibile rimuovere gli attributi e i commenti di localizzazione e inserire i commenti in un file *loc* separato dall'assembly generato. È possibile eseguire questa operazione mediante l'attributo **LocalizationPropertyStorage**. Per altre informazioni sui commenti e gli attributi di localizzazione e su **LocalizationPropertyStorage**, vedere [Attributi e commenti di localizzazione](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Esempio

L'esempio seguente unisce i commenti di localizzazione di diversi file di formato binario XAML in un singolo file *loc.*

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

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento MSBuild attività wpf](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
