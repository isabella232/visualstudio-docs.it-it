---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292132"
---
Distribuzione Web 3.6 per server di hosting offre funzionalità di configurazione aggiuntive che consentono la creazione del file di impostazioni di pubblicazione dall'interfaccia utente.

1. Se distribuzione Web già installato in Windows Server, disinstallarlo utilizzando programmi del **Pannello di controllo**  >  **Programs**  >  **Disinstalla un programma**.

2. Installare quindi Distribuzione Web 3.6 per server di hosting in Windows Server.

    Per installare Distribuzione Web per server di hosting, usare Installazione guidata piattaforma Web (WebPI). Per trovare il collegamento di Installazione guidata piattaforma Web da IIS, selezionare **IIS** nel riquadro sinistro di Server Manager. Nel riquadro Server fare clic con il pulsante destro del mouse sul server e scegliere **gestione Internet Information Services (IIS)**. Usare quindi il collegamento **ottenere nuovi componenti della piattaforma Web** nella finestra **azioni** . È anche possibile ottenere l'installazione guidata piattaforma Web (WebPI) dai [download](https://www.microsoft.com/web/downloads/platform.aspx).

    Nell'installazione guidata piattaforma Web è possibile trovare **Distribuzione Web 3,6 per ospitare i server** nella scheda applicazioni.

3. Installare **Strumenti e script di gestione IIS**, se non lo si è ancora fatto.

    Passare a **Selezione ruoli server**server  >  **Web (IIS)**  >  **strumenti di gestione**, quindi selezionare il ruolo **strumenti e script di gestione IIS** , fare clic su **Avanti**, quindi installare il ruolo.

    ![Installare Strumenti e script di gestione IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Gli script e gli strumenti sono necessari per consentire la generazione del file delle impostazioni di pubblicazione.

4. Opzionale Verificare che Distribuzione Web venga eseguito correttamente aprendo il **Pannello di controllo > sistema e sicurezza > strumenti di amministrazione > Servizi**, quindi verificare che:

    * Il **servizio Deployment Agent Web** è in esecuzione (il nome del servizio è diverso nelle versioni precedenti).

    * Il **servizio gestione Web** è in esecuzione.

    Se uno dei servizi dell'agente non è in esecuzione, riavviare il **servizio Web Deployment Agent**.

    Se il servizio Web Deployment Agent non è disponibile, passare a pannello di **controllo > programmi > Disinstalla un programma**, trova **distribuzione Web \<version> Microsoft **. Scegliere di **modificare** l'installazione e assicurarsi di scegliere **Installazione su disco rigido locale** per i componenti di Distribuzione Web. Completare la procedura di modifica dell'installazione di modifica.