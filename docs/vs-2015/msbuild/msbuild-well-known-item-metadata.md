---
title: Metadati noti degli elementi di MSBuild | Microsoft Docs
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
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154079"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadati noti degli elementi di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tabella seguente descrive i metadati assegnati a ogni elemento durante la fase di creazione. In ogni esempio è stata usata la dichiarazione di elemento riportata di seguito per includere il file `C:\MyProject\Source\Program.cs` nel progetto.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadati degli elementi|Descrizione|  
|-------------------|-----------------|  
|%(FullPath)|Contiene il percorso completo dell'elemento. Ad esempio:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Contiene la directory radice dell'elemento. Ad esempio:<br /><br /> `C:\`|  
|%(Filename)|Contiene il nome file dell'elemento, senza estensione. Ad esempio:<br /><br /> `Program`|  
|%(Extension)|Contiene l'estensione del nome file dell'elemento. Ad esempio:<br /><br /> `.cs`|  
|%(RelativeDir)|Contiene il percorso specificato nell'attributo `Include`, fino alla barra rovesciata (\\) finale. Ad esempio:<br /><br /> `Source\`|  
|%(Directory)|Contiene la directory dell'elemento, senza la directory radice. Ad esempio:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Se l'attributo `Include` contiene il carattere jolly \*\*, questi metadati specificano la parte del percorso che sostituisce il carattere jolly. Per altre informazioni sui caratteri jolly, vedere [Procedura: Selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se la cartella *C:\MySolution\MyProject\Source\\* contiene il file Program.cs e se il file di progetto contiene l'elemento seguente:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> il valore di `%(MyItem.RecursiveDir)` sarà *MySolution\MyProject\Source\\* .|  
|%(Identity)|Elemento specificato nell'attributo `Include`. Ad esempio:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Contiene il timestamp relativo all'ultima modifica dell'elemento. Ad esempio:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Contiene il timestamp relativo alla creazione dell'elemento. Ad esempio:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Contiene il timestamp relativo all'ora dell'ultimo accesso all'elemento.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi](../msbuild/msbuild-items.md)   
 [Suddivisione in batch](../msbuild/msbuild-batching.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
