---
title: Modelli di applicazione
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc14aadfafb16fcae571ab66e5811ea465cb55a9
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302399"
---
# <a name="application-patterns-for-visual-studio"></a>Modelli delle applicazioni per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interazioni con le finestre

### <a name="overview"></a>Panoramica
 I due tipi di finestra principali utilizzati in Visual Studio sono gli editor di documenti e le finestre degli strumenti. Rari, ma possibili, sono grandi finestre di dialogo non modali. Anche se questi sono tutti moderazioni nella shell, i loro modelli sono fondamentalmente diversi. In questo argomento viene illustrata la differenza tra finestre di documento, finestre degli strumenti e finestre di dialogo non modali. I modelli di finestra di dialogo modali sono trattati in [Finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Confronto dei modelli di utilizzo delle finestreComparing window usage patterns
 **Le finestre del documento** vengono quasi sempre visualizzate all'interno del documento. In questo modo l'editor di documenti una "fase centrale" per disporre le finestre degli strumenti supplementari intorno.

 Una **finestra degli strumenti** viene spesso visualizzata come una finestra separata, più piccola, che può essere visibile, nascosta o nascosta automaticamente, compressa rispetto al bordo dell'IDE. Tuttavia, a volte vengono presentati all'interno del documento bene, deselezionando il **Window/Docking** proprietà nella finestra. Ciò si traduce in più spazio, ma anche una decisione di progettazione comune: quando si tenta di integrare in Visual Studio, è necessario decidere se la funzionalità deve visualizzare una finestra degli strumenti o una finestra del documento.

 **Le finestre di dialogo non sono incoraggiate** in Visual Studio.Modeless dialogs are not encouraged in Visual Studio. In larga misura, sono – per definizione – finestre degli strumenti mobili e devono essere implementati come tali. Le finestre di dialogo non modali sono consentite nei casi in cui le dimensioni di una normale finestra degli strumenti ancorata al lato della shell sarebbero troppo limitanti. Sono inoltre consentiti nei casi in cui è probabile che l'utente sposti la finestra di dialogo su un monitor secondario.

 Pensa attentamente a quale tipo di contenitore ti serve. Considerazioni sui modelli di utilizzo comuni per la progettazione dell'interfaccia utente sono nella tabella seguente.

||Finestra del documento|Finestra degli strumenti|Finestra di dialogo non modale|
|-|---------------------|-----------------|---------------------|
|**Posizione**|Sempre posizionato all'interno del documento e non ancorare intorno ai bordi dell'IDE. Può essere "tirato fuori" in modo che galleggia separatamente dal guscio principale.|In genere ancorato a schede intorno ai bordi dell'IDE, ma può essere personalizzato per essere mobile, nascosto automaticamente (sbloccato) o ancorato all'interno del documento.|Finestra mobile di grandi dimensioni separata dall'IDE.|
|**Modello di commitCommit model**|*Commit ritardato*<br /><br /> Per salvare i dati in un documento, l'utente deve eseguire il comando File/Salva, Salva con nome o Salva tutto. Una finestra del documento ha il concetto dei dati all'interno di esso essere "sporcato" quindi il commit a uno dei comandi di salvataggio. Quando si chiude una finestra del documento, tutti i contenuti vengono salvati su disco o persi.|*Commit immediato*<br /><br /> Non esiste un modello di salvataggio. Per le finestre degli strumenti di controllo che facilitano la modifica di un file, il file deve essere aperto nell'editor o nella finestra di progettazione attiva e l'editor o la finestra di progettazione è proprietaria del salvataggio.|*Commit ritardato o immediato*<br /><br /> Molto spesso, una finestra di dialogo non modale di grandi dimensioni richiede un'azione per eseguire il commit delle modifiche e consente un'operazione "Annulla", che esegue il rollback di tutte le modifiche apportate all'interno della sessione di dialogo.  In questo modo viene differenziata una finestra di dialogo non modale da una finestra degli strumenti in tale finestre degli strumenti un modello di commit immediato.|
|**Visibilità**|*Apri/Crea (file) e Chiudi*<br /><br /> L'apertura di una finestra di documento avviene tramite l'apertura di un documento esistente o l'utilizzo di un modello per creare un nuovo documento. Non esiste un \<comando "Apri> dell'editor specifico".|*Nascondi e mostra*<br /><br /> Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate. Il contenuto e gli stati all'interno della finestra degli strumenti vengono mantenuti sia nella visualizzazione che nascosti. Le finestre degli strumenti a più istanze possono essere chiuse e nascoste. Quando una finestra degli strumenti a più istanze viene chiusa, il contenuto e lo stato all'interno della finestra degli strumenti vengono eliminati.|*Avviato da un comando*<br /><br /> Le finestre di dialogo vengono avviate da un comando basato su attività.|
|**Istanze**|*Istanza multipla*<br /><br /> Diversi editor possono essere aperti contemporaneamente e modificare file diversi, mentre alcuni editor consentono anche l'apertura dello stesso file in più editor (utilizzando il comando **Finestra > nuova finestra).**<br /><br /> Un singolo editor può modificare uno o più file contemporaneamente (Progettazione progetti).|*Istanza singola o multipla*<br /><br /> Il contenuto cambia per riflettere il contesto (come nel Visualizzatore proprietà) o spostare lo stato attivo/contesto in altre finestre (Elenco attività, Esplora soluzioni).<br /><br /> Entrambe le finestre degli strumenti a istanza singola e a più istanze devono essere associate alla finestra del documento attivo, a meno che non esista un motivo valido per non farlo.|*Istanza singola*|
|**Esempi**|**Editor di testo**, ad esempio l'editor di codice<br /><br /> **Progettare superfici,** ad esempio una finestra di progettazione di moduli o un'area di modellazione<br /><br /> **Layout dei controlli simili alle finestre**di dialogo , ad esempio Progettazione manifesto|**Esplora soluzioni** fornisce una soluzione e progetti contenuti all'interno della soluzione<br /><br /> **Esplora server** offre una visualizzazione gerarchica dei server e delle connessioni dati che l'utente sceglie di aprire nella finestra. L'apertura di un oggetto dalla gerarchia del database, ad esempio una query, apre una finestra del documento e consente all'utente di modificare la query.<br /><br /> Nel **Visualizzatore proprietà** vengono visualizzate le proprietà dell'oggetto selezionato in una finestra del documento o in un'altra finestra degli strumenti. Le proprietà vengono presentate in una visualizzazione griglia gerarchica o in controlli complessi simili a finestre di dialogo e consentono all'utente di impostare i valori per tali proprietà.||

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Finestre degli strumenti

### <a name="overview"></a>Panoramica
 Le finestre degli strumenti supportano il lavoro dell'utente che si verifica nelle finestre di documento. Possono essere utilizzati per visualizzare una gerarchia che rappresenta un oggetto radice fondamentale che Visual Studio fornisce e può modificare.

 Quando si considera una nuova finestra degli strumenti nell'IDE, gli autori devono:When considering a new tool window in the IDE, authors should:

- Usare finestre degli strumenti esistenti appropriate per le attività e non crearne di nuove con funzionalità simili. Le nuove finestre degli strumenti devono essere create solo se offrono uno "strumento" o una funzionalità significativamente diversa che non può essere integrata in una finestra simile o trasformando una finestra esistente in un hub di rotazione.

- Utilizzare una barra dei comandi standard, se necessario, nella parte superiore della finestra degli strumenti.

- Essere coerenti con i motivi già presenti in altre finestre degli strumenti per la presentazione dei controlli e la navigazione tramite tastiera.

- Essere coerenti con la presentazione del controllo in altre finestre degli strumenti.

- Le finestre degli strumenti specifiche del documento devono essere visibili automaticamente quando possibile in modo che vengano visualizzate solo quando viene attivato il documento principale.

- Assicurarsi che il contenuto della finestra sia navigabile dalla tastiera (tasti freccia di supporto).

#### <a name="tool-window-states"></a>Stati della finestra degli strumenti
 Finestre degli strumenti di Visual Studio hanno stati diversi, alcuni dei quali sono attivati dall'utente (ad esempio la funzionalità Nascondi automaticamente). Altri stati, ad esempio auto-visibile, consentono alle finestre degli strumenti di apparire nel contesto corretto e nascondere quando non è necessario. Ci sono cinque stati della finestra degli strumenti in totale.

- Le finestre degli strumenti **ancorate/bloccate** possono essere associate a uno qualsiasi dei quattro lati dell'area del documento. L'icona della puntina da disegno viene visualizzata nella barra del titolo della finestra degli strumenti. La finestra degli strumenti può essere ancorata orizzontalmente o verticalmente lungo il bordo della shell e di altre finestre degli strumenti e può anche essere collegata a schede.

- Le finestre degli strumenti **nascoste automaticamente** vengono sbloccate. La finestra può scorrere fuori dalla vista, lasciando una scheda (con il nome della finestra degli strumenti e la sua icona) sul bordo dell'area del documento. La finestra degli strumenti scorre quando un utente passa il mouse sulla scheda.

- **Le** finestre degli strumenti visibili automaticamente vengono visualizzate automaticamente quando viene avviata un'altra parte dell'interfaccia utente, ad esempio un editor, o acquisisce lo stato attivo.

- Finestre degli strumenti mobili al **passaggio** del mouse all'esterno dell'IDE. Ciò è utile per le configurazioni con più monitor.

- **Le** finestre degli strumenti per i documenti a schede possono essere ancorate all'interno del documento. Ciò è utile per le finestre degli strumenti di grandi dimensioni, ad esempio il Visualizzatore oggetti, che richiedono più spazio rispetto all'ancoraggio ai bordi della cornice.

  ![Stati della finestra degli strumenti in Visual Studio](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702-01_ToolWindowStates")

  **Stati della finestra degli strumenti in Visual Studio**

#### <a name="single-instance-and-multi-instance"></a>Istanza singola e a istanza multipla
 Le finestre degli strumenti sono a istanza singola o a istanza multipla. Alcune finestre degli strumenti a istanza singola potrebbero essere associate alla finestra del documento attivo, mentre le finestre degli strumenti a istanza multipla potrebbero non essere associate. Le finestre degli strumenti a più istanze rispondono al comando Finestra/Nuova finestra creando una nuova istanza della finestra. L'immagine seguente illustra una finestra degli strumenti che abilita il comando Nuova finestra quando è attiva un'istanza della finestra:

 ![Comandi per abilitare la finestra degli strumenti in Visual Studio](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")

 **Finestra degli strumenti che attiva il comando 'Nuova finestra' quando è attiva un'istanza della finestra**

 Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate, mentre le finestre degli strumenti a istanza multipla possono essere chiuse e nascoste. Tutte le finestre degli strumenti possono essere ancorate, collegate a schede, mobili o impostate come finestra figlio MDI (Multiple-Document Interface) (simile a una finestra del documento). Tutte le finestre degli strumenti devono rispondere ai comandi di gestione delle finestre appropriati nel menu Finestra:All tool windows should respond to the appropriate window management commands in the Window menu:

 ![Comandi per la gestione della finestra in Visual Studio](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702-03_WindowManagementControls")

 **Comandi di gestione delle finestre nel menu Finestra di Visual Studio**

#### <a name="document-specific-tool-windows"></a>Finestre degli strumenti specifiche del documento
 Alcune finestre degli strumenti sono progettate per essere modificate in base a un determinato tipo di documento. Queste finestre si aggiornano continuamente per riflettere le funzionalità applicabili alla finestra del documento attivo nell'IDE.

 Esempi di finestre degli strumenti il cui contenuto cambia per riflettere l'editor selezionato sono la casella degli strumenti e la struttura del documento. Queste finestre mostrano una filigrana quando un editor ha lo stato attivo che non offre contesto alla finestra.

#### <a name="navigable-list-tool-windows"></a>Finestre degli strumenti dell'elenco esplorabile
 Alcune finestre degli strumenti visualizzano un elenco di elementi navigabili con cui l'utente può interagire. In questo tipo di finestra, dovrebbe essere sempre presente un feedback per l'elemento corrente nell'elenco, anche se la finestra è inattiva. L'elenco deve rispondere ai comandi **GoToNextLocation** e **GoToPrevLocation** modificando anche l'elemento attualmente selezionato nella finestra

 Esempi di finestre degli strumenti elenco esplorabile sono Esplora soluzioni e la finestra Risultati ricerca.

### <a name="tool-window-types"></a>Tipi di finestra degli strumenti

#### <a name="common-tool-windows-and-their-functions"></a>Finestre degli strumenti comuni e relative funzioni

|Type|Finestra degli strumenti|Funzione|
|----------|-----------------|--------------|
|**Hierarchy**|Esplora soluzioni|Struttura ad albero gerarchica che visualizza un elenco di documenti contenuti in progetti, file esterni ed elementi di soluzione. La visualizzazione degli elementi all'interno dei progetti è definita dal pacchetto proprietario del tipo di progetto (ad esempio, tipi basati su riferimento, basati su directory o in modalità mista).|
|**Hierarchy**|Visualizzazione classi|Un albero gerarchico delle classi e vari elementi nel working set dei documenti, indipendente dai file stessi.|
|**Hierarchy**|Esplora server|Albero gerarchico che visualizza tutti i server e le connessioni dati nella soluzione.|
|**Hierarchy**|Struttura documento.|Struttura gerarchica del documento attivo.|
|**Griglia**|Proprietà|Griglia che visualizza un elenco di proprietà per l'oggetto selezionato, insieme ai selettori di valori per modificare tali proprietà.|
|**Griglia**|Elenco attività|Griglia che consente all'utente di creare/modificare/eliminare attività e commenti.|
|**Contenuto**|Guida|Una finestra che consente agli utenti di accedere a vari metodi per ottenere assistenza, da "Come posso?" video ai forum MSDN.|
|**Contenuto**|Guida dinamica|Finestra degli strumenti che visualizza i collegamenti agli argomenti della Guida applicabili alla selezione corrente.|
|**Contenuto**|Visualizzatore oggetti|Un set di frame a due colonne con un elenco di componenti oggetto gerarchici nel riquadro sinistro e le proprietà e i metodi dell'oggetto nella colonna di destra.|
|**Finestra di dialogo**|Trova, Ricerca avanzata|Finestra di dialogo che consente all'utente di trovare o trovare e sostituire in vari file all'interno della soluzione.|
|**Altro**|Casella degli strumenti|Finestra degli strumenti utilizzata per archiviare gli elementi che verranno rilasciati nelle aree di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione.|
|**Altro**|Pagina iniziale|Portale dell'utente in Visual Studio, con accesso afeed di notizie per sviluppatori, Guida di Visual Studio e progetti recenti. Gli utenti possono anche creare pagine iniziali personalizzate copiando il file StartPage.xaml dalla directory dei file di programma di Visual Studio "Common7" IDE , StartPages, nella cartella StartPages nella directory dei documenti di Visual Studio e quindi modificando manualmente il codice XAML l'apertura in Visual Studio o in un altro editor di codice.|
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Auto||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Immediato||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Output|La finestra di output può essere utilizzata ogni volta che si dispone di eventi testuali o stato da dichiarare.|
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Memoria||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Punti di interruzione||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|In esecuzione||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Documenti||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Stack di chiamate||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Variabili locali||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Orologi||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Disassembly||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Registri||
|**Debugger:** un gruppo di finestre specifiche per le attività di debug e monitoraggio|Threads||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Convenzioni dell'editor di documenti

### <a name="document-interactions"></a>Interazioni con i documenti
 Il "documento bene" è lo spazio più grande all'interno dell'IDE ed è dove l'utente in genere ha concentrato la loro attenzione al fine di completare le loro attività, assistito da finestre degli strumenti supplementari. Gli editor di documenti rappresentano le unità fondamentali di lavoro che l'utente apre e salva all'interno di Visual Studio.Document editors represent the fundamental units of work that the user opens and saves within Visual Studio. Mantengono un forte senso di selezione legato a Esplora soluzioni o altre finestre della gerarchia attiva. L'utente deve essere in grado di puntare a una di queste finestre della gerarchia e sapere dove è contenuto il documento e la relativa relazione con la soluzione, il progetto o un altro oggetto radice fornito da un pacchetto di Visual Studio.

 La modifica dei documenti richiede un'esperienza utente coerente. Per consentire all'utente di concentrarsi sull'attività in questione anziché sulla gestione delle finestre e sulla ricerca dei comandi, selezionare una strategia di visualizzazione del documento che meglio si adatta alle attività utente per la modifica di tale tipo di documento.

#### <a name="common-interactions-for-the-document-well"></a>Interazioni comuni per il documento

- Mantenere un modello di interazione coerente nelle esperienze comuni **Nuovo file** e **Apri file.**

- Aggiornare le funzionalità correlate nelle finestre e nei menu correlati all'apertura della finestra del documento.

- I comandi di menu sono integrati in modo appropriato in menu comuni quali i menu **Modifica**, **Formato**e **Visualizza.** Se è disponibile una notevole quantità di comandi specializzati, è possibile creare un nuovo menu che è visibile solo quando il documento ha lo stato attivo.

- Una barra degli strumenti incorporata può essere posizionata nella parte superiore dell'editor. È preferibile disporre di una barra degli strumenti separata che viene visualizzata all'esterno dell'editor.

- Mantenere sempre una selezione in Esplora soluzioni o una finestra della gerarchia attiva simile.

- Facendo doppio clic su un documento in Esplora soluzioni deve eseguire la stessa azione **Apri**.

- Se è possibile utilizzare più di un editor su un tipo di documento, l'utente deve essere in grado di ignorare o reimpostare l'azione predefinita su un determinato tipo di documento utilizzando la finestra di dialogo **Apri con** facendo clic con il pulsante destro del mouse sul file e selezionando **Apri con** dal menu di scelta rapida.

- Non creare una procedura guidata in un documento.

### <a name="user-expectations-for-specific-document-types"></a>Aspettative degli utenti per tipi di documenti specifici
 Esistono diversi tipi di base di editor di documenti e ognuno ha un set di interazioni che sono coerenti con altri dello stesso tipo.

- **Editor basato su testo:** editor di codice, file di logText-based editor: code editor, log files

- **Area di progettazione:** Progettazione formWPF forms designer, Windows Forms

- **Editor in stile finestra di dialogo:** Progettazione manifesto, proprietà del progettoManifest Designer, project properties

- **Progettazione modelli:** finestra di progettazione del flusso di lavoro, mappa del codice, diagramma dell'architettura, progressione

  Ci sono anche diversi tipi non editor che utilizzano bene il documento. Anche se non modificano i documenti stessi, devono seguire le interazioni standard per le finestre dei documenti.

- **Rapporti:** Report IntelliTrace, report Hyper-V, report profiler

- **Dashboard:** Hub di diagnostica

#### <a name="text-based-editors"></a>Editor basati su testo

- Il documento fa parte del modello di scheda di anteprima, consentendo di visualizzare in anteprima il documento senza aprirlo.

- La struttura del documento può essere rappresentata all'interno di una finestra degli strumenti complementare, ad esempio una struttura del documento.

- IntelliSense (se appropriato) si comporterà in modo coerente con altri editor di codice.

- I popup o l'interfaccia utente per l'accesso facilitato seguono stili e modelli simili per l'interfaccia utente simile esistente, ad esempio CodeLens.Pop-up or assistive UI follow similar styles and patterns for existing similar UI, such as CodeLens.

- I messaggi relativi allo stato del documento verranno visualizzati in un controllo della barra informazioni nella parte superiore del documento o nella barra di stato.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere e dei colori utilizzando una pagina **Strumenti > Opzioni,** ovvero la pagina Tipi di carattere e colori condivisi o una specifica per l'editor.

#### <a name="design-surfaces"></a>Progettare superfici

- Una finestra di progettazione vuota deve avere una filigrana sulla superficie che indica come iniziare.

- I meccanismi di commutazione di visualizzazione seguiranno i modelli esistenti, ad esempio fare doppio clic per aprire un editor di codice o schede all'interno della finestra del documento che consente l'interazione con entrambi i riquadri.

- L'aggiunta di elementi all'area di progettazione deve essere eseguita tramite la casella degli strumenti, a meno che non sia necessaria una finestra degli strumenti altamente specifica.

- Gli elementi sulla superficie seguiranno un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono solo comandi specifici del documento, non comandi comuni come **Salva**.

#### <a name="dialog-style-editors"></a>Editor in stile finestra di dialogo

- Il layout del controllo deve seguire le normali convenzioni di layout delle finestre di dialogo.

- Le schede all'interno dell'editor non devono corrispondere all'aspetto delle schede del documento, ma devono corrispondere a uno dei due stili di tabulazione interni consentiti.

- Gli utenti devono essere in grado di interagire con i controlli utilizzando solo la tastiera; attivando l'editor e la tabulazione attraverso i controlli o utilizzando i tasti di scelta standard.

- La finestra di progettazione deve usare il modello di salvataggio comune. Nessun generale Salva o commit pulsanti devono essere posizionati sulla superficie, anche se altri pulsanti possono essere appropriati.

#### <a name="model-designers"></a>Designer di modelli

- Una finestra di progettazione vuota deve avere una filigrana sulla superficie che indica come iniziare.

- L'aggiunta di elementi all'area di progettazione deve essere eseguita tramite la casella degli strumenti.

- Gli elementi sulla superficie seguiranno un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono solo comandi specifici del documento, non comandi comuni come **Salva**.

- Sulla superficie può essere visualizzata una legenda, indicativa o filigrana.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere/colori utilizzando una pagina **Strumenti > Opzioni,** la pagina Tipi di carattere e colori condivisi o specifica dell'editor.

#### <a name="reports"></a>Report

- I report sono in genere solo di informazioni e non partecipano al modello di salvataggio. Tuttavia, possono includere l'interazione, ad esempio collegamenti ad altre informazioni rilevanti o sezioni che si espandono e comprimono.

- La maggior parte dei comandi sulla superficie deve essere collegamenti ipertestuali, non pulsanti.

- Il layout deve includere un'intestazione e seguire le linee guida standard per il layout del report.

#### <a name="dashboards"></a>Dashboard

- I dashboard non hanno un modello di interazione, ma servono come mezzo per offrire una varietà di altri strumenti.

- Non partecipano al modello Salva.

- Gli utenti devono essere in grado di interagire con i controlli utilizzando solo la tastiera, attivando l'editor e la tabulazione attraverso i controlli o utilizzando i tasti di scelta standard.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Finestre

### <a name="introduction"></a>Introduzione
 Le finestre di dialogo in Visual Studio devono in genere supportare un'unità discreta del lavoro dell'utente e quindi essere chiuso.

 Se si è stabilito che è necessaria una finestra di dialogo, sono disponibili tre opzioni, in ordine di preferenza:

1. Integrare le funzionalità in una delle finestre di dialogo condivise in Visual Studio.Integrate your features into one of the shared dialogs in Visual Studio.

2. Creare una finestra di dialogo personalizzata utilizzando un modello trovato in una finestra di dialogo simile esistente.

3. Creare una nuova finestra di dialogo, seguendo le linee guida per l'interazione e il layout.

   In questo argomento viene descritto come scegliere il modello di finestra di dialogo corretto all'interno dei flussi di lavoro di Visual Studio e le convenzioni comuni per la progettazione di finestre di dialogo.

### <a name="themes"></a>Themes
 Le finestre di dialogo in Visual Studio seguono uno dei due stili di base:Dialogs in Visual Studio follow one of two basic styles:

#### <a name="standard-unthemed"></a>Standard (senza tema)
 La maggior parte delle finestre di dialogo sono finestre di dialogo di utilità standard e devono essere unme. Non ricreare il modello di controlli comuni o tentare di creare pulsanti o controlli "moderni" stilizzati. I controlli e l'aspetto del colore seguono le linee guida standard per [l'interazione di Windows Desktop per le finestre di dialogo.](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)

#### <a name="themed"></a>Tema
 Le finestre di dialogo di "firma" speciali possono essere a tema. Le finestre di dialogo a tema hanno un aspetto distinto, che ha anche alcuni modelli di interazione speciali associati allo stile. Tema la finestra di dialogo solo se soddisfa questi requisiti:Theme your dialog only if it meets these requirements:

- La finestra di dialogo è un'esperienza comune che verrà visualizzata e utilizzata spesso o da molti utenti (ad esempio, la finestra di dialogo **Nuovo progetto.**

- La finestra di dialogo contiene elementi importanti del marchio del prodotto (ad esempio, la finestra di dialogo **Impostazioni account).**

- La finestra di dialogo viene visualizzata come parte integrante di un flusso più ampio che include altre finestre di dialogo a tema (ad esempio, la finestra di dialogo **Aggiungi servizio connesso).**

- La finestra di dialogo è una parte importante di un'esperienza che svolge un ruolo strategico nella promozione o differenziazione di una versione del prodotto.

  Quando si crea una finestra di dialogo a tema, utilizzare i colori di ambiente appropriati e seguire i modelli di layout e interazione corretti. (Vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>Progettazione di finestre di dialogo
 Finestre di dialogo ben progettate prendono in considerazione i seguenti elementi:

- L'attività utente supportata

- Stile, lingua e terminologia del testo della finestra di dialogo

- Scelta del controllo e convenzioni dell'interfaccia utenteControl choice and UI conventions

- Specifiche del layout visivo e allineamento dei controlli

- Accesso da tastiera

#### <a name="content-organization"></a>Organizzazione dei contenuti
 Considerare le differenze tra questi tipi di finestre di dialogo di base:Consider the differences between these basic types of dialogs:

- [Le finestre di dialogo semplici](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentano i controlli in un'unica finestra modale. La presentazione può includere variazioni di pattern di controllo complessi, tra cui un selettore di campo o una barra delle icone.

- Le finestre di [dialogo a](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) più livelli vengono usate per sfruttare al meglio lo spazio sullo schermo quando una singola parte dell'interfaccia utente comprende più gruppi di controlli. I raggruppamenti della finestra di dialogo sono "stratificati" tramite controlli struttura a schede, controlli elenco di spostamento o pulsanti in modo che l'utente possa scegliere quale raggruppamento visualizzare in un determinato momento.

- [Le procedure guidate](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sono utili per indirizzare l'utente attraverso una sequenza logica di passaggi verso il completamento di un'attività. Una serie di scelte sono disponibili in pannelli sequenziali, a volte introducendo diversi flussi di lavoro ("fili") a seconda di una scelta effettuata nel pannello precedente.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Finestre di dialogo semplici
 Una semplice finestra di dialogo è una presentazione dei controlli in una singola finestra modale. Questa presentazione potrebbe includere variazioni di pattern di controllo complessi, ad esempio una selezione campi. Per le finestre di dialogo semplici, seguire il layout generale standard e qualsiasi layout specifico necessario per raggruppamenti di controlli complessi.

 ![Finestra di dialogo semplice in Visual Studio](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704-01_CreateStrongNameKey")

 **Crea chiave con nome sicuro è un esempio di una semplice finestra di dialogo in Visual Studio.Create Strong Name Key is an example of a simple dialog in Visual Studio.**

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Finestre di dialogo sovrapposte
 Le finestre di dialogo sovrapposte includono schede, dashboard e alberi incorporati. Vengono utilizzati per ottimizzare lo spazio quando sono disponibili più gruppi di controlli in un'unica parte dell'interfaccia utente. I raggruppamenti sono sovrapposti in modo che l'utente possa scegliere quale raggruppamento visualizzare in qualsiasi momento.

 Nel caso più semplice, il meccanismo per passare da un raggruppamento all'altro è un controllo struttura a schede. Ci sono diverse alternative disponibili. Per informazioni su come scegliere lo stile più appropriato, consultate Definizione delle priorità e stratificazione.

 La finestra di dialogo **Strumenti > Opzioni** è un esempio di finestra di dialogo a più livelli che utilizza un albero incorporato:

 ![Finestra di dialogo a più livelli in Visual Studio](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704-02_ToolsOptions")

 **Strumenti > Opzioni è un esempio di finestra di dialogo a più livelli in Visual Studio.Tools of Options is an example of a layered dialog in Visual Studio.**

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Procedure guidate
 Le procedure guidate sono utili per indirizzare l'utente attraverso una sequenza logica di passaggi nel completamento di un'attività. Una serie di scelte sono disponibili in pannelli sequenziali e l'utente deve continuare attraverso ogni passaggio prima di procedere al successivo. Una volta che sono disponibili valori predefiniti sufficienti, il pulsante **Fine** è abilitato.

 Le procedure guidate modali vengono utilizzate per le attività che:

- Contengono rami, in cui vengono offerti percorsi diversi a seconda delle scelte dell'utente

- Contengono dipendenze tra i passaggi, in cui i passaggi successivi dipendono dall'input dell'utente dai passaggi precedenti

- Sono sufficientemente complesse da dover utilizzare l'interfaccia utente per spiegare le scelte offerte e i possibili risultati in ogni passaggio

- Sono transazionali e richiedono il completamento completo di una serie di passaggi prima del commit delle modifiche

### <a name="common-conventions"></a>Convenzioni comuni
 Per ottenere una progettazione e una funzionalità ottimali con le finestre di dialogo, seguire queste convenzioni su dimensioni, posizione, standard, configurazione e allineamento dei controlli, testo dell'interfaccia utente, barre del titolo, pulsanti di controllo e tasti di scelta.

 Per linee guida specifiche del layout, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Dimensione
 Le finestre di dialogo devono rientrare nella risoluzione minima dello schermo di 1024x768 e le dimensioni iniziali della finestra di dialogo non devono superare i 900x700 pixel. Le finestre di dialogo possono essere ridimensionabili, ma non è un requisito.

 Esistono due consigli per le finestre di dialogo ridimensionabili:There are two recommendations for resizable dialogs:

1. Che una dimensione minima è un definito per la finestra di dialogo che ottimizzerà per il set di controlli senza ritaglio e regolare per supportare la crescita di localizzazione ragionevole.

2. Che le dimensioni scalate dall'utente permangano da una sessione all'altra. Ad esempio, se l'utente ridimensiona una finestra di dialogo al 150%, un successivo avvio della finestra di dialogo verrà visualizzato al 150%.

#### <a name="position"></a>Posizione
 Le finestre di dialogo devono essere visualizzate centrate all'interno dell'IDE al primo avvio. Per le finestre di dialogo non ridimensionabili, non è necessario che l'ultima posizione della finestra di dialogo venga mantenuta, pertanto verrà visualizzata centrata nei successivi avvii. Per le finestre di dialogo ridimensionabili, la dimensione deve essere mantenuta nei successivi avvii. Per le finestre di dialogo ridimensionabili che sono modali, la posizione non deve essere mantenuta. La loro visualizzazione centrata all'interno dell'IDE impedisce la possibilità che la finestra di dialogo venga visualizzata in una posizione imprevedibile o inutilizzabile quando la configurazione di visualizzazione dell'utente è stata modificata. Per le finestre di dialogo non modali che possono essere riposizionate, la posizione dell'utente deve essere mantenuta nei successivi avvii, in quanto la finestra di dialogo può essere utilizzata frequentemente come parte integrante di un flusso di lavoro più ampio.

 Quando le finestre di dialogo devono generare altre finestre di dialogo, la finestra di dialogo in primo piano deve propagarsi a destra e verso il basso dall'elemento padre in modo che sia ovvio per l'utente che si è verificato un accesso in una nuova posizione.

#### <a name="modality"></a>Modalità
 Essere modali significa che gli utenti sono tenuti a completare o annullare la finestra di dialogo prima di continuare. Poiché le finestre di dialogo modali impediscono all'utente di interagire con altre parti dell'ambiente, il flusso di attività della funzionalità deve usarle nel modo più parsimonioso possibile. Quando è necessaria un'operazione modale, Visual Studio dispone di una serie di finestre di dialogo condivise in cui è possibile integrare le funzionalità. Se è necessario creare una nuova finestra di dialogo, seguire il modello di interazione di una finestra di dialogo esistente con funzionalità simili.

 Quando gli utenti devono eseguire due attività contemporaneamente, ad esempio **Trova** e **sostituisci** durante la scrittura di nuovo codice, la finestra di dialogo deve essere non modale in modo che l'utente possa passare facilmente da una all'altra. Visual Studio usa in genere le finestre degli strumenti per questo tipo di attività collegata che supporta l'editor.

#### <a name="control-configuration"></a>Configurazione del controllo
 Essere coerenti con le configurazioni di controllo esistenti che eseguire la stessa operazione in Visual Studio.Be consistent with existing control configurations that accomplish the same thing in Visual Studio.

#### <a name="title-bars"></a>Barre del titolo

- Il testo nella barra del titolo deve riflettere il nome del comando che lo ha avviato.

- Nessuna icona deve essere utilizzata nelle barre del titolo della finestra di dialogo. Nei casi in cui il sistema ne richiede uno, usare il logo di Visual Studio.In cases where the system requires one, use the Visual Studio logo.

- Le finestre di dialogo non devono avere pulsanti di riduzione a icona o ingrandimento.

- I pulsanti della Guida nella barra del titolo sono stati deprecati. Non aggiungerli alle nuove finestre di dialogo. Quando esistono, devono avviare un argomento della Guida concettualmente rilevante per l'attività.

  ![Specifiche per la barra del titolo per Visual Studio](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704-03_TitleBarSpecs")

  **Specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio.Guideline specifications for title bars in Visual Studio dialogs.**

#### <a name="control-buttons"></a>Pulsanti di controllo
 In generale, i pulsanti **OK**/**Annulla**/**Guida** devono essere disposti orizzontalmente nell'angolo inferiore destro della finestra di dialogo. Lo stack verticale alternativo è consentito se una finestra di dialogo dispone di diversi altri pulsanti nella parte inferiore della finestra di dialogo che presenterebbe confusione visiva con i pulsanti di controllo.

 ![Configurazione dei pulsanti di controllo in Visual Studio](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704-04_ControlButtonConfig")

 **Configurazioni accettabili per i pulsanti di controllo nelle finestre di dialogo di Visual StudioAcceptable configurations for control buttons in Visual Studio dialogs**

 La finestra di dialogo deve includere un pulsante di controllo predefinito. Per determinare il comando migliore da utilizzare come predefinito, scegliere una delle seguenti opzioni (elencate in ordine di precedenza):

- Scegliere il comando più sicuro e più sicuro come predefinito. Ciò significa scegliere il comando più probabile per prevenire la perdita di dati ed evitare l'accesso involontario al sistema.

- Se la perdita di dati e la sicurezza non sono fattori, scegliere il comando predefinito in base alla convenienza. L'inclusione del comando più probabile come predefinito migliorerà il flusso di lavoro dell'utente quando la finestra di dialogo supporta attività frequenti o ripetitive.

  Evitare di scegliere un'azione distruttiva in modo permanente per il comando predefinito. Se tale comando è presente, scegliere invece un comando più sicuro come predefinito.

#### <a name="access-keys"></a>Chiavi di accesso
 Non utilizzare i tasti di scelta per i **pulsanti OK**/**Annulla**/**Guida.** Questi pulsanti sono mappati ai tasti di scelta rapida per impostazione predefinita:

|Nome pulsante|Tasto di scelta rapida|
|-----------------|-----------------------|
|OK|Immettere|
|Annulla|ESC|
|Guida|F1|

#### <a name="imagery"></a>Immagini
 Usa le immagini con parsimonia nelle finestre di dialogo. Non utilizzare icone grandi nelle finestre di dialogo solo per consumare spazio. Usa le immagini solo se sono una parte importante della trasmissione del messaggio all'utente, ad esempio icone di avviso o animazioni di stato.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Assegnazione di priorità e stratificazione

#### <a name="prioritizing-your-ui"></a>Assegnazione di priorità all'interfaccia utente
 Potrebbe essere necessario portare alcuni elementi dell'interfaccia utente in primo piano e inserire il comportamento e le opzioni più avanzate (inclusi i comandi oscuri) nelle finestre di dialogo. Portare in primo piano le funzionalità di uso comune facendo spazio per esso e rendendolo visibile per impostazione predefinita nell'interfaccia utente con un'etichetta di testo quando viene visualizzata la finestra di dialogo.

#### <a name="layering-your-ui"></a>Stratificazione dell'interfaccia utente
 Se si è stabilito che una finestra di dialogo è necessaria, ma la funzionalità correlata che si desidera presentare all'utente va oltre ciò che può essere visualizzato in una semplice finestra di dialogo, è necessario sovrapporre l'interfaccia utente. I metodi di stratificazione più comuni utilizzati da Visual Studio sono schede e corridoi o dashboard. In alcuni casi, le aree che possono espandersi e comprimersi potrebbero essere appropriate. L'interfaccia utente adattiva non è in genere consigliata in Visual Studio.Adaptive UI is generally not recommended in Visual Studio.

 Esistono vantaggi e svantaggi per i diversi metodi di stratificazione dell'interfaccia utente tramite controlli di tipo scheda. Esaminare l'elenco seguente per assicurarsi di scegliere una tecnica di stratificazione appropriata alla propria situazione.

##### <a name="tabbing"></a>Tabulazione

|Meccanismo di commutazione|Vantaggi e uso appropriato|Svantaggi e uso inappropriato|
|-------------------------|------------------------------------|-----------------------------------------|
|Controllo Tab|Raggruppare logicamente le pagine della finestra di dialogo in set correlati<br /><br /> Utile per meno di cinque (o il numero di schede che rientrano in una riga nella finestra di dialogo) pagine di controlli correlati nella finestra di dialogo<br /><br /> Le etichette delle schede devono essere brevi: una o due parole in grado di identificare facilmente il contenuto<br /><br /> Uno stile di finestra di dialogo di sistema comune<br /><br /> Esempio: **Proprietà > elemento di Esplora file**|Creare etichette brevi descrittive può essere difficile<br /><br /> In genere non viene ridimensionato oltre cinque schede in una finestra di dialogo<br /><br /> Inappropriato se si dispone di troppe schede per una riga; utilizzare una tecnica di stratificazione alternativa<br /><br /> Non estensibile|
|Navigazione nella barra laterale|Dispositivo di commutazione semplice in grado di ospitare più categorie che schede<br /><br /> Elenco semplice di categorie (nessuna gerarchia)<br /><br /> Estensibilità<br /><br /> Esempio: **Personalizza... > Aggiungi comando**|Non è un buon uso dello spazio orizzontale se ci sono meno di tre gruppi<br /><br /> L'attività potrebbe essere più adatta a un menu a discesa|
|Controllo Tree|Permette categorie illimitate<br /><br /> Consente il raggruppamento e/o la gerarchia delle categorie<br /><br /> Estensibilità<br /><br /> Esempio: **Strumenti > Opzioni**|Gerarchie fortemente annidate possono causare uno scorrimento orizzontale eccessivo<br /><br /> Visual Studio ha una sovrabbondanza di visualizzazioni struttura ad albero|
|Procedura guidata|Aiuta nel completamento delle attività guidando i passaggi sequenziali basati sulle attività. La procedura guidata rappresenta un'attività di alto livello e i singoli pannelli rappresentano le sottoattività necessarie per eseguire l'attività complessiva.<br /><br /> Utile quando l'attività supera i limiti Ui, come quando l'utente avrebbe altrimenti dovuto utilizzare più editor e finestre degli strumenti per completare l'attività<br /><br /> Utile quando l'attività richiede la diramazione<br /><br /> Utile quando l'attività contiene dipendenze tra i passaggi<br /><br /> Utile quando diverse attività simili con un fork di decisione possono essere presentate in una finestra di dialogo per ridurre il numero di diverse finestre di dialogo simili.|Inappropriato per qualsiasi attività che non richiede un flusso di lavoro sequenziale<br /><br /> Gli utenti possono diventare sopraffatti e confusi da una procedura guidata con troppi passaggi<br /><br /> I maghi hanno immobili sullo schermo intrinsecamente limitati|

##### <a name="hallways-or-dashboards"></a>Corridoi o dashboard
 Le sale e i dashboard sono finestre di dialogo o pannelli che fungono da punti di avvio per altre finestre di dialogo e finestre. Il "corridoio" ben progettato espone immediatamente solo le opzioni più comuni, comandi e impostazioni, consentendo all'utente di eseguire facilmente le attività comuni. Come un corridoio del mondo reale fornisce porte per accedere alle stanze dietro di loro, qui l'interfaccia utente meno comune viene raccolto in "stanze" separate (spesso altre finestre di dialogo) di funzionalità correlate a cui si può accedere dal corridoio principale.

 In alternativa, un'interfaccia utente che offre tutte le funzionalità disponibili in una singola raccolta anziché il refactoring delle funzionalità meno comuni in posizioni separate è semplicemente un dashboard.

 ![Concetto Hallway in Outlook](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704-08_Hallway")

 **Concetto di Hallway per esporre un'interfaccia utente aggiuntiva in Outlook**

##### <a name="adaptive-ui"></a>Interfaccia utente adattiva
 Mostrare o nascondere l'interfaccia utente in base all'utilizzo o all'esperienza segnalata dall'utente è un altro modo per presentare l'interfaccia utente necessaria nascondendo altre parti. Questa operazione non è consigliata in Visual Studio poiché gli algoritmi per decidere quando mostrare o nascondere l'interfaccia utente possono essere complicate e le regole saranno sempre errate per alcuni set di casi.

## <a name="projects"></a><a name="BKMK_Projects"></a>Progetti

### <a name="projects-in-the-solution-explorer"></a>Progetti in Esplora soluzioniProjects in the Solution Explorer
 La maggior parte dei progetti è classificata come basata su riferimenti, basata su directory o mista. Tutti e tre i tipi di progetti sono supportati contemporaneamente in Esplora soluzioni. La radice dell'esperienza utente nell'utilizzo dei progetti avviene all'interno di questa finestra. Sebbene nodi di progetto diversi siano progetti di tipo riferimento, directory o in modalità mista, esiste un modello di interazione comune che deve essere applicato come punto di partenza prima di divergere in modelli utente specifici del progetto.

 I progetti devono sempre:

- Supporta la possibilità di aggiungere cartelle di progetto per organizzare il contenuto del progetto

- Mantenere un modello coerente per la persistenza del progetto

  I progetti devono inoltre mantenere modelli di interazione coerenti per:

- Rimozione di elementi di progettoRemoving project items

- Salvataggio di documenti

- Modifica delle proprietà del progetto

- Modifica del progetto in una visualizzazione alternativa

- Operazioni di trascinamento della selezione

### <a name="drag-and-drop-interaction-model"></a>Modello di interazione di trascinamento della selezione
 I progetti in genere si classificano come basati su riferimenti (in grado di rendere persistenti solo i riferimenti agli elementi di progetto nell'archivio), basati su directory (in grado di rendere persistenti solo gli elementi di progetto archiviati fisicamente all'interno della gerarchia di un progetto) o misti (in grado di rendere persistenti i riferimenti o oggetti fisici). L'IDE supporta tutti e tre i tipi di progetti contemporaneamente all'interno di **Esplora soluzioni.**

 Dal punto di vista del trascinamento della selezione, le caratteristiche seguenti devono essere applicate a ogni tipo di progetto all'interno di **Esplora soluzioni:**

- **Progetto basato su riferimento:** Il punto chiave è che il progetto viene trascinato intorno a un riferimento a un elemento nell'archivio. Quando un progetto basato su riferimento funge da origine per un'operazione di spostamento, deve solo rimuovere il riferimento all'elemento dal progetto. L'elemento non deve essere effettivamente eliminato dal disco rigido. Quando un progetto basato su riferimento funge da destinazione per un'operazione di spostamento (o copia), deve aggiungere un riferimento all'elemento di origine originale senza creare una copia privata dell'elemento.

- **Progetto basato su directory:** Dal punto di vista del trascinamento della selezione, il progetto viene trascinato intorno all'elemento fisico anziché a un riferimento. Quando un progetto basato su directory funge da origine per un'operazione di spostamento, dovrebbe finire per eliminare l'elemento fisico dal disco rigido e rimuoverlo dal progetto. Quando un progetto basato su directory funge da destinazione per un'operazione di spostamento (o copia), deve creare una copia dell'elemento di origine nel percorso di destinazione.

- **Progetto a destinazione mista:** Dal punto di vista del trascinamento della selezione, il comportamento di questo tipo di progetto si basa sulla natura dell'elemento trascinato (un riferimento a un elemento nell'archivio o all'elemento stesso). Il comportamento corretto per i riferimenti e gli elementi fisici è descritto in precedenza.

  Se in **Esplora soluzioni**fosse presente un solo tipo di progetto, le operazioni di trascinamento della selezione sarebbero semplici. Poiché ogni sistema di progetto ha la possibilità di definire il proprio comportamento di trascinamento della selezione, alcune linee guida (basate sul comportamento di trascinamento e rilascio di Esplora risorse) devono essere seguite per garantire un'esperienza utente prevedibile:Because each project system has the ability to define its own drag-and-drop behavior, certain guidelines (based on the Windows Explorer drag-and-drop behavior) should be followed to ensure a predictable user experience:

- Un'operazione di trascinamento non modificata in **Esplora soluzioni** (quando non si tiene premuto CTRL o MAIUSC) deve comportare un'operazione di spostamento.

- L'operazione di trascinamento del tasto Maiusc dovrebbe anche comportare un'operazione di spostamento.

- Ctrl-trascina operazione dovrebbe provocare un'operazione di copia.

- I sistemi di progetto misti e basati su riferimenti supportano la nozione di aggiunta di un collegamento (o riferimento) all'elemento di origine. Quando questi progetti sono la destinazione di un'operazione di trascinamento della selezione (quando si tiene premuto **Ctrl e Maiusc),** deve risultare in un riferimento all'elemento aggiunto al progetto

  Non tutte le operazioni di trascinamento della selezione sono ragionevoli tra combinazioni di progetti basati su riferimenti, basati su directory e misti. In particolare, è problematico fingere di consentire un'operazione di spostamento tra un progetto di origine basato su directory e un progetto di destinazione basato su riferimento perché il progetto basato su directory di origine dovrà eliminare l'elemento di origine al completamento dello spostamento. Il progetto basato sul riferimento di destinazione finirebbe quindi con un riferimento a un elemento eliminato.

  È inoltre fuorviante fingere di consentire un'operazione di copia tra questi tipi di progetti perché il progetto basato su riferimento di destinazione non deve creare una copia indipendente dell'elemento di origine. Allo stesso modo, Ctrl : Maiusc trascinando in un progetto di destinazione basato su directory non dovrebbe essere consentito perché un progetto basato su directory non è in grado di mantenere i riferimenti. Nei casi in cui l'operazione di trascinamento della selezione non è supportata, l'IDE deve non consentire il rilascio e mostrare all'utente il cursore di non rilascio (mostrato nella tabella dei puntatori riportata di seguito).

  Per implementare correttamente il comportamento di trascinamento della selezione, il progetto di origine del trascinamento deve comunicare la sua natura (ad esempio, è basato su riferimento o directory?) al progetto di destinazione. Queste informazioni sono indicate dal formato degli Appunti offerto dall'origine. Come origine di un'operazione di trascinamento (o di copia degli Appunti) un progetto deve offrire rispettivamente **CF_VSREFPROJECTITEM**S o **CF_VSSTGPROJECTITEMS,** a seconda che il progetto sia basato su riferimenti o su directory. Entrambi questi formati hanno lo stesso contenuto di dati, che è simile al formato **di Windows CF_HDROP** ad eccezione del fatto che gli elenchi di stringhe, anziché essere nomi di file, sono un elenco di stringhe **Projref** con terminazione**NULL** doppio (come restituito da **IVsSolution::GetProjrefOfItem** o **::GetProjrefOfProject** in base alle esigenze).

  Come destinazione di un'operazione di trascinamento (o incolla degli Appunti), un progetto deve accettare sia **CF_VSREFPROJECTITEMS che** **CF_VSSTGPROJECTITEMS**, anche se la gestione esatta dell'operazione di trascinamento della selezione varia a seconda della natura del progetto di destinazione e del progetto di origine. Il progetto di origine dichiara la sua natura se offre **CF_VSREFPROJECTITEMS** o **CF_VSSTGPROJECTITEMS**. L'obiettivo del rilascio comprende la propria natura e pertanto dispone di informazioni sufficienti per prendere decisioni in merito all'esecuzione di uno spostamento, una copia o un collegamento. L'utente modifica anche l'operazione di trascinamento e rilascio deve essere eseguita premendo il Ctrl, Shift, o entrambi Ctrl e Shift tasti. È importante che la destinazione di rilascio indichi correttamente quale operazione verrà eseguita in anticipo nei metodi **DragEnter** e **DragOver.** **Esplora soluzioni** sa automaticamente se il progetto di origine e il progetto di destinazione sono lo stesso progetto.

  Il trascinamento di elementi di progetto tra istanze di Visual Studio, ad esempio da un'istanza di devenv.exe a un'altra, non è supportato in modo specifico. In **Esplora soluzioni** viene inoltre disabilitato direttamente.

  L'utente deve essere sempre in grado di determinare l'effetto di un'operazione di trascinamento della selezione selezionando un elemento, trascinandolo nella posizione di destinazione e osservando quale dei seguenti puntatori del mouse viene visualizzato prima che l'elemento venga rilasciato:

|Puntatore del mouse|Comando|Descrizione|
|-------------------|-------------|-----------------|
|![Icona di "nessun rilascio" del mouse](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706-01_MouseNoDrop")|Nessuna goccia|L'elemento non può essere rilasciato nella posizione specificata.|
|![Icona "copia" del mouse](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706-02_MouseCopy")|Copiare|L'elemento verrà copiato nel percorso di destinazione.|
|![Icona "spostamento" del mouse](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706-03_MouseMove")|Spostamento|L'elemento verrà spostato nella posizione di destinazione.|
|![Icona "aggiungi riferimento" del mouse](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706-04_MouseAddRef")|Aggiungi riferimento|Un riferimento all'elemento selezionato verrà aggiunto alla posizione di destinazione.|

#### <a name="reference-based-projects"></a>Progetti basati su riferimenti
 Nella tabella seguente sono riepilogate le operazioni di trascinamento della selezione (così come Taglia/Copia/Incolla) che devono essere eseguite in base alla natura dell'elemento di origine e i tasti di modifica premuti per i progetti di destinazione basati su riferimento:

|||Elemento di origine: Riferimento/Collegamento|Elemento di origine: elemento fisico o file system (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Nessun modificatore|Azione|Spostamento|Collegamento|
|Nessun modificatore|Destinazione|Aggiunge un riferimento all'elemento originale|Aggiunge un riferimento all'elemento originale|
|Nessun modificatore|Source (Sorgente)|Elimina il riferimento all'elemento originale|Mantiene l'elemento originale|
|Nessun modificatore|Risultato|**DROPEFFECT_MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nello spazio di archiviazione|**DROPEFFECT_LINK** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|
|Maiusc-Trascinamento|Azione|Spostamento|Nessuna goccia|
|Maiusc-Trascinamento|Destinazione|Aggiunge un riferimento all'elemento originale|Nessuna goccia|
|Maiusc-Trascinamento|Source (Sorgente)|Elimina il riferimento all'elemento originale|Nessuna goccia|
|Maiusc-Trascinamento|Risultato|**DROPEFFECT_MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nello spazio di archiviazione|Nessuna goccia|
|Premere CTRL e trascinare|Azione|Copiare|Nessuna goccia|
|Premere CTRL e trascinare|Destinazione|Aggiunge un riferimento all'elemento originale|Nessuna goccia|
|Premere CTRL e trascinare|Source (Sorgente)|Mantiene il riferimento all'elemento originale|Nessuna goccia|
|Premere CTRL e trascinare|Risultato|**DROPEFFECT_COPY** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nello spazio di archiviazione|Nessuna goccia|
|Ctrl , Maiusc e Trascina|Azione|Collegamento|Collegamento|
|Ctrl , Maiusc e Trascina|Destinazione|Aggiunge un riferimento all'elemento originale|Aggiunge un riferimento all'elemento originale|
|Ctrl , Maiusc e Trascina|Source (Sorgente)|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|
|Ctrl , Maiusc e Trascina|Risultato|**DROPEFFECT_LINK** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|**DROPEFFECT_LINK** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|
|Ctrl , Maiusc e Trascina|Note|Uguale al comportamento di trascinamento della selezione per i collegamenti in Esplora risorse.||
|Taglia/Incolla|Azione|Spostamento|Collegamento|
|Taglia/Incolla|Destinazione|Aggiunge un riferimento all'elemento originale|Aggiunge un riferimento all'elemento originale|
|Taglia/Incolla|Source (Sorgente)|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|
|Taglia/Incolla|Risultato|L'elemento rimane nella posizione originale nello spazio di archiviazione|L'elemento rimane nella posizione originale nello spazio di archiviazione|
|Copia/Incolla|Azione|Copiare|Collegamento|
|Copia/Incolla|Source (Sorgente)|Aggiunge un riferimento all'elemento originale|Aggiunge un riferimento all'elemento originale|
|Copia/Incolla|Risultato|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|
|Copia/Incolla|Azione|L'elemento rimane nella posizione originale nello spazio di archiviazione|L'elemento rimane nella posizione originale nello spazio di archiviazione|

#### <a name="directory-based-projects"></a>Progetti basati su directory
 Nella tabella seguente sono riepilogate le operazioni di trascinamento della selezione (così come taglia/copia/incolla) che devono essere eseguite in base alla natura dell'elemento di origine e i tasti di modifica premuti per i progetti di destinazione basati su directory:

|||Elemento di origine: Riferimento/Collegamento|Elemento di origine: elemento fisico o file system (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Nessun modificatore|Azione|Spostamento|Spostamento|
|Nessun modificatore|Destinazione|Copia l'elemento nella posizione di destinazione|Copia l'elemento nella posizione di destinazione|
|Nessun modificatore|Source (Sorgente)|Elimina il riferimento all'elemento originale|Elimina il riferimento all'elemento originale|
|Nessun modificatore|Risultato|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nell'archivio|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nell'archivio|
|Maiusc-Trascinamento|Azione|Spostamento|Spostamento|
|Maiusc-Trascinamento|Destinazione|Copia l'elemento nella posizione di destinazione|Copia l'elemento nella posizione di destinazione|
|Maiusc-Trascinamento|Source (Sorgente)|Elimina il riferimento all'elemento originale|Elimina l'elemento dalla posizione originale|
|Maiusc-Trascinamento|Risultato|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nell'archivio|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nell'archivio|
|Premere CTRL e trascinare|Azione|Copiare|Copiare|
|Premere CTRL e trascinare|Destinazione|Copia l'elemento nella posizione di destinazione|Copia l'elemento nella posizione di destinazione|
|Premere CTRL e trascinare|Source (Sorgente)|Mantiene il riferimento all'elemento originale|Mantiene il riferimento all'elemento originale|
|Premere CTRL e trascinare|Risultato|**DROPEFFECT_ COPY** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|**DROPEFFECT_ COPY** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|
|Ctrl , Maiusc e Trascina||Nessuna goccia|Nessuna goccia|
|Taglia/Incolla|Azione|Spostamento|Spostamento|
|Taglia/Incolla|Destinazione|Copia l'elemento nella posizione di destinazione|Copia l'elemento nella posizione di destinazione|
|Taglia/Incolla|Source (Sorgente)|Elimina il riferimento all'elemento originale|Elimina l'elemento dalla posizione originale|
|Taglia/Incolla|Risultato|L'elemento rimane nella posizione originale nello spazio di archiviazione|L'elemento viene eliminato dalla posizione originale nello spazio di archiviazione|
|Copia/Incolla|Azione|Copiare|Copiare|
|Copia/Incolla|Destinazione|Aggiunge un riferimento all'elemento originale|Copia l'elemento nella posizione di destinazione|
|Copia/Incolla|Source (Sorgente)|Mantiene l'elemento originale|Mantiene l'elemento originale|
|Copia/Incolla|Risultato|L'elemento rimane nella posizione originale nello spazio di archiviazione|L'elemento rimane nella posizione originale nello spazio di archiviazione|

#### <a name="mixed-target-projects"></a>Progetti a destinazione mista
 Nella tabella seguente sono riepilogate le operazioni di trascinamento della selezione (così come Taglia/Copia/Incolla) che devono essere eseguite in base alla natura dell'elemento di origine e i tasti di modifica premuti per i progetti di destinazione mista:

|||Elemento di origine: Riferimento/Collegamento|Elemento di origine: elemento fisico o file system (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Nessun modificatore|Azione|Spostamento|Spostamento|
|Nessun modificatore|Destinazione|Aggiunge un riferimento all'elemento originale|Copia l'elemento nella posizione di destinazione|
|Nessun modificatore|Source (Sorgente)|Elimina il riferimento all'elemento originale|Elimina il riferimento all'elemento originale|
|Nessun modificatore|Risultato|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nell'archivio|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento viene eliminato dalla posizione originale nel magazzino|
|Maiusc-Trascinamento|Azione|Spostamento|Spostamento|
|Maiusc-Trascinamento|Destinazione|Aggiunge un riferimento all'elemento originale|Copia l'elemento nella posizione di destinazione|
|Maiusc-Trascinamento|Source (Sorgente)|Elimina il riferimento all'elemento originale|Elimina l'elemento dalla posizione originale|
|Maiusc-Trascinamento|Risultato|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nell'archivio|**DROPEFFECT_ MOVE** viene restituito come azione da **::Drop** e l'elemento viene eliminato dalla posizione originale nel magazzino|
|Premere CTRL e trascinare|Azione|Copiare|Copiare|
|Premere CTRL e trascinare|Destinazione|Aggiunge un riferimento all'elemento originale|Copia l'elemento nella posizione di destinazione|
|Premere CTRL e trascinare|Source (Sorgente)|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|
|Premere CTRL e trascinare|Risultato|**DROPEFFECT_ COPY** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|**DROPEFFECT_ COPY** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale in memoria|
|Ctrl , Maiusc e Trascina|Azione|Collegamento|Collegamento|
|Ctrl , Maiusc e Trascina|Destinazione|Aggiunge un riferimento all'elemento originale|Aggiunge un riferimento all'elemento di origine originale|
|Ctrl , Maiusc e Trascina|Source (Sorgente)|Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale|
|Ctrl , Maiusc e Trascina|Risultato|**DROPEFFECT_ LINK** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nello spazio di archiviazione|**DROPEFFECT_ LINK** viene restituito come azione da **::Drop** e l'elemento rimane nella posizione originale nello spazio di archiviazione|
|Taglia/Incolla|Azione|Spostamento|Spostamento|
|Taglia/Incolla|Destinazione|Copia l'elemento nella posizione di destinazione|Copia l'elemento nella posizione di destinazione|
|Taglia/Incolla|Source (Sorgente)|Elimina il riferimento all'elemento originale|Elimina l'elemento dalla posizione originale|
|Taglia/Incolla|Risultato|L'elemento rimane nella posizione originale nello spazio di archiviazione|L'elemento viene eliminato dalla posizione originale nello spazio di archiviazione|
|Copia/Incolla|Azione|Copiare|Copiare|
|Copia/Incolla|Destinazione|Aggiunge un riferimento all'elemento originale|Copia l'elemento nella posizione di destinazione|
|Copia/Incolla|Source (Sorgente)|Mantiene l'elemento originale|Mantiene l'elemento originale|
|Copia/Incolla|Risultato|L'elemento rimane nella posizione originale nello spazio di archiviazione|L'elemento rimane nella posizione originale nello spazio di archiviazione|

 Questi dettagli devono essere presi in considerazione quando si implementa il trascinamento in **Esplora soluzioni**:

- Progettare per più scenari di selezione.

- I nomi di file (percorso completo) devono essere univoci nel progetto di destinazione o l'eliminazione non deve essere consentita.

- I nomi delle cartelle devono essere univoci (senza distinzione tra maiuscole e minuscole) al livello in cui vengono eliminati.

- Esistono differenze di comportamento tra i file aperti o chiusi al momento del trascinamento (non menzionati negli scenari precedenti).

- I file di primo livello si comportano in modo leggermente diverso rispetto ai file nelle cartelle.

  Un altro problema da tenere presente è come gestire le operazioni di spostamento su elementi che dispongono di finestre di progettazione o editor aperti. Il comportamento previsto è il seguente (si applica a tutti i tipi di progetto):The expected behavior is as follows (this applies to all project types):

1. Se l'editor o la finestra di progettazione aperta non contiene modifiche non salvate, la finestra dell'editor/progettazione deve essere chiusa in modo invisibile all'utente.

2. Se l'editor o la finestra di progettazione aperta contiene modifiche non salvate, l'origine del trascinamento deve attendere che si verifichi il rilascio e quindi chiedere all'utente di salvare le modifiche di cui non è stato eseguito il commit nei documenti aperti prima di chiudere la finestra con un prompt simile al seguente:

   ```
   ==========================================================
        One or more open documents have unsaved changes.
   Do you want to save uncommitted changes before proceeding?
                     [Yes]  [No]  [Cancel]
   ==========================================================
   ```

   Ciò offre all'utente la possibilità di salvare i lavori in corso prima che il target faccia le proprie copie. Un nuovo metodo **IVsHierarchyDropDataSource2::OnBeforeDropNotify** è stato aggiunto per abilitare questa gestione.

   La destinazione copierà quindi lo stato dell'elemento così come si trova nell'archivio (escluse le modifiche non salvate nell'editor se l'utente ha scelto **No**). Dopo che la destinazione ha completato la copia (in **IVsHierarchyDropDataSource::Drop**), all'origine viene data la possibilità di completare la parte di eliminazione dell'operazione di spostamento (in **IVsHierarchyDropDataSource::OnDropNotify**).

   Tutti gli editor con modifiche non salvate devono essere lasciati aperti. Per i documenti con modifiche non salvate, ciò significa che la parte di copia dell'operazione di spostamento verrà eseguita ma la parte di eliminazione verrà interrotta. In uno scenario di selezione multipla quando l'utente sceglie **No**, i documenti con modifiche non salvate non devono essere chiusi o rimossi, ma quelli senza modifiche non salvate devono essere chiusi e rimossi.
