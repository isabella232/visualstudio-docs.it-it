---
title: Aggiunta di riferimenti utilizzando NuGet o SDK di estensione
ms.date: 08/02/2019
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 372e82f9bb032ac5a81362017d2062ecf0d44e3f
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2019
ms.locfileid: "68795594"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet versus SDK come riferimento a un progetto

Questo articolo è progettato per consentire agli sviluppatori di scegliere se comprimere il software come pacchetto NuGet o come Software Development Kit (SDK). In particolare, vengono illustrate le differenze tra i due quando vi si fa riferimento in un progetto di Visual Studio.

- [NuGet](/nuget) è un sistema open source di gestione dei pacchetti che semplifica il processo di incorporazione delle librerie in un progetto. Per .NET (incluso .NET Core), NuGet è il meccanismo supportato da Microsoft per la condivisione del codice. NuGet definisce il modo in cui vengono creati, ospitati e utilizzati i pacchetti per .NET e fornisce gli strumenti per ognuno di questi ruoli. In Visual Studio i pacchetti NuGet vengono aggiunti a un progetto tramite l'interfaccia utente di [Gestione pacchetti](/nuget/consume-packages/install-use-packages-visual-studio) .

- Un [SDK](../extensibility/creating-a-software-development-kit.md) è una raccolta di file che Visual Studio considera come un singolo elemento di riferimento. La finestra di dialogo Gestione riferimenti in Visual Studio elenca tutti gli SDK rilevanti per il progetto corrente quando si sceglie **Aggiungi riferimento**. Quando si aggiunge un SDK a un progetto, è possibile accedere a tutto il contenuto di tale SDK tramite IntelliSense, la finestra casella degli strumenti, le finestre di progettazione, il Visualizzatore oggetti, MSBuild, distribuzione, debug e creazione di pacchetti.

## <a name="which-mechanism-should-i-use"></a>Scelta del meccanismo da usare

La tabella seguente consente di confrontare le funzionalità di riferimento di un SDK con le funzionalità di riferimento di NuGet.

| Funzionalità | Supporto SDK | Note all'SDK | Supporto NuGet | Note a NuGet |
| - | - | - |---------------| - |
| Facendo riferimento a una sola entità, il meccanismo rende disponibili tutti i file e tutte le funzionalità. | Y | Per aggiungere un SDK, usare la finestra di dialogo **Gestione riferimenti**. Tutti i file e tutte le funzionalità sono disponibili durante il flusso di lavoro di sviluppo. | Y | |
| MSBuild consuma automaticamente gli assembly e i file di metadati (con estensione *winmd*) di Windows. | Y | I riferimenti all'interno dell'SDK vengono passati automaticamente al compilatore. | Y | |
| MSBuild consuma automaticamente i file con estensione h o lib. | Y | Il file *NomeSDK.props* indica a Visual Studio come impostare la directory di Visual C++ e così via, per il consumo automatico dei file con estensione *h* o *lib*. | N | |
| MSBuild consuma automaticamente i file con estensione *js* o *css*. | Y | In **Esplora soluzioni** è possibile espandere il nodo dei riferimenti di JavaScript SDK per visualizzare singoli file con estensione *js* o *css* e quindi generare tag `<source include/>` trascinando i file sui rispettivi file di origine. L'SDK supporta F5 e il programma di installazione automatica dei pacchetti. | Y | |
| MSBuild aggiunge automaticamente il controllo nella **casella degli strumenti**. | Y | La **casella degli strumenti** può consumare gli SDK e visualizzare i controlli nelle schede specificate dall'utente. | N | |
| Il meccanismo supporta il programma di installazione di Visual Studio per le estensioni (VSIX, Visual Studio Installer for eXtensions). | Y | VSIX è dotato di un manifesto speciale e di logica per la creazione di pacchetti SDK | Y | È possibile incorporare VSIX in un altro programma di installazione. |
| Il **Visualizzatore oggetti** enumera i riferimenti. | Y | Il **Visualizzatore oggetti** ottiene automaticamente l'elenco di riferimenti negli SDK e li enumera. | N | |
| I file e i collegamenti vengono aggiunti automaticamente alla finestra di dialogo **Gestione riferimenti**. I collegamenti della Guida e così via vengono popolati automaticamente. | Y | La finestra di dialogo **Gestione riferimenti** enumera automaticamente gli SDK, nonché i collegamenti della Guida e l'elenco delle dipendenze degli SDK. | N | NuGet ha una propria finestra di dialogo, **Gestisci pacchetti NuGet**. |
| Il meccanismo supporta più architetture. | Y | Gli SDK possono fornire più configurazioni. MSBuild consuma i file appropriati per ogni configurazione di progetto. | N | |
| Il meccanismo supporta più configurazioni. | Y | Gli SDK possono fornire più configurazioni. A seconda dell'architettura del progetto, MSBuild consuma i file appropriati per ogni architettura di progetto. | N | |
| Il meccanismo consente di specificare che cosa non deve essere copiato. | Y | A seconda che i file vengano trascinati nella cartella *\redist* o *\designtime*, è possibile determinare quali file copiare nel pacchetto dell'applicazione che li consuma. | N | I file da copiare vengono dichiarati dall'utente nel manifesto del pacchetto. |
| Il contenuto viene visualizzato nei file localizzati. | Y | I documenti XML localizzati negli SDK vengono inclusi automaticamente per una migliore esperienza in fase di progettazione. | N | |
| MSBuild supporta il consumo di più versioni di un SDK contemporaneamente. | Y | L'SDK supporta il consumo di più versioni contemporaneamente. | N | Questo non ha a che fare con i riferimenti. Non è possibile avere nel progetto più versioni dei file NuGet contemporaneamente. |
| Il meccanismo supporta la definizione dei framework di destinazione, delle versioni di Visual Studio e dei tipi di progetto applicabili. | Y | La finestra di dialogo **Gestione riferimenti** e la **casella degli strumenti** visualizzano solo gli SDK applicabili per un progetto, in modo che gli utenti possano scegliere più facilmente l'SDK appropriato. | Y (parziale) | Il pivot è il framework di destinazione. Non ci sono filtri nell'interfaccia utente. Durante l'installazione potrebbe essere restituito un errore. |
| Il meccanismo supporta l'indicazione delle informazioni di registrazione per WinMD nativi. | Y | È possibile specificare la correlazione tra il file con estensione winmd e il file con estensione dll in *SDKManifest.xml*. | N | |
| Il meccanismo supporta l'indicazione delle dipendenze da altri SDK. | Y | L'SDK si limita a informare l'utente. L'utente deve comunque installarle e farvi riferimento manualmente. | Y | NuGet le richiama automaticamente. L'utente non riceve alcuna notifica. |
| Il meccanismo si integra con i concetti di [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], ad esempio il manifesto dell'app e l'ID framework. | Y | L'SDK deve passare i concetti specifici di [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] in modo che la creazione di pacchetti e F5 funzionino correttamente con gli SDK disponibili in [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | N | |
| Il meccanismo si integra con la pipeline di debug delle app per le app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. | Y | L'SDK deve passare concetti specifici di [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] in modo che la creazione di pacchetti e F5 funzionino correttamente con gli SDK disponibili in [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | Il contenuto NuGet diventa parte del progetto. Non sono necessarie particolari considerazioni relative al comando F5. |
| Il meccanismo si integra con i manifesti delle app. | Y | L'SDK deve passare concetti specifici di [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] in modo che la creazione di pacchetti e F5 funzionino correttamente con gli SDK disponibili in [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | Il contenuto NuGet diventa parte del progetto. Non sono necessarie particolari considerazioni relative al comando F5. |
| Il meccanismo distribuisce file non di riferimento, ad esempio un framework di test con cui eseguire i test delle app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. | Y | Se si trascinano i file nella cartella *\redist*, questi vengono distribuiti automaticamente. | Y | |
| Il meccanismo aggiunge automaticamente gli SDK della piattaforma nell'IDE di Visual Studio. | Y | Se si trascina il [!INCLUDE[win8](../debugger/includes/win8_md.md)] o il Windows Phone SDK in un percorso specifico con un layout specifico, l'SDK viene integrato automaticamente con tutte le funzionalità di Visual Studio. | N | |
| Il meccanismo supporta un computer di sviluppo pulito. In altre parole, non è richiesta alcuna installazione e il semplice recupero dal controllo del codice sorgente funziona. | N | Poiché si fa riferimento a un SDK, è necessario archiviare la soluzione e l'SDK separatamente. È possibile archiviare l'SDK dai due percorsi predefiniti non presenti nel Registro di configurazione da cui MSBuild esegue l'iterazione degli SDK. Per informazioni dettagliate, vedere [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md) (Creazione di un SDK). In alternativa, se un percorso personalizzato è costituito da SDK, è possibile specificare il codice seguente nel file di progetto:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Archiviare quindi gli SDK in tale percorso. | Y | È possibile estrarre la soluzione. Visual Studio la riconosce e agisce sui file immediatamente. |
| È possibile partecipare a un'ampia community di autori di pacchetti. | N/D | La community è nuova. | Y | |
| È possibile partecipare a un'ampia community di consumer. | N/D | La community è nuova. | Y | |
| È possibile entrare a far parte di un ecosistema di partner (raccolte personalizzate, repository e così via). | N/D | I repository disponibili includono Visual Studio Marketplace, Area download Microsoft e [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | Y | |
| Il meccanismo si integra con i server delle build di integrazione continua sia per la creazione dei pacchetti che per il consumo. | Y | L'SDK deve passare il percorso di archiviazione (proprietà SDKReferenceDirectoryRoot) a MSBuild dalla riga di comando. | Y | |
| Il meccanismo supporta sia le versioni stabili che le versioni non definitive dei pacchetti. | Y | L'SDK supporta l'aggiunta di riferimenti a più versioni. | Y | |
| Il meccanismo supporta l'aggiornamento automatico per i pacchetti installati. | Y | Se fornito come VSIX o all'interno di aggiornamenti automatici di Visual Studio, l'SDK è dotato della funzione di notifica automatica. | Y | |
| Il meccanismo contiene un file autonomo con estensione *exe* per la creazione e il consumo dei pacchetti. | Y | L'SDK contiene *MSBuild.exe*. | Y | |
| I pacchetti possono essere archiviati nel controllo della versione. | Y | Non è possibile archiviare nessun elemento all'esterno del nodo Documenti. Ciò significa che gli SDK di estensione potrebbero non essere archiviati. Le dimensioni di un SDK di estensione possono essere notevoli. | Y | |
| Per creare e consumare pacchetti è possibile usare l'interfaccia PowerShell. | Y (consumo), N (creazione) | Mancanza di strumenti per la creazione di SDK. Il consumo corrisponde all'esecuzione di MSBuild dalla riga di comando. | Y | |
| È possibile usare un pacchetto simboli per il supporto del debug. | Y | Se si trascinano file con estensione *pdb* all'interno dell'SDK, i file vengono prelevati automaticamente. | Y | |
| Il meccanismo supporta gli aggiornamenti automatici di Gestione pacchetti. | N/D | L'SDK viene rivisto con MSBuild. | Y | |
| Il meccanismo supporta un formato leggero per i manifesti. | Y | *SDKManifest.xml* supporta molti attributi, ma in genere è necessario solo un subset di dimensioni ridotte. | Y | |
| Il meccanismo è disponibile per tutte le edizioni di Visual Studio. | Y | L'SDK supporta tutte le edizioni di Visual Studio. | Y | NuGet supporta tutte le edizioni di Visual Studio. |

## <a name="see-also"></a>Vedere anche

- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
- [Gestione dei riferimenti in un progetto (Visual Studio per Mac)](/visualstudio/mac/managing-references-in-a-project)