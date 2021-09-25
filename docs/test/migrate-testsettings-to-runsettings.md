---
title: Eseguire la migrazione di testsettings a runsettings
description: Informazioni su come eseguire la migrazione di testsettings a runsettings
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 348de2d34e30c96449dcd2e4c2ba6eb83ed24c4c
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429688"
---
# <a name="upgrade-from-testsettings-to-runsettings"></a>Eseguire l'aggiornamento da .testsettings a .runsettings

È possibile aggiornare il file di configurazione di test da *.testsettings* a *.runsettings* con lo strumento SettingsMigrator che viene installato insieme a Visual Studio. A seconda del percorso Visual Studio di installazione, è possibile trovare lo strumento di migrazione delle impostazioni nel percorso seguente:
::: moniker range=">=vs-2022"
`C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`
::: moniker-end
::: moniker range="vs-2019"
`C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`
::: moniker-end

Nel percorso corretto della directory è possibile eseguire lo strumento con il formato seguente:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Esempio
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Se si è interessati a leggere altre informazioni su come le opzioni *.testsettings* vengono convertite in *.runsettings,* è possibile trovare altri dettagli di implementazione nel repository della piattaforma di test di [open source](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) in GitHub.

## <a name="see-also"></a>Vedi anche

- [Configurare le esecuzioni dei test con `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Eseguire l'aggiornamento da MSTestv1 a MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire il debug di unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md)
