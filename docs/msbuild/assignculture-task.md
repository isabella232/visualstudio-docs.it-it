---
title: Attività AssignCulture | Microsoft Docs
description: Usare l MSBuild'attività AssignCulture per produrre un elemento con un metadati denominato Culture contenente l'identificatore delle impostazioni cultura corrispondente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5bce381e9d851764d2c7d331a247d085f829e94a06ea2750da332c7ab0997008
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428627"
---
# <a name="assignculture-task"></a>AssignCulture (attività)

Questa attività accetta un elenco di elementi che possono contenere una stringa dell'identificatore di impostazioni cultura .NET valida come parte del nome file e genera elementi con metadati denominati `Culture` che contengono l'identificatore di impostazioni cultura corrispondente. Ad esempio, il nome di file *Form1.fr-fr.resx* contiene un identificatore di impostazioni cultura incorporato, "fr-fr", quindi questa attività genera un elemento con lo stesso nome di file con i metadati `Culture` uguali a `fr-fr`. L'attività genera inoltre un elenco di nomi di file con le impostazioni cultura rimosse dal nome del file.

## <a name="task-parameters"></a>Parametri dell'attività

Nella tabella che segue vengono descritti i parametri dell'attività `AssignCulture` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AssignedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di elementi ricevuti nel parametro `Files`, con una voce di metadati `Culture` aggiunta a ogni elemento.<br /><br /> Se l'elemento proveniente dal parametro `Files` contiene già una voce di metadati `Culture`, viene usata la voce di metadati originale.<br /><br /> L'attività assegna una voce di metadati `Culture` solo se il nome del file contiene un identificatore di impostazioni cultura valido. L'identificatore di impostazioni cultura deve essere compreso tra gli ultimi due punti nel nome file.|
|`AssignedFilesWithCulture`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene il subset degli elementi del parametro `AssignedFiles` che hanno una voce di metadati `Culture`.|
|`AssignedFilesWithNoCulture`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene il subset degli elementi del parametro `AssignedFiles` che non hanno una voce di metadati `Culture`.|
|`CultureNeutralAssignedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene lo stesso elenco di elementi generato nel parametro `AssignedFiles`, eccetto le impostazioni cultura rimosse dal nome del file.<br /><br /> L'attività rimuove le impostazioni cultura dal nome del file solo se viene usato un identificatore di impostazioni cultura valido.|
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco di file con nomi di impostazioni cultura incorporati a cui assegnare le impostazioni cultura.|

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 Nell'esempio seguente viene eseguita l'attività `AssignCulture` con la raccolta di elementi `ResourceFiles`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ResourceFiles Include="MyResource1.fr.resx"/>
        <ResourceFiles Include="MyResource2.XX.resx"/>
    </ItemGroup>

    <Target Name="Culture">
        <AssignCulture
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
            <Output TaskParameter="AssignedFilesWithCulture"
                ItemName="OutAssignedFilesWithCulture"/>
            <Output TaskParameter="AssignedFilesWithNoCulture"
                ItemName="OutAssignedFilesWithNoCulture"/>
            <Output TaskParameter="CultureNeutralAssignedFiles"
                ItemName="OutCultureNeutralAssignedFiles"/>
        </AssignCulture>
    </Target>
</Project>
```

La tabella seguente descrive il valore degli elementi di output dopo l'esecuzione dell'attività. I metadati degli elementi vengono visualizzati tra parentesi dopo l'elemento.

|Raccolta di elementi|Contenuto|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx* (Impostazioni cultura="fr")<br /><br /> *MyResource2.XX.resx* (senza metadati aggiuntivi)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (Impostazioni cultura="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (senza metadati aggiuntivi)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (Impostazioni cultura="fr")<br /><br /> *MyResource2.XX.resx* (senza metadati aggiuntivi)|

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
