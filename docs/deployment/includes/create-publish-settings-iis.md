
1. Chiudere e riaprire la Console di gestione IIS per visualizzare le opzioni di configurazione aggiornate nell'interfaccia utente.

1. In IIS, fare doppio clic sui **sito Web predefinito**, scegliere **Distribuisci** > **configurare distribuire pubblicazione sul Web**.

    ![Configurazione di distribuzione Web](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. Nel **configurare la distribuzione di pubblicazione sul Web** dialogo casella, esaminare le impostazioni.

1. Fare clic su **installazione**.

    Nel **risultati** pannello, l'output indica che i diritti di accesso viene concesse all'utente specificato e che un file con un *con estensione publishsettings* estensione di file è stato generato nel percorso indicato nella finestra di dialogo finestra di.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    A seconda della configurazione di Windows Server e IIS, vedrai valori diversi nel file XML. Di seguito sono riportati alcuni dettagli sui valori visualizzati:

    * Il *MSDeploy. axd* file cui fa riferimento il `publishUrl` attributo è un file di gestore HTTP generato dinamicamente per distribuzione Web. (Per i test `http://myhostname:8172` opererà nonché.)
    * Il `publishUrl` porta è impostata su porta 8172, ovvero l'impostazione predefinita per la distribuzione Web.
    * Il `destinationAppUrl` porta è impostata sulla porta 80, ovvero il valore predefinito per IIS.
    * Se non si riesce a connettersi all'host remoto in Visual Studio usando il nome host (nei passaggi successivi), verificare l'indirizzo IP al posto del nome host.

    > [!NOTE]
    > Se esegue la pubblicazione in IIS in esecuzione in una macchina virtuale di Azure, è necessario aprire le porte IIS e distribuzione Web nel gruppo di sicurezza di rete. Per informazioni dettagliate, vedere [installare ed eseguire IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copiare questo file nel computer in cui si esegue Visual Studio.
