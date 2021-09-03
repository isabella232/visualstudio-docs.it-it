---
ms.openlocfilehash: 6e9650a10a193947f11172d717481f8221a66ccf
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397869"
---

1. Chiudere e riaprire la Console di gestione IIS per visualizzare le opzioni di configurazione aggiornate nell'interfaccia utente.

2. In IIS fare clic con il pulsante destro del mouse su **Sito Web predefinito**, quindi scegliere **Distribuisci** > **Abilita pubblicazione Distribuzione Web**.

    ![Impostare la configurazione Distribuzione Web](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   Se il **menu** Distribuisci non è visualizzato, vedere la sezione precedente per verificare che Distribuzione Web sia in esecuzione.

3. Nella finestra di dialogo **Abilita pubblicazione Distribuzione Web** esaminare le impostazioni.

4. Fare clic su **Configura**.

    Nel riquadro **Risultati** l'output indica che i diritti di accesso vengono concessi all'utente specificato e che è stato generato un file con estensione *publishsettings* nella posizione indicata nella finestra di dialogo.

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

    A seconda della configurazione di Windows Server e IIS vengono visualizzati valori diversi nel file XML. Di seguito sono riportati alcuni dettagli sui valori visualizzati:

   * Il file *msdeploy.axd* al quale si fa riferimento nell'attributo `publishUrl` è un file gestore HTTP generato dinamicamente per Distribuzione Web. Ai fini dei test, in genere è possibile usare anche `http://myhostname:8172`.
   * La porta `publishUrl` è impostata sulla porta 8172, il valore predefinito per Distribuzione Web.
   * La porta `destinationAppUrl` è impostata sulla porta 80, il valore predefinito per IIS.
   * Se, nei passaggi successivi, non è possibile connettersi all'host remoto da Visual Studio usando il nome host, testare l'indirizzo IP del server al posto del nome host.

     > [!NOTE]
     > Se si esegue la pubblicazione in IIS in esecuzione in una macchina virtuale di Azure, è necessario aprire una porta in ingresso per Distribuzione Web e IIS nel gruppo Sicurezza di rete. Per informazioni dettagliate, vedere [Aprire porte a una macchina virtuale.](/azure/virtual-machines/windows/nsg-quickstart-portal)

5. Copiare questo file nel computer in cui si esegue Visual Studio.
