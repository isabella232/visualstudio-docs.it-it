---
title: Attività Copy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08442d6044ca978e69f199e76c4668db63c319da
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086273"
---
# <a name="copy-task"></a>Attività Copy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Copia i file in un nuovo percorso del file system.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Copy` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`CopiedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi copiati correttamente.|  
|`DestinationFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elenco di file in cui copiare i file di origine. Dovrebbe esistere un mapping uno-a-uno tra questo elenco e quello specificato nel parametro `SourceFiles`. In altri termini, il primo file specificato in `SourceFiles` verrà copiato nel primo percorso specificato in `DestinationFiles`e così via.|  
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la directory in cui si vogliono copiare i file. Deve trattarsi di una directory, non di un file. Se la directory non esiste, viene creata automaticamente.|  
|`OverwriteReadOnlyFiles`|Parametro `Boolean` facoltativo.<br /><br /> Sovrascrivi file anche se sono contrassegnati come file di sola lettura|  
|`Retries`|Parametro `Int32` facoltativo.<br /><br /> Specifica il numero di tentativi da eseguire per la copia, se tutti i tentativi precedenti hanno avuto esito negativo. Il valore predefinito è zero.<br /><br /> **Nota:** La ripetizione dei tentativi può nascondere un problema di sincronizzazione nel processo di compilazione.|  
|`RetryDelayMilliseconds`|Parametro `Int32` facoltativo.<br /><br /> Specifica il ritardo tra eventuali nuovi tentativi necessari. Imposta come valore predefinito l'argomento RetryDelayMillisecondsDefault, che viene passato al costruttore CopyTask.|  
|`SkipUnchangedFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, i file rimasti invariati dall'origine alla destinazione non vengono copiati. L'attività `Copy` considera invariati i file con le stesse dimensioni e la stessa ora dell'ultima modifica. **Nota:** Se questo parametro viene impostato su `true`, è consigliabile non usare l'analisi delle dipendenze nella destinazione contenitore, perché in questo caso l'attività viene eseguita soltanto se l'ora dell'ultima modifica dei file di origine è più recente rispetto a quella dei file di destinazione.|  
|`SourceFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da copiare.|  
|`UseHardlinksIfPossible`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, vengono creati dei collegamenti reali per i file copiati invece di copiare i file.|  
  
## <a name="warnings"></a>Avvisi  
 Gli avvisi vengono registrati, inclusi:  
  
- `Copy.DestinationIsDirectory`  
  
- `Copy.SourceIsDirectory`  
  
- `Copy.SourceFileNotFound`  
  
- `Copy.CreatesDirectory`  
  
- `Copy.HardLinkComment`  
  
- `Copy.RetryingAsFileCopy`  
  
- `Copy.FileComment`  
  
- `Copy.RemovingReadOnlyAttribute`  
  
## <a name="remarks"></a>Osservazioni  
 È necessario specificare il parametro `DestinationFolder` o `DestinationFiles`, ma non entrambi. Se vengono specificati entrambi, l'attività avrà esito negativo e verrà registrato un errore.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito gli elementi della raccolta `MySourceFiles` vengono copiati nella cartella c:\MyProject\Destination.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFolder="c:\MyProject\Destination"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come creare una copia ricorsiva. Tutti i file del progetto vengono copiati in modo ricorsivo da c:\MySourceTree a c:\MyDestinationTree, mantenendo al tempo stesso la struttura di directory.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
