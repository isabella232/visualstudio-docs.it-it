---
title: Attività UidManager | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631523"
---
# <a name="uidmanager-task"></a>Attività UidManager

L' <xref:Microsoft.Build.Tasks.Windows.UidManager> attività controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi XAML inclusi nei file XAML di origine.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|-------------------------| - |
| `IntermediateDirectory` | Parametro **stringa** facoltativo.<br /><br /> Specifica la directory utilizzata per eseguire il backup dei file XAML di origine specificati dal parametro **MarkupFiles** . |
| `MarkupFiles` | Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica i file XAML di origine da includere per il controllo, l'aggiornamento o la rimozione degli UID. |
| `Task` | Parametro **String** obbligatorio.<br /><br /> Specifica l'attività di gestione degli UID da eseguire. Le opzioni valide sono **Check**, **Update** o **Remove**. |

## <a name="example"></a>Esempio

 Nell'esempio seguente viene usata l' <xref:Microsoft.Build.Tasks.Windows.UidManager> attività per verificare che i file XAML di origine specificati contengano elementi XAML con UID appropriati.

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

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Procedura: localizzare un'applicazione](/dotnet/framework/wpf/advanced/how-to-localize-an-application)