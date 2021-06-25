---
title: Visual Studio glossario dell'SDK | Microsoft Docs
description: Questo glossario fornisce le definizioni per i termini usati nella documentazione Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49e91a64220882eea196819a1860052dc871bec4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905423"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio glossario di SDK
Questo glossario fornisce le definizioni per i termini usati nella [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentazione.

## <a name="terms"></a>Termini
 componente aggiuntivo Applicazione di utilità, driver o altro software aggiunto a un'applicazione primaria. Nell'Visual Studio di sviluppo integrato (IDE, Integrated Development Environment) un componente aggiuntivo è un'applicazione basata su Automazione che estende le funzionalità dell'IDE.

 modello di automazione Il modello di automazione, noto nelle versioni precedenti di Visual Studio come modello di estendibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti che guidano l'IDE. I componenti aggiuntivi, le procedure guidate e le macro usano oggetti nel modello di automazione per controllare o estendere le funzionalità dell'IDE.

 contesto dell'interfaccia utente del comando Associazione di un GUID con la visibilità di un comando o di un elemento dell'interfaccia utente, ad esempio una barra degli strumenti. Il contesto dell'interfaccia utente dei comandi è diverso dal contesto di selezione perché non è associato a una finestra.

 Il contesto dell'interfaccia utente dei comandi può essere usato per:

- Assegnare un GUID a una barra degli strumenti visualizzata quando viene attivata una determinata finestra.

- Assegnare un GUID alla disponibilità di un comando senza dover caricare o eseguire un VSPackage.

- Assegnare un GUID per influire sull'associazione di tasti attiva.

- Assegnare un GUID per attivare la registrazione delle macro.

- Assegnare un GUID per attivare la modalità di debug o passare dalla modalità di progettazione alla modalità di esecuzione in un editor.

  componente Componente Software che può essere reso parte della funzionalità di un'applicazione senza che tale applicazione abbia informazioni preesiste sull'implementazione del software. La comunicazione tra un componente e un'applicazione si basa esclusivamente su interfacce di stile OLE.

  gestione componenti Un servizio, `SOleComponentManager` , che fornisce servizi di coordinamento non dell'interfaccia utente per i componenti di primo livello. Il `SOleComponentManager` servizio implementa `IOleComponentManager` l'interfaccia .

  Gestione interfaccia utente componente Un servizio, `SOleComponentUIManager` , che fornisce servizi di coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` servizio implementa le interfacce e `IOleComponentUIManager` `IOleInPlaceComponentUIManager` .

  context bag Oggetto `IVsUserContext` (oggetto COM) associato a un componente dell'ambiente. Questo oggetto contiene parole chiave di ricerca, parole chiave **F1** e attributi correlati al componente. I sacchetti di contesto puntano anche a tutti i sacchetti di sottocontesto collegati.

  provider di contesto Componente nell'IDE a cui è associato un contenitore del contesto. Tali componenti includono una finestra degli strumenti, un editor o una gerarchia di progetti.

  designer Interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente (form, pulsanti e altri controlli).

  DocData Un oggetto COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente la separazione documento/visualizzazione (ad esempio, nel caso dell'editor di testo, si tratta del buffer di testo sottostante tutte le visualizzazioni dell'editor di testo). Se EditorFactory non fornisce questo oggetto, l'IDE ne produce uno per suo conto. La responsabilità di questo oggetto è gestire la persistenza dei dati e la semantica di condivisione per più visualizzazioni sullo stesso `DocData` oggetto . Se `DocData` l'oggetto supporta `IOleCommandTarget` l'interfaccia , viene incluso nel routing dei comandi di UIShell.

  Tecnologia DocObject usata per ospitare l'interfaccia utente all'interno di un frame fornito dall'host. In particolare, questo termine si riferisce a qualsiasi incorporamento che supporta le `IOleDocument` interfacce e correlate. Questa tecnologia ha molte potenziali applicazioni, ad esempio un dettaglio di implementazione di documenti COM, finestre degli strumenti in Visual Basic 5.0, finestre di progettazione ActiveX in Visual Basic 6.0 e così via.

  document Usato per fare riferimento in modo generico al documento nel suo complesso, sia `DocData` che `DocView` . Ad esempio, un DocumentFrame contiene un oggetto , ma mantiene anche un riferimento `DocView` a per gestire la `DocData` persistenza.

  DocView DocObject/Embedding/WindowPane con cui l'utente interagisce per visualizzare e modificare l'oggetto `DocData` sottostante. Gli utenti non sfruttano la separazione documento/visualizzazione che fa parte della progettazione `DocObject` dell'interfaccia. Gli utenti usano un intero DocObject per fungere da visualizzazione anziché usare una nozione più astratta (e meno formalizzata) dei dati sottostanti nota come `DocData` . `DocView` Gli oggetti vengono sempre incorporati con gli oggetti frame del documento (finestre figlio MDI) dell'IDE.

  DTE L'oggetto (estendibilità degli strumenti di sviluppo) è il punto di accesso più in alto nel modello di automazione di Visual Studio, che consente di automatizzare ed estendere l'IDE a livello di `DTE` codice.

  Finestra Guida dinamica Finestra degli strumenti implementata dall'IDE e che visualizza un elenco di parole chiave di ricerca o argomenti della Guida **F1.**

  editor Codice (classe, CLSID) che implementa `DocView` . Implementa inoltre se `DocData` la separazione dei dati e della vista è supportata.

  estensione Funzionalità che modifica, personalizza o aggiunge a un IDE. Le estensioni vengono create usando il modello di automazione o i pacchetti VSPackage.

  editor esterno Un editor non specifico dell'IDE, ad esempio Microsoft Word. È stato registrato tramite meccanismi propri e può essere usato all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzato all'interno di una finestra nell'IDE. Se non può essere incorporata, viene creata una finestra di primo livello separata.

  gerarchia Albero dei nodi, ogni nodo associato a un set di proprietà.

  componente indipendente di primo livello Componente che usa una finestra di primo livello non modabile e può funzionare in modo efficace come finestra dell'applicazione autonoma, ma viene implementato come oggetto in-process. Pertanto, un componente di primo livello indipendente deve coordinare i servizi di modalità e ciclo di messaggi con l'IDE. Gli oggetti in-process non hanno un proprio ciclo di messaggi.

  provider di informazioni Il provider di informazioni è un modulo in grado di cercare parole chiave e restituire un elenco di argomenti sotto forma di `IVsUserContextItem` oggetti . Per specificare **F1 e** gli elementi delle parole chiave di ricerca per il provider di informazioni, registrare il file della Guida compilato (*. HxS*) con il sistema. Gli argomenti della Guida in questi file forniscono l'elenco degli argomenti visualizzati nella finestra Guida dinamica e indicano se un utente preme **F1.**

  Componente sul posto Oggetto VSPackage che implementa l'interfaccia per gestire una finestra contenuta visivamente all'interno di una finestra del documento `IOleInPlaceComponent` di proprietà dell'IDE. I componenti sul posto non partecipano all'unione di menu OLE standard. integrano invece gli elementi dell'interfaccia utente nell'IDE.

  Esistono due tipi di componenti sul posto: componenti sul posto hardwired e controlli dei componenti.

  I componenti sul posto hardwired hanno menu, barre degli strumenti e comandi strettamente integrati nell'interfaccia utente dell'IDE, visualizzati come se fossero stati compilati direttamente nell'IDE.

  I controlli componente non hanno uno dei propri elementi dell'interfaccia utente integrati nell'IDE. usano invece i menu, i comandi e le barre degli strumenti dell'IDE. Ad esempio, il comando Grassetto può essere usato per applicare il grassetto a una parola selezionata all'interno di un controllo RTF incorporato in un modulo. Tuttavia, i controlli dei componenti possono richiedere la visualizzazione di elementi dell'interfaccia utente specifici del componente installati dinamicamente.

  servizio di linguaggio Un set di oggetti che consente agli sviluppatori VSPackage di implementare le funzionalità degli editor di codice del linguaggio del computer, ad esempio il contrassegno del testo e la colorazione.

  Progetto file esterni Progetto usato per ospitare file aperti che non sono presenti in alcun progetto. L'elenco di elementi in questo progetto non è persistente.

  I progetti sono costituito da oggetti gerarchia o oggetti COM che implementano `IVsHierarchy` l'interfaccia .

  Finestra di progettazione o editor specifico del progetto Una finestra di progettazione che non può essere usata indipendentemente dal tipo di progetto. Tutte le finestre di progettazione specifiche del progetto devono immettere le informazioni di Editor Factory nel Registro di sistema. L'IDE può quindi creare un'istanza della finestra di progettazione ogni volta che viene aperto un determinato tipo di file in un progetto specifico.

  project-type window Finestra che tiene traccia costantemente della gerarchia del progetto attualmente attiva e dell'elemento dal contesto di selezione globale. Le finestre di tipo progetto usano il `SVsTrackSelectionEx` servizio per avvisare l'IDE delle modifiche e per visualizzare commenti e suggerimenti per l'utente. Esplora soluzioni è un esempio di finestra di tipo progetto.

  Finestra Proprietà visualizzatore proprietà in precedenza.

  progetti basati su riferimento Progetto che non richiede che i file per il progetto siano nella stessa directory. I riferimenti ai file di altre directory non correlate vengono invece archiviati e gestiti dal progetto stesso.

  tabella di documenti in esecuzione Struttura interna in base alla quale l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. L'elenco include tutti i documenti aperti in memoria indipendentemente dal fatto che i documenti siano in fase di modifica. Un documento è qualsiasi elemento salvato, incluse le stored procedure aperte in un editor, i file in un progetto o il file di progetto principale ,ad esempio il file con estensione vcproj.

  contesto di selezione Dati che fanno parte dei dettagli di ogni finestra nell'IDE e vengono usati per tenere traccia delle selezioni attive. Il contesto di selezione è costituito da:

- Puntatore `IVsHierarchy` all'interfaccia della gerarchia del progetto

- Identificatore dell'elemento di progetto.

- Puntatore `ISelectionContainer` all'interfaccia che fornisce l'accesso alle proprietà per gli oggetti attivi.

- Matrice di valori di elemento.

  service Un contratto per un set di interfacce COM che risiede in un singolo oggetto COM. Quando si crea un servizio identificato da un GUID, si definisce il set di interfacce COM che esegue il servizio. Gli oggetti COM usano i servizi per comunicare tra loro.

  soluzione Gruppo di progetti correlati con cui lavora un utente.

  finestra di progettazione standard Finestra di progettazione che può essere utilizzata indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard devono immettere le informazioni di Editor Factory nel Registro di sistema. L'IDE può quindi creare un'istanza della finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. I dati devono essere mantenuti in un file.

  Editor standard che può essere usato indipendentemente da qualsiasi tipo di progetto specifico. Tali editor hanno EditorFactories registrato nel Registro di sistema. Ciò consente all'IDE di individuare e richiamare l'editor.

  editor del sistema operativo standard Un'incorporamento non Visual Studio specifico. Viene registrato usando le chiavi Win32 note(ad esempio, Win32 Explorer sa come richiamare). Se è possibile incorporare un editor di questo tipo, l'editor viene comunque visualizzato al suo posto nell'IDE. In caso contrario, viene creata una finestra di primo livello separata per tali editor.

  contenitore del contesto `IVsUserContext` secondario Oggetto collegato a un contenitore di contesto. L'oggetto contiene parole chiave di ricerca, parole chiave **F1** e attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.

  Finestra degli strumenti elenco attività implementata dall'IDE e visualizza un elenco di attività attive.

  buffer di testo Nome comune per l'oggetto `VSTextBuffer` .

  Visualizzazione testo Nome comune per l'oggetto `VSTextView` .

  Componente di primo livello dello strumento Componente che opera come finestra popup non modale, coordinato strettamente con l'interfaccia utente dell'IDE. Analogamente ai componenti di primo livello indipendenti, anche i componenti di primo livello degli strumenti devono coordinare i servizi di modalità e ciclo di messaggi con l'IDE.

  componente di primo livello Oggetto VSPackage che gestisce una finestra di primo livello non modali anziché l'area client di una finestra IDE. I componenti di primo livello implementano `IOleComponent` l'interfaccia per sfruttare i vantaggi dei servizi del ciclo di messaggi, ad esempio l'accesso al tempo di inattività.

  Ui active Oggetto VSPackage visibile e attualmente attivo.

  Gerarchia dell'interfaccia utente Oggetto COM che implementa `IVsUIHierarchy` l'interfaccia per consentire la visualizzazione di una gerarchia. La finestra della gerarchia dell'interfaccia utente implementa l'interfaccia per aggiornare il Finestra Proprietà; altre finestre di tipo progetto possono usare questa `ISelectionContainer` implementazione, se necessario.

  VSCT Visual Studio Command Table. Il file con estensione vsct contiene informazioni sul posizionamento e sui comportamenti di menu, barre degli strumenti e comandi in formato XML.

  VSPackage Un componente software installabile che estende l'IDE di Visual Studio mediante l'invio di uno o più degli elementi seguenti: interfaccia utente, servizi, tipi di progetto o editor/finestra di progettazione. Un VSPackage è costituito da un oggetto COM che implementa l'interfaccia e da uno o più altri oggetti COM che implementano altre interfacce per supportare la selezione `IVsPackage` e altre funzionalità. Inoltre, un PACCHETTO VSPackage ha requisiti di registrazione specifici.
