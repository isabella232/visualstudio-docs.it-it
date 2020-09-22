---
title: Batch MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839584"
---
# <a name="msbuild-batching"></a>Batch MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] è possibile dividere gli elenchi di elementi in diverse categorie, o batch, in base ai metadati degli elementi ed eseguire una destinazione o un'attività una sola volta per ogni batch.  
  
## <a name="task-batching"></a>Suddivisione in batch delle attività  
 Suddividere le attività in batch consente di semplificare i file di progetto, dividendo gli elenchi di elementi in diversi batch che vengono poi passati separatamente in un'attività. Ciò significa che per un file di progetto è necessario dichiarare l'attività e i relativi attributi solo una volta, anche se può essere eseguito più volte.  
  
 Si specifica che si vuole [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] eseguire la suddivisione in batch con un'attività usando la notazione%(*ItemMetaDataName*) in uno degli attributi di attività. L'esempio seguente suddivide l'elenco di elementi `Example` in batch in base al valore dei metadati degli elementi `Color` e passa ogni batch all'attività `MyTask` separatamente.  
  
> [!NOTE]
> Se non si fa riferimento all'elenco di elementi in un'altra posizione negli attributi dell'attività oppure il nome dei metadati potrebbe essere ambiguo, è possibile usare la notazione%(*ItemCollection. ItemMetaDataName*) per qualificare completamente il valore dei metadati dell'elemento da usare per l'invio in batch.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Per esempi di batch più specifici, vedere [metadati degli elementi nell'invio in batch delle attività](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Suddivisione in batch della destinazione  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verifica se gli input e output di una destinazione sono aggiornati prima di eseguire la destinazione. Se sia gli input che gli output sono aggiornati, la destinazione viene ignorata. Se un'attività all'interno di una destinazione usa la suddivisione in batch, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] deve determinare se gli input e gli output per ogni batch di elementi sono aggiornati. In caso contrario, la destinazione viene eseguita ogni volta che viene raggiunta.  
  
 Nell'esempio seguente viene illustrato un `Target` elemento che contiene un `Outputs` attributo con la notazione%(*ItemMetaDataName*). [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] suddivide l'elenco di elementi `Example` in batch in base ai metadati degli elementi `Color` e analizza i timestamp dei file di output per ogni batch. Se gli output di un batch non sono aggiornati, la destinazione viene eseguita. In caso contrario, la destinazione viene ignorata.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Per un altro esempio di batch di destinazione, vedere [metadati degli elementi nel batch di destinazione](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funzioni delle proprietà che usano i metadati  
 La suddivisione in batch può essere controllata usando funzioni delle proprietà che includono i metadati. Ad esempio,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 usa <xref:System.IO.Path.Combine%2A> per combinare un percorso di cartella radice con un percorso di elemento Compile.  
  
 Le funzioni delle proprietà possono non apparire all'interno dei valori dei metadati.  Ad esempio,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 non è consentito.  
  
 Per ulteriori informazioni sulle funzioni di proprietà, vedere [funzioni di proprietà](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
 [Concetti avanzati](../msbuild/msbuild-advanced-concepts.md)
