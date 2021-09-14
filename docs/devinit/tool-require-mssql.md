---
title: require-mssql
description: devinit tool require-mssql.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e39a03fe70d2e4399b758e06e9acb2e0de59ef08
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636492"
---
# <a name="require-mssql"></a>require-mssql

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-mssql` strumento viene usato per installare Microsoft SQL Server [2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) da tramite MS SQL SERVER ISO. Il server SQL sarà disponibile in tramite l'autenticazione integrata Windows il server SQL sarà accessibile con `localhost` la stringa di connessione `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                   |
| [**Input**](#input)                              | stringa | No       | Per informazioni [dettagliate,](#input) vedere Input di seguito.                                                  |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.              |

### <a name="input"></a>Input

La `input` proprietà può essere una stringa con uno dei due valori seguenti:

| Valore     | Descrizione                              |
|-----------|------------------------------------------|
| Installazione   | Installa SQL server.                     |
| uninstall | Disinstalla tutte le SQL server. |

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-mssql` strumento è l'installazione SQL server.

### <a name="built-in-options"></a>Opzioni predefinite

Lo strumento imposta diversi argomenti della riga di comando del programma di installazione per garantire che il `require-mssql` programma di installazione possa essere eseguito senza testa. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella documentazione [SQL installare](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true).

| Nome                                                               | Descrizione |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION=Install                                                    |             |
| /FEATURES=SQLEngine, Local DB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource=MU                                                   |             |
| /X86=false                                                         |             |
| /INSTANCENAME=MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR="C:\Programmi\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR="C:\Programmi (x86)\Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT=True                                        |             |
| /INSTANCEDIR="C:\Programmi\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT="NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE=Manual                                          |             |
| /SQLSVCSTARTUPTYPE=Automatic                                       |             |
| /SQLCOLLATION="SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT="NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS=Administrators                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-msssql` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.json che installerà MSSQL:
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