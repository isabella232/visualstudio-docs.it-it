---
title: Funzionalità avanzate
description: Informazioni sulle funzionalità avanzate che potrebbero essere più appropriate per gli sviluppatori esperti o per gli sviluppatori che hanno già familiarità con Visual Studio.
ms.custom: vs-acquisition
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2107eae3f2b25172daf85c625adfa7770f87c1a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102077"
---
# <a name="features-of-visual-studio"></a>Funzionalità di Visual Studio

L'articolo [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md) offre un'introduzione a Visual Studio. Questo articolo descrive funzionalità che potrebbero essere più appropriate per gli sviluppatori esperti o per gli sviluppatori che hanno già familiarità con Visual Studio.

## <a name="modular-installation"></a>Installazione modulare

Il programma di installazione modulare di Visual Studio consente di scegliere e installare *carichi di lavoro*. I carichi di lavoro sono gruppi di funzionalità necessarie per il linguaggio di programmazione o la piattaforma preferita. Questa strategia riduce il footprint dell'installazione di Visual Studio e questo significa anche una maggiore velocità di installazione e aggiornamento.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

Per altre informazioni sull'installazione di Visual Studio nel sistema, vedere [Installare Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Creare app abilitate per il cloud per Azure

Visual Studio offre un gruppo di strumenti che consentono di creare facilmente applicazioni abilitate per il cloud con tecnologia Microsoft Azure. È possibile gestire la configurazione, la compilazione, il debug, l'inserimento in pacchetti e la distribuzione di applicazioni e servizi in Microsoft Azure direttamente dall'IDE. Per ottenere gli strumenti e i modelli di progetto di Azure, selezionare il carico di lavoro **Sviluppo di Azure** quando si installa Visual Studio.

![Carico Sviluppo di Azure](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Dopo aver installato il carico di lavoro **Sviluppo di Azure**, vengono resi disponibili i modelli **Cloud** seguenti per C# nella finestra di dialogo **Nuovo progetto**:

![Modelli progetto cloud per Visual Studio](media/cloud-project-templates.png)

::: moniker-end

[Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) di Visual Studio consente di visualizzare e gestire le risorse cloud basate su Azure in Visual Studio. Queste risorse possono includere macchine virtuali, tabelle, database SQL e altro ancora. **Cloud Explorer** rende disponibili le risorse di Azure in tutti gli account gestiti con la sottoscrizione di Azure a cui si è connessi. E se una particolare operazione richiede il portale di Azure, **Cloud Explorer** specifica i collegamenti che consentono di accedere al punto del portale di Azure in cui si vuole arrivare.

![Cloud Explorer in Visual Studio](media/cloud-explorer.png)

È possibile sfruttare i servizi di Azure per le app usando **Servizi connessi**, ad esempio:

- [Servizio connesso di Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) in modo che gli utenti possano usare i propri account [Azure Active Directory](/azure/active-directory/active-directory-whatis) per connettersi alle app Web
- [Servizio connesso Archiviazione di Azure](/azure/vs-azure-tools-connected-services-storage) per archiviazione BLOB, code e tabelle
- [Servizio connesso Key Vault](/azure/key-vault/vs-key-vault-add-connected-service) per gestire i segreti per le app web

I **servizi connessi** disponibili dipendono dal tipo di progetto. Aggiungere un servizio facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliendo **Aggiungi** > **Servizio connesso**.

![Servizi connessi di Visual Studio](media/connected-services.png)

Per altre informazioni, vedere [Passare al cloud con Visual Studio e Azure](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Creare app per il Web

Il mondo moderno è dominato dal Web e Visual Studio può essere utile per scrivere app per questa piattaforma. È possibile creare app Web con ASP.NET, Node.js, Python, JavaScript e TypeScript. Visual Studio riconosce framework Web quali Angular, jQuery, Express e altri. ASP.NET Core e .NET Core supportano i sistemi operativi Windows, Mac e Linux. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) è un aggiornamento principale per MVC, WebAPI e SignalR e viene eseguito in Windows, Mac e Linux.  ASP.NET Core è stato completamente riprogettato per fornire uno stack .NET pulito e componibile per la compilazione di moderni servizi e app Web basati sul cloud.

Per altre informazioni, vedere [Strumenti Web moderni](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Creare app e giochi multipiattaforma

È possibile usare Visual Studio per compilare app e giochi per macOS, Linux e Windows, nonché per Android, iOS e altri [dispositivi mobili](https://visualstudio.microsoft.com/vs/mobile-app-development/).

- Compilare [app .NET Core](/dotnet/core/) eseguite in Windows, macOS e Linux.

- Compilare app per dispositivi mobili per iOS, Android e Windows in C# e F# usando [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/).

- Compilare giochi 2D e 3D in C# tramite [Visual Studio Tools per Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md).

- Compilare app C++ native per dispositivi iOS, Android e Windows. Condividere il codice comune nelle librerie create per iOS, Android e Windows usando [C++ per lo sviluppo multipiattaforma](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development).

## <a name="connect-to-databases"></a>Connettersi ai database

**Esplora server** consente di esplorare e gestire le istanze e gli asset di SQL Server in locale, in remoto e in Azure, Salesforce.com, Microsoft 365 e siti Web. Per aprire **Esplora server**, scegliere **Visualizza** > **Esplora server** dal menu principale. Per altre informazioni sull'uso di Esplora server, vedere [Aggiungere nuove connessioni](../data-tools/add-new-connections.md).

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) è un ambiente di sviluppo avanzato per SQL Server, database SQL di Azure e Azure SQL Data Warehouse. Consente di creare, eseguire il debug, gestire ed effettuare il refactoring di database. È possibile usare un progetto di database o direttamente un'istanza del database connesso locale o remota.

**Esplora oggetti di SQL Server** in Visual Studio offre una visualizzazione degli oggetti di database simile a quella di SQL Server Management Studio. Esplora oggetti di SQL Server consente di eseguire operazioni di amministrazione e progettazione di database semplici. Gli esempi di lavoro includono la modifica dei dati di tabella, il confronto degli schemi, l'esecuzione di query usando i menu contestuali direttamente da Esplora oggetti di SQL Server e altro ancora.

![Esplora oggetti di SQL Server](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Eseguire il debug del codice, testarlo e migliorarlo

Durante la scrittura del codice è necessario eseguirlo e testarlo per individuare eventuali bug e controllarne le prestazioni. Il sistema di debug all'avanguardia di Visual Studio consente di eseguire il debug del codice in esecuzione nel progetto locale, in un dispositivo remoto o in un [emulatore di dispositivo](../cross-platform/visual-studio-emulator-for-android.md). È possibile esaminare il codice un'istruzione alla volta e controllare le variabili man mano. È possibile impostare punti di interruzione che vengono raggiunti solo quando viene soddisfatta una condizione specificata. Le opzioni di debug possono essere gestite nell'editor del codice senza uscire dal codice. Per altri dettagli sul debug in Visual Studio, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md).

Per altre informazioni su come migliorare le prestazioni delle app, vedere la funzionalità di [profilatura](../profiling/profiling-feature-tour.md) di Visual Studio.

Per le operazioni di [test](../test/improve-code-quality.md), Visual Studio supporta il testing unità, Live Unit Testing, IntelliTest, test di carico e delle prestazioni e altro ancora. Visual Studio include anche funzionalità avanzate di [analisi del codice](../code-quality/code-analysis-for-managed-code-overview.md) per individuare difetti di progettazione, sicurezza e di altro tipo.

## <a name="deploy-your-finished-application"></a>Distribuire l'applicazione completata

Quando l'applicazione è pronta per la distribuzione a utenti o clienti, Visual Studio offre gli strumenti necessari per eseguire questa operazione. È possibile distribuire in Microsoft Store, in un sito SharePoint o con le tecnologie InstallShield o Windows Installer. Tutti gli strumenti sono accessibili dall'IDE. Per altre informazioni, vedere [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Gestire il codice sorgente e collaborare con altri utenti

È possibile gestire il codice sorgente in repository GIT ospitati da qualsiasi provider, incluso GitHub. In alternativa, usare [Azure DevOps Services](/azure/devops/index) per gestire il codice insieme ai bug e agli elementi di lavoro per l'intero progetto. Per altre informazioni sulla gestione dei repository GIT in Visual Studio con Team Explorer, vedere [Get Started with Git and Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) (Introduzione a GIT e Azure Repos). Visual Studio include anche altre funzionalità predefinite di controllo del codice sorgente. Per altre informazioni su tali funzionalità, vedere il post del blog [New Git Features in Visual Studio](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/) (Nuove funzionalità Git in Visual Studio).

Azure DevOps Services include servizi basati su cloud per la pianificazione, l'hosting, l'automazione e la distribuzione di software e per consentire la collaborazione nei team. Azure DevOps Services supporta repository Git (controllo di versione distribuito) e il controllo della versione di Team Foundation (controllo di versione centralizzato). I servizi supportano le pipeline per la compilazione e il rilascio continui (CI/CD) del codice archiviato nei sistemi di controllo della versione. Azure DevOps Services supporta anche le metodologie di sviluppo Scrum, CMMI e Agile.

Team Foundation Server (TFS) è l'hub di gestione del ciclo di vita delle applicazioni per Visual Studio. Consente a tutte le parti interessate di partecipare al processo di sviluppo usando un'unica soluzione. TFS è utile anche per la gestione di team e progetti eterogenei.

Se in rete è presente un'organizzazione di Azure DevOps o Team Foundation Server, è possibile connettersi usando la finestra **Team Explorer** in Visual Studio. Da questa finestra è possibile archiviare o estrarre il codice dal controllo del codice sorgente, gestire gli elementi di lavoro, avviare le compilazioni e accedere alle chat team e alle aree di lavoro. È possibile aprire **Team Explorer** dalla casella di ricerca o dal menu principale tramite **Visualizza** > **Team Explorer** o **Team** > **Gestisci connessioni**.

L'immagine seguente illustra la finestra **Team Explorer** per una soluzione ospitata in Azure DevOps Services.

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer_devops.png)

È anche possibile automatizzare il processo di compilazione per compilare il codice che gli sviluppatori del team hanno archiviato nel controllo della versione. È possibile ad esempio compilare uno o più progetti di notte o ogni volta che il codice viene controllato. Per altre informazioni, vedere [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="extend-visual-studio"></a>Estensione di Visual Studio

Se Visual Studio non include la funzionalità esatta di cui si ha bisogno, è possibile aggiungerla. È possibile personalizzare l'IDE in base al flusso e allo stile di lavoro personali, aggiungere il supporto per strumenti esterni non ancora integrati in Visual Studio e modificare le funzionalità esistenti per aumentare la produttività. Per trovare la versione più recente degli strumenti di estendibilità di Visual Studio (VS SDK), vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

È possibile usare .NET Compiler Platform ("Roslyn") per scrivere analizzatori di codice e generatori di codice personalizzati. Tutto ciò che serve è disponibile nella pagina di [Roslyn](https://github.com/dotnet/Roslyn).

Cercare le [estensioni esistenti](https://marketplace.visualstudio.com/vs) per Visual Studio create dagli sviluppatori Microsoft, nonché dalla community di sviluppo.

Per altre informazioni sull'estensione di Visual Studio, vedere [Estendi Visual Studio IDE](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Vedi anche

- [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Novità di Visual Studio 2017](../ide/whats-new-visual-studio-2017.md)
- [Novità di Visual Studio 2019](../ide/whats-new-visual-studio-2019.md)
