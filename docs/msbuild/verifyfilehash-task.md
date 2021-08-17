---
title: Attività VerifyFileHash | Microsoft Docs
description: Informazioni su MSBuild'attività VerifyFileHash per verificare che un file corrisponda all'hash di file previsto e ha esito negativo se non corrisponde.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e2680b9617f157aab3a3b96486e887842adc94a004994383f22d54751e2e55b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334068"
---
# <a name="verifyfilehash-task"></a>Attività VerifyFileHash

Verifica che un file corrisponda all'hash file previsto. Se l'hash non corrisponde, l'attività ha esito negativo.

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

In MSBuild 16.5 e versioni successive, se non si vuole che la compilazione non riesca quando l'hash non corrisponde, ad esempio se si usa il confronto hash come condizione per il flusso di controllo, è possibile eseguire il downgrade dell'avviso a un messaggio usando il codice seguente:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
