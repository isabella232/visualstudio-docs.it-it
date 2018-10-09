---
title: "Errore: Non si dispone dell'autorizzazione per controllare il processo di&#39;identità s | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4aafd6215c868ff93108e3b170999a8d028e2df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526061"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Errore: Non si dispone dell'autorizzazione per controllare il processo di&#39;identità s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [errori: non hai le autorizzazioni per controllare il processo di&#39;identità s](https://docs.microsoft.com/visualstudio/debugger/error-you-do-not-have-permission-to-inspect-the-process-s-identity).  
  
Non si dispone dell'autorizzazione necessaria per controllare l'identità del processo. Probabilmente l'errore è causato dalla configurazione del sistema.  
  
 Il debugger non è stato in grado di controllare l'identità del processo, un'informazione necessaria per l'esecuzione del debug. Probabilmente Servizi terminal è disabilitato. Per impostazione predefinita, questo servizio è attivato. Per riattivarlo, eseguire la procedura seguente.  
  
### <a name="to-enable-terminal-services"></a>Per attivare Servizi terminal  
  
1.  Fare clic su **avviare** e quindi scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo, scegliere **passa alla visualizzazione classica**, se necessario e quindi fare doppio clic su **strumenti di amministrazione**.  
  
3.  Nel **strumenti di amministrazione** finestra, fare doppio clic su **Gestione Computer**.  
  
4.  Nella finestra Gestione Computer espandere il **applicazioni e servizi** nodo.  
  
5.  Sotto il **applicazioni e servizi**, fare clic su **Services**.  
  
     Nel riquadro di destra verrà visualizzato un elenco di servizi.  
  
6.  Nel **Services** elenco, fare doppio clic su **servizi Terminal** e quindi scegliere **proprietà**.  
  
7.  Nel **proprietà servizi Terminal** finestra, passa al **generali** scheda e impostare **tipo di avvio** al **manuale**.  
  
8.  Fare clic su **OK**.  
  
9. Riavviare il computer.  
  
     Con questa procedura non si attiva automaticamente Desktop remoto. Se si desidera attivare Desktop remoto nel computer in uso, eseguire la procedura aggiuntiva seguente.  
  
### <a name="to-enable-remote-desktop"></a>Per attivare Desktop remoto  
  
1.  Fare clic su **avviare** e quindi fare doppio clic su **My Computer**.  
  
2.  Scegliere **Proprietà**.  
  
     Il **le proprietà di sistema** viene visualizzata la finestra.  
  
3.  Fare clic su **remota**.  
  
4.  Sotto **Desktop remoto**, selezionare **consentire agli utenti di connettersi in remoto al computer**.  
  
5.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)


