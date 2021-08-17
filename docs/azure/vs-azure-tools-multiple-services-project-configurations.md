---
title: Configurare il servizio cloud con più configurazioni
description: Informazioni su come configurare un progetto di servizio cloud di Azure modificando i file ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg e ServiceConfiguration.Cloud.cscfg.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 7d2c0c7e54bb57f199579716499ee02901ae58c16dadf773dc4e5513bb28484d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348748"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Configurazione del progetto Azure di Visual Studio per l'uso di più configurazioni del servizio

Un progetto di servizio cloud di Azure in Visual Studio include tre file di configurazione: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg` e `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` viene distribuito in Azure per descrivere i requisiti del servizio cloud e i relativi ruoli e per fornire le impostazioni applicabili a tutte le istanze. Impostazioni può essere letto in fase di esecuzione usando l'API del runtime di hosting del servizio di Azure. Questo file può essere aggiornato in Azure solo quando il servizio cloud viene arrestato.
- `ServiceConfiguration.Local.cscfg` e `ServiceConfiguration.Cloud.cscfg` forniscono i valori per le impostazioni del file di definizione e specificano il numero di istanze da eseguire per ogni ruolo. Il file "Local" contiene i valori usati nel debug locale, mentre il file "Cloud" viene distribuito in Azure come `ServiceConfiguration.cscfg` e fornisce le impostazioni per l'ambiente server. Questo file può essere aggiornato mentre il servizio cloud è in esecuzione in Azure.

Le impostazioni di configurazione vengono gestite e modificate in Visual Studio attraverso le pagine delle proprietà relative al ruolo applicabile (fare clic con il pulsante destro del mouse sul ruolo e scegliere **Proprietà** oppure fare doppio clic sul ruolo). L'ambito delle modifiche può essere delimitato da qualsiasi configurazione scelta nell'elenco a discesa **Configurazione servizio**. Le proprietà dei ruoli Web e di lavoro sono simili, tranne per gli aspetti descritti nelle sezioni seguenti.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Per informazioni sugli schemi sottostanti per i file di definizione e di configurazione del servizio, vedere gli articoli [Schema XML .csdef](/azure/cloud-services/schema-csdef-file) e [Schema XML .cscfg](/azure/cloud-services/schema-cscfg-file). Per altre informazioni sulla configurazione del servizio, vedere [Come configurare i servizi cloud](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Pagina Configurazione

### <a name="service-configuration"></a>Service Configuration

Consente di selezionare il file `ServiceConfiguration.*.cscfg` interessato dalle modifiche. Per impostazione predefinita, sono disponibili le varianti Local e Cloud ed è possibile usare il comando **Gestisci** per copiare, rinominare e rimuovere i file di configurazione. Questi file vengono aggiunti al progetto di servizio cloud e vengono visualizzati in **Esplora soluzioni**. Tuttavia, la ridenominazione o la rimozione di configurazioni può essere eseguita solo da questo controllo.

### <a name="instances"></a>Istanze

Impostare la proprietà **Conteggio istanze** sul numero di istanze che il servizio deve eseguire per questo ruolo.

Impostare la proprietà delle **Dimensioni macchina virtuale** su **Molto piccola**, **Piccola**, **Media**, **Grande** o **Molto grande**.  Per altre informazioni, vedere [Dimensioni dei servizi cloud.](/azure/cloud-services/cloud-services-sizes-specs)

### <a name="startup-action-web-role-only"></a>Startup Action (Azione di avvio) (solo ruolo Web)

Impostare questa proprietà per specificare che in Visual Studio deve essere avviato un Web browser per gli endpoint HTTP o HTTPS o entrambi quando si inizia il debug.

**L'opzione Endpoint HTTPS** è disponibile solo se è già stato definito un endpoint HTTPS per il ruolo. È possibile definire un endpoint HTTPS nella pagina delle proprietà **Endpoint** .

Se è già stato aggiunto un endpoint HTTPS, l'opzione Endpoint HTTPS è abilitata per impostazione predefinita e Visual Studio avvia un browser per questo endpoint all'inizio del debug in aggiunta a un browser per l'endpoint HTTP, presupponendo che entrambe le opzioni di avvio siano abilitate.

### <a name="diagnostics"></a>Diagnostica

Per impostazione predefinita, la diagnostica è abilitata per il ruolo Web. Il progetto di servizio cloud di Azure e l'account di archiviazione sono impostati per usare l'emulatore di archiviazione locale. Quando si è pronti a eseguire la distribuzione in Azure, è possibile selezionare il pulsante del generatore (**…**) per usare in sostituzione l’archiviazione di Azure. È possibile trasferire i dati di diagnostica nell'account di archiviazione a richiesta o a intervalli pianificati automaticamente. Per altre informazioni sulla diagnostica di Azure, vedere [Abilitazione della diagnostica nei servizi cloud e nelle macchine virtuali di Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Pagina Impostazioni

Nella pagina **Impostazioni** è possibile aggiungere impostazioni a una configurazione come coppie nome-valore. Il codice in esecuzione nel ruolo può leggere i valori delle impostazioni di configurazione in fase di esecuzione usando le classi fornite dalla libreria gestita di [Azure,](/previous-versions/azure/dn602775(v=azure.11))in particolare il [metodo GetConfigurationSettingValue.](/previous-versions/azure/reference/ee772857(v=azure.100))

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Configurazione di una stringa di connessione per un account di archiviazione

Una stringa di connessione è un'impostazione che fornisce informazioni di connessione e autenticazione per l'emulatore di archiviazione o per un account di archiviazione di Azure. Una stringa di connessione è necessaria ogni volta che il codice in un ruolo accede all'archiviazione di Azure (BLOB, code o tabelle).

> [!Note]
> Una stringa di connessione per l'account di archiviazione di Azure deve avere un formato definito (vedere [Configurare le stringhe di connessione di Archiviazione di Azure](/azure/storage/common/storage-configure-connection-string)).

È possibile impostare la stringa di connessione per l'uso dell'archiviazione locale in base alle necessità, quindi impostarla su un account di archiviazione di Azure quando si distribuisce l'applicazione del servizio cloud. Se la stringa di connessione viene impostata in modo errato, è possibile che il ruolo non venga avviato o che continui a passare in modo ciclico dalla fase di inizializzazione, allo stato occupato e alla fase di arresto.

Per creare una stringa di connessione, selezionare **Aggiungi impostazione** e impostare **Tipo** su "Stringa di connessione".

Per le stringhe di connessione nuove o esistenti, selezionare **...** _ a destra del campo _ *Valore** per aprire la finestra **di dialogo Crea Archiviazione di connessione:**

1. In **Connetti con** scegliere l'opzione **Sottoscrizione** per selezionare un account di archiviazione da una sottoscrizione. Visual Studio otterrà quindi le credenziali dell'account di archiviazione automaticamente dal file `.publishsettings`.
1. Se si seleziona **Credenziali immesse manualmente**, è possibile specificare il nome e la chiave dell'account direttamente, usando le informazioni presenti nel portale di Azure. Per copiare la chiave dell'account:
    1. Selezionare l'account di archiviazione nel portale di Azure e fare clic su **Gestisci chiavi**.
    1. Per copiare la chiave dell'account, passare all'account di archiviazione nel portale di Azure, selezionare **Impostazioni > Chiavi di accesso** e quindi usare il pulsante Copia per copiare la chiave di accesso primaria negli Appunti.
1. Selezionare una delle opzioni di connessione. In **Specifica endpoint personalizzati** viene chiesto di specificare gli URL di BLOB, tabelle e code. Gli endpoint personalizzati consentono di usare i [domini personalizzati](/azure/storage/blobs/storage-custom-domain-name) e controllare l'accesso in maniera più precisa. Vedere [Configurare le stringhe di connessione di archiviazione di Azure](/azure/storage/common/storage-configure-connection-string).
1. Fare clic su **OK**, quindi selezionare **File > Salva** per aggiornare la configurazione con la nuova stringa di connessione.

Quando si pubblica l'applicazione in Azure, ricordarsi di scegliere la configurazione del servizio che contiene l'account di archiviazione di Azure per la stringa di connessione. Dopo la pubblicazione, verificare che l'applicazione funzioni come previsto in base ai servizi di archiviazione di Azure.

Per altre informazioni su come aggiornare le configurazioni del servizio, vedere la sezione [Gestire le stringhe di connessione per gli account di archiviazione](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Pagina Endpoint

Un ruolo Web ha in genere un solo endpoint HTTP sulla porta 80. Un ruolo di lavoro, invece, può avere un qualsiasi numero di endpoint HTTP, HTTPS o TCP. Gli endpoint possono essere endpoint di input, disponibili a client esterni, o endpoint interni, disponibili ad altri ruoli in esecuzione nel servizio.

- Per rendere un endpoint HTTP disponibile a client esterni e Web browser, cambiare il tipo di endpoint in input e specificare un nome e un numero di porta pubblico.
- Per rendere un endpoint HTTPS disponibile a client esterni e Web browser, cambiare il tipo di endpoint in **input** e specificare un nome, un numero di porta pubblico e un nome di certificato di gestione. Prima di poter specificare un certificato di gestione, è necessario anche definire il certificato nella pagina delle proprietà **Certificati**.
- Per rendere un endpoint disponibile per l'accesso interno da parte di altri ruoli nel servizio cloud, cambiare il tipo di endpoint in interno e specificare un nome e le possibili porte private per questo endpoint.

## <a name="local-storage-page"></a>Pagina Archiviazione locale

È possibile usare la pagina delle proprietà **Archiviazione locale** per riservare una o più risorse di archiviazione locali per un ruolo. Una risorsa di archiviazione locale è una directory riservata nel file system della macchina virtuale di Azure in cui è eseguita un'istanza di un ruolo.

## <a name="certificates-page"></a>Pagina Certificati

La pagina delle proprietà **Certificati** consente di aggiungere informazioni sui certificati alla configurazione del servizio. Si noti che i certificati non sono inclusi nel servizio. È necessario caricarli separatamente in Azure usando il [portale di Azure](https://portal.azure.com).

Aggiungendo un certificato nel portale si inseriscono informazioni sui certificati nella configurazione del servizio. I certificati non sono inclusi nel servizio. È necessario caricarli separatamente in Azure usando il portale di Azure.

Per associare un certificato al ruolo, fornire un nome per il certificato. Questo nome sarà usato per fare riferimento al certificato quando si configura un endpoint HTTPS nella pagina **Endpoint**. Specificare quindi se l'archivio certificati è **Computer locale** o **Utente corrente** e il nome dell'archivio. Infine, immettere l'identificazione personale del certificato. Se il certificato si trova nell'archivio Utente corrente\Personale, è possibile immettere l'identificazione personale del certificato selezionandolo da un elenco popolato. Se si trova in qualsiasi altro percorso, immettere manualmente il valore dell'identificazione personale.

Quando si aggiunge un certificato dall'archivio certificati, qualsiasi certificato intermedio viene aggiunto automaticamente alle impostazioni di configurazione. Inoltre, questi certificati intermedi devono essere caricati in Azure per poter configurare correttamente il servizio per SSL.

Qualsiasi certificato di gestione associato al servizio si applica al servizio solo quando è in esecuzione nel cloud. Quando il servizio è in esecuzione nell'ambiente di sviluppo locale, viene usato un certificato standard gestito dall'emulatore di calcolo.
