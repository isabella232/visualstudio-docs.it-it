---
title: Glossario di Visual Studio SDK | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698161"
---
# <a name="visual-studio-sdk-glossary"></a>Glossario di Visual Studio SDK
Questo glossario fornisce le definizioni dei termini usati nella [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentazione.

## <a name="terms"></a>Termini
 componente aggiuntivo di un'applicazione di utilità, di un driver o di un altro software aggiunto a un'applicazione primaria. In Visual Studio Integrated Development Environment (IDE), un componente aggiuntivo è un'applicazione basata sull'automazione che estende le funzionalità dell'IDE.

 modello di automazione il modello di automazione, noto nelle versioni precedenti di Visual Studio come modello di estendibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti che guidano l'IDE. I componenti aggiuntivi, le procedure guidate e le macro usano oggetti nel modello di automazione per controllare o estendere le funzionalità dell'IDE.

 Associazione del contesto dell'interfaccia utente del comando di un GUID con la visibilità di un comando o elemento dell'interfaccia utente, ad esempio una barra degli strumenti. Il contesto dell'interfaccia utente del comando è diverso dal contesto di selezione perché non è collegato a una finestra.

 Il contesto dell'interfaccia utente comando può essere usato per:

- Assegnare un GUID a una barra degli strumenti visualizzata quando viene attivata una determinata finestra.

- Assegnare un GUID alla disponibilità di un comando senza dover caricare o eseguire un pacchetto VSPackage.

- Assegnare un GUID per influire sull'associazione di chiavi attive.

- Assegnare un GUID per attivare la registrazione delle macro.

- Assegnare un GUID per attivare la modalità di debug o passare dalla modalità progettazione alla modalità di esecuzione in un editor.

  componente software che può essere fatto parte delle funzionalità di un'applicazione senza che l'applicazione disponga di informazioni preesistenti sull'implementazione del software. La comunicazione tra un componente e un'applicazione si basa esclusivamente sulle interfacce di stile OLE.

  Gestione componenti un servizio, `SOleComponentManager` , che fornisce servizi di coordinamento dell'interfaccia non utente per i componenti di primo livello. Il `SOleComponentManager` servizio implementa l' `IOleComponentManager` interfaccia.

  componente UI Manager servizio, `SOleComponentUIManager` , che fornisce i servizi di coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` servizio implementa le `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfacce e.

  contenitore di contesto un `IVsUserContext` oggetto (oggetto com) collegato a un componente dell'ambiente. Questo oggetto include parole chiave di ricerca, parole chiave **F1** e attributi correlati al componente. I sacchetti di contesto puntano inoltre a tutti i contenitori di sottocontesto collegati.

  provider di contesto un componente nell'IDE a cui è associato un elenco di contesti. Tali componenti includono una finestra degli strumenti, un editor o una gerarchia del progetto.

  progettazione di un'interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente (moduli, pulsanti e altri controlli).

  DocData un oggetto COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente la separazione tra documenti e viste (ad esempio, nel caso dell'editor di testo, si tratta del buffer di testo sottostante tutte le visualizzazioni dell'editor di testo). Se il EditorFactory non fornisce questo oggetto, l'IDE ne produce uno per conto suo. La responsabilità di questo oggetto è gestire la persistenza dei dati e la semantica di condivisione per più visualizzazioni rispetto alla stessa `DocData` . Se l' `DocData` oggetto supporta l' `IOleCommandTarget` interfaccia, viene incluso nel routing dei comandi di uiShell.

  Tecnologia DocObject utilizzata per ospitare l'interfaccia utente all'interno di un frame fornito dall'host. In particolare, questo termine si riferisce a qualsiasi incorporamento che supporta le `IOleDocument` interfacce e correlate. Questa tecnologia ha molte applicazioni potenziali, ad esempio un dettaglio di implementazione di documenti COM, finestre degli strumenti in Visual Basic 5,0, progettisti ActiveX in Visual Basic 6,0 e così via.

  documento utilizzato per fare riferimento in modo generico al documento nel suo complesso, sia che `DocData` `DocView` . Ad esempio, un DocumentFrame contiene un oggetto `DocView` , ma mantiene anche un riferimento a `DocData` per gestire la persistenza.

  DocView DocObject/incapsulamento/WindowPane con cui l'utente interagisce per visualizzare e modificare l'oggetto sottostante `DocData` . Gli utenti non usufruiscono della separazione documento/visualizzazione che fa parte della `DocObject` progettazione dell'interfaccia. Gli utenti usano un intero DocObject per fungere da vista anziché usare una nozione più astratta (e meno formalizzata) dei dati sottostanti noti come `DocData` . `DocView` gli oggetti sono sempre incorporati con oggetti cornice di documento (finestre figlio MDI) dell'IDE.

  DTE l' `DTE` oggetto (extensibility degli strumenti di sviluppo) è il punto di accesso in primo piano nel modello di automazione di Visual Studio, che consente di automatizzare ed estendere l'IDE a livello di codice.

  Finestra degli strumenti della finestra Guida dinamica implementata dall'IDE e visualizza un elenco di parole chiave di ricerca o argomenti della Guida **F1** .

  Codice dell'editor (classe, CLSID) che implementa `DocView` . Implementa inoltre `DocData` se la visualizzazione e la separazione dei dati sono supportate.

  estensione di una funzionalità di modifica, personalizzazione o aggiunta a un IDE. Le estensioni vengono create usando il modello di automazione o i pacchetti VSPackage.

  editor esterno editor non specifico dell'IDE, ad esempio Microsoft Word. È stata registrata tramite i propri meccanismi e può essere usata all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzato all'interno di una finestra nell'IDE. Se non è possibile incorporare, viene creata una finestra di primo livello distinta.

  Albero gerarchico dei nodi, ogni nodo associato a un set di proprietà.

  componente di livello superiore indipendente un componente che usa una finestra di primo livello non modale e può funzionare in modo efficace come finestra dell'applicazione autonoma, ma viene implementato come un oggetto in-process. Pertanto, un componente di livello superiore indipendente deve coordinare la modalità e i servizi di Message loop con l'IDE. Gli oggetti in-process non hanno il proprio ciclo di messaggi.

  provider di informazioni il provider di informazioni è un modulo che può cercare parole chiave e restituire un elenco di argomenti, sotto forma di `IVsUserContextItem` oggetti. Per specificare gli elementi della parola chiave **F1** e Lookup per il provider di informazioni, registrare il file della Guida compilato (*. HxS*) con il sistema. Gli argomenti della Guida in questi file forniscono l'elenco degli argomenti visualizzati nella finestra Guida dinamica e mostrano se un utente preme **F1**.

  componente sul posto un oggetto VSPackage che implementa l' `IOleInPlaceComponent` interfaccia per gestire una finestra che è contenuta visivamente all'interno di una finestra del documento di proprietà dell'IDE. I componenti sul posto non partecipano al menu OLE standard-merge; ma integrano gli elementi dell'interfaccia utente nell'IDE.

  Esistono due tipi di componenti sul posto: i componenti e i controlli componenti sul posto cablati.

  I componenti cablati sul posto includono menu, barre degli strumenti e comandi integrati strettamente nell'interfaccia utente dell'IDE, che vengono visualizzati come se fossero compilati direttamente nell'IDE.

  I controlli componente non hanno elementi dell'interfaccia utente integrati nell'IDE. usano invece i menu, i comandi e le barre degli strumenti dell'IDE. Ad esempio, il comando Bold può essere usato per grassare una parola selezionata all'interno di un controllo RTF incorporato in un form. Tuttavia, i controlli componente possono richiedere che vengano visualizzati elementi dell'interfaccia utente specifici del componente installati in modo dinamico.

  servizio di linguaggio un set di oggetti che consente agli sviluppatori VSPackage di implementare le funzionalità degli editor di codice della lingua del computer, ad esempio il contrassegno del testo e la colorazione.

  Progetto di file esterni usato per ospitare file aperti che non sono in alcun progetto. L'elenco di elementi in questo progetto non è permanente.

  i progetti di progetto sono costituiti da oggetti gerarchia o oggetti COM che implementano l' `IVsHierarchy` interfaccia.

  progettazione o editor specifico del progetto una finestra di progettazione che non può essere utilizzata indipendentemente dal tipo di progetto. Tutte le finestre di progettazione specifiche del progetto devono immettere le informazioni relative alla factory dell'editor nel registro di sistema. L'IDE può quindi creare un'istanza della finestra di progettazione ogni volta che un determinato tipo di file viene aperto in un determinato progetto.

  finestra del tipo di progetto finestra che tiene traccia costantemente della gerarchia e dell'elemento del progetto attualmente attivo dal contesto di selezione globale. Le finestre di tipo progetto utilizzano il `SVsTrackSelectionEx` servizio per avvisare l'IDE delle modifiche e per visualizzare commenti e suggerimenti all'utente. Esplora soluzioni è un esempio di una finestra di tipo progetto.

  Finestra Proprietà in precedenza Visualizzatore proprietà.

  Progetto di progetti basati su riferimenti che non richiede che i file del progetto si trovino nella stessa directory. Al contrario, i riferimenti ai file di altre directory non correlate vengono archiviati e gestiti dal progetto stesso.

  esecuzione della struttura interna della tabella documenti mediante la quale l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. L'elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che i documenti siano in corso di modifica. Un documento è qualsiasi elemento salvato, incluse le stored procedure aperte in un editor, i file in un progetto o il file di progetto principale (ad esempio, il file *. vcproj).

  Dati del contesto di selezione che fanno parte del dettaglio di ogni finestra nell'IDE e vengono usati per tenere traccia delle selezioni attive. Il contesto di selezione è costituito da:

- Puntatore all' `IVsHierarchy` interfaccia della gerarchia del progetto

- Identificatore dell'elemento del progetto.

- Puntatore all' `ISelectionContainer` interfaccia che fornisce l'accesso alle proprietà degli oggetti attivi.

- Matrice di valori di elemento.

  servizio un contratto per un set di interfacce COM che risiede in un singolo oggetto COM. Quando si crea un servizio, identificato da un GUID, si definisce il set di interfacce COM che esegue il servizio. Gli oggetti COM utilizzano i servizi per comunicare tra loro.

  Gruppo di soluzioni di progetti correlati con cui un utente funziona.

  finestra di progettazione standard che può essere utilizzata indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard devono immettere le informazioni relative alla factory dell'editor nel registro di sistema. L'IDE può quindi creare un'istanza della finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. I dati devono essere mantenuti in un file.

  Editor standard che può essere utilizzato indipendentemente da qualsiasi tipo di progetto specifico. Questi editor hanno registrato EditorFactories nel registro di sistema. Questo consente all'IDE di individuare e richiamare l'editor.

  Editor del sistema operativo standard un incorporamento che non è specifico di Visual Studio. Viene registrato utilizzando le chiavi Win32 note, ad esempio Win32 Explorer sa come richiamare. Se è possibile incorporare un editor di questo tipo, l'editor viene comunque visualizzato al suo posto nell'IDE. In caso contrario, per tali editor viene creata una finestra di primo livello distinta.

  contenitore di sottocontesto un `IVsUserContext` oggetto collegato a un contenitore di contesti. L'oggetto include parole chiave di ricerca, parole chiave **F1** e attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.

  Finestra degli strumenti elenco attività implementata dall'IDE e visualizza un elenco di attività attive.

  nome comune del buffer di testo per l'oggetto `VSTextBuffer` .

  Nome comune della visualizzazione di testo per l'oggetto `VSTextView` .

  componente di primo livello dello strumento un componente che funziona come finestra popup non modale, coordinandosi strettamente con l'interfaccia utente dell'IDE. Analogamente ai componenti di primo livello indipendenti, i componenti di livello superiore degli strumenti devono anche coordinare la modalità e i servizi di Message loop con l'IDE.

  componente di primo livello un oggetto VSPackage che gestisce una finestra di primo livello non modale anziché l'area client di una finestra IDE. I componenti di primo livello implementano l' `IOleComponent` interfaccia per sfruttare i vantaggi dei servizi del ciclo di messaggi, ad esempio l'accesso al tempo di inattività.

  Interfaccia utente attiva un oggetto VSPackage che è visibile e attualmente ha lo stato attivo.

  Gerarchia dell'interfaccia utente un oggetto COM che implementa l' `IVsUIHierarchy` interfaccia per consentire la visualizzazione di una gerarchia. La finestra gerarchia dell'interfaccia utente implementa l' `ISelectionContainer` interfaccia per aggiornare la finestra Proprietà; altre finestre di tipo progetto possono usare questa implementazione, se necessario.

  Tabella comandi di Visual Studio VSCT. Il file. vsct contiene informazioni sulla posizione e sui comportamenti dei menu, delle barre degli strumenti e dei comandi in formato XML.

  VSPackage un componente software installabile che estende l'IDE di Visual Studio contribuendo a uno o più degli elementi seguenti: interfaccia utente, servizi, tipi di progetto o editor/finestra di progettazione. Un pacchetto VSPackage è costituito da un oggetto COM che implementa l' `IVsPackage` interfaccia e uno o più oggetti com che implementano altre interfacce per supportare la selezione e altre funzionalità. Inoltre, un pacchetto VSPackage presenta requisiti di registrazione specifici.
