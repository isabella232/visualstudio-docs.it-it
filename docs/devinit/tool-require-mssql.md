---
title: require-mssql
description: per lo strumento devinit è necessario MSSQL.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 95558da015462899d0388870fce95d19030fc291
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442098"
---
# <a name="require-mssql"></a>require-mssql

Lo `require-mssql` strumento viene utilizzato per installare [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) da tramite l'ISO di MS SQL Server. SQL Server sarà disponibile per l' `localhost` utilizzo dell'autenticazione integrata di Windows e SQL Server sarà accessibile con la stringa di connessione `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                   |
| [**input**](#input)                              | stringa | No       | Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                                                  |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.              |

### <a name="input"></a>Input

La `input` proprietà può essere una stringa con uno dei due valori seguenti:

| Valore     | Descrizione                              |
|-----------|------------------------------------------|
| Installazione   | Installa SQL Server.                     |
| uninstall | Disinstalla tutte le installazioni di SQL Server. |

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-mssql` strumento è l'installazione di SQL Server.

### <a name="built-in-options"></a>Opzioni predefinite

Lo `require-mssql` strumento imposta un numero di argomenti della riga di comando del programma di installazione per garantire che il programma di installazione possa essere eseguito. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella [documentazione sull'installazione di SQL](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

| Nome                                                               | Descrizione |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = install                                                    |             |
| /FEATURES = SQLEngine, database locale                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = false                                                         |             |
| /INSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Programmi\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Programmi (x86) \Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT = true                                        |             |
| /INSTANCEDIR = "C:\Programmi\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = manuale                                          |             |
| /SQLSVCSTARTUPTYPE = automatico                                       |             |
| /SQLCOLLATION = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS = amministratori                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-msssql` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.jssu che installerà MSSQL:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```