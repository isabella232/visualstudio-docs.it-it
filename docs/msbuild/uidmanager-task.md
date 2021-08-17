---
title: Attività UidManager | Microsoft Docs
description: Informazioni su come MSBuild'attività UidManager controlla, aggiorna o rimuove identificatori univoci (UID) per localizzare tutti gli elementi XAML nei file XAML di origine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 90df39308965b8ac7fd9513a44f4c136dcfc14cd71abd8b5973f33851830d2fe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369696"
---
# <a name="uidmanager-task"></a>Attività UidManager

L'attività controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi XAML inclusi nei <xref:Microsoft.Build.Tasks.Windows.UidManager> file XAML di origine.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|-------------------------| - |
| `IntermediateDirectory` | Parametro **String** facoltativo.<br /><br /> Specifica la directory usata per eseguire il backup dei file XAML di origine specificati dal **parametro MarkupFiles.** |
| `MarkupFiles` | Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica i file XAML di origine da includere per il controllo, l'aggiornamento o la rimozione dell'UID. |
| `Task` | Parametro **String** obbligatorio.<br /><br /> Specifica l'attività di gestione degli UID da eseguire. Le opzioni valide sono **Check**, **Update** o **Remove**. |

## <a name="example"></a>Esempio

 L'esempio seguente usa l'attività per verificare che i file XAML di origine specificati <xref:Microsoft.Build.Tasks.Windows.UidManager> contengano elementi XAML con UID appropriati.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Procedura: Localizzare un'applicazione](/dotnet/framework/wpf/advanced/how-to-localize-an-application)