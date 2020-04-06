---
title: Glossario di Visual Studio SDK Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698161"
---
# <a name="visual-studio-sdk-glossary"></a>Glossario di Visual Studio SDK
Questo glossario fornisce le definizioni [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dei termini utilizzati nella documentazione.

## <a name="terms"></a>Termini
 componente aggiuntivo Applicazione di utilità, driver o altro software aggiunto a un'applicazione principale. Nell'ambiente di sviluppo integrato (IDE) di Visual Studio, un componente aggiuntivo è un'applicazione basata sull'automazione che estende le funzionalità dell'IDE.

 modello di automazione Il modello di automazione, noto nelle versioni precedenti di Visual Studio come modello di estendibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti che guidano l'IDE. Componenti aggiuntivi, procedure guidate e macro utilizzano oggetti nel modello di automazione per controllare o estendere la funzionalità dell'IDE.

 contesto dell'interfaccia utente comando Associazione di un GUID con la visibilità di un comando dell'interfaccia utente o di un elemento, ad esempio una barra degli strumenti. Il contesto dell'interfaccia utente dei comandi è diverso dal contesto di selezione in quanto non è associato a una finestra.

 Il contesto dell'interfaccia utente dei comandi può essere usato per:Command UI context can be used to:

- Assegnare un GUID a una barra degli strumenti che viene visualizzata quando viene attivata una determinata finestra.

- Assegnare un GUID alla disponibilità di un comando senza dover caricare o eseguire un pacchetto VSPackage.Assign a GUID to the availability of a command without having to load or run a VSPackage.

- Assegnare un GUID per influire sull'associazione di tasti attiva.

- Assegnare un GUID per attivare la registrazione macro.

- Assegnare un GUID per attivare la modalità di debug o per passare dalla modalità progettazione alla modalità di esecuzione in un editor.

  componente Pezzo di software che può essere fatto parte della funzionalità di un'applicazione senza che tale applicazione abbia informazioni preesistenti sull'implementazione del software. La comunicazione tra un componente e un'applicazione avviene esclusivamente tramite interfacce di stile OLE.

  gestione componenti Un `SOleComponentManager`servizio, che fornisce servizi di coordinamento dell'interfaccia non utente per i componenti di primo livello. Il `SOleComponentManager` servizio `IOleComponentManager` implementa l'interfaccia.

  gestore dell'interfaccia `SOleComponentUIManager`utente del componente Un servizio, che fornisce servizi di coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` servizio `IOleComponentUIManager` implementa `IOleInPlaceComponentUIManager` le interfacce e .

  context bag `IVsUserContext` Un oggetto (oggetto COM) collegato a un componente di ambiente. Questo oggetto contiene parole chiave di ricerca, parole chiave **F1** e attributi correlati al componente. Le borse di contesto indicano inoltre eventuali contenitori di sottocontesto ad essi collegati.

  provider di contesto Un componente nell'IDE a cui è associato un contenitore di contesto. Tali componenti includono una finestra degli strumenti, un editor o una gerarchia di progetto.

  Designer Un'interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente (form, pulsanti e altri controlli).

  DocData Un oggetto COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente la separazione documento/visualizzazione (ad esempio, nel caso dell'editor di testo, questo sarebbe il buffer di testo sottostante tutte le visualizzazioni dell'editor di testo). Se il EditorFactory non fornisce questo oggetto, l'IDE ne produce uno per suo conto. La responsabilità di questo oggetto consiste nel gestire la persistenza `DocData`dei dati e la semantica di condivisione per più visualizzazioni su questo stesso oggetto . Se `DocData` l'oggetto `IOleCommandTarget` supporta l'interfaccia, viene incluso nel routing dei comandi di UIShell.

  Tecnologia DocObject utilizzata per ospitare l'interfaccia utente all'interno di un frame fornito dall'host. Più specificamente, questo termine si riferisce a `IOleDocument` qualsiasi incorporamento che supporta le interfacce e correlate. Questa tecnologia ha molte applicazioni potenziali, ad esempio un dettaglio di implementazione di documenti COM, finestre degli strumenti in Visual Basic 5.0, finestre di progettazione ActiveX in Visual Basic 6.0 e così via.

  documento Utilizzato per fare riferimento genericamente all'intero documento, sia il `DocData` . `DocView` Ad esempio, un DocumentFrame contiene un `DocView`oggetto , `DocData` ma mantiene anche un riferimento a per gestire la persistenza.

  DocView DocObject/Embedding/WindowPane con cui l'utente interagisce `DocData`per visualizzare e modificare l'oggetto sottostante. Gli utenti non sfruttano la separazione documento/visualizzazione `DocObject` che fa parte della progettazione dell'interfaccia. Gli utenti utilizzano un intero oggetto DocObject per fungere da visualizzazione anziché utilizzare `DocData`una nozione più astratta (e meno formalizzata) dei dati sottostanti noti come . `DocView`gli oggetti vengono sempre incorporati con gli oggetti cornice del documento (finestre figlio MDI) dell'IDE.

  DTE `DTE` L'oggetto (Estensibilità degli strumenti di sviluppo) è il punto di accesso di livello superiore nel modello di automazione di Visual Studio, che consente di automatizzare ed estendere l'IDE a livello di codice.

  Finestra Guida dinamica, implementata dall'IDE e visualizza un elenco di parole chiave di ricerca o argomenti della Guida **F1.**

  codice dell'editor (classe, CLSID) che implementa l'oggetto `DocView`. Implementa anche `DocData` se la visualizzazione e la separazione dei dati sono supportate.

  extension Caratteristica che modifica, personalizza o aggiunge un IDE. Creare estensioni utilizzando il modello di automazione o VSPackage.You create extensions using the automation model or VSPackages.

  editor esterno Editor non specifico dell'IDE, ad esempio Microsoft Word. È stato registrato tramite i propri meccanismi e può essere utilizzato all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzato all'interno di una finestra nell'IDE. Se non può essere incorporato, viene creata una finestra di primo livello separata.

  albero gerarchico di nodi, ogni nodo associato a un set di proprietà.

  componente di primo livello indipendente Un componente che utilizza una finestra di primo livello non modale e può funzionare in modo efficace come una finestra dell'applicazione autonoma, ma viene implementato come oggetto in-process. Pertanto, un componente di primo livello indipendente deve coordinare i servizi di modalità e ciclo di messaggi con l'IDE. Gli oggetti in-process non dispongono di un proprio ciclo di messaggi.

  provider di informazioni Il provider di informazioni è un modulo in grado `IVsUserContextItem` di cercare parole chiave e restituire un elenco di argomenti, sotto forma di oggetti. Per fornire **F1** e gli elementi delle parole chiave di ricerca per il provider di informazioni, registrare il file della Guida compilato (*. HxS*) con il sistema. Negli argomenti della Guida di questi file viene visualizzato l'elenco degli argomenti visualizzati nella finestra Guida dinamica e viene visualizzato se un utente preme **F1**.

  componente sul posto un OGGETTO VSPackage che implementa l'interfaccia `IOleInPlaceComponent` per gestire una finestra che è visivamente contenuta all'interno di una finestra del documento di proprietà dell'IDE. I componenti sul posto non partecipano all'unione di menu OLE standard; invece integrano gli elementi dell'interfaccia utente nell'IDE.

  Esistono due tipi di componenti sul posto: componenti cablati sul posto e controlli dei componenti.

  I componenti sul posto cablati dispongono di menu, barre degli strumenti e comandi che sono integrati strettamente nell'interfaccia utente dell'IDE, che appaiono come se fossero stati creati direttamente nell'IDE.

  I controlli componente non dispongono di uno dei propri elementi dell'interfaccia utente integrati nell'IDE; invece utilizzano i menu, i comandi e le barre degli strumenti dell'IDE. Ad esempio, il comando Grassetto può essere utilizzato per applicare il grassetto a una parola selezionata all'interno di un controllo RTF incorporato in un modulo. Tuttavia, i controlli componente possono richiedere la visualizzazione di elementi dell'interfaccia utente specifici del componente installati in modo dinamico.

  servizio di linguaggio Un set di oggetti che consente agli sviluppatori VSPackage di implementare le funzionalità degli editor di codice del linguaggio del computer, ad esempio il contrassegno del testo e la colorazione.

  File vari progetto Progetto utilizzato per ospitare i file aperti che non sono in qualsiasi progetto. L'elenco di elementi in questo progetto non è persistente.

  I progetti sono costituiti da oggetti gerarchia `IVsHierarchy` o da oggetti COM che implementano l'interfaccia.

  progettazione o editor specifico del progetto Una finestra di progettazione che non può essere utilizzata indipendentemente dal tipo di progetto. Tutte le finestre di progettazione specifiche del progetto devono immettere le informazioni Editor Factory nel Registro di sistema. L'IDE può quindi creare un'istanza della finestra di progettazione ogni volta che un determinato tipo di file viene aperto in un determinato progetto.

  finestra di tipo progetto Finestra che tiene traccia costantemente della gerarchia di progetto e dell'elemento attualmente attivi dal contesto di selezione globale. Finestre di tipo `SVsTrackSelectionEx` progetto utilizzano il servizio per avvisare l'IDE delle modifiche e per visualizzare commenti e suggerimenti per l'utente. Esplora soluzioni è un esempio di finestra di tipo progetto.

  Finestra Proprietà In precedenza Visualizzatore proprietà.

  progetti basati su riferimenti Progetto che non richiede che i file per il progetto si trovano nella stessa directory. Al contrario, i riferimenti ai file da altre directory non correlate vengono memorizzati e gestiti dal progetto stesso.

  esecuzione tabella documenti Struttura interna con cui l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. L'elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che i documenti siano attualmente in fase di modifica. Un documento è qualsiasi elemento che viene salvato, incluse le stored procedure aperte in un editor, i file in un progetto o il file di progetto principale (ad esempio, il file con estensione vcproj).

  contesto di selezione Dati che fanno parte dei dettagli di ogni finestra nell'IDE e viene utilizzato per tenere traccia delle selezioni attive. Il contesto di selezione è costituito da:

- Puntatore `IVsHierarchy` all'interfaccia della gerarchia del progetto

- Identificatore dell'elemento di progetto.

- Puntatore `ISelectionContainer` all'interfaccia che fornisce l'accesso alle proprietà per gli oggetti attivi.

- Matrice di valori di elemento.

  service Un contratto per un set di interfacce COM che risiede in un singolo oggetto COM. Quando si crea un servizio, identificato da un GUID, si definisce il set di interfacce COM che esegue il servizio. Gli oggetti COM utilizzano i servizi per comunicare tra loro.

  soluzione Gruppo di progetti correlati con cui un utente lavora.

  finestra di progettazione standard Una finestra di progettazione che può essere utilizzata indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard devono immettere le informazioni editor Factory nel Registro di sistema. L'IDE può quindi creare un'istanza della finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. I dati devono essere mantenuti in un file.

  Editor editor standard Editor che può essere utilizzato indipendentemente da qualsiasi tipo di progetto particolare. Tali editor hanno EditorFactories registrato nel Registro di sistema. Ciò consente all'IDE di individuare e richiamare l'editor.

  editor oS standard Incorporamento che non è specifico di Visual Studio. Viene registrato utilizzando le chiavi Win32 note (ad esempio, Win32 Explorer sa come richiamare). Se tale editor può essere incorporato, l'editor viene ancora visualizzato al suo posto nell'IDE. In caso contrario, viene creata una finestra di primo livello separata per tali editor.

  sacchetto di `IVsUserContext` sottocontesto Oggetto collegato a un contenitore di contesto. L'oggetto contiene parole chiave di ricerca, parole chiave **F1** e attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.

  Finestra degli strumenti Elenco attività implementata dall'IDE e visualizza un elenco di attività attive.

  buffer di testo Nome `VSTextBuffer`comune per l'oggetto .

  Visualizzazione Testo Nome comune `VSTextView`per l'oggetto .

  componente di primo livello dello strumento Un componente che opera come una finestra popup non modale, coordinandosi strettamente con l'interfaccia utente dell'IDE. Analogamente ai componenti di primo livello indipendenti, anche i componenti di primo livello dello strumento devono coordinare i servizi di modalità e ciclo di messaggi con l'IDE.

  componente di primo livello oggetto VSPackage che gestisce una finestra di primo livello non modale anziché l'area client di una finestra dell'IDE. I componenti di `IOleComponent` primo livello implementano l'interfaccia per sfruttare i servizi del ciclo di messaggi, ad esempio l'accesso al tempo di inattività.

  Interfaccia utente attivo oggetto VSPackage che è visibile e attualmente ha lo stato attivo.

  Gerarchia dell'interfaccia utente `IVsUIHierarchy` Un oggetto COM che implementa l'interfaccia per consentire la visualizzazione di una gerarchia. La finestra della `ISelectionContainer` gerarchia dell'interfaccia utente implementa l'interfaccia per aggiornare la finestra Proprietà; altre finestre di tipo di progetto possono utilizzare questa implementazione, se lo si desidera.

  Tabella dei comandi di Visual Studio VSCT. Il file vsct contiene informazioni sul posizionamento e sui comportamenti di menu, barre degli strumenti e comandi in formato XML.

  VSPackage Un software installabile che estende l'IDE di Visual Studio contribuendo uno o più degli elementi seguenti: interfaccia utente, servizi, tipi di progetto o editor/finestra di progettazione. Un pacchetto VSPackage è costituito `IVsPackage` da un oggetto COM che implementa l'interfaccia e uno o più altri oggetti COM che implementano altre interfacce per supportare la selezione e altre funzionalità. Inoltre, un vsPackage ha requisiti di registrazione specifici.
