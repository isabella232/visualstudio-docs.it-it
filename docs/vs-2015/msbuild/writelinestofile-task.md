---
title: Attività WriteLinesToFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f530648c7dd772fb60148f4d755d4a4ffb420cbb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655136"
---
# <a name="writelinestofile-task"></a>Attività WriteLinesToFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Scrive i percorsi degli elementi specificati nel file di testo indicato.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `WriteLinestoFile`.  
  
|Parametro|Description|  
|---------------|-----------------|  
|`File`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file in cui scrivere gli elementi.|  
|`Lines`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli elementi da scrivere nel file.|  
|`Overwrite`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività sovrascrive qualsiasi contenuto esistente nel file.|  
|`Encoding`|Parametro `String` facoltativo.<br /><br /> Seleziona la codifica dei caratteri, ad esempio "Unicode".  Vedere anche <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Osservazioni  
 Se `Overwrite` è `true`, crea un nuovo file, scrive il contenuto nel file e quindi lo chiude. Se il file di destinazione è già esistente, viene sovrascritto. Se `Overwrite` è `false`, accoda il contenuto al file, creando il file di destinazione nel caso in cui non esista.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `WriteLinesToFile` per scrivere i percorsi degli elementi della raccolta di elementi `MyItems` nel file specificato dalla raccolta di elementi `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
