---
description: SSDEBUGPS.dll è il componente host di SQL Server per il debug.
title: SQL Impossibile &apos; trovare SSDEBUGPS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 75ab62def371ef1fa210b39a23dc62d33f98cd39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154453"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Errore: SQL impossibile&#39;trovare SSDEBUGPS

SSDEBUGPS.dll è il componente host di SQL Server per il debug.

Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.

Per risolvere l'errore è possibile eseguire nuovamente l'installazione della funzionalità per il debug remoto oppure copiare il file nel computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Per rieseguire l'installazione del debug remoto, seguire le istruzioni in [Debug remoto](../debugger/remote-debugging.md).

Se è disponibile una copia di ssdebugps.dll, è possibile copiare il file nel computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Se presente, il file si trova nella directory \Programmi\File comuni\Microsoft Shared\SQL Debugging. È possibile trovarlo in un altro computer o in un computer in cui Visual Studio [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 2005.

Per copiare SSDEBUGPS.dll nel computer SQL Server 2005:

1. Copiare il file nella directory con lo stesso nome e percorso sul computer [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Effettuare la registrazione aprendo una finestra del **prompt dei comandi** ed eseguendo il seguente comando:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
