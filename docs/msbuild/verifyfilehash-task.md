---
title: Attività VerifyFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3acdaabffc35122616cced4113abbc5a43beb9a1
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481969"
---
# <a name="verifyfilehash-task"></a>Attività VerifyFileHash

Verifica che un file corrisponda all'hash file previsto.

Questa attività è stata aggiunta nella versione 15.8. È tuttavia necessaria una [soluzione alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) per poter usare le versioni di MSBuild precedenti alla versione 16.0.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `VerifyFileHash` .

|Parametro|Descrizione|
|---------------|-----------------|
|`File`|Parametro `String` obbligatorio.<br /><br />File di cui eseguire l'hashing e la convalida.|
|`Hash`|Parametro `String` obbligatorio.<br /><br />Hash file previsto.|
|`Algorithm`|Parametro `String` facoltativo.<br /><br />Algoritmo. Valori consentiti: `SHA256`, `SHA384`, `SHA512`. Valore predefinito = `SHA256`.|
|`HashEncoding`|Parametro `String` facoltativo.<br /><br />Codifica da usare per gli hash generati. Il valore predefinito è `hex`. Valori consentiti = `hex`, `base64`.|

## <a name="example"></a>Esempio

Nell'esempio seguente l'attività `VerifyFileHash` viene usata per verificare il relativo checksum.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)