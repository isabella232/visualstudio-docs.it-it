---
title: Modelli di applicazione per Visual Studio | Microsoft Docs
description: Informazioni sulla differenza tra le finestre di documento, le finestre degli strumenti e le finestre di dialogo non modali, inclusi i modelli di utilizzo delle finestre per le nuove funzionalità di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b19d60294431a08fa26f11bf58606893f392cd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060237"
---
# <a name="application-patterns-for-visual-studio"></a>Modelli delle applicazioni per Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interazioni finestra

### <a name="overview"></a>Panoramica
I due tipi di finestra principali utilizzati in Visual Studio sono gli editor di documenti e le finestre degli strumenti. Rare, ma possibili, sono finestre di dialogo non modali di grandi dimensioni. Sebbene siano tutti non modali nella shell, i modelli sono fondamentalmente diversi. In questa sezione viene illustrata la differenza tra le finestre di documento, le finestre degli strumenti e le finestre di dialogo non modali. I modelli di finestre di dialogo modali sono analizzati nelle [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Confronto dei modelli di utilizzo delle finestre
Le **finestre dei documenti** vengono visualizzate quasi sempre all'interno dell'area documento. In questo modo all'editor di documenti viene assegnata una "fase centrale" per disporre le finestre degli strumenti aggiuntive.

Una **finestra degli strumenti** viene spesso visualizzata come finestra separata e più piccola compressa rispetto al bordo dell'IDE. Questo può essere visibile, nascosto o nascosto automaticamente. Tuttavia, a volte le finestre degli strumenti vengono presentate all'interno dell'area dei documenti, deselezionando la proprietà **Window/docking** nella finestra. Questo comporta una maggiore proprietà, ma anche una decisione di progettazione comune: quando si tenta di eseguire l'integrazione in Visual Studio, è necessario decidere se la funzionalità deve visualizzare una finestra degli strumenti o una finestra del documento.

Le **finestre di dialogo non modali** sono sconsigliate in Visual Studio. La maggior parte delle finestre di dialogo non modali sono, per definizione, le finestre degli strumenti mobili e devono essere implementate in questo modo. Le finestre di dialogo non modali sono consentite nei casi in cui le dimensioni di una normale finestra degli strumenti ancorata al lato della Shell sarebbero troppo limitate. Sono inoltre consentite nei casi in cui è probabile che l'utente sposti la finestra di dialogo in un monitor secondario.

Valutare con attenzione il tipo di contenitore necessario. Nella tabella seguente sono riportate le considerazioni sul modello di utilizzo comune per la progettazione dell'interfaccia utente.

||Finestra del documento|Finestra degli strumenti|Finestra di dialogo non modale|
|-|---------------------|-----------------|---------------------|
| **Position** | Sempre posizionato all'interno dell'area dei documenti e non è ancorato attorno ai bordi dell'IDE. Il valore può essere "Estratto", in modo che venga eseguito il float separatamente dalla shell principale. | In genere, la scheda è ancorata attorno ai bordi dell'IDE, ma può essere personalizzata in modo da essere mobile, nascosta automaticamente (sbloccata) o ancorata all'interno dell'area dei documenti.|Grande finestra mobile separata dall'IDE. |
| **Modello di commit** | *Commit ritardato*<br /><br /> Per salvare i dati in un documento, l'utente deve eseguire il comando **&gt; Salva file**, **Salva con nome** o **Salva tutto** . Una finestra del documento ha il concetto di dati all'interno del quale è stata "sporcata", quindi è stato eseguito il commit in uno dei comandi Save. Quando si chiude una finestra del documento, tutti i contenuti vengono salvati su disco o persi. | *Commit immediato*<br /><br /> Nessun modello di salvataggio. Per le finestre degli strumenti di controllo che facilitano la modifica di un file, il file deve essere aperto nell'editor o nella finestra di progettazione attiva e l'editor o la finestra di progettazione è proprietario del salvataggio. | *Commit posticipato o immediato*<br /><br /> In genere, una finestra di dialogo non modale di grandi dimensioni richiede un'azione per eseguire il commit delle modifiche e consente un'operazione di annullamento, che esegue il rollback delle modifiche apportate all'interno della sessione di dialogo.  In questo modo si distingue una finestra di dialogo non modale da una finestra degli strumenti in cui le finestre degli strumenti hanno sempre un modello di commit immediato. |
| **Visibilità** | *Apri/crea (file) e Chiudi*<br /><br /> L'apertura di una finestra di documento viene eseguita tramite l'apertura di un documento esistente o l'utilizzo di un modello per creare un nuovo documento. Non è presente alcun comando "Apri \<specific editor> ". | *Nascondi e Mostra*<br /><br /> Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate. Il contenuto e gli Stati nella finestra degli strumenti vengono mantenuti in visualizzazione o nascosti. Le finestre degli strumenti a più istanze possono essere chiuse e nascoste. Quando viene chiusa una finestra degli strumenti a più istanze, il contenuto e lo stato all'interno della finestra degli strumenti vengono eliminati. | *Avviato da un comando*<br /><br /> Le finestre di dialogo vengono avviate da un comando basato su attività. |
| **Istanze** | *Istanze a istanze diverse*<br /><br /> Molti editor possono essere aperti contemporaneamente e modificare file diversi, mentre alcuni editor consentono anche di aprire lo stesso file in più di un editor (usando il comando **finestra &gt; nuova finestra** ).<br /><br /> Un singolo editor può modificare uno o più file allo stesso tempo (Progettazione progetti). | *A istanza singola o a istanze diverse*<br /><br /> I contenuti cambiano per riflettere il contesto (come nel Visualizzatore proprietà) o lo stato attivo/contesto push ad altre finestre (Elenco attività, Esplora soluzioni).<br /><br /> Le finestre degli strumenti a istanza singola e a istanza singola devono essere associate alla finestra del documento attivo, a meno che non esista un motivo valido per non farlo. | *Istanza singola* |
| **esempi** | Editor di **testo**, ad esempio l'editor di codice<br /><br /> **Aree di progettazione**, ad esempio una finestra di progettazione di form o una superficie di modellazione<br /><br /> **Layout di controllo simili a finestre di dialogo** come la finestra di progettazione del manifesto | Il **Esplora soluzioni** fornisce una soluzione e i progetti contenuti nella soluzione<br /><br /> Il **Esplora server** fornisce una visualizzazione gerarchica dei server e delle connessioni dati che l'utente sceglie di aprire nella finestra di. Aprendo un oggetto dalla gerarchia del database, ad esempio una query, viene aperta una finestra del documento che consente all'utente di modificare la query.<br /><br /> Il **Visualizzatore proprietà** Visualizza le proprietà dell'oggetto selezionato in una finestra del documento o in un'altra finestra degli strumenti. Le proprietà vengono presentate in una visualizzazione griglia gerarchica o in controlli di tipo finestra di dialogo complessi e consentono all'utente di impostare i valori per tali proprietà. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Finestre degli strumenti

### <a name="overview"></a>Panoramica
Le finestre degli strumenti supportano le operazioni dell'utente che si verificano nelle finestre dei documenti. Possono essere usati per visualizzare una gerarchia che rappresenta un oggetto radice fondamentale fornito da Visual Studio e che può essere modificato.

Quando si considera una nuova finestra degli strumenti nell'IDE, gli autori devono:

- Usare le finestre degli strumenti esistenti appropriate per le attività e non crearne di nuove con funzionalità simili. Le nuove finestre degli strumenti devono essere create solo se offrono uno strumento o una funzionalità molto diversa che non possono essere integrate in una finestra simile oppure trasformando una finestra esistente in un hub pivot.

- Utilizzare una barra dei comandi standard, se necessario, nella parte superiore della finestra degli strumenti.

- Essere coerenti con i modelli già presenti in altre finestre degli strumenti per la presentazione del controllo e la navigazione da tastiera.

- Essere coerenti con la presentazione del controllo in altre finestre degli strumenti.

- Rendere visibile automaticamente le finestre degli strumenti specifici del documento quando possibile, in modo che vengano visualizzate solo quando il documento padre è attivato.

- Verificare che il contenuto della finestra sia navigabile tramite la tastiera (supporto dei tasti di direzione).

#### <a name="tool-window-states"></a>Stati della finestra degli strumenti
Le finestre degli strumenti di Visual Studio hanno stati diversi, alcune delle quali sono attivate dall'utente, ad esempio la funzionalità Nascondi automaticamente. Gli altri Stati, come la visibilità automatica, consentono di visualizzare le finestre degli strumenti nel contesto corretto e di nasconderle quando non sono necessarie. Sono presenti cinque Stati della finestra degli strumenti in totale.

- Le finestre degli strumenti **ancorate/** bloccate possono essere collegate a uno dei quattro lati dell'area del documento. Viene visualizzata l'icona della puntina da disegno sulla barra del titolo della finestra degli strumenti. La finestra degli strumenti può essere ancorata orizzontalmente o verticalmente lungo il bordo della shell e altre finestre degli strumenti e può anche essere collegata a schede.

- Le finestre degli strumenti **nascoste automaticamente** sono sbloccate. La finestra può scivolare fuori dal controllo, lasciando una scheda (con il nome della finestra degli strumenti e la relativa icona) sul bordo dell'area del documento. La finestra degli strumenti viene sottoposta a scorrimento quando un utente passa sulla scheda.

- Le finestre degli strumenti **visibili** automaticamente vengono visualizzate quando viene avviata un'altra parte dell'interfaccia utente, ad esempio un editor, o si ottiene lo stato attivo.

- Spostamento delle finestre degli strumenti **mobili** all'esterno dell'IDE. Questa funzionalità è utile per le configurazioni di più monitor.

- Le finestre degli strumenti per **documenti a schede** possono essere ancorate all'interno dell'area dei documenti. Questa operazione è utile per le finestre degli strumenti di grandi dimensioni, come le Visualizzatore oggetti, che necessitano di una maggiore quantità di spazio reale rispetto all'ancoraggio ai bordi del frame.

![Stati della finestra degli strumenti in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Stati della finestra degli strumenti in Visual Studio

#### <a name="single-instance-and-multi-instance"></a>A istanza singola e a istanze diverse
Le finestre degli strumenti sono a istanza singola o a istanze diverse. Alcune finestre degli strumenti a istanza singola potrebbero essere associate alla finestra del documento attiva, mentre le finestre degli strumenti a più istanze potrebbero non. Le finestre degli strumenti a istanze diverse rispondono al comando **finestra &gt; nuova finestra** creando una nuova istanza della finestra. Nell'immagine seguente viene illustrata una finestra degli strumenti che Abilita il comando nuova finestra quando un'istanza della finestra è attiva:

![Finestra degli strumenti che Abilita il comando ' nuova finestra ' quando un'istanza della finestra è attiva](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Finestra degli strumenti che Abilita il comando ' nuova finestra ' quando un'istanza della finestra è attiva

Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate, mentre le finestre degli strumenti a istanze diverse possono essere chiuse e nascoste. Tutte le finestre degli strumenti possono essere ancorate, collegate a schede, a virgola mobile o impostate come finestra figlio interfaccia Multiple-Document (MDI) (simile a una finestra del documento). Tutte le finestre degli strumenti devono rispondere ai comandi appropriati di gestione della finestra nel menu finestra:

![Comandi di gestione della finestra nel menu finestra di Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandi di gestione della finestra nel menu finestra di Visual Studio

#### <a name="document-specific-tool-windows"></a>Finestre degli strumenti specifiche del documento
Alcune finestre degli strumenti sono progettate per essere modificate in base a un tipo di documento specifico. Queste finestre vengono aggiornate continuamente per riflettere la funzionalità applicabile alla finestra del documento attiva nell'IDE.

Esempi di finestre degli strumenti il cui contenuto viene modificato per riflettere l'editor selezionato sono la casella degli strumenti e la struttura del documento. Queste finestre mostrano una filigrana quando un editor ha lo stato attivo che non offre contesto alla finestra.

#### <a name="navigable-list-tool-windows"></a>Finestre degli strumenti elenco navigabile
In alcune finestre degli strumenti viene visualizzato un elenco di elementi esplorabili con cui l'utente può interagire. In questo tipo di finestra dovrebbero essere sempre presenti commenti e suggerimenti per l'elemento corrente nell'elenco, anche se la finestra è inattiva. L'elenco deve rispondere ai comandi **GoToNextLocation** e **GoToPrevLocation** cambiando anche l'elemento attualmente selezionato nella finestra

Esempi di finestre degli strumenti di elenco navigabile sono le Esplora soluzioni e la finestra Risultati ricerca.

### <a name="tool-window-types"></a>Tipi di finestra degli strumenti

#### <a name="common-tool-windows-and-their-functions"></a>Finestre degli strumenti comuni e relative funzioni

**Finestre degli strumenti gerarchici**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Esplora soluzioni | Struttura ad albero gerarchica che visualizza un elenco di documenti contenuti in progetti, file esterni ed elementi della soluzione. La visualizzazione degli elementi all'interno dei progetti è definita dal pacchetto proprietario del tipo di progetto (ad esempio, i tipi basati su riferimenti, basati su directory o in modalità mista). |
| Visualizzazione classi | Struttura ad albero gerarchica delle classi e dei vari elementi nel working set di documenti, indipendentemente dai file stessi. |
| Esplora server | Struttura ad albero gerarchica che consente di visualizzare tutti i server e le connessioni dati nella soluzione. |
| Struttura documento | Struttura gerarchica del documento attivo. |

**Finestre degli strumenti griglia**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Proprietà | Griglia che visualizza un elenco di proprietà per l'oggetto selezionato, insieme ai selezionatori di valore per modificare tali proprietà. |
| Elenco attività | Griglia che consente all'utente di creare, modificare o eliminare attività e commenti. |

**Finestre degli strumenti di contenuto**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Help | Una finestra che consente agli utenti di accedere a diversi metodi per ottenere informazioni dalla guida, da "ricerca per categorie" video nei forum MSDN. |
| Guida dinamica | Una finestra degli strumenti che Visualizza i collegamenti agli argomenti della guida applicabili alla selezione corrente. |
| Visualizzatore oggetti | Un frame a due colonne con un elenco di componenti oggetto gerarchici nel riquadro sinistro e le proprietà e i metodi dell'oggetto nella colonna a destra. |

**Finestre degli strumenti di dialogo**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Find | Finestra di dialogo che consente all'utente di trovare o trovare e sostituire in vari file all'interno della soluzione. |
| Ricerca avanzata | Finestra di dialogo che consente all'utente di trovare o trovare e sostituire in vari file all'interno della soluzione. |

**Altre finestre degli strumenti**

::: moniker range="vs-2017"

| Finestra degli strumenti | Funzione |
| --- | --- |
| Casella degli strumenti | Finestra degli strumenti utilizzata per archiviare gli elementi che verranno rilasciati nelle aree di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione. |
| Pagina iniziale | Il portale dell'utente per Visual Studio, con accesso ai feed di notizie per gli sviluppatori, alla guida di Visual Studio e ai progetti recenti. Gli utenti possono anche creare pagine iniziali personalizzate copiando il file StartPage. XAML dalla directory dei \" file di programma di Visual Studio Common7\IDE\StartPages alla cartella StartPages nella directory dei documenti di Visual Studio, quindi modificando il codice XAML manualmente o aprendolo in Visual Studio o in un altro editor di codice. |

::: moniker-end

::: moniker range=">=vs-2019"

| Finestra degli strumenti | Funzione |
| --- | --- |
| Casella degli strumenti | Finestra degli strumenti utilizzata per archiviare gli elementi che verranno rilasciati nelle aree di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione. |

::: moniker-end

**Finestre degli strumenti del debugger**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Auto ||
| Immediato ||
| Output | La finestra output può essere usata ogni volta che sono presenti eventi testuali o lo stato da dichiarare. |
| Memoria ||
| Punti di interruzione ||
| In esecuzione ||
| Documenti ||
| Stack di chiamate ||
| Variabili locali ||
| Orologi ||
| Disassembly ||
| Registri ||
| Thread ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Convenzioni dell'editor di documenti

### <a name="document-interactions"></a>Interazioni tra documenti
Il "documento" è lo spazio più grande all'interno dell'IDE ed è il punto in cui l'utente ha in genere focalizzato l'attenzione per completare le attività, assistito da finestre degli strumenti supplementari. Gli editor di documenti rappresentano le unità di lavoro fondamentali che l'utente apre e Salva in Visual Studio. Mantengono un forte senso di selezione associato a Esplora soluzioni o ad altre finestre di gerarchia attive. L'utente deve essere in grado di puntare a una di queste finestre della gerarchia e di individuare la posizione in cui è contenuto il documento e la relativa relazione con la soluzione, il progetto o un altro oggetto radice fornito da un pacchetto di Visual Studio.

Per la modifica di documenti è necessaria un'esperienza utente coerente. Per consentire all'utente di concentrarsi sull'attività invece che sulla gestione della finestra e sulla ricerca dei comandi, selezionare una strategia di visualizzazione dei documenti più adatta alle attività dell'utente per la modifica del tipo di documento.

#### <a name="common-interactions-for-the-document-well"></a>Interazioni comuni per l'area dei documenti

- Mantenere un modello di interazione coerente nel **nuovo file** e nelle esperienze di **apertura dei file** comuni.

- Aggiornare la funzionalità correlata nei menu e nelle finestre correlate quando si apre la finestra del documento.

- I comandi di menu sono integrati in modo appropriato in menu comuni come i menu **modifica**, **formato** e **Visualizza** . Se è disponibile una quantità sostanziale di comandi specializzati, è possibile creare un nuovo menu. Questo nuovo menu dovrebbe essere visibile solo quando il documento ha lo stato attivo.

- Una barra degli strumenti incorporata può essere posizionata nella parte superiore dell'editor. È preferibile disporre di una barra degli strumenti separata visualizzata all'esterno dell'editor.

- Mantenere sempre una selezione nella finestra della gerarchia attiva Esplora soluzioni o simile.

- Facendo doppio clic su un documento nel Esplora soluzioni sarà necessario eseguire la stessa azione di **Apri**.

- Se è possibile utilizzare più di un editor in un tipo di documento, l'utente deve essere in grado di eseguire l'override o di reimpostare l'azione predefinita per un determinato tipo di documento utilizzando la finestra di dialogo **Apri con** facendo clic con il pulsante destro del mouse sul file e selezionando **Apri con** dal menu di scelta rapida.

- Non compilare una procedura guidata in un documento.

### <a name="user-expectations-for-specific-document-types"></a>Aspettative degli utenti per tipi di documento specifici
Esistono diversi tipi di base di editor di documenti e ognuno presenta un set di interazioni coerenti con altri tipi dello stesso tipo.

- **Editor basato su testo:** editor di codice, file di log

- **Area di progettazione:** Progettazione form WPF, Windows Form

- **Editor in stile finestra di dialogo:** Progettazione manifesto, proprietà progetto

- **Progettazione modelli:** progettazione flussi di lavoro, codemap, diagramma dell'architettura, progressione

Sono disponibili anche diversi tipi non di editor che usano l'area documento. Sebbene non modifichino i documenti, devono seguire le interazioni standard per le finestre dei documenti.

- **Report:** Rapporto IntelliTrace, report Hyper-V, report Profiler

- **Dashboard:** Hub di diagnostica

#### <a name="text-based-editors"></a>Editor basati su testo

- Il documento fa parte del modello di scheda Anteprima, consentendo di visualizzare in anteprima il documento senza aprirlo.

- La struttura del documento può essere rappresentata all'interno di una finestra degli strumenti complementare, ad esempio una struttura documento.

- IntelliSense (se appropriato) si comporterà in modo coerente con altri editor di codice.

- I popup o l'interfaccia utente per l'accesso facilitato seguono stili e modelli simili per un'interfaccia utente simile esistente, ad esempio CodeLens.

- I messaggi relativi allo stato dei documenti verranno presentati in un controllo barra informazioni nella parte superiore del documento o nella barra di stato.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere e dei colori utilizzando una pagina di **opzioni > strumenti** , ovvero la pagina tipi di carattere e colori condivisi o uno specifico per l'editor.

#### <a name="design-surfaces"></a>Aree di progettazione

- Una finestra di progettazione vuota deve avere una filigrana sulla superficie che indica come iniziare.

- I meccanismi di cambio di visualizzazione seguiranno i modelli esistenti, ad esempio fare doppio clic per aprire un editor di codice o schede all'interno della finestra del documento, consentendo l'interazione con entrambi i riquadri.

- L'aggiunta di elementi all'area di progettazione deve essere eseguita tramite la casella degli strumenti, a meno che non sia necessaria una finestra degli strumenti molto specifica.

- Gli elementi sull'area seguiranno un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono solo comandi specifici del documento, non comandi comuni, ad esempio **Save**.

#### <a name="dialog-style-editors"></a>Editor di tipo finestra di dialogo

- Il layout del controllo deve seguire le normali convenzioni di layout del dialogo.

- Le schede all'interno dell'editor non devono corrispondere all'aspetto delle schede del documento, devono corrispondere a uno dei due stili di tabulazione interni consentiti.

- Gli utenti devono essere in grado di interagire con i controlli usando solo la tastiera. attivando l'editor e la tabulazione tramite i controlli o usando i tasti di scelta standard.

- La finestra di progettazione deve utilizzare il modello di salvataggio comune. Non è necessario che i pulsanti di salvataggio o di commit complessivi siano posizionati sull'area, anche se è possibile che altri pulsanti siano appropriati.

#### <a name="model-designers"></a>Progettazione modelli

- Una finestra di progettazione vuota deve avere una filigrana sulla superficie che indica come iniziare.

- L'aggiunta di elementi all'area di progettazione deve essere eseguita tramite la casella degli strumenti.

- Gli elementi sull'area seguiranno un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono solo comandi specifici del documento, non comandi comuni, ad esempio **Save**.

- Una legenda può essere visualizzata sulla superficie, indicativa o una filigrana.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere/colori utilizzando una pagina di **opzioni > strumenti** , ovvero la pagina tipi di carattere e colori condivisi o uno specifico per l'editor.

#### <a name="reports"></a>Report

- I report sono in genere di sola informazione e non partecipano al modello Save. Tuttavia, possono includere interazioni quali collegamenti ad altre informazioni o sezioni rilevanti che si espandono e comprimono.

- La maggior parte dei comandi sulla superficie deve essere collegamenti ipertestuali, non pulsanti.

- Il layout deve includere un'intestazione e seguire le linee guida standard per il layout del report.

#### <a name="dashboards"></a>Dashboard

- I dashboard non dispongono di un modello di interazione, ma servono come mezzo per offrire un'ampia gamma di altri strumenti.

- Non partecipano al modello Save.

- Gli utenti devono essere in grado di interagire con i controlli usando solo la tastiera, attivando l'editor e la tabulazione tramite i controlli o usando i tasti di scelta standard.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Finestre

### <a name="introduction"></a>Introduzione
Le finestre di dialogo in Visual Studio in genere supportano un'unità discreta del lavoro dell'utente e quindi vengono rilasciate.

Se è stato determinato che è necessaria una finestra di dialogo, sono disponibili tre opzioni, in ordine di preferenza:

1. Integrare le funzionalità in una delle finestre di dialogo condivise in Visual Studio.

2. Creare una finestra di dialogo personalizzata usando un modello trovato in una finestra di dialogo simile esistente.

3. Creare una nuova finestra di dialogo, seguendo le linee guida per l'interazione e il layout.

Questa sezione descrive come scegliere il modello di finestra di dialogo corretto nei flussi di lavoro di Visual Studio e le convenzioni comuni per la progettazione di finestre di dialogo.

### <a name="themes"></a>Temi
Le finestre di dialogo in Visual Studio seguono uno dei due stili di base:

#### <a name="standard-unthemed"></a>Standard (non con tema)
La maggior parte delle finestre di dialogo sono finestre di dialogo di utilità standard e devono essere disattivate. Non ricreare modelli di controlli comuni o tentare di creare pulsanti o controlli "moderni" stilizzati. I controlli e l'aspetto di Chrome seguono le [linee guida standard di interazione desktop di Windows per le finestre di dialogo](/windows/desktop/uxguide/win-dialog-box)

#### <a name="themed"></a>Tema
Le finestre di dialogo speciali "Signature" possono essere a tema. Le finestre di dialogo con tema hanno un aspetto distinto, che include anche alcuni modelli di interazione speciali associati allo stile. Tema la finestra di dialogo solo se soddisfa i requisiti seguenti:

- La finestra di dialogo è un'esperienza comune che verrà visualizzata e usata spesso o da molti utenti, ad esempio la finestra di dialogo **nuovo progetto** .

- La finestra di dialogo contiene elementi principali del marchio del prodotto, ad esempio la finestra di dialogo **Impostazioni account** .

- La finestra di dialogo viene visualizzata come parte integrante di un flusso più ampio che include altre finestre di dialogo con tema, ad esempio la finestra di dialogo **Aggiungi servizio connesso** .

- La finestra di dialogo è una parte importante di un'esperienza che svolge un ruolo strategico nella promozione o nella differenziazione di una versione del prodotto.

Quando si crea una finestra di dialogo con tema, usare i colori dell'ambiente appropriati e seguire il layout e i modelli di interazione corretti. Vedere [layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

### <a name="dialog-design"></a>Progettazione finestra di dialogo
Le finestre di dialogo ben progettate prendono in considerazione gli elementi seguenti:

- Attività utente supportata

- Stile del testo della finestra di dialogo, lingua e terminologia

- Opzioni di controllo e convenzioni dell'interfaccia utente

- Specifica del layout visivo e allineamento del controllo

- Accesso da tastiera

#### <a name="content-organization"></a>Organizzazione del contenuto
Prendere in considerazione le differenze tra questi tipi di dialogo di base:

- [Finestre di dialogo semplici](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentano controlli in un'unica finestra modale. La presentazione potrebbe includere varianti di pattern di controllo complessi, tra cui una selezione dei campi o una barra delle icone.

- Le [finestre di dialogo sovrapposte](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) vengono usate per sfruttare al meglio la proprietà dello schermo quando una singola parte dell'interfaccia utente è costituita da più gruppi di controlli. I raggruppamenti della finestra di dialogo sono "sovrapposti" tramite i controlli struttura a schede, i controlli elenco di navigazione o i pulsanti in modo che l'utente possa scegliere il raggruppamento da visualizzare in un determinato momento.

- Le [procedure guidate](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) sono utili per indirizzare l'utente tramite una sequenza logica di passaggi verso il completamento di un'attività. Nei pannelli sequenziali viene offerta una serie di opzioni, a volte introducendo flussi di lavoro diversi ("Branch") dipendenti da una scelta effettuata nel pannello precedente.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Finestre di dialogo semplici
Una semplice finestra di dialogo è una presentazione di controlli in un'unica finestra modale. Questa presentazione potrebbe includere varianti di pattern di controllo complessi, ad esempio un selettore di campo. Per le finestre di dialogo semplici, seguire il layout generale standard e qualsiasi layout specifico necessario per raggruppamenti di controlli complessi.

![>creare una chiave con nome sicuro è un esempio di una semplice finestra di dialogo in Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Crea chiave con nome sicuro è un esempio di una semplice finestra di dialogo in Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Finestre di dialogo sovrapposte
Le finestre di dialogo sovrapposte includono schede, dashboard e alberi incorporati. Vengono usati per ottimizzare le proprietà quando sono disponibili più gruppi di controlli in un'unica parte dell'interfaccia utente. I raggruppamenti sono sovrapposti in modo che l'utente possa scegliere il raggruppamento da visualizzare in qualsiasi momento.

Nel caso più semplice, il meccanismo di cambio tra i raggruppamenti è un controllo struttura a schede. Sono disponibili diverse alternative. Per informazioni su come scegliere lo stile più appropriato, vedere priorità e livelli.

La finestra di dialogo **&gt; Opzioni strumenti** è un esempio di finestra di dialogo sovrapposta che utilizza un albero incorporato:

![Strumenti > opzioni è un esempio di finestra di dialogo sovrapposta in Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Strumenti > opzioni è un esempio di finestra di dialogo sovrapposta in Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Procedure guidate
Le procedure guidate sono utili per indirizzare l'utente tramite una sequenza logica di passaggi nel completamento di un'attività. Nei pannelli sequenziali viene offerta una serie di opzioni e l'utente deve continuare a eseguire ogni passaggio prima di procedere al successivo. Quando sono disponibili impostazioni predefinite sufficienti, il pulsante **fine** è abilitato.

 Le procedure guidate modali vengono utilizzate per le attività che:

- Contenere la diramazione, in cui vengono offerti percorsi diversi a seconda delle scelte utente

- Contenere le dipendenze tra i passaggi, in cui i passaggi successivi dipendono dall'input dell'utente dei passaggi precedenti

- Sono sufficientemente complesse che l'interfaccia utente deve essere usata per spiegare le scelte offerte e i possibili risultati in ogni passaggio

- Sono transazionali, che richiedono il completamento di un set di passaggi prima di eseguire il commit delle modifiche

### <a name="common-conventions"></a>Convenzioni comuni
Per ottenere una progettazione e una funzionalità ottimali con le finestre di dialogo, attenersi alle convenzioni seguenti relative alle dimensioni, alla posizione, agli standard, alla configurazione e all'allineamento dei controlli, testo dell'interfaccia utente, barre del titolo, pulsanti di controllo e chiavi di accesso.

Per le linee guida specifiche del layout, vedere [layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Dimensione
Le finestre di dialogo devono rientrare in una risoluzione dello schermo di almeno 1024x768 e le dimensioni iniziali della finestra di dialogo non devono superare 900x700 pixel. Le finestre di dialogo possono essere ridimensionabili, ma non è un requisito.

Sono disponibili due consigli per le finestre di dialogo ridimensionabili:

1. Che una dimensione minima è definita per la finestra di dialogo che verrà ottimizzata per il set di controlli senza ritaglio e per adattarsi a una ragionevole crescita della localizzazione.

2. Che le dimensioni ridimensionate dall'utente vengano mantenute da sessione a sessione. Se, ad esempio, l'utente ridimensiona una finestra di dialogo al 150%, il successivo avvio della finestra di dialogo verrà visualizzato al 150%.

#### <a name="position"></a>Posizione
Al primo avvio, le finestre di dialogo devono essere visualizzate al centro all'interno dell'IDE. L'ultima posizione delle finestre di dialogo non ridimensionabili non deve essere persistente, quindi verrà visualizzata al centro in seguito a lanci successivi.

Per le finestre di dialogo ridimensionabili, le dimensioni devono essere rese permanente all'avvio successivo. Per le finestre di dialogo modali ridimensionabili, non è necessario che la posizione sia persistente. La visualizzazione centrata all'interno dell'IDE impedisce la possibilità che la finestra di dialogo venga visualizzata in una posizione imprevedibile o inutilizzabile quando la configurazione di visualizzazione dell'utente è cambiata.

Per le finestre di dialogo non modali che possono essere riposizionate, la posizione dell'utente deve essere mantenuta nei lanci successivi, perché la finestra di dialogo può essere usata spesso come parte integrante di un flusso di lavoro più grande.

Quando le finestre di dialogo devono generare altre finestre di dialogo, la finestra di dialogo in primo piano dovrebbe propagarsi verso destra e verso il basso rispetto all'elemento padre, in modo che sia ovvio per l'utente che è stato spostato in una nuova posizione.

#### <a name="modality"></a>Modalità
Il metodo modale indica che gli utenti devono completare o annullare la finestra di dialogo prima di continuare. Poiché le finestre di dialogo modali impediscono all'utente di interagire con altre parti dell'ambiente, il flusso attività della funzionalità dovrebbe utilizzarle nel modo più sporadico possibile. Quando è necessaria un'operazione modale, Visual Studio include diverse finestre di dialogo condivise in cui è possibile integrare le funzionalità. Se è necessario creare una nuova finestra di dialogo, seguire il modello di interazione di una finestra di dialogo esistente con funzionalità simili.

Quando gli utenti devono eseguire due attività contemporaneamente, ad esempio **trova** e **Sostituisci** durante la scrittura di nuovo codice, la finestra di dialogo non deve essere modale, in modo che l'utente possa passare facilmente da una all'altra. Visual Studio USA in genere le finestre degli strumenti per questo tipo di attività collegata di supporto dell'editor.

#### <a name="control-configuration"></a>Configurazione del controllo
Essere coerenti con le configurazioni di controllo esistenti che eseguono la stessa operazione in Visual Studio.

#### <a name="title-bars"></a>Barre del titolo

- Il testo nella barra del titolo deve riflettere il nome del comando che lo ha avviato.

- Nelle barre del titolo della finestra di dialogo non deve essere utilizzata alcuna icona. Nei casi in cui il sistema ne richiede uno, usare il logo di Visual Studio.

- Nelle finestre di dialogo non devono essere presenti pulsanti Riduci a icona o Ingrandisci.

- I pulsanti della guida nella barra del titolo sono stati deprecati. Non aggiungerli alle nuove finestre di dialogo. Quando sono presenti, devono avviare un argomento della Guida concettualmente pertinente per l'attività.

  ![Specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Specifiche delle linee guida per le barre del titolo nelle finestre di dialogo di Visual Studio

#### <a name="control-buttons"></a>Pulsanti di controllo
In generale, i pulsanti **OK**, **Annulla** e **Guida** devono essere disposti orizzontalmente nell'angolo inferiore destro della finestra di dialogo. Lo stack verticale alternativo è consentito se una finestra di dialogo contiene diversi altri pulsanti nella parte inferiore della finestra di dialogo che potrebbero presentare confusione visiva con i pulsanti di controllo.

![Configurazioni accettabili per i pulsanti di controllo nelle finestre di dialogo di Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurazioni accettabili per i pulsanti di controllo nelle finestre di dialogo di Visual Studio

La finestra di dialogo deve includere un pulsante di controllo predefinito. Per determinare il comando migliore da usare come predefinito, scegliere una delle opzioni seguenti (elencate in ordine di precedenza):

- Scegliere il comando più sicuro e sicuro come valore predefinito. Ciò significa che la scelta del comando più probabile impedisce la perdita di dati ed evita l'accesso non intenzionale al sistema.

- Se la perdita di dati e la sicurezza non sono fattori, scegliere il comando predefinito in base a praticità. Includere il comando più probabile come valore predefinito migliorerà il flusso di lavoro dell'utente quando la finestra di dialogo supporta attività frequenti o ripetitive.

Evitare di scegliere un'azione distruttiva in modo permanente per il comando predefinito. Se è presente un comando di questo tipo, scegliere un comando più sicuro come predefinito.

#### <a name="access-keys"></a>Chiavi di accesso
Non usare chiavi di accesso per i pulsanti **OK**, **Annulla** o **Guida** . Per impostazione predefinita, questi pulsanti vengono mappati ai tasti di scelta rapida:

| Nome pulsante | Tasti di scelta rapida |
| --- | --- |
| OK | Immettere |
| Annulla | ESC |
| Guida | F1 |

#### <a name="imagery"></a>Immagini
Utilizzare le immagini sporadicamente nelle finestre di dialogo. Non usare icone grandi nelle finestre di dialogo semplicemente per usare spazio. Usare le immagini solo se rappresentano una parte importante della trasmissione del messaggio all'utente, ad esempio le icone di avviso o le animazioni di stato.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Assegnazione di priorità e livelli

#### <a name="prioritizing-your-ui"></a>Assegnazione delle priorità all'interfaccia utente
Potrebbe essere necessario portare determinati elementi dell'interfaccia utente in Forefront e inserire opzioni e comportamenti più avanzati, inclusi i comandi nascosti, nelle finestre di dialogo. È possibile usare le funzionalità di uso comune in Forefront facendo spazio al suo interno e rendendola visibile per impostazione predefinita nell'interfaccia utente con un'etichetta di testo quando viene visualizzata la finestra di dialogo.

#### <a name="layering-your-ui"></a>Sovrapposizione dell'interfaccia utente
Se è stata rilevata la necessità di una finestra di dialogo, ma la funzionalità correlata che si desidera presentare all'utente supera quella che può essere visualizzata in una semplice finestra di dialogo, è necessario eseguire il layer dell'interfaccia utente. I metodi di sovrapposizione più comuni usati da Visual Studio sono schede e corridoi o dashboard. In alcuni casi, le aree che possono espandersi e comprimere potrebbero essere appropriate. L'interfaccia utente adattiva non è in genere consigliata in Visual Studio.

Sono disponibili vantaggi e svantaggi per diversi metodi di sovrapposizione dell'interfaccia utente tramite controlli di tipo tabulazione. Esaminare l'elenco seguente per assicurarsi di scegliere una tecnica di sovrapposizione adatta alla propria situazione.

##### <a name="tabbing"></a>Tabulazione

| Meccanismo di cambio | Vantaggi e uso appropriato | Svantaggi e utilizzo non appropriato |
| --- | --- | --- |
| Controllo Tab | Raggruppare logicamente le pagine della finestra di dialogo in set correlati<br /><br />Utile per meno di cinque (o il numero di schede che si adattano a una riga nella finestra di dialogo) pagine di controlli correlati nella finestra di dialogo<br /><br />Le etichette delle schede devono essere brevi: una o due parole che possono identificare facilmente il contenuto<br /><br />Uno stile di finestra di dialogo di sistema comune<br /><br />Esempio: **&gt; Proprietà elemento di Esplora file** | La creazione di etichette brevi descrittive può essere difficile<br /><br />In genere non si ridimensionano le ultime cinque schede in un'unica finestra di dialogo<br /><br />Non appropriato se si dispone di un numero eccessivo di schede per una riga (usare una tecnica di sovrapposizione alternativa)<br /><br />Non estendibile |
| Navigazione nell'intestazione laterale | Semplice dispositivo di cambio che può contenere più categorie rispetto alle schede<br /><br />Elenco semplice di categorie (nessuna gerarchia)<br /><br />Estendibilità<br /><br />Esempio: **Customize... &gt; Aggiungi comando** | Non è un valido utilizzo dello spazio orizzontale se sono presenti meno di tre gruppi<br /><br />L'attività potrebbe essere più adatta a un elenco a discesa |
| Controllo Tree | Consente le categorie illimitate<br /><br />Consente il raggruppamento e/o la gerarchia di categorie<br /><br />Estendibilità<br /><br />Esempio: **&gt; Opzioni degli strumenti** | Le gerarchie molto annidate possono causare un eccessivo scorrimento orizzontale<br /><br />Visual Studio presenta una sovrabbondanza di visualizzazioni ad albero |
| Procedura guidata | Consente di completare le attività tramite la guida dell'utente tramite passaggi sequenziali basati su attività: la procedura guidata rappresenta un'attività di alto livello e i singoli pannelli rappresentano le sottoattività necessarie per completare l'attività complessiva<br /><br />Utile quando l'attività supera i limiti dell'interfaccia utente, come quando l'utente altrimenti dovrà utilizzare più editor e finestre degli strumenti per completare l'attività<br /><br />Utile quando l'attività richiede la diramazione<br /><br />Utile quando l'attività contiene dipendenze tra i passaggi<br /><br />Utile quando in una finestra di dialogo è possibile presentare diverse attività simili con un fork di decisione per ridurre il numero di finestre di dialogo simili | Non appropriato per le attività che non richiedono un flusso di lavoro sequenziale<br /><br />Gli utenti possono diventare sopraffatti e confusi da una procedura guidata con troppi passaggi<br /><br />Le procedure guidate hanno un patrimonio di schermo intrinsecamente limitato |

##### <a name="hallways-or-dashboards"></a>Corridoi o dashboard
I corridoi e i dashboard sono finestre di dialogo o pannelli che funge da punti di avvio per altre finestre di dialogo e finestre. Il "corridoio" ben progettato presenta immediatamente solo le opzioni, i comandi e le impostazioni più comuni, consentendo all'utente di eseguire immediatamente le attività più comuni. Analogamente a un corridoio reale che fornisce le porte per accedere alle sale dietro di esse, qui l'interfaccia utente meno comune viene raccolta in "chat room" separate (spesso altre finestre di dialogo) delle funzionalità correlate a cui è possibile accedere dal corridoio principale.

In alternativa, un'interfaccia utente che offre tutte le funzionalità disponibili in una singola raccolta invece di effettuare il refactoring delle funzionalità meno comuni in posizioni separate è semplicemente un dashboard.

![Concetto di corridoio per l'esposizione di un'interfaccia utente aggiuntiva in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concetto di corridoio per l'esposizione di un'interfaccia utente aggiuntiva in Outlook

##### <a name="adaptive-ui"></a>Interfaccia utente adattiva
Mostrare o nascondere l'interfaccia utente in base all'utilizzo o all'esperienza autosegnalata di un utente è un altro modo per presentare l'interfaccia utente necessaria per nascondere altre parti. Questa operazione non è consigliata in Visual Studio, perché gli algoritmi per decidere quando visualizzare o nascondere l'interfaccia utente possono essere complessi e le regole sono sempre errate per alcuni set di case.

## <a name="projects"></a><a name="BKMK_Projects"></a> Progetti

### <a name="projects-in-the-solution-explorer"></a>Progetti nel Esplora soluzioni
La maggior parte dei progetti è classificata come basata su riferimento, basata su directory o mista. Tutti e tre i tipi di progetto sono supportati simultaneamente nel Esplora soluzioni. La radice dell'esperienza utente nell'utilizzo dei progetti si verifica all'interno di questa finestra. Sebbene i diversi nodi di progetto siano progetti di tipo riferimento, directory o in modalità mista, è necessario applicare un modello di interazione comune come punto di partenza prima di divergere in modelli utente specifici del progetto.

I progetti devono sempre:

- Supporto della possibilità di aggiungere cartelle di progetto per organizzare il contenuto del progetto

- Mantenere un modello coerente per la persistenza del progetto

I progetti devono inoltre mantenere modelli di interazione coerenti per:

- Rimozione di elementi di progetto

- Salvataggio di documenti

- Modifica delle proprietà del progetto

- Modifica del progetto in una visualizzazione alternativa

- Operazioni di trascinamento della selezione

### <a name="drag-and-drop-interaction-model"></a>Modello di interazione con trascinamento della selezione
I progetti vengono in genere classificati come basati sui riferimenti (in grado di salvare in modo permanente solo i riferimenti agli elementi di progetto nell'archiviazione), basati su directory (in grado di salvare in modo permanente solo gli elementi di progetto archiviati fisicamente all'interno della gerarchia di un progetto) oppure misti (in grado di salvare in modo permanente i riferimenti o gli L'IDE supporta contemporaneamente tutti e tre i tipi di progetti all'interno dell' **Esplora soluzioni**.

Dal punto di vista del trascinamento della selezione, è consigliabile applicare le seguenti caratteristiche a ogni tipo di progetto all'interno dell' **Esplora soluzioni**:

- **Progetto basato su riferimento:** Il punto chiave è che il progetto viene trascinato in un riferimento a un elemento nell'archivio. Quando un progetto basato su riferimento funge da origine per un'operazione di spostamento, deve rimuovere solo il riferimento all'elemento dal progetto. L'elemento non deve essere effettivamente eliminato dal disco rigido. Quando un progetto basato su riferimento funge da destinazione per un'operazione di spostamento o copia, deve aggiungere un riferimento all'elemento di origine originale senza creare una copia privata dell'elemento.

- **Progetto basato su directory:** Dal punto di vista del trascinamento della selezione, il progetto viene trascinato intorno all'elemento fisico anziché a un riferimento. Quando un progetto basato su directory funge da origine per un'operazione di spostamento, deve terminare l'eliminazione dell'elemento fisico dal disco rigido e la relativa rimozione dal progetto. Quando un progetto basato su directory funge da destinazione per un'operazione di spostamento o copia, deve creare una copia dell'elemento di origine nel percorso di destinazione.

- **Progetto di destinazione mista:** Dal punto di vista del trascinamento, il comportamento di questo tipo di progetto è basato sulla natura dell'elemento trascinato, ovvero un riferimento a un elemento nell'archivio o l'elemento stesso. Il comportamento corretto per i riferimenti e gli elementi fisici è descritto in precedenza.

Se nel **Esplora soluzioni** fosse presente un solo tipo di progetto, le operazioni di trascinamento della selezione sarebbero semplici. Poiché ogni sistema di progetto è in grado di definire il proprio comportamento di trascinamento della selezione, è necessario seguire alcune linee guida (basate sul comportamento di trascinamento della selezione di Esplora risorse) per garantire un'esperienza utente prevedibile:

- Un'operazione di trascinamento non modificata nel **Esplora soluzioni** (quando non vengono mantenuti i tasti CTRL e MAIUSC) dovrebbe causare un'operazione di spostamento.

- L'operazione di trascinamento del cambio deve anche causare un'operazione di spostamento.

- L'operazione di trascinamento deve comportare l'esecuzione di un'operazione di copia.

- I sistemi di progetto misti e basati sui riferimenti supportano la nozione di aggiunta di un collegamento (o riferimento) all'elemento di origine. Quando questi progetti sono la destinazione di un'operazione di trascinamento della selezione (quando si tiene premuto **CTRL + MAIUSC** ), dovrebbe essere visualizzato un riferimento all'elemento aggiunto al progetto

Non tutte le operazioni di trascinamento della selezione sono sensate tra le combinazioni di progetti basati su riferimenti, basati su directory e misti. In particolare, è problematico far finta di consentire un'operazione di spostamento tra un progetto di origine basato su directory e un progetto di destinazione basato su riferimenti perché il progetto basato su directory di origine dovrà eliminare l'elemento di origine al termine dello spostamento. Il progetto basato sul riferimento di destinazione dovrebbe quindi finire con un riferimento a un elemento eliminato.

È anche preferibile fingersi di consentire un'operazione di copia tra questi tipi di progetti perché il progetto basato su riferimento di destinazione non deve creare una copia indipendente dell'elemento di origine. Analogamente, il trascinamento di CTRL + MAIUSC in un progetto di destinazione basato su directory non deve essere consentito perché un progetto basato su directory non è in grado di salvare in modo permanente i riferimenti. Nei casi in cui l'operazione di trascinamento della selezione non è supportata, l'IDE deve impedire l'eliminazione e visualizzare all'utente il cursore no-drop (visualizzato nella tabella del puntatore riportata di seguito).

Per implementare correttamente il comportamento di trascinamento della selezione, è necessario che il progetto di origine del trascinamento comunichi la propria natura al progetto di destinazione. Ad esempio, è un riferimento o basato su directory? Queste informazioni sono indicate dal formato degli Appunti offerto dall'origine. Come origine di un'operazione di copia del trascinamento (o di copia degli Appunti), un progetto deve offrire `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` rispettivamente, a seconda che il progetto sia basato sul riferimento o sulla directory. Entrambi questi formati hanno lo stesso contenuto dati, che è simile al formato di Windows, `CF_HDROP` ad eccezione del fatto che gli elenchi di stringhe, anziché i nomi file, sono un `NULL` elenco di stringhe con terminazione doppia `Projref` (restituito da `IVsSolution::GetProjrefOfItem` o a seconda dei `::GetProjrefOfProject` casi).

Come destinazione di un'operazione DROP (o Incolla appunti), un progetto deve accettare sia `CF_VSREFPROJECTITEMS` che `CF_VSSTGPROJECTITEMS` , sebbene la gestione esatta dell'operazione di trascinamento della selezione varia a seconda della natura del progetto di destinazione e del progetto di origine. Il progetto di origine dichiara la natura in base al fatto che offra `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` . La destinazione del trascinamento comprende la propria natura e pertanto dispone di informazioni sufficienti per prendere decisioni in merito alla possibilità di eseguire uno spostamento, una copia o un collegamento. L'utente modifica anche le operazioni di trascinamento della selezione che devono essere eseguite premendo CTRL, MAIUSC o tasti CTRL e MAIUSC. È importante per l'obiettivo di rilascio indicare correttamente quale operazione verrà eseguita in anticipo nei relativi `DragEnter` `DragOver` metodi e. Il **Esplora soluzioni** sa automaticamente se il progetto di origine e il progetto di destinazione sono lo stesso progetto.

Il trascinamento di elementi di progetto tra istanze di Visual Studio (ad esempio, da un'istanza di devenv.exe a un'altra) non è supportato in modo specifico. Il **Esplora soluzioni** Disabilita anche direttamente questa.

L'utente deve sempre essere in grado di determinare l'effetto di un'operazione di trascinamento della selezione selezionando un elemento, trascinandolo nel percorso di destinazione e osservando quale dei seguenti puntatori del mouse viene visualizzato prima che l'elemento venga eliminato:

| Puntatore del mouse | Comando | Descrizione |
| :---: | --- | --- |
| ![Icona di "nessun rilascio" del mouse](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Nessuna eliminazione | Non è possibile eliminare l'elemento nella posizione specificata. |
| ![Icona "copia" del mouse](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copia | L'elemento verrà copiato nel percorso di destinazione. |
| ![Icona "spostamento" del mouse](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Sposta | L'elemento verrà spostato nel percorso di destinazione. |
| ![Icona "aggiungi riferimento" del mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Aggiungi riferimento | Un riferimento all'elemento selezionato verrà aggiunto al percorso di destinazione. |

#### <a name="reference-based-projects"></a>Progetti basati su riferimento
 Nella tabella seguente sono riepilogate le operazioni di trascinamento della selezione, nonché le operazioni Taglia/copia/incolla, che devono essere eseguite in base alla natura dell'elemento di origine e dei tasti di modifica premuti per i progetti di destinazione basati su riferimento:

| Modificatore | Category | Elemento di origine: riferimento/collegamento | Elemento di origine: elemento fisico o file system ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Nessun modificatore | Azione | Sposta | Collegamento |
| Nessun modificatore | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Nessun modificatore | Source (Sorgente) | Elimina il riferimento all'elemento originale | Mantiene l'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Maiusc + trascina | Azione | Sposta | Nessuna eliminazione |
| Maiusc + trascina | Destinazione | Aggiunge un riferimento all'elemento originale | Nessuna eliminazione |
| Maiusc + trascina | Source (Sorgente) | Elimina il riferimento all'elemento originale | Nessuna eliminazione |
| Maiusc + trascina | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | Nessuna eliminazione |
| Ctrl + trascina | Azione | Copia | Nessuna eliminazione |
| Ctrl + trascina | Destinazione | Aggiunge un riferimento all'elemento originale | Nessuna eliminazione |
| Ctrl + trascina | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Nessuna eliminazione |
| Ctrl + trascina | Risultato | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | Nessuna eliminazione |
| Ctrl + Maiusc + trascina | Azione | Collegamento | Collegamento |
| Ctrl + Maiusc + trascina | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Ctrl + Maiusc + trascina | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| Ctrl + Maiusc + trascina | Risultato | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Ctrl + Maiusc + trascina | Nota | Come il comportamento di trascinamento della selezione per i collegamenti in Esplora risorse. ||
| Taglia/incolla | Azione | Sposta | Collegamento |
| Taglia/incolla | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Taglia/incolla | Source (Sorgente) | Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale |
| Taglia/incolla | Risultato | L'elemento rimane nella posizione originale nella risorsa di archiviazione | L'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Copia/incolla | Azione | Copia | Collegamento |
| Copia/incolla | Source (Sorgente) | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Copia/incolla | Risultato | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| Copia/incolla | Azione | L'elemento rimane nella posizione originale nella risorsa di archiviazione | L'elemento rimane nella posizione originale nella risorsa di archiviazione |

#### <a name="directory-based-projects"></a>Progetti basati su directory
Nella tabella seguente sono riepilogate le operazioni di trascinamento della selezione, nonché le operazioni Taglia/copia/incolla, che devono essere eseguite in base alla natura dell'elemento di origine e dei tasti di modifica premuti per i progetti di destinazione basati su directory:

| Modificatore | Category | Elemento di origine: riferimento/collegamento | Elemento di origine: elemento fisico o file system ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Nessun modificatore | Azione | Sposta | Sposta |
| Nessun modificatore | Destinazione | Copia l'elemento nella posizione di destinazione | Copia l'elemento nella posizione di destinazione |
| Nessun modificatore | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina il riferimento all'elemento originale |
| Maiusc + trascina | Azione | Sposta | Sposta |
| Maiusc + trascina | Destinazione | Copia l'elemento nella posizione di destinazione | Copia l'elemento nella posizione di destinazione |
| Maiusc + trascina | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dal percorso originale |
| Maiusc + trascina | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Ctrl + trascina | Azione | Copia | Copia |
| Ctrl + trascina | Destinazione | Copia l'elemento nella posizione di destinazione | Copia l'elemento nella posizione di destinazione |
| Ctrl + trascina | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene il riferimento all'elemento originale |
| Ctrl + trascina | Risultato | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Ctrl + Maiusc + trascina | | Nessuna eliminazione | Nessuna eliminazione |
| Taglia/incolla | Azione | Sposta | Sposta |
| Taglia/incolla | Destinazione | Copia l'elemento nella posizione di destinazione | Copia l'elemento nella posizione di destinazione |
| Taglia/incolla | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dal percorso originale |
| Taglia/incolla | Risultato | L'elemento rimane nella posizione originale nella risorsa di archiviazione | L'elemento è stato eliminato dal percorso originale nella risorsa di archiviazione |
| Copia/incolla | Azione | Copia | Copia |
| Copia/incolla | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nella posizione di destinazione |
| Copia/incolla | Source (Sorgente) | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copia/incolla | Risultato | L'elemento rimane nella posizione originale nella risorsa di archiviazione | L'elemento rimane nello spazio di archiviazione nella posizione originale |

#### <a name="mixed-target-projects"></a>Progetti di destinazione mista
Nella tabella seguente sono riepilogate le operazioni di trascinamento della selezione, nonché le operazioni Taglia/copia/incolla, che devono essere eseguite in base alla natura dell'elemento di origine e dei tasti di modifica premuti per i progetti di destinazione mista:

| Modificatore | Category | Elemento di origine: riferimento/collegamento | Elemento di origine: elemento fisico o file system ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Nessun modificatore | Azione | Sposta | Sposta |
| Nessun modificatore | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nella posizione di destinazione |
| Nessun modificatore | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina il riferimento all'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento viene eliminato dal percorso originale nella risorsa di archiviazione |
| Maiusc + trascina | Azione | Sposta | Sposta |
| Maiusc + trascina | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nella posizione di destinazione |
| Maiusc + trascina | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dal percorso originale |
| Maiusc + trascina | Risultato | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento viene eliminato dal percorso originale nella risorsa di archiviazione |
| Ctrl + trascina | Azione | Copia | Copia |
| Ctrl + trascina | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nella posizione di destinazione |
| Ctrl + trascina | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| Ctrl + trascina | Risultato | `DROPEFFECT_ COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_ COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Ctrl + Maiusc + trascina | Azione | Collegamento | Collegamento |
| Ctrl + Maiusc + trascina | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento di origine originale |
| Ctrl + Maiusc + trascina | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| Ctrl + Maiusc + trascina | Risultato | `DROPEFFECT_ LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione | `DROPEFFECT_ LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella risorsa di archiviazione |
| Taglia/incolla | Azione | Sposta | Sposta |
| Taglia/incolla | Destinazione | Copia l'elemento nella posizione di destinazione | Copia l'elemento nella posizione di destinazione |
| Taglia/incolla | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dal percorso originale |
| Taglia/incolla | Risultato | L'elemento rimane nella posizione originale nella risorsa di archiviazione | L'elemento è stato eliminato dal percorso originale nella risorsa di archiviazione |
| Copia/incolla | Azione | Copia | Copia |
| Copia/incolla | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nella posizione di destinazione |
| Copia/incolla | Source (Sorgente) | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copia/incolla | Risultato | L'elemento rimane nella posizione originale nella risorsa di archiviazione | L'elemento rimane nella posizione originale nella risorsa di archiviazione |

Questi dettagli devono essere presi in considerazione durante l'implementazione del trascinamento nella **Esplora soluzioni**:

- Progettazione per più scenari di selezione.

- I nomi file (percorso completo) devono essere univoci nel progetto di destinazione. in caso contrario, il rilascio non dovrebbe essere consentito.

- I nomi di cartella devono essere univoci (senza distinzione tra maiuscole e minuscole) al livello che vengono eliminati.

- Esistono differenze di comportamento tra i file aperti o chiusi al momento del trascinamento (non menzionati negli scenari precedenti).

- I file di primo livello hanno un comportamento leggermente diverso rispetto ai file nelle cartelle.

Un altro problema da tenere presente è la modalità di gestione delle operazioni di spostamento sugli elementi con finestre di progettazione o editor aperti. Il comportamento previsto è il seguente (si applica a tutti i tipi di progetto):

1. Se la finestra di progettazione o l'Editor aperto non contiene modifiche non salvate, la finestra Editor/finestra di progettazione verrà chiusa automaticamente.

2. Se nella finestra di progettazione/editor aperto sono presenti modifiche non salvate, l'origine del trascinamento deve attendere l'esecuzione del rilascio, quindi chiedere all'utente di salvare le modifiche di cui non è stato eseguito il commit nei documenti aperti prima di chiudere la finestra con un prompt simile al seguente:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Ciò consente all'utente di salvare il lavoro in corso prima che la destinazione ne faccia le copie. `IVsHierarchyDropDataSource2::OnBeforeDropNotify`Per abilitare questa gestione è stato aggiunto un nuovo metodo.

La destinazione copierà quindi lo stato dell'elemento come si trova nell'archivio (escluse le modifiche non salvate nell'editor se l'utente ha scelto **No**). Dopo che la destinazione ha completato la copia (in `IVsHierarchyDropDataSource::Drop` ), all'origine viene data la possibilità di completare la parte relativa all'eliminazione dell'operazione di spostamento (in `IVsHierarchyDropDataSource::OnDropNotify` ).

Eventuali editor con modifiche non salvate devono essere lasciati aperti. Per i documenti con modifiche non salvate, significa che la parte di copia dell'operazione di spostamento verrà eseguita, ma la parte relativa all'eliminazione verrà interrotta. In uno scenario a selezione multipla quando l'utente sceglie No, i documenti con modifiche non salvate non devono essere chiusi o rimossi, ma quelli senza modifiche **non** salvate devono essere chiusi e rimossi.
