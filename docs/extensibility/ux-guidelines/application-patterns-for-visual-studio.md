---
title: I modelli di applicazione per Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd12d18c0230af4307d0dec8fe37868801226472
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432576"
---
# <a name="application-patterns-for-visual-studio"></a>Modelli di applicazione per Visual Studio
## <a name="BKMK_WindowInteractions"></a> Interazioni di finestra

### <a name="overview"></a>Panoramica
I due tipi di finestra principale utilizzati in Visual Studio sono editor di documenti e finestre degli strumenti. Rare, ma possibili, sono finestre di dialogo non modale di grandi dimensioni. Anche se questi sono tutti non modali nella shell, i modelli sono fondamentalmente diversi. Questa sezione illustra la differenza tra le finestre dei documenti, finestre degli strumenti e finestre di dialogo non modale. Vengono analizzati i modelli di finestra di dialogo modale [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Confronto dei modelli di utilizzo di finestra
**Finestre dei documenti** sono quasi sempre visualizzato anche all'interno del documento. In questo modo, una "fase center" editor di documenti per disporre di finestre degli strumenti aggiuntivi intorno.

Oggetto **finestra degli strumenti** viene spesso visualizzato come una finestra separata di piccole dimensioni compressa contro il bordo dell'IDE. Ciò può essere visibile, nascosto o nascosto automaticamente. Tuttavia, talvolta finestre degli strumenti vengono presentate all'interno del documento insomma, deselezionando il **finestra/ancoraggio** proprietà nella finestra. Il risultato è un'area maggiore, ma anche un comune decisioni di progettazione: quando si tenta di integrare in Visual Studio, è necessario decidere se la funzionalità deve essere visualizzata una finestra degli strumenti o una finestra del documento.

**Le finestre di dialogo non modale** sono sconsigliato in Visual Studio. Le finestre di dialogo non modale più sono, per definizione, finestre degli strumenti mobili e devono essere implementati in questo modo. Le finestre di dialogo non modali sono consentiti nei casi in cui le dimensioni di una finestra normale degli strumenti ancorata al lato della shell potrebbero essere troppo restrittivo. Sono consentiti anche nei casi in cui l'utente sarebbe probabilmente spostare la finestra di dialogo a un monitoraggio secondario.

Considerare con attenzione sul tipo contenitore è necessario. Considerazioni sul modello di utilizzo comuni per la progettazione dell'interfaccia utente sono nella tabella seguente.

||Finestra del documento|Finestra degli strumenti|Finestra di dialogo non modale|
|-|---------------------|-----------------|---------------------|
| **posizione** | Sempre posizionato all'interno del documento bene e non ancorare intorno ai bordi dell'IDE. È possibile essere "pull" in modo da spostarla separatamente dalla shell di principale. | In genere ancorate intorno ai bordi dell'IDE, ma può essere personalizzato per essere a virgola mobile, nascosta automaticamente (unpinned) o ancorato anche all'interno del documento.|Finestra mobile grande separato dall'IDE. |
| **Commit modello** | *Commit ritardato*<br /><br /> Per salvare i dati in un documento, l'utente deve inviare il **File &gt; salvare**, **Salva con nome**, oppure **Salva tutto** comando. Una finestra del documento è presente il concetto dei dati all'interno di esso venga "scritto" quindi eseguito il commit a una delle Salva i comandi. Quando si chiude una finestra del documento, tutti i contenuti vengono salvati su disco o persi. | *Commit immediato*<br /><br /> Non vi è alcun Salva modello. Per finestre di strumento di controllo che assistono nella modifica di un file, il file deve essere aperto nell'editor attivo o nella finestra di progettazione e l'editor o finestra di progettazione è proprietario di salvataggio. | *Commit ritardato o controllo immediato*<br /><br /> In genere, una finestra di dialogo non modale grandi dimensioni richiede un'azione per eseguire il commit delle modifiche e consente un'operazione di "Annullamento", che il rollback di tutte le modifiche apportate all'interno della sessione di finestra di dialogo.  Questo consente di distinguere una finestra di dialogo non modale da una finestra degli strumenti in finestre degli strumenti dispongono sempre di un modello di commit immediato. |
| **Visibilità** | *Aprire/creare (file) e Close*<br /><br /> Aprire una finestra del documento viene eseguita tramite l'apertura di un documento esistente o usare un modello per creare un nuovo documento. È presente alcun "Apri \<specifica dell'editor >" comando. | *Nascondere e mostrare*<br /><br /> Finestre degli strumenti a istanza singola possono essere nascoste o visualizzate. Contenuto e gli stati nella finestra degli strumenti persistono se nella visualizzazione o nascosto. Finestre degli strumenti a istanza multipla possono essere chiusa nonché nascoste. Quando viene chiusa una finestra degli strumenti a istanza multipla, viene eliminato il contenuto e lo stato all'interno della finestra degli strumenti. | *Avviato da un comando*<br /><br /> Le finestre di dialogo vengono avviate da un comando basato su attività. |
| **Istanze** | *Multi-instance*<br /><br /> Numerosi editor possono essere aperti al momento stesso e modifica dei file diversi, anche se alcuni editor offre anche lo stesso file sia aperto in più di un editor (usando il **finestra &gt; nuova finestra** comando).<br /><br /> Un singolo editor stia modificando uno o più file contemporaneamente (Progettazione progetti). | *Singolo o più istanze*<br /><br /> Contenuto cambia per riflettere contesto (ad esempio, il Visualizzatore di proprietà) o eseguire il push dello stato attivo/contesto altre finestre (elenco attività, Esplora soluzioni).<br /><br /> Finestre degli strumenti a istanza singola e a istanza multipla devono essere associate alla finestra del documento attivo, a meno che non esiste un motivo a. | *A istanza singola* |
| **Esempi** | **Gli editor di testo**, ad esempio l'editor di codice<br /><br /> **Aree di progettazione**, ad esempio una finestra di progettazione di form o un'area di modellazione<br /><br /> **Layout simile alle finestre di dialogo di controllo**, ad esempio la finestra Progettazione manifesto | Il **Esplora soluzioni** fornisce una soluzione e progetti contenuti all'interno della soluzione<br /><br /> Il **Esplora Server** offre una visualizzazione gerarchica di connessioni server e dei dati che l'utente sceglie di aprire la finestra. Apertura di un oggetto dalla gerarchia di database, ad esempio una query, si apre una finestra del documento e consente all'utente di modificare la query.<br /><br /> Il **Visualizzatore proprietà** vengono visualizzate le proprietà per l'oggetto selezionato in una finestra del documento o un'altra finestra degli strumenti. Le proprietà vengono presentate in una visualizzazione griglia gerarchici o nei controlli di finestra di dialogo complessi e consentono all'utente di impostare i valori per tali proprietà. | |

## <a name="BKMK_ToolWindows"></a> Finestre degli strumenti

### <a name="overview"></a>Panoramica
Finestre degli strumenti supportano le attività dell'utente che si verifica nelle finestre dei documenti. Possono essere utilizzati per visualizzare una gerarchia che rappresenta un oggetto radice fondamentali di Visual Studio offre e sono modificabili.

Quando si considera una nuova finestra degli strumenti nell'IDE, gli autori devono:

- Usare attività appropriata per la finestre degli strumenti esistenti e non crearne uno nuovo con funzionalità simili. Nuove finestre degli strumenti devono essere create solo se queste connessioni offrono un "strumento" significativamente diverso o una funzionalità che non può essere integrata in una finestra simile, o convertendo una finestra esistente in un hub di trasformazione tramite pivot.

- Usare una barra dei comandi standard, se necessario, nella parte superiore della finestra degli strumenti.

- Essere coerenti con i modelli già presenti in altre finestre degli strumenti per lo spostamento di presentazione e della tastiera di controllo.

- Essere coerenti con la presentazione di controllo in altre finestre degli strumenti.

- Creare finestre degli strumenti specifici del documento visibili automaticamente quando possibile, in modo che vengano visualizzati solo quando viene attivato il documento padre.

- Verificare che il contenuto della finestra è esplorabile da tastiera (tasti di direzione supporto).

#### <a name="tool-window-states"></a>Stati della finestra degli strumenti
Finestre degli strumenti di Visual Studio hanno diversi stati, alcuni dei quali sono utente attivato (ad esempio, la funzionalità Nascondi automaticamente). Altri Stati, come visibili automaticamente, consenta le finestre degli strumenti vengono visualizzati nel contesto corretto e nascondere quando non sono necessarie. Esistono cinque stati della finestra degli strumenti in totale.

- **Ancorato/bloccato** finestre degli strumenti possono essere collegate a uno qualsiasi dei quattro lati dell'area del documento. L'icona della puntina da disegno viene visualizzato nella barra del titolo di finestra degli strumenti. La finestra degli strumenti può essere ancorata orizzontalmente o verticalmente lungo il bordo della shell e altre finestre degli strumenti e può anche essere collegata a schede.

- **Nascosta automaticamente** finestre degli strumenti vengono rimossi. Non è più visualizzata, lasciando una scheda (con il nome della finestra degli strumenti e la relativa icona) sul bordo dell'area del documento può scorrere la finestra. La finestra degli strumenti verrà visualizzato quando l'utente passa sopra la scheda.

- **Visibili automaticamente** finestre degli strumenti vengono visualizzati automaticamente quando un altro componente dell'interfaccia utente, ad esempio un editor, viene avviato o ottiene lo stato attivo.

- **Mobile** finestre degli strumenti al passaggio del mouse all'esterno dell'IDE. Ciò è utile per le configurazioni con più monitor.

- **Documento a schede** finestre degli strumenti possono essere ancorate anche all'interno del documento. Ciò è utile per le finestre dello strumento di grandi dimensioni, ad esempio il Visualizzatore oggetti, che richiedono più spazio rispetto ai bordi della cornice di ancoraggio.

![Strumento gli stati della finestra in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 01_ToolWindowStates")<br />Stati della finestra degli strumenti in Visual Studio

#### <a name="single-instance-and-multi-instance"></a>A istanza singola e a istanza multipla
Finestre degli strumenti sono a istanza singola o multi-istanza. Alcune finestre degli strumenti a istanza singola potrebbero essere associate alla finestra di documento attivo, mentre finestre degli strumenti a istanza multipla forse no. Finestre degli strumenti a istanza multipla rispondono per il **finestra &gt; nuova finestra** comando creando una nuova istanza della finestra. L'immagine seguente illustra una finestra degli strumenti se si abilita il comando nuova finestra quando è attiva un'istanza della finestra:

![Comando "Nuova finestra" quando un'istanza della finestra per abilitare la finestra degli strumenti è attiva](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")<br />Per abilitare il comando "Nuova finestra" quando un'istanza della finestra è attiva la finestra degli strumenti

Finestre degli strumenti a istanza singola possono essere nascoste o visualizzate, mentre finestre degli strumenti a istanza multipla possono essere chiusa nonché nascoste. Tutte le finestre degli strumenti possono essere ancorate, collegata a schede, mobili o impostato come una finestra figlia di interfaccia a documenti multipli (MDI) (simile a una finestra del documento). Tutte le finestre degli strumenti devono rispondere ai comandi del menu finestra Gestione finestra appropriato:

![Comandi della finestra Gestione nel menu finestra di Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 03_WindowManagementControls")<br />Comandi della finestra Gestione nel menu finestra di Visual Studio

#### <a name="document-specific-tool-windows"></a>Finestre degli strumenti specifici del documento
Alcune finestre degli strumenti sono progettati per variare in base a un determinato tipo di documento. Queste finestre vengono aggiornati continuamente per riflettere funzionalità applicabili alla finestra del documento attivo nell'IDE.

Sono esempi di finestre degli strumenti, il cui contenuto viene modificato in modo da riflettere l'editor selezionato della casella degli strumenti e la struttura del documento. Tali finestre mostrano una filigrana quando un editor ha lo stato attivo che non offre alcun contesto alla finestra.

#### <a name="navigable-list-tool-windows"></a>Finestre degli strumenti elenco esplorabile
Alcune finestre degli strumenti Visualizza un elenco di elementi navigabili che l'utente può interagire con. In questo tipo di finestra, si deve essere sempre commenti e suggerimenti per l'elemento corrente nell'elenco, anche se la finestra è inattiva. L'elenco deve rispondere per il **GoToNextLocation** e **GoToPrevLocation** comandi anche modificando l'elemento attualmente selezionato nella finestra

Esplora soluzioni e la finestra Risultati ricerca sono esempi di finestre degli strumenti elenco esplorabile.

### <a name="tool-window-types"></a>Tipi di finestre degli strumenti

#### <a name="common-tool-windows-and-their-functions"></a>Finestre degli strumenti comuni e le relative funzioni

**Finestre degli strumenti gerarchici**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Esplora soluzioni | Un albero gerarchica che visualizza un elenco di documenti inclusi in progetti, file esterni e gli elementi della soluzione. La visualizzazione degli elementi all'interno dei progetti è definita dal pacchetto a cui appartiene il tipo di progetto (ad esempio, i tipi in base al riferimento, basata su directory o in modalità mista). |
| Visualizzazione classi | Un albero gerarchico delle classi e i vari elementi nel working set di documenti, indipendenti dei file stessi. |
| Esplora server | Un albero gerarchico che consente di visualizzare tutte le connessioni server e dei dati nella soluzione. |
| Struttura documento | La struttura gerarchica del documento attivo. |

**Finestre degli strumenti della griglia**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Proprietà | Una griglia che visualizza un elenco delle proprietà per l'oggetto selezionato, insieme ai controlli di selezione valore per modificare tali proprietà. |
| Elenco attività | Una griglia che consente all'utente di creare, modificare o eliminare attività e i commenti. |

**Finestre degli strumenti del contenuto**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Help | Una finestra che consente agli utenti l'accesso ai diversi metodi di richiesta di supporto, dal "Ricerca per categorie?" video ai forum MSDN. |
| Guida dinamica | Una finestra degli strumenti che consente di visualizzare i collegamenti per gli argomenti applicabili alla selezione corrente. |
| Visualizzatore oggetti | Una pagina con frame due colonne con un elenco di componenti gerarchico di oggetti nel riquadro sinistro e dell'oggetto delle proprietà e metodi nella colonna destra. |

**Finestre degli strumenti finestra di dialogo**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Find | Una finestra di dialogo che consente all'utente di ricerca o Trova e Sostituisci nei file diversi all'interno della soluzione. |
| Ricerca avanzata | Una finestra di dialogo che consente all'utente di ricerca o Trova e Sostituisci nei file diversi all'interno della soluzione. |

**Altre finestre degli strumenti**

::: moniker range="vs-2017"

| Finestra degli strumenti | Funzione |
| --- | --- |
| Casella degli strumenti | La finestra degli strumenti utilizzata per archiviare gli elementi che verranno eliminati su superfici di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione. |
| Pagina iniziale | Portale dell'utente a Visual Studio, con accesso ai feed di notizie per gli sviluppatori, la Guida di Visual Studio e progetti recenti. Gli utenti possono anche creare pagine iniziali personalizzate copiando il file StartPage. XAML dal "Common7\IDE\StartPages\" directory dei file di programma Visual Studio nella cartella StartPages in Visual Studio documenta directory e quindi una modifica di XAML a mano o aprirlo in Visual Studio o un altro editor di codice. |

::: moniker-end

::: moniker range=">=vs-2019"

| Finestra degli strumenti | Funzione |
| --- | --- |
| Casella degli strumenti | La finestra degli strumenti utilizzata per archiviare gli elementi che verranno eliminati su superfici di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione. |

::: moniker-end

**Finestre degli strumenti del debugger**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Auto ||
| Controllo immediato ||
| Output | La finestra di output può essere usata ogni volta che si dispone di eventi testuali o lo stato per dichiarare. |
| Memoria ||
| Punti di interruzione ||
| In esecuzione ||
| Documenti ||
| Stack di chiamate ||
| Variabili locali ||
| Espressioni di controllo ||
| Disassembly ||
| Registri ||
| Thread ||

## <a name="BKMK_DocumentEditorConventions"></a> Convenzioni dell'editor di documento

### <a name="document-interactions"></a>Interazioni di documento
"Documento well" è il più grande spazio all'interno dell'IDE e in cui l'utente in genere si è concentrata l'attenzione per poter completare le attività, assistite da finestre degli strumenti supplementare. Gli editor di documento rappresentano l'unità fondamentale di lavoro che l'utente apre e salvati all'interno di Visual Studio. Hanno mantenuto un forte senso di selezione a Esplora soluzioni o altre finestre gerarchia attiva. L'utente deve essere in grado di scegliere una di queste finestre di gerarchia e sapere in cui è contenuto il documento e la relativa relazione per la soluzione, il progetto o un altro oggetto radice fornito da un pacchetto di Visual Studio.

Modifica di documenti richiede un'esperienza utente coerente. Per consentire all'utente di concentrarsi sull'attività in questione anziché sulla gestione delle finestre e ricerca dei comandi, selezionare una strategia di visualizzazione documento più adatto alle attività dell'utente per la modifica di tale tipo di documento.

#### <a name="common-interactions-for-the-document-well"></a>Interazioni più comuni per l'area dei documenti

- Gestire un modello di interazione coerenti in più comuni **nuovo File** e **Apri File** esperienze.

- Aggiornare le funzionalità correlate nei menu e finestre correlate quando si apre la finestra del documento.

- I comandi di menu sono integrati in modo appropriato nel menu comuni, ad esempio **Edit**, **formato**, e **visualizzazione** i menu. Se sono disponibili una notevole quantità di comandi specializzati, quindi è possibile creare un nuovo menu. Questo nuovo menu deve essere visibile solo quando il documento dispone dello stato attivo.

- Una barra degli strumenti incorporata può essere posizionato nella parte superiore dell'editor. Ciò è preferibile alla presenza di una barra degli strumenti separata che viene visualizzato all'esterno dell'editor.

- Mantenere sempre una selezione di Esplora soluzioni o attivo simile finestra gerarchia.

- Fare doppio clic su un documento in Esplora soluzioni dovrebbe eseguire la stessa azione **aperto**.

- Se più di un editor può essere utilizzato in un tipo di documento, l'utente deve essere in grado di eseguire l'override o reimpostare l'azione predefinita di un tipo di documento specificato usando il **Apri con** finestra di dialogo facendo clic sul file e selezionando **Open Con** dal menu di scelta rapida.

- Non creare anche una procedura guidata in un documento.

### <a name="user-expectations-for-specific-document-types"></a>Aspettative dell'utente per i tipi di documento specifico
Esistono diversi tipi di base differenti degli editor di documento e ognuna ha un set di interazioni che siano coerenti con altri utenti dello stesso tipo.

- **Editor di testo:** editor di codice, i file di log

- **Nell'area di progettazione:** WPF, Progettazione Windows Form

- **Editor finestra di dialogo-style:** Progettazione manifesto, proprietà del progetto

- **Progettazione modelli:** Progettazione flussi di lavoro, codemap, diagramma dell'architettura, progressione

Esistono anche diversi tipi non di editor che usano anche il documento. Anche se essi non modificare i documenti autonomamente, è necessario eseguire interazioni standard per le finestre dei documenti.

- **Report:** Report di IntelliTrace, report di Hyper-V, report del profiler

- **Dashboard:** Hub diagnostica

#### <a name="text-based-editors"></a>Editor basati su testo

- Il documento viene utilizzata nel modello di scheda di anteprima, consentendo la visualizzazione in anteprima il documento senza aprirlo.

- La struttura del documento possa essere rappresentata all'interno di una finestra degli strumenti complementare, ad esempio una struttura documento.

- IntelliSense (se appropriato) si comporteranno in modo coerente con altri editor di codice.

- I popup o l'interfaccia utente per l'accesso facilitato seguono gli stili e modelli simili per interfaccia utente simile esistente, come CodeLens.

- I messaggi riguardanti lo stato del documento verranno presentati in un controllo nella barra nella parte superiore del documento o nella barra di stato.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere e colori usando un **strumenti > Opzioni** pagina della pagina tipi di carattere e colori condivisa o un determinato nell'editor.

#### <a name="design-surfaces"></a>Aree di progettazione

- Una finestra di progettazione vuota deve avere una filigrana per l'area che indica come iniziare a usare.

- Cambio visualizzazione meccanismi seguirà i modelli esistenti, ad esempio fare doppio clic per aprire un editor di codice o schede all'interno della finestra di documento che consente l'interazione con entrambi i riquadri.

- Aggiunta di elementi nell'area di progettazione deve essere eseguita tramite la casella degli strumenti, a meno che non è necessaria una finestra degli strumenti molto specifici.

- Gli elementi nell'area di seguirà un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono i comandi non comuni, solo i comandi specifici del documento, ad esempio **salvare**.

#### <a name="dialog-style-editors"></a>Editor di stile di finestra di dialogo

- Il layout dei controlli deve seguire convenzioni di layout di finestra di dialogo normale.

- Schede all'interno dell'editor non devono corrispondere l'aspetto delle schede del documento, deve corrispondere a uno dei due stili consentiti scheda interni.

- Gli utenti devono essere in grado di interagire con i controlli tramite tastiera di sola lettura. tramite l'editor di attivazione e la tabulazione tra i controlli o usando i tasti di scelta standard.

- La finestra di progettazione deve utilizzare Salva con nome modello comune. Non salva complessivo o pulsanti di commit devono essere posizionati sulla superficie, anche se altri pulsanti potrebbero essere appropriato.

#### <a name="model-designers"></a>Progettisti di modelli

- Una finestra di progettazione vuota deve avere una filigrana per l'area che indica come iniziare a usare.

- Aggiunta di elementi nell'area di progettazione deve essere eseguita tramite la casella degli strumenti.

- Gli elementi nell'area di seguirà un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono i comandi non comuni, solo i comandi specifici del documento, ad esempio **salvare**.

- Una legenda può vengono visualizzati nell'area di indicativi o una filigrana.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere o colori usando un **strumenti > Opzioni** pagina della pagina tipi di carattere e colori condivisa o un determinato nell'editor.

#### <a name="reports"></a>Report

- I report vengono in genere solo le informazioni e non fanno parte del modello di salvataggio. Tuttavia, possono comprendere l'interazione, ad esempio collegamenti ad altre informazioni rilevanti e le sezioni che espandere e comprimere.

- La maggior parte dei comandi nell'area di devono essere collegamenti ipertestuali, pulsanti non.

- Layout deve includere un'intestazione e seguire le linee guida layout di report standard.

#### <a name="dashboards"></a>Dashboard

- I dashboard non sono un modello di interazione autonomamente, ma servono come mezzo per offrire un'ampia gamma di altri strumenti.

- Non partecipano nel modello di salvataggio.

- Gli utenti devono essere in grado di interagire con i controlli tramite tastiera, solo l'editor di attivazione e la tabulazione tra i controlli oppure usando i tasti di scelta standard.

## <a name="BKMK_Dialogs"></a> Finestre di dialogo

### <a name="introduction"></a>Introduzione
Finestre di dialogo in Visual Studio in genere deve supportare una unità discreta di lavoro dell'utente e quindi essere chiuse.

Se si è appurato che è necessario una finestra di dialogo, sono disponibili tre opzioni, in ordine di preferenza:

1. Integrare le funzionalità in una delle finestre di dialogo condivisi in Visual Studio.

2. Creare il proprio finestra di dialogo utilizzando un criterio è stato trovato in una finestra di dialogo simile esistente.

3. Creare una nuova finestra di dialogo, l'interazione seguente e linee guida di layout.

In questa sezione viene descritto come scegliere il modello di finestra di dialogo corretto all'interno dei flussi di lavoro di Visual Studio e le convenzioni comuni per la progettazione della finestra.

### <a name="themes"></a>Themes
Finestre di dialogo in Visual Studio seguire uno dei due stili di base:

#### <a name="standard-unthemed"></a>Standard (unthemed)
La maggior parte delle finestre di dialogo sono finestre di dialogo utilità standard e devono essere unthemed. Non non controlli comuni di reimpostare come modelli o provare a creare pulsanti "moderni" stilizzati o controlli. I controlli e l'aspetto di chrome seguire [linee guida per l'interazione Desktop di Windows standard per le finestre di dialogo](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Con tema
Le finestre di dialogo di specializzazione "firma" potrebbe essere a tema. Le finestre di dialogo con tema hanno un aspetto distinto, che presenta anche alcuni modelli di interazione speciali associati allo stile. Tema la finestra di dialogo solo se soddisfa questi requisiti:

- La finestra di dialogo è un'esperienza comune che verrà visualizzata e usata spesso o dal numero di utenti (ad esempio, il **nuovo progetto** finestra di dialogo.

- La finestra di dialogo contiene gli elementi del marchio del prodotto notificate all'utente (ad esempio, il **impostazioni Account** finestra di dialogo).

- La finestra di dialogo viene visualizzato come parte integrante di un flusso più grande che includa altre finestre di dialogo con tema (ad esempio, il **Aggiungi servizio connesso** finestra di dialogo).

- La finestra di dialogo è una parte importante di un'esperienza che riveste un ruolo strategico nell'innalzamento di livello o differenziare una versione del prodotto.

Quando si crea una finestra di dialogo con tema, utilizzare i colori di ambiente appropriate e seguire il layout corretto e modelli di interazione. (Vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Progettazione di finestra di dialogo
Le finestre di dialogo ben progettate considerare gli elementi seguenti:

- L'attività definita dall'utente è supportato

- Stile del testo della finestra, linguaggio e terminologia

- Scelta del controllo e le convenzioni dell'interfaccia utente

- Allineamento specifica e il controllo di layout visivo

- Accesso da tastiera

#### <a name="content-organization"></a>Organizzazione del contenuto
Prendere in considerazione le differenze tra questi tipi di base delle finestre di dialogo:

- [Le finestre di dialogo semplice](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentare i controlli in una singola finestra modale. La presentazione può includere le variazioni del pattern di controllo complessi, tra cui un controllo di selezione del campo o una barra delle icone.

- [A più livelli di finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) consentono di sfruttare al meglio l'area dello schermo quando un singolo elemento di interfaccia utente è costituito da più gruppi di controlli. Raggruppamenti della finestra di dialogo "stratificati" tramite controlli struttura a schede, i controlli elenco di navigazione o pulsanti in modo che l'utente può scegliere quali raggruppamento per visualizzare in qualsiasi momento.

- [Procedure guidate](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sono utili per indirizzare l'utente attraverso una sequenza logica di passo per il completamento di un'attività. Una serie di opzioni sono disponibili nei pannelli sequenziali, talvolta introdurre diversi flussi di lavoro ("branch") dipende da una selezione effettuata nel pannello precedente.

#### <a name="BKMK_SimpleDialogs"></a> Finestre di dialogo semplice
Una semplice finestra di dialogo è una presentazione dei controlli in una singola finestra modale. In questa presentazione potrebbe includere le variazioni del pattern di controllo complessi, ad esempio un controllo di selezione del campo. Per le finestre di dialogo semplice seguire il layout generale standard, nonché qualsiasi layout specifici necessari per i raggruppamenti di controllo complessa.

![> Crea chiave con nome sicuro è un esempio di una finestra di dialogo semplice in Visual Studio. ](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 01_CreateStrongNameKey")<br />Crea chiave con nome sicuro è un esempio di una finestra di dialogo semplice in Visual Studio.

#### <a name="BKMK_LayeredDialogs"></a> Finestre di dialogo a più livelli
Le finestre di dialogo a più livelli include schede, i dashboard e alberi incorporati. Vengono utilizzati per ottimizzare immobiliare quando sono presenti più gruppi di controlli disponibili in una singola parte di interfaccia utente. I raggruppamenti sono disposti in modo che l'utente può scegliere quali raggruppamento per visualizzare in qualsiasi momento.

Nel caso più semplice, il meccanismo per il passaggio tra i raggruppamenti è un controllo struttura a schede. Sono disponibili diverse alternative. Vedere l'assegnazione di priorità sulle e dei livelli per informazioni su come scegliere lo stile più appropriato.

Il **degli strumenti &gt; opzioni** finestra di dialogo è riportato un esempio di una finestra di dialogo a più livelli usando una struttura ad albero incorporata:

![Strumenti > Opzioni è riportato un esempio di una finestra di dialogo a più livelli in Visual Studio. ](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 02_ToolsOptions")<br />Strumenti > Opzioni è riportato un esempio di una finestra di dialogo a più livelli in Visual Studio.

#### <a name="BKMK_Wizards"></a> Procedure guidate
Procedure guidate sono utili per indirizzare l'utente attraverso una sequenza di passaggi logica per il completamento di un'attività. Una serie di opzioni sono disponibili nei pannelli sequenziali e l'utente deve continuare a ogni passaggio prima di procedere al successivo. Una volta sufficienti valori predefiniti sono disponibili, il **fine** pulsante è abilitato.

 Modale procedure guidate vengono utilizzate per le attività che:

- Contenere diramazioni, in cui sono disponibili percorsi diversi a seconda delle scelte utente

- Contengono le dipendenze tra i vari passaggi, in cui i passaggi successivi dipendono da input dell'utente tramite la procedura precedente

- Sono sufficientemente complessi che l'interfaccia utente deve essere utilizzata per spiegare le scelte disponibili e i possibili risultati in ogni passaggio

- Sono transazionali, che richiedono una serie di passaggi da completare nella sua interezza prima tutte le modifiche vanno eseguito il commit

### <a name="common-conventions"></a>Convenzioni comuni
Per ottenere una progettazione ottimale e funzionalità con le finestre di dialogo, seguire queste convenzioni in dimensioni di finestra di dialogo, posizione, agli standard, la configurazione del controllo e allineamento, dell'interfaccia utente testo, le barre del titolo, i pulsanti di controllo e le chiavi di accesso.

Per linee guida per layout specifici, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Dimensione
Le finestre di dialogo deve adattarsi all'interno di una risoluzione minima dello schermo 1024 x 768 e dimensioni di finestra di dialogo iniziale non devono superare i 900 x 700 pixel. Le finestre di dialogo può essere ridimensionabile, ma non è un requisito.

Sono due raccomandazioni per le finestre di dialogo ridimensionabili:

1. Che una dimensione minima è definito per la finestra di dialogo che consente di ottimizzare per il controllo impostato senza ritaglio e regolare per supportare la crescita di localizzazione ragionevole.

2. Che le dimensioni in scala utente viene mantenuta tra le sessioni. Ad esempio, se l'utente ridimensiona una finestra di dialogo 150%, quindi un avvio successivo della finestra di dialogo visualizzerà a 150%.

#### <a name="position"></a>Posizione
Le finestre di dialogo deve essere presente al centro all'interno dell'IDE al primo avvio. L'ultima posizione delle finestre di dialogo non ridimensionabile non deve essere reso persistente, in modo che appaiano centrati su avvii successivi.

Per le finestre di dialogo ridimensionabili, le dimensioni devono essere mantenute sul avvii successivi. Per finestre di dialogo modale ridimensionabile, la posizione non deve essere resa persistente. Che vengano visualizzate al centro all'interno dell'IDE impedisce la possibilità della finestra di dialogo che viene visualizzato in una posizione imprevedibile o inutilizzabile quando configurazione schermo dell'utente è stato modificato.

Per i dialoghi non modale che possono essere spostati, la posizione dell'utente deve essere mantenuta in avvii successivi, come la finestra di dialogo può essere usato di frequente come parte integrante del flusso di lavoro più grande.

Quando le finestre di dialogo deve generare altre finestre di dialogo, la finestra di dialogo in primo piano deve sovrapporsi verso destra e verso il basso dall'elemento padre in modo che sia ovvio per l'utente che è stato aperto un altro percorso.

#### <a name="modality"></a>Modalità
Finestra modale in corso indica che gli utenti sono necessari per completare o annullare la finestra di dialogo prima di continuare. Poiché le finestre di dialogo modale impedisce all'utente l'interazione con altre parti dell'ambiente, il flusso di attività della funzionalità dovrebbe limitarne l'impiego come possibili. Quando è necessaria un'operazione modale, Visual Studio include un numero di finestre di dialogo condivise in che è possibile integrare le funzionalità. Se è necessario creare una nuova finestra di dialogo, seguire il modello di interazione di un dialogo esistente con funzionalità simili.

Quando gli utenti devono eseguire due attività contemporaneamente, ad esempio **trovare** e **sostituire** durante la scrittura del nuovo codice, la finestra di dialogo deve essere non modale in modo che l'utente può passare facilmente tra di essi. Visual Studio Usa in genere finestre degli strumenti per questo tipo di supporto di editor attività collegata.

#### <a name="control-configuration"></a>Configurazione del controllo
Essere coerenti con le configurazioni del controllo esistenti che eseguono la stessa operazione in Visual Studio.

#### <a name="title-bars"></a>Barre del titolo

- Il testo nella barra del titolo deve riflettere il nome del comando che l'ha avviata.

- Nessuna icona deve essere utilizzata nella barra del titolo della finestra. Nei casi in cui il sistema richiede uno, usare il logo di Visual Studio.

- Le finestre di dialogo non è necessario ridurre o ingrandire i pulsanti.

- Pulsante nella barra del titolo sono state deprecate. Non verranno aggiunte alle nuove finestre di dialogo. Quando sono presenti, avviano un argomento della Guida che è concettualmente attinenti all'attività.

  ![Le specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 03_TitleBarSpecs")<br />Specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio

#### <a name="control-buttons"></a>Pulsanti di controllo
In genere **OK**, **Annulla**, e **Guida** devono essere disposte orizzontalmente i pulsanti nell'angolo inferiore destro della finestra di dialogo. Se una finestra di dialogo dispone di diversi altri pulsanti nella parte inferiore della finestra di dialogo che potrebbe presentarsi visual confusione con i pulsanti di controllo, è consentita la pila verticale alternativa.

![Le configurazioni accettabile per i pulsanti di controllo nelle finestre di dialogo di Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 04_ControlButtonConfig")<br />Configurazioni accettabile per i pulsanti di controllo nelle finestre di dialogo di Visual Studio

La finestra di dialogo deve includere un pulsante di controllo predefinito. Per determinare il comando migliore da usare come valore predefinito, scegliere una delle opzioni seguenti (elencate in ordine di priorità):

- Scegliere il comando più sicuro e sicuro come impostazione predefinita. Ciò significa che se si sceglie il comando più probabile evitare la perdita di dati ed evitare l'accesso di sistema non intenzionali.

- Se sicurezza e la perdita di dati non sono fattori, quindi scegliere il comando predefinito basato su convenience. Tra cui il comando probabilmente come predefinito determinerà un miglioramento del flusso di lavoro dell'utente quando la finestra di dialogo supporta le attività frequenti o ripetitive.

Evitare di scegliere un'azione distruttiva in modo permanente per il comando predefinito. Se è presente un comando di questo tipo, scegliere un comando sicuro come impostazione predefinita.

#### <a name="access-keys"></a>Chiavi di accesso
Non usare chiavi di accesso per **OK**, **Cancel**, o **Guida** pulsanti. Per impostazione predefinita, questi pulsanti sono mappati a tasti di scelta rapida:

| Nome del pulsante | Tasto di scelta rapida |
| --- | --- |
| OK | INVIO |
| Annulla | ESC |
| Help | F1 |

#### <a name="imagery"></a>Immagini
Utilizzare le immagini con parsimonia nelle finestre di dialogo. Non usare le icone grandi nelle finestre di dialogo si limita l'utilizzo massimo dello spazio. Usare immagini solo se sono una parte importante di trasmettere il messaggio all'utente, come le icone di avviso o stato animazioni.

### <a name="BKMK_PrioritizingAndLayering"></a> Definire le priorità e sovrapposizione

#### <a name="prioritizing-your-ui"></a>Definizione delle priorità dell'interfaccia utente
Potrebbe essere necessario portare alcuni elementi dell'interfaccia utente a forefront e inserire il comportamento più avanzato e le opzioni (inclusi i comandi sconosciuti) nelle finestre di dialogo. Forniscono le funzionalità comunemente usato all'avanguardia per creare spazio per tale e rendendo visibile per impostazione predefinita nell'interfaccia utente con un'etichetta di testo quando viene visualizzata la finestra di dialogo.

#### <a name="layering-your-ui"></a>Disposizione su livelli dell'interfaccia utente
Se è stato determinato che una finestra di dialogo è necessario ma le funzionalità correlate che si desidera presentare all'utente va oltre ciò che può essere visualizzato in una semplice finestra di dialogo, è necessario per l'interfaccia utente di livello. Visual Studio Usa i metodi dei livelli più comuni sono le schede e corridoi o dashboard. In alcuni casi, potrebbero essere appropriate aree che è possono espandere e comprimere. Interfaccia utente adattiva è in genere sconsigliato in Visual Studio.

Esistono vantaggi e svantaggi in metodi diversi di sovrapposizione dell'interfaccia utente tramite i controlli di tipo scheda. Esaminare l'elenco seguente per assicurarsi che si sceglie una tecnica di sovrapposizione appropriata alle proprie esigenze.

##### <a name="tabbing"></a>Tabulazione

| Meccanismo di passaggio a un'altra | Vantaggi e uso appropriato | Uso inappropriato e svantaggi |
| --- | --- | --- |
| Controllo Tab | Raggruppare in modo logico le pagine della finestra in insiemi correlati<br /><br />Utile per meno di cinque, o il numero di schede che rientrano in una riga tra la finestra di dialogo, pagine di controlli correlati nella finestra di dialogo<br /><br />Le etichette delle schede deve essere breve: uno o due parole in grado di identificare facilmente il contenuto<br /><br />Uno stile di finestra di dialogo di sistema comuni<br /><br />Esempio: **Esplora file &gt; le proprietà degli elementi** | L'impostazione di etichette descrittive brevi può risultare difficile<br /><br />In genere non supporta la scalabilità oltre cinque schede in una finestra di dialogo<br /><br />Non appropriato se sono presenti troppi schede per una riga (usare una tecnica alternativa dei livelli)<br /><br />Non è estendibile |
| Navigazione nella barra laterale | Dispositivo per lo scambio semplice in grado di soddisfare più categorie rispetto a schede<br /><br />Elenco completo delle categorie (senza gerarchia)<br /><br />Estendibile<br /><br />Esempio: **Personalizza... &gt; Comando Aggiungi** | Non è un utilizzo corretto di spazio orizzontale se sono presenti meno di tre gruppi<br /><br />Attività potrebbe essere più adatti per un elenco a discesa |
| Controllo Tree | Consente di categorie senza limite<br /><br />Consente di raggruppamento e/o gerarchia delle categorie<br /><br />Estendibile<br /><br />Esempio: **Strumenti &gt; opzioni** | Gerarchie molto annidate possono causare un numero eccessivo di scorrimento orizzontale<br /><br />Visual Studio include un eccesso di visualizzazioni dell'albero |
| Wizard | Consente il completamento dell'operazione per guidare l'utente tramite i passaggi sequenziali, basato su attività: la procedura guidata rappresenta un'attività di alto livello e i pannelli singole rappresentano le sottoattività necessarie per eseguire l'attività complessiva<br /><br />Utile quando l'attività supera i limiti dell'interfaccia utente, come quando l'utente sarebbe altrimenti necessario usare più editor e finestre per completare l'attività degli strumenti<br /><br />Utile quando l'attività richiede la creazione di rami<br /><br />Utile quando l'attività contiene le dipendenze tra i vari passaggi<br /><br />Utile quando più attività simili con fork una decisione può essere presentata in una finestra di dialogo per ridurre il numero di diverse finestre di dialogo simile | Non è appropriato per qualsiasi attività che non richiede un flusso di lavoro sequenza<br /><br />Gli utenti possono diventare sovraccaricato e confusi da una procedura guidata con un numero eccessivo di passaggi<br /><br />Procedure guidate non dispongono intrinsecamente sullo schermo |

##### <a name="hallways-or-dashboards"></a>Corridoi o nei dashboard
Corridoi e i dashboard sono i pannelli che fungono da avvio punti da altre finestre di dialogo e finestre o finestre di dialogo. Ben progettata "corridoio" evidenzia immediatamente solo le più comuni opzioni di, comandi e le impostazioni, consentendo all'utente di eseguire facilmente le attività comuni. Ad esempio un corridoio reale fornisce porte per accedere a locali di cui dispone, qui l'interfaccia utente meno comuni verrà raccolti in separato "chat" (spesso altre finestre di dialogo) di funzionalità correlate che è possibile accedere da corridoio principale.

In alternativa, un'interfaccia utente che offre tutte le funzionalità disponibili in una raccolta singola anziché il refactoring della funzionalità meno comuni in posizioni distinte è semplicemente un dashboard.

![Concetto hallway per esporre un'interfaccia utente aggiuntiva in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 08_Hallway")<br />Concetto hallway per esporre un'interfaccia utente aggiuntiva in Outlook

##### <a name="adaptive-ui"></a>Interfaccia utente adattiva
Mostrare o nascondere l'interfaccia utente in base all'utilizzo o Self-segnalate esperienza di un utente è un altro modo per presentare l'interfaccia utente necessaria, nascondendo altre parti. Ciò non è consigliata in Visual Studio, perché gli algoritmi per decidere quando mostrare o nascondere l'interfaccia utente possono essere difficili e le regole saranno sempre errate per alcuni set di case.

## <a name="BKMK_Projects"></a> Progetti

### <a name="projects-in-the-solution-explorer"></a>Progetti in Esplora soluzioni
La maggior parte dei progetti vengono classificati in base al riferimento, basata su directory o misto. Tutti i tre tipi di progetti sono supportati contemporaneamente in Esplora soluzioni. La radice dell'esperienza utente in uso dei progetti viene eseguita all'interno di questa finestra. Anche se i nodi di progetto diversi sono riferimenti, directory o i progetti di tipo modalità mista, è presente un modello di interazione comune che deve essere applicato come punto di partenza prima divergenti in motivi definiti dall'utente specifici del progetto.

I progetti devono sempre:

- Supporta la possibilità di aggiungere le cartelle dei progetti per organizzare il contenuto di progetto

- Gestire un modello coerente per la persistenza del progetto

I progetti deve essere gestito anche modelli di interazione coerente per:

- Rimozione di elementi di progetto

- Salvataggio di documenti

- Modifica delle proprietà di progetto

- Modifica il progetto in una visualizzazione alternativa

- Operazioni di trascinamento e rilascio

### <a name="drag-and-drop-interaction-model"></a>Modello di interazione di trascinamento e rilascio
In genere classificare se stessi come basato sul riferimento (in modo permanente solo i riferimenti a elementi del progetto in archiviazione), i progetti basati su directory (in grado di rendere persistenti solo gli elementi di progetto fisicamente archiviate all'interno di gerarchia del progetto), o mista (in modo permanente i riferimenti o gli elementi fisici). L'IDE supporta tutti i tre tipi di progetti contemporaneamente all'interno di **Esplora soluzioni**.

Da una prospettiva di trascinamento e rilascio, le caratteristiche seguenti devono applicare a ogni tipo di progetto all'interno di **Esplora soluzioni**:

- **In base al riferimento progetto:** Il punto chiave è che il progetto sta trascinando intorno a un riferimento a un elemento nell'archivio. Quando un progetto basato sul riferimento agisce come origine per un'operazione di spostamento, è necessario rimuovere solo il riferimento all'elemento dal progetto. L'elemento non deve effettivamente eliminato dal disco rigido. Quando un progetto basato sul riferimento agisce come una destinazione per un'operazione (copia o spostamento), opportuno aggiungere un riferimento all'elemento di origine originale senza creare una copia privata dell'elemento.

- **Directory in base al progetto:** Da un punto di vista di trascinamento e rilascio, il progetto sta trascinando tutto l'elemento fisico anziché un riferimento. Quando un progetto basato su directory agisce come origine per un'operazione di spostamento, deve finire eliminazione dell'elemento fisico dal disco rigido, oltre a rimuoverlo dal progetto. Quando un progetto basato su directory agisce come una destinazione per un'operazione (copia o spostamento), consigliabile eseguire una copia dell'elemento di origine nel relativo percorso di destinazione.

- **Progetto di destinazione mista:** Da un punto di vista di trascinamento e rilascio, il comportamento di questo tipo di progetto è basato sulla natura dell'elemento trascinato (un riferimento a un elemento nello spazio di memorizzazione) o l'elemento stesso. Il comportamento corretto per i riferimenti e gli elementi fisici sono descritti in precedenza.

Se si sono verificati solo un tipo di progetto nel **Esplora soluzioni**, operazioni di trascinamento e rilascio sarà molto semplice. Poiché ogni sistema del progetto ha la possibilità di definire il comportamento di trascinamento e rilascio, alcune linee guida (basati sul comportamento di trascinamento e rilascio di Windows Explorer) deve essere seguita per garantire un'esperienza utente prevedibile:

- Invariato un'operazione di trascinamento **Esplora soluzioni** (quando Ctrl né MAIUSC è premuto) deve risultare in un'operazione di spostamento.

- Operazione di spostamento trascinamento dovrebbe restituire anche un'operazione di spostamento.

- Trascinare premendo CTRL operazione dovrebbe restituire un'operazione di copia.

- I sistemi di progetto basato su riferimenti e mista supportano la nozione di aggiunta di un collegamento (o riferimento) all'elemento di origine. Quando questi progetti vengono usati come destinazione di un'operazione di trascinamento e rilascio (quando **Ctrl + Maiusc** viene tenuto premuto), dovrebbe restituire un riferimento all'elemento da aggiungere al progetto

Non tutte le operazioni di trascinamento e rilascio sono ragionevole tra le combinazioni dei progetti in base al riferimento basato su directory e misti. In particolare, è problematico al fatto che consentire un'operazione di spostamento tra un progetto di origine basato su directory e un progetto di destinazione in base al riferimento perché il progetto di origine basato su directory sarà necessario eliminare l'elemento di origine dopo il completamento dello spostamento. Progetto di destinazione basato su riferimenti terminerebbe quindi con un riferimento a un elemento eliminato.

È inoltre fuorviante al fatto che consentire un'operazione di copia tra questi tipi di progetti perché il progetto in base al riferimento di destinazione non deve fare una copia indipendente dell'elemento di origine. Analogamente, Ctrl + Maiusc trascinando una directory in base al progetto di destinazione non deve essere consentito perché è in grado di mantenere riferimenti a un progetto basato su directory. Nei casi in cui l'operazione di trascinamento e rilascio non è supportata, l'IDE deve impedire l'eliminazione e far visualizzare all'utente il cursore di non trascinamento (mostrato nella seguente tabella puntatore).

Per implementare correttamente il comportamento di trascinamento e rilascio, il progetto di origine dell'operazione di trascinamento deve comunicare la sua natura per il progetto di destinazione. (Ad esempio, si tratta o directory dal basato su riferimenti?) Queste informazioni sono indicate dal formato degli Appunti che è disponibile dall'origine. Come origine di un trascinamento (o l'operazione di copia negli Appunti) un progetto deve offrire uno `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` rispettivamente, a seconda se il progetto è basato sul riferimento o basate su directory. Entrambi questi formati hanno lo stesso contenuto di dati, che è simile a di Windows `CF_HDROP` formattare ad eccezione del fatto che gli elenchi di stringhe, anziché essere nomi di file, sono un valore double -`NULL` terminato l'elenco di `Projref` stringhe (come restituito da `IVsSolution::GetProjrefOfItem`o `::GetProjrefOfProject` come appropriato).

Come destinazione di un rilascio (o l'operazione Incolla degli Appunti), un progetto deve accettare entrambi `CF_VSREFPROJECTITEMS` e `CF_VSSTGPROJECTITEMS`, anche se la gestione dell'operazione di trascinamento e rilascio esatta varia a seconda della natura del progetto di destinazione e il progetto di origine. Il progetto di origine dichiara la sua natura dal fatto che offre `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS`. La destinazione del trascinamento riconosce la propria natura e pertanto ha informazioni sufficienti per prendere le decisioni come e se un sposta, copia e collegamento deve essere eseguito. L'utente modifica l'operazione di trascinamento e rilascio deve essere eseguita premendo il Ctrl, MAIUSC, o i tasti Ctrl e MAIUSC. È importante che l'obiettivo di rilascio indicare in modo corretto verrà eseguita in anticipo in quale operazione relativi `DragEnter` e `DragOver` metodi. Il **Esplora soluzioni** eseguirà automaticamente se il progetto di origine e il progetto di destinazione sono nello stesso progetto.

Il trascinamento degli elementi di progetto tra istanze di Visual Studio (ad esempio, da un'istanza di devenv.exe a un'altra) in modo specifico non è supportato. Il **Esplora soluzioni** Disabilita direttamente anche questo.

L'utente deve sempre essere in grado di determinare l'effetto di un'operazione di trascinamento e rilascio selezionando un elemento, trascinarlo nella posizione di destinazione e osservare che i seguenti puntatori del mouse viene visualizzata prima l'elemento viene eliminato:

| Puntatore del mouse | Comando | Descrizione |
| :---: | --- | --- |
| ![Passare il mouse sull'icona "nessun rilascio"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | Nessun rilascio | Elemento non può essere rilasciato nella posizione specificata. |
| ![Mouse "copy" icon](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copia | Elemento verrà copiato nel percorso di destinazione. |
| ![Mouse "spostare" sull'icona](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | Move | Elemento verrà spostato nel percorso di destinazione. |
| ![Icona "Aggiungi riferimento" del mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | Aggiungi riferimento | Verrà aggiunto un riferimento all'elemento selezionato nel percorso di destinazione. |

#### <a name="reference-based-projects"></a>Progetti in base al riferimento
 Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché le operazioni Taglia/Copia/Incolla) che devono essere eseguite in base alla natura di chiavi di elemento e il modificatore di origine premuto per i progetti di destinazione basati su cui viene fatto riferimento:

| Modificatore | Category | Elemento di origine: Collegamento/riferimento | Elemento di origine: Elemento o il file system fisico (`CF_HDROP`) |
| --- | --- | --- | --- |
| Nessun modificatore | Operazione | Move | Collegamento |
| Nessun modificatore | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |
| Nessun modificatore | Source | Elimina riferimento all'elemento originale | Mantiene l'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| Maiusc + trascinamento | Operazione | Move | Nessun rilascio |
| Maiusc + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Nessun rilascio |
| Maiusc + trascinamento | Source | Elimina riferimento all'elemento originale | Nessun rilascio |
| Maiusc + trascinamento | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | Nessun rilascio |
| CTRL + trascinare | Operazione | Copia | Nessun rilascio |
| CTRL + trascinare | destinazione | Aggiunge il riferimento alla voce originale | Nessun rilascio |
| CTRL + trascinare | Source | Mantiene il riferimento all'elemento originale | Nessun rilascio |
| CTRL + trascinare | Risultato | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | Nessun rilascio |
| CTRL + MAIUSC + trascinamento | Operazione | Collegamento | Collegamento |
| CTRL + MAIUSC + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |
| CTRL + MAIUSC + trascinamento | Source | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL + MAIUSC + trascinamento | Risultato | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| CTRL + MAIUSC + trascinamento | Nota | Stesso comportamento di trascinamento e rilascio per tasti di scelta rapida in Windows Explorer. ||
| Taglia e Incolla | Operazione | Move | Collegamento |
| Taglia e Incolla | destinazione | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |
| Taglia e Incolla | Source | Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale |
| Taglia e Incolla | Risultato | Elemento rimane nella posizione originale nell'archiviazione | Elemento rimane nella posizione originale nell'archiviazione |
| Copiare e incollare | Operazione | Copia | Collegamento |
| Copiare e incollare | Source | Aggiunge il riferimento alla voce originale | Aggiunge il riferimento alla voce originale |
| Copiare e incollare | Risultato | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| Copiare e incollare | Operazione | Elemento rimane nella posizione originale nell'archiviazione | Elemento rimane nella posizione originale nell'archiviazione |

#### <a name="directory-based-projects"></a>Progetti basati su directory
Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché le operazioni Taglia/Copia/Incolla) che devono essere eseguite in base alla natura di chiavi di elemento e il modificatore di origine premuto per i progetti basati su directory di destinazione:

| Modificatore | Category | Elemento di origine: Collegamento/riferimento | Elemento di origine: Elemento o il file system fisico (`CF_HDROP`) |
|-----------------|----------| - | - |
| Nessun modificatore | Operazione | Move | Move |
| Nessun modificatore | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |
| Nessun modificatore | Source | Elimina riferimento all'elemento originale | Elimina riferimento all'elemento originale |
| Maiusc + trascinamento | Operazione | Move | Move |
| Maiusc + trascinamento | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |
| Maiusc + trascinamento | Source | Elimina riferimento all'elemento originale | Elimina elemento dalla posizione originale |
| Maiusc + trascinamento | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| CTRL + trascinare | Operazione | Copia | Copia |
| CTRL + trascinare | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |
| CTRL + trascinare | Source | Mantiene il riferimento all'elemento originale | Mantiene il riferimento all'elemento originale |
| CTRL + trascinare | Risultato | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| CTRL + MAIUSC + trascinamento | | Nessun rilascio | Nessun rilascio |
| Taglia e Incolla | Operazione | Move | Move |
| Taglia e Incolla | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |
| Taglia e Incolla | Source | Elimina riferimento all'elemento originale | Elimina elemento dalla posizione originale |
| Taglia e Incolla | Risultato | Elemento rimane nella posizione originale nell'archiviazione | Elemento viene eliminato dalla posizione originale nell'archiviazione |
| Copiare e incollare | Operazione | Copia | Copia |
| Copiare e incollare | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Copiare e incollare | Source | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copiare e incollare | Risultato | Elemento rimane nella posizione originale nell'archiviazione | Elemento rimane in archiviazione di componenti aggiuntivi di percorso originale |

#### <a name="mixed-target-projects"></a>Progetti di destinazione mista
Nella tabella seguente sono riepilogate le operazioni di trascinamento e rilascio (nonché le operazioni Taglia/Copia/Incolla) che devono essere eseguite in base alla natura di chiavi di elemento e il modificatore di origine premuto per i progetti di destinazione mista:

| Modificatore | Category | Elemento di origine: Collegamento/riferimento | Elemento di origine: Elemento o il file system fisico (`CF_HDROP`) |
| --- | --- | --- | --- |
| Nessun modificatore | Operazione | Move | Move |
| Nessun modificatore | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Nessun modificatore | Source | Elimina riferimento all'elemento originale | Elimina riferimento all'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento viene eliminato dalla posizione originale nell'archiviazione |
| Maiusc + trascinamento | Operazione | Move | Move |
| Maiusc + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Maiusc + trascinamento | Source | Elimina riferimento all'elemento originale | Elimina elemento dalla posizione originale |
| Maiusc + trascinamento | Risultato | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento viene eliminato dalla posizione originale nell'archiviazione |
| CTRL + trascinare | Operazione | Copia | Copia |
| CTRL + trascinare | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| CTRL + trascinare | Source | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL + trascinare | Risultato | `DROPEFFECT_ COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| CTRL + MAIUSC + trascinamento | Operazione | Collegamento | Collegamento |
| CTRL + MAIUSC + trascinamento | destinazione | Aggiunge il riferimento alla voce originale | Aggiunto riferimento a elemento di origine originale |
| CTRL + MAIUSC + trascinamento | Source | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL + MAIUSC + trascinamento | Risultato | `DROPEFFECT_ LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| Taglia e Incolla | Operazione | Move | Move |
| Taglia e Incolla | destinazione | Elemento di copie da percorso di destinazione | Elemento di copie da percorso di destinazione |
| Taglia e Incolla | Source | Elimina riferimento all'elemento originale | Elimina elemento dalla posizione originale |
| Taglia e Incolla | Risultato | Elemento rimane nella posizione originale nell'archiviazione | Elemento viene eliminato dalla posizione originale nell'archiviazione |
| Copiare e incollare | Operazione | Copia | Copia |
| Copiare e incollare | destinazione | Aggiunge il riferimento alla voce originale | Elemento di copie da percorso di destinazione |
| Copiare e incollare | Source | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copiare e incollare | Risultato | Elemento rimane nella posizione originale nell'archiviazione | Elemento rimane nella posizione originale nell'archiviazione |

Tali dettagli devono prendere in considerazione quando si implementa il trascinamento **Esplora soluzioni**:

- Progettare per più scenari di selezione.

- I nomi di file (percorso completo) devono essere univoci per il progetto di destinazione o l'eliminazione non deve essere consentito.

- I nomi delle cartelle devono essere univoci (senza maiuscole/minuscole) a livello di essi vengono eliminati.

- Vi sono differenze di comportamento tra i file che sono chiusi o aperti in fase di trascinamento (non indicata nei scenari descritti in precedenza).

- File di livello superiore si comportano in modo leggermente diverso rispetto ai file nelle cartelle.

Un altro problema da considerare è la modalità di gestione di operazioni di spostamento agli elementi che dispongono di editor o aprire finestre di progettazione. Il comportamento previsto è come indicato di seguito (si applica a tutti i tipi di progetto):

1. Se l'aprire editor/finestra di progettazione non ha le modifiche non salvate, quindi la finestra dell'editor/progettazione deve essere automaticamente chiuso.

2. Se l'aprire editor/finestra di progettazione sono modifiche non salvate, quindi l'origine dell'operazione di trascinamento deve attendere per l'eliminazione si verificano e quindi chiedere all'utente di salvare le modifiche non sottoposte a commit nei documenti aperti prima di chiudere la finestra con un prompt simile al seguente :

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

In questo modo l'utente la possibilità di salvare i lavori in corso prima che la destinazione crea le copie. Un nuovo metodo `IVsHierarchyDropDataSource2::OnBeforeDropNotify` è stato aggiunto per consentire queste operazioni di gestione.

La destinazione è possibile copiare lo stato dell'elemento perché è nello spazio di memorizzazione (senza includere le modifiche non salvate nell'editor, se l'utente ha scelto **No**). Dopo che la destinazione è stata completata la copia (in `IVsHierarchyDropDataSource::Drop`), l'origine è data la possibilità di completare la parte di eliminazione dell'operazione di spostamento (in `IVsHierarchyDropDataSource::OnDropNotify`).

Qualsiasi editor con le modifiche non salvate deve essere lasciato aperto. Per i documenti con le modifiche non salvate, ciò significa che la fase di copia dell'operazione di spostamento verrà eseguita ma verrà interrotta la porzione di eliminazione. In uno scenario di selezione di più quando l'utente sceglie **No**, tali documenti con le modifiche non salvate non devono essere chiuso o rimossi, ma quelli senza modifiche non salvate deve essere chiuso e rimossi.