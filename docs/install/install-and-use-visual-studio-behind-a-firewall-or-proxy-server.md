---
title: Installare e usare prodotti protetti da un firewall o un server proxy
description: Verificare gli URL di dominio, le porte e i protocolli da aggiungere a un elenco di elementi consentiti o da aprire se l'organizzazione usa un firewall o un server proxy
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c33de2ef29394cc09b6a65072439c745ca24af94
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594097"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Installare e usare Visual Studio e i servizi di Azure protetti da un firewall o un server proxy

Se un utente o un'organizzazione usa misure di sicurezza, come un firewall o un server proxy, è possibile che vi siano URL di dominio da aggiungere a un elenco di indirizzi consentiti, così come porte e protocolli da aprire per ottenere un'esperienza ottimale durante l'installazione e l'uso di Visual Studio e dei servizi di Azure.

* **[Installare Visual Studio](#install-visual-studio)** : queste tabelle includono gli URL di dominio da aggiungere a un elenco Consenti, in modo da poter accedere a tutti i componenti e i carichi di lavoro desiderati.

* **[Usare Visual Studio e i servizi di Azure](#use-visual-studio-and-azure-services)** : questa tabella include gli URL di dominio da aggiungere a un elenco Consenti e le porte e i protocolli da aprire per poter accedere a tutte le funzionalità e i servizi desiderati.

> [!NOTE]
> Questo articolo è stato scritto per Visual Studio in Windows, ma alcune informazioni sono applicabili anche all'[installazione di Visual Studio per Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) dietro un firewall o un server proxy.

## <a name="install-visual-studio"></a>Installare Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>URL da aggiungere a un elenco di indirizzi consentiti

Dato che il programma di installazione di Visual Studio scarica i file da vari domini e dai rispettivi server di download, questi sono gli URL di dominio che possono essere aggiunti a un elenco di indirizzi consentiti considerati attendibili nell'interfaccia utente o negli script di distribuzione.

#### <a name="microsoft-domains"></a>Domini Microsoft

| Dominio | Scopo |
| - | - |
| go.microsoft.com | Risoluzione degli URL di installazione |
| aka.ms | Risoluzione degli URL di installazione |
| download.visualstudio.microsoft.com | Percorso di download dei pacchetti di installazione |
| download.microsoft.com | Percorso di download dei pacchetti di installazione |
| download.visualstudio.com | Percorso di download dei pacchetti di installazione |
| dl.xamarin.com | Percorso di download dei pacchetti di installazione |
| xamarin-downloads.azureedge.net | Percorso dell'elenco di download dei pacchetti di Android SDK |
| marketplace.visualstudio.com | Percorso di download delle estensioni di Visual Studio |
| visualstudio.microsoft.com | Percorso della documentazione |
| docs.microsoft.com | Percorso della documentazione |
| msdn.microsoft.com | Percorso della documentazione |
| www\.microsoft.com | Percorso della documentazione |
| \*.windows.net | Percorso di accesso |
| \*.microsoftonline.com | Percorso di accesso |
| \*.live.com | Percorso di accesso |
| | |

#### <a name="non-microsoft-domains"></a>Domini non Microsoft

| Dominio | Installa questi carichi di lavoro |
| - | - |
| archive.apache.org | Sviluppo di app per dispositivi mobili con JavaScript (Cordova) |
| cocos2d-x.org | Sviluppo di giochi con C++ (Cocos) |
| download.epicgames.com | Sviluppo di giochi con C++ (Unreal Engine) |
| download.oracle.com | Sviluppo per dispositivi mobili con JavaScript (Java SDK) <br /><br />Sviluppo per dispositivi mobili con .NET (Java SDK) |
| download.unity3d.com | Sviluppo di giochi con Unity (Unity) |
| netstorage.unity3d.com | Sviluppo di giochi con Unity (Unity) |
| dl.google.com | Sviluppo per dispositivi mobili con JavaScript (Android SDK e NDK, emulatore) <br /><br />Sviluppo per dispositivi mobili con .NET (Android SDK e NDK, emulatore) |
| www\.incredibuild.com | Sviluppo di giochi con C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Sviluppo di giochi con C++ (IncrediBuild) |
| www\.python.org | Sviluppo Python (Python) <br /><br />Applicazioni analitiche e di analisi scientifica dei dati (Python) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Usare Visual Studio e i servizi di Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>URL da aggiungere a un elenco di indirizzi consentiti e porte e protocolli da aprire

Per assicurarsi di disporre dell'accesso a tutte le informazioni necessarie quando si usano Visual Studio o i servizi di Azure protetti da un firewall o un server proxy, di seguito sono riportati gli URL che è consigliabile aggiungere a un elenco di indirizzi consentiti e le porte e i protocolli che è possibile aprire.

| Servizio o scenario | Endpoint DNS | Protocollo | Port | Descrizione |
| - | - | - | - | - |
| URL<br>risoluzione | go.microsoft.com<br><br>aka.ms | | | Usato per abbreviare gli URL, risolti quindi in URL più lunghi |
| Pagina iniziale | vsstartpage.blob.core.windows.net | | 443 | Usato per visualizzare le Novità per gli sviluppatori nella pagina iniziale (solo Visual Studio 2017) |
| Servizio di<br> Notifica <br>Servizio | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443 | Usato per filtrare un elenco globale delle notifiche in un elenco applicabile solo a specifici tipi di computer/scenari di utilizzo |
| Estensione <br>per le estensioni | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | | 443 | Usato per fornire notifiche quando è disponibile un aggiornamento per un'estensione installata <br><br> Usato come posizione di accesso |
| Integrazione di <br>Integration | az861674.vo.msecnd.net | | 443<br> | Usato per configurare nuovi progetti per l'invio di dati di utilizzo all'account registrato di Application Insights |
| CodeLens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | | 443 | Usato per fornire informazioni nell'editor sull'ultimo aggiornamento di un file, la sequenza temporale delle modifiche, gli elementi di lavoro a cui sono associate le modifiche, gli autori e altro |
| Sperimentale <br>funzionalità sperimentali | visualstudio-devdiv-c2s.msedge.net | | 80 | Usato per attivare nuove funzionalità sperimentali o modifiche di funzionalità |
| "Badge" di identità <br>(nome utente e avatar)<br>e <br>Roaming delle impostazioni | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net | | 443 | Usato per visualizzare il nome e l'avatar dell'utente nell'IDE <br><br> Usato per assicurare il roaming delle modifiche delle impostazioni da un computer a un altro |
| Impostazioni remote | az700632.vo.msecnd.net | | 443 | Usato per disattivare le estensioni che potrebbero causare problemi in Visual Studio |
| Strumenti di Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https | 443 | Usato per gli scenari dello store di app per Windows |
| Definizione dello <br>Individuazione <br><br>Definizione dello <br>Definizione<br><br>Definizione dello <br>Supporto per <br>le risorse di Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http<br>https<br><br>http<br><br>https | 80<br>443 <br><br> 443<br><br>443 | Usato per individuare e scaricare gli schemi JSON che l'utente può usare durante la modifica di documenti JSON <br><br>Usato per ottenere lo schema di convalida dei metadati per JSON<br><br>Usato per ottenere lo schema corrente per i modelli di distribuzione di Azure Resource Manager |
| Individuazione di <br>individuazione | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https<br><br>http/s<br><br>https | 443<br><br>80/443<br><br>443 | Necessario per la ricerca di pacchetti NPM e usato per l'installazione di pacchetti di script sul lato client nei progetti Web |
| Ricerca di pacchetti<br> icone<br><br>Ricerca di pacchetti <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https | 80<br><br>443<br>80<br>443 | Fornisce l'icona predefinita per i pacchetti Bower  <br><br>Offre la possibilità di cercare pacchetti Bower |
| NuGet<br><br>Pacchetto NuGet<br> individuazione | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https<br><br>http/s | 443<br><br>80/443<br> | Usato per verificare i pacchetti NuGet firmati.<br><br>Richiesto per la ricerca pacchetti e versioni NuGet |
| Informazioni sul repository GitHub | api.github.com | https | 443 | Necessario per ottenere informazioni aggiuntive sui pacchetti Bower |
| Linter Web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http | 80 | |
| Cookiecutter<br>Individuazione di modelli<br>individuazione <br><br>Cookiecutter <br>Creazione di progetti<br> di Explorer | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https | 443<br> | Usato per individuare modelli online dal feed consigliato e dai repository GitHub <br><br>Usato per creare un progetto da un modello di Cookiecutter che richiede un'unica installazione su richiesta di un pacchetto di Python Cookiecutter dall'indice dei pacchetti di Python (PyPI) |
| Pacchetto Python <br>individuazione<br><br>Pacchetto Python <br>Gestione di<br><br>Nuovo <br>Python <br> Progetto <br>modelli | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https | 443 | Offre la possibilità di cercare pacchetti pip<br><br>Usato per installare automaticamente pip, se mancante <br><br>Usato per trovare la corrispondenza tra i nuovi modelli di progetto Python seguenti e gli URL di modelli di Cookiecutter:<br> - Progetto Classificatore<br>- Progetto Clustering <br> - Progetto Regressione <br> - PyGame con PyKinect <br> - Progetto Pyvot |
| Componente aggiuntivo <br>componente aggiuntivo <br> Manifest <br>Verifica <br>Servizio | verificationservice.osi.office.net | https | 443 | Usato per convalidare i manifesti per i componenti aggiuntivi Web di Office |
| Componenti aggiuntivi di <br>Componenti aggiuntivi di Office | sharepoint.com | https | 443 | Usato per pubblicare e testare i componenti aggiuntivi di SharePoint e Office in SharePoint Online |
| Gestione flusso di lavoro <br>di test di<br> Host | | http | 12292 | Regola del firewall che viene creata automaticamente per il test di componenti aggiuntivi di SharePoint con i flussi di lavoro |
| Statistiche di affidabilità <br>raccolte automaticamente <br>e altri programmi <br>Analisi utilizzo <br>software (CEIP)<br> per Azure SDK e <br>per gli strumenti SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https | 443 | Usato per inviare le statistiche di affidabilità (dati su arresti anomali/blocchi) dall'utente a Microsoft. I dump effettivi di arresto anomalo/blocco verranno ancora caricati se è abilitata la Segnalazione errori Windows. Verranno omesse solo le informazioni statistiche. <br>Usato per individuare i modelli di utilizzo anonimo per l'estensione Azure Tools SDK per Visual Studio e per i modelli di utilizzo per gli strumenti SQL per Visual Studio |
| Visual Studio <br> Analisi utilizzo <br>di Visual Studio <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https | 443 | Usato per la raccolta di modelli di utilizzo e log degli errori anonimi <br><br>Usato per tenere traccia dei problemi di blocco dell'interfaccia utente |
| Creazione e<br>gestione di <br>risorse di Azure | management.azure.com <br>management.core.windows.net | https | 443 | Usato per la creazione di siti Web di Azure o altre risorse per supportare la pubblicazione di applicazioni Web, funzioni di Azure o processi Web |
| Controlli della disponibilità di strumenti <br>di pubblicazione Web aggiornati e <br>indicazioni | marketplace.visualstudio.com | https | 443 | Usato per controllare la disponibilità di strumenti di pubblicazione aggiornati. Se disabilitato, potrebbe non essere visualizzata una potenziale estensione per la pubblicazione Web consigliata |
| Informazioni sugli endpoint per la <br>creazione di risorse di Azure aggiornati | \*.blob.core.windows.net | https | 443 | Usato per aggiornare gli endpoint usati per la creazione di risorse di Azure per alcuni servizi di Azure. Se disabilitato, vengono usate le ultime posizioni degli endpoint scaricati o predefiniti |
| Debug remoto e <br>profilatura remota di <br>Siti Web di Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Usato per collegare il debugger remoto a Siti Web di Azure. Se disabilitato, il collegamento del debugger remoto a Siti Web di Azure non funzionerà |
| Active Directory <br>Graph | graph.windows.net | https | 443 | Usato per eseguire il provisioning di nuove applicazioni di Azure Active Directory. Usato anche dal provider di servizi connessi Office 365 MSGraph |
| Funzioni di Azure <br>Controllo degli aggiornamenti <br>Controlla | functionscdn.azureedge.net | https | 443 | Usato per controllare la disponibilità di versioni aggiornate dell'interfaccia della riga di comando di Funzioni di Azure. Se disabilitato, verrà usata una copia dell'interfaccia della riga di comando memorizzata nella cache (o la copia inclusa nel componente Funzioni di Azure) |
| Cordova | npmjs.org<br>gradle.org | http/s | 80/443 | Viene usato HTTP per il download di Gradle durante la compilazione; Viene usato HTTPS per includere i plug-in Cordova nei progetti |
| Cloud Explorer | 1. &#60;endpoint clustere&#62; <br>Service Fabric <br>2. &#60;endpoint di gestione&#62;<br>Cloud Exp generale <br>3. &#60;endpoint grafico&#62;<br>Cloud Exp generale<br>4. &#60;endpoint account di archiviazione&#62;<br>Nodi di archiviazione <br>5. &#60;URL portale di Azure&#62;<br>Cloud Exp generale <br>6. &#60;endpoint insieme di credenziale delle chiavi&#62; <br>Nodi VM di Azure Resource Manager<br>7. &#60;IndirizzoIPpubblicoCluster&#62;<br>Debug remoto di Service Fabric e tracce ETW | <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7: tcp | 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dynamic | 1. esempio: test12.eastus.cloudapp.com<br>2. Recupera le sottoscrizioni e recupera/gestisce le risorse di Azure<br>3. Recupera Azure Stack sottoscrizioni<br>4. gestisce le risorse di archiviazione, ad esempio: mystorageaccount.blob.core.windows.net<br>5. opzione del menu di scelta rapida "Apri nel portale" (apre una risorsa nella portale di Azure)<br>6. crea e USA insiemi di credenziali delle chiavi per il debug della macchina virtuale (ad esempio: myvault.vault.azure.net) <br><br>7. alloca in modo dinamico un blocco di porte in base al numero di nodi nel cluster e alle porte disponibili. <br><br>Un blocco di porte tenterà di ottenere tre volte il numero di nodi con almeno 10 porte.<br><br>Per le tracce di streaming, viene effettuato un tentativo di ottenere il blocco di porte a partire da 810. Se un blocco qualsiasi di porte è già in uso, viene effettuato un tentativo di ottenere il blocco successivo e così via. (Se il servizio di bilanciamento del carico è vuoto, molto probabilmente vengono usate le porte a partire da 810) <br><br>In modo analogo per il debug, vengono riservati quattro set di blocchi di porte: <br>- connectorPort: 30398, <br>- forwarderPort: 31398, <br>- forwarderPortx86: 31399,<br>- fileUploadPort: 32398<br> |
| Servizi cloud | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;servizio cloud utente&#62;.cloudapp.net <br> &#60;macchina virtuale utente&#62;.&#60;regione&#62;.azure.com | 1. rdp <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6. a) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1. Desktop remoto alla VM dei servizi cloud <br><br> 2. componente dell'account di archiviazione della configurazione di diagnostica privata <br><br> 3. portale di Azure <br><br> 4. Esplora server-archiviazione &#42; di Azure è un account di archiviazione denominato del cliente  <br><br> 5. collegamenti per aprire il portale &#47; scaricare il file di &#47; impostazioni di pubblicazione del certificato di sottoscrizione <br><br>6. a) Porta locale del connettore per il debug remoto per il servizio cloud e la macchina virtuale<br> 6. b) Porta pubblica del connettore per il debug remoto per il servizio cloud e la macchina virtuale <br> 6. c) Porta locale del server di inoltro per il debug remoto per il servizio cloud e la macchina virtuale <br> 6. d) Porta pubblica del server di inoltro per il debug remoto per il servizio cloud e la macchina virtuale  <br> 6. e) Porta locale del caricatore di file per il debug remoto per il servizio cloud e la macchina virtuale <br> 6. f) Porta pubblica del caricatore di file per il debug remoto per il servizio cloud e la macchina virtuale |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https | 443 | 1. documentazione <br><br> 2. creare la funzionalità cluster <br><br>3. &#42; è il nome dell'insieme di credenziali delle chiavi di Azure, ad esempio-test11220180112110108.Vault.Azure.NET  <br><br>  4. &#42; è dinamico (ad esempio: vsspsextprodch1su1.vsspsext.VisualStudio.com) |
| Snapshot <br>Debugger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon (. exe) | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (dipendente dalla versione di Visual Studio) | 1. file query. JSON per le dimensioni dello SKU del servizio app <br>2. varie chiamate di Azure RM <br>3. chiamata riscaldamento del sito tramite  <br>4. endpoint Kudu del servizio app di destinazione del cliente <br>5. versione dell'estensione del sito di query pubblicata in nuget.org <br>6. canale di debug remoto |
| Analisi di flusso di Azure <br><br>HDInsight | Management.azure.com | https | 443 | Usato per visualizzare, inviare, eseguire e gestire i processi ASA <br><br> Usato per esplorare i cluster HDI e inviare, diagnosticare ed eseguire il debug di processi HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Usato per compilare, inviare, visualizzare, diagnosticare ed eseguire il debug di processi; usato per visualizzare file ADLS; usato per caricare e scaricare file |
| Servizio di creazione di pacchetti | [account].visualstudio.com <br/> [account].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | I domini \*.npmjs.org, \*.nuget.org e \*.nodejs.org sono necessari solo per determinati scenari di attività di compilazione, ad esempio il programma di installazione dello strumento NuGet o il programma di installazione dello strumento Node, o se si prevede di usare upstream pubblici con i feed. Gli altri tre domini sono necessari per la funzionalità core del servizio Creazione pacchetto. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | | Usato per la connessione con Azure DevOps Services |
| | | | | |

## <a name="troubleshoot-network-related-errors"></a>Risoluzione dei problemi correlati alla rete

In alcuni casi, è possibile che si riscontrino problemi correlati alla rete o al proxy quando si installa o si usa Visual Studio protetto da un firewall o un server proxy. Per altre informazioni sulle soluzioni per questo tipo di messaggi di errore, vedere la pagina [Troubleshooting network-related errors when you install or use Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) (Risoluzione dei problemi correlati alla rete quando si installa o usa Visual Studio).

## <a name="get-support"></a>Supporto

Per i problemi correlati all'installazione è disponibile un'opzione di supporto che offre una [**chat attiva**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese).

Ecco alcune altre opzioni di supporto:

* Segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* Suggerire una funzionalità, tenere traccia dei problemi del prodotto e trovare risposte in [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Usare l'account [GitHub](https://github.com/) per comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Vedere anche

* [Requisiti di connettività per Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Risoluzione dei problemi correlati alla rete in Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Installare Visual Studio protetto da un firewall o un server proxy (Visual Studio per Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
