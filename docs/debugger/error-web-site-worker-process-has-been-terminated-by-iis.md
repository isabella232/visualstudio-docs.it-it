---
title: 'Errore: il processo di lavoro di sito Web è stato terminato da IIS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 582cf1b5faf0cc62d85e17544aa03c4ede4ab0a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852843"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Errore: il processo di lavoro del sito Web è stato terminato da IIS
L'esecuzione del codice sul sito Web è stata interrotta dal debugger. Di conseguenza, Internet Information Services (IIS) presuppone che il processo di lavoro non risponda e lo termina.  
  
 Per continuare a eseguire il debug è necessario configurare IIS in modo che consenta al processo di lavoro di procedere. Questo messaggio di errore non viene visualizzato con le versioni di IIS precedenti a IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Per configurare IIS 7 in modo che consenta al processo di lavoro di procedere  
  
1. Aprire il **strumenti di amministrazione** finestra.  
  
   1.  Fare clic su **avviare**, quindi scegliere **Pannello di controllo**.  
  
   2.  Nelle **Pannello di controllo**, scegliere **passare alla visualizzazione classica**, se necessario e quindi fare doppio clic su **strumenti di amministrazione**.  
  
2. Nel **strumenti di amministrazione** finestra, fare doppio clic su **Internet Information Services (IIS) Manager**.  
  
    Gestione IIS verrà aperto.  
  
3. Nel **connessioni** riquadro, espandere il \<nome computer > nodo se necessario.  
  
4. Sotto il \<nome computer > nodo, fare clic su **pool di applicazioni**.  
  
5. Nel **pool di applicazioni** elenco, fare doppio clic il nome del pool in cui viene eseguita l'applicazione e quindi fare clic su **impostazioni avanzate**.  
  
6. Nel **impostazioni avanzate** finestra di dialogo individuare il **modello di processo** sezione ed eseguire una delle azioni seguenti:  
  
   - Impostare **Ping abilitato** al **False**.  
  
   - Impostare **massimo tempo di risposta Ping** su un valore maggiore di 90 secondi.  
  
     L'impostazione **Ping abilitato** al **False** arresta IIS dalla verifica se il processo di lavoro è ancora in esecuzione e lo mantiene attivo il processo di lavoro fino a quando non si arresta il processo sottoposto a debug. L'impostazione **massimo tempo di risposta Ping** su un valore elevato consente a IIS di continuare a monitorare il processo di lavoro.  
  
7. Fare clic su **OK** per chiudere la **impostazioni avanzate** nella finestra di dialogo.  
  
8. Chiudere Gestione IIS e il **strumenti di amministrazione** finestra.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)