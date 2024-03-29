---
title: Funzionalità avanzate
description: Informazioni sulle funzionalità avanzate che potrebbero essere più appropriate per gli sviluppatori esperti o per gli sviluppatori che hanno già familiarità con Visual Studio.
ms.custom: vs-acquisition
ms.date: 10/01/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 136c66296e1980f3faae31dc0d5fc4c16fbaff57
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431484"
---
# <a name="features-of-visual-studio"></a>Funzionalità di Visual Studio

Questo articolo descrive le funzionalità per sviluppatori esperti o sviluppatori che hanno già familiarità con Visual Studio. Per un'introduzione di base Visual Studio, vedere la panoramica dell Visual Studio [IDE](../get-started/visual-studio-ide.md).

## <a name="modular-installation"></a>Installazione modulare

Nel Visual Studio del programma di installazione modulare è possibile scegliere e installare i *carichi di lavoro* desiderati. I carichi di lavoro sono gruppi di funzionalità che devono essere utilizzati da linguaggi o piattaforme di programmazione. Questa strategia modulare consente di ridurre il Visual Studio di installazione, in modo da installare e aggiornare più rapidamente.

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

Per altre informazioni sull'installazione di Visual Studio nel sistema, vedere [Installare Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-azure-apps"></a>Creare app di Azure abilitate per il cloud

Visual Studio dispone di una suite di strumenti per creare facilmente Microsoft Azure applicazioni abilitate per il cloud. È possibile configurare, compilare, eseguire il debug, creare pacchetti e distribuire app e servizi di Azure direttamente dal Visual Studio di sviluppo integrato (IDE). Per ottenere gli strumenti e i modelli di progetto di Azure, selezionare il carico di lavoro **Sviluppo di Azure** quando si installa Visual Studio.

::: moniker range="<=vs-2019"
![Screenshot del carico di lavoro sviluppo di Azure nel Programma di installazione di Visual Studio.](../data-tools/media/azure-development-workload.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/azure-development-workload.png" alt-text="Screenshot del carico di lavoro sviluppo di Azure selezionato nel Programma di installazione di Visual Studio." border="false":::
::: moniker-end

::: moniker range="vs-2017"

Dopo aver installato il carico di lavoro **Sviluppo di Azure**, vengono resi disponibili i modelli **Cloud** seguenti per C# nella finestra di dialogo **Nuovo progetto**:

![Modelli progetto cloud per Visual Studio](media/cloud-project-templates.png)

::: moniker-end

::: moniker range="vs-2019"

In Visual Studio [usare](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) Cloud Explorer per visualizzare e gestire le risorse cloud basate su Azure. Le risorse cloud possono includere macchine virtuali (VM), tabelle e SQL database. **Cloud Explorer** mostra le risorse di Azure in tutti gli account nella sottoscrizione di Azure a cui si è connessi. Se un'operazione richiede portale di Azure, **Cloud Explorer** contiene collegamenti alla posizione nel portale che è necessario passare.

![Screenshot della Cloud Explorer in Visual Studio.](media/cloud-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"
> [!Important]
> La Cloud Explorer viene ritirata nel Visual Studio 2022. Per altre informazioni, vedere [Gestire le risorse associate agli account Azure in Visual Studio Cloud Explorer](../azure/vs-azure-tools-resources-managing-with-cloud-explorer.md?view=vs-2022&preserve-view=true).
>
> Usare il portale di Azure per accedere alle risorse di Azure in base alle esigenze. È possibile continuare a usare il nodo azure di Esplora server nelle versioni precedenti di Visual Studio.
>
::: moniker-end

È possibile usare i servizi di Azure per le app **aggiungendo Servizi connessi**, ad esempio:

- [Servizio connesso Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service)per usare [Azure Active Directory](/azure/active-directory/active-directory-whatis) (Azure AD) per connettersi alle app Web
- [Servizio connesso Archiviazione di Azure](/azure/vs-azure-tools-connected-services-storage) per archiviazione BLOB, code e tabelle
- [Servizio connesso Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) per gestire i segreti per le app web

I **servizi connessi** disponibili dipendono dal tipo di progetto. Aggiungere un servizio facendo clic con il pulsante destro del mouse sul **progetto** Esplora soluzioni e scegliendo **Aggiungi**  >  **servizio connesso**.

::: moniker range="<=vs-2019"
![Screenshot che mostra Visual Studio Servizi connessi.](media/connected-services.png)
::: moniker-end

::: moniker range=">=vs-2022"

Nella schermata **Servizi connessi** selezionare il collegamento o il segno più per **Aggiungere una dipendenza del servizio**. Nella schermata **Aggiungi dipendenza** selezionare il servizio da aggiungere e seguire le schermate per connettersi alla sottoscrizione e al servizio di Azure.

:::image type="content" source="media/vs-2022/connected-services.png" alt-text="Screenshot che mostra Servizi connessi dipendenze." border="false":::

::: moniker-end

Per altre informazioni, vedere [Passare al cloud con Visual Studio e Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-web-apps"></a>Creare app Web

Visual Studio consente di scrivere app per il Web. È possibile creare app Web usando ASP.NET, Node.js, Python, JavaScript e TypeScript. Visual Studio supporta molti framework Web, ad esempio Angular, jQuery ed Express.

[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) e .NET Core vengono eseguiti in Windows, Mac e Linux. ASP.NET Core è un aggiornamento importante di MVC, WebAPI e SignalR. ASP.NET Core è progettato da zero per fornire uno stack .NET snello e componibile per la creazione di servizi e app Web moderne basate sul cloud.

Per altre informazioni, vedere [Strumenti Web moderni](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Creare app e giochi multipiattaforma

Visual Studio creare app e giochi per macOS, Linux e Windows e per Android, iOS e altri [dispositivi mobili.](https://visualstudio.microsoft.com/vs/mobile-app-development/) Con Visual Studio, è possibile compilare:

- [App .NET Core](/dotnet/core/) eseguite in Windows, macOS e Linux.

- App per dispositivi mobili per iOS, Android e Windows in C# e F# usando [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Giochi 2D e 3D in C# usando [Visual Studio Tools per Unity](/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity).

- App C++ native per dispositivi iOS, Android e Windows applicazioni. Condividere codice comune nelle librerie iOS, Android e Windows usando [C++ per lo sviluppo multipiattaforma.](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)

## <a name="connect-to-databases"></a>Connettersi ai database

**Esplora server** consente di esplorare e gestire le istanze e gli asset del server in locale, in remoto e in Azure, Microsoft 365, Salesforce.com e siti Web. Per aprire **Esplora server**, scegliere **Visualizza Esplora server**  >  . Per altre informazioni sull'uso di Esplora server, vedere [Aggiungere nuove connessioni](../data-tools/add-new-connections.md).

**SQL Server Esplora oggetti** offre una visualizzazione degli oggetti di database, simile a SQL Server Management Studio. Con SQL Server Esplora oggetti, è possibile eseguire attività di progettazione e amministrazione del database leggere. Ad esempio, la modifica dei dati delle tabelle, il confronto degli schemi e l'esecuzione di query tramite menu contestuali.

::: moniker range="<=vs-2019"
![Screenshot che mostra la finestra SQL Server Esplora oggetti di lavoro.](../ide/media/vs2015_sqlobjectexplorer.png)
::: moniker-end

::: moniker range=">=vs-2022"

Per aprire **SQL Server Esplora oggetti,** selezionarne l'icona nella  parte superiore della finestra  Esplora server oppure selezionare Visualizza SQL Server Esplora oggetti dal menu Visual Studio >  superiore.

:::image type="content" source="media/vs-2022/sql-server-object-explorer.png" alt-text="Screenshot che mostra la finestra SQL Server Esplora oggetti di lavoro." border="false":::

::: moniker-end

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) è un ambiente di sviluppo avanzato per SQL Server, database SQL di Azure e Azure SQL Data Warehouse. Con SSDT è possibile compilare, eseguire il debug, gestire ed effettuare il refactoring dei database. È possibile usare un progetto di database o direttamente un'istanza del database connesso locale o remota. Per ottenere SSDT, usare il Programma di installazione di Visual Studio per installare il carico di lavoro Di **archiviazione ed elaborazione** dati.

## <a name="debug-test-and-improve-your-code"></a>Eseguire il debug del codice, testarlo e migliorarlo

Quando si scrive codice, è necessario eseguirlo e testarlo per verificare la verifica di bug e prestazioni. Con Visual Studio di debug di , è possibile eseguire il debug del codice in esecuzione nel progetto locale, in un dispositivo remoto o in un [emulatore di dispositivo](../cross-platform/visual-studio-emulator-for-android.md). Eseguire il codice un'istruzione alla volta ed esaminare le variabili man in base alle istruzioni. Oppure impostare punti di interruzione che vengono raggiunto solo quando una condizione specificata è true. È possibile gestire le opzioni di debug nell'editor di codice stesso, in modo da non lasciare il codice.

Per altre informazioni sul debug in Visual Studio, vedere [Prima di tutto il debugger](../debugger/debugger-feature-tour.md).

Per migliorare le prestazioni dell'app, vedere la Visual Studio [di profilatura.](../profiling/profiling-feature-tour.md)

Visual Studio offre opzioni [di test](../test/improve-code-quality.md) come unit test, Live Unit Testing, IntelliTest e test di carico e prestazioni. Visual Studio ha anche funzionalità avanzate [di analisi del](../code-quality/code-analysis-for-managed-code-overview.md) codice per individuare la progettazione, la sicurezza e altri difetti.

## <a name="deploy-your-finished-application"></a>Distribuire l'applicazione completata

Visual Studio strumenti per distribuire l'app a utenti o clienti tramite le tecnologie Microsoft Store, SharePoint o InstallShield o Windows Installer. È possibile accedere a tutte queste opzioni tramite l Visual Studio IDE. Per altre informazioni, vedere [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gestire il codice sorgente e collaborare con altri utenti

In Visual Studio, è possibile gestire il codice sorgente nei repository Git ospitati da qualsiasi provider, incluso GitHub. È anche possibile cercare un Azure DevOps Server a cui connettersi.

::: moniker range=">=vs-2022"

Per informazioni dettagliate complete, vedere [l'esperienza Git in Visual Studio](../version-control/git-with-visual-studio.md) pagina e la Visual Studio di navigazione della documentazione del controllo [della](../version-control/index.yml) versione. Per un'esercitazione dettagliata su come connettersi a un repository Git o Azure DevOps usando Visual Studio, vedere la pagina Aprire un progetto da un [repository.](../get-started/tutorial-open-project-from-repo.md?view=vs-2022&preserve-view=true)

> [!TIP]
> Microsoft continua a creare il set di funzionalità Git e a eseguire l'iterazione in base ai commenti e suggerimenti. Per altre informazioni su un aggiornamento delle funzionalità recente insieme a un collegamento al sondaggio in cui è possibile condividere i commenti e suggerimenti, vedere il post di blog [Supporto per più repo in Visual Studio.](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/)

::: moniker-end

::: moniker range="vs-2019"

La modalità di apertura di un progetto da un GitHub usando Visual Studio 2019 dipende dalla versione disponibile. In particolare, se è stata installata la versione [**16.8**](/visualstudio/releases/2019/release-notes/) o successiva, è disponibile una nuova esperienza [Git](../ide/git-with-visual-studio.md) Visual Studio completamente integrata. Per altre informazioni, vedere la pagina della [documentazione Visual Studio controllo della versione.](../version-control/index.yml)

Per un'esercitazione dettagliata su come connettersi a un repository Git o Azure DevOps usando Visual Studio, vedere la pagina Aprire un progetto da un [repository.](../get-started/tutorial-open-project-from-repo.md?view=vs-2019&preserve-view=true)

::: moniker-end

::: moniker range="vs-2017"

Per altre informazioni sulla gestione dei repository Git in Visual Studio **usando** Team Explorer , vedere Introduzione a Git [e Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio). Per altre informazioni sulle Visual Studio funzionalità di controllo del codice sorgente incorporate, vedere il post di blog Sulle funzionalità [git in Visual Studio.](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/)

[Azure DevOps Services](/azure/devops/index) è una suite di servizi basati sul cloud che pianificano, ospitano, automatizzano e distribuiscono software e promuovono la collaborazione in team. DevOps Services supporta sia il GitHub della versione distribuita che controllo della versione di Team Foundation controllo della versione centralizzato (TFVC). DevOps Services fornisce pipeline di compilazione e rilascio continue (CI/CD) per il codice archiviato nei sistemi di controllo della versione. DevOps Services supporta anche metodologie di sviluppo Scrum, CMMI e Agile. È possibile usare DevOps Services per gestire il codice insieme ai bug e agli elementi di lavoro per il progetto.

Team Foundation Server (TFS) è l'hub di gestione del ciclo di vita delle applicazioni per Visual Studio. Consente a tutte le parti interessate di partecipare al processo di sviluppo usando un'unica soluzione. TFS è utile anche per la gestione di team e progetti eterogenei.

È possibile connettersi a un'Azure DevOps aziendale o a un Team Foundation Server nella rete tramite la finestra Visual Studio **Team Explorer** rete. Dalla finestra **Team Explorer** è possibile archiviare o rimuovere il codice dal controllo del codice sorgente, gestire gli elementi di lavoro, avviare le compilazioni e accedere alle sale e alle aree di lavoro del team. Per aprire **Team Explorer**, usare la casella di ricerca o **selezionare**  >  **Visualizza Team Explorer**.

L'immagine seguente **mostra Team Explorer** finestra di configurazione per una soluzione ospitata in Azure DevOps Services.

![Screenshot della finestra Visual Studio Team Explorer a un progetto.](../ide/media/vs2017_teamexplorer_devops.png)

Azure DevOps è un hub di gestione del ciclo di vita delle applicazioni per Visual Studio. Azure DevOps consente a tutti gli utenti coinvolti nel processo di sviluppo di partecipare usando un'unica soluzione. Azure DevOps è utile anche per la gestione di team e progetti eterogenei.

È possibile connettersi a un'Azure DevOps aziendale o Azure DevOps Server rete  tramite la finestra Team Explorer in Visual Studio. Dalla finestra **Team Explorer** è possibile archiviare o rimuovere il codice dal controllo del codice sorgente, gestire gli elementi di lavoro, avviare le compilazioni e accedere alle sale e alle aree di lavoro del team. Per aprire **Team Explorer**, usare la casella di ricerca o **selezionare**  >  **Visualizza Team Explorer**.

È anche possibile automatizzare il processo di compilazione per compilare codice che gli sviluppatori archiviano nel controllo della versione. Ad esempio, è possibile compilare uno o più progetti ogni notte o ogni volta che viene archiviato un determinato codice. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

- Se Visual Studio non ha la funzionalità esatta necessaria, è possibile aggiungerla. Personalizzare l'IDE in base al flusso di lavoro e allo stile, aggiungere il supporto per gli strumenti esterni non integrati con Visual Studio e modificare le funzionalità esistenti per aumentare la produttività. Per la versione più recente di Visual Studio Extensibility Tools (VS SDK), vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

- È possibile usare il .NET Compiler Platform *Roslyn per* scrivere analizzatori di codice e generatori di codice personalizzati. Tutto ciò che serve è disponibile nella pagina di [Roslyn](https://github.com/dotnet/Roslyn).

- Trovare [le estensioni esistenti](https://marketplace.visualstudio.com/vs) per Visual Studio create da sviluppatori Microsoft e dalla community Visual Studio sviluppo.

- Per altre informazioni sull'estensione di Visual Studio, vedere [Estendi Visual Studio IDE](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Vedi anche

- [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Novità di Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Novità di Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
- [Novità di Visual Studio 2022](whats-new-visual-studio-2022.md)