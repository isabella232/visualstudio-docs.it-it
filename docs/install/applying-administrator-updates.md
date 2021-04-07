---
title: Applicazione degli aggiornamenti dell'amministratore a Visual Studio con Microsoft endpoint Configuration Manager
titleSuffix: ''
description: Informazioni su come applicare gli aggiornamenti amministratore a Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d316fc35df8c571a9112d7a653737e099df80559
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547453"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Applicazione degli aggiornamenti amministratore che usano Microsoft endpoint Configuration Manager

In questo documento vengono descritti i diversi tipi e caratteristiche degli aggiornamenti degli amministratori di Visual Studio. Di seguito sono riportate informazioni su come e quando devono essere distribuite nell'intera organizzazione, sulle opzioni di configurazione disponibili e su come visualizzare i report e la risoluzione dei problemi. Per altre informazioni sui prerequisiti per l'uso degli aggiornamenti amministrativi, vedere [Abilitazione degli aggiornamenti dell'amministratore](../install/enabling-administrator-updates.md).

## <a name="understanding-visual-studio-administrator-updates"></a>Informazioni sugli aggiornamenti degli amministratori di Visual Studio 

Il pacchetto di aggiornamento dell'amministratore di Visual Studio pubblicato per Microsoft Update per l'utilizzo da parte del catalogo Microsoft e WSUS contiene informazioni che il Configuration Manager deve essere in grado di scaricare e distribuire l'aggiornamento a Visual Studio nei computer client. Contiene anche le informazioni necessarie a un amministratore IT per decidere quali aggiornamenti distribuire in tutta l'organizzazione e semplifica la manutenzione dei layout di rete. I pacchetti di aggiornamento dell'amministratore di Visual Studio non contengono informazioni sufficienti per eseguire una nuova installazione del prodotto, né contengono i file binari dei prodotti effettivi pubblicati nella rete per la distribuzione di contenuti. Gli aggiornamenti degli amministratori di Visual Studio sono cumulativi, proprio come i normali aggiornamenti di Visual Studio. Si può presupporre che qualsiasi aggiornamento di Visual Studio con un numero di versione del prodotto più elevato e una data di rilascio successiva sia un superset di una versione precedente, inferiore. 

Gli aggiornamenti degli amministratori di Visual Studio si applicano alle versioni di manutenzione di Visual Studio supportate. Per ulteriori informazioni sulle linee di base di manutenzione di Visual Studio ancora in corso in un determinato intervallo di tempo, vedere ciclo di vita [e manutenzione dei prodotti Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Tutte le linee di base di manutenzione di Visual Studio supportate verranno mantenute sicure.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Tipi e caratteristiche degli aggiornamenti dell'amministratore 

Sono disponibili tre tipi di aggiornamenti per gli amministratori di Visual Studio:

* **Gli aggiornamenti della sicurezza** sono applicabili a tutte le edizioni di Visual Studio (ad esempio Enterprise, Professional, community e così via) e contengono modifiche a livello di manutenzione limitate, altamente mirate e compatibili. Gli aggiornamenti della sicurezza non faranno avanzare un client a una versione secondaria successiva; sono progettati per fornire correzioni alle vulnerabilità di sicurezza a un client che è già a un livello di versione secondario specifico. Gli aggiornamenti della sicurezza avranno almeno una correzione per la sicurezza, ma la correzione di sicurezza potrebbe essere o meno in un componente o un carico di lavoro installato nel computer client. Ad esempio, è possibile correggere una vulnerabilità di sicurezza nei componenti .NET e l'aggiornamento verrà etichettato come aggiornamento della sicurezza, ma non avrebbe alcun effetto significativo su un computer client in cui erano installati solo i componenti di C++. Gli aggiornamenti della sicurezza possono anche contenere altre correzioni di affidabilità o altri aggiornamenti dei componenti necessari. Gli aggiornamenti della sicurezza vengono pubblicati sia nel [catalogo Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) che nel [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus), in cui vengono classificati come "aggiornamenti della sicurezza".
 
* **Gli aggiornamenti delle funzionalità** consentono agli amministratori IT di far avanzare i computer dell'organizzazione a una versione secondaria più recente di Visual Studio 2019. Gli aggiornamenti delle funzionalità sono validi solo per le edizioni di Visual Studio che sono comunemente presenti nelle aziende, ad esempio gli SKU di strumenti Enterprise, Professional e Build. Tutti gli aggiornamenti delle funzionalità verranno pubblicati nel catalogo di Microsoft Update come "Feature Pack" ed è possibile [importarli manualmente nel Configuration Manager dal catalogo di Microsoft Update](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog). Gli aggiornamenti delle funzionalità sono cumulativi e conterranno una maggiore qualità e correzioni di sicurezza precedenti. Vedere la [sezione Opzioni di configurazione](#understanding-configuration-options) seguente per istruzioni su come configurare un computer client in modo che rimanga in una linea di base di manutenzione e impedire che gli aggiornamenti delle funzionalità vengano recapitati a client specifici. 

* **Gli aggiornamenti qualitativi** sono validi anche per le edizioni di Visual Studio in genere presenti nelle aziende e contengono modifiche a livello di manutenzione limitate, altamente mirate e compatibili. Gli aggiornamenti qualitativi non consentiranno a un client di passare a una versione secondaria successiva; sono progettati per fornire correzioni delle prestazioni e dell'affidabilità o altri aggiornamenti dei componenti necessari a un client che è già a un livello di versione secondario specifico. Gli aggiornamenti qualitativi si accumulano insieme agli aggiornamenti della sicurezza e pertanto contengono correzioni di sicurezza solo se la correzione della sicurezza è già stata rilasciata in modo indipendente. Gli aggiornamenti qualitativi vengono pubblicati nel catalogo Microsoft Update come "aggiornamenti" ed è anche possibile [importarli manualmente nel Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog).

### <a name="decoding-the-titles-of-administrator-updates"></a>Decodifica dei titoli degli aggiornamenti dell'amministratore

Il titolo di ogni aggiornamento dell'amministratore descrive sia l'intervallo di versioni applicabile che la versione risultante dell'aggiornamento.Ad esempio,

::: moniker range="vs-2017"

* **Visual studio 2017 versione 15.9.0 per l'aggiornamento 15.9.35** Classificato come "aggiornamento della sicurezza" si applica a qualsiasi edizione di visual studio 2017 sul client tra le versioni 15.9.0 e 15.9.35 e aggiorna le edizioni client in 15.9.35.

* **Visual studio 2017 versione 15.0.0 per l'aggiornamento 15.9.0** Classificato come "Feature Pack" verrà applicato alle edizioni di visual studio 2017 concesse in licenza per l'uso aziendale sul client tra l'intero intervallo di versioni del prodotto di 15.0.0 tramite 15.9.0 e le edizioni client verranno aggiornate in 15.9.0. L'applicazione di questo Feature Pack consente ai client di ricevere quindi gli aggiornamenti della sicurezza. 

* **Visual studio 2017 versione 15.9.0 per l'aggiornamento 15.9.37** Classificato come "aggiornamenti" verrà applicato alle edizioni di visual studio 2017 concesse in licenza per l'uso aziendale sul client tra le versioni 15.9.0 tramite 15.9.37 e aggiornerà le edizioni client in 15.9.37. 

::: moniker-end

::: moniker range="vs-2019"

* **Visual studio 2019 versione 16.7.0 per l'aggiornamento 16.7.12** Classificato come "aggiornamento della sicurezza" si applica a qualsiasi edizione di visual studio 2019 sul client tra le versioni 16.7.0 e 16.7.12 e aggiorna le edizioni client in 16.7.12.  

* **Visual studio 2019 versione 16.0.0 per l'aggiornamento 16.9.0** Classificato come "Feature Pack" verrà applicato alle edizioni di visual studio 2019 concesse in licenza per l'uso aziendale sul client tra l'intero intervallo di versioni del prodotto di 16.0.0 tramite 16.9.0 e aggiornerà le edizioni client (che non sono state configurate per rimanere in una baseline di manutenzione precedente) a 16.9.0. 

* **Visual studio 2019 versione 16.8.0 per l'aggiornamento 16.8.7** Classificato come "aggiornamenti" verrà applicato alle edizioni di visual studio 2019 concesse in licenza per l'uso aziendale sul client tra le versioni 16.8.0 tramite 16.8.7 e aggiornerà le edizioni client in 16.8.7. 

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Uso di Configuration Manager per distribuire gli aggiornamenti di Visual Studio

### <a name="understanding-configuration-options"></a>Informazioni sulle opzioni di configurazione

Sono disponibili alcune opzioni di configurazione che possono essere usate per adattare gli aggiornamenti dell'amministratore di Visual Studio in modo che siano compatibili e allineati con le preferenze e i requisiti di distribuzione dell'organizzazione. Le opzioni di configurazione più comuni sono elencate di seguito. Per un elenco completo di tutti i comportamenti di aggiornamento dell'amministratore supportati, vedere [usare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) e prestare attenzione solo a quelli che corrispondono all'azione di aggiornamento.

* **[Consenso esplicito](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)** per l'aggiornamento dell'amministratore: questa chiave del registro di sistema è necessaria affinché il computer client riceva gli aggiornamenti dell'amministratore. Si tratta di una chiave a livello di computer, che indica che si applica a tutte le istanze di Visual Studio installate nella casella. 
 
* **Rifiuto esplicito dell'utente di Visual Studio**: gli utenti di Visual Studio possono usare una chiave del registro di sistema **AdministratorUpdatesOptOut** a livello di computer separata per *rifiutare esplicitamente* la ricezione degli aggiornamenti dell'amministratore di Visual Studio. Lo scopo di questa chiave è consentire all'utente di Visual Studio di avere un certo controllo sugli aggiornamenti applicati automaticamente al computer. Per configurare il computer client in modo da bloccare gli aggiornamenti dell' **** amministratore, impostare la   chiave di REG_DWORD AdministratorUpdatesOptOut su **1**. L'assenza della chiave o un valore impostato su **0** indica che l'utente di Visual Studio vuole ricevere gli aggiornamenti dell'amministratore a Visual Studio.

    Si noti che la chiave **AdministratorUpdatesOptOut**   per la codifica delle preferenze utente viene classificata in ordine di priorità sulla chiave **AdministratorUpdatesEnabled**   , che codifica lo scopo dell'amministratore it. Se **AdministratorUpdatesOptOut**   è impostato su **1**, l'aggiornamento verrà bloccato sul client, anche se anche la chiave **AdministratorUpdatesEnabled**   è impostata su **1**.Questa azione presuppone che gli amministratori IT possano accedere e monitorare quali sviluppatori hanno scelto di rifiutare esplicitamente e che le due parti possano quindi discutere le cui esigenze sono più importanti.Gli amministratori IT possono sempre modificare qualsiasi chiave ogni volta che desiderano.
 
* **Percorso dei bit del prodotto aggiornati**: nella maggior parte dei casi, i computer client scaricano i bit di prodotto aggiornati da Internet tramite la rete CDN Microsoft. Questo scenario richiede che i computer client dispongano di accesso a Internet. Alcune aziende, tuttavia, limitano i computer client a installare e aggiornare solo BITS da un percorso di layout di rete interno. Per assicurarsi che gli aggiornamenti dell'amministratore possano essere applicati utilizzando bit aggiornati che si trovano in un percorso di rete interno, è necessario che le condizioni seguenti siano vere prima che l'aggiornamento dell'amministratore possa essere distribuito correttamente: 

  - Il computer client deve avere a un certo punto il programma di avvio automatico da tale percorso di layout di rete. Idealmente, l'installazione client originale avrebbe dovuto usare il programma di avvio automatico dal layout di rete, ma è anche possibile che sia stato appena installato un aggiornamento usando un programma di avvio automatico aggiornato nello stesso percorso di rete. Una di queste azioni può incorporare nel computer client una connessione con la posizione di layout specifica.   
  - Il percorso di layout di rete (a cui è connesso il client) deve essere [aggiornato in modo da contenere i bit di prodotto aggiornati](../install/update-a-network-installation-of-visual-studio.md) che l'aggiornamento dell'amministratore desidera distribuire. 

::: moniker range="vs-2019"

* **Viscosità di base di manutenzione**: come descritto in precedenza, gli aggiornamenti dell'amministratore che sono aggiornamenti delle funzionalità consentono di eseguire un'installazione di Visual Studio in una versione secondaria più recente del prodotto. In alcuni casi, tuttavia, i team di sviluppo preferiscono rimanere in un particolare livello di base di manutenzione stabile e sicuro e desiderano controllare quando i client passano a una versione secondaria più recente. Per configurare un computer client in modo che rimanga in una linea di base di manutenzione e ignorare gli aggiornamenti delle funzionalità di amministratore indesiderati, è necessario creare e impostare il valore di **BaselineStickinessVersions2019** REG_SZ i dati su una stringa che rappresenta le linee di base consentite a cui il computer client può bloccarsi e rimanere attivo.  La stringa può contenere una sequenza di versioni di base di manutenzione, separate da virgole, ad esempio **16.4.0, 16.7.0**. È possibile includere nella stringa un numero qualsiasi di versioni di base di manutenzione e la parola **All**, che è una forma abbreviata per fare riferimento a tutte le linee di base di manutenzione supportate, è anche supportata. 

     Se il `BaselineStickinessVersions2019` valore del registro di sistema non è valido, l'installazione di tutti gli aggiornamenti delle funzionalità verrà bloccata nel computer. È anche necessario prestare attenzione agli intervalli di tempo [supportati per gli aggiornamenti delle funzionalità di Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs). Sebbene sia tecnicamente possibile applicare gli aggiornamenti delle funzionalità che hanno raggiunto la fine della durata, non è consigliabile perché non saranno supportati e pertanto potenzialmente non sicuri.

::: moniker-end

* **Forzare l'aggiornamento anche se Visual Studio è in uso**: prima di installare l'aggiornamento, è necessario chiudere Visual Studio. Se Visual Studio è aperto o in uso, l'installazione dell'aggiornamento verrà interrotta. Un modo semplice per assicurarsi che Visual Studio sia chiuso consiste nel configurare la gestione della conferma per applicare l'aggiornamento subito dopo il riavvio del computer. È anche possibile usare il `--force` parametro per forzare l'arresto di Visual Studio. Se si forza la chiusura di Visual Studio, è possibile che si verifichi una perdita di lavoro, quindi è consigliabile usarla con cautela. L'esecuzione di un aggiornamento dell'amministratore nel contesto di sistema predefinito ignorerà il `–-force` flag, pertanto sarà necessario configurare l'aggiornamento dell'amministratore per l'esecuzione nel contesto utente.

### <a name="methods-for-configuring-an-administrator-update"></a>Metodi per la configurazione di un aggiornamento dell'amministratore

Sono disponibili tre metodi principali per la configurazione degli aggiornamenti dell'amministratore: una chiave del registro di sistema, un file di configurazione nel computer client o una modifica del pacchetto di distribuzione Configuration Manager stesso.   

* **Chiave del registro di sistema**: gli aggiornamenti dell'amministratore cercano chiavi del registro di sistema specifiche in uno dei percorsi standard di Visual Studio, come descritto in [impostare le impostazioni predefinite per le distribuzioni aziendali](../install/set-defaults-for-enterprise-deployments.md). Le opzioni controllate dalle chiavi del registro di sistema sono elementi, ad esempio **AdministratorUpdatesOptOut** REG_DWORD, **AdministratorUpdatesOptOut**   REG_DWORD e **BaselineStickinessVersions2019** REG_SZ. Per creare e impostare il valore delle chiavi del registro di sistema, è necessario disporre dell'accesso amministratore nel computer client. 
 
* **File di configurazione**: alcune impostazioni possono essere conservate nel computer client in un file di configurazione facoltativo, che offre il vantaggio di impostarlo una sola volta e applicarlo a tutti gli aggiornamenti futuri dell'amministratore. L'approccio del file di configurazione si comporta come una chiave del registro di sistema ed è a livello di computer, ovvero verrà applicato a tutte le installazioni di Visual Studio installate nel computer client. Il percorso standard per il file di configurazione è `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Tuttavia, se si desidera utilizzare un altro percorso per archiviare il file, è possibile creare una chiave del registro di sistema Reg_SZ denominata **UpdateConfigurationFile** e impostare il valore di questa chiave sul percorso del file di configurazione. Questa chiave del registro di sistema può essere posizionata in uno dei percorsi del registro di sistema di Visual Studio, come descritto in [impostare le impostazioni predefinite per le distribuzioni aziendali](../install/set-defaults-for-enterprise-deployments.md). Se si sceglie di aggiungere un valore del registro di sistema per un percorso di file di configurazione personalizzato, il file verrà cercato. Se il file non esiste, verrà generata un'eccezione e l'aggiornamento avrà esito negativo.    
 
     Il file di configurazione, in formato JSON, supporta l'opzione `installerUpdateArgs` che è una matrice di stringhe separate da virgole che specificano più opzioni che è possibile passare al programma di installazione di Visual Studio. Se il contenuto del file include un campo non valido o un'opzione non supportata, l'aggiornamento avrà esito negativo. Per altre informazioni, vedere [usare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).
 
   Di seguito è riportato un esempio di file di configurazione: 

   ```
   “installerUpdateArgs” : [“--quiet”, “--noWeb”], 

   “checkPendingReboot” :  “true” 
   ```

* **Aggiornamento manuale del pacchetto di aggiornamenti amministratore in SCCM**: è possibile modificare manualmente anche i parametri della riga di comando di un singolo pacchetto di aggiornamento dell'amministratore in SCCM.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Verifica, report e codici di errore per la risoluzione dei problemi

### <a name="determining-that-visual-studio-was-updated"></a>Determinazione dell'aggiornamento di Visual Studio

Per verificare che l'aggiornamento dell'amministratore sia stato installato correttamente, è possibile utilizzare uno dei metodi seguenti: 

* Nel computer client avviare Visual Studio 2019 **, selezionare informazioni**   >  **su** e verificare che il numero di versione corrisponda all'ultimo numero nel titolo dell'aggiornamento previsto. 

* Usare lo strumento **vswhere** nel computer client per identificare le diverse versioni di Visual Studio nel computer. Per altre informazioni, vedere [strumenti per il rilevamento e la gestione di istanze di Visual Studio](../install/tools-for-managing-visual-studio-instances.md). 

* Ogni tentativo di aggiornamento amministrativo genera diversi file di log nella directory del computer client `%temp%` che acquisisce lo stato di avanzamento dell'operazione di aggiornamento.Ordinare la cartella per data e cercare i file che iniziano  `dd_updatedriver` ,  `dd_bootstrapper` ,  `dd_client` e  `dd_setup`   per gli aggiornamenti amministrativi, il programma di avvio automatico, il programma di installazione di Visual Studio e il motore di installazione, rispettivamente.Verificare che questi file di log contengano un valore 0, a indicare che l'aggiornamento è stato applicato correttamente. Si noti che questi file di log possono essere usati anche per verificare che il file di configurazione venga usato. Per ulteriori informazioni, vedere lo [strumento di raccolta dei log di Visual Studio](https://www.microsoft.com/download/details.aspx?id=12493) .     

### <a name="error-codes-and-conditions"></a>Codici di errore e condizioni

>[!IMPORTANT]
> Tenere presente che Visual Studio deve essere chiuso prima di installare l'aggiornamento. Se Visual Studio è aperto o in uso, l'installazione dell'aggiornamento verrà annullata.

Gli aggiornamenti amministrativi possono restituire i seguenti codici restituiti:  

| Codice di errore | Definizione |
|--|:-|
| 0 | Installazione dell'aggiornamento amministrativo completata. |
| 1001 | Programma di installazione di Visual Studio o un processo di installazione correlato è in esecuzione. Aggiornamento non applicato. |
| 1002 | Programma di installazione di Visual Studio sospesa. Aggiornamento non applicato. |
| 1003 | Visual Studio è in esecuzione. Aggiornamento non applicato. Questa condizione può essere sovraregolata utilizzando il `--force` flag. |
| 1004 | Nessun Internet rilevato.L'aggiornamento non è riuscito a contattare il percorso Internet che contiene i file aggiornati. Aggiornamento non applicato. |
| 1005 | Il  ****   valore del registro di sistema AdministratorUpdatesEnabled è impostato su **0** o non è impostato. Aggiornamento non applicato. |
| 1006 | Il  ****   valore del registro di sistema AdministratorUpdatesOptOut è impostato su **1**. Aggiornamento non applicato. La chiave è destinata ai computer client che non devono essere aggiornati dall'amministratore. |
| 1007 | Il Programma di installazione di Visual Studio non è installato. |
| 1008 | Il valore del registro di sistema **BaselineStickinessVersions2019** non è in un formato leggibile. Il valore del registro di sistema deve includere **tutte** le versioni o valide con il numero di build impostato su 0 in modo esplicito, ad esempio, X. Y. 0. |
| 3010 | Il sistema richiede un riavvio.È possibile che l'aggiornamento sia stato applicato o meno. Riavviare il computer e ritentare l'aggiornamento. |
| Altro | Si è verificato un errore durante il tentativo di applicare l'aggiornamento.Aggiornamento non applicato. |

Per un elenco completo dei codici di errore del client, vedere [usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md). 

## <a name="feedback-and-support"></a>Feedback e supporto
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

È possibile utilizzare i metodi seguenti per fornire commenti e suggerimenti sugli aggiornamenti degli amministratori di Visual Studio o per segnalare problemi che influiscono sugli aggiornamenti:
* Vedere la guida alla [risoluzione dei problemi di installazione e aggiornamento di Visual Studio](../install/troubleshooting-installation-issues.md) .
* Porre domande alla community nel programma di [installazione di Visual Studio Q&un forum](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Passare alla [pagina del supporto di Visual Studio](https://visualstudio.microsoft.com/vs/support/)e verificare se il problema è elencato nelle domande frequenti.  È anche possibile selezionare il pulsante [link supporto](https://visualstudio.microsoft.com/vs/support/#talktous) per la Guida di chat.
* [Fornire commenti sulle funzionalità o segnalare un problema](https://aka.ms/vs/wsus/feedback) al team di Visual Studio in merito a questa esperienza di applicazione degli aggiornamenti amministratore.
* Rivolgersi all'account manager tecnico dell'organizzazione per Microsoft.

## <a name="see-also"></a>Vedi anche
* [Abilitazione degli aggiornamenti dell'amministratore](../install/enabling-administrator-updates.md)    
* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Note sulla versione di Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Note sulla versione di Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Installa Visual Studio](../install/install-visual-studio.md)
* [Uso dei parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](../install/tools-for-managing-visual-studio-instances.md)
* [Creare un'installazione di rete di Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Come definire impostazioni in un file di risposta](../install/automated-installation-with-response-file.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](../install/controlling-updates-to-visual-studio-deployments.md)
* [Domande frequenti sul catalogo Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Documentazione di Microsoft endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importare gli aggiornamenti da Microsoft Catalog in Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Documentazione di Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
