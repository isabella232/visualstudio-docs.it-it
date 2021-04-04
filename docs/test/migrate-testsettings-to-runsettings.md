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
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087186"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>Aggiornamento da  *. testsettings* a *. runsettings*

È possibile aggiornare il file di configurazione di test da *. testsettings* a *. runsettings* con lo strumento SettingsMigrator installato insieme a Visual Studio. A seconda del percorso di installazione di Visual Studio, è possibile trovare lo strumento Migrator delle impostazioni nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

Nel percorso della directory corretta, è possibile eseguire lo strumento con il formato seguente:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Esempio
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Se si è interessati a leggere altre informazioni sul modo in cui le opzioni *. testsettings* vengono convertite in *. runsettings* , è possibile trovare altri dettagli sull'implementazione nell' [Archivio della piattaforma di test Open Source](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) su GitHub.

## <a name="see-also"></a>Vedi anche

- [Configurare esecuzioni dei test con `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Eseguire l'aggiornamento da MSTestv1 a MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire il debug di unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md)
