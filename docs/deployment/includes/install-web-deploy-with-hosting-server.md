---
ms.openlocfilehash: 09f6e03fa38c8f953ea5d70aedf81cd09c065a08
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397867"
---
Distribuzione Web 3.6 per server di hosting offre funzionalità di configurazione aggiuntive che consentono la creazione del file di impostazioni di pubblicazione dall'interfaccia utente.

L'Installazione guidata piattaforma Web per IIS consente l'installazione della versione 3.6, non 4.0, quindi è la versione consigliata in questo articolo.

1. Se è già Distribuzione Web installato in Windows Server, disinstallarlo usando Pannello di controllo  >    >  **Programmi Disinstalla programma**.

2. Installare quindi Distribuzione Web 3.6 per server di hosting in Windows Server.

    Per installare Distribuzione Web per server di hosting, usare Installazione guidata piattaforma Web (WebPI). Per trovare il collegamento di Installazione guidata piattaforma Web da IIS, selezionare **IIS** nel riquadro sinistro di Server Manager. Nel riquadro del server fare clic con il pulsante destro del mouse sul server **e scegliere Gestione Internet Information Services (IIS).** Usare quindi il **collegamento Get New Web Platform Components** (Ottieni nuovi componenti della piattaforma Web) nella finestra Actions **(Azioni).** È anche possibile ottenere l'Installazione installazione piattaforma Web (WebPI) dai [download di](https://www.microsoft.com/web/downloads/platform.aspx).

    In Installazione installazione piattaforma Web è possibile trovare **Distribuzione Web 3.6 per** i server di hosting nella scheda Applicazioni.

3. Installare **Strumenti e script di gestione IIS**, se non lo si è ancora fatto.

    Passare a **Selezione ruoli server** Strumenti di gestione Server Web  >  **(IIS),** selezionare il ruolo Strumenti e script di gestione IIS, fare clic su  >   **Avanti** e quindi installare  il ruolo.

    ![Installare Strumenti e script di gestione IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Gli script e gli strumenti sono necessari per consentire la generazione del file delle impostazioni di pubblicazione.

4. (Facoltativo) Verificare che Distribuzione Web funzioni correttamente aprendo strumenti di amministrazione di Pannello di controllo > Sistema e sicurezza  **> > Services** e quindi verificare che:

    * **Il Deployment Agent Web è** in esecuzione (il nome del servizio è diverso nelle versioni precedenti).

    * **Il servizio di gestione Web** è in esecuzione.

    Se uno dei servizi agente non è in esecuzione, riavviare il **servizio Deployment Agent Web**.

    Se il servizio Web Deployment Agent non è presente, passare a Programmi Pannello di controllo > > **Disinstallare** un programma , trovare **Microsoft Distribuzione Web \<version>**. Scegliere di **modificare** l'installazione e assicurarsi di scegliere **Installazione su disco rigido locale** per i componenti di Distribuzione Web. Completare la procedura di modifica dell'installazione di modifica.