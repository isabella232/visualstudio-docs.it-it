---
title: "Errore: non si dispone dell'autorizzazione per controllare l'identità&#39;del processo | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: cad229f80676c3d1f7a7d23ad7a29729c834929b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736226"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Errore: non si dispone dell'autorizzazione per controllare l'identità&#39;del processo
Non si dispone dell'autorizzazione necessaria per controllare l'identità del processo. Probabilmente l'errore è causato dalla configurazione del sistema.

 Il debugger non è stato in grado di controllare l'identità del processo, un'informazione necessaria per l'esecuzione del debug. Probabilmente Servizi terminal è disabilitato. Per impostazione predefinita, questo servizio è attivato. Per riattivarlo, eseguire la procedura seguente.

### <a name="to-enable-terminal-services"></a>Per attivare Servizi terminal

1. Fare clic su **Start**, quindi scegliere **Pannello di controllo**.

2. Nel Pannello di controllo scegliere **Passa alla visualizzazione classica**, se necessario, quindi fare doppio clic su **Strumenti di amministrazione**.

3. Nella finestra **Strumenti di amministrazione** fare doppio clic su **Gestione computer**.

4. Nella finestra di Gestione computer espandere il nodo **Servizi e applicazioni**.

5. In **Servizi e applicazioni** fare clic su **Servizi**.

     Nel riquadro di destra verrà visualizzato un elenco di servizi.

6. Nell'elenco **Servizi** fare clic con il pulsante destro del mouse su **Servizi terminal** e quindi scegliere **Proprietà**.

7. Nella finestra **Proprietà Servizi terminal** passare alla scheda **generale** e impostare **tipo di avvio** su **manuale**.

8. Fare clic su **OK**.

9. Riavviare il computer.

     Con questa procedura non si attiva automaticamente Desktop remoto. Se si desidera attivare Desktop remoto nel computer in uso, eseguire la procedura aggiuntiva seguente.

### <a name="to-enable-remote-desktop"></a>Per attivare Desktop remoto

1. Fare clic su **Start** e quindi fare clic con il pulsante destro del mouse su **Risorse del computer**.

2. Scegliere **Proprietà**.

     Verrà visualizzata la finestra **Proprietà del sistema**.

3. Fare clic su **Connessione remota**.

4. In **Desktop remoto** selezionare **Consenti agli utenti di connettersi in remoto al computer**.

5. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)