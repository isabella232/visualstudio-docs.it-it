---
title: Attività GetWinFXPath | Microsoft Docs
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21aa8cd81465917c33709b751ba2e206e7d7484d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526001"
---
# <a name="getwinfxpath-task"></a>Attività GetWinFXPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività GetWinFXPath](https://docs.microsoft.com/visualstudio/msbuild/getwinfxpath-task).  
  
  
L'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> restituisce la directory del runtime [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] corrente.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WinFXPath`|Parametro di output **String** facoltativo.<br /><br /> Specifica il percorso reale del runtime [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)].|  
|`WinFXNativePath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso del runtime [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] nativo.|  
|`WinFXWowPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso degli assembly [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] nel modulo **Windows on Windows** a 32 bit nei sistemi a 64 bit.|  
  
## <a name="remarks"></a>Note  
 Se l'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> viene eseguita su un processore a 64 bit, il parametro **WinFXPath** viene impostato sul percorso archiviato nel parametro **WinFXWowPath**. In caso contrario, il parametro **WinFXPath** viene impostato sul percorso archiviato nel parametro **WinFXNativePath**.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come usare l'attività **GetWinFXPath** per individuare il percorso nativo del runtime [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)].  
  
```  
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
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



