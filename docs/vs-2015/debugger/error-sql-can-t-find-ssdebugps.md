---
title: 'Errore: SQL possono&#39;t trova SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 47e0557e3ad2022250d54b7bd45844825ff79a03
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757472"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Errore: SQL possono&#39;t trova SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll è il componente host di SQL Server per il debug.  
  
 Questo errore si verifica quando si tenta di avviare il debug e indica che il file specificato non è presente sul computer [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. È possibile che la funzionalità per il debug remoto non sia mai stata installata oppure che il file sia stato eliminato accidentalmente.  
  
 Esistono due modi per risolvere questo errore: eseguendo nuovamente l'installazione del debug remoto e copiare il file nel [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] macchina.  
  
 Per eseguire nuovamente l'installazione di debug remoto, seguire le istruzioni in [debug remoto](../debugger/remote-debugging.md).  
  
 Se non è possibile individuare una copia di ssdebugps. dll, è possibile copiarlo nel [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] macchina. Se presente, il file si trova nella directory \Programmi\File comuni\Microsoft Shared\SQL Debugging. È possibile trovarlo in un altro [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] computer, o in un computer dotato di [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] installato.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Per copiare SSDEBUGPS.dll nel computer SQL Server 2005  
  
1.  Copiare il file nella directory con lo stesso nome e percorso sul [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] macchina.  
  
2.  Effettuare la registrazione aprendo una **prompt dei comandi**ed eseguendo il comando seguente:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



