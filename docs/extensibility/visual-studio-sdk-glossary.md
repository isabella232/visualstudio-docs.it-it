---
title: Glossario di Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5aa8398f3a102031c3a40074f76557ef311d4d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322414"
---
# <a name="visual-studio-sdk-glossary"></a>Glossario di Visual Studio SDK
Questo glossario include le definizioni dei termini utilizzati nel [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentazione.

## <a name="terms"></a>Termini
 componente aggiuntivo un'applicazione di utilità, driver o altro software aggiunti a un'applicazione primaria. Nell'ambiente di sviluppo integrato (IDE) di Visual Studio, un componente aggiuntivo è un'applicazione basata su automazione che estende le funzionalità dell'IDE.

 modello di automazione con il modello di automazione, noto nelle versioni precedenti di Visual Studio come modello di estendibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti tale unità IDE. Componenti aggiuntivi, le procedure guidate e le macro utilizzano gli oggetti nel modello di automazione per controllare o estendono le funzionalità dell'IDE.

 contesto dell'interfaccia utente del comando associazione di un GUID con la visibilità di un comando dell'interfaccia utente o un elemento, ad esempio una barra degli strumenti. Contesto dell'interfaccia utente del comando è diversa dalla contesto di selezione, in quanto non è associata a una finestra.

 Contesto dell'interfaccia utente del comando può essere utilizzato per:

- Assegnare un GUID a una barra degli strumenti viene visualizzata quando viene attivata una particolare finestra.

- Assegnare un GUID per la disponibilità di un comando senza la necessità di caricare o eseguire un pacchetto VSPackage.

- Assegnare un GUID per influire sul tasto di scelta rapida attiva.

- Assegnare un GUID per attivare la registrazione macro.

- Assegnare un GUID per attivare la modalità di debug o per passare dalla progettazione alla modalità di esecuzione in un editor.

  componente software che possono essere eseguite parte delle funzionalità di un'applicazione senza tale applicazione con le informazioni sull'implementazione del software pre-esistenti. Comunicazione tra un componente e un'applicazione è esclusivamente tramite interfacce OLE stile.

  servizio di gestione un componente, `SOleComponentManager`, che fornisce servizi di coordinamento non di interfaccia utente per i componenti di livello superiore. Il `SOleComponentManager` del servizio implementa il `IOleComponentManager` interfaccia.

  servizio di gestione un componente dell'interfaccia utente, `SOleComponentUIManager`, che fornisce servizi coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` del servizio implementa le `IOleComponentUIManager` e `IOleInPlaceComponentUIManager` interfacce.

  contenitore di contesto un `IVsUserContext` oggetto (COM) collegato a un componente di ambiente. Questo oggetto contiene parole chiave di ricerca **F1** parole chiave e gli attributi relativi al componente. Contenitori di contesto inoltre puntano a qualsiasi elenco di sottocontesti collegati ad essi.

  componente provider un contesto dell'IDE che dispone di un contenitore di contesto è associato. Tali componenti includono una finestra degli strumenti, editor o la gerarchia di progetto.

  finestra di progettazione di un'interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente (moduli, pulsanti e altri controlli).

  Oggetto DocData A COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente la separazione di documento/visualizzazione (ad esempio, nel caso dell'editor di testo, questa sarebbe il buffer di testo sottostante tutte le visualizzazioni dell'editor di testo). Se l'oggetto EditorFactory non fornisce questo oggetto, l'IDE produce uno per suo conto. La responsabilità di questo oggetto consiste nel gestire la persistenza dei dati e la semantica di condivisione per più viste attraverso questa stessa `DocData`. Se il `DocData` oggetto supporta la `IOleCommandTarget` interfaccia, è inclusa nel routing dei comandi dell'UIShell.

  DocObject tecnologia usata per ospitare l'interfaccia utente in un intervallo fornito dall'host. In particolare, questo termine si riferisce all'incorporamento di qualsiasi che supporta il `IOleDocument` e relative interfacce. Questa tecnologia ha molte applicazioni potenziali, ad esempio un dettaglio di implementazione di documenti di COM, finestre degli strumenti in Visual Basic 5.0, le finestre di progettazione ActiveX in Visual Basic 6.0 e così via.

  documento utilizzato per fare riferimento in modo generico per il documento nel suo complesso, ovvero sia le `DocData` e il `DocView`. Ad esempio, un DocumentFrame contiene un `DocView`, ma anche mantiene un riferimento al `DocData` per gestire la persistenza.

  DocView The DocObject/incorporamento/riquadro della finestra con cui interagisce l'utente per visualizzare e manipolare sottostante `DocData`. Gli utenti non sfruttare la separazione di documenti/visualizzazioni che fa parte di `DocObject` progettazione di interfacce. Gli utenti usano un'intera DocObject per fungere da una vista anziché una nozione più astratto (e meno formalizzato) dei dati sottostanti, noti come `DocData`. `DocView` gli oggetti vengono sempre incorporati con gli oggetti di frame di documento (finestre figlio MDI) dell'IDE.

  DTE il `DTE` oggetto (estensibilità degli strumenti di sviluppo) è il punto di accesso di livello superiore nel modello di automazione di Visual Studio, che consente di automatizzare ed estendere l'IDE a livello di codice.

  Guida dinamica finestra degli strumenti finestra che viene implementata dall'IDE e visualizza un elenco di parole chiave di ricerca oppure **F1** gli argomenti della Guida.

  editor di codice (classe, CLSID) che implementa il `DocView`. Implementa inoltre `DocData` se è supportata la separazione dei dati e visualizzazione.

  funzionalità di estensione che consente di modificare, consente di personalizzare o aggiunge a un ambiente IDE. Si creano estensioni usando il modello di automazione o i pacchetti VSPackage.

  editor esterno, un editor che non è specifico per l'IDE, ad esempio Microsoft Word. È stato registrato tramite i proprio meccanismi e può essere usato all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzata in una finestra dell'IDE. Se non può essere incorporato, viene creata una finestra di primo livello separata.

  gerarchia dell'albero di nodi, ogni nodo associato a un set di proprietà.

  componente componente di primo livello indipendente A che usa una finestra di primo livello non modo e può operare in modo efficace come una finestra di applicazione autonoma, ma viene implementato come un oggetto in-process. Pertanto, un componente indipendente di primo livello deve coordinare servizi del ciclo di messaggi con l'IDE e modalità. Gli oggetti in-process non sono proprio ciclo di messaggi.

  informazioni provider il provider di informazioni è un modulo che può cercare le parole chiave e restituire un elenco di argomenti, sotto forma di `IVsUserContextItem` oggetti. Per fornire **F1** e parola chiave di ricerca di elementi per il provider di informazioni, registrare il file della Guida compilato ( *. HxS*) con il sistema. Gli argomenti della Guida di questi file forniscono l'elenco degli argomenti visualizzati nella finestra Guida dinamica e indicato se un utente preme **F1**.

  posto oggetto VSPackage di un componente che implementa il `IOleInPlaceComponent` interfaccia per la gestione di una finestra in modo visivo all'interno di una finestra del documento dell'IDE di proprietà. Non partecipano al posto componenti standard OLE dall'unione di menu; al contrario si integrano loro elementi dell'interfaccia utente nell'IDE.

  Esistono due tipi di componenti sul posto: hardwired posto componenti e controlli del componente.

  Hardwired posto componenti sono disponibili i menu, barre degli strumenti e i comandi che sono strettamente integrati nell'interfaccia utente dell'IDE, verrà visualizzato come se sono state compilate direttamente nell'IDE.

  Controlli del componente non sono disponibili i propri elementi dell'interfaccia utente integrati nell'IDE di; In alternativa usare i menu, comandi e le barre degli strumenti dell'IDE. Ad esempio, il comando grassetto potrebbe essere usato mostrato in grassetto una parola selezionata all'interno di un controllo RTF incorporato in un form. Controlli del componente possono tuttavia richiedere che visualizzati elementi dell'interfaccia utente di specifiche del componente installati in modo dinamico.

  linguaggio servizio un set di oggetti che consente agli sviluppatori di VSPackage per implementare le funzionalità del linguaggio di programmazione gli editor di codice, ad esempio il testo di contrassegni e colorare.

  Progetto utilizzato per i file aperti di casa che non sono in qualsiasi progetto del progetto file esterni. L'elenco di elementi in questo progetto non è persistente.

  i progetti di progetto sono costituiti da oggetti della gerarchia o COM gli oggetti che implementano il `IVsHierarchy` interfaccia.

  finestra di progettazione specifici del progetto o un editor di progettazione che non può essere usato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione specifici del progetto immettere le informazioni di Factory dell'Editor del Registro di sistema. L'IDE quindi possibile creare un'istanza della finestra di progettazione ogni volta che un determinato tipo di file viene aperto in un particolare progetto.

  tipo di progetto A finestra monitora questo costantemente la gerarchia del progetto attualmente attiva e l'elemento dal contesto di selezione globale. Tipo di progetto windows Usa il `SVsTrackSelectionEx` servizio per indicare all'IDE di modifiche e per visualizzare il feedback all'utente. Esplora soluzioni è un esempio di una finestra del tipo di progetto.

  Finestra delle proprietà in precedenza Visualizzatore proprietà.

  riferimento i progetti basati su progetto che non richiede i file per il progetto si trovi nella stessa directory. Al contrario, i riferimenti ai file da altre directory non correlate sono archiviati e gestiti dal progetto stesso.

  in esecuzione nella tabella interna struttura del documento mediante il quale l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. L'elenco include tutti i documenti aperti in memoria indipendentemente dal fatto che i documenti sono attualmente in corso di modifica. Un documento è qualsiasi elemento che viene salvato, incluse le stored procedure aperte in un editor, i file in un progetto o file di progetto principale (ad esempio, *. vcproj file).

  contesto di selezione dei dati che fa parte dei dettagli di ogni finestra dell'IDE e consente di tenere traccia delle selezioni attive. Contesto di selezione è costituita da:

- Puntatore al `IVsHierarchy` dell'interfaccia della gerarchia del progetto

- Identificatore dell'elemento dell'elemento del progetto.

- Puntatore al `ISelectionContainer` interfaccia che fornisce accesso alle proprietà di oggetti attivi.

- Matrice di valori di elemento.

  Un contratto per un set di interfacce COM che si trova in un singolo oggetto COM del servizio. Quando si crea un servizio, che è identificato da un GUID, è definire il set di interfacce COM che esegue il servizio. Gli oggetti COM utilizzano servizi di comunicare tra loro.

  soluzione di gruppo di progetti correlati con cui lavora un utente.

  progettazione di standard una finestra di progettazione che può essere usato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard immettere le informazioni di Factory dell'Editor del Registro di sistema. L'IDE quindi possibile creare un'istanza della finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. Devono salvare in modo permanente i dati in un file.

  editor standard dell'Editor che può essere utilizzato indipendente da qualsiasi tipo di progetto specifico. Tali editor includono EditorFactories registrato nel Registro di sistema. In questo modo l'IDE individuare e richiamare l'editor.

  standard del sistema operativo editor di incorporamento che non è specifico di Visual Studio. È stato registrato usando le chiavi di Win32 note (ad esempio, Esplora risorse Win32 sa come richiamare). Se un editor di questo tipo può essere incorporato, l'editor ancora visualizzata al suo posto nell'IDE. In caso contrario, viene creata una finestra di primo livello separata per tali editor.

  elenco di sottocontesti un `IVsUserContext` oggetto collegato a un contenitore di contesto. L'oggetto contiene parole chiave di ricerca **F1** parole chiave e gli attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.

  Finestra degli strumenti elenco attività che viene implementata dall'IDE e visualizza un elenco di attività attive.

  nome comune del buffer di testo per l'oggetto `VSTextBuffer`.

  Nome comune della visualizzazione testo per l'oggetto `VSTextView`.

  componente componente principale A dello strumento che agisce come una finestra popup modale, coordinamento perfettamente con l'interfaccia utente dell'IDE. Ad esempio i componenti indipendenti di primo livello, componenti di livello principale dello strumento devono coordinare anche servizi del ciclo di messaggi con l'IDE e modalità.

  oggetto di un VSPackage di componente di primo livello che gestisce una finestra di primo livello non modo anziché l'area client di una finestra dell'IDE. Implementata da componenti di livello superiore di `IOleComponent` interfaccia possa sfruttare i vantaggi dei servizi del ciclo di messaggi, ad esempio l'accesso a tempo di inattività.

  Active VSPackage di un oggetto di interfaccia utente è visibile e attualmente dispone dello stato attivo.

  Oggetto di COM di una gerarchia dell'interfaccia utente che implementa il `IVsUIHierarchy` interfaccia per consentire la visualizzazione di una gerarchia. Implementa la finestra gerarchia dell'interfaccia utente di `ISelectionContainer` interfaccia per aggiornare la finestra Proprietà, altre finestre tipo di progetto è possono usare questa implementazione, se lo si desidera.

  VSCT Visual Studio Command Table. Il file con estensione vsct contiene informazioni sulla selezione host e i comportamenti di menu, barre degli strumenti e comandi in formato XML.

  VSPackage, un componente installabile software che consente di estendere l'IDE di Visual Studio, aggiungendo uno o più dei seguenti elementi: interfaccia utente, servizi, tipi di progetti o editor/finestra di progettazione. Un pacchetto VSPackage è costituito da un oggetto COM che implementa il `IVsPackage` interfaccia e uno o più altri oggetti COM che implementano altre interfacce per supportare altre funzioni e selezione. Inoltre, un pacchetto VSPackage ha i requisiti di registrazione specifiche.