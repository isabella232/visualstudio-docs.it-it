---
title: Editor di codice XAML
description: Presentazione dell'editor di codice XAML in Visual Studio
ms.date: 06/16/2020
ms.topic: overview
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6421fd0139b04262ac5f1e835f010c1372c034ee
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329177"
---
# <a name="xaml-code-editor"></a>Editor di codice XAML

L'editor di codice XAML nell' [IDE di Visual Studio](../get-started/visual-studio-ide.md) include tutti gli strumenti necessari per creare app WPF e UWP per la piattaforma Windows e per [Novell. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). Questo articolo illustra sia il ruolo che l'editor di codice svolge quando si sviluppano app basate su XAML e le funzionalità univoche per l'editor di codice XAML in Visual Studio 2019.

Per iniziare, esaminiamo l'IDE (Integrated Development Environment) con un progetto WPF aperto. Nell'immagine seguente vengono illustrati molti degli strumenti IDE principali che verranno utilizzati insieme all'editor di codice XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="IDE di Visual Studio 2019 con un progetto WPF aperto in XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

Dalla parte inferiore sinistra dell'immagine in senso orario, gli strumenti IDE principali sono i seguenti:

- La finestra dell' **[editor di codice XAML](#xaml-code-editor-ui)** &mdash; è l'oggetto di questo articolo in &mdash; cui si crea e si modifica il codice.
- La finestra di **[finestra di progettazione XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** , in cui è possibile progettare l'interfaccia utente.
- Finestra della **[casella degli strumenti](../ide/reference/toolbox.md)** ancorabile, in cui è possibile aggiungere controlli all'interfaccia utente.
- Il pulsante **[debug](../debugger/debugger-feature-tour.md)** , in cui è possibile eseguire il codice ed eseguirne il debug. <br>È anche possibile modificare il codice in tempo reale mentre si esegue il debug con il [ricaricamento a caldo di XAML](xaml-hot-reload.md).
- La finestra di **[Esplora soluzioni](../ide/solutions-and-projects-in-visual-studio.md)** , in cui è possibile gestire file, progetti e soluzioni.
- La finestra **[Proprietà](../ide/reference/properties-window.md)** , in cui è possibile modificare la modalità di aspetto dell'interfaccia utente e il funzionamento dei controlli dell'interfaccia utente.

Per continuare, verranno fornite altre informazioni sull'editor di codice XAML.

## <a name="xaml-code-editor-ui"></a>Interfaccia utente dell'editor di codice XAML

Mentre la finestra dell'editor di codice per le app XAML condivide alcuni elementi dell'interfaccia utente (interfaccia utente) che vengono visualizzati anche nell'IDE standard, include anche alcune funzionalità esclusive che semplificano lo sviluppo di app XAML.

Ecco la finestra dell'editor di codice XAML.

![Finestra dell'editor di codice XAML in Visual Studio](media/xaml-code-editor-window.png "Screenshot della finestra dell'editor di codice XAML in Visual Studio 2019")

Verranno ora esaminate le funzioni di ogni elemento dell'interfaccia utente nell'editor di codice.

### <a name="first-row"></a>Prima riga

Nella prima riga nella parte superiore della finestra del codice XAML, a sinistra, sono disponibili una scheda **progettazione** , un pulsante **Scambia riquadri** , una scheda **XAML** e un pulsante Apri codice **XAML** .

![Prima delle due prime righe della finestra dell'editor di codice XAML in Visual Studio, con il lato sinistro della prima riga evidenziata](media/xaml-code-editor-top-row-left.png "Screenshot della prima delle due prime righe della finestra dell'editor di codice XAML in Visual Studio 2019, in cui gli elementi dell'interfaccia utente a sinistra sono evidenziati")

Ecco come funzionano:

- La scheda **progettazione** modifica lo stato attivo dall'editor del codice XAML al finestra di progettazione XAML.
- Il pulsante **Scambia riquadri** inverte il percorso del finestra di progettazione XAML e l'editor di codice XAML nell'IDE.
- La scheda **XAML** modifica lo stato attivo nuovamente nell'editor di codice XAML.
- Il pulsante **Apri in XAML** crea una finestra dell'editor di codice XAML separata all'esterno dell'IDE.

Continuando a destra è presente un pulsante di **suddivisione verticale** , un pulsante di **suddivisione orizzontale** e un pulsante **Comprimi riquadri** .

![Prima delle due prime righe della finestra dell'editor di codice XAML in Visual Studio, con il lato destro della prima riga evidenziata](media/xaml-code-editor-top-row-right.png "Screenshot della prima delle due prime righe della finestra dell'editor di codice XAML in Visual Studio 2019, in cui gli elementi dell'interfaccia utente a destra sono evidenziati")

Ecco come funzionano:

- Il pulsante di **suddivisione verticale** cambia il percorso del finestra di progettazione XAML e l'editor di codice XAML nell'IDE da un allineamento orizzontale a un allineamento verticale.
- Il pulsante di **suddivisione orizzontale** modifica il percorso del finestra di progettazione XAML e l'editor di codice XAML nell'IDE da un allineamento verticale a un allineamento orizzontale.
- Il pulsante **Comprimi riquadro** consente di comprimere gli elementi nel riquadro inferiore, sia che si tratti dell'editor del codice o della finestra di progettazione. Per ripristinare il riquadro inferiore, scegliere di nuovo lo stesso pulsante, che ora è denominato pulsante **Espandi riquadro** .

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Seconda riga

Nella seconda riga nella parte superiore della finestra del codice XAML sono presenti due elenchi a discesa della finestra. Tuttavia, se si visualizza la descrizione comando per questi elementi dell'interfaccia utente, tali elementi vengono identificati ulteriormente come "elemento: finestra" e "membro: finestra".

![Seconda delle due prime righe della finestra dell'editor di codice XAML in Visual Studio, in cui sono visibili entrambi gli elenchi a discesa della finestra](media/xaml-code-editor-top-row-windows.png "Screenshot della seconda delle due prime righe della finestra dell'editor di codice XAML in Visual Studio 2019, in cui sono visibili entrambi gli elenchi a discesa della finestra")

Gli elenchi a discesa della finestra hanno funzioni diverse, come indicato di seguito:

- L' **elemento: Window** a sinistra consente di visualizzare e passare a elementi padre o di pari livello.

  In particolare, viene visualizzata una visualizzazione simile a un contorno che rivela la struttura dei tag del codice. Quando si seleziona dall'elenco, lo stato attivo nell'editor di codice si blocca sulla riga di codice che include l'elemento selezionato.

    ![Elenco a discesa elemento: finestra in Visual Studio](media/xaml-element-window-dropdown.png "Screenshot dell'elemento: elenco a discesa finestra in Visual Studio 2019")

- La **finestra membro:** a destra consente di visualizzare e passare a elementi figlio o attributo.

    In particolare, viene visualizzato un elenco delle proprietà nel codice. Quando si seleziona dall'elenco, lo stato attivo nell'editor di codice si blocca alla riga di codice che include la proprietà selezionata.

    ![Elenco a discesa membro: finestra in Visual Studio](media/xaml-member-window-dropdown.png "Screenshot dell'elenco a discesa membro: finestra in Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Riquadro centrale, editor di codice

Il riquadro centrale è la parte "code" dell'editor di codice XAML. Include la maggior parte delle funzionalità disponibili nell' [editor di codice IDE](../get-started/tutorial-editor.md). Si toccheranno diverse funzionalità dell'IDE universale che consentono di sviluppare il codice XAML. Verranno anche evidenziate anche le funzionalità univoche per XAML nell'IDE.

![Editor del codice XAML, solo il riquadro centrale, in Visual Studio](media/xaml-code-editor-middle.png "Screenshot dell'editor del codice XAML, solo del riquadro centrale, in Visual Studio 2019")

#### <a name="quick-actions"></a>Azioni rapide

È possibile usare le [azioni rapide](../ide/quick-actions.md) per effettuare il refactoring, generare o modificare in altro modo il codice con un'unica azione.

Ad esempio, un'attività utile che è possibile eseguire con azioni rapide consiste nel **rimuovere le using non necessarie** dal codice C# nella scheda **MainWindow.XAML.cs** .

Ecco come:

1. Passare il puntatore del mouse su un'istruzione using, scegliere l'icona a forma di lampadina, quindi scegliere **Rimuovi using non necessari** dall'elenco a discesa.

    ![Opzione "Rimuovi using superflue" dell'editor IDE dal menu azioni rapide](media/xaml-code-editor-remove-usings.png "Screenshot dell'opzione Rimuovi using superflue dell'editor IDE dal menu azioni rapide")

1. Scegliere se si desidera correggere tutte le occorrenze nel **documento**, nel **progetto**o nella **soluzione**.
1. Visualizzare la finestra di dialogo **Anteprima** , quindi scegliere **applica**.

È anche possibile accedere a questa funzionalità dalla barra dei menu. A tale scopo, scegliere **modifica**  >  **IntelliSense**  >  **Rimuovi e Ordina using**.

Per ulteriori informazioni sull'utilizzo delle impostazioni, vedere la pagina [Ordina using](../ide/reference/sort-usings.md) . Per ulteriori informazioni su IntelliSense, vedere la pagina relativa [a IntelliSense in Visual Studio](../ide/using-intellisense.md) . Per ulteriori informazioni su alcune delle modalità tipiche di utilizzo delle azioni rapide da parte degli sviluppatori, vedere la pagina delle [azioni rapide comuni](../ide/common-quick-actions.md) .

#### <a name="change-tracking"></a>Change tracking

Il colore del margine sinistro consente di tenere traccia delle modifiche apportate al file. Ecco il modo in cui i colori sono correlati alle azioni intraprese:

- Le modifiche apportate dopo l'apertura del file ma non salvate sono identificate da una barra **gialla** sul margine sinistro (noto come margine di selezione).

    ![Editor di codice modificare con la barra gialla](media/code-editor-edit-yellow.png "Screenshot dell'editor del codice con una modifica contrassegnata con una barra gialla nel margine di selezione.")

- Dopo aver salvato le modifiche, ma prima di chiudere il file, la barra diventa **verde**.

    ![Editor di codice modificare con la barra verde](media/code-editor-edit-green.png "Screenshot dell'editor del codice con una modifica contrassegnata con una barra verde nel margine di selezione.")

Per attivare e disattivare questa funzionalità, modificare l'opzione **rileva modifiche** nelle impostazioni dell' **editor di testo** (**strumenti**  >  **Opzioni**  >  **editor di testo**).

Per ulteriori informazioni sul rilevamento &mdash; delle modifiche per includere le linee ondulate (note anche come "controllo ortografia durante") visualizzate in stringhe di codice, &mdash; vedere la sezione **[funzionalità dell'editor](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** delle [funzionalità della pagina editor di codice di Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md) .

#### <a name="right-click-context-menu"></a>Pulsante destro del mouse sul menu di scelta rapida

Quando si modifica il codice nell'editor di codice XAML, sono disponibili diverse funzionalità a cui è possibile accedere tramite il menu di scelta rapida. La maggior parte di queste funzionalità sono disponibili universalmente nell'IDE di Visual Studio, mentre altre sono specifiche dell'uso di un editor di codice insieme a una finestra di progettazione.

![Menu di scelta rapida dell'editor di codice XAML in Visual Studio](media/xaml-code-editor-right-click-menu.png "Screenshot del menu di scelta rapida dell'editor di codice XAML in Visual Studio 2019")

Di seguito sono riportate le caratteristiche di ogni funzionalità e il modo in cui è utile:

- **Visualizza codice** : apre la finestra del codice del linguaggio di programmazione, che in genere è a schede accanto alla visualizzazione predefinita che include la finestra di progettazione e l'editor di codice XAML.
- **Progettazione viste** : apre la visualizzazione predefinita che include la finestra di progettazione e l'editor di codice XAML. (Se si è già nella visualizzazione predefinita, non esegue alcuna operazione).
- **Azioni rapide e refactoring** : refactoring, generazione o modifica di codice con una singola azione. Quando si passa il mouse sul codice, viene visualizzata un'icona a lampadina quando è disponibile un'azione rapida o un refactoring. <br>Vedere anche: [azioni rapide](../ide/quick-actions.md) ed effettuare il [refactoring del codice](../ide/refactoring-in-visual-studio.md).
- **Rinomina...** -Rinomina solo gli spazi dei nomi. Se non si dispone di uno spazio dei nomi da rinominare, verrà visualizzato un messaggio di errore che indica che è possibile rinominare solo i prefissi degli spazi dei nomi.
- **Rimuovi e Ordina spazi dei** nomi: rimuove gli spazi dei nomi inutilizzati e quindi Ordina gli spazi dei nomi rimanenti.
- **Visualizza definizione** -Visualizza in anteprima la definizione di un tipo senza uscire dalla posizione corrente nell'editor. <br>Vedere anche: visualizzare la [definizione](../ide/go-to-and-peek-definition.md#peek-definition) e [visualizzare e modificare il codice usando Visualizza definizione](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Vai a definizione** : consente di passare all'origine di un tipo o di un membro e di aprire il risultato in una nuova scheda. <br>Vedere anche: [Vai a definizione](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Racchiudi tra...** -Usare frammenti di codice racchiusi, che vengono aggiunti intorno a un blocco di codice selezionato. <br>Vedere anche: [frammenti di espansione e frammenti Racchiudi](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Inserisci frammento** -inserisce un frammento di codice nella posizione del cursore.
- **Cut** -spiegazione automatica
- **Copia** -spiegazione automatica
- **Incolla** -spiegazione automatica
- **Struttura** : espandere e comprimere sezioni di codice. <br>Vedere anche: [struttura](../ide/outlining.md).
- **Controllo** del codice sorgente: consente di visualizzare la cronologia dei contributi del codice a un repository open source.

### <a name="middle-pane-scroll-bar"></a>Riquadro centrale, barra di scorrimento

La barra di scorrimento può eseguire più di scorrere il codice. È anche possibile usarlo per aprire un altro riquadro dell'editor di codice. È possibile utilizzare la barra di scorrimento per semplificare il codice aggiungendo annotazioni o utilizzando diverse modalità di visualizzazione.

#### <a name="split-the-code-window"></a>Suddividere la finestra del codice

Nella barra di scorrimento dell'editor di codice è presente un pulsante di **divisione** in alto a destra. Quando lo si sceglie, è possibile aprire un altro riquadro dell'editor di codice. Questa operazione è utile perché funzionano indipendentemente l'una dall'altra, quindi è possibile usarle per lavorare sul codice in posizioni diverse.

![Editor del codice XAML, solo il riquadro centrale, in Visual Studio](media/code-editor-split-window-button.png "Screenshot dell'editor del codice XAML, solo del riquadro centrale, in Visual Studio 2019")

Per ulteriori informazioni su come suddividere una finestra dell'editor, vedere la pagina [gestione delle finestre dell'editor](../ide/how-to-manage-editor-windows.md) .

#### <a name="use-annotations-or-map-mode"></a>Usare le annotazioni o la modalità mappa

È anche possibile modificare l'aspetto della barra di scorrimento e le funzionalità aggiuntive in esso contenute. Ad esempio, molti utenti desiderano includere *annotazioni* nella barra di scorrimento, che forniscono segnali visivi come le modifiche al codice, i punti di interruzione, i segnalibri, gli errori e la posizione del punto di inserimento.

Altri apprezzano l'uso della *modalità mappa*, che consente di visualizzare le righe di codice in miniatura sulla barra di scorrimento. Gli sviluppatori che dispongono di una grande quantità di codice in un file potrebbero scoprire che la modalità mappa tiene traccia delle righe di codice in modo più efficace rispetto alla barra di scorrimento predefinita.

Per ulteriori informazioni su come modificare le impostazioni predefinite della barra di scorrimento, vedere la pagina [personalizzare la barra di scorrimento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) .

## <a name="xaml-specific-features"></a>Funzionalità specifiche di XAML

La maggior parte delle funzionalità seguenti sono disponibili a livello universale nell'IDE di Visual Studio, ma sono state aggiunte dimensioni ad alcune di esse che semplificano la scrittura di codice per gli sviluppatori XAML.

### <a name="xaml-code-snippets"></a>Frammenti di codice XAML

I frammenti di codice sono piccoli blocchi di codice riutilizzabile che è possibile inserire in un file di codice usando il comando del menu di scelta rapida per **inserire il frammento** di codice o una combinazione di tasti di scelta rapida (**CTRL** + **K**, **CTRL** + **X**). [IntelliSense](../ide/using-intellisense.md) è stato migliorato in modo da supportare la visualizzazione dei frammenti XAML, che funzionano sia per i frammenti predefiniti sia per eventuali frammenti personalizzati aggiunti manualmente. Alcuni frammenti di codice XAML predefiniti includono,,, `#region` `Column definition` `Row definition` `Setter` e `Tag` .

![Editor del codice XAML con le opzioni dei frammenti di codice XAML visualizzate in IntelliSense](media/xaml-code-snippets.png "Screenshot dell'editor del codice XAML con le opzioni dei frammenti di codice XAML visualizzate in IntelliSense")

Per ulteriori informazioni, vedere i [frammenti di codice](../ide/code-snippets.md) e le pagine dei [frammenti di codice C#](../ide/visual-csharp-code-snippets.md) .

### <a name="xaml-region-support"></a>Supporto #region XAML

A partire da Visual Studio 2015, abbiamo reso disponibile #region supporto per gli sviluppatori XAML in WPF e UWP e, più recentemente, in [Novell. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). In Visual Studio 2019, continuiamo a apportare miglioramenti incrementali al supporto #region. Nella [versione 16,4](/visualstudio/releases/2019/release-notes-v16.4/) e successive, ad esempio, #region opzioni vengono visualizzate quando si inizia a digitare `<!` .

![Editor di codice XAML con opzioni di #region visualizzate in IntelliSense](media/code-editor-xaml-region.png "Screenshot dell'editor del codice XAML con opzioni di #region visualizzate in IntelliSense")

È possibile utilizzare le aree quando si desidera raggruppare le sezioni del codice che si desidera espandere o comprimere.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Per ulteriori informazioni sulle aree, vedere la pagina [#region (riferimenti per C#)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) . Per ulteriori informazioni sull'espansione e la compressione di sezioni di codice, vedere la pagina relativa alla [struttura](../ide/outlining.md) .

### <a name="xaml-comments"></a>Commenti XAML

Gli sviluppatori preferiscono spesso documentare il proprio codice usando commenti. È possibile aggiungere commenti al codice XAML presente nella scheda **MainWindow. XAML** nei modi seguenti:

- Immettere `<!--` prima di un commento e quindi aggiungere `-->` dopo il commento.
- Immettere `<!` e quindi scegliere `!--` dall'elenco di opzioni.

  ![Editor del codice XAML fare clic con il pulsante destro del mouse su Aggiungi commenti](media/xaml-code-editor-comments.png "Screenshot del menu di scelta rapida per aggiungere commenti nell'editor di codice XAML")

- Selezionare il codice che si desidera racchiudere con un commento, quindi scegliere il pulsante **Commento** sulla barra degli strumenti dell'IDE. Per invertire l'azione, scegliere il pulsante **Rimuovi commento** .

  ![Pulsante di commento e pulsante Rimuovi commento sulla barra degli strumenti dell'IDE](media/comment-undo-comment-buttons.png "Screenshot del pulsante commento e del pulsante Rimuovi commento sulla barra degli strumenti dell'IDE")

- Selezionare il codice che si desidera racchiudere con un commento, quindi premere **CTRL** + **K**, **CTRL** + **C**. Per rimuovere il commento dal codice selezionato, premere **CTRL** + **K**, **CTRL** + **U**.

Per altre informazioni su come usare i commenti nel codice C# disponibile nella scheda **MainWindow.XAML.cs** , vedere la pagina relativa ai [commenti sulla documentazione](/dotnet/csharp/language-reference/language-specification/documentation-comments/) .

### <a name="xaml-lightbulbs"></a>Lampadine XAML

Le icone a forma di lampadina visualizzate nel codice XAML fanno parte delle [azioni rapide](../ide/quick-actions.md) che è possibile usare per effettuare il refactoring, generare o modificare il codice in altro modo.

Di seguito sono riportati alcuni esempi di come possono trarre vantaggio dall'esperienza di codifica XAML:

- **Rimuovere gli spazi dei nomi non necessari**. Nell'editor di codice XAML gli spazi dei nomi non necessari vengono visualizzati nel testo in grigio. Se si passa il cursore su un oggetto non necessario usando, viene visualizzata una lampadina. Quando si sceglie l'opzione **Rimuovi spazi dei nomi non necessari** dall'elenco a discesa, verrà visualizzata un'anteprima di che è possibile rimuovere.

  ![Opzione Rimuovi spazi dei nomi superflui nell'editor del codice XAML dalla lampadina azioni rapide](media/xaml-code-editor-dimmed-namespaces-preview.png "Screenshot dell'opzione Rimuovi spazi dei nomi non necessari dell'editor del codice XAML visualizzata tramite la lampadina azioni rapide")

- **Rinominare lo spazio dei nomi**. Questa funzionalità, disponibile dal menu di scelta rapida dopo aver evidenziato uno spazio dei nomi, semplifica la modifica di più istanze di un'impostazione alla volta. Per accedere a questa funzionalità, è anche possibile usare la barra dei menu, **modificare**  >  **Rinomina refactoring**  >  **Rename**oppure premere **CTRL** + **r**, quindi premere di nuovo **CTRL** + **r** .

  ![Opzione Rinomina spazio dei nomi dell'editor del codice XAML dal menu di scelta rapida](media/code-editor-rename-namespace.png "Screenshot dell'opzione Rinomina spazio dei nomi dell'editor del codice XAML visualizzato tramite il menu di scelta rapida")

  Per altre informazioni, vedere la pagina [rinominare un simbolo di codice](../ide/reference/rename.md) .

### <a name="conditional-xaml-for-uwp"></a>XAML condizionale per UWP

XAML condizionale consente di usare il metodo [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) nel markup XAML. Puoi così impostare le proprietà e creare istanze di oggetti nel markup in base alla presenza di un'API senza dover usare code-behind.

Per ulteriori informazioni, vedere la pagina [XAML condizionale](/windows/uwp/debug-test-perf/conditional-xaml/) e i [controlli XAML UWP host in app desktop (Isole XAML)](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>Visualizzatore struttura XAML

La funzionalità Visualizzatore struttura nell'editor di codice mostra le linee guida per le strutture, ovvero linee verticali tratteggiate che indicano gli elementi tag aperti e chiusi corrispondenti nel codice. Queste linee verticali rendono più semplice la visualizzazione dei blocchi logici Begin e end.

Per ulteriori informazioni, vedere la pagina relativa all' [esplorazione della tabella codici](../ide/navigating-code.md) .

### <a name="intellicode-for-xaml"></a>IntelliCode per XAML

Quando si aggiunge un tag XAML al codice, si inizia in genere con una parentesi uncinata aperta `<` . Quando si digita la parentesi angolare, viene visualizzato un menu IntelliCode che elenca diversi dei tag XAML più diffusi. Scegliere quello che si desidera aggiungere rapidamente al codice.

È possibile riconoscere le selezioni IntelliCode perché vengono visualizzate nella parte superiore dell'elenco e sono contrassegnate come.

![Elenco IntelliCode per l'editor di testo XAML](media/xaml-intellicode-selection.png "Screenshot dell'elenco IntelliCode per l'editor di testo XAML")

Per ulteriori informazioni, vedere la pagina relativa alla [Panoramica della pagina IntelliCode](/visualstudio/intellicode/overview/) .

### <a name="settings"></a>Impostazioni

Per altre informazioni su *tutte* le impostazioni nell'IDE di Visual Studio, vedere le [funzionalità della pagina dell'editor di codice](../ide/writing-code-in-the-code-and-text-editor.md) .

## <a name="xaml-optional-settings"></a>Impostazioni facoltative XAML

È possibile utilizzare la finestra di dialogo [Opzioni](../ide/reference/options-dialog-box-visual-studio.md) per modificare le impostazioni predefinite per l'editor di codice XAML. Per visualizzare le impostazioni, scegliere **strumenti**  >  **Opzioni**  >  **editor di testo**  >  **XAML**.

![Elenco di opzioni per l'editor di testo XAML](media/xaml-tools-options.png "Screenshot dell'elenco di opzioni per l'editor di testo XAML")

> [!NOTE]
> È anche possibile usare i tasti di scelta rapida per accedere alla finestra di dialogo Opzioni. Ecco come: premere **CTRL** + **Q** per cercare nell'IDE, digitare **options**, quindi premere **invio**. Premere quindi **CTRL** + **e** per cercare la finestra di dialogo Opzioni, digitare **editor di testo**, premere **invio**, digitare **XAML**, quindi premere **invio**.
>  
> Per ulteriori informazioni sui tasti di scelta rapida, vedere la pagina Suggerimenti rapidi [per Visual Studio](../ide/productivity-shortcuts.md#code-editor) .

### <a name="universal-text-editor-options"></a>Opzioni dell'editor di testo universale

Nella finestra di dialogo [Opzioni](../ide/reference/options-text-editor-xaml-formatting.md) per XAML i primi tre elementi seguenti sono universali per tutti i linguaggi di programmazione supportati dall'IDE di Visual Studio. Per ulteriori informazioni su queste opzioni e su come usarle, vedere le informazioni collegate nella tabella seguente.

|Nome  |Altre informazioni  |
|---------|---------|
|Generale  | [Finestra di dialogo Opzioni: editor di testo > tutti i linguaggi](../ide/reference/options-text-editor-all-languages.md) |
|Barre di scorrimento | [Opzioni, Editor di testo, Tutti i linguaggi, Barre di scorrimento](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Schede  |  [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Opzioni dell'editor di testo specifiche di XAML

Nella tabella seguente sono elencate le impostazioni della finestra di dialogo [Opzioni](../ide/reference/options-text-editor-xaml-formatting.md) che consentono di migliorare l'esperienza di modifica quando si sviluppano app basate su XAML. Per ulteriori informazioni su queste opzioni e su come usarle, vedere le informazioni collegate.

|Nome  |Altre informazioni  |
|---------|---------|
|Formattazione | [Opzioni, Editor di testo, XAML, Formattazione](../ide/reference/options-text-editor-xaml-formatting.md) |
|Varie |  [Opzioni, Editor di testo, XAML, Varie](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> L'impostazione del **nome del metodo del gestore eventi in maiuscolo** nella sezione **varie** è particolarmente utile per gli sviluppatori XAML. Questa impostazione è *disattivata* per impostazione predefinita perché è nuova, ma è consigliabile impostarla *su on* per supportare la corretta combinazione di maiuscole e minuscole nel codice.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come modificare il codice in tempo reale mentre si esegue l'app in modalità di debug, vedere la pagina relativa al [ricaricamento a caldo di XAML](xaml-hot-reload.md) .

## <a name="see-also"></a>Vedi anche

- [Funzionalità dell'editor di codice di Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
- [Sviluppo di app per dispositivi mobili Novell (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 per Mac-IDE Tour (Mac)](/visualstudio/mac/ide-tour/)
