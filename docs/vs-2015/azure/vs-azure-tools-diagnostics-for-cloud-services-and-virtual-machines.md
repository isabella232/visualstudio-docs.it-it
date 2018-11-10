---
title: Configurare la diagnostica per le macchine virtuali e servizi Cloud di Azure | Microsoft Docs
description: Informazioni su come configurare la diagnostica per il debug di servizi cloud di Azure e delle macchine virtuali (VM) in Visual Studio.
author: mikejo5000
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 4448825c5d443887833a405aab14d2243a0e5216
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003071"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Configurare la diagnostica per Servizi cloud di Azure e macchine virtuali
Quando è necessario risolvere i problemi di un servizio cloud di Azure o una macchina virtuale, è possibile utilizzare Visual Studio per configurare più facilmente la diagnostica di Azure. Diagnostica di Azure acquisisce i dati di sistema e i dati di registrazione nelle macchine virtuali e istanze di macchine virtuali che eseguono il servizio cloud. I dati di diagnostica vengono trasferiti a un account di archiviazione scelto. Per altre informazioni sulla diagnostica registrazione in Azure, vedere [abilitare la registrazione diagnostica per le app Web nel servizio App di Azure](/azure/app-service/web-sites-enable-diagnostic-log).

In questo articolo viene illustrato come usare Visual Studio per attivare e configurare la diagnostica di Azure, prima e dopo la distribuzione. Informazioni su come configurare la diagnostica in macchine virtuali di Azure, come selezionare i tipi di informazioni di diagnostica da raccogliere e come visualizzare le informazioni che vengono raccolte.

Per configurare diagnostica di Azure, è possibile utilizzare una delle opzioni seguenti:

* Modificare le impostazioni di diagnostica nel **configurazione di diagnostica** finestra di dialogo in Visual Studio. Le impostazioni vengono salvate in un file denominato Diagnostics. wadcfgx (in Azure SDK 2.4 e versioni precedenti, il file è denominato Diagnostics. wadcfg). È anche possibile modificare direttamente il file di configurazione. Se si aggiorna manualmente il file, la configurazione le modifiche diventano effettive la volta successiva che si distribuisce nel cloud del servizio in Azure o eseguire il servizio nell'emulatore.
* Usare Cloud Explorer o Esplora Server in Visual Studio per modificare le impostazioni di diagnostica per un servizio cloud o macchina virtuale è in esecuzione.

## <a name="azure-sdk-26-diagnostics-changes"></a>Modifiche alla diagnostica di Azure SDK 2.6
Le modifiche seguenti si applicano a Azure SDK 2.6 e versioni successive progetti in Visual Studio:

* L'emulatore locale supporta ora la diagnostica. Ciò significa che è possibile raccogliere dati di diagnostica e assicurarsi che l'applicazione crei le tracce corrette durante lo sviluppo e test in Visual Studio. La stringa di connessione `UseDevelopmentStorage=true` viene attivata la raccolta dei dati di diagnostica durante l'esecuzione del progetto servizio cloud in Visual Studio usando l'emulatore di archiviazione di Azure. Tutti i dati di diagnostica vengono raccolti nell'account di archiviazione archivio di sviluppo.
* La stringa di connessione account di archiviazione di diagnostica `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` viene archiviato nel file di configurazione (con estensione cscfg) del servizio. In Azure SDK 2.5 l'account di archiviazione di diagnostica viene specificato nel file Diagnostics. wadcfgx.

La stringa di connessione funziona in modo diverso in alcuni modi principali in Azure SDK 2.6 e versioni successive rispetto ad Azure SDK 2.4 e versioni precedenti:

* In Azure SDK 2.4 e versioni precedenti, la stringa di connessione viene utilizzata come runtime dal plug-in di diagnostica per ottenere le informazioni sull'account di archiviazione per il trasferimento dei log di diagnostica.
* In Azure SDK 2.6 e versioni successive, Visual Studio Usa la stringa di connessione di diagnostica per configurare l'estensione diagnostica di Azure con le informazioni sull'account di archiviazione appropriato durante la pubblicazione. È possibile usare la stringa di connessione per definire diversi account di archiviazione per diverse configurazioni del servizio utilizzato da Visual Studio durante la pubblicazione. Tuttavia, perché il plug-in diagnostica non è disponibile dopo Azure SDK 2.5, il solo file con estensione cscfg non è possibile configurare l'estensione di diagnostica. È necessario configurare l'estensione separatamente usando strumenti come Visual Studio o PowerShell.
* Per semplificare il processo di configurazione dell'estensione di diagnostica tramite PowerShell, l'output del pacchetto da Visual Studio include il file XML di configurazione pubblica per l'estensione di diagnostica per ogni ruolo. Visual Studio Usa la stringa di connessione di diagnostica per popolare le informazioni sull'account di archiviazione nella configurazione pubblica. I file di configurazione pubblica vengono creati nella cartella Extensions. I file di configurazione pubblica usano il modello di denominazione PaaSDiagnostics. &lt;nome del ruolo\>. Pubconfig. Eventuali distribuzioni basate su PowerShell possono usare questo modello per eseguire il mapping di ogni configurazione a un ruolo.
* Il [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040) Usa la stringa di connessione nel file con estensione cscfg per accedere ai dati di diagnostica. I dati vengono visualizzati nei **Monitoring** scheda. La stringa di connessione è necessaria per impostare il servizio per visualizzare dati dettagliati del monitoraggio nel portale.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Eseguire la migrazione di progetti ad Azure SDK 2.6 e versioni successive
Quando esegue la migrazione da Azure SDK 2.5 ad Azure SDK 2.6 o versioni successive, se si ha un account di archiviazione di diagnostica specificato nel file con estensione wadcfgx, l'account di archiviazione rimarrà in tale file. Per poter sfruttare la flessibilità dell'uso di account di archiviazione diversi per le configurazioni di archiviazione diverso, aggiungere manualmente la stringa di connessione al progetto. Se si sta eseguendo la migrazione di un progetto da Azure SDK 2.4 o versioni precedenti ad Azure SDK 2.6, le stringhe di connessione di diagnostica vengono mantenute. Si noti, tuttavia, le modifiche in modo in cui le stringhe di connessione vengono gestite in Azure SDK 2.6, come descritto nella sezione precedente.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Come Visual Studio determina l'account di archiviazione di diagnostica
* Se nel file cscfg viene specificata una stringa di connessione di diagnostica, Visual Studio la userà per configurare l'estensione di diagnostica durante la pubblicazione e quando vengono generati i file XML di configurazione pubblica durante la creazione di pacchetti.
* Se una stringa di connessione di diagnostica non è specificata nel file con estensione cscfg, Visual Studio userà di nuovo l'account di archiviazione specificato nel file con estensione wadcfgx per configurare l'estensione di diagnostica per la pubblicazione e per la generazione di codice XML di configurazione pubblica file durante la creazione di pacchetti.
* La stringa di connessione di diagnostica nel file cscfg ha la precedenza su account di archiviazione nel file con estensione wadcfgx. Se è una stringa di connessione di diagnostica specificati nel file con estensione cscfg, Visual Studio usa tale stringa e ignora l'account di archiviazione specificato nel file wadcfgx.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Che cosa fa la casella di controllo "Aggiorna stringhe di connessione archiviazione..."?
Il **Aggiorna stringhe di connessione di archiviazione per la diagnostica e la memorizzazione nella cache con le credenziali dell'account di archiviazione di Microsoft Azure durante la pubblicazione in Microsoft Azure** casella di controllo è un modo pratico per aggiornare qualsiasi archivio di sviluppo le stringhe di connessione dell'account con l'account di archiviazione di Azure specificato durante la pubblicazione.

Ad esempio, se si seleziona questa casella di controllo e la stringa di connessione di diagnostica specifica `UseDevelopmentStorage=true`, quando si pubblica il progetto in Azure, Visual Studio aggiorna automaticamente la stringa di connessione di diagnostica con l'account di archiviazione specificato nel la pubblicazione guidata. Tuttavia, se è stato specificato un account di archiviazione effettivo come stringa di connessione di diagnostica, viene usato invece tale account.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Differenze di funzionalità di diagnostica in Azure SDK 2.4 e versioni precedenti e. Azure SDK 2.5 e versioni successive
Se si aggiorna il progetto da Azure SDK 2.4 e versioni precedenti ad Azure SDK 2.5 o versioni successive, tenere presenti le differenze di funzionalità di diagnostica seguenti:

* **Le API di configurazione sono deprecate**. Configurazione a livello di diagnostica è disponibile in Azure SDK 2.4 e versioni precedenti, ma è deprecata in Azure SDK 2.5 e versioni successive. Se la configurazione della diagnostica è attualmente definita nel codice, è necessario riconfigurare tali impostazioni da zero nel progetto migrato per la diagnostica per continuare a lavorare. Il file di configurazione di diagnostica per Azure SDK 2.4 è Diagnostics. wadcfg. Il file di configurazione di diagnostica per Azure SDK 2.5 e versioni successive è Diagnostics. wadcfgx.
* **Diagnostica per le applicazioni del servizio cloud può essere configurata solo a livello di ruolo**. In Azure SDK 2.5 e versioni successive, è possibile configurare la diagnostica per le applicazioni del servizio cloud a livello di istanza.
* **Ogni volta che si distribuisce l'app, la configurazione di diagnostica viene aggiornata**. Ciò può causare problemi di parità se si modifica la configurazione di diagnostica da Esplora Server di Visual Studio e quindi si ridistribuisce l'app.
* **In Azure SDK 2.5 e versioni successive, i dump di arresto anomalo del sistema sono configurati nel file di configurazione della diagnostica e non nel codice**. Se i dump di arresto anomalo del sistema configurati nel codice, è necessario trasferire manualmente la configurazione dal codice nel file di configurazione. I dump di arresto anomalo del sistema non vengono trasferiti durante la migrazione ad Azure SDK 2.6.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Attivare la diagnostica nei progetti servizio cloud prima di distribuirli
In Visual Studio, è possibile raccogliere i dati di diagnostica per i ruoli eseguiti in Azure quando si esegue il servizio nell'emulatore prima della distribuzione. Tutte le modifiche alle impostazioni diagnostiche in Visual Studio vengono salvate nel file di configurazione Diagnostics. wadcfgx. Queste impostazioni specificano l'account di archiviazione in cui i dati di diagnostica vengono salvati quando si distribuisce il servizio cloud.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Per attivare la diagnostica in Visual Studio prima della distribuzione

1. Menu di scelta rapida per il ruolo, selezionare **proprietà**. Il ruolo **delle proprietà** finestra di dialogo, seleziona la **configurazione** scheda.
2. Nel **Diagnostics** sezione, verificare che il **Abilita diagnostica** casella di controllo è selezionata.
   
    ![Accedere all'opzione Abilita diagnostica](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Per specificare l'account di archiviazione per i dati di diagnostica, selezionare il pulsante con puntini di sospensione (...).
   
    ![Specificare l'account di archiviazione da usare](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. Nel **crea stringa di connessione di archiviazione** finestra di dialogo, specificare se si vuole connettere usando l'emulatore di archiviazione di Azure, una sottoscrizione di Azure o credenziali immesse manualmente.
   
    ![Finestra di dialogo account di archiviazione](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * Se si seleziona **emulatore di archiviazione di Microsoft Azure**, la stringa di connessione è impostata su `UseDevelopmentStorage=true`.
   * Se si seleziona **sottoscrizione**, è possibile selezionare la sottoscrizione di Azure che si desidera usare e immettere un nome dell'account. Per gestire le sottoscrizioni di Azure, selezionare **Manage Accounts**.
   * Se si seleziona **credenziali immesse manualmente**, immettere il nome e chiave dell'account di Azure che si desidera utilizzare.
5. Per visualizzare il **configurazione di diagnostica** finestra di dialogo **configura**. Ad eccezione di **generali** e **directory Log**, ogni scheda rappresenta un'origine dati di diagnostica che è possibile raccogliere. Il valore predefinito **generali** nella scheda sono disponibili opzioni di raccolta dati di diagnostica seguenti: **solo gli errori**, **tutte le informazioni**, e **Personalizza piano**. Il valore predefinito **solo gli errori** opzione utilizzata la quantità minima di spazio di archiviazione, perché non trasferisce gli avvisi o messaggi di traccia. Il **tutte le informazioni** opzione trasferisce le informazioni più Usa al meglio archiviazione e di conseguenza, è l'opzione più costosa.

   > [!NOTE]
   > Dimensione minima supportata per "Quota disco in MB" è 4GB. Tuttavia, se si stanno raccogliendo i dump di memoria, aumentare questo valore, ad esempio 10GB.
   >
  
    ![Abilitare la configurazione e diagnostica di Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Per questo esempio, selezionare la **Personalizza piano** opzione, pertanto è possibile personalizzare i dati raccolti.
7. Nel **Quota disco in MB** casella, è possibile impostare la quantità di spazio da allocare nell'account di archiviazione dei dati di diagnostica. È possibile modificare o accettare il valore predefinito.
8. In ogni scheda dei dati di diagnostica che si desidera raccogliere, selezionare la **Abilita il trasferimento dei \<tipo registro\>**  casella di controllo. Ad esempio, se si desidera raccogliere i log applicazioni, nel **log applicazioni** scheda, seleziona il **Abilita il trasferimento dei log applicazione** casella di controllo. Inoltre, specificare qualsiasi altra informazione necessaria per ogni tipo di dati di diagnostica. Per informazioni sulla configurazione per ogni scheda, vedere la sezione **impostare le origini dati di diagnostica** più avanti in questo articolo. 
9. Dopo aver abilitato la raccolta di tutti i dati di diagnostica desiderati, selezionare **OK**.
10. Eseguire il progetto di servizio cloud di Azure in Visual Studio come di consueto. Quando si usa l'applicazione, viene salvate le informazioni del log che è stata abilitata per l'account di archiviazione di Azure che è stato specificato.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Attivare la diagnostica in macchine virtuali di Azure
In Visual Studio, è possibile raccogliere i dati di diagnostica per le macchine virtuali di Azure.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Per attivare la diagnostica in macchine virtuali di Azure

1. In Esplora Server, selezionare il nodo di Azure e quindi connettersi alla sottoscrizione di Azure, se non è già connessi.
2. Espandere la **macchine virtuali** nodo. È possibile creare una nuova macchina virtuale o selezionare un nodo esistente.
3. Menu di scelta rapida per la macchina virtuale desiderata, selezionare **configura**. Viene visualizzata la finestra di dialogo di configurazione macchina virtuale.
   
    ![Configurare una macchina virtuale di Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Se non è già installato, aggiungere l'estensione diagnostica di Microsoft Monitoring Agent. Con questa estensione, è possibile raccogliere i dati di diagnostica per la macchina virtuale di Azure. Sotto **estensioni installate**, nella **Seleziona estensione disponibile** casella di riepilogo a discesa selezionare **Microsoft Monitoring Agent Diagnostics**.
   
    ![Installare un'estensione di macchina virtuale di Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > Altre estensioni di diagnostica sono disponibili per le macchine virtuali. Per altre informazioni, vedere [estensioni di macchina virtuale e funzionalità per Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   > 
   > 
5. Per aggiungere l'estensione e visualizzare relativi **configurazione di diagnostica** finestra di dialogo **Add**.
6. Per specificare un account di archiviazione, selezionare **Configure**, quindi selezionare **OK**.
   
    Ogni scheda (tranne che per **generali** e **directory Log**) rappresenta un'origine dati di diagnostica che è possibile raccogliere.
   
    ![Abilitare la configurazione e diagnostica di Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    La scheda predefinita, **generali**, offre opzioni di raccolta dati di diagnostica seguenti: **solo gli errori**, **tutte le informazioni**, e **Personalizza piano**. L'opzione predefinita **solo gli errori**, richiede la quantità minima di spazio di archiviazione perché non trasferisce gli avvisi o messaggi di traccia. Il **tutte le informazioni** opzione trasferisce più le informazioni e, pertanto, l'opzione più costosa in termini di archiviazione.
7. Per questo esempio, selezionare la **Personalizza piano** opzione in modo che è possibile personalizzare i dati raccolti.
8. Il **Quota disco in MB** casella consente di specificare la quantità di spazio da allocare nell'account di archiviazione dei dati di diagnostica. Se si desidera, è possibile modificare il valore predefinito.
9. In ogni scheda dei dati di diagnostica da raccogliere, selezionare relative **Abilita il trasferimento dei \<tipo registro\>**  casella di controllo.
   
    Ad esempio, se si desidera raccogliere i log applicazioni, selezionare la **Abilita il trasferimento dei log applicazioni** casella di controllo la **registri applicazioni** scheda. Inoltre, specificare qualsiasi altra informazione necessaria per ogni tipo di dati di diagnostica. Per informazioni sulla configurazione per ogni scheda, vedere la sezione **impostare le origini dati di diagnostica** più avanti in questo articolo.
10. Dopo aver abilitato la raccolta di tutti i dati di diagnostica desiderati, selezionare **OK**.
11. Salvare il progetto aggiornato.
    
    Un messaggio nel **Log attività di Microsoft Azure** finestra indica che la macchina virtuale è stata aggiornata.

## <a name="set-up-diagnostics-data-sources"></a>Impostare le origini dati di diagnostica
Dopo aver abilitato la raccolta dati di diagnostica, è possibile scegliere esattamente le origini dati da raccogliere e le informazioni raccolte. Le sezioni successive descrivono le schede di **configurazione di diagnostica** nella finestra di dialogo e significa che ogni opzione di configurazione.

### <a name="application-logs"></a>Log dell'applicazione
I log applicazioni includono informazioni di diagnostica che sono prodotta da un'applicazione web. Se si desidera acquisire i log applicazioni, selezionare la **Abilita il trasferimento dei log applicazione** casella di controllo. Per aumentare o diminuire l'intervallo tra il trasferimento dei log applicazioni all'account di archiviazione, modificare il **periodo di trasferimento (min)** valore. È anche possibile modificare la quantità di informazioni acquisite nel log impostando il **livello di registrazione** valore. Ad esempio, selezionare **Verbose** per ottenere altre informazioni oppure selezionare **critico** per acquisire solo gli errori critici. Se si dispone di un provider di diagnostica specifico che genera log applicazioni, è possibile acquisirli aggiungendo il GUID del provider nel **GUID Provider** casella.

  ![Log dell'applicazione](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Per altre informazioni sui log applicazioni, vedere [abilitare la registrazione diagnostica per le app Web nel servizio App di Azure](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Registri eventi di Windows
Per acquisire i registri eventi di Windows, selezionare la **Abilita il trasferimento dei log di eventi di Windows** casella di controllo. Per aumentare o diminuire l'intervallo tra il trasferimento dei registri eventi all'account di archiviazione, modificare il **periodo di trasferimento (min)** valore. Selezionare le caselle di controllo per i tipi di eventi che si vuole tenere traccia.

![Log eventi](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Se si usa Azure SDK 2.6 o versione successiva e si vuole specificare un'origine dati personalizzata, immetterla nella **\<nome dell'origine dati\>** casella di testo e quindi selezionare **Add**. L'origine dati viene aggiunto al file cfcfg.

Se si usa Azure SDK 2.5 e si vuole specificare un'origine dati personalizzata, è possibile aggiungerlo al `WindowsEventLog` file sezione Diagnostics. wadcfgx, come nell'esempio seguente:

```
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>Contatori delle prestazioni
Informazioni sui contatori delle prestazioni consente di individuare i colli di bottiglia e ottimizzare le prestazioni di sistema e dell'applicazione. Per altre informazioni, vedere [creare e usare contatori di prestazioni in un'applicazione Azure](https://msdn.microsoft.com/library/azure/hh411542.aspx). Per acquisire i contatori delle prestazioni, selezionare la **Abilita il trasferimento di contatori delle prestazioni** casella di controllo. Per aumentare o diminuire l'intervallo tra il trasferimento dei registri eventi all'account di archiviazione, modificare il **periodo di trasferimento (min)** valore. Selezionare le caselle di controllo per i contatori delle prestazioni che si vuole tenere traccia.

![Contatori delle prestazioni](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Per tracciare un contatore delle prestazioni che non è elencato, immettere il contatore delle prestazioni usando la sintassi suggerita. e quindi selezionare **Add**. Il sistema operativo nella macchina virtuale determina quali contatori delle prestazioni è possibile tenere traccia. Per altre informazioni sulla sintassi, vedere [specificare un percorso di contatore](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Log dell'infrastruttura
I log dell'infrastruttura contengono informazioni sull'infrastruttura di diagnostica Azure, il modulo RemoteAccess e il modulo RemoteForwarder. Per raccogliere informazioni sui log dell'infrastruttura, selezionare la **Abilita il trasferimento dei log dell'infrastruttura** casella di controllo. Per aumentare o diminuire l'intervallo tra il trasferimento dei log dell'infrastruttura all'account di archiviazione, modificare il **periodo di trasferimento (min)** valore.

![Log dell'infrastruttura di diagnostica](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Per altre informazioni, vedere [raccogliere dati di registrazione utilizzando diagnostica Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Directory log
Directory di log contengono i dati raccolti dalle directory di log per le richieste Internet Information Services (IIS), le richieste non riuscite o le cartelle selezionate. Per acquisire le directory di log, selezionare la **Abilita il trasferimento di directory di Log** casella di controllo. Per aumentare o diminuire l'intervallo tra il trasferimento dei log all'account di archiviazione, modificare il **periodo di trasferimento (min)** valore.

Selezionare le caselle di controllo dei log che si desidera raccogliere, ad esempio **log di IIS** e **richieste non riuscite** i log. Vengono forniti i nomi dei contenitori di archiviazione predefinito, ma è possibile modificare i nomi.

È possibile acquisire log da qualsiasi cartella. Specificare il percorso nella **Log da Directory assoluta** sezione e quindi selezionare **Aggiungi Directory**. I log vengono acquisiti nei contenitori specificati.

![Directory log](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>Log ETW
Se si usa [traccia eventi per Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) e si vuole acquisire i log ETW, selezionare la **Abilita il trasferimento dei log ETW** casella di controllo. Per aumentare o diminuire l'intervallo tra il trasferimento dei log all'account di archiviazione, modificare il **periodo di trasferimento (min)** valore.

Gli eventi vengono acquisiti da origini eventi e manifesti evento specificato. Per specificare un'origine evento, il **origini eventi** sezione, immettere un nome e quindi selezionare **Aggiungi origine evento**. Analogamente, è possibile specificare un manifesto evento nella **manifesti evento** sezione e quindi selezionare **Aggiungi manifesto evento**.

![Log ETW](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

Il framework ETW è supportato in ASP.NET tramite le classi di [aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) dello spazio dei nomi. Lo spazio dei nomi windowsazure, che eredita da ed estende standard [aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) classi, consente di usare [aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) come una registrazione Framework nell'ambiente Azure. Per altre informazioni, vedere [assumere il controllo di registrazione e traccia in Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) e [abilitare la diagnostica nei servizi Cloud di Azure e macchine virtuali](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Dump di arresto anomalo del sistema
Per acquisire informazioni su quando si blocca un'istanza del ruolo, selezionare la **Abilita il trasferimento di dump di arresto anomalo del sistema** casella di controllo. (Poiché ASP.NET gestisce la maggior parte delle eccezioni, si tratta in genere utile solo per i ruoli di lavoro.) Per aumentare o ridurre la percentuale di spazio di archiviazione dedicata ai dump di arresto anomalo del sistema, modificare il **Quota di Directory (%)** valore. È possibile modificare il contenitore di archiviazione in cui vengono archiviati i dump di arresto anomalo del sistema e consente di indicare se si desidera acquisire una **completa** oppure **Mini** dump.

I processi attualmente tracciati sono elencati nel prossimo screenshot. Selezionare le caselle di controllo per i processi che si desidera acquisire. Per aggiungere un altro processo all'elenco, immettere il nome del processo e quindi selezionare **Aggiungi processo**.

![Dump di arresto anomalo del sistema](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Per altre informazioni, vedere [assumere il controllo di registrazione e traccia in Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) e [Microsoft Azure Diagnostics-parte 4: personalizzare i componenti di registrazione e diagnostica di Azure 1.3 modifiche](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Visualizzare i dati di diagnostica
Dopo aver raccolto i dati di diagnostica per un servizio cloud o macchina virtuale, è possibile visualizzarlo.

### <a name="to-view-cloud-service-diagnostics-data"></a>Per visualizzare i dati di diagnostica del servizio cloud
1. Distribuire il servizio cloud come di consueto e quindi eseguirlo.
2. È possibile visualizzare i dati di diagnostica in un report generato da Visual Studio o in tabelle nell'account di archiviazione. Per visualizzare i dati in un report, aprire Cloud Explorer o Esplora Server, aprire il menu di scelta rapida del nodo per il ruolo che si desidera e quindi selezionare **Visualizza dati di diagnostica**.
   
    ![Visualizza dati di diagnostica](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    Verrà visualizzato un report che mostra i dati disponibili.
   
    ![Report di diagnostica di Microsoft Azure in Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    Se non vengono visualizzati i dati più recenti, potrebbe essere necessario attendere il termine del periodo di trasferimento.
   
    Per aggiornare immediatamente i dati, selezionare la **Aggiorna** collegamento. Per aggiornare automaticamente i dati, selezionare un intervallo nel **l'aggiornamento automatico** casella di riepilogo a discesa. Per esportare i dati di errore, selezionare la **Esporta in CSV** pulsante per creare un file con valori delimitati da virgole che è possibile aprire in un foglio di lavoro di Excel.
   
    In Cloud Explorer o Esplora Server, aprire l'account di archiviazione associata con la distribuzione.
3. Aprire le tabelle di diagnostica nel Visualizzatore di tabelle e quindi esaminare i dati che sono stati raccolti. Per i log IIS e i log personalizzati, è possibile aprire un contenitore blob. La tabella seguente elenca le tabelle o contenitori di blob che contengono i dati per i file di log diverso. Oltre ai dati per tale file di log, le voci della tabella contengono **EventTickCount**, **DeploymentId**, **ruolo**, e **RoleInstance** , che consentono di identificare quali macchine virtuali e dei ruoli generato i dati e quando. 
   
   | Dati di diagnostica | Descrizione | Percorso |
   | --- | --- | --- |
   | Log dell'applicazione |I log generati chiamando i metodi di codice le **Trace** classe. |WADLogsTable |
   | Log eventi |Dati dai registri eventi di Windows nelle macchine virtuali. Windows archivia le informazioni in questi registri, ma le applicazioni e servizi anche usano i log per segnalare errori o registrano informazioni. |WADWindowsEventLogsTable |
   | Contatori delle prestazioni |È possibile raccogliere i dati nei contatori delle prestazioni che sono disponibili nella macchina virtuale. Il sistema operativo fornisce contatori delle prestazioni, che includono molte statistiche, quali il tempo di elaborazione e di utilizzo della memoria. |WADPerformanceCountersTable |
   | Log dell'infrastruttura |Log generati dall'infrastruttura di diagnostica stessa. |WADDiagnosticInfrastructureLogsTable |
   | Log di IIS |Log che registrano le richieste web. Se il servizio cloud riceve una quantità significativa di traffico, questi log possono essere lunghi. È una buona idea per raccogliere e archiviare questi dati solo quando ti serve. |È possibile trovare i log di richieste non riuscite nel contenitore blob in wad-iis-failedreqlogs corrispondente, in un percorso per tale distribuzione, ruolo e istanza. È possibile trovare i log completi in wad-iis-logfiles. Per ogni file vengono immessi nella tabella WADDirectories. |
   | Dump di arresto anomalo del sistema |Forniscono immagini binarie del processo del servizio cloud (in genere un ruolo di lavoro). |contenitore blob wad-crush-dumps |
   | File di log personalizzati |Log di dati definiti dall'utente. |È possibile specificare nel codice il percorso del file di log personalizzati nell'account di archiviazione. Ad esempio, è possibile specificare un contenitore blob personalizzato. |
4. Se i dati di qualsiasi tipo vengono troncati, è possibile provare ad aumentare il buffer per i dati di tali tipo o ridurre l'intervallo tra trasferimenti di dati dalla macchina virtuale per l'account di archiviazione.
5. (Facoltativo) Eliminare i dati dall'account di archiviazione in alcuni casi per ridurre i costi complessivi di archiviazione.
6. Quando si esegue una distribuzione completa, il file Diagnostics cscfg (con estensione wadcfgx per Azure SDK 2.5) viene aggiornato in Azure e il servizio cloud rileva ogni modifica della configurazione di diagnostica. Se invece si aggiorna una distribuzione esistente, il file con estensione cscfg non viene aggiornato in Azure. È comunque possibile modificare le impostazioni di diagnostica, tuttavia, seguendo i passaggi descritti nella sezione successiva. Per altre informazioni sull'esecuzione di una distribuzione completa e l'aggiornamento di una distribuzione esistente, vedere [pubblicazione guidata applicazione di Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Per visualizzare i dati di diagnostica macchina virtuale
1. Menu di scelta rapida per la macchina virtuale, selezionare **Visualizza dati di diagnostica**.
   
    ![Visualizzare i dati di diagnostica in una macchina virtuale di Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    Il **riepilogo diagnostica** verrà visualizzata la finestra di dialogo.
   
    ![Riepilogo diagnostica macchina virtuale di Azure](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    Se non vengono visualizzati i dati più recenti, potrebbe essere necessario attendere il termine del periodo di trasferimento.
   
    Per aggiornare immediatamente i dati, selezionare la **Aggiorna** collegamento. Per aggiornare automaticamente i dati, selezionare un intervallo nel **l'aggiornamento automatico** casella di riepilogo a discesa. Per esportare i dati di errore, selezionare la **Esporta in CSV** pulsante per creare un file con valori delimitati da virgole che è possibile aprire in un foglio di lavoro di Excel.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Configurare la diagnostica del servizio cloud dopo la distribuzione
Se si sta esaminando un problema con un servizio cloud che è già in esecuzione, è possibile raccogliere i dati che non sono state specificate prima della distribuzione originale del ruolo. In questo caso, è possibile iniziare a raccogliere i dati modificando le impostazioni in Esplora Server. È possibile configurare la diagnostica per una singola istanza o per tutte le istanze in un ruolo, a seconda del fatto che si apre la **configurazione di diagnostica** finestra di dialogo dal menu di scelta rapida per l'istanza o per il ruolo. Se si configura il nodo del ruolo, eventuali modifiche apportate si applicano a tutte le istanze. Se si configura il nodo dell'istanza, eventuali modifiche apportate si applicano solo a tale istanza.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Per configurare la diagnostica per un servizio cloud in esecuzione
1. In Esplora Server espandere il **servizi Cloud** nodo, quindi espandere l'elenco dei nodi per trovare il ruolo o istanza (o entrambi) che si desidera analizzare.
   
    ![Configurare la diagnostica](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Menu di scelta rapida per un nodo dell'istanza o un nodo del ruolo, selezionare **Aggiorna impostazioni diagnostica**e quindi selezionare le impostazioni di diagnostica che si desidera raccogliere.
   
    Per informazioni sulle impostazioni di configurazione, vedere la sezione **impostare le origini dati di diagnostica** in questo articolo. Per informazioni su come visualizzare i dati di diagnostica, vedere la sezione **visualizzare i dati di diagnostica** in questo articolo.
   
    Se si modifica la raccolta dei dati in Esplora Server, le modifiche rimangono valide fino a quando non una nuova distribuzione completa del servizio cloud. Se si usa il valore predefinito delle impostazioni di pubblicazione, le modifiche non vengono sovrascritti. Impostazione della pubblicazione predefinita è per aggiornare la distribuzione esistente, anziché eseguire una ridistribuzione completa. Per garantire che le impostazioni di cancellare in fase di distribuzione, passare al **impostazioni avanzate** scheda nella pubblicazione guidata e deselezionare le **aggiornamento distribuzione** casella di controllo. Quando esegue la ridistribuzione con tale casella di controllo deselezionata, le impostazioni vengono ripristinate le nel file con estensione wadcfgx (o wadcfg) definite tramite le **proprietà** editor per il ruolo. Se si aggiorna la distribuzione, Azure mantiene le impostazioni precedenti.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Risolvere i problemi relativi al servizio cloud di Azure
Se si verificano problemi con i progetti servizio cloud, ad esempio un ruolo che si blocca in uno stato "occupato", riciclato ripetutamente o genera un errore interno del server, sono disponibili strumenti e tecniche che è possibile usare per diagnosticare e risolvere il problema. Per esempi specifici di problemi e soluzioni comuni e per una panoramica dei concetti e strumenti che è possibile usare per diagnosticare e risolvere questi errori, vedere [i dati di diagnostica di calcolo Azure PaaS](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Domande e risposte
**Che cos'è la dimensione del buffer e devono essere grandi come?**

In ogni istanza di macchina virtuale, le quote limitano la quantità dei dati di diagnostica possono essere archiviati nel file system locale. Inoltre, specificare una dimensione del buffer per ogni tipo di dati di diagnostica che sono disponibili. Questa dimensione del buffer funge da quota individuale per quel tipo di dati. Per determinare la quota complessiva e la quantità di memoria rimanente, vedere la parte inferiore della finestra di dialogo per il tipo di dati di diagnostica. Se si specificano buffer più grandi o più tipi di dati, ci si avvicinerà la quota complessiva. È possibile modificare la quota complessiva, modificando il file di configurazione Diagnostics. wadcfg o wadcfgx. I dati di diagnostica vengono archiviati nel file system stesso come i dati dell'applicazione. Se l'applicazione usa una grande quantità di spazio su disco, è consigliabile non aumentare la quota di diagnostica complessiva.

**Che cos'è il periodo di trasferimento e quanto deve essere lungo?**

Il periodo di trasferimento è la quantità di tempo che trascorre tra dati acquisisce. Dopo ogni periodo di trasferimento, i dati vengono spostati dal file system locale in una macchina virtuale a tabelle nell'account di archiviazione. Se la quantità di dati raccolti supera la quota prima della fine del periodo di trasferimento, i dati meno recenti viene eliminati. Se si perdono dati perché i dati superano le dimensioni del buffer o la quota complessiva, è possibile ridurre il periodo di trasferimento.

**Quale fuso orario viene usato il timestamp?**

Timestamp usano il fuso orario locale del Data Center che ospita il servizio cloud. Vengono usate i seguenti tre colonne di timestamp nelle tabelle del log:

* **PreciseTimeStamp**: timestamp ETW dell'evento. Vale a dire, l'ora dell'evento viene registrato dal client.
* **TIMESTAMP**: il valore per **PreciseTimeStamp** arrotondati per difetto il limite di frequenza di caricamento. Ad esempio, se la frequenza di caricamento è 5 minuti e l'evento tempo 00:17:12, TIMESTAMP è 15:00:00.
* **Timestamp**: il timestamp in corrispondenza del quale l'entità è stata creata nella tabella di Azure.

**Come gestire i costi quando si raccolgono le informazioni di diagnostica?**

Le impostazioni predefinite (**livello di registrazione** impostata su **errore**, e **periodo di trasferimento** impostata su **1 minuto**) sono progettate per ridurre al minimo i costi. I costi calcolati aumentano quando si raccolgono più dati di diagnostica o si riduce il periodo di trasferimento. Non raccogliere più dati necessarie e non dimenticare di disabilitare la raccolta dei dati quando non è più necessario. È sempre possibile abilitarla nuovamente, anche in fase di esecuzione, come descritto in precedenza in questo articolo.

**Come si raccolgono i log di richieste non riuscite da IIS?**

Per impostazione predefinita, IIS non raccoglie i log di richieste non riuscite. È possibile configurare IIS per raccogliere i log di richieste non riuscite modificando il file Web. config per il ruolo web.

**Non vengono visualizzati le informazioni di traccia dai metodi RoleEntryPoint quali OnStart. Qual è il problema?**

I metodi della **RoleEntryPoint** vengono chiamati nel contesto di WAIISHost.exe, non in IIS. Informazioni di configurazione nel file Web. config che in genere abilitano la traccia non sono applicabili. Per risolvere questo problema, aggiungere un file con estensione config al progetto di ruolo web e denominare il file corrispondente all'assembly di output che contiene il **RoleEntryPoint** codice. Nel progetto di ruolo web predefinito, il nome del file con estensione config sarà Waiishost. Aggiungere le righe seguenti al file:

```
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

Nel **proprietà** impostare nella finestra di **copia in Directory di Output** proprietà **Copia sempre**.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sulle registrazioni di diagnostica in Azure, vedere [abilitare la diagnostica nei servizi Cloud di Azure e macchine virtuali](/azure/cloud-services/cloud-services-dotnet-diagnostics.md) e [abilita la registrazione diagnostica per le app Web nel servizio App di Azure](/azure/app-service/web-sites-enable-diagnostic-log).

