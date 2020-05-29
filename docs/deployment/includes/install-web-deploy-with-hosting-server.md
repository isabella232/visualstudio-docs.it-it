---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173883"
---
Distribuzione Web 3.6 per server di hosting offre funzionalità di configurazione aggiuntive che consentono la creazione del file di impostazioni di pubblicazione dall'interfaccia utente.

1. Se si dispone di distribuzione Web 3,6 già installato in Windows Server, disinstallarlo utilizzando programmi del **Pannello di controllo**  >  **Programs**  >  **Disinstalla un programma**.

2. Installare quindi Distribuzione Web 3.6 per server di hosting in Windows Server.

    Per installare Distribuzione Web per server di hosting, usare Installazione guidata piattaforma Web (WebPI). Per trovare il collegamento di Installazione guidata piattaforma Web da IIS, selezionare **IIS** nel riquadro sinistro di Server Manager. Nel riquadro Server fare clic con il pulsante destro del mouse sul server e scegliere **gestione Internet Information Services (IIS)**. Usare quindi il collegamento **ottenere nuovi componenti della piattaforma Web** nella finestra **azioni** . È anche possibile ottenere l'installazione guidata piattaforma Web (WebPI) dai [download](https://www.microsoft.com/web/downloads/platform.aspx).

    Nell'installazione guidata piattaforma Web è possibile trovare **Distribuzione Web 3,6 per ospitare i server** nella scheda applicazioni.

3. Installare **Strumenti e script di gestione IIS**, se non lo si è ancora fatto.

    Passare a **Selezione ruoli server**server  >  **Web (IIS)**  >  **strumenti di gestione**, quindi selezionare il ruolo **strumenti e script di gestione IIS** , fare clic su **Avanti**, quindi installare il ruolo.

    ![Installare Strumenti e script di gestione IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Gli script e gli strumenti sono necessari per consentire la generazione del file delle impostazioni di pubblicazione.

4. (Facoltativo) Verificare che Distribuzione Web sia correttamente in esecuzione. A tale scopo, aprire **Pannello di controllo > Sistema e sicurezza > Strumenti di amministrazione > Servizi** e assicurarsi che il **Servizio Agente distribuzione Web** sia in esecuzione (il nome del servizio è diverso nelle versioni precedenti).

    Se il servizio agente non è in esecuzione, avviarlo. Se non è presente, passare a **Pannello di controllo > Programmi > Disinstalla un programma** e trovare **Distribuzione Web di Microsoft\<version>**. Scegliere di **modificare** l'installazione e assicurarsi di scegliere **Installazione su disco rigido locale** per i componenti di Distribuzione Web. Completare la procedura di modifica dell'installazione di modifica.