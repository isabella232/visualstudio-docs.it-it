---
title: 'Errore: SQL possono&#39;t trova SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058256"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Errore: SQL possono&#39;t trova SSDEBUGPS

SSDEBUGPS.dll è il componente host di SQL Server per il debug.

Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.

Esistono due modi per risolvere questo errore: eseguendo nuovamente l'installazione del debug remoto e copiare il file nel [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] macchina.

Per eseguire nuovamente l'installazione di debug remoto, seguire le istruzioni in [debug remoto](../debugger/remote-debugging.md).

Se non è possibile individuare una copia di ssdebugps. dll, è possibile copiarlo nel [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] macchina. Se presente, il file si trova nella directory \Programmi\File comuni\Microsoft Shared\SQL Debugging. È possibile trovarlo in un altro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] computer o in un computer con installato Visual Studio 2005.

Per copiare SSDEBUGPS. dll nel computer SQL Server 2005:

1. Copiare il file nella directory con lo stesso nome e percorso sul [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] macchina.

2. Effettuare la registrazione aprendo una **prompt dei comandi**ed eseguendo il comando seguente:

    ```cmd
    regsrv32 ssdebugps.dll
    ```
