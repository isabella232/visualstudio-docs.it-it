---
title: Destinazioni di MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06b49a8fda448707540d5bfe65d0499c6c2dde96
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767363"
---
# <a name="msbuild-targets"></a>Destinazioni di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Le destinazioni raggruppano le attività in un determinato ordine e consentono di suddividere il processo di compilazione in unità più piccole. Ad esempio, una destinazione può eliminare tutti i file presenti nella directory di output per preparare la compilazione, mentre un'altra compila gli input per il progetto e li inserisce nella directory vuota. Per altre informazioni sulle attività, vedere [Attività](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Dichiarazione delle destinazioni nel file di progetto  
 Per dichiarare le destinazioni in un file di progetto si usa l'elemento [Target](../msbuild/target-element-msbuild.md). Ad esempio, il codice XML seguente crea una destinazione denominata Construct che chiama l'attività Csc con il tipo di elemento Compile.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Come le proprietà di MSBuild, le destinazioni possono essere ridefinite. Ad esempio,  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Se si esegue AfterBuild, viene visualizzato solo "Second occurrence".  
  
## <a name="target-build-order"></a>Ordine di compilazione delle destinazioni  
 Le destinazioni devono venire ordinate se l'input per una destinazione dipende dall'output di un'altra destinazione. Esistono diversi modi per specificare l'ordine di esecuzione delle destinazioni.  
  
- Destinazioni iniziali  
  
- Destinazioni predefinite  
  
- Prima destinazione  
  
- Dipendenze tra destinazioni  
  
- `BeforeTargets` e `AfterTargets` (MSBuild 4.0)  
  
  Una destinazione non viene mai eseguita due volte durante una compilazione, anche se da essa dipende una destinazione successiva nella compilazione. Il contributo della destinazione alla compilazione termina dopo che è stata eseguita.  
  
  Per dettagli e altre informazioni sull'ordine di compilazione delle destinazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Suddivisione in batch della destinazione  
 Un elemento di destinazione può avere un attributo `Outputs` che specifica i metadati nel formato %(metadati). In questo caso MSBuild esegue la destinazione una volta per ogni valore univoco dei metadati, raggruppando o suddividendo in "batch" gli elementi che contengono quel valore dei metadati. Ad esempio,  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 suddivide in batch gli elementi di riferimento in base ai metadati RequiredTargetFramework. L'output dell'esempio è simile al seguente:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 La suddivisione in batch della destinazione viene usata raramente nelle compilazioni reali. La suddivisione in batch delle attività è più comune. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Compilazioni incrementali  
 Le compilazioni incrementali sono compilazioni ottimizzate in modo da non eseguire le destinazioni con file di output aggiornati rispetto ai file di input corrispondenti. Un elemento di destinazione può avere entrambi gli attributi `Inputs` e `Outputs` per indicare quali elementi la destinazione accetta come input e quali elementi genera come output.  
  
 Se tutti gli elementi di output sono aggiornati, MSBuild ignora la destinazione e questo migliora notevolmente la velocità di compilazione. Questa operazione è definita compilazione incrementale della destinazione. Se solo alcuni file sono aggiornati, MSBuild esegue la destinazione senza gli elementi aggiornati. Questa operazione è definita compilazione incrementale parziale della destinazione. Per altre informazioni, vedere [Compilazioni incrementali](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
