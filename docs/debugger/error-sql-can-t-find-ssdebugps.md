---
title: 'Errore: SQL può&#39;t trova SSDEBUGPS | Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: 038b448c0ecd0b19afd7671a381eb68c9ba8cbbe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854113"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Errore: SQL può&#39;t trova SSDEBUGPS

SSDEBUGPS.dll è il componente host di SQL Server per il debug.

Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.

Per risolvere l'errore è possibile eseguire nuovamente l'installazione della funzionalità per il debug remoto oppure copiare il file nel computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Per eseguire nuovamente l'installazione di debug remoto, seguire le istruzioni in [debug remoto](../debugger/remote-debugging.md).

Se è disponibile una copia di ssdebugps.dll, è possibile copiare il file nel computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Se presente, il file si trova nella directory \Programmi\File comuni\Microsoft Shared\SQL Debugging. È possibile trovarlo in un altro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] computer o in un computer con installato Visual Studio 2005.

Per copiare SSDEBUGPS.dll nel computer SQL Server 2005:

1. Copiare il file nella directory con lo stesso nome e percorso sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Effettuare la registrazione aprendo una finestra del **prompt dei comandi** ed eseguendo il seguente comando:

    ```cmd
    regsrv32 ssdebugps.dll
    ```
