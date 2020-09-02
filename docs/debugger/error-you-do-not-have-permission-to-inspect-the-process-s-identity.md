---
title: "Errore: non si dispone dell'autorizzazione per controllare l'identità del processo &apos; | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: e91745b8910a9e87ccd4a22fe09c6764a2ab4c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706529"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Errore: non si dispone dell'autorizzazione per controllare l'identità del processo&#39;s
Non si dispone dell'autorizzazione necessaria per controllare l'identità del processo. Probabilmente l'errore è causato dalla configurazione del sistema.

 Il debugger non è stato in grado di controllare l'identità del processo, un'informazione necessaria per l'esecuzione del debug. Probabilmente Servizi terminal è disabilitato. Per impostazione predefinita, questo servizio è attivato. Per riattivarlo, eseguire la procedura seguente.

### <a name="to-enable-terminal-services"></a>Per attivare Servizi terminal

1. Fare clic su **Start** , quindi scegliere **Pannello di controllo**.

2. Nel pannello di controllo scegliere **passa alla visualizzazione classica**, se necessario, quindi fare doppio clic su **strumenti di amministrazione**.

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

3. Fare clic su **Remoto**.

4. In **Desktop remoto** selezionare **Consenti agli utenti di connettersi in remoto al computer**.

5. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)