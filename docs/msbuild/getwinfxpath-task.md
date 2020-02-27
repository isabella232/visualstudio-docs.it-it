---
title: Attività GetWinFXPath | Microsoft Docs
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
ms.openlocfilehash: ab8e15cef722e935dde322072f6834ba00be8bc5
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633967"
---
# <a name="getwinfxpath-task"></a>Attività GetWinFXPath

L'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> restituisce la directory del runtime .NET corrente.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|-------------------| - |
| `WinFXPath` | Parametro di output **String** facoltativo.<br /><br /> Specifica il percorso reale del runtime .NET. |
| `WinFXNativePath` | Parametro **String** obbligatorio.<br /><br /> Specifica il percorso del runtime .NET nativo. |
| `WinFXWowPath` | Parametro **String** obbligatorio.<br /><br /> Specifica il percorso degli assembly .NET nel modulo Windows a 32 bit per **Windows** su sistemi a 64 bit. |

## <a name="remarks"></a>Note

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
- [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
