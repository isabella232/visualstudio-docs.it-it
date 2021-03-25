---
title: Menu e comandi per Visual Studio | Microsoft Docs
description: Informazioni su come le barre dei comandi consentono flessibilità nell'interfaccia utente quando si creano nuove funzionalità per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1061de343ae24dce163dd0a7665d58ec7aac3a3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068388"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menu e comandi per Visual Studio
## <a name="command-usage"></a>Utilizzo comando

### <a name="overview"></a>Panoramica
 A differenza di Microsoft Office, ovvero una suite che comprende molti prodotti distinti, Visual Studio contiene molti prodotti che contribuiscono a tutti i set di comandi all'IDE globale di Visual Studio. L'IDE gestisce la complessità di migliaia di comandi filtrando la funzionalità disponibile per l'utente in base al contesto.

 Quando il contesto di un utente cambia, ad esempio passando da una finestra di progettazione a una finestra di modifica del codice, la funzionalità non correlata al nuovo contesto scompare. Allo stesso tempo, le nuove funzionalità vengono riportate insieme alle informazioni dinamiche correlate, ad esempio le proprietà e le opzioni della casella degli strumenti. L'utente non deve notare lo scambio del set di comandi disponibile. Se l'utente è distratto o confuso dai comandi visualizzati o scompare, è necessario regolare la progettazione dell'interfaccia utente. Il contesto corrente dell'utente è sempre indicato in uno o più modi, ad esempio nella barra del titolo IDE, nella Finestra Proprietà o nella finestra di dialogo Pagine delle proprietà.

 Le barre dei comandi consentono flessibilità nell'interfaccia utente. Le uniche strutture di comando inerenti all'ambiente di Visual Studio sono il menu principale e la barra dei comandi principale, che possono essere personalizzate e persino nascoste. Le altre barre dei comandi vengono visualizzate e scompaiono in base allo stato dell'applicazione. Le finestre degli strumenti e gli editor di documenti possono contenere anche barre degli strumenti incorporate all'interno dei bordi della finestra.

#### <a name="basic-guidelines"></a>Linee guida di base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Quando possibile, utilizzare i comandi, i gruppi di comandi e i menu condivisi esistenti.
 Poiché i comandi vengono in genere visualizzati in base al contesto, l'uso di menu condivisi e gruppi di comandi esistenti garantisce che la struttura dei comandi rimanga relativamente stabile tra le modifiche nel contesto. Il riutilizzo di comandi condivisi e l'inserimento di nuovi comandi vicino ai comandi condivisi correlati riduce anche la complessità dell'IDE e crea un'esperienza più intuitiva. Se è necessario definire un nuovo comando, provare a posizionarlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, posizionarlo in un menu condiviso esistente vicino a un gruppo di comandi correlato prima di creare un nuovo menu di primo livello.

##### <a name="do-not-create-icons-for-every-command"></a>Non creare icone per ogni comando.
 Valutare attentamente prima di creare un'icona di comando. Le icone devono essere create solo per i comandi che:

- visualizzato su una barra degli strumenti predefinita.

- è probabile che gli utenti vengano aggiunti a una barra degli strumenti tramite la finestra di dialogo **Personalizza...** .

- avere un'icona associata alla stessa azione in un altro prodotto Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitare l'aggiunta di tasti di scelta rapida
 La maggior parte degli utenti impiega una piccola frazione di tutti i tasti di scelta rapida disponibili. In caso di dubbi, non associare la funzionalità a un tasto di scelta rapida. Collaborare con il team dell'esperienza utente prima di aggiungere nuovi tasti di scelta rapida.

##### <a name="give-commands-a-default-menu-placement"></a>Assegnare ai comandi una posizione predefinita per i menu.
 Tenere presente che i comandi verranno personalizzati da altri utenti e li progettano di conseguenza. Non esiste un comando nascosto. Tutti i comandi di Visual Studio vengono visualizzati nella finestra di dialogo **strumenti > Personalizza** , nella finestra di comando, completamento automatico, **strumenti > opzioni >** finestra di dialogo tastiera e l'ambiente strumenti di sviluppo (DTE). Assicurarsi di assegnare ai comandi un nome e una descrizione comando nel file con estensione CTC in modo che gli utenti possano trovarli facilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Non duplicare i comandi condivisi su una barra degli strumenti incorporata.
 È utile posizionare i comandi in prossimità dell'area di interesse dell'utente. Un modo per eseguire questa operazione consiste nel creare una barra degli strumenti incorporata nella parte superiore della finestra degli strumenti o dell'editor di documenti. I comandi posizionati sulla barra degli strumenti devono essere specifici dell'area del contenuto all'interno della finestra. Non duplicare i comandi condivisi su queste barre degli strumenti. Ad esempio, non inserire mai un'icona "Save" all'interno di una barra degli strumenti incorporata.

### <a name="content-and-command-visibility"></a>Visibilità del contenuto e del comando
 I comandi sono disponibili negli ambiti seguenti: **ambiente**, **gerarchia** e **documento**. Conosce ogni ambito per avere confidenza nel posizionamento del comando.

 I comandi nell'ambito dell' **ambiente** definiscono il contesto primario e sono condivisi tra più contesti. Modificano la visibilità o la disposizione dei documenti e delle finestre degli strumenti. Tra i comandi nell'ambito dell'ambiente sono presenti **nuovo progetto**, **Connetti al server**, Connetti **processo**, **taglia**, **copia**, **Incolla**, **trova**, **Opzioni**, **Personalizza**, **nuova finestra** e **Visualizza Guida**.

 I comandi nell'ambito della **gerarchia** gestiscono le gerarchie in Visual Studio, inclusi il **progetto**, il **Team** e **i dati**. Sono correlati al sottocontesto di un progetto, ad esempio **debug**, **compilazione**, **test**, **architettura** o **analisi**. Tra i comandi nell'ambito della gerarchia sono **Aggiungi nuovo elemento**, **nuova query**, **Impostazioni progetto**, **Aggiungi nuova origine dati**, **Avvia Creazione guidata sessione di prestazioni** e **nuovo diagramma**.

 I comandi nell'ambito del **documento** agiscono sul contenuto di un documento, ad esempio codice, progettazione o una query elemento di lavoro (wiq). Agiscono anche sulla visualizzazione di una finestra degli strumenti o sono specifici di tale finestra degli strumenti. I comandi dell'ambito del documento agiscono anche sugli oggetti file che sono specifici della gerarchia, ad esempio **Rimuovi dal progetto**. Tra i comandi nell'ambito del documento sono **Refactor > Rinomina**, **Crea copia di elemento di lavoro**, **Espandi tutto**, **Comprimi tutto** e **Crea attività utente**.

### <a name="command-placement-decisions"></a>Decisioni sul posizionamento del comando
 Dopo aver deciso di creare un comando, è necessario determinarne il posizionamento appropriato e se creare un tasto di scelta rapida. Seguire questo percorso decisionale per stabilire dove inserire il comando:

 ![Grafico di decisione posizione comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Percorso decisionale per la selezione host dei comandi in Visual Studio**

### <a name="command-placement-in-menus"></a>Posizionamento del comando nei menu

#### <a name="main-menu-bar"></a>Barra dei menu principale
 La barra dei menu principale deve essere la posizione standard per i comandi di tutti i pacchetti di menu specifici del contesto che contribuiscono all'interfaccia utente. La barra dei menu principale è diversa dalle altre strutture di comando in quanto l'ambiente lo usa per controllare quali comandi sono visibili. Tutte le altre barre dei comandi disabilitano semplicemente i comandi che non sono contesti, indipendentemente dal fatto che vengano posizionati in un menu o in una barra degli strumenti.

 L'ambiente definisce un set di comandi incorporati nella barra dei menu principale comuni nell'intero IDE e in più domini attività. Questi comandi sono sempre visibili indipendentemente dai pacchetti VSPackage caricati nell'ambiente. Sebbene i pacchetti VSPackage possano estendere questo set di comandi, il set di comandi di ogni prodotto e il posizionamento dei comandi sono responsabili di ogni team.

 La struttura del menu principale di Visual Studio può essere suddivisa nelle categorie di menu seguenti:

##### <a name="core-menus"></a>Menu di base

- File

- Modifica

- Visualizzazione

- Strumenti

- Finestra

- Help

##### <a name="project-specific-menus"></a>Menu specifici del progetto

- Project

- Compilazione

- Debug

##### <a name="context-specific-menus"></a>Menu specifici del contesto

- Team

- Dati

- Test

- Architettura

- Analisi

##### <a name="document-specific-menus"></a>Menu specifici del documento

- Formato

- Tabella

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Quando si progettano i menu principali, attenersi a queste regole:

- Non superare 25 elementi di primo livello in un determinato contesto

- I menu non devono mai superare i 600 pixel in altezza.

- Valutare un menu principale in più contesti, ad esempio nello SKU Ultimate e nel profilo generale.

- I menu a comparsa sono accettabili.

- I menu a comparsa devono contenere almeno tre elementi e non più di sette.

- I menu a comparsa devono passare solo a un livello di profondità. alcune voci di menu di Visual Studio hanno sottomenu a cascata, ma questo modello non è consigliato.

- Non usare più di sei separatori. I raggruppamenti devono rispettare la figura seguente:

     ![Indicazioni per il raggruppamento dei menu principali](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Sebbene non sia necessario per ogni raggruppamento nella figura, l'aggiunta di ulteriori raggruppamenti è limitata.

- Ogni raggruppamento deve avere da due a sette voci di menu.

#### <a name="main-menu-ordering"></a>Ordinamento menu principale
 Prima di aggiungere un nuovo elemento di primo livello, provare a inserire il comando in un menu di primo livello esistente. Quando si aggiunge un nuovo menu di primo livello, assicurarsi di posizionarlo nella posizione corretta. Decidere se il menu è specifico per progetto, contesto o documento. Lasciare conciso il nome del menu di primo livello e usare una sola parola.

 I menu di base devono bookend il resto dei comandi. Il file, la modifica e la visualizzazione devono essere sempre a sinistra e gli strumenti, la finestra e la guida devono essere sempre a destra.

#### <a name="context-menus"></a>Menu di scelta rapida
 L'inserimento di una quantità eccessiva di funzionalità nei menu di scelta rapida comporta un'interfaccia difficile da apprendere. Tutte le funzionalità principali dovrebbero essere disponibili tramite la barra dei menu principale. Il posizionamento dei comandi deve essere riconciliato con i comandi esistenti per evitare comandi duplicati. Per i menu di scelta rapida, la shell definisce i gruppi di menu standard che devono essere inclusi a seconda che il menu di scelta rapida sia per la soluzione, un nodo di progetto o un elemento di progetto.

 Quando si progettano i menu di scelta rapida, rispettare le stesse regole del menu principale e, in aggiunta:

- Non superare 25 voci di menu di primo livello.

- I menu a comparsa sono accettabili, ma non devono superare un livello, ma non usare mai riquadri a comparsa a cascata.

- Non usare più di sei separatori.

### <a name="command-placement-in-toolbars"></a>Posizionamento del comando nelle barre degli strumenti

#### <a name="general-toolbars"></a>Barre degli strumenti generali
 Quando si progettano e si organizzano le barre degli strumenti, attenersi agli standard seguenti:

- Non usare più di un verbo per pulsante. Un pulsante = un'azione.

- Usare il testo accanto all'icona solo se deve essere rinforzato con l'etichetta.

- Usare una casella combinata esclusivamente per le proprietà che verranno scambiate più volte in una sessione. In caso contrario, esporre la proprietà altrove.

- La larghezza di una casella combinata deve essere uguale alla larghezza dell'elemento più lungo nella casella + 30%. Ad esempio, se l'elemento più lungo è 200 pixel, la casella combinata deve avere una larghezza di 260 pixel.

- Limitare l'utilizzo dei separatori. L'uso di un separatore accanto a un elenco a discesa è un anti-pattern, perché la forma dell'elenco a discesa funge da separatore visivo.

- I gruppi di icone devono contenere da tre a sei icone.

- Se i qualificatori generano più comandi utili, utilizzare un pulsante di suddivisione che archivia l'ultima impostazione:

     ![Pulsanti di menu combinati in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Esempio di pulsante di suddivisione. I sei comandi a sinistra possono invece rientrare in un singolo pulsante.**

#### <a name="product-specific-toolbars"></a>Barre degli strumenti specifiche del prodotto
 Ogni prodotto può fornire una barra degli strumenti predefinita che contiene comandi di uso frequente e importanti e la barra degli strumenti predefinita di ogni prodotto verrà visualizzata la prima volta che si avvia Visual Studio dopo l'installazione del prodotto.

 I prodotti devono inoltre sfruttare i gruppi di comandi e i menu condivisi forniti dall'IDE. Ogni gruppo di comandi condiviso viene inserito in un menu condiviso per organizzare i comandi correlati in modo significativo per l'utente. Per ridurre la complessità, è importante sfruttare questa struttura del comando condivisa.

#### <a name="global-toolbars"></a>Barre degli strumenti globali
 Le barre degli strumenti globali sono necessarie per adattarsi a una riga a destra. Quando si crea una nuova barra degli strumenti globale, attenersi alle linee guida per il tipo di barra degli strumenti.

 **Linee guida generali della barra degli strumenti:**

- Ogni barra degli strumenti ha 24 pixel nei controlli comuni (grip, overflow).

- Ogni pulsante della barra degli strumenti è di larghezza 22 pixel, inclusa la spaziatura. Se si fa in modo che l'icona venga visualizzata in un pulsante di divisione, vengono aggiunti altri 11 pixel

- È consentita la duplicazione dei comandi tra le barre degli strumenti.

  Le **barre degli strumenti specifiche del documento** vengono visualizzate quando un determinato tipo di file è attivo e scompaiono quando un tipo di file diverso diventa attivo.

- Le barre degli strumenti specifiche del documento non possono contenere più di 12 pulsanti.

- La larghezza totale della barra degli strumenti non può superare 300 pixel.

- Ogni tipo di file può avere una barra degli strumenti incorporata o una barra degli strumenti globale specifica del documento, ma non entrambe.

  Le **barre degli strumenti specifiche del contesto** vengono visualizzate quando si imposta un determinato contesto e tendono a rimanere attive per periodi prolungati.

- Il limite del pulsante per tutte le barre degli strumenti specifiche del contesto è 18.

- Se la maggior parte degli utenti non utilizzerà in modo coerente i comandi della barra degli strumenti quando il contesto è attivo, non associare la barra degli strumenti a un contesto.

- Assicurarsi che la barra degli strumenti scompaia quando si esce dal contesto. Nessuna di queste barre degli strumenti verrà visualizzata all'avvio.

  **Le barre degli strumenti senza contesto** non vengono mai visualizzate automaticamente. Questi elementi vengono visualizzati solo quando vengono attivati dall'utente. Mantieni la larghezza massima inferiore a 200 pixel.

### <a name="general-organization-and-shell-defined-groups"></a>Organizzazione generale e gruppi definiti dalla shell
 Usare i comandi, i gruppi di comandi e i menu condivisi esistenti. Se è necessario definire un nuovo comando, provare a posizionarlo in un gruppo di comandi condiviso esistente. Se è necessario definire un nuovo gruppo, provare a posizionarlo in un menu condiviso esistente vicino a un gruppo di comandi correlato prima di creare un nuovo menu di primo livello. Questo consente di ridurre la complessità dei comandi garantendo al contempo un posizionamento dei comandi coerente nell'IDE.

 Il menu di **formato** condiviso, in genere visualizzato nel contesto delle finestre di documento di tipo progettazione, è illustrato nell'immagine seguente:

 ![Menu Formato con callout di Visual Studio](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Gruppi di menu in Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Riduzione e riutilizzo di comandi
 I comandi vengono in genere visualizzati in base al contesto, per ridurre il numero di comandi visualizzati dall'utente in un determinato momento. Tuttavia, è necessario riutilizzare anche i menu condivisi e i gruppi di comandi esistenti per assicurarsi che la struttura dei comandi rimanga relativamente stabile tra le modifiche nel contesto.

 Il riutilizzo di comandi condivisi e l'inserimento di nuovi comandi vicino ai comandi condivisi correlati riduce la complessità dell'IDE e crea un'esperienza più intuitiva.

## <a name="naming-commands"></a>Denominazione dei comandi

### <a name="naming-conventions"></a>Convenzioni di denominazione
 Un nome di comando coerente è fondamentale, in modo che gli utenti possano trovare ed eseguire comandi, usando la riga di comando o l'associazione a un tasto di scelta rapida. I nomi dei comandi consentono inoltre all'utente di comprendere quale scopo viene utilizzato da un comando quando viene visualizzato su una barra degli strumenti o in un menu a cascata o di contesto.

#### <a name="when-naming-commands"></a>Quando si assegnano nomi ai comandi:

- Costruire il testo in modo che sia facilmente localizzabile. Per ulteriori informazioni sulla localizzazione del testo, vedere [procedure consigliate di localizzazione](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Essere concisi. I comandi non devono usare più di tre parole.

- Use maiuscole/minuscole del titolo: la prima lettera di ogni parola deve essere in maiuscolo. Per altre informazioni sulla formattazione del testo in Visual Studio, vedere [stile testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Prendere in considerazione la posizione in cui verrà inserito il comando. Si trova in un menu di primo livello o in un riquadro a comparsa? Ad esempio, quando si raggruppano i comandi di allineamento in un riquadro a comparsa, il comando di primo livello deve essere "align" e i comandi del riquadro a comparsa devono essere "left", "Right", "Center", "giustificate" e così via. Sarebbe ridondante denominare i comandi a comparsa "align left" o "align right".

     ![Menu Formato di Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Uso delle icone con i comandi
 Usare l'associazione di icone con i comandi. Sebbene l'associazione di un'immagine univoca a un comando acceleri la capacità dell'utente di identificare tale comando, il disordine visivo e l'inefficienza si verificano con un utilizzo eccessivo delle immagini. Le regole seguenti consentono di decidere se creare un'icona di comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Usare un'icona con un comando solo se:

- Allo stesso comando è associata un'icona in un altro prodotto Microsoft importante, ad esempio una delle applicazioni Microsoft Office.

- Il comando verrà inserito in una barra degli strumenti predefinita.

- Il comando è un comando specializzato che è probabile che gli utenti aggiungano a una barra degli strumenti usando la finestra di dialogo **"Personalizza..."** .

## <a name="access-and-shortcut-keys"></a>Accesso e tasti di scelta rapida

### <a name="overview"></a>Panoramica
 Esistono due tipi di assegnazione di tasti di tastiera:

- Le **chiavi di accesso** (note anche come acceleratori) consentono l'accesso tramite tastiera tramite i menu per i comandi e per ogni etichetta nell'interfaccia utente della finestra di dialogo. Le chiavi di accesso sono destinate principalmente ai fini dell'accessibilità, vengono assegnate a tutti i menu e alla maggior parte dei controlli della finestra di dialogo, non devono essere memorizzate, influiscono solo sulla finestra corrente e sono localizzate.

- I **tasti di scelta rapida** utilizzano per lo più le sequenze di tasti Control (CTRL) e Function (FN). Sono progettate più per utenti avanzati e per favorire la produttività. Sono assegnati solo ai comandi usati più spesso e consentono l'accesso rapido ignorando il menu principale. I tasti di scelta rapida devono essere memorizzati e per questo motivo è necessario assegnarli coerenti con lo schema del profilo. Gli schemi dei tasti di scelta rapida possono variare da profilo a profilo. Un utente può personalizzare i tasti di scelta rapida tramite **strumenti > opzioni > tastiera**.

### <a name="assigning-access-keys"></a>Assegnazione delle chiavi di accesso
 Le chiavi di accesso sono costituite da Alt più chiavi alfanumeriche. Assegnare una chiave di accesso a ogni voce di menu senza eccezione. Seguire le convenzioni di Windows e comuni per l'assegnazione delle chiavi di accesso. ad esempio, la chiave di accesso per **File > nuova** deve essere sempre **ALT, F, N**.

 Non usare lettere a larghezza singola, ad esempio ' i ' (in lettere maiuscole o minuscole) o minuscole ' l,' ed evitare di usare caratteri con discendenti (g, j, p, q e y) perché sono difficili da distinguere.

 Evitare di utilizzare chiavi duplicate quando possibile. Nei casi in cui la duplicazione è inevitabile, il sistema di menu gestisce i conflitti eseguendo il ciclo di tutti i comandi che usano la chiave. Ad esempio, per un comando ipotetico "Number" nel menu file che duplica la chiave di accesso "N", **ALT, f, n** creerebbe un nuovo file e **ALT, f, n, n** eseguirebbe il comando "Number".

### <a name="assigning-shortcut-keys"></a>Assegnazione di tasti di scelta rapida
 Evitare di assegnare nuovi tasti di scelta rapida perché non sono necessari per ogni comando e imposta il sistema (e la memoria utente) se sovrautilizzato. I dati della Analisi utilizzo software (analisi utilizzo software) indicano che gli utenti di Visual Studio usano solo un piccolo subset dei collegamenti integrati.

 Quando si definiscono i collegamenti, attenersi alle regole seguenti:

- **Usare le sequenze di tasti Control (CTRL) e Function (FN).**

- **Conserva i collegamenti usati di frequente.** Mantenere i collegamenti più diffusi.

- **Semplifica la digitazione dei collegamenti dell'editor.** È possibile associare collegamenti facili da digitare ai comandi necessari agli sviluppatori per la scrittura di codice. Ad esempio, **Edit. InvokeSmartTag** deve avere un tasto di scelta rapida simile a CTRL +/e non ALT + MAIUSC + F10.

- **Cercare i collegamenti con tema coerente.**

- **Seguire le linee guida di Windows per determinare i tasti di modifica da usare.** Usare le combinazioni di tasti CTRL per i comandi con effetti su larga scala, ad esempio i comandi che si applicano a un intero documento. Usare le combinazioni di tasti MAIUSC per i comandi che estendono o completano le azioni del tasto di scelta rapida standard. Non usare combinazioni di tasti CTRL + ALT.

- **Rimuovere i collegamenti estranei.** Se si dispone di una funzionalità legacy, provare a rimuovere i tasti di scelta rapida usati con l'infrequenza estrema (meno di 10 volte dai dati di analisi utilizzo software) o l'infrequenza moderata (meno di 100 volte dai dati di analisi utilizzo software) se una chiave di accesso fornisce accesso rapido allo stesso comando. Ad esempio: Alt, H, C apre la Guida/contenuto.

  Non esiste un modo semplice per controllare la disponibilità del collegamento. Se si desidera aggiungere un collegamento, attenersi alla seguente procedura:

1. Controllare l'elenco di [tasti di scelta rapida Visual Studio 2013](http://visualstudioshortcuts.com/2013/) per determinare se sono presenti comandi simili per il gruppo.

2. Passare a **strumenti > opzioni > ambiente > tastiera** e testare il collegamento. Controllare ogni schema di mappatura della tastiera elencato in "applica il seguente schema di mappatura della tastiera aggiuntivo". Controllare i profili generale, C#, VB e C++, perché condividono collegamenti univoci. Il collegamento è disponibile se non è mappato in nessuna di queste posizioni.
