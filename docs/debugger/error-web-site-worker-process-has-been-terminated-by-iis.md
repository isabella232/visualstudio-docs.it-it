---
title: 'Errore: Processo di lavoro del sito Web è stato terminato da IIS | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30cab8602690df47a6fba18c3bc738a53959f036
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946126"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Errore: Il processo di lavoro del sito Web è stato terminato da IIS
L'esecuzione del codice sul sito Web è stata interrotta dal debugger. Di conseguenza, Internet Information Services (IIS) presuppone che il processo di lavoro non risponda e lo termina.  
  
 Per continuare a eseguire il debug è necessario configurare IIS in modo che consenta al processo di lavoro di procedere. Questo messaggio di errore non viene visualizzato con le versioni di IIS precedenti a IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Per configurare IIS 7 in modo che consenta al processo di lavoro di procedere  
  
1. Aprire la finestra **Strumenti di amministrazione**.  
  
   1.  Fare clic su **Start**, quindi scegliere **Pannello di controllo**.  
  
   2.  Nel **Pannello di controllo** scegliere **Passa alla visualizzazione classica**, se necessario, quindi fare doppio clic su **Strumenti di amministrazione**.  
  
2. Nella finestra **Strumenti di amministrazione** fare doppio clic su **Gestione Internet Information Services (IIS)**.  
  
    Gestione IIS verrà aperto.  
  
3. Nel riquadro **Connessioni** espandere il nodo \<nome computer>, se necessario.  
  
4. Nel nodo \<nome computer> fare clic su **Pool di applicazioni**.  
  
5. Nell'elenco **Pool di applicazioni** fare clic con il pulsante destro del mouse sul nome del pool nel quale viene eseguita l'applicazione e quindi fare clic su **Impostazioni avanzate**.  
  
6. Nella finestra di dialogo **Impostazioni avanzate** individuare la sezione **Modello di processo** ed eseguire una delle seguenti azioni:  
  
   - Impostare **Ping abilitato** su **False**.  
  
   - Impostare **Tempo massimo di risposta ping** su un valore maggiore di 90 secondi.  
  
     L'impostazione di **Ping abilitato** su **False** interrompe il controllo da parte di IIS se il processo di lavoro è in esecuzione e lo mantiene attivo fino a quando il processo sottoposto a debug non viene interrotto manualmente. L'impostazione di **Tempo massimo di risposta ping** su un valore elevato consente a IIS di continuare il monitoraggio del processo di lavoro.  
  
7. Scegliere **OK** per chiudere la finestra di dialogo **Impostazioni avanzate**.  
  
8. Chiudere Gestione IIS e la finestra **Strumenti di amministrazione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)