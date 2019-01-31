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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b4bd8ed846ab4f3d461a29f152db0b83232ec8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972248"
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
    regsvr32 ssdebugps.dll
    ```
