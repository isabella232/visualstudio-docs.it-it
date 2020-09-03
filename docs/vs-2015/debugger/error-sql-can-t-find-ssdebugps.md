---
title: 'Errore: SQL può&#39;t find SSDEBUGPS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185198"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Errore: SQL può&#39;t find SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll è il componente host di SQL Server per il debug.  
  
 Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.  
  
 Per risolvere l'errore è possibile eseguire nuovamente l'installazione della funzionalità per il debug remoto oppure copiare il file nel computer [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
 Per eseguire di nuovo l'installazione del debug remoto, seguire le istruzioni riportate in [Remote Debugging](../debugger/remote-debugging.md).  
  
 Se è disponibile una copia di ssdebugps.dll, è possibile copiare il file nel computer [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Se presente, il file si trova nella directory \Programmi\File comuni\Microsoft Shared\SQL Debugging. Potrebbe trovarsi in un altro [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] computer o in un computer in cui è [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] installato.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Per copiare SSDEBUGPS.dll nel computer SQL Server 2005  
  
1. Copiare il file nella directory con lo stesso nome e percorso sul computer [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
2. Effettuare la registrazione aprendo una finestra del **prompt dei comandi** ed eseguendo il seguente comando:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
