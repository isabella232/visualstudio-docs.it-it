---
title: Attività DownloadFile | Microsoft Docs
description: Informazioni sui parametri dell'attività MSBuild DownloadFile, che scarica i file specificati tramite HTTP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 44f1f59b30cca2cd547766350285491c348d3513
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077621"
---
# <a name="downloadfile-task"></a>Attività DownloadFile

Consente di scaricare i file specificati usando Hypertext Transfer Protocol (HTTP).

>[!NOTE]
>L'attività DownloadFile è disponibile solo in MSBuild 15.8 e versioni successive.

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `DownloadFile` .

|Parametro|Descrizione|
|---------------|-----------------|
|`DestinationFileName`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo<br /><br /> Nome da usare per il file scaricato.  Per impostazione predefinita, il nome del file è derivato dall'elemento `SourceUrl` o server remoto.|
|`DestinationFolder`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica la cartella di destinazione in cui scaricare il file.  Se non esiste, la cartella viene creata.|
|`DownloadedFile`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il file scaricato.|
|`Retries`|Parametro `Int32` facoltativo.<br /><br /> Specifica il numero di tentativi da eseguire per il download, se tutti i tentativi precedenti hanno avuto esito negativo. Il valore predefinito è zero.|
|`RetryDelayMilliseconds`|Parametro `Int32` facoltativo.<br /><br /> Specifica il ritardo in millisecondi tra eventuali nuovi tentativi necessari. Il valore predefinito è 5000.|
|`SkipUnchangedFiles`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, ignora il download dei file invariati. Il valore predefinito è `true`. L'attività `DownloadFile` considera invariati i file con le stesse dimensioni e la stessa ora dell'ultima modifica secondo il server remoto. <br /><br />**Nota:** se non tutti i server HTTP indicano la data dell'ultima modifica dei file, il file verrà scaricato nuovamente.|
|`SourceUrl`|Parametro `String` obbligatorio.<br /><br /> Specifica l'URL da scaricare.|

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene scaricato un file e incluso negli elementi `Content` prima della compilazione del progetto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
