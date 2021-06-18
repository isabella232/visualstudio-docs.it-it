---
title: Applicazione degli aggiornamenti dell'amministratore Visual Studio con Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Informazioni su come applicare gli aggiornamenti dell'amministratore Visual Studio.
ms.date: 04/16/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c18c460ebcffdba93279aafec2f3d76503ab2383
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307687"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Applicazione di aggiornamenti dell'amministratore che usano Microsoft Endpoint Configuration Manager

Questo documento descrive i diversi tipi e caratteristiche degli aggiornamenti Visual Studio amministratore. Di seguito sono riportate informazioni su come e quando devono essere distribuite in tutta l'organizzazione, sulle opzioni di configurazione disponibili e su come visualizzare i report e risolvere i problemi. Per altre informazioni sui prerequisiti per l'uso degli aggiornamenti dell'amministratore, vedere [Abilitazione degli aggiornamenti dell'amministratore](../install/enabling-administrator-updates.md). Gli aggiornamenti dell'amministratore presupsume che Visual Studio sia già installato nel computer. L'applicazione degli aggiornamenti dell'amministratore non avvierà una nuova installazione.

## <a name="understanding-visual-studio-administrator-updates"></a>Informazioni sugli Visual Studio amministratore

Il pacchetto di aggiornamento dell'amministratore di Visual Studio pubblicato in Microsoft Update per l'utilizzo da parte di Microsoft Catalog e WSUS contiene informazioni che il Gestione configurazione deve essere in grado di scaricare e distribuire l'aggiornamento Visual Studio nei computer client. Contiene anche le informazioni necessarie a un amministratore IT per decidere quali aggiornamenti distribuire nell'organizzazione. Può anche essere usato per facilitare la manutenzione dei layout di rete. I Visual Studio di aggiornamento dell'amministratore non contengono informazioni sufficienti per eseguire una nuova installazione del prodotto, né contengono i file binari effettivi del prodotto pubblicati nella rete per la distribuzione di contenuti. Visual Studio gli aggiornamenti dell'amministratore sono cumulativi, proprio come gli aggiornamenti Visual Studio regolari. È possibile presupporre che qualsiasi aggiornamento Visual Studio con un numero di versione del prodotto superiore e una data di versione successiva sia un superset di una versione precedente e inferiore.

Visual Studio gli aggiornamenti dell'amministratore Visual Studio versioni di manutenzione supportate. Per altre informazioni su quali Visual Studio di manutenzione sono ancora supportate durante un determinato intervallo di tempo, vedere Visual Studio Ciclo di vita e [manutenzione del prodotto](/visualstudio/productinfo/vs-servicing-vs). Tutte le linee Visual Studio di manutenzione supportate verranno mantenute sicure.  

## <a name="types-and-characteristics-of-administrator-updates"></a>Tipi e caratteristiche degli aggiornamenti dell'amministratore

Esistono tre tipi di aggiornamenti amministratore da Visual Studio:

* **Gli aggiornamenti** della sicurezza sono applicabili a tutte Visual Studio edizioni (ad esempio Enterprise, Professional, Community e così via) e contengono modifiche limitate, altamente mirate e compatibili al livello di manutenzione. Gli aggiornamenti della sicurezza non spostano un client a una versione secondaria successiva. sono progettate per fornire correzioni alle vulnerabilità della sicurezza a un client che si trova già a un particolare livello di versione secondaria. Gli aggiornamenti della sicurezza avranno almeno una correzione di sicurezza, ma la correzione di sicurezza può essere o meno in un componente o in un carico di lavoro installato nel computer client. Ad esempio, è possibile correggere una vulnerabilità di sicurezza nei componenti .NET e l'aggiornamento verrebbe etichettato come aggiornamento della sicurezza, ma non avrebbe alcun effetto significativo su un computer client in cui erano installati solo componenti C++. Gli aggiornamenti della sicurezza possono contenere anche altre correzioni di affidabilità o altri aggiornamenti dei componenti necessari. Gli aggiornamenti della sicurezza vengono pubblicati in [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) e [Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus), dove sono classificati come "Aggiornamenti della sicurezza".
* **Gli aggiornamenti delle** funzionalità consentono agli amministratori IT di far avanzare i computer dell'organizzazione a una versione secondaria più recente Visual Studio. Gli aggiornamenti delle funzionalità si applicano Visual Studio che si trovano comunemente nelle aziende, ad esempio SKU Enterprise, Professional e Build Tools. Tutti gli aggiornamenti delle funzionalità verranno pubblicati nel catalogo Microsoft Update come "Feature Pack" e saranno disponibili per l'importazione manuale in Gestione configurazione da Microsoft Update [Catalog](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog). Gli aggiornamenti delle funzionalità sono cumulativi e conterranno ulteriori correzioni di qualità e di sicurezza precedenti. Vedere la [sezione opzioni di](#understanding-configuration-options) configurazione riportata di seguito per istruzioni su come configurare un computer client in modo che rimanga in una linea di base di manutenzione e impedire il recapito degli aggiornamenti delle funzionalità a client specifici.
* **Gli aggiornamenti** qualitativi sono applicabili solo alle edizioni Visual Studio che si trovano comunemente nelle aziende e contengono modifiche limitate, altamente mirate e compatibili del livello di manutenzione. Gli aggiornamenti qualitativi non spostano un client a una versione secondaria successiva. sono progettate per offrire correzioni di prestazioni e affidabilità o altri aggiornamenti dei componenti necessari a un client già a un determinato livello di versione secondaria. Gli aggiornamenti qualitativi si accumulano insieme agli aggiornamenti della sicurezza e di conseguenza conterranno correzioni di sicurezza solo se la correzione di sicurezza è già stata rilasciata in modo indipendente. Gli aggiornamenti qualitativi vengono pubblicati nel catalogo Microsoft Update come "Aggiornamenti" e sono anche disponibili per l'importazione manuale in Gestione configurazione [.](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)

### <a name="decoding-the-titles-of-administrator-updates"></a>Decodifica dei titoli degli aggiornamenti dell'amministratore

Il titolo di ogni aggiornamento amministratore descrive sia l'intervallo di versioni applicabili che la versione risultante dell'aggiornamento.Ad esempio,

::: moniker range="vs-2017"

* **Visual Studio 2017 versione 15.9.0 a 15.9.35** l'aggiornamento classificato come aggiornamento della sicurezza verrà applicato a qualsiasi edizione di Visual Studio 2017 nel client tra le versioni da 15.9.0 a 15.9.35 e aggiornerà tali edizioni client alla versione 15.9.35.
* **Visual Studio 2017 versione 15.0.0 a 15.9.0 l'aggiornamento** classificato come "Feature Pack" verrà applicato alle edizioni di Visual Studio 2017 concesse in licenza per l'uso aziendale sul client tra l'intera gamma di versioni del prodotto da 15.0.0 a 15.9.0 e le edizioni client verranno aggiornate alla versione 15.9.0. L'applicazione di questo Feature Pack consente fondamentalmente ai client di ricevere gli aggiornamenti della sicurezza. 
* **Visual Studio 2017 versione 15.9.0 a 15.9.37 l'aggiornamento** classificato semplicemente come "Aggiornamenti" verrà applicato alle edizioni di Visual Studio 2017 concesse in licenza per l'uso aziendale nel client tra le versioni da 15.9.0 a 15.9.37 e aggiornerà tali edizioni client alla versione 15.9.37.

::: moniker-end

::: moniker range="vs-2019"

* **Visual Studio 2019 versione 16.7.0 a 16.7.12** l'aggiornamento classificato come aggiornamento della sicurezza verrà applicato a qualsiasi edizione di Visual Studio 2019 nel client tra le versioni da 16.7.0 a 16.7.12 e aggiornerà tali edizioni client alla versione 16.7.12.  
* **Visual Studio 2019 versione 16.0.0 a 16.9.0 l'aggiornamento** classificato come "Feature Pack" verrà applicato alle edizioni di Visual Studio 2019 concesse in licenza per l'uso aziendale sul client tra l'intera gamma di versioni del prodotto da 16.0.0 a 16.9.0, e aggiornerà le edizioni client (che non sono state configurate per rimanere in una baseline di manutenzione precedente) alla versione 16.9.0. 
* **Visual Studio 2019 versione 16.8.0 a 16.8.7 l'aggiornamento** classificato semplicemente come "Aggiornamenti" verrà applicato alle edizioni di Visual Studio 2019 concesse in licenza per l'uso aziendale nel client tra le versioni da 16.8.0 a 16.8.7 e aggiornerà tali edizioni client alla versione 16.8.7.

::: moniker-end

::: moniker range=">=vs-2022"

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Uso Gestione configurazione per distribuire Visual Studio aggiornamenti

### <a name="understanding-configuration-options"></a>Informazioni sulle opzioni di configurazione

Esistono alcune opzioni di configurazione che possono essere usate per personalizzare gli aggiornamenti dell'amministratore di Visual Studio in modo che siano compatibili e allineati alle preferenze e ai requisiti di distribuzione dell'organizzazione. Di seguito sono elencate le opzioni di configurazione più comuni. Per un elenco completo di tutti i comportamenti di aggiornamento dell'amministratore supportati, vedere Usare i parametri della riga di comando per installare Visual Studio e prestare attenzione solo [a](../install/use-command-line-parameters-to-install-visual-studio.md) quelli che corrispondono all'azione "update".

* **[Consenso esplicito per l'aggiornamento](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)** dell'amministratore: questa chiave del Registro di sistema è necessaria per consentire al computer client di ricevere gli aggiornamenti dell'amministratore. Si tratta di una chiave a livello di computer, ovvero si applica a tutte le istanze di Visual Studio installate nella casella.
* **Visual Studio rifiuto** esplicito dell'utente: Visual Studio utenti possono usare una chiave del Registro di  sistema **AdministratorUpdatesOptOut** separata a livello di computer per rifiutare esplicitamente la ricezione degli aggiornamenti Visual Studio amministratore. Lo scopo di questa chiave è consentire all Visual Studio'utente di avere un certo controllo sulla presenza di aggiornamenti applicati automaticamente al computer. Per configurare il computer client in modo da bloccare gli aggiornamenti dell'amministratore, impostare la chiave **administratorUpdatesOptOut**   REG_DWORD su **1**. L'assenza della chiave, o un valore impostato pari a **0,** significa che l'utente Visual Studio desidera ricevere gli aggiornamenti dell'amministratore per Visual Studio.
    Si noti che la chiave **AdministratorUpdatesOptOut** per la codifica delle preferenze utente è prioritaria rispetto alla chiave    **AdministratorUpdatesEnabled,** che codifica la finalità di amministratore   IT. Se **AdministratorUpdatesOptOut** è impostato su 1, l'aggiornamento verrà bloccato nel client, anche se anche la chiave    **AdministratorUpdatesEnabled** è ****   impostata su **1.**Questa azione presuppone che gli amministratori IT possano accedere e monitorare quali sviluppatori hanno scelto di rifiutare esplicitamente e che le due parti possano quindi discutere le esigenze più importanti.Gli amministratori IT possono sempre modificare entrambe le chiavi ogni volta che vogliono.
* **Posizione dei bit del prodotto aggiornati:** nella maggior parte dei casi, i computer client scaricano i bit del prodotto aggiornati da Internet tramite la rete CDN Microsoft. Questo scenario richiede che i computer client abbia accesso a Internet. Alcune aziende, tuttavia, limitano i computer client solo all'installazione e all'aggiornamento dei bit da un percorso di layout di rete interno. Per garantire che gli aggiornamenti dell'amministratore possano essere applicati usando bit aggiornati che si esercitino in un percorso di rete interno, prima che l'aggiornamento dell'amministratore possa essere distribuito correttamente, è necessario che siano soddisfatte le condizioni seguenti: 
  * Il computer client deve avere, a un certo punto, già eseguito il programma di avvio automatico da tale percorso di layout di rete. Idealmente, l'installazione del client originale si sarebbe verificata usando il programma di avvio automatico dal layout di rete, ma è anche possibile avere appena installato un aggiornamento usando un programma di avvio automatico aggiornato nello stesso percorso di rete. Una di queste azioni incorpora nel computer client una connessione con quel particolare percorso di layout.
  * Il percorso del layout di rete (a cui il client è connesso) deve essere aggiornato per contenere i bit di [prodotto](../install/update-a-network-installation-of-visual-studio.md) aggiornati che l'aggiornamento dell'amministratore vuole distribuire.

::: moniker range=">=vs-2019"

* **Stickiness baseline di** manutenzione: come descritto in precedenza, gli aggiornamenti delle funzionalità dell'amministratore anticipano un'installazione Visual Studio a una versione secondaria più recente del prodotto. A volte, tuttavia, Visual Studio utenti devono rimanere a un livello di base di manutenzione stabile e sicuro specifico e vogliono controllare quando i computer passano a una versione secondaria più recente. Per configurare un computer client in modo che rimanga in una linea di base di manutenzione e ignorare gli aggiornamenti indesiderati delle funzionalità dell'amministratore inviati, è necessario creare e impostare il valore dei dati **baselineStickinessVersions2019** Reg_SZ su una stringa che rappresenta la baseline preferita a cui il computer client deve allinearsi e rimanere attiva. La stringa può contenere una versione di base di manutenzione consentita, ad esempio **16.7.0.**  
     Se il formato del valore del Registro di sistema non è corretto, l'installazione di tutti gli aggiornamenti delle funzionalità dell'amministratore verrà `BaselineStickinessVersions2019` bloccata nel computer. Assicurarsi di prestare attenzione agli intervallo di tempo supportati per gli aggiornamenti Visual Studio [funzionalità .](/visualstudio/productinfo/vs-servicing-vs) Inoltre, indipendentemente dalla presenza o dal valore della chiave, anche se è tecnicamente possibile applicare gli aggiornamenti delle funzionalità di amministratore che hanno raggiunto la fine della loro durata, non è consigliabile perché non saranno supportati e quindi potenzialmente `BaselineStickinessVersions2019` non sicuri.

::: moniker-end

* **Forzare l'aggiornamento anche se Visual Studio è in uso:** è Visual Studio prima di installare l'aggiornamento. Se Visual Studio è aperto o in uso, l'installazione dell'aggiornamento verrà interrotta. Un modo semplice per assicurarsi che Visual Studio sia chiuso è configurare Confirmation Manager per applicare l'aggiornamento subito dopo il riavvio del computer. È anche possibile usare il `--force` parametro per forzare l'arresto Visual Studio. Forzare Visual Studio chiusura potrebbe causare la perdita di lavoro, quindi usarlo con cautela. L'esecuzione di un aggiornamento amministratore nel contesto di sistema predefinito ignorerà il flag, pertanto sarà necessario configurare l'aggiornamento dell'amministratore per `–-force` l'esecuzione nel contesto utente.

### <a name="methods-for-configuring-an-administrator-update"></a>Metodi per la configurazione di un aggiornamento amministratore

Esistono tre metodi principali per configurare gli aggiornamenti dell'amministratore: una chiave del Registro di sistema, un file di configurazione nel computer client o una modifica del pacchetto di Gestione configurazione distribuzione.   

* **Chiave del Registro di** sistema: gli aggiornamenti dell'amministratore ricercano chiavi del Registro di sistema specifiche in uno dei percorsi Visual Studio standard, come descritto in [Impostare le impostazioni predefinite per le distribuzioni aziendali.](../install/set-defaults-for-enterprise-deployments.md) Le opzioni controllate dalle chiavi del Registro di sistema sono elementi come **AdministratorUpdatesOptOut** Reg_DWORD, **AdministratorUpdatesOptOut**   Reg_DWORD e **BaselineStickinessVersions2019** Reg_SZ. L'accesso amministratore nel computer client è necessario per creare e impostare il valore delle chiavi del Registro di sistema.

* **File di configurazione:** alcune impostazioni possono essere mantenute nel computer client in un file di configurazione facoltativo, che ha il vantaggio di impostarlo una sola volta e di applicarlo a tutti gli aggiornamenti futuri dell'amministratore. L'approccio del file di configurazione si comporta come una chiave del Registro di sistema ed è a livello di computer, ovvero verrà applicato a tutte le installazioni di Visual Studio installate nel computer client. Il percorso standard per il file di configurazione si trova in `C:\ProgramData\Microsoft\VisualStudio\updates.config` . Se tuttavia si vuole usare un altro percorso per archiviare il file, è possibile creare una chiave del Registro di sistema Reg_SZ denominata **UpdateConfigurationFile** e impostare il valore di questa chiave sul percorso del file di configurazione. Questa chiave del Registro di sistema può essere posizionata in uno dei percorsi Visual Studio del Registro di sistema, come descritto in [Impostare le impostazioni predefinite per le distribuzioni aziendali](../install/set-defaults-for-enterprise-deployments.md). Se si sceglie di aggiungere un valore del Registro di sistema per un percorso di file di configurazione personalizzato, il file verrà ricercato. se il file non esiste, verrà generata un'eccezione e l'aggiornamento avrà esito negativo.

     Il file di configurazione, che è in formato JSON, supporta l'opzione che è una matrice di stringhe separate da virgole che specificano più opzioni che è possibile passare al programma di `installerUpdateArgs` Visual Studio programma di installazione. Se il contenuto del file include un campo non valido o un'opzione non supportata, l'aggiornamento avrà esito negativo. Per altre informazioni, vedere [Usare i parametri della riga di](../install/use-command-line-parameters-to-install-visual-studio.md)comando per installare Visual Studio .

   Ecco un file di configurazione di esempio:

  ```json
  "installerUpdateArgs" : ["--quiet", "--noWeb"], 
  "checkPendingReboot" :  "true" 
  ```

* **Aggiornamento manuale del pacchetto di aggiornamenti dell'amministratore in SCCM:** è anche possibile modificare manualmente i parametri della riga di comando di un singolo pacchetto di aggiornamento amministratore in SCCM.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>Verifica, report e risoluzione dei problemi relativi ai codici di errore

### <a name="determining-that-visual-studio-was-updated"></a>Determinazione dell'Visual Studio stato aggiornato

È possibile usare uno dei metodi seguenti per verificare che l'aggiornamento dell'amministratore sia stato installato correttamente:

* Nel computer client avviare Visual Studio, selezionare **** Informazioni su e verificare che il numero di versione corrisponda all'ultimo numero nel titolo   >  **** dell'aggiornamento previsto.
* Usare lo **strumento vswhere** nel computer client per identificare le varie versioni Visual Studio nel computer. Per altre informazioni, vedere [Strumenti per il rilevamento e la gestione Visual Studio istanze di](../install/tools-for-managing-visual-studio-instances.md).
* Ogni tentativo di aggiornamento amministrativo genera diversi file di log nella directory del computer client che `%temp%` acquisisce lo stato di avanzamento dell'operazione di aggiornamento.Ordinare la cartella in base alla data e cercare i file che iniziano con , , e per gli aggiornamenti amministrativi, il programma di avvio automatico, il Programma di installazione di Visual Studio e il motore di  `dd_updatedriver`  `dd_bootstrapper`  `dd_client`  `dd_setup`   installazione, rispettivamente.Verificare che questi file di log contengano un valore 0, che indica che l'aggiornamento è stato applicato correttamente. Si noti che questi file di log possono essere usati anche per verificare che il file di configurazione sia in uso. Per altri [dettagli, Visual Studio lo](https://www.microsoft.com/download/details.aspx?id=12493) strumento di raccolta dei log.

### <a name="error-codes-and-conditions"></a>Codici di errore e condizioni

>[!IMPORTANT]
> Tenere presente Visual Studio necessario chiudere prima di installare l'aggiornamento. Se Visual Studio è aperto o in uso, l'installazione dell'aggiornamento verrà annullata.

Gli aggiornamenti amministrativi possono restituire i codici restituiti seguenti:  

| Codice di errore | Definizione                                                                                                                                                                                                  |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0          | L'aggiornamento amministrativo è stato installato correttamente.                                                                                                                                                       |
| 1001       | Programma di installazione di Visual Studio o un processo di installazione correlato è in esecuzione. L'aggiornamento non viene applicato.                                                                                                                   |
| 1002       | Programma di installazione di Visual Studio è in pausa. L'aggiornamento non viene applicato.                                                                                                                                               |
| 1003       | Visual Studio è in esecuzione. L'aggiornamento non viene applicato. Questa condizione può essere ignorata usando il `--force` flag .                                                                                              |
| 1004       | Non è stata rilevata alcuna connessione Internet.L'aggiornamento non è riuscito a contattare il percorso Internet contenente i file aggiornati. L'aggiornamento non viene applicato.                                                                          |
| 1005       | Il valore del Registro di sistema  **AdministratorUpdatesEnabled**   è impostato su **0** o non è impostato affatto. L'aggiornamento non viene applicato.                                                                                            |
| 1006       | Il  **valore del Registro di sistema AdministratorUpdatesOptOut** è impostato su   **1.** L'aggiornamento non viene applicato. La chiave è destinata ai computer client che non devono essere aggiornati dall'amministratore.                     |
| 1007       | Il Programma di installazione di Visual Studio non è installato.                                                                                                                                                               |
| 1008       | Il valore del Registro di sistema **BaselineStickinessVersions2019** non è in un formato leggibile. Il valore del Registro di sistema deve **includere tutte** le versioni o le versioni valide con il numero di build impostato su 0 in modo esplicito, ad esempio X.Y.0. |
| 3010       | Il sistema richiede un riavvio.L'aggiornamento potrebbe essere stato applicato o meno. Riavviare il computer e riprovare a eseguire l'aggiornamento.                                                                                |
| Altro      | Errore durante il tentativo di applicare l'aggiornamento.L'aggiornamento non viene applicato.                                                                                                                                   |

Per un elenco completo dei codici di errore client, vedere [Usare i parametri della riga di](use-command-line-parameters-to-install-visual-studio.md)comando per installare Visual Studio .

## <a name="feedback-and-support"></a>Feedback e supporto

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

È possibile usare i metodi seguenti per fornire commenti e suggerimenti sugli aggiornamenti Visual Studio amministratore o per segnalare problemi che interessano gli aggiornamenti:

* Fare riferimento alle linee guida [sulla risoluzione Visual Studio problemi di installazione e aggiornamento.](../install/troubleshooting-installation-issues.md)
* Porre domande alla community nel forum [Visual Studio setup Q&A .](/answers/topics/vs-setup.html)
* Passare alla pagina [Visual Studio supporto](https://visualstudio.microsoft.com/vs/support/)tecnico e verificare se il problema è elencato nelle domande frequenti.  È anche possibile selezionare il pulsante [Collegamento al supporto](https://visualstudio.microsoft.com/vs/support/#talktous) per la Guida alla chat.
* [Inviare commenti e suggerimenti sulle funzionalità o segnalare un](https://aka.ms/vs/wsus/feedback) problema al team Visual Studio riguardo a questa esperienza di applicazione degli aggiornamenti dell'amministratore.
* Contattare l'amministratore dell'technical account manager per Microsoft.

## <a name="see-also"></a>Vedi anche

* [Abilitazione degli aggiornamenti dell'amministratore](../install/enabling-administrator-updates.md)
* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
* [Ciclo di vita del prodotto e manutenzione di Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Note sulla versione di Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Installa Visual Studio](../install/install-visual-studio.md)
* [Uso dei parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](../install/tools-for-managing-visual-studio-instances.md)
* [Creare un'installazione di rete di Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Come definire impostazioni in un file di risposta](../install/automated-installation-with-response-file.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](../install/controlling-updates-to-visual-studio-deployments.md)
* [Microsoft Update domande frequenti sul catalogo](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Importare gli aggiornamenti da Microsoft Catalog Gestione configurazione](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
