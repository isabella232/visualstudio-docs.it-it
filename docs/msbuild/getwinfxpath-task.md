---
title: Attività GetWinFXPath | Microsoft Docs
description: Informazioni su come usare l'attività GetWinFXPath di MSBuild, che restituisce la directory del runtime .NET corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 820ca103d88cde941fe558e59ed1c78622adccd4
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436767"
---
# <a name="getwinfxpath-task"></a>Attività GetWinFXPath

L' <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> attività restituisce la directory del runtime .NET corrente.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|-------------------| - |
| `WinFXPath` | Parametro di output **stringa** facoltativo.<br /><br /> Specifica il percorso reale del runtime .NET. |
| `WinFXNativePath` | Parametro **String** obbligatorio.<br /><br /> Specifica il percorso del runtime .NET nativo. |
| `WinFXWowPath` | Parametro **String** obbligatorio.<br /><br /> Specifica il percorso degli assembly .NET nel modulo Windows a 32 bit per **Windows** su sistemi a 64 bit. |

## <a name="remarks"></a>Commenti

 Se l'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> viene eseguita su un processore a 64 bit, il parametro **WinFXPath** viene impostato sul percorso archiviato nel parametro **WinFXWowPath**. In caso contrario, il parametro **WinFXPath** viene impostato sul percorso archiviato nel parametro **WinFXNativePath**.

## <a name="example"></a>Esempio

 Nell'esempio seguente viene illustrato come utilizzare l'attività **GetWinFXPath** per rilevare il percorso nativo del runtime .NET.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GetWinFXPathTask">
    <GetWinFXPath
      WinFXNativePath="c:\WinFXNative"
      WinFXWowPath="c:\WinFXWowNative" />
  </Target>
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
