---
title: Menu e comandi per Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b7fb3b82d56038695c728d2125658a7f51d31f6
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57870478"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu e comandi per Visual Studio
## <a name="command-usage"></a>Uso del comando

### <a name="overview"></a>Panoramica
 A differenza di Microsoft Office, che è una suite che comprende molti prodotti separati, Visual Studio contiene molti prodotti che ognuno contribuire con i set di comandi per l'IDE di Visual Studio globali. L'IDE gestisce la complessità di migliaia di comandi filtrando le funzionalità disponibili per l'utente in base al contesto.

 Quando un contesto dell'utente cambia - ad esempio il passaggio da una finestra di progettazione a una finestra di modifica del codice - funzionalità non correlate a viene rimosso il nuovo contesto. Allo stesso tempo, nuove funzionalità viene visualizzata insieme alle informazioni dinamiche correlate, ad esempio le opzioni di proprietà e della casella degli strumenti. L'utente non noterà lo scambio del set di comandi disponibili. Se l'utente è distratti o confuso dai comandi visualizzate o scompaiono, la progettazione dell'interfaccia utente deve quindi regolazione. Il contesto dell'utente corrente è sempre indicato in uno o più modi, ad esempio nella barra del titolo dell'IDE, la finestra proprietà o la finestra di dialogo Pagine delle proprietà.

 Barre dei comandi consentono di flessibilità nell'interfaccia utente. L'unico comando strutture inerenti a Visual Studio ambiente sono nel menu principale e la barra di comando principale, che può essere personalizzata e anche nascosta. Altre barre dei comandi apparire e scomparire basati sullo stato dell'applicazione. Editor di documenti e finestre degli strumenti può inoltre contenere barre degli strumenti incorporate entro i margini di finestra.

#### <a name="basic-guidelines"></a>Linee guida di base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Usare i comandi condivisi esistenti, gruppi di comandi e menu laddove possibile.
 Poiché i comandi sono in genere visualizzati in basati sul contesto, l'uso di menu condivisi esistenti e i gruppi di comandi assicura che la struttura del comando rimane relativamente stabile tra le modifiche nel contesto. Riutilizzo di comandi condivisi e l'inserimento di nuovi comandi vicino i comandi correlati alla condivisi inoltre riduce la complessità dell'IDE e crea un'esperienza più semplice. Se è necessario definire un nuovo comando, provare a inserirlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, è necessario inserirlo in un menu condiviso esistente vicino a un gruppo di comandi correlati prima di creare un nuovo menu di primo livello.

##### <a name="do-not-create-icons-for-every-command"></a>Non creare icone per ogni comando.
 Considerare con attenzione prima di creare un'icona del comando. Le icone devono essere create solo per i comandi che:

-   vengono visualizzati in una barra degli strumenti predefinita.

-   è probabile che venga aggiunta da parte degli utenti a una barra degli strumenti tramite il **Personalizza...**  finestra di dialogo.

-   è associata un'icona con la stessa azione in un altro prodotto Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitare l'aggiunta di tasti di scelta rapida
 La maggior parte degli utenti utilizzano una frazione di tutti i collegamenti disponibili. In caso di dubbi, non si associano le funzionalità a un tasto di scelta rapida. Funzionano con l'utente esperienza team prima di aggiungere nuovi tasti di scelta rapida.

##### <a name="give-commands-a-default-menu-placement"></a>Impartire comandi di posizionamento di menu predefinita.
 Tenere presente che i comandi verranno personalizzati da altri utenti e li progettare di conseguenza. Non vi è alcun equivalente di un comando nascosto. Tutti i comandi di Visual Studio vengono visualizzati nei **strumenti > Personalizza** finestra di dialogo, la finestra di comando, completamento automatico, il **strumenti > Opzioni > tastiera** finestra di dialogo e l'ambiente DTE (Development Tools). Assicurarsi di assegnare i comandi di un nome e una descrizione comando nel file con estensione CTC in modo che gli utenti possono trovare facilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Non corrispondenti a comandi condivisi in una barra degli strumenti incorporata.
 È utile posizionare i comandi in stretta vicinanza all'area di interesse dell'utente. Un modo per eseguire questa operazione consiste nel creare una barra degli strumenti incorporata nella parte superiore del documento o finestra degli strumenti editor. I comandi posizionati nella barra degli strumenti devono essere specifici per l'area del contenuto all'interno della finestra. Non corrispondenti a comandi condivisi in queste barre degli strumenti. Mai inserire, ad esempio, un'icona "Salva" all'interno di una barra degli strumenti incorporata.

### <a name="content-and-command-visibility"></a>Visibilità del contenuto e comando
 I comandi sono disponibili negli ambiti seguenti: **Ambiente**, **gerarchia**, e **documento**. Conoscere ogni ambito per avere la certezza di posizionamento del comando.

 I comandi di **ambiente** ambito stabilire contesto principale e vengono condivise tra più contesti. Modificano la visibilità o la disposizione dei documenti e finestre degli strumenti. Tra i comandi nell'ambiente di ambito sono **nuovo progetto**, **Connetti al Server**, **Connetti processo**, **Taglia**,  **Copia**, **incollare**, **trovare**, **opzioni**, **personalizzare**, **nuova finestra**, e **visualizzare la Guida**.

 I comandi di **gerarchia** ambito gestione gerarchie di Visual Studio, tra cui **progetto**, **Team**, e **dati**. Ad esempio, si riferiscono a sottocontesto di un progetto - **eseguire il Debug**, **compilare**, **Test**, **architettura**, o **analizza** . Tra i comandi nella gerarchia di ambito sono **Aggiungi nuovo elemento**, **nuova Query**, **impostazioni di progetto**, **Aggiungi nuova origine dati**, **Avvia procedura guidata di prestazioni**, e **nuovo diagramma**.

 I comandi di **documento** act ambito sul contenuto di un documento, ad esempio di codice, progettazione o query di elemento di lavoro (. WIQ). Sono inoltre agire sulla visualizzazione di una finestra degli strumenti o in caso contrario, sono specifici di tale finestra degli strumenti. Comandi con ambito documento può essere utilizzato anche per gli oggetti di file specifici di gerarchia, ad esempio a loro volta **Rimuovi dal progetto**. Tra i comandi nel documento di ambito sono **refactoring > Rinomina**, **Crea copia di elemento di lavoro**, **Espandi tutto**, **Comprimi tutto**, e **Crea attività definita dall'utente**.

### <a name="command-placement-decisions"></a>Comando decisioni relative al posizionamento
 Dopo aver deciso di creare un comando, è necessario determinare la posizione appropriata e se si desidera creare un tasto di scelta rapida. Seguire questo percorso di decisione per stabilire dove posizionare il comando:

 ![Grafico di decisione posizione comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501 a_CommandPlacement")

 **Percorso di decisione per il posizionamento di comando in Visual Studio**

### <a name="command-placement-in-menus"></a>Commandplacement nei menu

#### <a name="main-menu-bar"></a>Barra dei menu principale
 Barra dei menu principale deve essere il percorso standard per i comandi di tutti i pacchetti dal menu specifici del contesto che contribuiscono all'interfaccia utente. Barra dei menu principale si differenzia da altre strutture di comando nell'ambiente viene utilizzato per controllare quali comandi sono visibili. Tutte le altre barre dei comandi è sufficiente disabilitare i comandi che sono fuori contesto, se vengono posizionati in un menu o in una barra degli strumenti.

 L'ambiente definisce un set di comandi compilato nella barra dei menu principale che sono comuni a più domini di attività e l'intero IDE. Questi comandi sono sempre visibili indipendentemente dal fatto che dei quali vengono caricati i pacchetti VSPackage nell'ambiente. Anche se i pacchetti VSPackage possono estendere questo set di comandi, il set di comandi in ogni prodotto e il posizionamento dei comandi sono responsabilità di ogni team.

 La struttura del menu principale di Visual Studio può essere suddivisi nelle categorie seguenti menu:

##### <a name="core-menus"></a>Menu di scelta principali

-   File

-   Modifica

-   Visualizza

-   Strumenti

-   Finestra

-   ?

##### <a name="project-specific-menus"></a>Menu specifici del progetto

-   Progetto

-   Compila

-   Debug

##### <a name="context-specific-menus"></a>Menu specifici del contesto

-   Team

-   Dati

-   Test

-   Architettura

-   Analyze

##### <a name="document-specific-menus"></a>Menu specifici del documento

-   Formato

-   Tabella

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Quando si progetta menu principali, è necessario attenersi a queste regole:

-   Non superano 25 elementi di primo livello in un determinato contesto

-   I menu non devono mai superare 600 pixel in altezza.

-   Valutare un menu principale in più contesti, ad esempio nello SKU Ultimate e il profilo generale.

-   Menu a comparsa sono accettabili.

-   Menu a comparsa devono contenere almeno tre elementi e non più di sette.

-   Menu a comparsa devono passare un solo livello profonde: alcune voci di menu di Visual Studio dispongano sottomenu CSS, ma non è consigliabile in questo modello.

-   Usare i separatori non più di sei. Raggruppamenti devono rispettare la figura seguente:

     ![Linee guida per il raggruppamento di menu principale](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501 b_MainMenus")

-   Anche se non è necessario disporre di ogni raggruppamento nella figura, l'aggiunta di raggruppamenti aggiuntivi è limitato.

-   Ogni raggruppamento deve avere da due a sette voci di menu.

#### <a name="main-menu-ordering"></a>Menu principale di ordinamento
 Prima di aggiungere un nuovo elemento di primo livello, è consigliabile inserire il comando in un menu di primo livello esistente. Quando si aggiunge un nuovo menu di primo livello, assicurarsi di inserirlo nella posizione corretta. Decidere se il menu di scelta è specifico di progetto, contesto o nel documento. Che il nome del menu di primo livello concisa e usare solo una parola.

 I menu principali devono delimitatore il resto dei comandi. File, modifica e visualizzazione deve essere sempre a sinistra, quindi Strumenti, finestra e della Guida in linea deve essere sempre a destra.

#### <a name="context-menus"></a>Menu di scelta rapida
 Inserimento di una quantità eccessiva funzionalità all'interno di menu di scelta rapida risultati in un'interfaccia difficili da apprendere. Tutte le funzionalità principali devono essere disponibile tramite la barra dei menu principale. Posizionamento dei comandi deve essere riconciliato con i comandi esistenti per evitare duplicati comandi. Per i menu di scelta rapida, la shell definisce i gruppi di menu standard che devono essere inclusi, a seconda che il menu di scelta rapida sia per la soluzione, un nodo del progetto o un elemento del progetto.

 Quando si progettano i menu di scelta rapida, rispettare le stesse regole per il menu principale e inoltre:

-   Non superano 25 voci di menu di primo livello.

-   Menu a comparsa sono accettabili, ma deve non superano un livello di profondità - non usare mai riquadri a comparsa a catena.

-   Usare i separatori non più di sei.

### <a name="command-placement-in-toolbars"></a>Commandplacement nelle barre degli strumenti

#### <a name="general-toolbars"></a>Barre degli strumenti generale
 Durante la progettazione e la disposizione delle barre degli strumenti, seguire questi standard:

-   Non usare più di un verbo al pulsante. Un unico pulsante = una sola azione.

-   Usare testo con l'icona solo se è necessario essere rafforzata con l'etichetta.

-   Usare una casella combinata esclusivamente per le proprietà che verranno passate più volte in una sessione. In caso contrario, espongono la proprietà in un' posizione.

-   La larghezza di una casella combinata dovrebbe corrispondere la larghezza dell'elemento più lungo entro la casella + 30%. Ad esempio, se l'elemento più lungo è di 200 pixel, della casella combinata deve essere 260 pixel di larghezza.

-   Limitare l'uso di separatori. L'uso di un separatore accanto a un elenco a discesa è un antipattern, perché la forma di elenco a discesa stesso agisce come un separatore visivo.

-   I gruppi di icona devono contenere da tre a sei icone.

-   Se i qualificatori comportano più utili comandi, usare un pulsante a cui è archiviato l'ultima impostazione:

     ![Suddividere i pulsanti in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501 c_SplitButtons")

     **Esempio di un pulsante di menu combinato. I sei comandi sulla sinistra invece possono rientrare in un unico pulsante.**

#### <a name="product-specific-toolbars"></a>Barre degli strumenti specifici del prodotto
 Ogni prodotto può fornire una barra degli strumenti predefinita che contiene più frequente e comandi importanti e barra degli strumenti predefinita di ogni prodotto deve essere visualizzato la prima volta Visual Studio viene avviato dopo il prodotto sia installato.

 Prodotti devono anche sfruttare i gruppi di comandi condivisi e i menu forniti dall'IDE. Ogni gruppo di comandi condiviso viene inserito in un menu condiviso lo scopo di organizzare i comandi correlati in modo significativo per l'utente. È importante sfruttare questa struttura dei comandi condivisi per ridurre la complessità.

#### <a name="global-toolbars"></a>Barre degli strumenti globale
 Le barre degli strumenti globale sono necessari per adattarsi a destra di una riga predefinita. Quando si crea una nuova barra degli strumenti globale, seguire le linee guida per tale tipo di barra degli strumenti.

 **Linee guida generali sulla barra degli strumenti:**

- Ogni barra degli strumenti dispone di 24 pixel common Controls (gripper, overflow).

- Ogni pulsante sulla barra degli strumenti è 22 pixel in larghezza include spaziature interne. Effettua l'icona di un pulsante di menu combinato consente di aggiungere un altro 11 pixel di larghezza.

- È consentita la duplicazione di comandi tra le barre degli strumenti.

  **Barre degli strumenti specifici del documento** vengono visualizzati quando un determinato tipo è attivo e scompare quando un tipo di file diversi diventa attivo.

- Barre degli strumenti specifici del documento non può avere più di 12 pulsanti.

- La larghezza totale della barra degli strumenti non può superare i 300 pixel.

- Ogni tipo di file può avere uno degli strumenti incorporata o una barra degli strumenti globale specifica del documento, ma non entrambi.

  **Barre degli strumenti specifici per il contesto** vengono visualizzati quando un determinato contesto sia impostato e tendono a rimanere attivi per lunghi periodi di tempo.

- Il limite di pulsante per tutte le barre degli strumenti specifici per il contesto è 18.

- Se la maggior parte degli utenti in modo coerente non utilizzano i comandi della barra degli strumenti quando il contesto è attivo, quindi non associare questa barra degli strumenti con un contesto.

- Assicurarsi che la barra degli strumenti scomparirà quando si esce dal contesto. Nessuna di queste barre degli strumenti deve essere visualizzato all'avvio.

  **Le barre degli strumenti senza alcun contesto** non vengono mai visualizzati automaticamente. Viene visualizzata solo quando l'utente li attiva. Conservare la larghezza massima di sotto di 200 pixel.

### <a name="general-organization-and-shell-defined-groups"></a>Organizzazione generale e gruppi definiti shell
 Usare i comandi condivisi esistenti, gruppi di comandi e menu. Se è necessario definire un nuovo comando, provare a inserirlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, provare a inserirlo in un menu condiviso esistente vicino a un gruppo di comandi correlati prima di creare un nuovo menu di primo livello. In questo modo si riduce la complessità di comando, garantendo commandplacement coerenti nell'IDE.

 Condiviso **formato** menu, in genere presentato nel contesto delle finestre di documento basato su finestra di progettazione, è illustrato nell'immagine seguente:

 ![Menu di Visual Studio formato con callout](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501 d_FormatMenu")

 **Gruppi di menu in Visual Studio**

### <a name="reducing-and-reusing-commands"></a>La riduzione e il riutilizzo dei comandi
 I comandi sono in genere visualizzati in basati sul contesto, per ridurre il numero di comandi che viene visualizzato in un determinato momento. Tuttavia, è anche necessario riusare i menu condivisi esistenti e i gruppi di comandi per assicurarsi che la struttura del comando rimane relativamente stabili tra le modifiche nel contesto.

 Riutilizzo di comandi condivisi e l'inserimento di nuovi comandi vicino i comandi correlati alla condivisi riduce la complessità dell'IDE e crea un'esperienza più semplice.

## <a name="naming-commands"></a>Denominazione dei comandi

### <a name="naming-conventions"></a>Convenzioni di denominazione
 Comando coerente di denominazione è fondamentale in modo che gli utenti possono trovare ed eseguire i comandi, da riga di comando o associazione a tasti di scelta rapida. I nomi dei comandi consenta anche all'utente di comprendere quale scopo un comando viene usato quando viene visualizzato in una barra degli strumenti o in un menu di scelta rapida o di propagazione.

#### <a name="when-naming-commands"></a>Denominazione dei comandi quando:

-   Creare testo in modo da facilitarne la localizzazione. Per altre informazioni sulla localizzazione del testo, vedere [suggerimenti per la localizzazione](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

-   Essere concisi. I comandi devono utilizzare non più di tre parole.

-   Usare tutte le iniziali maiuscole maiuscole/minuscole: deve essere in maiuscolo la prima lettera di ogni parola. Per altre informazioni sulla formattazione del testo in Visual Studio, vedere [stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

-   Prendere in considerazione in cui verrà inserito il comando. È in un menu di primo livello o un riquadro a comparsa? Ad esempio, quando i comandi di allineamento di raggruppamento nel riquadro a comparsa, i comandi di primo livello devono essere "Allineamento" e i comandi di menu a comparsa dovrebbe essere "Left" "Destra", "Center", "giustifica" e così via. Sarebbe ridondante per denominare i comandi di menu a comparsa "Allinea a sinistra" o "Right Align."

     ![Menu di Visual Studio formato](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502 a_FormatMenu")

### <a name="using-icons-with-commands"></a>Usare le icone con comandi
 Essere riserva nell'uso dell'icona associazione con i comandi. Anche se l'associazione di un'immagine univoca con un comando opzione possibilità dell'utente per identificare tale comando, confusioni a livello visivo e inefficienza si verificano con utilizzo eccessivo di immagini. Le regole seguenti utili per decidere se creare un'icona del comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Usare un'icona con un comando solo se:

-   Lo stesso comando contiene un'icona associata in un altro prodotto Microsoft notificate all'utente, ad esempio quello delle applicazioni di Microsoft Office.

-   Il comando verrà inserito in una barra degli strumenti predefinita.

-   Il comando è una specializzazione che gli utenti possono aggiungere a una barra degli strumenti usando la **"In corso personalizzare"** finestra di dialogo.

## <a name="access-and-shortcut-keys"></a>Tasti di scelta rapida e accesso

### <a name="overview"></a>Panoramica
 Esistono due tipi di chiave da tastiera:

-   **Le chiavi di accesso** (noto anche come tasti di scelta rapida) consentono l'accesso della tastiera tramite i menu di scelta per l'esecuzione di comandi e a ogni etichetta nella finestra di dialogo dell'interfaccia utente. Le chiavi di accesso sono principalmente a scopo di accessibilità, vengono assegnate a tutti i menu e la maggior parte dei controlli di finestre di dialogo, non sono pensate per essere memorizzate, interessano solo la finestra corrente e sono localizzate.

-   **Tasti di scelta rapida** usato principalmente controllo (Ctrl) e le sequenze di tasti funzione (Fn). Sono più progettati per gli utenti avanzati e aiuto della produttività. Essi vengono assegnati solo per i comandi utilizzati più frequentemente e consentire l'accesso rapido, bypassando nel menu principale. Tasti di scelta rapida sono destinati a essere memorizzate, e per tale motivo deve essere assegnato coerente con lo schema di profilo. Gli schemi di tasti di scelta rapida possono variare da un profilo a profilo. Un utente può personalizzare i tasti di scelta rapida attraverso **strumenti > Opzioni > tastiera**.

### <a name="assigning-access-keys"></a>Assegnazione di chiavi di accesso
 Le chiavi di accesso sono costituiti da chiavi Alt più caratteri alfanumeriche. Assegnare una chiave di accesso per ogni voce di menu senza eccezioni. Seguire le convenzioni comuni per l'assegnazione di chiavi di accesso e Windows. ad esempio, la chiave di accesso per **File > New** deve essere sempre **Alt, F, N**.

 Non utilizzare single-pixel-width lettere, ad esempio 'i' (in maiuscolo o minuscola) o minuscolo "l" ed evitare l'utilizzo di caratteri con tratti discendenti (g j, p, q e y) come queste sono difficili da distinguere.

 Evitare di usare le chiavi duplicate quando possibile. Nei casi in cui è inevitabile la duplicazione, il sistema di menu gestisce i conflitti da scorrere tutti i comandi che usano la chiave. Ad esempio, per un ipotetico "Number" comando nel menu File che coincide con la chiave di accesso "N", **Alt, F, N** creerà un nuovo file, e **Alt, F, N, N=10** eseguirà il comando "Number".

### <a name="assigning-shortcut-keys"></a>Assegnazione di tasti di scelta rapida
 Evitare di assegnare nuovi tasti di scelta rapida, perché non sono necessarie per ogni comando e imposta il sistema (e la memoria di utente) se eccessivo. I dati dal miglioramento programma (CEIP) indicano che gli utenti di Visual Studio usare solo un piccolo subset delle scelte rapide integrate.

 Quando si definiscono i tasti di scelta rapida, seguire queste regole:

- **Usare il controllo (Ctrl) e le sequenze di tasti funzione (Fn).**

- **Mantenere i tasti di scelta rapida utilizzati di frequente.** Consente di gestire i collegamenti più diffusi.

- **Semplificano al tipo di editor tasti di scelta rapida.** Eseguire l'associazione al tipo di scelta rapida ai comandi che gli sviluppatori più durante la scrittura di codice necessitano. Ad esempio, **Edit.InvokeSmartTag** deve avere un tasto di scelta rapida, ad esempio Ctrl + / e non Alt + Maiusc + F10.

- **Cercare di mantenere in modo coerente con tema tasti di scelta rapida.**

- **Attenersi alle linee guida di Windows per determinare quali modificatore tasti da adottare.** Usare le combinazioni di tasti Ctrl per i comandi che hanno effetti su larga scala, ad esempio i comandi che si applicano a un intero documento. Usare le combinazioni di tasti MAIUSC per i comandi che estendono o integrano le azioni del tasto di scelta rapida standard. Non usare le combinazioni di Ctrl + Alt.

- **Rimuovere i collegamenti estranei.** Se si dispone di una funzionalità legacy, provare a rimuovere i collegamenti che vengono usati con estrema infrequency (meno di 10 volte dai dati di analisi utilizzo software) o con gravità moderata infrequency (meno di 100 volte dai dati di analisi utilizzo software) se una chiave di accesso consente di accedere rapidamente al comando stesso. Ad esempio: C ALT, H, verrà aperto il sommario della Guida /.

  Non esiste un modo semplice per verificare la disponibilità di scelta rapida. Se si desidera aggiungere un collegamento, seguire questa procedura:

1.  Controllare l'elenco degli [scelte rapide di Visual Studio 2013](http://visualstudioshortcuts.com/2013/) per determinare se sono presenti comandi simili a quelle in uso con gruppo.

2.  Passare a **strumenti > Opzioni > ambiente > tasti** e testare il collegamento. Selezionare che ogni schema di mappatura della tastiera elencato in "Applica il seguente schema di mappatura della tastiera aggiuntive". Controllare i profili in generale, c#, VB e C++, come quelle condivise tasti di scelta rapida univoci. Il collegamento è disponibile se non è mappata in una qualsiasi di queste posizioni.