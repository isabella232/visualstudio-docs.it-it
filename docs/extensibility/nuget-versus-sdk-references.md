---
title: Aggiunta di riferimenti utilizzando NuGet o SDK di estensione
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad7fc9132647988aee46a2bb07e992505109d33c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702424"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet e SDK come riferimento al progetto

Questo articolo è progettato per aiutare gli sviluppatori a scegliere se creare un pacchetto del software come pacchetto NuGet o come kit di sviluppo software (SDK). In particolare, vengono illustrate le differenze tra i due quando viene fatto riferimento in un progetto di Visual Studio.Specifically, it discusses differences between the two when they're referenced in a Visual Studio project.

- [NuGet](/nuget) è un sistema di gestione di pacchetti open source che semplifica il processo di incorporamento delle librerie in un progetto. Per .NET (incluso .NET Core), NuGet è il meccanismo supportato da Microsoft per la condivisione di codice. NuGet definisce la modalità di creazione, gestione e consumo dei pacchetti per .NET e fornisce gli strumenti per ognuno di questi ruoli. In Visual Studio, aggiungere pacchetti NuGet a un progetto utilizzando l'interfaccia utente di [Gestione pacchetti.](/nuget/consume-packages/install-use-packages-visual-studio)

- Un [SDK](../extensibility/creating-a-software-development-kit.md) è una raccolta di file che Visual Studio considera come un singolo elemento di riferimento. Nella finestra di dialogo Gestione riferimenti di Visual Studio sono elencati tutti gli SDK rilevanti per il progetto corrente quando si sceglie **Aggiungi riferimento**. Quando si aggiunge un SDK a un progetto, è possibile accedere a tutto il contenuto di tale SDK tramite IntelliSense, la finestra Casella degli strumenti, le finestre di progettazione, il Visualizzatore oggetti, MSBuild, la distribuzione, il debug e la creazione di pacchetti.

## <a name="which-mechanism-should-i-use"></a>Scelta del meccanismo da usare

La tabella seguente consente di confrontare le funzionalità di riferimento di un SDK con le funzionalità di riferimento di NuGet.

| Funzionalità | Supporto SDK | Note all'SDK | Supporto NuGet | Note a NuGet |
| - | - | - |---------------| - |
| Facendo riferimento a una sola entità, il meccanismo rende disponibili tutti i file e tutte le funzionalità. | S | Per aggiungere un SDK, usare la finestra di dialogo **Gestione riferimenti**. Tutti i file e tutte le funzionalità sono disponibili durante il flusso di lavoro di sviluppo. | S | |
| MSBuild utilizza automaticamente gli assembly e i file di metadati di Windows *(con estensione winmd).* | S | I riferimenti all'interno dell'SDK vengono passati automaticamente al compilatore. | S | |
| MSBuild consuma automaticamente i file con estensione h o lib. | S | Il file *SDKName.props* indica a Visual Studio come configurare la directory di Visual C, quindi per l'utilizzo automatico dei file *con estensione h* o *lib.* | N | |
| MSBuild utilizza automaticamente i file *con estensione js* o *css.* | S | In **Esplora soluzioni**è possibile espandere il nodo di riferimento di JavaScript `<source include/>` SDK per visualizzare singoli file con estensione *js* o *css* e quindi generare tag trascinando tali file nei relativi file di origine. L'SDK supporta F5 e il programma di installazione automatica dei pacchetti. | S | |
| MSBuild aggiunge automaticamente il controllo nella **casella degli strumenti**. | S | La **casella degli strumenti** può consumare gli SDK e visualizzare i controlli nelle schede specificate dall'utente. | N | |
| Il meccanismo supporta il programma di installazione di Visual Studio per le estensioni (VSIX, Visual Studio Installer for eXtensions). | S | VSIX è dotato di un manifesto speciale e di logica per la creazione di pacchetti SDK | S | È possibile incorporare VSIX in un altro programma di installazione. |
| Il **Visualizzatore oggetti** enumera i riferimenti. | S | Il **Visualizzatore oggetti** ottiene automaticamente l'elenco di riferimenti negli SDK e li enumera. | N | |
| I file e i collegamenti vengono aggiunti automaticamente alla finestra di dialogo **Gestione riferimenti**. I collegamenti della Guida e così via vengono popolati automaticamente. | S | La finestra di dialogo **Gestione riferimenti** enumera automaticamente gli SDK, nonché i collegamenti della Guida e l'elenco delle dipendenze degli SDK. | N | NuGet ha una propria finestra di dialogo, **Gestisci pacchetti NuGet**. |
| Il meccanismo supporta più architetture. | S | Gli SDK possono fornire più configurazioni. MSBuild consuma i file appropriati per ogni configurazione di progetto. | N | |
| Il meccanismo supporta più configurazioni. | S | Gli SDK possono fornire più configurazioni. A seconda dell'architettura del progetto, MSBuild consuma i file appropriati per ogni architettura di progetto. | N | |
| Il meccanismo consente di specificare che cosa non deve essere copiato. | S | A seconda che i file vengano eliminati nella *cartella* *,* è possibile controllare quali file copiare nel pacchetto dell'applicazione consumer. | N | I file da copiare vengono dichiarati dall'utente nel manifesto del pacchetto. |
| Il contenuto viene visualizzato nei file localizzati. | S | I documenti XML localizzati negli SDK vengono inclusi automaticamente per una migliore esperienza in fase di progettazione. | N | |
| MSBuild supporta il consumo di più versioni di un SDK contemporaneamente. | S | L'SDK supporta il consumo di più versioni contemporaneamente. | N | Questo non ha a che fare con i riferimenti. Non è possibile avere nel progetto più versioni dei file NuGet contemporaneamente. |
| Il meccanismo supporta la definizione dei framework di destinazione, delle versioni di Visual Studio e dei tipi di progetto applicabili. | S | La finestra di dialogo **Gestione riferimenti** e la **casella degli strumenti** visualizzano solo gli SDK applicabili per un progetto, in modo che gli utenti possano scegliere più facilmente l'SDK appropriato. | Y (parziale) | Il pivot è il framework di destinazione. Non ci sono filtri nell'interfaccia utente. Durante l'installazione potrebbe essere restituito un errore. |
| Il meccanismo supporta l'indicazione delle informazioni di registrazione per WinMD nativi. | S | È possibile specificare la correlazione tra il file con estensione winmd e il file DLL in *SDKManifest.xml*. | N | |
| Il meccanismo supporta l'indicazione delle dipendenze da altri SDK. | S | L'SDK si limita a informare l'utente. L'utente deve comunque installarle e farvi riferimento manualmente. | S | NuGet le richiama automaticamente. L'utente non riceve alcuna notifica. |
| Il meccanismo si integra con i concetti di [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], ad esempio il manifesto dell'app e l'ID framework. | S | L'SDK deve passare i concetti specifici di [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] in modo che la creazione di pacchetti e F5 funzionino correttamente con gli SDK disponibili in [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | N | |
| Il meccanismo si integra con la pipeline di debug delle app per le app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. | S | L'SDK deve passare concetti specifici di [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] in modo che la creazione di pacchetti e F5 funzionino correttamente con gli SDK disponibili in [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | S | Il contenuto NuGet diventa parte del progetto. Non sono necessarie particolari considerazioni relative al comando F5. |
| Il meccanismo si integra con i manifesti delle app. | S | L'SDK deve passare concetti specifici di [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] in modo che la creazione di pacchetti e F5 funzionino correttamente con gli SDK disponibili in [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | S | Il contenuto NuGet diventa parte del progetto. Non sono necessarie particolari considerazioni relative al comando F5. |
| Il meccanismo distribuisce file non di riferimento, ad esempio un framework di test con cui eseguire i test delle app di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. | S | Se si rilasciano i file nella cartella *.redist,* i file vengono distribuiti automaticamente. | S | |
| Il meccanismo aggiunge automaticamente gli SDK della piattaforma nell'IDE di Visual Studio. | S | Se si trascina il [!INCLUDE[win8](../debugger/includes/win8_md.md)] o il Windows Phone SDK in un percorso specifico con un layout specifico, l'SDK viene integrato automaticamente con tutte le funzionalità di Visual Studio. | N | |
| Il meccanismo supporta un computer di sviluppo pulito. In altre parole, non è richiesta alcuna installazione e il semplice recupero dal controllo del codice sorgente funziona. | N | Poiché si fa riferimento a un SDK, è necessario archiviare la soluzione e l'SDK separatamente. È possibile archiviare l'SDK dai due percorsi predefiniti non presenti nel Registro di configurazione da cui MSBuild esegue l'iterazione degli SDK. Per informazioni dettagliate, vedere [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md) (Creazione di un SDK). In alternativa, se un percorso personalizzato è costituito da SDK, è possibile specificare il codice seguente nel file di progetto:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Archiviare quindi gli SDK in tale percorso. | S | È possibile estrarre la soluzione. Visual Studio la riconosce e agisce sui file immediatamente. |
| È possibile partecipare a un'ampia community di autori di pacchetti. | N/D | La community è nuova. | S | |
| È possibile partecipare a un'ampia community di consumer. | N/D | La community è nuova. | S | |
| È possibile entrare a far parte di un ecosistema di partner (raccolte personalizzate, repository e così via). | N/D | I repository disponibili includono Visual Studio Marketplace, Area download Microsoft e [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | S | |
| Il meccanismo si integra con i server delle build di integrazione continua sia per la creazione dei pacchetti che per il consumo. | S | L'SDK deve passare il percorso di archiviazione (proprietà SDKReferenceDirectoryRoot) a MSBuild dalla riga di comando. | S | |
| Il meccanismo supporta sia le versioni stabili che le versioni non definitive dei pacchetti. | S | L'SDK supporta l'aggiunta di riferimenti a più versioni. | S | |
| Il meccanismo supporta l'aggiornamento automatico per i pacchetti installati. | S | Se fornito come VSIX o all'interno di aggiornamenti automatici di Visual Studio, l'SDK è dotato della funzione di notifica automatica. | S | |
| Il meccanismo contiene un file *.exe* autonomo per la creazione e l'utilizzo di pacchetti. | S | L'SDK contiene *MSBuild.exe*. | S | |
| I pacchetti possono essere archiviati nel controllo della versione. | S | Non è possibile archiviare nessun elemento all'esterno del nodo Documenti. Ciò significa che gli SDK di estensione potrebbero non essere archiviati. Le dimensioni di un SDK di estensione possono essere notevoli. | S | |
| Per creare e consumare pacchetti è possibile usare l'interfaccia PowerShell. | Y (consumo), N (creazione) | Mancanza di strumenti per la creazione di SDK. Il consumo corrisponde all'esecuzione di MSBuild dalla riga di comando. | S | |
| È possibile usare un pacchetto simboli per il supporto del debug. | S | Se si rilasciano file *con estensione pdb* nell'SDK, i file vengono prelevati automaticamente. | S | |
| Il meccanismo supporta gli aggiornamenti automatici di Gestione pacchetti. | N/D | L'SDK viene rivisto con MSBuild. | S | |
| Il meccanismo supporta un formato leggero per i manifesti. | S | *SDKManifest.xml* supporta molti attributi, ma in genere è necessario un sottoinsieme di piccole dimensioni. | S | |
| Il meccanismo è disponibile per tutte le edizioni di Visual Studio. | S | L'SDK supporta tutte le edizioni di Visual Studio. | S | NuGet supporta tutte le edizioni di Visual Studio. |

## <a name="see-also"></a>Vedere anche

- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
- [Gestione dei riferimenti in un progetto (Visual Studio per Mac)](/visualstudio/mac/managing-references-in-a-project)
