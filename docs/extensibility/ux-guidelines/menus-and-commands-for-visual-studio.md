---
title: Menu e comandi per Visual Studio . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698392"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu e comandi per Visual Studio
## <a name="command-usage"></a>Utilizzo dei comandi

### <a name="overview"></a>Panoramica
 A differenza di Microsoft Office, che è una suite che comprende molti prodotti separati, Visual Studio contiene molti prodotti che contribuiscono ciascuno i set di comandi per l'IDE di Visual Studio globale. L'IDE gestisce la complessità di migliaia di comandi filtrando le funzionalità disponibili per l'utente in base al contesto.

 Quando il contesto di un utente cambia, ad esempio passando da una finestra di progettazione a una finestra di modifica del codice, la funzionalità non correlata al nuovo contesto scompare. Allo stesso tempo, le nuove funzionalità vengono riproposte insieme alle informazioni dinamiche correlate, ad esempio le opzioni Proprietà e Casella degli strumenti. L'utente non dovrebbe notare lo scambio del set di comandi disponibile. Se l'utente è distratto o confuso da comandi visualizzati o che scompaiono, la progettazione dell'interfaccia utente deve essere rettificata. Il contesto corrente dell'utente è sempre indicato in uno o più modi, ad esempio nella barra del titolo dell'IDE, nella finestra Proprietà o nella finestra di dialogo Pagine delle proprietà.

 Le barre dei comandi consentono flessibilità nell'interfaccia utente.Command bars allow for flexibility in the UI. Le uniche strutture di comando inerenti all'ambiente di Visual Studio sono il menu principale e la barra dei comandi principale, che può essere personalizzata e persino nascosta. Altre barre dei comandi vengono visualizzate e scompaiono in base allo stato dell'applicazione. Le finestre degli strumenti e gli editor di documenti possono inoltre contenere barre degli strumenti incorporate all'interno dei bordi delle finestre.

#### <a name="basic-guidelines"></a>Linee guida di base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Quando possibile, utilizzare comandi condivisi, gruppi di comandi e menu esistenti.
 Poiché i comandi vengono in genere visualizzati in base al contesto, l'utilizzo di menu condivisi e gruppi di comandi esistenti garantisce che la struttura dei comandi rimanga relativamente stabile tra le modifiche nel contesto. Il riutilizzo dei comandi condivisi e l'inserimento di nuovi comandi vicino ai comandi condivisi correlati riduce anche la complessità dell'IDE e crea un'esperienza più intuitiva. Se è necessario definire un nuovo comando, provare a inserirlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, inserirlo in un menu condiviso esistente vicino a un gruppo di comandi correlato prima di creare un nuovo menu di primo livello.

##### <a name="do-not-create-icons-for-every-command"></a>Non creare icone per ogni comando.
 Riflettere attentamente prima di creare un'icona di comando. Le icone devono essere create solo per i comandi che:

- vengono visualizzati su una barra degli strumenti predefinita.

- è probabile che vengano aggiunti dagli utenti a una barra degli strumenti tramite la finestra di dialogo **Personalizza....**

- un'icona associata alla stessa azione in un altro prodotto Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitare l'aggiunta di tasti di scelta rapida
 La stragrande maggioranza degli utenti impiega una piccola frazione di tutte le scorciatoie disponibili. In caso di dubbio, non associare la funzionalità a una scelta rapida da tastiera. Collabora con il team dell'esperienza utente prima di aggiungere nuove scorciatoie.

##### <a name="give-commands-a-default-menu-placement"></a>Assegnare ai comandi una posizione di menu predefinita.
 Tenere presente che i comandi verranno personalizzati da altri utenti e progettarli di conseguenza. Non esiste un comando nascosto. Tutti i comandi di Visual Studio vengono visualizzati nella finestra di dialogo **Strumenti > Personalizza,** nella finestra di comando, nel completamento automatico, nella finestra di dialogo **Strumenti > tastiera > e** nell'ambiente DTE (Development Tools Environment). Assicurati di assegnare ai comandi un nome e una descrizione comando nel file .ctc in modo che gli utenti possano trovarli facilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Non duplicare i comandi condivisi su una barra degli strumenti incorporata.
 È utile posizionare i comandi in prossimità dell'area dello stato attivo dell'utente. Un modo per eseguire questa operazione consiste nel creare una barra degli strumenti incorporata nella parte superiore della finestra degli strumenti o dell'editor di documenti. I comandi inseriti nella barra degli strumenti devono essere specifici per l'area contenuto all'interno della finestra. Non duplicare i comandi condivisi su queste barre degli strumenti. Ad esempio, non inserire mai un'icona "Salva" all'interno di una barra degli strumenti incorporata.

### <a name="content-and-command-visibility"></a>Visibilità dei contenuti e dei comandi
 I comandi sono disponibili negli ambiti seguenti: **Ambiente**, **Gerarchia**e **Documento**. Conoscere ogni ambito per avere fiducia nel posizionamento dei comandi.

 I comandi nell'ambito **Ambiente** stabiliscono il contesto primario e sono condivisi tra più contesti. Modificano la visibilità o la disposizione di documenti e finestre degli strumenti. Tra i comandi nell'ambito dell'ambiente sono **Nuovo progetto**, **Connetti al server**, Collega **processo**, **Copia**, **Incolla**, **Trova**, **Opzioni**, **Personalizza**, **Nuova finestra**e **Visualizza Guida**. **Cut**

 I comandi nell'ambito **Gerarchia** gestiscono le gerarchie in Visual Studio, inclusi **Progetto,** **Team**e **Dati.** Si riferiscono al sottocontesto di un progetto, ad esempio **Debug**, **Build**, **Test**, **Architecture**o **Analyze**. Tra i comandi nell'ambito Gerarchia sono **Aggiungi nuovo elemento**, Nuova **query**, **Impostazioni progetto**, Aggiungi nuova **origine dati**, Avvia Creazione guidata **esecuzione guidata**e Nuovo **diagramma**.

 I comandi nell'ambito **Documento** agiscono sul contenuto di un documento, ad esempio codice, progettazione o query elemento di lavoro (WIQ). Agiscono anche sulla visualizzazione di una finestra degli strumenti o sono in altro modo specifici per tale finestra degli strumenti. I comandi dell'ambito del documento agiscono anche sugli oggetti file che sono essi stessi specifici della gerarchia, ad esempio **Rimuovi dal progetto**. Tra i comandi nell'ambito del documento sono **Effettua refactoring > Rinomina**, Crea copia **dell'elemento di lavoro**, **Espandi tutto**, **Comprimi tutto**e Crea attività **utente**.

### <a name="command-placement-decisions"></a>Decisioni di posizionamento dei comandi
 Dopo aver deciso di creare un comando, è necessario determinarne la posizione appropriata e se creare una scelta rapida da tastiera. Seguire questo percorso decisionale per stabilire dove posizionare il comando:Follow this decision path to establish where to place the command:

 ![Grafico di decisione posizione comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Percorso decisionale per il posizionamento dei comandi in Visual StudioDecision path for command placement in Visual Studio**

### <a name="command-placement-in-menus"></a>Posizionamento dei comandi nei menu

#### <a name="main-menu-bar"></a>Barra del menu principale
 La barra dei menu principale deve essere la posizione standard per i comandi di tutti i pacchetti di menu specifici del contesto che contribuiscono all'interfaccia utente. La barra dei menu principale differisce da altre strutture di comando in quanto l'ambiente lo utilizza per controllare quali comandi sono visibili. Tutte le altre barre dei comandi disabilitano semplicemente i comandi che sono fuori contesto, indipendentemente dal fatto che siano posizionati in un menu o in una barra degli strumenti.

 L'ambiente definisce un set di comandi incorporati nella barra dei menu principale che sono comuni all'intero IDE e più domini di attività. Questi comandi sono sempre visibili indipendentemente da quali VSPackage vengono caricati nell'ambiente. Anche se VSPackage possono estendere questo set di comandi, il set di comandi da ogni prodotto e il posizionamento dei relativi comandi è responsabilità di ogni team.

 La struttura del menu principale di Visual Studio può essere suddivisa nelle seguenti categorie di menu:

##### <a name="core-menus"></a>Menu principali

- File

- Modifica

- Visualizza

- Strumenti

- Finestra

- Guida

##### <a name="project-specific-menus"></a>Menu specifici del progetto

- Project

- Compilazione

- Debug

##### <a name="context-specific-menus"></a>Menu specifici del contesto

- Team

- Data

- Test

- Architecture

- Analisi

##### <a name="document-specific-menus"></a>Menu specifici del documento

- Format

- Tabella

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Quando si progettano i menu principali, attenersi alle seguenti regole:

- Non superare i 25 elementi di primo livello in un determinato contesto

- I menu non devono mai superare i 600 pixel di altezza.

- Valutare un menu principale in più contesti, ad esempio in SKU Ultimate e profilo generale.

- I menu a comparsa sono accettabili.

- I menu a comparsa devono contenere almeno tre elementi e non più di sette.

- I menu a comparsa devono andare a uno solo livello di profondità: alcune voci di menu di Visual Studio dispongono di sottomenu a cascata, ma questo modello non è consigliato.

- Non utilizzare più di sei separatori. I raggruppamenti devono rispettare la figura seguente:

     ![Indicazioni per il raggruppamento dei menu principali](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Anche se non è necessario disporre di ogni raggruppamento nella figura, l'aggiunta di ulteriori raggruppamenti è limitata.

- Ogni raggruppamento deve avere da due a sette voci di menu.

#### <a name="main-menu-ordering"></a>Ordinamento del menu principale
 Prima di aggiungere un nuovo elemento di primo livello, è consigliabile inserire il comando in un menu di primo livello esistente. Quando aggiungi un nuovo menu di primo livello, assicurati di posizionarlo nella posizione corretta. Decidere se il menu è specifico per il progetto, il contesto o il documento. Mantenere il nome del menu di primo livello conciso e utilizzare una sola parola.

 I menu principali dovrebbero prenotare il resto dei comandi. File, Modifica e Visualizza devono essere sempre a sinistra e Strumenti, Finestra e Guida devono essere sempre a destra.

#### <a name="context-menus"></a>Menu di scelta rapida
 L'inserimento di troppe funzionalità all'interno dei menu di scelta rapida comporta un'interfaccia difficile da imparare. Tutte le funzionalità principali devono essere disponibili tramite la barra dei menu principale. Il posizionamento dei comandi deve essere riconciliato con i comandi esistenti per evitare comandi duplicati. Per i menu di scelta rapida, la shell definisce i gruppi di menu standard che devono essere inclusi a seconda che il menu di scelta rapida sia per la soluzione, un nodo di progetto o un elemento di progetto.

 Quando si progettano i menu di scelta rapida, rispettare le stesse regole del menu principale e inoltre:

- Non superare le 25 voci di menu di primo livello.

- I menu a comparsa sono accettabili ma non devono superare un livello di profondità: non utilizzare mai riquadri a comparsa a cascata.

- Non utilizzare più di sei separatori.

### <a name="command-placement-in-toolbars"></a>Posizionamento dei comandi nelle barre degli strumenti

#### <a name="general-toolbars"></a>Barre degli strumenti generali
 Quando si progettano e si organizzano le barre degli strumenti, attenersi ai seguenti standard:

- Non usare più di un verbo per pulsante. Un pulsante: un'azione.

- Utilizzare il testo accanto all'icona solo se deve essere rinforzato con l'etichetta.

- Utilizzare una casella combinata esclusivamente per le proprietà che verranno commutate più volte in una sessione. In caso contrario, esporre la proprietà altrove.

- La larghezza di una casella combinata deve essere uguale alla larghezza dell'elemento più lungo all'interno della casella, ovvero 30%. Ad esempio, se l'elemento più lungo è 200 pixel, la casella combinata deve avere una larghezza di 260 pixel.

- Limitare l'uso dei separatori. L'uso di un separatore accanto a un elenco a discesa è un anti-modello, perché la forma dell'elenco a discesa stesso funge da separatore visivo.

- I gruppi di icone devono contenere da tre a sei icone.

- Se i qualificatori generano più comandi utili, usare un pulsante di divisione che archivia l'ultima impostazione:If qualifiers result in multiple useful commands, use a split button that stores the last setting:

     ![Pulsanti di menu combinati in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Esempio di pulsante di divisione. I sei comandi a sinistra possono invece essere inseriti in un singolo pulsante.**

#### <a name="product-specific-toolbars"></a>Barre degli strumenti specifiche del prodotto
 Ogni prodotto può fornire una barra degli strumenti predefinita che contiene i comandi utilizzati di frequente e importanti e la barra degli strumenti predefinita di ogni prodotto dovrebbe essere visualizzata al primo avvio di Visual Studio dopo l'installazione del prodotto.

 I prodotti devono inoltre sfruttare i menu e i gruppi di comandi condivisi forniti dall'IDE. Ogni gruppo di comandi condiviso viene inserito in un menu condiviso per organizzare i comandi correlati in modo significativo per l'utente. È importante sfruttare questa struttura di comando condivisa per ridurre la complessità.

#### <a name="global-toolbars"></a>Barre degli strumenti globali
 Le barre degli strumenti globali sono necessarie per adattarsi a una riga a destra della scatola. Quando si crea una nuova barra degli strumenti globale, seguire le linee guida per tale tipo di barra degli strumenti.

 **Linee guida generali della barra degli strumenti:**

- Ogni barra degli strumenti ha 24 pixel nei controlli comuni (gripper, overflow).

- Ogni pulsante della barra degli strumenti ha una larghezza di 22 pixel, inclusa la spaziatura interna. Rendendo l'icona un pulsante di divisione aggiunge altri 11 pixel di larghezza.

- È consentita la duplicazione dei comandi tra le barre degli strumenti.

  **Le barre degli strumenti specifiche del documento** vengono visualizzate quando un determinato tipo di file è attivo e scompaiono quando un tipo di file diverso diventa attivo.

- Le barre degli strumenti specifiche del documento potrebbero non avere più di 12 pulsanti.

- La larghezza totale della barra degli strumenti non può superare i 300 pixel.

- Ogni tipo di file può avere una barra degli strumenti incorporata o una barra degli strumenti globale specifica del documento, ma non entrambe.

  **Le barre degli strumenti specifiche del contesto** vengono visualizzate quando un determinato contesto è impostato e tendono a rimanere attive per periodi prolungati.

- Il limite dei pulsanti per tutte le barre degli strumenti specifiche del contesto è 18.The button limit for all context-specific toolbars is 18.

- Se la maggior parte degli utenti non utilizza in modo coerente i comandi di questa barra degli strumenti quando il contesto è attivo, non associare questa barra degli strumenti a un contesto.

- Assicurarsi che la barra degli strumenti scompaia quando si esce dal contesto. Nessuna di queste barre degli strumenti dovrebbe essere visualizzata all'avvio.

  **Le barre degli strumenti senza contesto** non vengono mai visualizzate automaticamente. Questi vengono visualizzati solo quando l'utente li attiva. Mantenere la larghezza massima al di sotto di 200 pixel.

### <a name="general-organization-and-shell-defined-groups"></a>Organizzazione generale e gruppi definiti dalla shell
 Utilizzare comandi condivisi, gruppi di comandi e menu esistenti. Se è necessario definire un nuovo comando, provare a inserirlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, provare a inserirlo in un menu condiviso esistente vicino a un gruppo di comandi correlato prima di creare un nuovo menu di primo livello. In questo modo si riduce la complessità dei comandi garantendo al tempo stesso un posizionamento coerente dei comandi nell'IDE.

 Il menu Formato condiviso, in genere visualizzato nel contesto delle finestre di documento in stile finestra di progettazione, è illustrato nell'immagine seguente:The shared **Format** menu, typically shown in the context of designer-style document windows, is illustrated in the following image:

 ![Menu Formato con callout di Visual Studio](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Menu groups in Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Riduzione e riutilizzo dei comandi
 I comandi vengono in genere visualizzati in base al contesto, al fine di ridurre il numero di comandi visualizzati dall'utente in un determinato momento. Tuttavia, è anche necessario riutilizzare i menu condivisi esistenti e i gruppi di comandi per garantire che la struttura dei comandi rimanga relativamente stabile tra le modifiche nel contesto.

 Il riutilizzo dei comandi condivisi e l'inserimento di nuovi comandi vicino ai comandi condivisi correlati riduce la complessità dell'IDE e crea un'esperienza più intuitiva.

## <a name="naming-commands"></a>Denominazione dei comandi

### <a name="naming-conventions"></a>Convenzioni di denominazione
 La denominazione coerente dei comandi è fondamentale in modo che gli utenti possano trovare ed eseguire comandi, tramite la riga di comando o l'associazione a un tasto di scelta rapida. I nomi dei comandi consentono inoltre all'utente di comprendere lo scopo di un comando quando viene visualizzato su una barra degli strumenti o in un menu di scelta rapida o a catena.

#### <a name="when-naming-commands"></a>Quando si assegnano nomi ai comandi:

- Costruire il testo in modo che sia facilmente localizzabile. Per ulteriori informazioni sulla localizzazione del testo, consultate Procedure consigliate per la [localizzazione.](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)

- Sii conciso. I comandi non devono usare più di tre parole.

- Usa maiuscole/minuscole: la prima lettera di ogni parola deve essere scritta in maiuscolo. Per ulteriori informazioni sulla formattazione del testo in Visual Studio, vedere [Stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Prendere in considerazione dove verrà inserito il comando. Si trova in un menu di primo livello o in un riquadro a comparsa? Ad esempio, quando si raggruppano i comandi di allineamento in un riquadro a comparsa, il comando di primo livello deve essere "Allinea" e i comandi del riquadro a comparsa devono essere "Left", "Right", "Center", "Justify" e così via. Sarebbe ridondante denominare i comandi a comparsa "Allinea a sinistra" o "Allinea a destra".

     ![Menu Formato di Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Uso delle icone con i comandi
 Essere parsimonioso nell'uso di icon pairing con i comandi. Anche se l'associazione di un'immagine univoca a un comando accelera la capacità dell'utente di identificare tale comando, l'ingombro visivo e l'inefficienza si verificano con l'uso eccessivo dell'immagine. Le regole seguenti consentono di decidere se creare un'icona di comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Utilizzare un'icona con un comando solo se:

- Lo stesso comando ha un'icona associata in un altro prodotto Microsoft di primo piano, ad esempio una delle applicazioni di Microsoft Office.

- Il comando verrà inserito in una barra degli strumenti predefinita.

- Il comando è un comando speciale che gli utenti possono aggiungere a una barra degli strumenti utilizzando la finestra di dialogo **"Personalizza...".**

## <a name="access-and-shortcut-keys"></a>Tasti di scelta rapida e di accesso

### <a name="overview"></a>Panoramica
 Esistono due tipi di assegnazioni dei tasti della tastiera:

- **I tasti di scelta** (noti anche come tasti di scelta rapida) consentono l'accesso tramite tastiera tramite i menu per l'esecuzione di comandi e per ogni etichetta nell'interfaccia utente della finestra di dialogo. I tasti di scelta sono principalmente per scopi di accessibilità, sono assegnati a tutti i menu e la maggior parte dei controlli della finestra di dialogo, non sono destinati a essere memorizzati, interessano solo la finestra corrente e sono localizzati.

- **I tasti di scelta rapida** utilizzano principalmente sequenze di tasti Ctrl (Ctrl) e Funzione (Fn). Sono progettati più per gli utenti avanzati e aiutano nella produttività. Vengono assegnati solo ai comandi utilizzati più di frequente e consentono un accesso rapido ignorando il menu principale. I tasti di scelta rapida devono essere memorizzati e per questo motivo devono essere assegnati in modo coerente con lo schema del profilo. Gli schemi dei tasti di scelta rapida possono variare da profilo a profilo. Un utente può personalizzare i tasti di scelta rapida tramite **Strumenti > Opzioni > Tastiera**.

### <a name="assigning-access-keys"></a>Assegnazione dei tasti di scelta
 I tasti di scelta sono costituiti da ALT più i tasti alfanumerici. Assegnare un tasto di scelta a ogni voce di menu senza eccezioni. Seguire Windows e le convenzioni comuni per l'assegnazione dei tasti di scelta. ad esempio, il tasto di scelta per **File > Nuovo** deve essere sempre **Alt, F, N**.

 Non usare lettere a pixel singolo come 'i' (in maiuscolo o minuscolo) o una 'l' minuscola, ed evitare di usare caratteri con discendenti (g, j, p, q e y) in quanto questi sono difficili da distinguere.

 Evitare di utilizzare chiavi duplicate quando possibile. Nei casi in cui la duplicazione è inevitabile, il sistema di menu gestisce i conflitti scorrendo tutti i comandi che utilizzano il tasto. Ad esempio, per un ipotetico comando "Numero" nel menu File che duplica il tasto di scelta "N", **Alt, F, N** creerebbe un nuovo file e **Alt, F, N, N** eseguirebbe il comando "Numero".

### <a name="assigning-shortcut-keys"></a>Assegnazione di tasti di scelta rapida
 Evitare di assegnare nuovi tasti di scelta rapida, perché non sono necessari per ogni comando e tassare il sistema (e la memoria utente) se sovrausato. I dati del programma Analisi utilizzo software indicano che gli utenti di Visual Studio utilizzano solo un piccolo sottoinsieme dei collegamenti integrati.

 Quando si definiscono i tasti di scelta rapida, attenersi alle seguenti regole:

- **Utilizzare le sequenze di tasti Ctrl (Ctrl) e Funzione (Fn).**

- **Conservare i collegamenti utilizzati di frequente.** Mantenere le scorciatoie più popolari.

- **Semplifica la digitazione dei tasti di scelta rapida dell'editor.** Associare tasti di scelta rapida facili da digitare ai comandi di cui gli sviluppatori hanno più bisogno durante la scrittura del codice. Ad esempio, **Edit.InvokeSmartTag** deve avere un tasto di scelta rapida, ad esempio Ctrl , e non Alt , Maiusc e F10.

- **Sforzatevi di guidare costantemente le scorciatoie a tema.**

- **Seguire le linee guida di Windows per determinare i tasti di modifica da utilizzare.** Utilizzare le combinazioni di tasti CTRL per i comandi con effetti su larga scala, ad esempio i comandi che si applicano a un intero documento. Utilizzare le combinazioni di tasti MAIUSC per i comandi che estendono o completano le azioni del tasto di scelta rapida standard. Non usare le combinazioni Ctrl .

- **Rimuovere le scorciatoie estranee.** Se si dispone di una funzionalità legacy, è consigliabile rimuovere i tasti di scelta rapida utilizzati con estrema infrequenza (meno di 10 volte dai dati di Analisi utilizzo software) o infrequenza moderata (meno di 100 volte dai dati di Analisi utilizzo software) se un tasto di scelta consente di accedere rapidamente allo stesso comando. Ad esempio: Alt, H, C aprirà Aiuto/ Sommario.

  Non esiste un modo semplice per verificare la disponibilità dei collegamenti. Se si desidera aggiungere un collegamento, attenersi alla seguente procedura:

1. Controllare l'elenco dei tasti di scelta rapida di [Visual Studio 2013](http://visualstudioshortcuts.com/2013/) per determinare se sono presenti comandi simili con cui raggruppare i propri.

2. Passare a **Strumenti > Opzioni > Ambiente > Tastiera** e testare la scelta rapida. Controllare ogni schema di mappatura della tastiera elencato in "Applicare il seguente schema aggiuntivo di mappatura della tastiera". Controllare i profili Generale, VB, VB e C, poiché questi condividono scelte rapide univoche. Il collegamento è disponibile se non è mappato in nessuna di queste posizioni.
