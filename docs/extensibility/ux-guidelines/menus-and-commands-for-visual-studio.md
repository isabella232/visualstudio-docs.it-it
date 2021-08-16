---
title: Menu e comandi per Visual Studio | Microsoft Docs
description: Informazioni su come le barre dei comandi offrono flessibilità nell'interfaccia utente quando si creano nuove funzionalità per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f137ba0db635587824ef0b574e090b8ba2b806d37855cd23a12978675ee8a81a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305113"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu e comandi per Visual Studio
## <a name="command-usage"></a>Utilizzo dei comandi

### <a name="overview"></a>Panoramica
 A Microsoft Office, che è una suite che comprende molti prodotti separati, Visual Studio contiene molti prodotti che ognuno contribuisce ai propri set di comandi nell'IDE Visual Studio globale. L'IDE gestisce la complessità di migliaia di comandi filtrando le funzionalità disponibili per l'utente in base al contesto.

 Quando il contesto di un utente cambia, ad esempio passando da una finestra di progettazione a una finestra di modifica del codice, la funzionalità non correlata al nuovo contesto scompare. Allo stesso tempo, le nuove funzionalità vengono visualizzate insieme alle informazioni dinamiche correlate, ad esempio proprietà e opzioni della casella degli strumenti. L'utente non dovrebbe notare lo scambio del set di comandi disponibile. Se l'utente è distratto o confuso dai comandi che appaiono o scompaiono, la progettazione dell'interfaccia utente deve essere regolata. Il contesto corrente dell'utente è sempre indicato in uno o più modi, ad esempio nella barra del titolo dell'IDE, nel Finestra Proprietà o nella finestra di dialogo Pagine delle proprietà.

 Le barre dei comandi offrono flessibilità nell'interfaccia utente. Le uniche strutture di comando intrinseche all'ambiente Visual Studio sono il menu principale e la barra dei comandi principale, che possono essere personalizzati e persino nascosti. Le altre barre dei comandi vengono visualizzate e scompaiono in base allo stato dell'applicazione. Le finestre degli strumenti e gli editor di documenti possono anche contenere barre degli strumenti incorporate all'interno dei bordi delle finestre.

#### <a name="basic-guidelines"></a>Linee guida di base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Quando possibile, usare comandi condivisi, gruppi di comandi e menu esistenti.
 Poiché i comandi vengono in genere visualizzati in base al contesto, l'uso di menu condivisi e gruppi di comandi esistenti garantisce che la struttura dei comandi rimanga relativamente stabile tra le modifiche nel contesto. Il riutilizzo dei comandi condivisi e l'inserimento di nuovi comandi vicini ai comandi condivisi correlati riducono anche la complessità dell'IDE e creano un'esperienza più semplice da usare. Se è necessario definire un nuovo comando, provare a posizionarlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, posizionarlo in un menu condiviso esistente vicino a un gruppo di comandi correlato prima di creare un nuovo menu di primo livello.

##### <a name="do-not-create-icons-for-every-command"></a>Non creare icone per ogni comando.
 Valutare attentamente prima di creare un'icona di comando. Le icone devono essere create solo per i comandi che:

- vengono visualizzati su una barra degli strumenti predefinita.

- È probabile che gli utenti aggienino gli utenti a una barra degli strumenti tramite la **finestra di dialogo** Personalizza.

- hanno un'icona associata alla stessa azione in un altro prodotto Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitare l'aggiunta di tasti di scelta rapida
 La maggior parte degli utenti usa una piccola frazione di tutti i tasti di scelta rapida disponibili. In caso di dubbi, non associare la funzionalità a un tasto di scelta rapida. Collaborare con il team dell'esperienza utente prima di aggiungere nuovi collegamenti.

##### <a name="give-commands-a-default-menu-placement"></a>Assegnare ai comandi una posizione di menu predefinita.
 Tenere presente che i comandi verranno personalizzati da altri utenti e progettarli di conseguenza. Non esiste un comando nascosto. Tutti Visual Studio comandi vengono visualizzati nella finestra di dialogo Strumenti > Personalizza, nella finestra di comando, nel completamento automatico, nella finestra di dialogo Strumenti **>** Opzioni **>** tastiera e in Ambiente strumenti di sviluppo (DTE). Assicurarsi di assegnare ai comandi un nome e una descrizione comando nel file con estensione ctc in modo che gli utenti possano trovarli facilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Non duplicare i comandi condivisi in una barra degli strumenti incorporata.
 È utile posizionare i comandi in prossimità dell'area dello stato attivo dell'utente. Un modo per eseguire questa operazione è creare una barra degli strumenti incorporata nella parte superiore della finestra degli strumenti o dell'editor di documenti. I comandi posizionati sulla barra degli strumenti devono essere specifici dell'area del contenuto all'interno della finestra. Non duplicare i comandi condivisi su queste barre degli strumenti. Ad esempio, non inserire mai un'icona "Salva" all'interno di una barra degli strumenti incorporata.

### <a name="content-and-command-visibility"></a>Visibilità del contenuto e dei comandi
 I comandi sono presenti negli ambiti seguenti: **Ambiente**, **Gerarchia** e **Documento**. Conoscere ogni ambito per avere fiducia nel posizionamento dei comandi.

 I comandi **nell'ambito Ambiente** stabiliscono il contesto primario e sono condivisi tra più contesti. Modificano la visibilità o la disposizione di documenti e finestre degli strumenti. Tra i comandi nell'ambito dell'ambiente ci sono New **Project**, **Connessione to Server**, Attach **Process**, **Cut**, Copy , **Paste**, **Find**, **Options**, **Customize**, **New Window** e **View Help**. 

 I comandi **nell'ambito Gerarchia** gestiscono le gerarchie in Visual Studio inclusi **Project**, **Team** e **Dati**. Sono correlate al sottocontesto di un progetto, ad esempio **Debug**, **Build**, **Test**, **Architecture** o **Analyze.** Tra i comandi nell'ambito gerarchia sono Aggiungi nuovo elemento **,** Nuova **query**, Project Impostazioni **,** **Aggiungi** nuova origine dati **,** Avvio guidato prestazioni e Nuovo **diagramma**.

 I comandi **nell'ambito** del documento agiscono sul contenuto di un documento, ad esempio codice, progettazione o una query elemento di lavoro (WIQ). Agiscono anche sulla visualizzazione di una finestra degli strumenti o sono altrimenti specifici di tale finestra. I comandi relativi all'ambito del documento agiscono anche sugli oggetti file a loro volta specifici della gerarchia, ad esempio **Remove from Project**. Tra i comandi nell'ambito del documento sono **refactoring > Rinomina** **,** Crea copia dell'elemento di lavoro **,** Espandi tutto , Comprimi **tutto** e Crea **attività utente**.

### <a name="command-placement-decisions"></a>Decisioni relative al posizionamento dei comandi
 Dopo aver deciso di creare un comando, è necessario determinarne la posizione appropriata e se creare un tasto di scelta rapida. Seguire questo percorso decisionale per stabilire dove posizionare il comando:

 ![Grafico di decisione posizione comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Percorso decisionale per il posizionamento dei comandi in Visual Studio**

### <a name="command-placement-in-menus"></a>Posizionamento dei comandi nei menu

#### <a name="main-menu-bar"></a>Barra dei menu principale
 La barra dei menu principale deve essere la posizione standard per i comandi di qualsiasi pacchetto di menu specifico del contesto che contribuisce all'interfaccia utente. La barra dei menu principale è diversa dalle altre strutture dei comandi in quanto l'ambiente la usa per controllare quali comandi sono visibili. Tutte le altre barre dei comandi disabilitano semplicemente i comandi non contestuali, indipendentemente dal fatto che siano posizionati in un menu o in una barra degli strumenti.

 L'ambiente definisce un set di comandi incorporati nella barra dei menu principale comuni nell'intero IDE e in più domini attività. Questi comandi sono sempre visibili indipendentemente da quali VSPackage vengono caricati nell'ambiente. Anche se i pacchetti VSPackage possono estendere questo set di comandi, il set di comandi di ogni prodotto e il posizionamento dei comandi sono responsabilità di ogni team.

 La struttura del menu Visual Studio menu principale può essere suddivisa nelle categorie di menu seguenti:

##### <a name="core-menus"></a>Menu principali

- File

- Modifica

- Visualizzazione

- Strumenti

- Finestra

- Help

##### <a name="project-specific-menus"></a>Project specifici dei menu

- Project

- Compilazione

- Debug

##### <a name="context-specific-menus"></a>Menu specifici del contesto

- Team

- Dati

- Test

- Architettura

- Analizzare

##### <a name="document-specific-menus"></a>Menu specifici del documento

- Formato

- Tabella

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Quando si progettano i menu principali, rispettare queste regole:

- Non superare 25 elementi di primo livello in un determinato contesto

- I menu non devono mai superare i 600 pixel di altezza.

- Valutare un menu principale in più contesti, ad esempio nello SKU Ultimate e nel profilo generale.

- I menu a comparsa sono accettabili.

- I menu a comparsa devono contenere almeno tre elementi e non più di sette.

- I menu a comparsa devono avere un solo livello di profondità: alcune Visual Studio di menu hanno sottomenu a cascata, ma questo modello non è consigliato.

- Non usare più di sei separatori. I raggruppamenti devono essere conformi alla figura seguente:

     ![Indicazioni per il raggruppamento dei menu principali](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Anche se non è necessario che ogni raggruppamento sia presente nella figura, l'aggiunta di altri raggruppamenti è limitata.

- Ogni raggruppamento deve avere da due a sette voci di menu.

#### <a name="main-menu-ordering"></a>Ordinamento del menu principale
 Prima di aggiungere un nuovo elemento di primo livello, è consigliabile inserire il comando in un menu di primo livello esistente. Quando si aggiunge un nuovo menu di primo livello, assicurarsi di posizionarlo nella posizione corretta. Decidere se il menu è specifico del progetto, del contesto o del documento. Mantenere conciso il nome del menu di primo livello e usare una sola parola.

 I menu principali dovrebbero contenere il resto dei comandi. File, Modifica e Visualizza devono essere sempre a sinistra e Strumenti, Finestra e Guida devono essere sempre a destra.

#### <a name="context-menus"></a>Menu di scelta rapida
 L'inserimento di troppe funzionalità all'interno dei menu di scelta rapida comporta un'interfaccia di difficile apprendimento. Tutte le funzionalità principali devono essere disponibili tramite la barra dei menu principale. Il posizionamento dei comandi deve essere riconciliato con i comandi esistenti per evitare comandi duplicati. Per i menu di scelta rapida, la shell definisce gruppi di menu standard che devono essere inclusi a seconda che il menu di scelta rapida sia per la soluzione, un nodo di progetto o un elemento di progetto.

 Quando si progettano menu di scelta rapida, rispettare le stesse regole del menu principale e:

- Non superare le 25 voci di menu di primo livello.

- I menu a comparsa sono accettabili, ma non devono superare un livello di profondità. Non usare mai riquadri a comparsa a cascata.

- Non usare più di sei separatori.

### <a name="command-placement-in-toolbars"></a>Posizionamento dei comandi nelle barre degli strumenti

#### <a name="general-toolbars"></a>Barre degli strumenti generali
 Quando si progettano e si dispone le barre degli strumenti, seguire questi standard:

- Non usare più di un verbo per pulsante. Un pulsante = un'azione.

- Usare il testo insieme all'icona solo se deve essere rinforzato con l'etichetta.

- Usare una casella combinata esclusivamente per le proprietà che verranno cambiate più volte in una sessione. In caso contrario, esporre la proprietà altrove.

- La larghezza di una casella combinata deve essere uguale alla larghezza dell'elemento più lungo all'interno della casella + 30%. Ad esempio, se l'elemento più lungo è 200 pixel, la casella combinata deve avere una larghezza di 260 pixel.

- Limitare l'uso dei separatori. L'uso di un separatore accanto a un elenco a discesa è un anti-pattern, perché la forma dell'elenco a discesa stesso funge da separatore visivo.

- I gruppi di icone devono contenere da tre a sei icone.

- Se i qualificatori comportano più comandi utili, usare un pulsante di menu suddiviso che archivia l'ultima impostazione:

     ![Pulsanti di menu combinati in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Esempio di pulsante di menu suddiviso. I sei comandi a sinistra possono invece rientrare in un singolo pulsante.**

#### <a name="product-specific-toolbars"></a>Barre degli strumenti specifiche del prodotto
 Ogni prodotto può fornire una barra degli strumenti predefinita che contiene comandi importanti e usati di frequente. La barra degli strumenti predefinita di ogni prodotto deve essere visualizzata al primo avvio di Visual Studio dopo l'installazione del prodotto.

 I prodotti devono anche sfruttare i gruppi di comandi condivisi e i menu forniti dall'IDE. Ogni gruppo di comandi condiviso viene inserito in un menu condiviso destinato a organizzare i comandi correlati in modo significativo per l'utente. È importante sfruttare questa struttura di comandi condivisi per ridurre la complessità.

#### <a name="global-toolbars"></a>Barre degli strumenti globali
 Le barre degli strumenti globali devono essere adattate direttamente a una riga. Quando si crea una nuova barra degli strumenti globale, seguire le linee guida per tale tipo di barra degli strumenti.

 **Linee guida generali sulla barra degli strumenti:**

- Ogni barra degli strumenti ha 24 pixel nei controlli comuni (gripper, overflow).

- Ogni pulsante della barra degli strumenti ha una larghezza di 22 pixel, inclusa la spaziatura interna. Se si rende l'icona un pulsante di menu suddiviso, vengono aggiunti altri 11 pixel di larghezza.

- È consentita la duplicazione dei comandi tra le barre degli strumenti.

  **Le barre degli strumenti specifiche del documento** vengono visualizzate quando un determinato tipo di file è attivo e scompaiono quando un tipo di file diverso diventa attivo.

- Le barre degli strumenti specifiche del documento potrebbero non avere più di 12 pulsanti.

- La larghezza totale della barra degli strumenti non può superare i 300 pixel.

- Ogni tipo di file può avere una barra degli strumenti incorporata o una barra degli strumenti globale specifica del documento, ma non entrambe.

  **Le barre degli strumenti specifiche del contesto** vengono visualizzate quando è impostato un determinato contesto e tendono a rimanere attive per periodi prolungati.

- Il limite dei pulsanti per tutte le barre degli strumenti specifiche del contesto è 18.

- Se la maggior parte degli utenti non usa in modo coerente i comandi di questa barra degli strumenti quando il contesto è attivo, non associarla a un contesto.

- Assicurarsi che la barra degli strumenti scompaia quando si esce dal contesto. Nessuna di queste barre degli strumenti dovrebbe essere visualizzata all'avvio.

  **Le barre degli strumenti senza contesto non** vengono mai visualizzate automaticamente. Vengono visualizzati solo quando l'utente li attiva. Mantenere la larghezza massima inferiore a 200 pixel.

### <a name="general-organization-and-shell-defined-groups"></a>Organizzazione generale e gruppi definiti dalla shell
 Usare comandi condivisi, gruppi di comandi e menu esistenti. Se è necessario definire un nuovo comando, provare a posizionarlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, provare a posizionarlo in un menu condiviso esistente vicino a un gruppo di comandi correlato prima di creare un nuovo menu di primo livello. In questo modo si riduce la complessità dei comandi assicurando al tempo stesso un posizionamento coerente dei comandi nell'IDE.

 Il menu **Formato** condiviso, in genere visualizzato nel contesto delle finestre di documento in stile finestra di progettazione, è illustrato nell'immagine seguente:

 ![Menu Formato con callout di Visual Studio](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Gruppi di menu in Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Riduzione e riutilizzo dei comandi
 I comandi vengono in genere visualizzati in base al contesto, per ridurre il numero di comandi visualizzati dall'utente in un determinato momento. È tuttavia consigliabile riutilizzare anche i menu condivisi e i gruppi di comandi esistenti per garantire che la struttura dei comandi rimanga relativamente stabile tra le modifiche nel contesto.

 Il riutilizzo dei comandi condivisi e l'inserimento di nuovi comandi vicino ai comandi condivisi correlati riducono la complessità dell'IDE e creano un'esperienza più semplice.

## <a name="naming-commands"></a>Comandi di denominazione

### <a name="naming-conventions"></a>Convenzioni di denominazione
 La denominazione coerente dei comandi è fondamentale in modo che gli utenti possano trovare ed eseguire comandi, tramite la riga di comando o l'associazione a un tasto di scelta rapida. I nomi dei comandi consentono anche all'utente di comprendere lo scopo di un comando quando viene visualizzato su una barra degli strumenti o in un menu a cascata o di scelta rapida.

#### <a name="when-naming-commands"></a>Quando si assegnano nomi ai comandi:

- Costruire il testo in modo che sia facilmente localizzabile. Per altre informazioni sulla localizzazione del testo, vedere [Procedure consigliate per la localizzazione.](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)

- Essere concisi. I comandi non devono usare più di tre parole.

- Usare l'uso di maiuscole/minuscole per il titolo: la prima lettera di ogni parola deve essere maiuscola. Per altre informazioni sulla formattazione del testo in Visual Studio, vedere [Stile del testo.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

- Prendere in considerazione la posizione in cui verrà inserito il comando. Si trova in un menu di primo livello o in un riquadro a comparsa? Ad esempio, quando si raggruppano i comandi di allineamento in un riquadro a comparsa, il comando di primo livello deve essere "Allinea" e i comandi del riquadro a comparsa devono essere "Left", "Right", "Center", "Justify" e così via. Sarebbe ridondante assegnare ai comandi del riquadro a comparsa il nome "Allinea a sinistra" o "Allinea a destra".

     ![Menu Formato di Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Uso delle icone con i comandi
 Evitare di usare l'associazione di icone con i comandi. Anche se l'associazione di un'immagine univoca a un comando accelera la capacità dell'utente di identificare tale comando, la confusione visiva e l'inefficienza si verificano con l'uso eccessivo dell'immagine. Le regole seguenti consentono di decidere se creare un'icona di comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Usare un'icona con un comando solo se:

- Allo stesso comando è associata un'icona in un altro prodotto Microsoft importante, ad esempio una delle Microsoft Office applicazioni.

- Il comando verrà inserito in una barra degli strumenti predefinita.

- Il comando è un comando speciale che gli utenti probabilmente aggiungeranno a una barra degli strumenti usando la **finestra di dialogo "Personalizza".**

## <a name="access-and-shortcut-keys"></a>Tasti di scelta e tasti di scelta rapida

### <a name="overview"></a>Panoramica
 Esistono due tipi di assegnazioni di tasti da tastiera:

- **I tasti di** scelta (noti anche come tasti di scelta rapida) consentono l'accesso tramite tastiera tramite i menu per l'esecuzione di comandi e per ogni etichetta nell'interfaccia utente della finestra di dialogo. I tasti di scelta sono principalmente per scopi di accessibilità, vengono assegnati a tutti i menu e la maggior parte dei controlli delle finestre di dialogo, non devono essere memorizzati, influiscono solo sulla finestra corrente e vengono localizzati.

- **I tasti di** scelta rapida usano principalmente le sequenze di tasti Ctrl (CTRL) e Funzione (Fn). Sono progettati in modo più avanzato per gli utenti avanzati e consentono di migliorare la produttività. Vengono assegnati solo ai comandi usati più di frequente e consentono l'accesso rapido ignorando il menu principale. I tasti di scelta rapida devono essere memorizzati e per questo motivo devono essere assegnati in modo coerente con lo schema del profilo. Gli schemi dei tasti di scelta rapida possono variare da profilo a profilo. Un utente può personalizzare i tasti di scelta rapida **tramite Strumenti > opzioni > tastiera**.

### <a name="assigning-access-keys"></a>Assegnazione di chiavi di accesso
 I tasti di scelta sono costituiti da ALT e da tasti alfanumerici. Assegnare una chiave di accesso a ogni voce di menu senza eccezioni. Seguire Windows convenzioni comuni per l'assegnazione delle chiavi di accesso. Ad esempio, la chiave di accesso per **File > New** deve essere sempre **ALT, F, N**.

 Non usare lettere a larghezza singola di pixel, ad esempio "i" (in lettere maiuscole o minuscole) o una "l" minuscola ed evitare l'uso di caratteri con discendenti (g, j, p, q e y), in quanto sono difficili da distinguere.

 Evitare di usare chiavi duplicate quando possibile. Nei casi in cui la duplicazione è inevitabile, il sistema di menu gestisce i conflitti ciclicamente attraverso tutti i comandi che usano la chiave. Ad esempio, per un ipotetico comando "Number" nel menu File che duplica il tasto di scelta "N", **Alt, F, N** creerebbe un nuovo file e **ALT, F, N, N** eseguirebbe il comando "Number".

### <a name="assigning-shortcut-keys"></a>Assegnazione di tasti di scelta rapida
 Evitare di assegnare nuovi tasti di scelta rapida, perché non sono necessari per ogni comando e impostano il sistema (e la memoria utente) in caso di sovrautilizzato. I dati del Analisi utilizzo software (Analisi utilizzo software) indicano che Visual Studio utenti usano solo un piccolo subset dei collegamenti integrati.

 Quando si definiscono i collegamenti, seguire queste regole:

- **Usare ctrl (CTRL) e sequenze di tasti funzione (Fn).**

- **Mantenere i tasti di scelta rapida usati di frequente.** Mantenere i tasti di scelta rapida più diffusi.

- **Semplificare la digitazione dei tasti di scelta rapida dell'editor.** Associare tasti di scelta rapida di facile digitazione ai comandi più necessari agli sviluppatori durante la scrittura del codice. Ad esempio, **Edit.InvokeSmartTag** deve avere un tasto di scelta rapida come CTRL+/ e non ALT+MAIUSC+F10.

- **Cercare collegamenti a t-to-them coerenti.**

- **Seguire Windows linee guida per determinare quali tasti di modifica usare.** Usare combinazioni di tasti CTRL per i comandi con effetti su larga scala, ad esempio comandi che si applicano a un intero documento. Usare combinazioni di tasti MAIUSC per i comandi che estendono o completano le azioni del tasto di scelta rapida standard. Non usare combinazioni CTRL+ALT.

- **Rimuovere i collegamenti estranei.** Se si dispone di una funzionalità legacy, è consigliabile rimuovere i collegamenti usati con estrema poco frequente (meno di 10 volte dai dati di Analisi utilizzo software) o moderare la raranza (meno di 100 volte dai dati di Analisi utilizzo software) se una chiave di accesso fornisce l'accesso rapido allo stesso comando. Ad esempio: ALT, H, C aprirà Guida/Contenuto.

  Non esiste un modo semplice per controllare la disponibilità dei collegamenti. Se si vuole aggiungere un collegamento, seguire questa procedura:

1. Controllare l'elenco [Visual Studio 2013 tasti di scelta](http://visualstudioshortcuts.com/2013/) rapida per determinare se sono disponibili comandi simili con cui raggruppare i comandi.

2. Passare a **Strumenti > opzioni > ambiente > tastiera** e testare il collegamento. Controllare ogni schema di mapping della tastiera elencato in "Applicare lo schema di mapping della tastiera aggiuntivo seguente". Selezionare i profili Generale, C#, VB e C++, in quanto condividono collegamenti univoci. Il collegamento è disponibile se non è mappato in nessuna di queste posizioni.
