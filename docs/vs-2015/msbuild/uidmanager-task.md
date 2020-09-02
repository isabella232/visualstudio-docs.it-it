---
title: Attività UidManager | Microsoft Docs
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
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5fd8175911def7fb1b63dc63d967c404d649e9e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703686"
---
# <a name="uidmanager-task"></a>Attività UidManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.UidManager> controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] inclusi nei file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] di origine.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`IntermediateDirectory`|Parametro **stringa** facoltativo.<br /><br /> Specifica la directory usata per eseguire il backup dei file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] di origine specificati dal parametro **MarkupFiles**.|  
|`MarkupFiles`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica i file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] di origine da includere per il controllo, l'aggiornamento o la rimozione degli UID.|  
|`Task`|Parametro **String** obbligatorio.<br /><br /> Specifica l'attività di gestione degli UID da eseguire. Le opzioni valide sono **Check**, **Update** o **Remove**.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività <xref:Microsoft.Build.Tasks.Windows.UidManager> per verificare che i file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] di origine specificati contengano gli elementi [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] con UID appropriati.  
  
```  
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
 [Riferimenti a MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Procedura: Localizzare un'applicazione](https://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)
