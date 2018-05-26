La funzionalità distribuzione Web 3.6 per i server di Hosting fornisce le funzionalità di configurazione aggiuntive che consentono la creazione del file di impostazioni di pubblicazione dall'interfaccia utente.

1. Se si dispone di 3,6 distribuire Web già installato in Windows Server, disinstallare l'estensione usando **Pannello di controllo** > **programmi** > **Disinstalla un programma**.

1. Installare quindi 3.6 distribuzione Web per i server di Hosting in Windows Server.

    Per installare distribuzione Web per i server di Hosting, usare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Per trovare il collegamento di installazione guidata piattaforma Web da IIS, selezionare **IIS** nel riquadro sinistro di Server Manager. Il server e scegliere **Gestione Internet Information Services (IIS)**.)

    Durante l'installazione guidata piattaforma Web, l'utente scoprire **distribuzione Web per i server che ospita** nella scheda applicazioni.

1. Se non è stato già installato **gli strumenti e script di gestione IIS**, installarlo ora.

    Passare a **Selezione ruoli server** > **Server Web (IIS)** > **gli strumenti di gestione**, quindi selezionare il **script di gestione IIS e gli strumenti** ruolo, fare clic su **successivo**e quindi installare il ruolo.

    ![Installare gli strumenti e script di gestione IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Gli script e strumenti sono necessarie per consentire la generazione del file di impostazioni di pubblicazione.

1. (Facoltativo) Verificare che distribuzione Web è in esecuzione correttamente aprendo **Pannello di controllo > sistema e sicurezza > Strumenti di amministrazione > servizi** e verificare che **servizio agente distribuzione Web** è in esecuzione (la nome del servizio è diverso nelle versioni precedenti).

    Se il servizio dell'agente non è in esecuzione, avviarlo. Se non è presente in tutti, passare a **Pannello di controllo > programmi > Disinstalla un programma**, trovare **Microsoft Web Deploy <version>** . Scegliere di **modifica** l'installazione e assicurarsi di scegliere **verrà installata sul disco rigido locale** per i componenti di distribuzione Web. Completare i passaggi di installazione di modifica.