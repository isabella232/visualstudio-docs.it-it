---
title: "Errore: Impossibile eseguire automaticamente all'interno del Server | Microsoft Docs"
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fca696fe9afc979d6775c5b2e97eebb5d82c266c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747823"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Errore: impossibile eseguire automaticamente l'istruzione sul server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il testo del messaggio di errore è il seguente:  
  
 Impossibile eseguire automaticamente l'istruzione sul server. Il debugger non ha ricevuto alcuna notifica prima dell'esecuzione della routine remota.  
  
 Questo errore può verificarsi quando si tenta di eseguire un servizio Web. Per altre informazioni, vedere [Accesso a un servizio Web XML](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764). L'errore è dovuto a una configurazione non corretta di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
 Possibili cause:  
  
-   Nel file web.config dell'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] non viene impostato il debug su "true" (vedere [Modalità debug nelle applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Una versione di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è stata installata dopo l'installazione di Visual Studio. Installare[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] prima di Visual Studio. Per risolvere il problema, accedere al **Pannello di controllo**di Windows e scegliere **Programmi e funzionalità** per ripristinare l'installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



