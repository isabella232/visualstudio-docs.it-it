---
title: Metadati noti degli elementi di MSBuild | Microsoft Docs
description: Informazioni sui MSBuild assegnati a ogni elemento al momento della creazione e su alcuni MSBuild facoltativi che è possibile definire per controllare il comportamento di compilazione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: da48ecf879478be22c3a8e2db9bb6a3700390869
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093684"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadati noti degli elementi di MSBuild

I metadati degli elementi sono valori associati agli elementi. Alcuni vengono assegnati MSBuild agli elementi quando vengono creati elementi, ma è anche possibile definire i metadati necessari. Alcuni valori di metadati definiti dall'utente hanno un significato MSBuild, attività specifiche o SDK, ad esempio .NET SDK.

La prima tabella di questo articolo descrive i metadati assegnati a ogni elemento al momento della creazione. La tabella seguente mostra alcuni metadati facoltativi che hanno un significato per MSBuild, che è possibile definire per controllare il comportamento di compilazione. In ogni esempio è stata usata la dichiarazione di elemento riportata di seguito per includere il file *C:\MyProject\Source\Program.cs* nel progetto.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadati degli elementi|Descrizione|
|-------------------|-----------------|
|%(FullPath)|Contiene il percorso completo dell'elemento. Esempio:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Contiene la directory radice dell'elemento. Esempio:<br /><br /> *C:\\*|
|%(Filename)|Contiene il nome file dell'elemento, senza estensione. Esempio:<br /><br /> *Programma*|
|%(Extension)|Contiene l'estensione del nome file dell'elemento. Esempio:<br /><br /> *Cs*|
|%(RelativeDir)|Contiene il percorso specificato nell'attributo `Include`, fino alla barra rovesciata (\\) finale. Esempio:<br /><br /> *Origine\\*<br /><br /> Se `Include` l'attributo è un percorso completo, `%(RelativeDir)` inizia con la directory radice `%(RootDir)` .  Esempio: <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|Contiene la directory dell'elemento, senza la directory radice. Esempio:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Se l'attributo `Include` contiene il carattere jolly \*\*, questi metadati specificano la parte del percorso che sostituisce il carattere jolly. Per altre informazioni sui caratteri jolly, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se la cartella *C:\MySolution\MyProject\Source\\* contiene il file *Program.cs* e se il file di progetto contiene l'elemento seguente:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> il valore di `%(MyItem.RecursiveDir)` sarà *MySolution\MyProject\Source\\*.|
|%(Identity)|Elemento specificato `Include` nell'attributo. Esempio:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Contiene il timestamp relativo all'ultima modifica dell'elemento. Esempio:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Contiene il timestamp relativo alla creazione dell'elemento. Esempio:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Contiene il timestamp relativo all'ora dell'ultimo accesso all'elemento.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Vedi anche

- [Metadati dell'elemento MSBuild comuni](common-msbuild-item-metadata.md)
- [Elementi](../msbuild/msbuild-items.md)
- [Batch](../msbuild/msbuild-batching.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
