Distribuzione Web 3.6 per server di hosting offre funzionalità di configurazione aggiuntive che consentono la creazione del file di impostazioni di pubblicazione dall'interfaccia utente.

1. Se Distribuzione Web 3.6 è già installato in Windows Server, disinstallarlo usando **Pannello di controllo** > **Programmi** > **Disinstalla un programma**.

2. Installare quindi Distribuzione Web 3.6 per server di hosting in Windows Server.

    Per installare Distribuzione Web per server di hosting, usare [Installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Per trovare il collegamento di Installazione guidata piattaforma Web da IIS, selezionare **IIS** nel riquadro sinistro di Server Manager. Fare clic con il pulsante destro del mouse sul server e selezionare **Gestione Internet Information Services (IIS)**.

    In Installazione guidata piattaforma Web, **Distribuzione Web per server di hosting** è disponibile nella scheda Applicazioni.

3. Installare **Strumenti e script di gestione IIS**, se non lo si è ancora fatto.

    Passare a **Selezione ruoli server** > **Server Web (IIS)** > **Strumenti di gestione** e quindi selezionare il ruolo **Strumenti e script di gestione IIS**, fare clic su **Avanti** e quindi installare il ruolo.

    ![Installare Strumenti e script di gestione IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Gli script e gli strumenti sono necessari per consentire la generazione del file delle impostazioni di pubblicazione.

4. (Facoltativo) Verificare che Distribuzione Web sia correttamente in esecuzione. A tale scopo, aprire **Pannello di controllo > Sistema e sicurezza > Strumenti di amministrazione > Servizi** e assicurarsi che il **Servizio Agente distribuzione Web** sia in esecuzione (il nome del servizio è diverso nelle versioni precedenti).

    Se il servizio agente non è in esecuzione, avviarlo. Se non è presente, passare a **Pannello di controllo > Programmi > Disinstalla un programma** e trovare **Distribuzione Web di Microsoft<version>**. Scegliere di **modificare** l'installazione e assicurarsi di scegliere **Installazione su disco rigido locale** per i componenti di Distribuzione Web. Completare la procedura di modifica dell'installazione di modifica.