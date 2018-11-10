---
title: Configurare i ruoli per un servizio cloud di Azure con Visual Studio | Microsoft Docs
description: Informazioni su come installare e configurare i ruoli per servizi cloud di Azure con Visual Studio.
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ce2259debb55c4792c2998f0e67df69dbc8cb7f9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003080"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Configurare i ruoli dei servizi cloud di Azure con Visual Studio
Un servizio cloud di Azure può avere uno o più lavoro o i ruoli web. Per ogni ruolo, è necessario definire come tale ruolo viene configurato e anche configurare la modalità di esecuzione del ruolo. Per altre informazioni sui ruoli in servizi cloud, vedere il video [Introduzione a servizi Cloud di Azure](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services). 

Le informazioni per il servizio cloud vengono archiviate nei file seguenti:

- **Servicedefinition. Csdef** -file di definizione del servizio definisce le impostazioni di runtime per il servizio cloud include i ruoli richiesti, endpoint e le dimensioni della macchina virtuale. Nessuno dei dati archiviati in `ServiceDefinition.csdef` può essere modificato durante l'esecuzione del ruolo.
- **ServiceConfiguration. cscfg** : file di configurazione del servizio configura il numero di istanze di un ruolo viene eseguito e i valori delle impostazioni definiti per un ruolo. I dati archiviati in `ServiceConfiguration.cscfg` possono essere modificati durante l'esecuzione del ruolo.

Per archiviare valori diversi per le impostazioni che controllano la modalità di esecuzione di un ruolo, è possibile definire più configurazioni del servizio. È possibile usare una configurazione del servizio diversa per ogni ambiente di distribuzione. Ad esempio, è possibile impostare la stringa di connessione di account di archiviazione per usare l'emulatore di archiviazione di Azure locale in una configurazione del servizio locale e creare un'altra configurazione del servizio per usare archiviazione di Azure nel cloud.

Quando si crea un servizio cloud di Azure in Visual Studio, due configurazioni del servizio vengono automaticamente create e aggiunti al progetto di Azure:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Configurare un servizio cloud di Azure
È possibile configurare un servizio cloud di Azure da Esplora soluzioni in Visual Studio, come illustrato nei passaggi seguenti:

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e, dal menu di scelta rapida, selezionare **proprietà**.
   
    ![Menu di scelta rapida progetto Esplora soluzioni](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Nella pagina delle proprietà del progetto, selezionare la **sviluppo** scheda. 

    ![Pagina delle proprietà di progetto - scheda sviluppo](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Nel **configurazione del servizio** elencare, selezionare il nome della configurazione del servizio che si desidera modificare. (Se si desidera apportare modifiche a tutte le configurazioni di servizio per questo ruolo, selezionare **tutte le configurazioni**.)
   
    > [!IMPORTANT]
    > Se si sceglie una configurazione del servizio specifica, alcune proprietà sono disabilitate perché può essere impostati solo per tutte le configurazioni. Per modificare queste proprietà, è necessario selezionare **tutte le configurazioni**.
    > 
    > 
   
    ![Elenco di configurazione del servizio per un servizio cloud di Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Modificare il numero di istanze del ruolo
Per migliorare le prestazioni del servizio cloud, è possibile modificare il numero di istanze di un ruolo in esecuzione, in base al numero di utenti o al carico previsto per un particolare ruolo. Una macchina virtuale separata viene creata per ogni istanza di un ruolo quando il servizio cloud in esecuzione in Azure. Ciò influirà sulla fatturazione per la distribuzione di questo servizio cloud. Per altre informazioni sulla fatturazione, vedere [comprendere la fattura per Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, espandere il nodo del progetto. Sotto il **ruoli** nodo, fare doppio clic il ruolo da aggiornare e, dal menu di scelta rapida, selezionare **proprietà**.

    ![Menu di scelta rapida ruolo Azure di Esplora soluzioni](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Selezionare il **configurazione** scheda.

    ![Scheda Configurazione](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Nel **configurazione del servizio** elencare, selezionare la configurazione del servizio che si desidera aggiornare.
   
    ![Elenco Configurazione servizio](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Nel **numero di istanze** testo casella, immettere il numero di istanze che si desidera avviare per questo ruolo. Ogni istanza viene eseguita su una macchina virtuale separata quando si pubblica il servizio cloud in Azure.

    ![Aggiornamento del conteggio istanze](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Da Visual Studio, sulla barra degli strumenti, seleziona **salvare**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Gestire le stringhe di connessione per gli account di archiviazione
È possibile aggiungere, rimuovere o modificare le stringhe di connessione per le configurazioni del servizio. Ad esempio, è possibile una stringa di connessione locale per una configurazione del servizio locale che ha un valore pari `UseDevelopmentStorage=true`. È anche possibile configurare una configurazione del servizio cloud che usa un account di archiviazione di Azure.

> [!WARNING]
> Quando si immettono le informazioni chiave account di archiviazione di Azure per una stringa di connessione di account di archiviazione, queste informazioni vengono archiviate in locale nel file di configurazione del servizio. Tuttavia, queste informazioni attualmente non archiviate come testo crittografato.
> 
> 

Utilizzando un valore diverso per ogni configurazione del servizio, non è necessario usare stringhe di connessione diverse nel servizio cloud o modificare il codice quando si pubblica il servizio cloud in Azure. È possibile usare lo stesso nome per la stringa di connessione nel codice e il valore sarà diverso in base alla configurazione del servizio selezionata quando si compila il servizio cloud o quando lo si pubblica.

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, espandere il nodo del progetto. Sotto il **ruoli** nodo, fare doppio clic il ruolo da aggiornare e, dal menu di scelta rapida, selezionare **proprietà**.

    ![Menu di scelta rapida ruolo Azure di Esplora soluzioni](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Selezionare il **impostazioni** scheda.

    ![Scheda Impostazioni](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Nel **configurazione del servizio** elencare, selezionare la configurazione del servizio che si desidera aggiornare.

    ![Configurazione del servizio](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Per aggiungere una stringa di connessione, selezionare **Aggiungi impostazione**.

    ![Aggiungere la stringa di connessione](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Dopo aver aggiunto la nuova impostazione all'elenco, aggiornare la riga nell'elenco con le informazioni necessarie.

    ![Nuova stringa di connessione](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nome** -immettere il nome che si desidera usare per la stringa di connessione.
    - **Tipo di** : selezionare questa opzione **stringa di connessione** nell'elenco a discesa.
    - **Valore** -è possibile immettere la stringa di connessione direttamente nella **valore** cella oppure selezionare i puntini di sospensione (...) per lavorare **crea stringa di connessione di archiviazione** finestra di dialogo.  

1. Nel **crea stringa di connessione di archiviazione** finestra di dialogo, selezionare un'opzione per **connettersi usando**. Seguire quindi le istruzioni per l'opzione selezionata:

    - **Emulatore di archiviazione di Microsoft Azure** -se si seleziona questa opzione, le impostazioni rimanenti nella finestra di dialogo sono disabilitate perché vengono applicati solo ad Azure. Scegliere **OK**.
    - **La sottoscrizione** : se si seleziona questa opzione, usare l'elenco a discesa per selezionare e accedere a un account Microsoft oppure aggiungere un account Microsoft. Selezionare un account di archiviazione e di sottoscrizione di Azure. Scegliere **OK**.
    - **Credenziali immesse manualmente** -immettere il nome di account di archiviazione e la chiave primaria o secondaria. Selezionare un'opzione per **connessione** (per la maggior parte degli scenari è consigliato HTTPS). Scegliere **OK**.

1. Per eliminare una stringa di connessione, selezionare la stringa di connessione e quindi selezionare **Rimuovi impostazione**.

1. Da Visual Studio, sulla barra degli strumenti, seleziona **salvare**.

## <a name="programmatically-access-a-connection-string"></a>Accedere a livello di codice a una stringa di connessione

La procedura seguente illustra come accedere a livello di codice a una stringa di connessione usando C#.

1. Aggiungere le seguenti direttive using un C# file in cui si intende usare l'impostazione:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Il codice seguente illustra un esempio di come accedere a una stringa di connessione. Sostituire il &lt;ConnectionStringName > segnaposto con il valore appropriato. 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Aggiungere impostazioni personalizzate da usare nel servizio cloud di Azure
Le impostazioni personalizzate nel file di configurazione del servizio consentono di aggiungere un nome e il valore di una stringa per una configurazione del servizio specifico. È possibile scegliere di utilizzare questa impostazione per configurare una funzionalità nel servizio cloud leggendo il valore dell'impostazione e utilizzando questo valore per controllare la logica nel codice. È possibile modificare questi valori di configurazione del servizio senza dovere ricompilare il pacchetto del servizio o quando è in esecuzione il servizio cloud. Il codice può cercare notifiche di quando viene modificata un'impostazione. Visualizzare [evento roleenvironment. Changing](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

È possibile aggiungere, rimuovere o modificare le impostazioni personalizzate per le configurazioni del servizio. È possibile valori diversi per queste stringhe per configurazioni del servizio diverse.

Utilizzando un valore diverso per ogni configurazione del servizio, non è necessario usare stringhe diverse nel servizio cloud o modificare il codice quando si pubblica il servizio cloud in Azure. È possibile usare lo stesso nome per la stringa nel codice e il valore sarà diverso in base alla configurazione del servizio selezionata quando si compila il servizio cloud o quando lo si pubblica.

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, espandere il nodo del progetto. Sotto il **ruoli** nodo, fare doppio clic il ruolo da aggiornare e, dal menu di scelta rapida, selezionare **proprietà**.

    ![Menu di scelta rapida ruolo Azure di Esplora soluzioni](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Selezionare il **impostazioni** scheda.

    ![Scheda Impostazioni](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Nel **configurazione del servizio** elencare, selezionare la configurazione del servizio che si desidera aggiornare.

    ![Elenco Configurazione servizio](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Per aggiungere un'impostazione personalizzata, selezionare **Aggiungi impostazione**.

    ![Aggiungere impostazioni personalizzate](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Dopo aver aggiunto la nuova impostazione all'elenco, aggiornare la riga nell'elenco con le informazioni necessarie.

    ![Nuova impostazione personalizzata](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Nome** -immettere il nome dell'impostazione.
    - **Tipo di** : selezionare questa opzione **stringa** nell'elenco a discesa.
    - **Valore** -immettere il valore dell'impostazione. È possibile immettere il valore direttamente nel **valore** delle celle o selezionare i puntini di sospensione (...) immettere il valore di **Modifica stringa** finestra di dialogo.  

1. Per eliminare un'impostazione personalizzata, selezionare l'impostazione e quindi selezionare **Rimuovi impostazione**.

1. Da Visual Studio, sulla barra degli strumenti, seleziona **salvare**.

## <a name="programmatically-access-a-custom-settings-value"></a>Accedere a livello di codice al valore dell'impostazione personalizzata
 
La procedura seguente illustra come accedere a livello di programmazione utilizzando un'impostazione personalizzata a C#.

1. Aggiungere le seguenti direttive using un C# file in cui si intende usare l'impostazione:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Il codice seguente illustra un esempio di come accedere a un'impostazione personalizzata. Sostituire il &lt;SettingName > segnaposto con il valore appropriato. 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Gestire l'archiviazione locale per ogni istanza del ruolo
È possibile aggiungere archiviazione di file locale del sistema per ogni istanza di un ruolo. I dati archiviati nella risorsa di archiviazione non è accessibile da altre istanze del ruolo per cui sono archiviati i dati o da altri ruoli.  

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, espandere il nodo del progetto. Sotto il **ruoli** nodo, fare doppio clic il ruolo da aggiornare e, dal menu di scelta rapida, selezionare **proprietà**.

    ![Menu di scelta rapida ruolo Azure di Esplora soluzioni](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Selezionare il **risorsa di archiviazione locale** scheda.

    ![Scheda archiviazione locale](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Nel **configurazione del servizio** elenco, assicurarsi che **tutte le configurazioni** selezionata come le impostazioni di archiviazione locale si applicano a tutte le configurazioni di servizio. Qualsiasi altro valore comporta in tutti i campi di input nella pagina di cui è stato disabilitato. 

    ![Elenco Configurazione servizio](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Per aggiungere una voce di risorsa di archiviazione locale, selezionare **Aggiungi risorsa di archiviazione locale**.

    ![Aggiungere spazio di archiviazione locale](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Dopo aver aggiunto la nuova voce di risorsa di archiviazione locale all'elenco, aggiornare la riga nell'elenco con le informazioni necessarie.

    ![Nuova risorsa di archiviazione locale](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Nome** -immettere il nome che si desidera utilizzare per la nuova risorsa di archiviazione locale.
    - **Dimensioni (MB)** -immettere la dimensione in MB necessaria per la nuova risorsa di archiviazione locale.
    - **Pulisci a riciclo ruolo** -selezionare questa opzione per rimuovere i dati nella nuova risorsa di archiviazione locale quando la macchina virtuale per il ruolo viene riciclata.

1. Per eliminare una voce di risorsa di archiviazione locale, selezionare la voce e quindi selezionare **Rimuovi risorsa di archiviazione locale**.

1. Da Visual Studio, sulla barra degli strumenti, seleziona **salvare**.

## <a name="programmatically-accessing-local-storage"></a>A livello di codice l'accesso all'archiviazione locale

Questa sezione illustra come accedere a livello di archiviazione locale usando C# scrivendo un file di testo test `MyLocalStorageTest.txt`.  

### <a name="write-a-text-file-to-local-storage"></a>Scrivere un file di testo nell'archivio locale

Il codice seguente illustra un esempio di come scrivere un file di testo nell'archivio locale. Sostituire il &lt;LocalStorageName > segnaposto con il valore appropriato. 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>Trovare un file scritto nell'archivio locale

Per visualizzare il file creato dal codice nella sezione precedente, seguire questa procedura:
    
1.  Nell'area di notifica Windows, fare doppio clic sull'icona di Azure e, dal menu di scelta rapida, selezionare **Mostra interfaccia emulatore di calcolo**. 

    ![Mostra emulatore di calcolo di Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Selezionare il ruolo web.

    ![Emulatore di calcolo di Azure](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Nel **emulatore di calcolo di Microsoft Azure** dal menu **Tools** > **Apri archivio locale**.

    ![Voce di menu Apri archivio locale](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Quando si apre la finestra di Windows Explorer, immettere "mylocalstoragetest. txt ' nel **ricerca** casella di testo e selezionare **invio** per avviare la ricerca. 

## <a name="next-steps"></a>Passaggi successivi
Altre informazioni sui progetti Azure in Visual Studio, vedere [configurazione di un progetto Azure](vs-azure-tools-configuring-an-azure-project.md). Altre informazioni sullo schema del servizio cloud leggendo [riferimenti allo Schema](https://msdn.microsoft.com/library/azure/dd179398).

