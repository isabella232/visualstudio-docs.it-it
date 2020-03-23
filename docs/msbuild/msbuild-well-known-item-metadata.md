---
title: Metadati noti degli elementi di MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633096"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadati noti degli elementi di MSBuild

La tabella seguente descrive i metadati assegnati a ogni elemento durante la fase di creazione. In ogni esempio è stata usata la dichiarazione di elemento riportata di seguito per includere il file *C:\MyProject\Source\Program.cs* nel progetto.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadati degli elementi|Descrizione|
|-------------------|-----------------|
|%(FullPath)|Contiene il percorso completo dell'elemento. Ad esempio:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Contiene la directory radice dell'elemento. Ad esempio:<br /><br /> *C:\\*|
|%(Filename)|Contiene il nome file dell'elemento, senza estensione. Ad esempio:<br /><br /> *Programma*|
|%(Extension)|Contiene l'estensione del nome file dell'elemento. Ad esempio:<br /><br /> *Cs*|
|%(RelativeDir)|Contiene il percorso specificato nell'attributo `Include`, fino alla barra rovesciata (\\) finale. Ad esempio:<br /><br /> *Origine\\*<br /><br /> Se `Include` l'attributo è `%(RelativeDir)` un percorso `%(RootDir)`completo, inizia con la directory radice .  Ad esempio: <br /><br /> *C:\\*|
|%(Directory)|Contiene la directory dell'elemento, senza la directory radice. Ad esempio:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Se l'attributo `Include` contiene il carattere jolly \*\*, questi metadati specificano la parte del percorso che sostituisce il carattere jolly. Per altre informazioni sui caratteri jolly, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se la cartella *C:\MySolution\MyProject\Source\\* contiene il file *Program.cs* e se il file di progetto contiene l'elemento seguente:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> il valore di `%(MyItem.RecursiveDir)` sarà *MySolution\MyProject\Source\\*.|
|%(Identity)|Elemento specificato nell'attributo. `Include` Ad esempio:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Contiene il timestamp relativo all'ultima modifica dell'elemento. Ad esempio:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Contiene il timestamp relativo alla creazione dell'elemento. Ad esempio:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Contiene il timestamp relativo all'ora dell'ultimo accesso all'elemento.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Vedere anche

- [Elementi](../msbuild/msbuild-items.md)
- [Batch](../msbuild/msbuild-batching.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
