---
title: Modelli di applicazione per Visual Studio | Microsoft Docs
description: Informazioni sulla differenza tra le finestre dei documenti, le finestre degli strumenti e le finestre di dialogo non modali, inclusi i modelli di utilizzo delle finestre per le nuove funzionalità per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fe65ecd124f8c76bf10fb9e9c1f157b50af5b0ce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069611"
---
# <a name="application-patterns-for-visual-studio"></a>Modelli delle applicazioni per Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interazioni tra finestre

### <a name="overview"></a>Panoramica
I due tipi di finestra principali usati Visual Studio editor di documenti e finestre degli strumenti. Rari, ma possibili, sono dialoghe non modali di grandi dimensioni. Anche se nella shell sono tutti non modali, i relativi modelli sono fondamentalmente diversi. Questa sezione illustra la differenza tra finestre del documento, finestre degli strumenti e finestre di dialogo non modali. I modelli di dialogo modali sono trattati in [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Confronto dei modelli di utilizzo delle finestre
**Le finestre dei** documenti vengono quasi sempre visualizzate all'interno dell'area del documento. In questo modo l'editor di documenti ha una "fase centrale" in cui disporre le finestre degli strumenti supplementari.

Una **finestra degli strumenti** viene spesso visualizzata come finestra separata e più piccola compressa sul bordo dell'IDE. Può essere visibile, nascosto o nascosto automaticamente. Tuttavia, a volte le finestre degli strumenti vengono presentate all'interno del documento, deselezionando la **proprietà Finestra/Ancoraggio** nella finestra. Ciò comporta più proprietà immobiliari, ma anche una decisione di progettazione comune: quando si tenta di eseguire l'integrazione in Visual Studio, è necessario decidere se la funzionalità deve visualizzare una finestra degli strumenti o una finestra del documento.

**Le finestre di dialogo non** modali sono sconsigliate Visual Studio. La maggior parte dei dialoghe non modali è, per definizione, finestre degli strumenti mobili e deve essere implementata in questo modo. Le finestre di dialogo non modali sono consentite nei casi in cui le dimensioni di una normale finestra degli strumenti ancorata al lato della shell sarebbero troppo limitanti. Sono consentiti anche nei casi in cui l'utente potrebbe spostare la finestra di dialogo in un monitoraggio secondario.

Valutare con attenzione il tipo di contenitore necessario. Le considerazioni sui modelli di utilizzo comuni per la progettazione dell'interfaccia utente sono riportate nella tabella seguente.

||Finestra del documento|Finestra degli strumenti|Finestra di dialogo non modabile|
|-|---------------------|-----------------|---------------------|
| **Position** | Sempre posizionato all'interno dell'area del documento e non viene ancorato intorno ai bordi dell'IDE. Può essere "ritirato" in modo che sia mobile separatamente dalla shell principale. | In genere è ancorata a schede intorno ai bordi dell'IDE, ma può essere personalizzata per essere mobile, nascosta automaticamente (non bloccata) o ancorata all'interno dell'area del documento.|Finestra mobile di grandi dimensioni separata dall'IDE. |
| **Modello di commit** | *Commit ritardato*<br /><br /> Per salvare i dati in un documento, l'utente deve eseguire il comando Salva file, Salva con nome o **Salva tutto.** **&gt;** Una finestra del documento ha il concetto di "dirtied" dei dati al suo interno e quindi viene eseguito il commit in uno dei comandi di salvataggio. Quando si chiude una finestra del documento, tutto il contenuto viene salvato su disco o perso. | *Commit immediato*<br /><br /> Non è presente alcun modello di salvataggio. Per le finestre degli strumenti di controllo che sono utili per la modifica di un file, il file deve essere aperto nell'editor o nella finestra di progettazione attiva e l'editor o la finestra di progettazione è proprietaria del salvataggio. | *Commit ritardato o immediato*<br /><br /> In genere, un dialogo non modabile di grandi dimensioni richiede un'azione per eseguire il commit delle modifiche e consente un'operazione "Annulla", che esegue il rollback di tutte le modifiche apportate all'interno della sessione del dialogo.  In questo modo un dialogo non modabile viene differenziato da una finestra degli strumenti in cui le finestre degli strumenti hanno sempre un modello di commit immediato. |
| **Visibilità** | *Apri/Crea (file) e Chiudi*<br /><br /> L'apertura di una finestra del documento avviene tramite l'apertura di un documento esistente o l'uso di un modello per creare un nuovo documento. Non è presente alcun comando \<specific editor> "Apri". | *Nascondere e visualizzare*<br /><br /> Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate. I contenuti e gli stati all'interno della finestra degli strumenti vengono mantenuti indipendentemente dalla visualizzazione o dalla visualizzazione. Le finestre degli strumenti a istanze multipla possono essere chiuse e nascoste. Quando una finestra degli strumenti a più istanze viene chiusa, il contenuto e lo stato all'interno della finestra degli strumenti vengono eliminati. | *Avviato da un comando*<br /><br /> I dialoghe vengono avviati da un comando basato su attività. |
| **Istanze** | *Istanze a più istanze*<br /><br /> Diversi editor possono essere aperti contemporaneamente e modificando file diversi, mentre alcuni editor consentono anche di aprire **&gt;** lo stesso file in più editor (usando il comando Finestra nuova finestra).<br /><br /> Un singolo editor può modificare uno o più file contemporaneamente (Project Designer). | *A istanza singola o multipla*<br /><br /> Il contenuto cambia per riflettere il contesto (come nel Visualizzatore proprietà) o per eseguire il push dello stato attivo/contesto in altre finestre (Elenco attività, Esplora soluzioni).<br /><br /> Sia le finestre degli strumenti a istanza singola che a istanza multipla devono essere associate alla finestra del documento attiva, a meno che non vi sia un motivo interessante per non. | *Istanza singola* |
| **esempi** | **Editor di testo,** ad esempio l'editor di codice<br /><br /> **Superfici di progettazione,** ad esempio una finestra di progettazione form o un'area di modellazione<br /><br /> **Layout dei controlli simili alle finestre di dialogo,** ad esempio Progettazione manifesti | Il **Esplora soluzioni** fornisce una soluzione e i progetti contenuti all'interno della soluzione<br /><br /> Il **Esplora server** offre una visualizzazione gerarchica dei server e delle connessioni dati che l'utente sceglie di aprire nella finestra. L'apertura di un oggetto dalla gerarchia del database, ad esempio una query, apre una finestra del documento e consente all'utente di modificare la query.<br /><br /> Nel **Visualizzatore proprietà vengono** visualizzate le proprietà per l'oggetto selezionato in una finestra del documento o in un'altra finestra degli strumenti. Le proprietà vengono presentate in una visualizzazione griglia gerarchica o in controlli complessi simili a finestre di dialogo e consentono all'utente di impostare i valori per tali proprietà. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Finestre degli strumenti

### <a name="overview"></a>Panoramica
Le finestre degli strumenti supportano il lavoro dell'utente che si verifica nelle finestre dei documenti. Possono essere usati per visualizzare una gerarchia che rappresenta un oggetto radice fondamentale che Visual Studio e può modificare.

Quando si considera una nuova finestra degli strumenti nell'IDE, gli autori devono:

- Usare finestre degli strumenti esistenti appropriate per le attività e non crearne di nuove con funzionalità simili. Le nuove finestre degli strumenti devono essere create solo se offrono uno "strumento" o una funzionalità significativamente diversa che non può essere integrata in una finestra simile o trasformando una finestra esistente in un hub pivot.

- Usare una barra dei comandi standard, se necessario, nella parte superiore della finestra degli strumenti.

- Essere coerenti con i modelli già presenti in altre finestre degli strumenti per la presentazione del controllo e la navigazione tramite tastiera.

- Essere coerenti con la presentazione dei controlli in altre finestre degli strumenti.

- Rendere visibili automaticamente le finestre degli strumenti specifiche del documento quando possibile, in modo che vengano visualizzate solo quando viene attivato il documento padre.

- Assicurarsi che il contenuto della finestra sia esplorabile dalla tastiera (supporta i tasti di direzione).

#### <a name="tool-window-states"></a>Stati della finestra degli strumenti
Visual Studio le finestre degli strumenti hanno stati diversi, alcuni dei quali sono attivati dall'utente (ad esempio la funzionalità nascondi automaticamente). Altri stati, ad esempio la visibilità automatica, consentono di visualizzare le finestre degli strumenti nel contesto corretto e di nascondersi quando non è necessario. In totale sono presenti cinque stati della finestra degli strumenti.

- **Le finestre degli** strumenti ancorate o bloccate possono essere collegate a uno dei quattro lati dell'area del documento. L'icona della puntina da disegno viene visualizzata nella barra del titolo della finestra degli strumenti. La finestra degli strumenti può essere ancorata orizzontalmente o verticalmente lungo il bordo della shell e altre finestre degli strumenti e può anche essere collegata a schede.

- **Le finestre degli strumenti** nascoste automaticamente vengono sbloccate. La finestra può scorrere fuori dalla vista, lasciando una scheda (con il nome della finestra degli strumenti e la relativa icona) sul bordo dell'area del documento. La finestra degli strumenti scorre quando un utente passa il puntatore del mouse sulla scheda.

- **Le finestre degli strumenti visibili** automaticamente vengono visualizzate quando viene avviata un'altra parte dell'interfaccia utente, ad esempio un editor, o si ottiene lo stato attivo.

- **Le finestre** degli strumenti mobili passano al passaggio del mouse all'esterno dell'IDE. Ciò è utile per le configurazioni con più monitor.

- **Le finestre degli strumenti del** documento a schede possono essere ancorate all'interno dell'area del documento. Ciò è utile per le finestre degli strumenti di grandi dimensioni, come il Visualizzatore oggetti, che necessitano di più spazio rispetto all'ancoraggio ai bordi del frame.

![Stati della finestra degli strumenti in Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Stati della finestra degli strumenti in Visual Studio

#### <a name="single-instance-and-multi-instance"></a>A istanza singola e a istanza multipla
Le finestre degli strumenti sono a istanza singola o a istanza multipla. Alcune finestre degli strumenti a istanza singola potrebbero essere associate alla finestra del documento attiva, mentre le finestre degli strumenti a istanze multipla potrebbero non essere associate. Le finestre degli strumenti a istanze multipla rispondono al **comando Finestra &gt; nuova** finestra creando una nuova istanza della finestra. L'immagine seguente illustra una finestra degli strumenti che abilita il comando Nuova finestra quando un'istanza della finestra è attiva:

![Finestra degli strumenti che abilita il comando "Nuova finestra" quando un'istanza della finestra è attiva](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Finestra degli strumenti che abilita il comando "Nuova finestra" quando un'istanza della finestra è attiva

Le finestre degli strumenti a istanza singola possono essere nascoste o visualizzate, mentre le finestre degli strumenti a istanze multipla possono essere chiuse e nascoste. Tutte le finestre degli strumenti possono essere ancorate, collegate a schede, mobili o impostate come finestra figlio dell'interfaccia Multiple-Document (MDI) (simile a una finestra del documento). Tutte le finestre degli strumenti devono rispondere ai comandi di gestione delle finestre appropriati nel menu Finestra:

![Comandi di gestione delle finestre nel menu Visual Studio finestra](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandi di gestione delle finestre nel menu Visual Studio finestra

#### <a name="document-specific-tool-windows"></a>Finestre degli strumenti specifiche del documento
Alcune finestre degli strumenti sono progettate per essere modificate in base a un determinato tipo di documento. Queste finestre vengono continuamente aggiornate per riflettere le funzionalità applicabili alla finestra del documento attivo nell'IDE.

Esempi di finestre degli strumenti il cui contenuto cambia in base all'editor selezionato sono la casella degli strumenti e la struttura del documento. Queste finestre mostrano una filigrana quando un editor ha lo stato attivo che non offre contesto alla finestra.

#### <a name="navigable-list-tool-windows"></a>Finestre degli strumenti elenco esplorabili
Alcune finestre degli strumenti visualizzano un elenco di elementi esplorabili con cui l'utente può interagire. In questo tipo di finestra devono essere sempre presenti commenti e suggerimenti per l'elemento corrente nell'elenco, anche se la finestra è inattiva. L'elenco deve rispondere ai **comandi GoToNextLocation** e **GoToPrevLocation** modificando anche l'elemento attualmente selezionato nella finestra

Esempi di finestre degli strumenti elenco esplorabili sono la Esplora soluzioni e la finestra Risultati ricerca.

### <a name="tool-window-types"></a>Tipi di finestra degli strumenti

#### <a name="common-tool-windows-and-their-functions"></a>Finestre degli strumenti comuni e relative funzioni

**Finestre degli strumenti gerarchici**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Esplora soluzioni | Albero gerarchico che visualizza un elenco di documenti contenuti in progetti, file esterni ed elementi della soluzione. La visualizzazione degli elementi all'interno dei progetti è definita dal pacchetto proprietario del tipo di progetto, ad esempio tipi basati su riferimento, basati su directory o in modalità mista. |
| Visualizzazione classi | Albero gerarchico delle classi e dei vari elementi nella working set di documenti, indipendentemente dai file stessi. |
| Esplora server | Albero gerarchico che visualizza tutti i server e le connessioni dati nella soluzione. |
| Struttura documento | Struttura gerarchica del documento attivo. |

**Finestre degli strumenti griglia**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Proprietà | Griglia che visualizza un elenco di proprietà per l'oggetto selezionato, insieme ai selettori di valori per modificare tali proprietà. |
| Elenco attività | Griglia che consente all'utente di creare/modificare/eliminare attività e commenti. |

**Finestre degli strumenti del contenuto**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Help | Finestra che consente agli utenti di accedere a vari metodi per ottenere assistenza, da "How Do I?" video nei forum MSDN. |
| Guida dinamica | Finestra degli strumenti che visualizza i collegamenti agli argomenti della Guida applicabili alla selezione corrente. |
| Visualizzatore oggetti | Set di frame a due colonne con un elenco di componenti di oggetti gerarchici nel riquadro sinistro e le proprietà e i metodi dell'oggetto nella colonna di destra. |

**Finestre degli strumenti della finestra di dialogo**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Find | Finestra di dialogo che consente all'utente di trovare o trovare e sostituire in vari file all'interno della soluzione. |
| Ricerca avanzata | Finestra di dialogo che consente all'utente di trovare o trovare e sostituire in vari file all'interno della soluzione. |

**Altre finestre degli strumenti**

::: moniker range="vs-2017"

| Finestra degli strumenti | Funzione |
| --- | --- |
| Casella degli strumenti | Finestra degli strumenti utilizzata per archiviare gli elementi che verranno rilasciati nelle superfici di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione. |
| Pagina iniziale | Portale dell'utente per Visual Studio, con accesso a feed di notizie per sviluppatori, Visual Studio guida e progetti recenti. Gli utenti possono anche creare pagine di avvio personalizzate copiando il file StartPage.xaml dalla directory dei file di programma "Common7\IDE\StartPages Visual Studio alla cartella StartPages nella directory dei documenti di Visual Studio e quindi modificando manualmente il codice XAML o aprendolo in Visual Studio o in un \" altro editor di codice. |

::: moniker-end

::: moniker range=">=vs-2019"

| Finestra degli strumenti | Funzione |
| --- | --- |
| Casella degli strumenti | Finestra degli strumenti utilizzata per archiviare gli elementi che verranno rilasciati nelle superfici di progettazione, fornendo un'origine di trascinamento coerente per tutte le finestre di progettazione. |

::: moniker-end

**Finestre degli strumenti del debugger**

| Finestra degli strumenti | Funzione |
| --- | --- |
| Auto ||
| Immediato ||
| Output | La finestra di output può essere usata ogni volta che si dispone di eventi testuali o di stato da dichiarare. |
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

### <a name="document-interactions"></a>Interazioni con i documenti
Il "document well" è lo spazio più grande all'interno dell'IDE ed è il punto in cui l'utente ha in genere concentrato la propria attenzione per completare le attività, assistiti da finestre degli strumenti supplementari. Gli editor di documenti rappresentano le unità di lavoro fondamentali che l'utente apre e salva Visual Studio. Mantengono un forte senso di selezione associato a Esplora soluzioni o ad altre finestre della gerarchia attive. L'utente deve essere in grado di puntare a una di queste finestre della gerarchia e sapere dove è contenuto il documento e la relativa relazione con la soluzione, il progetto o un altro oggetto radice fornito da un Visual Studio pacchetto.

La modifica dei documenti richiede un'esperienza utente coerente. Per consentire all'utente di concentrarsi sull'attività a portata di mano anziché sui comandi di gestione e ricerca delle finestre, selezionare una strategia di visualizzazione del documento più adatta alle attività dell'utente per la modifica del tipo di documento.

#### <a name="common-interactions-for-the-document-well"></a>Interazioni comuni per l'oggetto del documento

- Mantenere un modello di interazione coerente nelle esperienze **comuni Nuovo file** e Apri **file.**

- Aggiornare le funzionalità correlate nelle finestre e nei menu correlati all'apertura della finestra del documento.

- I comandi di menu sono integrati in modo appropriato nei menu **comuni,** ad esempio i menu **Modifica,** Formato **e** Visualizza. Se è disponibile una notevole quantità di comandi specializzati, è possibile creare un nuovo menu. Questo nuovo menu deve essere visibile solo quando il documento ha lo stato attivo.

- Una barra degli strumenti incorporata può essere posizionata nella parte superiore dell'editor. È preferibile avere una barra degli strumenti separata che viene visualizzata all'esterno dell'editor.

- Mantenere sempre una selezione nella finestra Esplora soluzioni gerarchia attiva o simile.

- Facendo doppio clic su un documento nel Esplora soluzioni dovrebbe essere eseguita la stessa azione di **Apri**.

- Se è possibile usare più editor per un tipo di documento, l'utente deve essere in  grado di eseguire l'override o reimpostare l'azione predefinita per un determinato tipo di documento usando la finestra di dialogo Apri con facendo clic con il pulsante destro del mouse sul file e scegliendo **Apri** con dal menu di scelta rapida.

- Non creare una procedura guidata in un documento.

### <a name="user-expectations-for-specific-document-types"></a>Aspettative degli utenti per tipi di documenti specifici
Esistono diversi tipi di base di editor di documenti e ognuno ha un set di interazioni coerenti con altri dello stesso tipo.

- **Editor basato su testo: editor** di codice, file di log

- **Area di progettazione:** Progettazione form WPF, Windows form

- **Editor in stile finestra di dialogo:** Progettazione manifesto, proprietà del progetto

- **Progettazione modelli: Progettazione** flussi di lavoro, mappa codici, diagramma dell'architettura, progressione

Esistono anche diversi tipi non editor che usano il documento. Anche se non modificano i documenti, devono seguire le interazioni standard per le finestre dei documenti.

- **Report:** Report di IntelliTrace, report Hyper-V, report del profiler

- **Dashboard:** Hub di diagnostica

#### <a name="text-based-editors"></a>Editor basati su testo

- Il documento fa parte del modello di scheda di anteprima, consentendo di visualizzare in anteprima il documento senza aprirlo.

- La struttura del documento può essere rappresentata all'interno di una finestra degli strumenti complementare, ad esempio una struttura del documento.

- IntelliSense (se appropriato) si comporterà in modo coerente con altri editor di codice.

- I popup o l'interfaccia utente assistiva seguono stili e modelli simili per l'interfaccia utente simile esistente, ad esempio CodeLens.

- I messaggi relativi allo stato del documento verranno visualizzati in un controllo barra informazioni nella parte superiore del documento o nella barra di stato.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere e dei colori usando una pagina Strumenti **> Opzioni,** la pagina Tipi di carattere e colori condivisi o una specifica dell'editor.

#### <a name="design-surfaces"></a>Superfici di progettazione

- Una finestra di progettazione vuota deve avere una filigrana sulla superficie che indica come iniziare.

- I meccanismi di cambio di visualizzazione seguiranno i modelli esistenti, ad esempio il doppio clic per aprire un editor di codice o le schede all'interno della finestra del documento, consentendo l'interazione con entrambi i riquadri.

- L'aggiunta di elementi all'area di progettazione deve essere eseguita tramite la casella degli strumenti, a meno che non sia necessaria una finestra degli strumenti altamente specifica.

- Gli elementi sulla superficie seguiranno un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono solo comandi specifici del documento, non comandi comuni, ad esempio **Salva**.

#### <a name="dialog-style-editors"></a>Editor di tipo finestra di dialogo

- Il layout dei controlli deve seguire le normali convenzioni di layout della finestra di dialogo.

- Le schede all'interno dell'editor non devono corrispondere all'aspetto delle schede del documento, ma devono corrispondere a uno dei due stili di tabulazione interni consentiti.

- Gli utenti devono poter interagire con i controlli usando solo la tastiera. attivando l'editor e la tabulazione tramite i controlli o usando i mnemonici standard.

- La finestra di progettazione deve usare il modello di salvataggio comune. Non devono essere posizionati pulsanti di salvataggio o commit complessivi sulla superficie, anche se altri pulsanti potrebbero essere appropriati.

#### <a name="model-designers"></a>Finestre di progettazione dei modelli

- Una finestra di progettazione vuota deve avere una filigrana sulla superficie che indica come iniziare.

- L'aggiunta di elementi all'area di progettazione deve essere eseguita tramite la casella degli strumenti.

- Gli elementi sulla superficie seguiranno un modello di selezione coerente.

- Le barre degli strumenti incorporate contengono solo comandi specifici del documento, non comandi comuni, ad esempio **Salva**.

- Sulla superficie può essere visualizzata una legenda, indicativa o una filigrana.

- L'utente deve essere in grado di personalizzare l'aspetto dei tipi di carattere/colori usando una pagina Strumenti **> Opzioni,** la pagina Tipi di carattere e colori condivisi o una specifica dell'editor.

#### <a name="reports"></a>Report

- I report sono in genere solo informazioni e non partecipano al modello Di salvataggio. Tuttavia, possono includere l'interazione, ad esempio collegamenti ad altre informazioni rilevanti o sezioni che si espandono e comprimino.

- La maggior parte dei comandi sulla superficie devono essere collegamenti ipertestuali, non pulsanti.

- Il layout deve includere un'intestazione e seguire le linee guida standard per il layout del report.

#### <a name="dashboards"></a>Dashboard

- I dashboard non hanno un modello di interazione, ma servono come mezzo per offrire un'ampia gamma di altri strumenti.

- Non partecipano al modello Di salvataggio.

- Gli utenti devono poter interagire con i controlli solo tramite tastiera, attivando l'editor e la tabulazione tramite i controlli o usando i tasti di scelta rapida standard.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Finestre

### <a name="introduction"></a>Introduzione
I dialog Visual Studio in genere devono supportare un'unità discreta del lavoro dell'utente e quindi essere ignorati.

Se si è determinato che è necessario un dialogo, sono disponibili tre opzioni, in ordine di preferenza:

1. Integrare le funzionalità in una delle finestre di dialogo condivise in Visual Studio.

2. Creare un dialogo personalizzato usando un modello trovato in un dialogo simile esistente.

3. Creare una nuova finestra di dialogo seguendo le linee guida per l'interazione e il layout.

Questa sezione descrive come scegliere il modello di dialogo corretto all'interno Visual Studio flussi di lavoro e le convenzioni comuni per la progettazione dei dialoghe.

### <a name="themes"></a>Temi
Le finestre di dialogo Visual Studio uno dei due stili di base seguenti:

#### <a name="standard-unthemed"></a>Standard (senzathemed)
La maggior parte dei dialoghe è un dialogo di utilità standard e deve essere inedito. Non ridefinire i controlli comuni o tentare di creare pulsanti o controlli "moderni" stilizzati. I controlli e l'aspetto del colore [seguono Windows linee guida di interazione del desktop per le finestre di dialogo](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Tema
Le finestre di dialogo speciali per la "firma" possono essere a base di testo. I dialoghe a colori hanno un aspetto distinto, che include anche alcuni modelli di interazione speciali associati allo stile. Creare un tema per la finestra di dialogo solo se soddisfa questi requisiti:

- La finestra di dialogo è un'esperienza comune che verrà visualizzata e usata spesso o da molti utenti,ad esempio la finestra di **dialogo Project** nuova finestra di dialogo.

- La finestra di dialogo contiene elementi principali del marchio del prodotto,ad esempio la finestra **di dialogo Account Impostazioni.**

- La finestra di dialogo viene visualizzata come parte integrante di un flusso più ampio che include altre finestre di dialogo tr(ad esempio, la finestra di **dialogo Aggiungi servizio** connesso).

- Il dialogo è una parte importante di un'esperienza che svolge un ruolo strategico nella promozione o nella differenziazione di una versione del prodotto.

Quando si crea un dialogo a tema, usare i colori dell'ambiente appropriati e seguire i modelli di layout e interazione corretti. Vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

### <a name="dialog-design"></a>Progettazione della finestra di dialogo
Le finestre di dialogo ben progettate prendono in considerazione gli elementi seguenti:

- Attività utente supportata

- Stile, lingua e terminologia del testo della finestra di dialogo

- Scelta dei controlli e convenzioni dell'interfaccia utente

- Specifica del layout visivo e allineamento dei controlli

- Accesso da tastiera

#### <a name="content-organization"></a>Organizzazione del contenuto
Considerare le differenze tra questi tipi di finestre di dialogo di base:

- [I dialoghe semplici](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) presentano i controlli in una singola finestra modale. La presentazione può includere variazioni di pattern di controllo complessi, tra cui un selettore di campo o una barra delle icone.

- [Le finestre di dialogo a](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) più livelli vengono usate per ottenere il massimo dall'immobiliare dello schermo quando una singola parte dell'interfaccia utente include più gruppi di controlli. I raggruppamenti della finestra di dialogo vengono "raggruppati" tramite controlli struttura a schede, controlli elenco di navigazione o pulsanti in modo che l'utente possa scegliere il raggruppamento da visualizzare in un determinato momento.

- [Le procedure](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) guidate sono utili per indirizzare l'utente attraverso una sequenza logica di passaggi verso il completamento di un'attività. Nei pannelli sequenziali è disponibile una serie di scelte, talvolta introducendo flussi di lavoro diversi ("rami") in base a una scelta effettuata nel pannello precedente.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Dialoghe semplici
Un dialogo semplice è una presentazione di controlli in una singola finestra modale. Questa presentazione può includere variazioni di pattern di controllo complessi, ad esempio un controllo selezione campi. Per i dialoghe semplici, seguire il layout generale standard e qualsiasi layout specifico necessario per i raggruppamenti di controlli complessi.

![>Create Strong Name Key (Crea chiave con nome sicuro) è un esempio di finestra di dialogo semplice Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Creare una chiave con nome sicuro è un esempio di una semplice finestra di dialogo Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Finestre di dialogo a più livelli
Le finestre di dialogo a più livelli includono schede, dashboard e alberi incorporati. Vengono usati per ottimizzare lo spazio quando sono disponibili più gruppi di controlli in un'unica parte dell'interfaccia utente. I raggruppamenti sono a livelli in modo che l'utente possa scegliere quale raggruppamento visualizzare in qualsiasi momento.

Nel caso più semplice, il meccanismo per passare da un raggruppamento all'altro è un controllo struttura a schede. Sono disponibili diverse alternative. Per informazioni su come scegliere lo stile più appropriato, vedere Assegnazione di priorità e livelli.

La **finestra di dialogo &gt; Opzioni** strumenti è un esempio di finestra di dialogo a più livelli che usa un albero incorporato:

![Strumenti > opzioni è un esempio di finestra di dialogo a più livelli in Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Strumenti > opzioni è un esempio di finestra di dialogo a più livelli in Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Procedure guidate
Le procedure guidate sono utili per indirizzare l'utente attraverso una sequenza logica di passaggi nel completamento di un'attività. Nei pannelli sequenziali è disponibile una serie di opzioni e l'utente deve continuare con ogni passaggio prima di procedere al passaggio successivo. Quando sono disponibili valori predefiniti sufficienti, il **pulsante** Fine è abilitato.

 Le procedure guidate modali vengono usate per le attività che:

- Contenere la diramazione, in cui vengono offerti percorsi diversi a seconda delle scelte dell'utente

- Contengono dipendenze tra i passaggi, in cui i passaggi successivi dipendono dall'input dell'utente dai passaggi precedenti

- Sono sufficientemente complesse che l'interfaccia utente deve essere usata per spiegare le scelte offerte e i possibili risultati in ogni passaggio

- Sono transazionali e richiedono il completamento completo di un set di passaggi prima del commit delle modifiche

### <a name="common-conventions"></a>Convenzioni comuni
Per ottenere una progettazione e una funzionalità ottimali con le finestre di dialogo, seguire queste convenzioni per dimensioni, posizione, standard, configurazione e allineamento dei controlli, testo dell'interfaccia utente, barre del titolo, pulsanti di controllo e tasti di scelta.

Per le linee guida specifiche del layout, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Dimensione
Le finestre di dialogo devono rientrare in una risoluzione dello schermo minima di 1024x768 e le dimensioni iniziali della finestra di dialogo non devono superare 900x700 pixel. I dialoghe possono essere ridimensionabili, ma non è un requisito.

Sono disponibili due raccomandazioni per i dialognti ridimensionabili:

1. Una dimensione minima è definita per la finestra di dialogo che verrà ottimizzata per il set di controlli senza ritaglio e adattata per supportare una crescita ragionevole della localizzazione.

2. Le dimensioni ridimensionate dall'utente vengono mantenute da una sessione all'altra. Ad esempio, se l'utente ridimensiona un dialogo al 150%, un successivo avvio del dialogo verrà visualizzato al 150%.

#### <a name="position"></a>Posizione
Le finestre di dialogo devono essere visualizzate al centro all'interno dell'IDE al primo avvio. Non è necessario salvare in modo permanente l'ultima posizione dei dialognti non ridimensionabili, quindi verranno visualizzati centrati sugli avvii successivi.

Per i dialognti ridimensionabili, le dimensioni devono essere mantenute nei successivi avvii. Per le finestre di dialogo modali ridimensionabili, non è necessario che la posizione sia persistente. La visualizzazione al centro all'interno dell'IDE impedisce la possibilità che la finestra di dialogo venga visualizzata in una posizione imprevedibile o inutilizzabile quando viene modificata la configurazione di visualizzazione dell'utente.

Per le finestre di dialogo non modali che possono essere riposizionate, la posizione dell'utente deve essere mantenuta nei successivi avvii, perché il dialogo potrebbe essere usato di frequente come parte integrante di un flusso di lavoro più ampio.

Quando le finestre di dialogo devono generare altri dialoghe, il dialogo in primo piano deve propagarsi verso destra e verso il basso dall'elemento padre in modo che sia evidente all'utente che si è spostati in una nuova posizione.

#### <a name="modality"></a>Modalità
Essere modali significa che gli utenti devono completare o annullare la finestra di dialogo prima di continuare. Poiché le finestre di dialogo modali bloccano l'interazione dell'utente con altre parti dell'ambiente, il flusso di attività della funzionalità deve usarle il più possibile. Quando è necessaria un'operazione modale, Visual Studio dispone di una serie di finestre di dialogo condivise in cui è possibile integrare le funzionalità. Se è necessario creare un nuovo dialogo, seguire il modello di interazione di un dialogo esistente con funzionalità simili.

Quando gli utenti devono eseguire due  attività  contemporaneamente, ad esempio Trova e sostituisci durante la scrittura di nuovo codice, la finestra di dialogo deve essere non modale in modo che l'utente possa passare facilmente da un'attività all'altro. Visual Studio usa in genere finestre degli strumenti per questo tipo di attività collegata che supporta l'editor.

#### <a name="control-configuration"></a>Controllare la configurazione
Essere coerenti con le configurazioni di controllo esistenti che ese hanno lo stesso risultato in Visual Studio.

#### <a name="title-bars"></a>Barre del titolo

- Il testo nella barra del titolo deve riflettere il nome del comando che lo ha avviato.

- Non è necessario usare alcuna icona nelle barre del titolo della finestra di dialogo. Nei casi in cui il sistema ne richiede uno, usare Visual Studio logo.

- Le finestre di dialogo non devono avere pulsanti riduci a icona o ingrandisci.

- I pulsanti della Guida nella barra del titolo sono stati deprecati. Non aggiungerli a nuovi dialoghe. Quando esistono, devono avviare un argomento della Guida concettualmente rilevante per l'attività.

  ![Specifiche delle linee guida per le barre del titolo Visual Studio finestre di dialogo](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Specifiche delle linee guida per le barre del titolo Visual Studio finestre di dialogo

#### <a name="control-buttons"></a>Pulsanti di controllo
In generale, **i pulsanti OK**, Annulla e Guida devono essere disposti orizzontalmente nell'angolo inferiore destro della finestra di dialogo.   Lo stack verticale alternativo è consentito se nella parte inferiore della finestra di dialogo sono presenti diversi altri pulsanti che possono creare confusione visiva con i pulsanti di controllo.

![Configurazioni accettabili per i pulsanti di controllo Visual Studio finestre di dialogo](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurazioni accettabili per i pulsanti di controllo Visual Studio finestre di dialogo

La finestra di dialogo deve includere un pulsante di controllo predefinito. Per determinare il comando migliore da usare come predefinito, scegliere una delle opzioni seguenti (elencate in ordine di precedenza):

- Scegliere il comando più sicuro e più sicuro come impostazione predefinita. Ciò significa scegliere il comando con maggiore probabilità per impedire la perdita di dati ed evitare l'accesso non intenzionale al sistema.

- Se la perdita di dati e la sicurezza non sono fattori, scegliere il comando predefinito in base alla praticità. L'inclusione del comando più probabile come impostazione predefinita migliorerà il flusso di lavoro dell'utente quando la finestra di dialogo supporta attività frequenti o ripetitive.

Evitare di scegliere un'azione distruttiva permanente per il comando predefinito. Se è presente un comando di questo tipo, scegliere invece un comando più sicuro come predefinito.

#### <a name="access-keys"></a>Chiavi di accesso
Non usare i tasti di scelta per i **pulsanti** **OK,** Annulla **o Guida.** Per impostazione predefinita, viene eseguito il mapping di questi pulsanti ai tasti di scelta rapida:

| Nome pulsante | Tasto di scelta rapida |
| --- | --- |
| OK | Immettere |
| Annulla | ESC |
| Guida | F1 |

#### <a name="imagery"></a>Immagini
Usare le immagini con parsimonio nelle finestre di dialogo. Non usare icone grandi nelle finestre di dialogo semplicemente per usare spazio. Usare le immagini solo se sono una parte importante della trasmissione del messaggio all'utente, ad esempio icone di avviso o animazioni di stato.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Assegnazione di priorità e livelli

#### <a name="prioritizing-your-ui"></a>Assegnazione delle priorità all'interfaccia utente
Potrebbe essere necessario mettere in primo piano determinati elementi dell'interfaccia utente e inserire opzioni e comportamenti più avanzati (inclusi i comandi nascosti) nelle finestre di dialogo. Mettere in primo piano le funzionalità di uso comune facendo spazio e rendendole visibili per impostazione predefinita nell'interfaccia utente con un'etichetta di testo quando viene visualizzata la finestra di dialogo.

#### <a name="layering-your-ui"></a>Livelli dell'interfaccia utente
Se si è determinato che una finestra di dialogo è necessaria, ma la funzionalità correlata che si vuole presentare all'utente va oltre ciò che può essere visualizzato in un dialogo semplice, è necessario disporre l'interfaccia utente su più livelli. I metodi di strating più comuni Visual Studio sono schede e sale o dashboard. In alcuni casi, le aree che possono espandersi e comprimere potrebbero essere appropriate. L'interfaccia utente adattiva in genere non è consigliata in Visual Studio.

Esistono vantaggi e svantaggi dei diversi metodi di visualizzazione su più livelli dell'interfaccia utente tramite controlli simili a schede. Esaminare l'elenco seguente per assicurarsi di scegliere una tecnica di strating appropriata per la situazione specifica.

##### <a name="tabbing"></a>Tabulazione

| Meccanismo di cambio | Vantaggi e uso appropriato | Svantaggi e uso inappropriato |
| --- | --- | --- |
| Controllo Tab | Raggruppare logicamente le pagine delle finestre di dialogo in set correlati<br /><br />Utile per meno di cinque pagine (o il numero di schede che si adattano a una riga nella finestra di dialogo) di controlli correlati nella finestra di dialogo<br /><br />Le etichette delle schede devono essere brevi: una o due parole che possono identificare facilmente il contenuto<br /><br />Uno stile di dialogo di sistema comune<br /><br />Esempio: proprietà **&gt; Esplora file'elemento** | La creazione di etichette brevi descrittive può essere difficile<br /><br />In genere non vengono ridimensionate le ultime cinque schede in un'unica finestra di dialogo<br /><br />Inappropriato se sono disponibili troppe schede per una riga (usare una tecnica di layering alternativa)<br /><br />Non estendibile |
| Spostamento nella barra laterale | Dispositivo di commutazione semplice che può contenere più categorie rispetto alle schede<br /><br />Elenco semplice di categorie (nessuna gerarchia)<br /><br />Estendibilità<br /><br />Esempio: **Personalizza... &gt; Comando Aggiungi** | Non è un buon uso dello spazio orizzontale se sono presenti meno di tre gruppi<br /><br />L'attività potrebbe essere più adatta a un elenco a discesa |
| Controllo Tree | Consente categorie illimitate<br /><br />Consente il raggruppamento e/o la gerarchia di categorie<br /><br />Estendibilità<br /><br />Esempio: **Opzioni degli &gt; strumenti** | Le gerarchie annidate in modo eccessivo possono causare uno scorrimento orizzontale eccessivo<br /><br />Visual Studio ha una sovrabbondanza di visualizzazioni albero |
| Procedura guidata | Facilita il completamento delle attività guidando l'utente attraverso passaggi sequenziali basati su attività: la procedura guidata rappresenta un'attività di alto livello e i singoli pannelli rappresentano le sottoattività necessarie per completare l'attività complessiva<br /><br />Utile quando l'attività supera i limiti dell'interfaccia utente, come quando l'utente deve altrimenti usare più editor e finestre degli strumenti per completare l'attività<br /><br />Utile quando l'attività richiede la creazione di rami<br /><br />Utile quando l'attività contiene dipendenze tra i passaggi<br /><br />Utile quando più attività simili con un fork delle decisioni possono essere presentate in un dialogo per ridurre il numero di dialoghe simili diverse | Inappropriato per qualsiasi attività che non richiede un flusso di lavoro sequenziale<br /><br />Gli utenti possono essere sovraccaricati e confusi da una procedura guidata con troppi passaggi<br /><br />Le procedure guidate hanno uno spazio dello schermo intrinsecamente limitato |

##### <a name="hallways-or-dashboards"></a>Hallway o dashboard
Hallway e dashboard sono finestre di dialogo o pannelli che fungono da punti di avvio per altre finestre e finestre. Il "ingresso" ben progettato consente di visualizzare immediatamente solo le opzioni, i comandi e le impostazioni più comuni, consentendo all'utente di eseguire facilmente attività comuni. Come un ingresso reale fornisce porte per accedere alle stanze dietro di esse, qui l'interfaccia utente meno comune viene raccolta in "stanze" separate (spesso altri dialoghe) di funzionalità correlate a cui è possibile accedere dal ingresso principale.

In alternativa, un'interfaccia utente che offre tutte le funzionalità disponibili in un'unica raccolta anziché eseguire il refactoring delle funzionalità meno comuni in posizioni separate è semplicemente un dashboard.

![Concetto di Hallway per esporre un'interfaccia utente aggiuntiva in Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Concetto di Hallway per esporre un'interfaccia utente aggiuntiva in Outlook

##### <a name="adaptive-ui"></a>Interfaccia utente adattiva
Visualizzare o nascondere l'interfaccia utente in base all'utilizzo o all'esperienza segnalata dall'utente è un altro modo per presentare l'interfaccia utente necessaria nascondendo altre parti. Questa operazione non è consigliata in Visual Studio, perché gli algoritmi per decidere quando visualizzare o nascondere l'interfaccia utente possono essere difficili e le regole saranno sempre erre per alcuni set di casi.

## <a name="projects"></a><a name="BKMK_Projects"></a> Progetti

### <a name="projects-in-the-solution-explorer"></a>Progetti nella Esplora soluzioni
La maggior parte dei progetti è classificata come basata su riferimento, basata su directory o mista. Tutti e tre i tipi di progetti sono supportati contemporaneamente nel Esplora soluzioni. La radice dell'esperienza utente nell'uso dei progetti avviene all'interno di questa finestra. Anche se nodi di progetto diversi sono progetti di riferimento, directory o tipi in modalità mista, esiste un modello di interazione comune che deve essere applicato come punto di partenza prima di divergere nei modelli utente specifici del progetto.

I progetti devono sempre:

- Supportare la possibilità di aggiungere cartelle di progetto per organizzare il contenuto del progetto

- Mantenere un modello coerente per la persistenza del progetto

I progetti devono inoltre mantenere modelli di interazione coerenti per:

- Rimozione di elementi di progetto

- Salvataggio di documenti

- Project delle proprietà

- Modifica del progetto in una visualizzazione alternativa

- Operazioni di trascinamento della selezione

### <a name="drag-and-drop-interaction-model"></a>Modello di interazione con trascinamento della selezione
I progetti in genere si classificano come basati sui riferimenti (in grado di rendere persistenti solo i riferimenti agli elementi del progetto nell'archiviazione), basati su directory (in grado di rendere persistenti solo gli elementi di progetto archiviati fisicamente all'interno della gerarchia di un progetto) o misti (in grado di rendere persistenti i riferimenti o gli elementi fisici). L'IDE supporta tutti e tre i tipi di progetti contemporaneamente **all'interno Esplora soluzioni**.

Dal punto di vista del trascinamento della selezione, le caratteristiche seguenti devono essere applicate a ogni tipo di progetto all'interno **del Esplora soluzioni**:

- **Progetto basato su riferimento:** Il punto chiave è che il progetto sta trascinando un riferimento a un elemento nella memoria. Quando un progetto basato su riferimenti funge da origine per un'operazione di spostamento, deve rimuovere solo il riferimento all'elemento dal progetto. L'elemento non deve essere effettivamente eliminato dal disco rigido. Quando un progetto basato su riferimenti funge da destinazione per un'operazione di spostamento (o copia), deve aggiungere un riferimento all'elemento di origine originale senza creare una copia privata dell'elemento.

- **Progetto basato su directory:** Da un punto di vista del trascinamento della selezione, il progetto trascina l'elemento fisico anziché un riferimento. Quando un progetto basato su directory funge da origine per un'operazione di spostamento, dovrebbe eliminare l'elemento fisico dal disco rigido e rimuoverlo dal progetto. Quando un progetto basato su directory funge da destinazione per un'operazione di spostamento (o copia), deve creare una copia dell'elemento di origine nel percorso di destinazione.

- **Progetto con destinazione mista:** Dal punto di vista del trascinamento della selezione, il comportamento di questo tipo di progetto si basa sulla natura dell'elemento trascinato (un riferimento a un elemento nella risorsa di archiviazione o all'elemento stesso). Il comportamento corretto per i riferimenti e gli elementi fisici è descritto in precedenza.

Se fosse presente un solo tipo di progetto nel **Esplora soluzioni**, le operazioni di trascinamento della selezione sarebbero semplici. Poiché ogni sistema di progetto è in grado di definire il proprio comportamento di trascinamento della selezione, è necessario seguire alcune linee guida (basate sul comportamento di trascinamento della selezione di Windows Explorer) per garantire un'esperienza utente prevedibile:

- Un'operazione di trascinamento non modificata **nell'Esplora soluzioni** (quando né CTRL né MAIUSC sono premuti) dovrebbe comportare un'operazione di spostamento.

- Anche l'operazione di trascinamento della selezione deve comportare un'operazione di spostamento.

- L'operazione di trascinamento con CTRL dovrebbe comportare un'operazione di copia.

- I sistemi di progetto misti e basati su riferimento supportano la nozione di aggiunta di un collegamento (o riferimento) all'elemento di origine. Quando questi progetti sono la destinazione di un'operazione di trascinamento della selezione (quando si tiene premuto **CTRL+MAIUSC),** dovrebbe essere aggiunto un riferimento all'elemento al progetto

Non tutte le operazioni di trascinamento della selezione sono sensibili a combinazioni di progetti basati su riferimento, basati su directory e misti. In particolare, è problematico fingere di consentire un'operazione di spostamento tra un progetto di origine basato su directory e un progetto di destinazione basato su riferimento perché il progetto basato su directory di origine dovrà eliminare l'elemento di origine al termine dello spostamento. Il progetto basato sul riferimento di destinazione finirebbe quindi con un riferimento a un elemento eliminato.

È anche fuorviante fingere di consentire un'operazione di copia tra questi tipi di progetti perché il progetto basato su riferimenti di destinazione non deve creare una copia indipendente dell'elemento di origine. Analogamente, il trascinamento di CTRL+MAIUSC in un progetto di destinazione basato su directory non deve essere consentito perché un progetto basato su directory non è in grado di rendere persistenti i riferimenti. Nei casi in cui l'operazione di trascinamento della selezione non è supportata, l'IDE deve non consentire il rilascio e mostrare all'utente il cursore no-drop (illustrato nella tabella del puntatore riportata di seguito).

Per implementare correttamente il comportamento di trascinamento della selezione, il progetto di origine del trascinamento deve comunicare la sua natura al progetto di destinazione. Ad esempio, è basato su riferimento o su directory. Queste informazioni sono indicate dal formato degli Appunti offerto dall'origine. Come origine di un'operazione di trascinamento (o copia degli Appunti), un progetto deve offrire rispettivamente o , a seconda che il progetto sia basato su riferimento o `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` su directory. Entrambi questi formati hanno lo stesso contenuto di dati, simile al formato Windows, ad eccezione del fatto che gli elenchi di stringhe, anziché essere nomi file, sono un elenco di stringhe con terminazione doppia (come restituito da o in base alle `CF_HDROP` `NULL` `Projref` `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` esigenze).

Come destinazione di un'operazione di rilascio (o incolla degli Appunti), un progetto deve accettare sia che , anche se la gestione esatta dell'operazione di trascinamento della selezione varia a seconda della natura del progetto di destinazione e del progetto di `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` origine. Il progetto di origine dichiara la propria natura in base all'offerta `CF_VSREFPROJECTITEMS` o `CF_VSSTGPROJECTITEMS` . La destinazione dell'eliminazione comprende la propria natura e pertanto dispone di informazioni sufficienti per prendere decisioni sull'esecuzione di uno spostamento, una copia o un collegamento. L'utente modifica anche l'operazione di trascinamento della selezione da eseguire premendo CTRL, MAIUSC o entrambi i tasti CTRL e MAIUSC. È importante che l'obiettivo di rilascio indichi correttamente quale operazione verrà eseguita in anticipo nei `DragEnter` metodi `DragOver` e . Il **Esplora soluzioni** automaticamente se il progetto di origine e il progetto di destinazione sono lo stesso progetto.

Il trascinamento di elementi di progetto tra istanze di Visual Studio (ad esempio, da un'istanza di devenv.exe a un'altra) non è supportato in modo specifico. **L Esplora soluzioni** disabilita direttamente anche questa impostazione.

L'utente deve essere sempre in grado di determinare l'effetto di un'operazione di trascinamento della selezione selezionando un elemento, trascinandolo nella posizione di destinazione e osservando quale dei seguenti puntatori del mouse viene visualizzato prima del rilascio dell'elemento:

| Puntatore del mouse | Comando | Descrizione |
| :---: | --- | --- |
| ![Icona di "nessun rilascio" del mouse](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Nessuna eliminazione | Impossibile eliminare l'elemento nel percorso specificato. |
| ![Icona "copia" del mouse](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Copia | L'elemento verrà copiato nel percorso di destinazione. |
| ![Icona "spostamento" del mouse](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Sposta | L'elemento verrà spostato nel percorso di destinazione. |
| ![Icona "aggiungi riferimento" del mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Aggiungi riferimento | Un riferimento all'elemento selezionato verrà aggiunto alla posizione di destinazione. |

#### <a name="reference-based-projects"></a>Progetti basati su riferimento
 La tabella seguente riepiloga le operazioni di trascinamento della selezione (nonché taglia/copia/incolla) che devono essere eseguite in base alla natura dell'elemento di origine e ai tasti di modifica premuti per i progetti di destinazione basati su riferimenti:

| Modificatore | Category | Elemento di origine: Riferimento/Collegamento | Elemento di origine: elemento fisico o file system ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Nessun modificatore | Azione | Sposta | Collegamento |
| Nessun modificatore | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Nessun modificatore | Source (Sorgente) | Elimina il riferimento all'elemento originale | Mantiene l'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria |
| MAIUSC+Trascinamento | Azione | Sposta | Nessuna eliminazione |
| MAIUSC+Trascinamento | Destinazione | Aggiunge un riferimento all'elemento originale | Nessuna eliminazione |
| MAIUSC+Trascinamento | Source (Sorgente) | Elimina il riferimento all'elemento originale | Nessuna eliminazione |
| MAIUSC+Trascinamento | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria | Nessuna eliminazione |
| CTRL+Trascinamento | Azione | Copia | Nessuna eliminazione |
| CTRL+Trascinamento | Destinazione | Aggiunge un riferimento all'elemento originale | Nessuna eliminazione |
| CTRL+Trascinamento | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Nessuna eliminazione |
| CTRL+Trascinamento | Risultato | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria | Nessuna eliminazione |
| CTRL+MAIUSC+Trascinamento | Azione | Collegamento | Collegamento |
| CTRL+MAIUSC+Trascinamento | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| CTRL+MAIUSC+Trascinamento | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL+MAIUSC+Trascinamento | Risultato | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria | `DROPEFFECT_LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria |
| CTRL+MAIUSC+Trascinamento | Nota | Uguale al comportamento di trascinamento della selezione per i tasti di scelta rapida in Windows Explorer. ||
| Taglia/Incolla | Azione | Sposta | Collegamento |
| Taglia/Incolla | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Taglia/Incolla | Source (Sorgente) | Mantiene il riferimento all'elemento originale|Mantiene l'elemento originale |
| Taglia/Incolla | Risultato | L'elemento rimane nella posizione originale nella memoria | L'elemento rimane nella posizione originale nella memoria |
| Copia/Incolla | Azione | Copia | Collegamento |
| Copia/Incolla | Source (Sorgente) | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento originale |
| Copia/Incolla | Risultato | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| Copia/Incolla | Azione | L'elemento rimane nella posizione originale nella memoria | L'elemento rimane nella posizione originale nella memoria |

#### <a name="directory-based-projects"></a>Progetti basati su directory
La tabella seguente riepiloga le operazioni di trascinamento della selezione (nonché taglia/copia/incolla) che devono essere eseguite in base alla natura dell'elemento di origine e ai tasti di modifica premuti per i progetti di destinazione basati su directory:

| Modificatore | Category | Elemento di origine: Riferimento/Collegamento | Elemento di origine: elemento fisico o file system ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Nessun modificatore | Azione | Sposta | Sposta |
| Nessun modificatore | Destinazione | Copia l'elemento nel percorso di destinazione | Copia l'elemento nel percorso di destinazione |
| Nessun modificatore | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina il riferimento all'elemento originale |
| MAIUSC+Trascinamento | Azione | Sposta | Sposta |
| MAIUSC+Trascinamento | Destinazione | Copia l'elemento nel percorso di destinazione | Copia l'elemento nel percorso di destinazione |
| MAIUSC+Trascinamento | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dal percorso originale |
| MAIUSC+Trascinamento | Risultato | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria | `DROPEFFECT_MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria |
| CTRL+Trascinamento | Azione | Copia | Copia |
| CTRL+Trascinamento | Destinazione | Copia l'elemento nel percorso di destinazione | Copia l'elemento nel percorso di destinazione |
| CTRL+Trascinamento | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene il riferimento all'elemento originale |
| CTRL+Trascinamento | Risultato | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria | `DROPEFFECT_COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nella memoria |
| CTRL+MAIUSC+Trascinamento | | Nessuna eliminazione | Nessuna eliminazione |
| Taglia/Incolla | Azione | Sposta | Sposta |
| Taglia/Incolla | Destinazione | Copia l'elemento nel percorso di destinazione | Copia l'elemento nel percorso di destinazione |
| Taglia/Incolla | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dal percorso originale |
| Taglia/Incolla | Risultato | L'elemento rimane nella posizione originale nella memoria | L'elemento viene eliminato dalla posizione originale nella memoria |
| Copia/Incolla | Azione | Copia | Copia |
| Copia/Incolla | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nel percorso di destinazione |
| Copia/Incolla | Source (Sorgente) | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copia/Incolla | Risultato | L'elemento rimane nella posizione originale nella memoria | L'elemento rimane nella posizione originale nell'archivio |

#### <a name="mixed-target-projects"></a>Progetti con destinazione mista
La tabella seguente riepiloga le operazioni di trascinamento della selezione (nonché taglia/copia/incolla) che devono essere eseguite in base alla natura dell'elemento di origine e ai tasti di modifica premuti per i progetti di destinazione mista:

| Modificatore | Category | Elemento di origine: Riferimento/Collegamento | Elemento di origine: elemento fisico o file system ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Nessun modificatore | Azione | Sposta | Sposta |
| Nessun modificatore | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nel percorso di destinazione |
| Nessun modificatore | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina il riferimento all'elemento originale |
| Nessun modificatore | Risultato | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento viene eliminato dalla posizione originale nell'archiviazione |
| MAIUSC+trascinamento | Azione | Sposta | Sposta |
| MAIUSC+trascinamento | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nel percorso di destinazione |
| MAIUSC+trascinamento | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dalla posizione originale |
| MAIUSC+trascinamento | Risultato | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ MOVE` viene restituito come azione da `::Drop` e l'elemento viene eliminato dalla posizione originale nell'archiviazione |
| CTRL+TRASCINAMENTO | Azione | Copia | Copia |
| CTRL+TRASCINAMENTO | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nel percorso di destinazione |
| CTRL+TRASCINAMENTO | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL+TRASCINAMENTO | Risultato | `DROPEFFECT_ COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ COPY` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| CTRL+MAIUSC+TRASCINAMENTO | Azione | Collegamento | Collegamento |
| CTRL+MAIUSC+TRASCINAMENTO | Destinazione | Aggiunge un riferimento all'elemento originale | Aggiunge un riferimento all'elemento di origine originale |
| CTRL+MAIUSC+TRASCINAMENTO | Source (Sorgente) | Mantiene il riferimento all'elemento originale | Mantiene l'elemento originale |
| CTRL+MAIUSC+TRASCINAMENTO | Risultato | `DROPEFFECT_ LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione | `DROPEFFECT_ LINK` viene restituito come azione da `::Drop` e l'elemento rimane nella posizione originale nell'archiviazione |
| Taglia/Incolla | Azione | Sposta | Sposta |
| Taglia/Incolla | Destinazione | Copia l'elemento nel percorso di destinazione | Copia l'elemento nel percorso di destinazione |
| Taglia/Incolla | Source (Sorgente) | Elimina il riferimento all'elemento originale | Elimina l'elemento dalla posizione originale |
| Taglia/Incolla | Risultato | L'elemento rimane nella posizione originale nell'archiviazione | L'elemento viene eliminato dalla posizione originale nell'archiviazione |
| Copia/Incolla | Azione | Copia | Copia |
| Copia/Incolla | Destinazione | Aggiunge un riferimento all'elemento originale | Copia l'elemento nel percorso di destinazione |
| Copia/Incolla | Source (Sorgente) | Mantiene l'elemento originale | Mantiene l'elemento originale |
| Copia/Incolla | Risultato | L'elemento rimane nella posizione originale nell'archiviazione | L'elemento rimane nella posizione originale nella memoria |

Questi dettagli devono essere presi in considerazione durante l'implementazione del trascinamento **nella Esplora soluzioni**:

- Progettare per più scenari di selezione.

- I nomi di file (percorso completo) devono essere univoci nel progetto di destinazione oppure l'eliminazione non deve essere consentita.

- I nomi delle cartelle devono essere univoci (senza distinzione tra maiuscole e minuscole) al livello in cui vengono eliminati.

- Esistono differenze di comportamento tra i file aperti o chiusi al momento del trascinamento (non menzionato negli scenari precedenti).

- I file di primo livello si comportano in modo leggermente diverso rispetto ai file nelle cartelle.

Un altro problema da tenere presente è come gestire le operazioni di spostamento su elementi con finestre di progettazione o editor aperti. Il comportamento previsto è il seguente (si applica a tutti i tipi di progetto):

1. Se l'editor o la finestra di progettazione aperti non contiene modifiche non salvate, la finestra dell'editor o della finestra di progettazione deve essere chiusa automaticamente.

2. Se l'editor o la finestra di progettazione aperta contiene modifiche non salvate, l'origine del trascinamento deve attendere l'esecuzione del rilascio e quindi chiedere all'utente di salvare le modifiche di cui non è stato eseguito il salvataggio nei documenti aperti prima di chiudere la finestra con un prompt simile al seguente:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

In questo modo l'utente ha la possibilità di salvare il lavoro in corso prima che la destinazione eserne le copie. È stato aggiunto `IVsHierarchyDropDataSource2::OnBeforeDropNotify` un nuovo metodo per abilitare questa gestione.

La destinazione copierà quindi lo stato dell'elemento così come si trova nell'archivio (senza includere le modifiche non salvate nell'editor se l'utente ha scelto **No).** Dopo che la destinazione ha completato la copia (in ), l'origine ha la possibilità di completare la parte di eliminazione dell'operazione `IVsHierarchyDropDataSource::Drop` di spostamento (in `IVsHierarchyDropDataSource::OnDropNotify` ).

Tutti gli editor con modifiche non salvate devono essere lasciati aperti. Per i documenti con modifiche non salvate, ciò significa che verrà eseguita la parte di copia dell'operazione di spostamento, ma la parte di eliminazione verrà interrotta. In uno scenario a selezione multipla quando l'utente sceglie **No,** i documenti con modifiche non salvate non devono essere chiusi o rimossi, ma quelli senza modifiche non salvate devono essere chiusi e rimossi.
