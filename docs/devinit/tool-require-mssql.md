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
ms.openlocfilehash: 7ad7e9d8518457c3f0c09164c0e1e9d561d229cea1afa59f72b1009a29324784
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390540"
---
# <a name="require-mssql"></a>require-mssql

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-mssql` strumento viene usato per installare Microsoft SQL Server [2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) da tramite l'ISO SQL server MS. Il SQL server sarà disponibile per l'uso dell'autenticazione integrata Windows il server SQL sarà accessibile `localhost` con la stringa di connessione `"Server=localhost;Integrated Security=true;"` .

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                   |
| [**Input**](#input)                              | stringa | No       | Per [informazioni dettagliate,](#input) vedere Input di seguito.                                                  |
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

Lo strumento imposta diversi argomenti della riga di comando del programma di installazione per garantire che il programma `require-mssql` di installazione possa essere eseguito senza testa. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella documentazione SQL [di installazione .](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true)

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
| /AGTSVCACCOUNT="SERVIZIO NT\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE=Manual                                          |             |
| /SQLSVCSTARTUPTYPE=Automatic                                       |             |
| /SQLCOLLATION="SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT="NT Service\MSSQLSERVER"                            |             |
| /SQLSYSADMINACCOUNTS=Administrators                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-msssql` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.jsin che installerà MSSQL:
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