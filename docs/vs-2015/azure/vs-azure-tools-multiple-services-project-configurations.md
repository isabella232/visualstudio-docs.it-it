---
title: Configurazione del progetto Azure tramite più configurazioni del servizio | Microsoft Docs
description: Informazioni su come configurare un progetto di servizio cloud di Azure modificando i file servicedefinition. Csdef, Local. cscfg e ServiceConfiguration.
author: ghogen
manager: douge
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f309c2a960d011601a9fdd41e29d767c667de838
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002931"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Configurazione del progetto di Azure in Visual Studio per l'uso di più configurazioni del servizio

Un progetto di servizio cloud di Azure in Visual Studio include tre file di configurazione: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg`, e `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` viene distribuito in Azure per descrivere i requisiti del servizio cloud e i relativi ruoli e per fornire le impostazioni che si applicano a tutte le istanze. Le impostazioni possono essere letti in fase di esecuzione usando l'API di Runtime che ospita servizi di Azure. Questo file può essere aggiornato in Azure solo quando il servizio cloud viene arrestato.
- `ServiceConfiguration.Local.cscfg` e `ServiceConfiguration.Cloud.cscfg` forniscono i valori per le impostazioni nella definizione di file e specificare il numero di istanze da eseguire per ogni ruolo. Il file "Local" contiene valori usati nel debug locale; il file "Cloud" viene distribuito in Azure come `ServiceConfiguration.cscfg` e fornisce le impostazioni per l'ambiente server. Questo file può essere aggiornato mentre il servizio cloud è in esecuzione in Azure.

Le impostazioni di configurazione vengono gestite e modificate in Visual Studio usando le pagine delle proprietà per il ruolo applicabile (fare doppio clic il ruolo e selezionare **proprietà**, oppure fare doppio clic il ruolo). Le modifiche possono essere limitate a qualsiasi configurazione scelta nel **configurazione del servizio** elenco a discesa. Le proprietà dei ruoli web e di lavoro sono simili, ad eccezione di dove descritto nelle sezioni seguenti.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Per informazioni sugli schemi sottostanti per la definizione del servizio e i file di configurazione del servizio, vedere la [Schema XML. csdef](/azure/cloud-services/schema-csdef-file.md) e [Schema XML. cscfg](/azure/cloud-services/schema-cscfg-file.md) articoli. Per altre informazioni sulla configurazione del servizio, vedere [come configurare i servizi Cloud](/azure/cloud-services/cloud-services-how-to-configure-portal).


## <a name="configuration-page"></a>Pagina di configurazione

### <a name="service-configuration"></a>Configurazione del servizio

Consente di selezionare `ServiceConfiguration.*.cscfg` file è interessato dalle modifiche. Per impostazione predefinita, sono disponibili varianti Local e Cloud, ed è possibile usare il **Gestisci...**  comando per copiare, rinominare e rimuovere i file di configurazione. Questi file vengono aggiunti al progetto di servizio cloud e vengono visualizzati nella **Esplora soluzioni**. Tuttavia, la ridenominazione o la rimozione di configurazioni può essere eseguito solo da questo controllo.

### <a name="instances"></a>Istanze

Impostare il **istanza** count (proprietà) per il numero di istanze deve essere eseguito il servizio per questo ruolo.

Impostare il **dimensioni della macchina virtuale** proprietà **molto piccola**, **piccole**, **Medium**, **grande**, o **Molto grande**.  Per altre informazioni, vedere [dimensioni dei servizi Cloud](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Azione di avvio (solo ruolo Web)

Impostare questa proprietà per specificare che Visual Studio deve essere avviato un web browser per gli endpoint HTTP o gli endpoint HTTPS o entrambi quando si avvia il debug.

Il **endpoint HTTPS** opzione è disponibile solo se è già stato definito un endpoint HTTPS per il ruolo. È possibile definire un endpoint HTTPS nella **endpoint** pagina delle proprietà.

Se è già stato aggiunto un endpoint HTTPS, l'opzione endpoint HTTPS è abilitato per impostazione predefinita e Visual Studio avvia un browser per questo endpoint quando si avvia il debug, oltre che in un browser per l'endpoint HTTP, presupponendo che sono abilitate entrambe le opzioni di avvio.

### <a name="diagnostics"></a>Diagnostica

Per impostazione predefinita, la diagnostica è abilitata per il ruolo Web. L'account di archiviazione e di progetto servizio cloud di Azure configurati per usare l'emulatore di archiviazione locale. Quando si è pronti per distribuire in Azure, è possibile selezionare il pulsante del generatore (**...** ) da usare invece archiviazione di Azure. È possibile trasferire i dati di diagnostica nell'account di archiviazione su richiesta o a intervalli pianificati automaticamente. Per altre informazioni su diagnostica di Azure, vedere [abilitazione della diagnostica nei servizi Cloud di Azure e macchine virtuali](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Pagina Impostazioni

Nel **impostazioni** pagina, è possibile aggiungere le impostazioni per una configurazione come coppie nome-valore. Il codice in esecuzione nel ruolo può leggere i valori delle impostazioni di configurazione in fase di esecuzione usando le classi fornite dal [libreria gestita di Azure](http://go.microsoft.com/fwlink?LinkID=171026), in particolare, il [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) (metodo).

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Configurazione di una stringa di connessione per un account di archiviazione

Una stringa di connessione è un'impostazione che fornisce informazioni di connessione e autenticazione per l'emulatore di archiviazione o per un account di archiviazione di Azure. Ogni volta che il codice in un ruolo accede archiviazione di Azure (BLOB, code o tabelle), è necessario che una stringa di connessione.

> [!Note]
> Una stringa di connessione per l'account di archiviazione di Azure è necessario usare un formato definito (vedere [configurare le stringhe di connessione di Azure Storage](/azure/storage/common/storage-configure-connection-string)).

È possibile impostare la stringa di connessione per usare l'archiviazione locale in base alle esigenze, quindi impostare su un account di archiviazione di Azure quando si distribuisce l'applicazione del servizio cloud. Impossibile impostare la stringa di connessione in modo corretto può causare il ruolo non venga avviato, oppure per scorrere gli stati inizializzazione, occupati e arresto.

Per creare una stringa di connessione, selezionare **Aggiungi impostazione** e impostare **tipo** "Stringa di connessione".

Per le stringhe di connessione nuova o esistente, selezionare **...** * a destra della **valore** campo per aprire la **crea stringa di connessione di archiviazione** finestra di dialogo:

1. Sotto **connettersi usando**, scegliere il **sottoscrizione** opzione per selezionare un account di archiviazione da una sottoscrizione. Visual Studio otterrà quindi le credenziali dell'account di archiviazione automaticamente dal `.publishsettings` file.
1. Selezionando **credenziali immesse manualmente** consente di specificare il nome dell'account e della chiave direttamente usando le informazioni dal portale di Azure. Per copiare la chiave dell'account:
    1. Passare all'account di archiviazione nel portale di Azure e seleziona **Gestisci chiavi**.
    1. Per copiare la chiave dell'account, passare all'account di archiviazione nel portale di Azure, selezionare **Impostazioni > chiavi di accesso**, quindi usare il pulsante Copia per copiare la chiave di accesso primaria negli Appunti.
1. Selezionare una delle opzioni di connessione. **Specifica endpoint personalizzati** viene richiesto di specificare gli URL di BLOB, tabelle e code. Gli endpoint personalizzati consentono di usare [domini personalizzati](/azure/storage/blobs/storage-custom-domain-name.md) e controllare l'accesso più preciso. Visualizzare [configurare le stringhe di connessione di archiviazione di Azure](/azure/storage/common/storage-configure-connection-string).
1. Selezionare **OK**, quindi **File > Salva** per aggiornare la configurazione con la nuova stringa di connessione.

Quando si pubblica l'applicazione in Azure, scegliere nuovamente la configurazione del servizio che contiene l'account di archiviazione di Azure per la stringa di connessione. Dopo aver pubblicato l'applicazione, verificare che l'applicazione funzioni come previsto rispetto ai servizi di archiviazione di Azure.

Per altre informazioni su come aggiornare le configurazioni del servizio, vedere la sezione [gestire le stringhe di connessione per gli account di archiviazione](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Pagina endpoint

Un ruolo web ha in genere un solo endpoint HTTP sulla porta 80. Un ruolo di lavoro, d'altra parte, può avere un numero qualsiasi di endpoint HTTP, HTTPS o TCP. Gli endpoint possono essere endpoint di input, che sono disponibili ai client esterni, o endpoint interni, quali sono disponibili ad altri ruoli in esecuzione nel servizio.

- Per rendere un endpoint HTTP disponibile a client esterni e Web browser, modificare il tipo di endpoint di input e specificare un nome e un numero di porta pubblica.
- Per rendere un endpoint HTTPS disponibile a client esterni e Web browser, modificare il tipo di endpoint da **input**e specificare un nome, un numero di porta pubblico e un nome di certificato di gestione. È anche necessario definire il certificato nella **certificati** pagina delle proprietà prima di poter specificare un certificato di gestione. 
- Per rendere un endpoint disponibile per l'accesso interno da altri ruoli nel servizio cloud, modificare il tipo di endpoint in interno e specificare un nome e possibili porte private per questo endpoint.

## <a name="local-storage-page"></a>Pagina archiviazione locale

È possibile usare la **risorsa di archiviazione locale** pagina delle proprietà per riservare una o più risorse di archiviazione locale per un ruolo. Una risorsa di archiviazione locale è una directory riservata nel file system della macchina virtuale di Azure in cui è in esecuzione un'istanza di un ruolo.

## <a name="certificates-page"></a>Pagina certificati

Il **certificati** pagina delle proprietà aggiunge informazioni sui certificati alla configurazione del servizio. Si noti che i certificati non sono incluse con il servizio. è necessario caricare i certificati separatamente in Azure tramite il [portale di Azure](http://portal.azure.com).

Aggiunta di un certificato nel portale aggiunge informazioni sui certificati alla configurazione del servizio. Certificati non sono inclusi con il servizio. è necessario caricare i certificati separatamente tramite il portale di Azure.

Per associare un certificato al ruolo, specificare un nome per il certificato. Questo nome viene usato per fare riferimento al certificato quando si configura un endpoint HTTPS nella **endpoint** pagina. Specificare quindi se l'archivio certificati è **computer locale** oppure **CurrentUser** e il nome dell'archivio. Infine, immettere l'identificazione personale del certificato. Se il certificato sia nel corrente\Personale archivio personale, è possibile immettere l'identificazione personale del certificato, selezionare il certificato da un elenco popolato. Se si trova in qualsiasi altra posizione, è possibile immettere manualmente il valore di identificazione personale.

Quando si aggiunge un certificato dall'archivio certificati, eventuali certificati intermedi vengono aggiunti automaticamente per le impostazioni di configurazione per l'utente. Inoltre, questi certificati intermedi devono essere caricati in Azure per configurare correttamente il servizio per SSL.

I certificati di gestione che è associato il servizio si applicano al servizio solo quando è in esecuzione nel cloud. Quando il servizio è in esecuzione nell'ambiente di sviluppo locale, Usa un certificato standard gestito dall'emulatore di calcolo.
