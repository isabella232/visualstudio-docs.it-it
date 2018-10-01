---
title: "Errore: Impossibile eseguire automaticamente all'interno del Server | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d75ed4ddb42705b95a5ddd834596bc828e0f3ec2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517810"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Errore: impossibile eseguire automaticamente l'istruzione sul server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: Impossibile eseguire automaticamente passaggio nel Server](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-automatically-step-into-the-server).  
  
Il testo del messaggio di errore è il seguente:  
  
 Impossibile eseguire automaticamente l'istruzione sul server. Il debugger non ha ricevuto alcuna notifica prima dell'esecuzione della routine remota.  
  
 Questo errore può verificarsi quando si tenta di eseguire un servizio Web. Per altre informazioni, vedere [Accesso a un servizio Web XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764). L'errore è dovuto a una configurazione non corretta di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 Possibili cause:  
  
-   Il file Web. config per il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dell'applicazione non viene impostato il debug su "true" (vedere [modalità Debug nelle applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Una versione di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è stato installato dopo l'installazione di Visual Studio. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] deve essere installato prima di Visual Studio. Per risolvere il problema, accedere al **Pannello di controllo**di Windows e scegliere **Programmi e funzionalità** per ripristinare l'installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)



