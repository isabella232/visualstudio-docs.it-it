---
title: Attività WriteLinesToFile | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0256ea6242a01cd8e18017889dc450bc60e6fc82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531444"
---
# <a name="writelinestofile-task"></a>Attività WriteLinesToFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività WriteLinesToFile](https://docs.microsoft.com/visualstudio/msbuild/writelinestofile-task).  
  
  
Scrive i percorsi degli elementi specificati nel file di testo indicato.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `WriteLinestoFile`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`File`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file in cui scrivere gli elementi.|  
|`Lines`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli elementi da scrivere nel file.|  
|`Overwrite`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività sovrascrive qualsiasi contenuto esistente nel file.|  
|`Encoding`|Parametro `String` facoltativo.<br /><br /> Seleziona la codifica dei caratteri, ad esempio "Unicode".  Vedere anche <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Note  
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



