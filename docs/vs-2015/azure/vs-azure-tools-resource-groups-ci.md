---
title: Integrazione continua in servizi di Azure DevOps con i progetti di gruppo di risorse di Azure | Microsoft Docs
description: Viene descritto come configurare l'integrazione continua in servizi di Azure DevOps con i progetti di distribuzione gruppo di risorse di Azure in Visual Studio.
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: f6404b15e8a7cd3f95ac63bbae6076ef62fcff06
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003010"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Integrazione continua in servizi di DevOps di Azure con i progetti di distribuzione gruppo di risorse di Azure
Per distribuire un modello di Azure, eseguire attività nelle varie fasi: compilazione, Test, copia in Azure (detta anche "Staging") e distribuire il modello. Esistono due modi diversi per distribuire i modelli di servizi di Azure DevOps. Entrambi i metodi forniscono gli stessi risultati, quindi scegliere quello che meglio si adatta il flusso di lavoro.

1. Aggiungere un unico passaggio alla pipeline di compilazione che esegue lo script di PowerShell incluso nel progetto di distribuzione gruppo di risorse di Azure (Deploy-AzureResourceGroup.ps1). Lo script copia gli elementi e quindi distribuisce il modello.
2. Aggiungere che più servizi di Azure DevOps istruzioni di compilazione, ognuna delle quali esegue un'attività della fase.

Questo articolo illustra entrambe le opzioni. La prima opzione ha il vantaggio di usare lo stesso script usato dagli sviluppatori in Visual Studio e fornire coerenza durante tutto il ciclo di vita. La seconda opzione offre una comoda alternativa allo script predefinito. Entrambe le procedure presuppongono che sia già un progetto di distribuzione di Visual Studio archiviato in servizi di Azure DevOps.

## <a name="copy-artifacts-to-azure"></a>Copiare gli elementi in Azure
Indipendentemente dallo scenario, se sono disponibili elementi necessari per la distribuzione del modello, è necessario concedere l'accesso di Azure Resource Manager a tali elementi. Questi elementi possono includere file, ad esempio:

* Modelli annidati
* Gli script di configurazione e gli script DSC
* File binari dell'applicazione

### <a name="nested-templates-and-configuration-scripts"></a>I modelli annidati e script di configurazione
Quando si usano i modelli forniti da Visual Studio (o compilati con frammenti di Visual Studio), lo script di PowerShell non solo Prepara gli elementi, Parametrizza anche l'URI per le risorse per distribuzioni diverse. Lo script quindi copia gli elementi in un contenitore protetto in Azure, crea un token di firma di accesso condiviso per tale contenitore e quindi passa le informazioni alla distribuzione del modello. Visualizzare [creare una distribuzione modello](https://msdn.microsoft.com/library/azure/dn790564.aspx) per altre informazioni sui modelli annidati.  Quando si usano le attività in servizi di Azure DevOps, è necessario selezionare le attività appropriate per la distribuzione del modello e se necessario, passare i valori dei parametri dal passaggio di gestione temporanea alla distribuzione del modello.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Impostare la distribuzione continua nelle pipeline di Azure
Per chiamare lo script di PowerShell nelle pipeline di Azure, è necessario aggiornare la pipeline di compilazione. In breve, i passaggi sono: 

1. Modificare la pipeline di compilazione.
2. Consente di impostare l'autorizzazione di Azure nelle pipeline di Azure.
3. Aggiungere un'istruzione di compilazione di Azure PowerShell che fa riferimento lo script di PowerShell nel progetto di distribuzione gruppo di risorse di Azure.
4. Impostare il valore della *- ArtifactsStagingDirectory* parametro per lavorare con un progetto compilato nelle pipeline di Azure.

### <a name="detailed-walkthrough-for-option-1"></a>Procedura dettagliata per l'opzione 1
Le procedure seguenti consentono di eseguire i passaggi necessari per configurare la distribuzione continua in servizi di DevOps di Azure con una singola attività che esegue lo script di PowerShell nel progetto. 

1. Modificare la pipeline di compilazione di servizi di Azure DevOps e aggiungere un'istruzione di compilazione di Azure PowerShell. Scegliere la pipeline di compilazione nel **compilare le pipeline** categoria e quindi scegliere il **modificare** collegamento.
   
   ![Modificare la pipeline di compilazione][0]
2. Aggiungere un nuovo **Azure PowerShell** compilare passaggio alla pipeline di compilazione e quindi scegliere il **Aggiungi istruzione di compilazione...** immagini (...).
   
   ![Aggiungi istruzione di compilazione][1]
3. Scegliere il **attività di distribuzione** categoria, seleziona la **Azure PowerShell** attività e quindi scegliere relativo **Add** pulsante.
   
   ![Aggiungi attività][2]
4. Scegliere il **Azure PowerShell** istruzione di compilazione e quindi compilare i relativi valori.
   
   1. Se si dispone già di un endpoint di servizio di Azure aggiunto a servizi di Azure DevOps, scegliere la sottoscrizione nel **sottoscrizione di Azure** casella di riepilogo a discesa e quindi passare alla sezione successiva. 
      
      Se non si dispone di un endpoint di servizio di Azure in servizi di Azure DevOps, è necessario aggiungerne uno. In questa sottosezione illustra il processo. Se l'account Azure Usa un account Microsoft (ad esempio Hotmail), è necessario eseguire i passaggi seguenti per ottenere un'autenticazione dell'entità servizio.

   2. Scegliere il **Manage** collegamento accanto al **sottoscrizione Azure** casella di riepilogo a discesa.
      
      ![Gestire le sottoscrizioni di Azure][3]
   3. Scegli **Azure** nel **nuovo Endpoint del servizio** casella di riepilogo a discesa.
      
      ![Nuovo endpoint del servizio][4]
   4. Nel **Aggiungi sottoscrizione di Azure** finestra di dialogo, seleziona la **dell'entità servizio** opzione.
      
      ![Opzione dell'entità servizio][5]
   5. Aggiungere le informazioni sulla sottoscrizione di Azure per il **Aggiungi sottoscrizione di Azure** nella finestra di dialogo. È necessario specificare gli elementi seguenti:
      
      * Id della sottoscrizione
      * Nome della sottoscrizione
      * Id dell'entità servizio
      * Chiave dell'entità servizio
      * Id del tenant
   6. Aggiungere un nome di propria scelta per il **sottoscrizione** casella nome. Questo valore verrà visualizzato in un secondo momento nel **sottoscrizione di Azure** elenco a discesa in servizi di Azure DevOps. 

   7. Se non si conosce l'ID sottoscrizione di Azure, è possibile usare uno dei comandi seguenti per recuperarlo.
      
      Per gli script di PowerShell, usare:
      
      `Get-AzureRmSubscription`
      
      Riga di comando di Azure, usare:
      
      `azure account show`
   8. Per ottenere un ID del Tenant, ID entità servizio e chiave dell'entità servizio, seguire la procedura nel [applicazione creare Active Directory e un'entità servizio tramite portale](/azure/azure-resource-manager/resource-group-create-service-principal-portal) o [autenticazione di un'entità servizio con Azure Resource Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Aggiungere i valori di ID entità servizio, chiave dell'entità servizio e ID Tenant per il **Aggiungi sottoscrizione di Azure** finestra di dialogo e quindi selezionare la **OK** pulsante.
      
      È ora disponibile un'entità servizio valida da usare per eseguire lo script Azure PowerShell.
5. Modificare la pipeline di compilazione e scegliere il **Azure PowerShell** istruzione di compilazione. Selezionare la sottoscrizione nel **sottoscrizione di Azure** casella di riepilogo a discesa. (Se la sottoscrizione non viene visualizzata, scegliere il **Refresh** sul pulsante accanto il **Gestisci** collegamento.) 
   
   ![Configurare attività di compilazione di Azure PowerShell][8]
6. Specificare un percorso per lo script di PowerShell Deploy-AzureResourceGroup.ps1. A tale scopo, scegliere il pulsante con puntini di sospensione (...) accanto al **percorso dello Script** passare allo script di PowerShell Deploy-AzureResourceGroup.ps1 nella **script** cartella del progetto, selezionarla e quindi Scegliere il **OK** pulsante.    
   
   ![Seleziona percorso dello script][9]
7. Dopo aver selezionato lo script, aggiornare il percorso allo script in modo che venga eseguito da build. stagingdirectory (nella stessa directory che *ArtifactsLocation* è impostato su). Questo scopo, è possibile aggiungere "$(Build.StagingDirectory)/"all'inizio del percorso dello script.
   
    ![Modificare il percorso dello script][10]
8. Nel **argomenti dello Script** immettere i parametri seguenti (in una singola riga). Quando si esegue lo script in Visual Studio, è possibile vedere come vengono usati i parametri in di **Output** finestra. È possibile usare come punto di partenza per impostare i valori dei parametri nell'istruzione di compilazione.
   
   | Parametro | Descrizione |
   | --- | --- |
   | -ResourceGroupLocation |Il valore di posizione geografica in cui si trova, ad esempio il gruppo di risorse **Stati Uniti orientali** oppure **'East US'**. (Aggiungere le virgolette singole se è presente uno spazio nel nome). Visualizzare [aree di Azure](https://azure.microsoft.com/regions/) per altre informazioni. |
   | -ResourceGroupName |Il nome del gruppo di risorse usato per la distribuzione. |
   | -UploadArtifacts |Questo parametro, se presente, specifica che gli elementi devono essere caricati in Azure dal sistema locale. È sufficiente impostare questa opzione se la distribuzione del modello richiede elementi aggiuntivi che si prevede di preparare usando lo script di PowerShell (ad esempio gli script di configurazione o modelli annidati). |
   | -StorageAccountName |Il nome dell'account di archiviazione usati per gli artefatti di fase per la distribuzione. Questo parametro viene utilizzato solo se si decide di elementi per la distribuzione. Se questo parametro viene specificato, viene creato un nuovo account di archiviazione se lo script non ha creato uno durante una distribuzione precedente. Se il parametro è specificato, l'account di archiviazione deve esistere già. |
   | -StorageAccountResourceGroupName |Il nome del gruppo di risorse associato all'account di archiviazione. Questo parametro è obbligatorio solo se si specifica un valore per il parametro StorageAccountName. |
   | -TemplateFile |Il percorso del file modello nel progetto di distribuzione gruppo di risorse di Azure. Per migliorare la flessibilità, usare un percorso per questo parametro è relativo alla posizione dello script PowerShell anziché un percorso assoluto. |
   | -TemplateParametersFile |Il percorso del file di parametri nel progetto di distribuzione gruppo di risorse di Azure. Per migliorare la flessibilità, usare un percorso per questo parametro è relativo alla posizione dello script PowerShell anziché un percorso assoluto. |
   | -ArtifactStagingDirectory |Questo parametro consente di script di PowerShell nella cartella da cui devono essere copiati i file binari del progetto. Questo valore sostituisce il valore predefinito utilizzato dallo script di PowerShell. Per usare servizi di Azure DevOps, impostare il valore su: - ArtifactStagingDirectory $(Build.StagingDirectory) |
   
   Ecco un esempio di argomenti di script (riga è interrotta per migliorare la leggibilità):
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   Quando hai finito, il **argomenti dello Script** finestra dovrebbe essere simile l'elenco seguente:
   
   ![Argomenti dello script][11]
9. Dopo aver aggiunto tutti gli elementi necessari per l'istruzione di compilazione di Azure PowerShell, scegliere il **coda** pulsante per compilare il progetto di compilazione. Il **compilazione** schermata mostra l'output dello script di PowerShell.

### <a name="detailed-walkthrough-for-option-2"></a>Procedura dettagliata per l'opzione 2
Le procedure seguenti consentono di eseguire i passaggi necessari per configurare la distribuzione continua in servizi di Azure DevOps usando le attività predefinite.

1. Modificare la pipeline di compilazione di servizi di Azure DevOps per aggiungere che due nuove istruzioni di compilazione. Scegliere la pipeline di compilazione con il **le definizioni di compilazione** categoria e quindi scegliere il **modificare** collegamento.
   
   ![Modifica definizione di compilazione][12]
2. Aggiungere le nuove istruzioni di compilazione per la pipeline di compilazione usando il **Aggiungi istruzione di compilazione...** immagini (...).
   
   ![Aggiungi istruzione di compilazione][13]
3. Scegliere il **Deploy** categoria attività, seleziona la **copia dei File di Azure** attività e quindi scegliere relativo **Add** pulsante.
   
   ![Aggiungere attività di copia dei File di Azure][14]
4. Scegliere il **distribuzione gruppo di risorse di Azure** attività e quindi scegliere relativo **Add** pulsante e quindi **Chiudi** il **catalogo delle attività**.
   
   ![Aggiungere attività distribuzione gruppo di risorse di Azure][15]
5. Scegliere il **copia dei File di Azure** compilare i relativi valori e delle attività.
   
   Se si dispone già di un endpoint di servizio di Azure aggiunto a servizi di Azure DevOps, scegliere la sottoscrizione nel **sottoscrizione di Azure** casella di riepilogo a discesa. Se non hai una sottoscrizione, vedere [Option 1](#detailed-walkthrough-for-option-1) per istruzioni sull'impostazione di una sottoscrizione in servizi di Azure DevOps.
   
   * Origine: immettere **$(Build.StagingDirectory)**
   * Tipo di connessione Azure: selezionare **Azure Resource Manager**
   * Sottoscrizione di Azure Resource Manager: selezionare la sottoscrizione per l'account di archiviazione da usare nel **sottoscrizione di Azure** casella di riepilogo a discesa. Se la sottoscrizione non viene visualizzata, scegliere il **Refresh** sul pulsante accanto il **Gestisci** collegamento.
   * Tipo di destinazione: selezionare **Blob di Azure**
   * Resource Manager Account di archiviazione: selezionare l'account di archiviazione da usare per la gestione temporanea degli elementi
   * Nome contenitore: immettere il nome del contenitore da usare per la gestione temporanea; è possibile utilizzare qualsiasi nome di contenitore valido, ma utilizzano uno dedicato per questa pipeline di compilazione
   
   Per i valori di output:
   
   * Immettere il contenitore di archiviazione URI - **artifactsLocation**
   * Token di firma di accesso condiviso contenitore di archiviazione - immettere **artifactsLocationSasToken**
   
   ![Configurare l'attività di copia dei File di Azure][16]
6. Scegliere il **distribuzione gruppo di risorse di Azure** istruzione di compilazione e quindi compilare i relativi valori.
   
   * Tipo di connessione Azure: selezionare **Azure Resource Manager**
   * Sottoscrizione di Azure Resource Manager: selezionare la sottoscrizione per la distribuzione nel **sottoscrizione di Azure** casella di riepilogo a discesa. In genere, questa sarà la stessa sottoscrizione usata nel passaggio precedente
   * Azione - selezionare **crea o Aggiorna gruppo di risorse**
   * Gruppo di risorse: selezionare un gruppo di risorse o immettere il nome del nuovo gruppo di risorse per la distribuzione
   * Posizione: selezionare la località del gruppo di risorse
   * Modello: immettere il percorso e nome del modello da distribuire anteponendo **$(Build.StagingDirectory)**, ad esempio: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Parametri di modello: immettere il percorso e nome dei parametri da usare, anteponendo **$(Build.StagingDirectory)**, ad esempio: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Esegui override dei parametri di modello: immettere o copiare e incollare il codice seguente:
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Configurare l'attività distribuzione gruppo di risorse di Azure][17]
7. Dopo aver aggiunto tutti gli elementi richiesti, salvare la pipeline di compilazione e scegliere **Accoda nuova compilazione** nella parte superiore.

## <a name="next-steps"></a>Passaggi successivi
Lettura [Panoramica di Azure Resource Manager](/azure-resource-manager/resource-group-overview.md) per altre informazioni su Azure Resource Manager e i gruppi di risorse di Azure.

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
