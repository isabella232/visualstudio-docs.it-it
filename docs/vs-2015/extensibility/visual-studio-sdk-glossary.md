---
title: Glossario di Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 453826081ae3d0b747d948212e713dd672550b31
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528755"
---
# <a name="visual-studio-sdk-glossary"></a>Glossario di Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [glossario di Visual Studio SDK](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-sdk-glossary).  
  
Questo glossario include le definizioni dei termini utilizzati nel [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] documentazione.  
  
## <a name="terms"></a>Termini  
 componente aggiuntivo  
 Un'applicazione di utilità, driver o altro software aggiunti a un'applicazione primaria. Nell'ambiente di sviluppo integrato (IDE) di Visual Studio, un componente aggiuntivo è un'applicazione basata su automazione che estende le funzionalità dell'IDE.  
  
 modello di automazione  
 Il modello di automazione, noto nelle versioni precedenti di Visual Studio come modello di estendibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti tale unità IDE. Componenti aggiuntivi, le procedure guidate e le macro utilizzano gli oggetti nel modello di automazione per controllare o estendono le funzionalità dell'IDE.  
  
 contesto dell'interfaccia utente di comando  
 Associazione di un GUID con la visibilità di un comando dell'interfaccia utente o un elemento, ad esempio una barra degli strumenti. Contesto dell'interfaccia utente del comando è diversa dalla contesto di selezione, in quanto non è collegato a una finestra.  
  
 Contesto dell'interfaccia utente del comando può essere utilizzato per:  
  
-   Assegnare un GUID a una barra degli strumenti viene visualizzata quando viene attivata una particolare finestra.  
  
-   Assegnare un GUID per la disponibilità di un comando senza la necessità di caricare o eseguire un pacchetto VSPackage.  
  
-   Assegnare un GUID per influire sul tasto di scelta rapida attiva.  
  
-   Assegnare un GUID per attivare la registrazione macro.  
  
-   Assegnare un GUID per attivare la modalità di debug o per passare dalla progettazione alla modalità di esecuzione in un editor.  
  
 component  
 Componente software che può essere eseguito parte delle funzionalità di un'applicazione senza tale applicazione con le informazioni sull'implementazione del software pre-esistenti. Comunicazione tra un componente e un'applicazione è esclusivamente tramite interfacce OLE stile.  
  
 gestione dei componenti  
 Un servizio, `SOleComponentManager`, che fornisce servizi di coordinamento non di interfaccia utente per i componenti di livello superiore. Il `SOleComponentManager` del servizio implementa il `IOleComponentManager` interfaccia.  
  
 gestione dei componenti dell'interfaccia utente  
 Un servizio, `SOleComponentUIManager`, che fornisce servizi coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` del servizio implementa le `IOleComponentUIManager` e `IOleInPlaceComponentUIManager` interfacce.  
  
 contenitore di contesto  
 Un `IVsUserContext` oggetto (COM) collegato a un componente di ambiente. Questo oggetto contiene parole chiave di ricerca, le parole chiave F1 e gli attributi relativi al componente. Contenitori di contesto inoltre puntano a qualsiasi elenco di sottocontesti collegati ad essi.  
  
 provider di contesto  
 Un componente nell'IDE che dispone di un contenitore di contesto è associato. Tali componenti includono una finestra degli strumenti, editor o la gerarchia di progetto.  
  
 finestra di progettazione  
 Un'interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente (moduli, pulsanti e altri controlli).  
  
 Oggetto DocData  
 Un oggetto COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente la separazione di documento/visualizzazione (ad esempio, nel caso dell'editor di testo, questa sarebbe il buffer di testo sottostante tutte le visualizzazioni dell'editor di testo). Se l'oggetto EditorFactory non fornisce questo oggetto, l'IDE verrà produrre uno per suo conto. La responsabilità di questo oggetto consiste nel gestire la persistenza dei dati e la semantica di condivisione per più viste attraverso questa stessa `DocData`. Se il `DocData` oggetto supporta la `IOleCommandTarget` interfaccia, verrà incluso nel routing dei comandi dell'UIShell.  
  
 DocObject  
 Tecnologia usata per ospitare l'interfaccia utente in un intervallo fornito dall'host. In particolare, questo termine si riferisce all'incorporamento di qualsiasi che supporta il `IOleDocument` e relative interfacce. Questa tecnologia ha molte applicazioni potenziali, ad esempio un dettaglio di implementazione di documenti di COM, finestre degli strumenti in Visual Basic 5.0, le finestre di progettazione ActiveX in Visual Basic 6.0 e così via.  
  
 documento  
 Usato per fare riferimento in modo generico per il documento nel suo complesso, ovvero sia le `DocData` e il `DocView`. Ad esempio, un DocumentFrame contiene un `DocView`, ma anche mantiene un riferimento al `DocData` per gestire la persistenza.  
  
 DocView  
 Il DocObject/incorporamento/riquadro della finestra con cui interagisce l'utente per visualizzare e manipolare sottostante `DocData`. Si noti che gli utenti non sfruttare la separazione di documenti/visualizzazioni che fa parte di `DocObject` progettazione di interfacce. Gli utenti usano un'intera DocObject per fungere da una vista anziché una nozione più astratto (e meno formalizzato) dei dati sottostanti, noti come `DocData`. `DocView` gli oggetti vengono sempre incorporati con gli oggetti di frame di documento (finestre figlio MDI) dell'IDE.  
  
 DTE  
 Il `DTE` oggetto (estensibilità degli strumenti di sviluppo) è il punto di accesso di livello superiore nel modello di automazione di Visual Studio, che consente di automatizzare ed estendere l'IDE a livello di codice.  
  
 Finestra Guida dinamica  
 Finestra dello strumento che viene implementata dall'IDE e visualizza un elenco di argomenti della Guida F1 o parola chiave di ricerca.  
  
 editor  
 Codice (classe, CLSID) che implementa il `DocView`. Implementa inoltre `DocData` se è supportata la separazione di visualizzazione/data.  
  
 estensione  
 Una funzionalità che consente di modificare, consente di personalizzare o aggiunge a un ambiente IDE. Si creano estensioni usando il modello di automazione o i pacchetti VSPackage.  
  
 editor esterno  
 Un editor che non è specifico per l'IDE, ad esempio Microsoft Word. È stato registrato tramite i proprio meccanismi e può essere usato all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzata in una finestra dell'IDE. Se non può essere incorporato, viene creata una finestra di primo livello separata.  
  
 gerarchia  
 Struttura ad albero dei nodi, ogni nodo associato a un set di proprietà.  
  
 componente di primo livello indipendente  
 Un componente che usa una finestra di primo livello non modo e può operare in modo efficace come una finestra di applicazione autonoma, ma viene implementato come un oggetto in-process. Pertanto, un componente indipendente di primo livello deve coordinare servizi del ciclo di messaggi con l'IDE e modalità. Gli oggetti in-process non è proprio ciclo di messaggi.  
  
 provider di informazioni  
 Il provider di informazioni è un modulo che può cercare le parole chiave e restituire un elenco di argomenti, sotto forma di `IVsUserContextItem` oggetti. Per fornire gli elementi di parola chiave F1 e ricerca per il provider di informazioni, registrare il file della Guida compilato (. HxS) con il sistema. Gli argomenti della Guida in questi file vengono usati per fornire l'elenco degli argomenti visualizzati nella finestra Guida dinamica e indicato se un utente preme F1.  
  
 componente sul posto  
 Un oggetto VSPackage che implementa il `IOleInPlaceComponent` interfaccia per la gestione di una finestra in modo visivo all'interno di una finestra del documento dell'IDE di proprietà. I componenti sul posto non partecipano standard OLE dall'unione di menu; al contrario si integrano loro elementi dell'interfaccia utente nell'IDE.  
  
 Esistono due tipi di componenti sul posto: hardwired posto componenti e controlli del componente.  
  
 Hardwired posto componenti sono disponibili i menu, barre degli strumenti e i comandi che sono strettamente integrati nell'interfaccia utente dell'IDE, verrà visualizzato come se sono state compilate direttamente nell'IDE.  
  
 Controlli del componente non siano presenti i propri elementi dell'interfaccia utente integrati nell'IDE di; In alternativa usare i menu, comandi e le barre degli strumenti dell'IDE. Ad esempio, il comando grassetto potrebbe essere usato mostrato in grassetto una parola selezionata all'interno di un controllo RTF incorporato in un form. Controlli del componente possono tuttavia richiedere che visualizzati elementi dell'interfaccia utente di specifiche del componente installati in modo dinamico.  
  
 servizio di linguaggio  
 Un set di oggetti che consente agli sviluppatori di VSPackage implementare le funzionalità dell'editor di codice linguaggio computer, ad esempio il testo di contrassegni e colorare.  
  
 Progetto di file esterni  
 Progetto utilizzato per i file aperti di casa che non sono presenti in qualsiasi progetto. L'elenco di elementi in questo progetto non è persistente.  
  
 progetto  
 I progetti sono costituiti da oggetti della gerarchia o COM gli oggetti che implementano il `IVsHierarchy` interfaccia.  
  
 progettazione specifici del progetto o nell'editor  
 Finestra di progettazione che non può essere usato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione specifici del progetto immettere le informazioni di Factory dell'Editor del Registro di sistema. L'IDE quindi possibile creare un'istanza della finestra di progettazione ogni volta che un determinato tipo di file viene aperto in un particolare progetto.  
  
 finestra di tipi di progetto  
 Una finestra che monitora costantemente la gerarchia del progetto attualmente attiva e l'elemento dal contesto di selezione globale. Tipo di progetto windows Usa il `SVsTrackSelectionEx` servizio per indicare all'IDE di modifiche e per visualizzare il feedback all'utente. Esplora soluzioni è un esempio di una finestra del tipo di progetto.  
  
 Finestra Proprietà  
 In precedenza Visualizzatore proprietà.  
  
 Progetti in base al riferimento  
 Progetto che non richiedono i file per il progetto si trovi nella stessa directory. Al contrario, i riferimenti ai file da altre directory non correlate sono archiviati e gestiti dal progetto stesso.  
  
 tabella documenti in esecuzione  
 Struttura interna con cui l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. Questo elenco include tutti i documenti aperti in memoria indipendentemente dal fatto che i documenti sono attualmente in corso di modifica. Un documento è qualsiasi elemento che viene salvato, incluse le stored procedure aperte in un editor, i file in un progetto o file di progetto principale (ad esempio, *. vcproj file).  
  
 Contesto di selezione  
 Dati che fa parte dei dettagli di ogni finestra dell'IDE e consente di tenere traccia delle selezioni attive. Contesto di selezione è costituita da:  
  
-   Puntatore al `IVsHierarchy` dell'interfaccia della gerarchia del progetto  
  
-   Identificatore dell'elemento dell'elemento del progetto.  
  
-   Puntatore al `ISelectionContainer` interfaccia che fornisce accesso alle proprietà di oggetti attivi.  
  
-   Matrice di valori di elemento.  
  
 servizio  
 Un contratto per un set di interfacce COM che si trovano in un singolo oggetto COM. Quando si crea un servizio, che è identificato da un GUID, è definire il set di interfacce COM che esegue il servizio. Gli oggetti COM utilizzano servizi di comunicare tra loro.  
  
 Soluzione  
 Gruppo di progetti correlati con cui lavora un utente.  
  
 finestra di progettazione standard  
 Finestra di progettazione che può essere usato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard immettere le informazioni di Factory dell'Editor del Registro di sistema. L'IDE quindi possibile creare un'istanza della finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. Devono salvare in modo permanente i dati in un file.  
  
 editor standard  
 Editor che può essere utilizzato indipendente da qualsiasi tipo di progetto specifico. Tali editor includono EditorFactories registrato nel Registro di sistema. In questo modo l'IDE individuare e richiamare l'editor.  
  
 editor standard del sistema operativo  
 Un tipo di incorporamento che non è Visual-Studio specifico. È stato registrato usando le chiavi di Win32 note (ad esempio, Esplora risorse Win32 sa come richiamare). Se un editor di questo tipo può essere incorporato, l'editor visualizzerà comunque al suo posto nell'IDE. In caso contrario, viene creata una finestra di primo livello separata per tali editor.  
  
 elenco di sottocontesti  
 Un `IVsUserContext` oggetto collegato a un contenitore di contesto. Questo oggetto contiene parole chiave di ricerca, le parole chiave F1 e attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.  
  
 Elenco attività  
 Finestra dello strumento che viene implementata dall'IDE e visualizza un elenco di attività attive.  
  
 Buffer di testo  
 Nome comune per l'oggetto `VSTextBuffer`.  
  
 Visualizzazione di testo  
 Nome comune per l'oggetto `VSTextView`.  
  
 componente di primo livello dello strumento  
 Un componente che funziona come una finestra popup modale, coordinamento perfettamente con l'interfaccia utente dell'IDE. Ad esempio i componenti indipendenti di primo livello, componenti di livello principale dello strumento devono coordinare anche servizi del ciclo di messaggi con l'IDE e modalità.  
  
 componente di primo livello  
 Un oggetto VSPackage che gestisce una finestra di primo livello non modo anziché l'area client di una finestra dell'IDE. Implementata da componenti di livello superiore di `IOleComponent` interfaccia possa sfruttare i vantaggi dei servizi del ciclo di messaggi, ad esempio l'accesso a tempo di inattività.  
  
 Attiva nell'interfaccia utente  
 Un oggetto VSPackage che è visibile e attualmente dispone dello stato attivo.  
  
 Gerarchia dell'interfaccia utente  
 Un oggetto COM che implementa il `IVsUIHierarchy` interfaccia per consentire la visualizzazione di una gerarchia. Implementa la finestra gerarchia dell'interfaccia utente di `ISelectionContainer` interfaccia per aggiornare la finestra Proprietà, altre finestre tipo di progetto è possono usare questa implementazione, se lo si desidera.  
  
 VSCT  
 Visual Studio Command Table. Il file con estensione vsct contiene informazioni sulla selezione host e i comportamenti di menu, barre degli strumenti e comandi in formato XML.  
  
 VSPackage  
 Un componente installabile software che consente di estendere l'IDE di Visual Studio aggiungendo uno o più dei valori seguenti: interfaccia utente, servizi, tipi di progetti o editor/finestra di progettazione. Un pacchetto VSPackage è costituito da un oggetto COM che implementa il `IVsPackage` interfaccia e uno o più altri oggetti COM che implementano altre interfacce per supportare altre funzioni e selezione. Inoltre, un pacchetto VSPackage ha i requisiti di registrazione specifiche.

