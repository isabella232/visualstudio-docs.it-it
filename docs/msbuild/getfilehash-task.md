---
title: Attività GetFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578657"
---
# <a name="getfilehash-task"></a>Attività GetFileHash

Calcola i checksum del contenuto di un file o di un set di file.

Questa attività è stata aggiunta nella versione 15.8. È tuttavia necessaria una [soluzione alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) per poter usare le versioni di MSBuild precedenti alla versione 16.0.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `GetFileHash`.

|Parametro|Descrizione|
|---------------|-----------------|
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br />File per i quali generare un hash.|
|`Items`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Input `Files` con metadati aggiuntivi impostato sul l'hash del file.|
|`Hash`|Parametro di output `String`.<br /><br />Hash del file. Questo output viene impostato solo se è stato passato esattamente un elemento.|
|`Algorithm`|Parametro `String` facoltativo.<br /><br />Algoritmo. Valori consentiti: `SHA256`, `SHA384`, `SHA512`. Valore predefinito = `SHA256`.|
|`MetadataName`|Parametro `String` facoltativo.<br /><br />Nome dei metadati in cui l'hash viene archiviato in ogni elemento. Il valore predefinito è `FileHash`.|
|`HashEncoding`|Parametro `String` facoltativo.<br /><br />Codifica da usare per gli hash generati. Il valore predefinito è `hex`. Valori consentiti = `hex`, `base64`.|

## <a name="example"></a>Esempio

L'esempio seguente usa l'attività `GetFileHash` per determinare e stampare il checksum degli elementi `FilesToHash`.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)