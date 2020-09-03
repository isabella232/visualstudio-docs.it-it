---
ms.openlocfilehash: b8002d9e911c8d8c07a5aaf5286168e49a374a7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85292126"
---

1. Chiudere e riaprire la Console di gestione IIS per visualizzare le opzioni di configurazione aggiornate nell'interfaccia utente.

2. In IIS fare clic con il pulsante destro del mouse su **Sito Web predefinito**, quindi scegliere **Distribuisci** > **Abilita pubblicazione Distribuzione Web**.

    ![Impostare la configurazione Distribuzione Web](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   Se il menu **Distribuisci** non viene visualizzato, vedere la sezione precedente per verificare che distribuzione Web sia in esecuzione.

3. Nella finestra di dialogo **Abilita pubblicazione Distribuzione Web** esaminare le impostazioni.

4. Fare clic su **Setup**.

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
   * Se non si riesce a connettersi all'host remoto in Visual Studio usando il nome host (nei passaggi successivi), provare con l'indirizzo IP al posto del nome host.

     > [!NOTE]
     > Se si esegue la pubblicazione in IIS in esecuzione in una VM di Azure, è necessario aprire le porte Distribuzione Web e IIS nel gruppo Sicurezza di rete. Per informazioni dettagliate, vedere [Install and run IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server) (Installare ed eseguire IIS).

5. Copiare questo file nel computer in cui si esegue Visual Studio.
