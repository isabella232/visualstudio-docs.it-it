
1. Nel computer in cui è aperto il progetto ASP.NET in Visual Studio, fare clic sul progetto in Esplora soluzioni e scegliere **pubblica**.

1. Se in precedenza è stato configurato alcun profilo di pubblicazione, il **pubblica** viene visualizzato il riquadro. Fare clic su **Crea nuovo profilo**.

1. Nel **selezionare una destinazione di pubblicazione** finestra di dialogo, fare clic su **Importa profilo**.

    ![Scegliere Pubblica](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Passare al percorso del file delle impostazioni pubblica che è stato creato nella sezione precedente.

1. Nel **Importa i File di impostazioni di pubblicazione** la finestra di dialogo, passare a e selezionare il profilo che è stato creato nella sezione precedente, fare clic su **Apri**.

    Visual Studio avvia il processo di distribuzione e nella finestra di Output viene visualizzato lo stato di avanzamento e risultati.

    Se si verificano una distribuzione di eventuali errori, fare clic su **impostazioni** per modificare le impostazioni. Modificare le impostazioni e fare clic su **Validate** per testare le nuove impostazioni. Se il nome host non viene trovato, provare l'indirizzo IP anziché il nome host nel **Server** e **URL di destinazione** campi.

    ![Modificare le impostazioni nello strumento di pubblicazione](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
