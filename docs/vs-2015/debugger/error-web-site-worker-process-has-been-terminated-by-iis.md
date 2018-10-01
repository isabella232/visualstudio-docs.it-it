---
title: 'Errore: il processo di lavoro di sito Web è stato terminato da IIS | Microsoft Docs'
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
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81396165841b0c23a317a857e73d7adbf88971dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530032"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Errore: il processo di lavoro del sito Web è stato terminato da IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errore: il processo di lavoro di sito Web è stato terminato da IIS](https://docs.microsoft.com/visualstudio/debugger/error-web-site-worker-process-has-been-terminated-by-iis).  
  
L'esecuzione del codice sul sito Web è stata interrotta dal debugger. Di conseguenza, Internet Information Services (IIS) presuppone che il processo di lavoro non risponda e lo termina.  
  
 Per continuare a eseguire il debug è necessario configurare IIS in modo che consenta al processo di lavoro di procedere. Questo messaggio di errore non viene visualizzato con le versioni di IIS precedenti a IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Per configurare IIS 7 in modo che consenta al processo di lavoro di procedere  
  
1.  Aprire il **strumenti di amministrazione** finestra.  
  
    1.  Fare clic su **avviare**, quindi scegliere **Pannello di controllo**.  
  
    2.  Nelle **Pannello di controllo**, scegliere **passare alla visualizzazione classica**, se necessario e quindi fare doppio clic su **strumenti di amministrazione**.  
  
2.  Nel **strumenti di amministrazione** finestra, fare doppio clic su **Internet Information Services (IIS) Manager**.  
  
     Gestione IIS verrà aperto.  
  
3.  Nel **connessioni** riquadro, espandere il \<nome computer > nodo se necessario.  
  
4.  Sotto il \<nome computer > nodo, fare clic su **pool di applicazioni**.  
  
5.  Nel **pool di applicazioni** elenco, fare doppio clic il nome del pool in cui viene eseguita l'applicazione e quindi fare clic su **impostazioni avanzate**.  
  
6.  Nel **impostazioni avanzate** finestra di dialogo individuare il **modello di processo** sezione ed eseguire una delle azioni seguenti:  
  
    -   Impostare **Ping abilitato** al **False**.  
  
    -   Impostare **massimo tempo di risposta Ping** su un valore maggiore di 90 secondi.  
  
     L'impostazione **Ping abilitato** al **False** arresta IIS dalla verifica se il processo di lavoro è ancora in esecuzione e lo mantiene attivo il processo di lavoro fino a quando non si arresta il processo sottoposto a debug. L'impostazione **massimo tempo di risposta Ping** su un valore elevato consente a IIS di continuare a monitorare il processo di lavoro.  
  
7.  Fare clic su **OK** per chiudere la **impostazioni avanzate** nella finestra di dialogo.  
  
8.  Chiudere Gestione IIS e il **strumenti di amministrazione** finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)



