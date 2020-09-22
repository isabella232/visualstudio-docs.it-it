---
title: Richiedi-MSSQL
description: per lo strumento devinit è necessario MSSQL.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ecd3839e114fd5cd542e0a35c0f3b6a1dcb7bbb4
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808424"
---
# <a name="require-mssql"></a>Richiedi-MSSQL

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

### <a name="builtin-options"></a>Opzioni predefinite

Lo `require-mssql` strumento imposta un numero di argomenti della riga di comando del programma di installazione per garantire che il programma di installazione possa essere eseguito. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella [documentazione sull'installazione di SQL](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs MSSQL.",
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```