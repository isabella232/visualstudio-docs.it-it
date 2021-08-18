---
title: Editor di codice XAML
description: Presentazione dell'editor di codice XAML in Visual Studio
ms.date: 06/16/2020
ms.topic: overview
f1_keywords:
- VS.XamlEditor
monikerRange: vs-2019
ms.custom: contperf-fy21q4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: b99a75dd6c03183b49154a6c3ea4d68edc7130b2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130351"
---
# <a name="xaml-code-editor"></a>Editor di codice XAML

L'editor di codice XAML [nell'IDE Visual Studio](../get-started/visual-studio-ide.md) include tutti gli strumenti necessari per creare app WPF e UWP per la piattaforma Windows e per [Xamarin.Forms.](/xamarin/xamarin-forms/user-interface/text/editor/) Questo articolo illustra sia il ruolo che l'editor di codice svolge quando si sviluppano app basate su XAML, sia le funzionalità univoche dell'editor di codice XAML in Visual Studio 2019.

Per iniziare, diamo un'occhiata all'IDE (ambiente di sviluppo integrato) con un progetto WPF aperto. L'immagine seguente mostra diversi strumenti IDE chiave che verranno utilizzati insieme all'editor di codice XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="Ide Visual Studio 2019 con un progetto WPF aperto in XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

In basso a sinistra dell'immagine in senso orario, i principali strumenti IDE sono i seguenti:

- Finestra **[dell'editor di codice XAML](#xaml-code-editor-ui)** &mdash; nell'oggetto di questo articolo &mdash; in cui si crea e si modifica il codice.
- Finestra **[finestra di progettazione XAML,](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** in cui si progetta l'interfaccia utente.
- Finestra **[ancorabile](../ide/reference/toolbox.md)** della casella degli strumenti, in cui aggiungere controlli all'interfaccia utente.
- Pulsante **[Debug,](../debugger/debugger-feature-tour.md)** in cui è possibile eseguire il codice ed eseguirne il debug. <br>È anche possibile modificare il codice in tempo reale durante il debug [con Ricaricamento rapido XAML](xaml-hot-reload.md).
- Finestra **[Esplora soluzioni,](../ide/solutions-and-projects-in-visual-studio.md)** in cui è possibile gestire file, progetti e soluzioni.
- Finestra **[Proprietà,](../ide/reference/properties-window.md)** in cui è possibile modificare l'aspetto dell'interfaccia utente e il funzionamento dei controlli dell'interfaccia utente.

Per continuare, si apprenderà di più sull'editor di codice XAML.

## <a name="xaml-code-editor-ui"></a>Interfaccia utente dell'editor di codice XAML

Anche se la finestra dell'editor di codice per le app XAML condivide alcuni elementi dell'interfaccia utente visualizzati anche nell'IDE standard, include anche alcune funzionalità univoche che semplificano lo sviluppo di app XAML.

Di seguito viene visualizzata la finestra dell'editor di codice XAML stessa.

![Finestra dell'editor di codice XAML in Visual Studio](media/xaml-code-editor-window.png "Screenshot della finestra dell'editor di codice XAML in Visual Studio 2019")

Si esaminino ora le funzioni di ogni elemento dell'interfaccia utente nell'editor di codice.

### <a name="first-row"></a>Prima riga

Nella prima riga nella parte superiore della finestra del codice XAML, a  sinistra, sono presenti una scheda **Progettazione,** un pulsante Scambia riquadri, una **scheda XAML** e un pulsante **POPUP XAML.**

![La prima delle due prime righe della finestra dell'editor di codice XAML Visual Studio, con il lato sinistro della prima riga evidenziato](media/xaml-code-editor-top-row-left.png "Screenshot della prima delle due prime righe della finestra dell'editor di codice XAML in Visual Studio 2019, in cui sono evidenziati gli elementi dell'interfaccia utente a sinistra")

Ecco come funzionano:

- La **scheda Progettazione** modifica lo stato attivo dall'editor di codice XAML al finestra di progettazione XAML.
- Il **pulsante Scambia riquadri** inverte la posizione del finestra di progettazione XAML e dell'editor di codice XAML nell'IDE.
- La **scheda XAML** modifica lo stato attivo nell'editor di codice XAML.
- Il **pulsante POP OUT XAML** crea una finestra dell'editor di codice XAML separata all'esterno dell'IDE.

Continuando a destra, sono presenti un pulsante **Divisione** verticale, **un** pulsante Divisione orizzontale e un pulsante **Comprimi** riquadri.

![La prima delle due prime righe della finestra dell'editor di codice XAML Visual Studio, con il lato destro della prima riga evidenziato](media/xaml-code-editor-top-row-right.png "Screenshot della prima delle due prime righe della finestra dell'editor di codice XAML in Visual Studio 2019, in cui sono evidenziati gli elementi dell'interfaccia utente a destra")

Ecco come funzionano:

- Il **pulsante Dividi** verticale modifica la posizione dell'finestra di progettazione XAML e dell'editor di codice XAML nell'IDE da un allineamento orizzontale a un allineamento verticale.
- Il **pulsante Divisione orizzontale** modifica la posizione dell'finestra di progettazione XAML e dell'editor di codice XAML nell'IDE da un allineamento verticale a un allineamento orizzontale.
- Il **pulsante Comprimi** riquadro consente di comprimere gli elementi presenti nel riquadro inferiore, che si tratta dell'editor di codice o della finestra di progettazione. Per ripristinare il riquadro inferiore, scegliere di nuovo lo stesso pulsante, denominato **pulsante Espandi** riquadro.

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Seconda riga

Nella seconda riga nella parte superiore della finestra del codice XAML sono disponibili due elenchi a discesa Finestra. Tuttavia, se si visualizza la descrizione comando per questi elementi dell'interfaccia utente, li identifica ulteriormente come "Elemento: Finestra" e "Membro: Finestra".

![Seconda delle due prime righe della finestra dell'editor di codice XAML in Visual Studio, in cui sono visibili entrambi gli elenchi a discesa Finestra](media/xaml-code-editor-top-row-windows.png "Screenshot della seconda delle due prime righe della finestra dell'editor di codice XAML in Visual Studio 2019, in cui sono visibili entrambi gli elenchi a discesa Finestra")

Gli elenchi a discesa Finestra hanno funzioni diverse, come indicato di seguito:

- Elemento: **finestra a** sinistra consente di visualizzare e passare agli elementi padre o di pari livello.

  In particolare, mostra una visualizzazione di tipo struttura che rivela la struttura dei tag del codice. Quando si seleziona dall'elenco, lo stato attivo nell'editor di codice verrà allineato alla riga di codice che include l'elemento selezionato.

    ![Elenco a discesa Elemento: Finestra in Visual Studio](media/xaml-element-window-dropdown.png "Screenshot dell'elenco a discesa Elemento: Finestra in Visual Studio 2019")

- La **finestra Membro: a** destra consente di visualizzare e passare agli attributi o agli elementi figlio.

    In particolare, viene visualizzato un elenco delle proprietà nel codice. Quando si seleziona dall'elenco, lo stato attivo nell'editor di codice verrà allineato alla riga di codice che include la proprietà selezionata.

    ![Elenco a discesa Membro: Finestra in Visual Studio](media/xaml-member-window-dropdown.png "Screenshot dell'elenco a discesa Membro: Finestra in Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Riquadro centrale, editor di codice

Il riquadro centrale è la parte "codice" dell'editor di codice XAML. Include la maggior parte delle funzionalità disponibili [nell'editor di codice IDE](../get-started/tutorial-editor.md). Verranno trattate alcune delle funzionalità dell'IDE universale che consentono di sviluppare il codice XAML. Verranno anche evidenziate le funzionalità da univoco a XAML nell'IDE.

![Editor di codice XAML, solo riquadro centrale, in Visual Studio](media/xaml-code-editor-middle.png "Screenshot dell'editor di codice XAML, solo riquadro centrale, in Visual Studio 2019")

#### <a name="quick-actions"></a>Azioni rapide

È possibile usare [Azioni rapide per](../ide/quick-actions.md) eseguire il refactoring, generare o modificare in altro modo il codice con una singola azione.

Ad esempio, un'attività utile che è possibile  eseguire usando Azioni rapide è rimuovere gli utilizzi non necessari dal codice C# nella **scheda MainWindow.xaml.cs.**

Ecco come:

1. Passare il puntatore del mouse su un'istruzione using, scegliere l'icona a forma di lampadina e quindi **scegliere Rimuovi** utilizzi non necessari dall'elenco a discesa.

    ![Opzione "Rimuovi utilizzi non necessari" dell'editor IDE dal menu Azioni rapide](media/xaml-code-editor-remove-usings.png "Screenshot dell'opzione Rimuovi using non necessari dell'editor IDE dal menu Azioni rapide")

1. Scegliere se correggere tutte le occorrenze in **Document**, **Project** o **Solution**.
1. Visualizzare la **finestra di** dialogo Anteprima e quindi scegliere **Applica**.

È anche possibile accedere a questa funzionalità dalla barra dei menu. A tale scopo, scegliere **Modifica**  >  **IntelliSense**  >  **Rimuovi e ordina con**.

Per altre informazioni sull'uso delle impostazioni di , vedere la [pagina Ordina con](../ide/reference/sort-usings.md) . Per altre informazioni su IntelliSense, vedere la pagina [IntelliSense in Visual Studio.](../ide/using-intellisense.md) Per altre informazioni su alcuni dei modi tipici in cui gli sviluppatori usano Azioni rapide, vedere la [pagina Azioni rapide](../ide/common-quick-actions.md) comuni.

#### <a name="change-tracking"></a>Rilevamento modifiche

Il colore del margine sinistro consente di tenere traccia delle modifiche apportate al file. Ecco come i colori sono correlati alle azioni eseguite:

- Le modifiche apportate dopo l'apertura del file ma  non salvate vengono denotata da una barra gialla sul margine sinistro (nota come margine di selezione).

    ![Modifica dell'editor di codice con barra gialla](media/code-editor-edit-yellow.png "Screenshot dell'editor di codice con una modifica contrassegnata con una barra gialla nel margine di selezione.")

- Dopo aver salvato le modifiche (ma prima di chiudere il file), la barra diventa **verde.**

    ![Modifica dell'editor di codice con barra verde](media/code-editor-edit-green.png "Screenshot dell'editor di codice con una modifica contrassegnata con una barra verde nel margine di selezione.")

Per disattivare e attivare questa  funzionalità, modificare l'opzione Rileva modifiche nelle impostazioni **dell'editor** di testo (**Editor di** testo  >  **opzioni**  >  **strumenti**).

Per altre informazioni sul rilevamento delle modifiche per includere le righe ondulate (note anche come "sottolineature ondulate") visualizzate sotto le stringhe di codice, vedere la sezione Funzionalità dell'editor della pagina Funzionalità dell'editor di codice &mdash; &mdash; [Visual Studio.](../ide/writing-code-in-the-code-and-text-editor.md) **[](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)**

#### <a name="right-click-context-menu"></a>Fare clic con il pulsante destro del mouse sul menu di scelta rapida

Quando si modifica il codice nell'editor di codice XAML, è possibile accedere a diverse funzionalità usando il menu di scelta rapida con il pulsante destro del mouse. La maggior parte di queste funzionalità è disponibile universalmente nell'IDE Visual Studio, mentre alcune sono specifiche per l'uso di un editor di codice insieme a una finestra di progettazione.

![Screenshot del menu di scelta rapida dell'editor di codice XAML in Visual Studio 2019.](media/xaml-code-editor-right-click-menu.png)

Ecco cosa fa ogni funzionalità e come è utile:

- **Visualizza codice:** apre la finestra del codice del linguaggio di programmazione, in genere a schede accanto alla visualizzazione predefinita che include la finestra Progettazione e l'editor di codice XAML.
- **Progettazione visualizzazioni:** apre la visualizzazione predefinita che include la finestra Progettazione e l'editor di codice XAML. Se si è già nella visualizzazione predefinita, non esegue alcuna operazione.
- **Azioni rapide e refactoring: refactoring,** genera o modifica in altro modo il codice con una singola azione. Quando si passa il mouse sul codice, viene visualizzata un'icona a forma di lampadina quando è disponibile un'azione rapida o un refactoring. <br>Vedere anche: [Azioni rapide e](../ide/quick-actions.md) [refactoring del codice](../ide/refactoring-in-visual-studio.md).
- **Rinomina...** - Rinomina solo gli spazi dei nomi. Se non si ha uno spazio dei nomi da rinominare, verrà visualizzato un messaggio di errore che indica che è possibile rinominare solo i prefissi degli spazi dei nomi.
- **Rimuovi e ordina spazi dei nomi:** rimuove gli spazi dei nomi inutilizzati e quindi ordina gli spazi dei nomi che rimangono.
- **Visualizza definizione:** visualizza in anteprima la definizione di un tipo senza uscire dalla posizione corrente nell'editor. <br>Vedere anche: [Visualizzare la definizione](../ide/go-to-and-peek-definition.md#peek-definition) e visualizzare e modificare il codice usando Visualizza [definizione](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Vai a definizione:** passa all'origine di un tipo o di un membro e apre il risultato in una nuova scheda. <br>Vedere anche: [Vai a definizione](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Racchiudere con...** - Usare frammenti di codice racchiusi, che vengono aggiunti intorno a un blocco di codice selezionato. <br>Vedere anche: [Frammenti di espansione e frammenti di codice racchiusi.](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets)
- **Inserisci frammento:** inserisce un frammento di codice nella posizione del cursore.
- **Taglia** - Auto-esplicativo
- **Copia** - Auto-esplicativo
- **Incolla** - Auto-esplicativo
- **Struttura: espandere** e comprimere sezioni di codice. <br>Vedere anche: [Struttura .](../ide/outlining.md)
- **Controllo del codice** sorgente: consente di visualizzare la cronologia dei contributi di codice a un repository open source.

### <a name="middle-pane-scroll-bar"></a>Riquadro centrale, barra di scorrimento

La barra di scorrimento può non scorrere il codice. È anche possibile usarlo per aprire un altro riquadro dell'editor di codice. È anche possibile usare la barra di scorrimento per creare codice in modo più efficiente aggiungendo annotazioni o usando diverse modalità di visualizzazione.

#### <a name="split-the-code-window"></a>Dividere la finestra del codice

Nella barra di scorrimento dell'editor di codice è presente un **pulsante** Dividi in alto a destra. Quando lo si sceglie, è possibile aprire un altro riquadro dell'editor di codice. Ciò è utile perché operano indipendentemente l'uno dall'altro, quindi è possibile usarli per lavorare sul codice in posizioni diverse.

![Screenshot che mostra il riquadro centrale dell'editor di codice XAML in Visual Studio 2019 con il pulsante Dividi evidenziato in alto a destra nel riquadro.](media/code-editor-split-window-button.png)

Per altre informazioni su come dividere una finestra dell'editor, vedere la [pagina Gestisci finestre dell'editor.](../ide/how-to-manage-editor-windows.md)

#### <a name="use-annotations-or-map-mode"></a>Usare annotazioni o modalità mappa

È anche possibile modificare l'aspetto della barra di scorrimento e le funzionalità aggiuntive contenute. Molti utenti, ad esempio, desiderano includere annotazioni nella barra di scorrimento, che forniscono segnali visivi, ad esempio modifiche al codice, punti di interruzione, segnalibri, errori e posizione del cursore. 

Altri apprezzano *l'uso della modalità mappa*, che visualizza le righe di codice in miniatura sulla barra di scorrimento. Gli sviluppatori che hanno molto codice in un file potrebbero trovare che la modalità di mapping tiene traccia delle righe di codice in modo più efficace rispetto alla barra di scorrimento predefinita.

Per altre informazioni su come modificare le impostazioni predefinite della barra di scorrimento, vedere la pagina [Personalizzare la barra di scorrimento.](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

## <a name="xaml-specific-features"></a>Funzionalità specifiche di XAML

La maggior parte delle funzionalità seguenti è disponibile universalmente nell'IDE di Visual Studio, ma alcune sono state aggiunte dimensioni che semplificano la scrittura di codice per gli sviluppatori XAML.

### <a name="xaml-code-snippets"></a>Frammenti di codice XAML

I frammenti di codice sono piccoli blocchi di codice riutilizzabile che è possibile inserire  in un file di codice usando il comando del menu di scelta rapida Inserisci frammento di codice o una combinazione di tasti di scelta rapida (**CTRL** + **K**, **CTRL** + **X**). [IntelliSense](../ide/using-intellisense.md) è stato migliorato in modo che supporti la visualizzazione di frammenti XAML, che funzionano sia per i frammenti predefiniti che per i frammenti personalizzati aggiunti manualmente. Alcuni frammenti di codice XAML disponibili includono `#region` , , , e `Column definition` `Row definition` `Setter` `Tag` .

![Editor di codice XAML con le opzioni del frammento di codice XAML visualizzate in IntelliSense](media/xaml-code-snippets.png "Screenshot dell'editor di codice XAML con le opzioni del frammento di codice XAML visualizzate in IntelliSense")

Per altre informazioni, vedere le pagine [Frammenti di codice e](../ide/code-snippets.md) [Frammenti di](../ide/visual-csharp-code-snippets.md) codice C#.

### <a name="xaml-region-support"></a>Supporto #region XAML

A partire da Visual Studio 2015, è stato reso disponibile #region supporto per gli sviluppatori XAML in WPF e UWP e più di recente anche in [Xamarin.Forms.](/xamarin/xamarin-forms/user-interface/text/editor/) Nel Visual Studio 2019 si continuano a apportare miglioramenti incrementali al #region supporto. Ad esempio, nella [versione 16.4](/visualstudio/releases/2019/release-notes-v16.4/) e successive, le #region vengono mostrate quando si inizia a digitare `<!` .

![Editor di codice XAML con #region opzioni visualizzate in IntelliSense](media/code-editor-xaml-region.png "Screenshot dell'editor di codice XAML con #region seguenti in IntelliSense")

È possibile usare le aree quando si desidera raggruppare sezioni del codice che si desidera espandere o comprimere.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Per altre informazioni sulle aree, vedere la [#region (Riferimenti per C#).](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) Per altre informazioni sull'espansione e la compressione di sezioni di codice, vedere la [pagina Struttura.](../ide/outlining.md)

### <a name="xaml-comments"></a>Commenti XAML

Gli sviluppatori preferiscono spesso documentare il codice usando i commenti. È possibile aggiungere commenti al codice XAML presente nella **scheda MainWindow.xaml** nei modi seguenti:

- Immettere `<!--` prima di un commento e quindi aggiungere dopo il `-->` commento.
- Immettere `<!` e quindi scegliere `!--` dall'elenco di opzioni.

  ![Nell'editor di codice XAML fare clic con il pulsante destro del mouse sulla finestra di dialogo Aggiungi commenti](media/xaml-code-editor-comments.png "Screenshot del menu di scelta rapida per aggiungere commenti nell'editor di codice XAML")

- Selezionare il codice da racchiudere in un commento e quindi scegliere il pulsante **Commento** sulla barra degli strumenti nell'IDE. Per invertire l'azione, scegliere il **pulsante Rimuovi** commento.

  ![Il pulsante Commento e il pulsante Rimuovi commento nella barra degli strumenti dell'IDE](media/comment-undo-comment-buttons.png "Screenshot del pulsante Commento e del pulsante Rimuovi commento nella barra degli strumenti dell'IDE")

- Selezionare il codice da racchiudere tra un commento e quindi premere **CTRL** + **K**, **CTRL** + **C**. Per rimuovere il commento dal codice selezionato, premere **CTRL** + **K,**  + **CTRL+U.**

Per altre informazioni su come usare i commenti nel codice C# presente nella scheda **MainWindow.xaml.cs,** vedere la pagina [Commenti della](/dotnet/csharp/language-reference/language-specification/documentation-comments/) documentazione.

### <a name="xaml-lightbulbs"></a>Lampadine XAML

Le icone a lampadina visualizzate nel codice XAML fanno parte delle [azioni](../ide/quick-actions.md) rapide che è possibile usare per eseguire il refactoring, generare o modificare in altro modo il codice.

Ecco alcuni esempi di come possono trarre vantaggio dall'esperienza di scrittura del codice XAML:

- **Rimuovere gli spazi dei nomi non necessari.** Nell'editor di codice XAML gli spazi dei nomi non necessari vengono visualizzati in grigio. Se si passa il cursore su un oggetto non necessario usando, verrà visualizzata una lampadina. Quando si  sceglie l'opzione Rimuovi spazi dei nomi non necessari dall'elenco a discesa, viene visualizzata un'anteprima di ciò che è possibile rimuovere.

  ![Opzione Rimuovi spazi dei nomi non necessari dell'editor di codice XAML dalla lampadina Azioni rapide](media/xaml-code-editor-dimmed-namespaces-preview.png "Screenshot dell'opzione Rimuovi spazi dei nomi non necessari dell'editor di codice XAML visualizzata usando la lampadina Azioni rapide")

- **Rinominare lo spazio dei nomi**. Questa funzionalità, disponibile nel menu di scelta rapida dopo aver evidenziato uno spazio dei nomi, semplifica la modifica di più istanze di un'impostazione contemporaneamente. È anche possibile accedere a questa funzionalità usando la barra dei **menu,** Modifica  >  **refactoring** Rinomina oppure premendo CTRL R e quindi  >  di  +  **nuovo CTRL** + **R.**

  ![Opzione Rinomina spazio dei nomi dell'editor di codice XAML dal menu di scelta rapida](media/code-editor-rename-namespace.png "Screenshot dell'opzione Rinomina spazio dei nomi dell'editor di codice XAML visualizzata tramite il menu di scelta rapida")

  Per altre informazioni, vedere la pagina [Rinominare un refactoring dei](../ide/reference/rename.md) simboli di codice.

### <a name="conditional-xaml-for-uwp"></a>XAML condizionale per UWP

XAML condizionale consente di usare il metodo [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) nel markup XAML. Puoi così impostare le proprietà e creare istanze di oggetti nel markup in base alla presenza di un'API senza dover usare code-behind.

Per altre informazioni, vedere la [pagina XAML](/windows/uwp/debug-test-perf/conditional-xaml/) condizionale e la pagina Ospitare controlli [XAML UWP nelle app desktop (isole XAML).](/windows/apps/desktop/modernize/xaml-islands/)

### <a name="xaml-structure-visualizer"></a>Visualizzatore struttura XAML

La funzionalità Visualizzatore struttura nell'editor di codice mostra le linee guida della struttura, ovvero linee tratteggiate verticali che indicano elementi tag aperti e chiusi corrispondenti nel codice. Queste linee verticali rendono più semplice vedere dove iniziano e terminano i blocchi logici.

Per altre informazioni, vedere la tabella [codici Esplorazione.](../ide/navigating-code.md)

### <a name="intellicode-for-xaml"></a>IntelliCode per XAML

Quando si aggiunge un tag XAML al codice, in genere si inizia con una parentesi uncinata `<` sinistra. Quando si digita la parentesi uncinata, viene visualizzato un menu IntelliCode che elenca alcuni dei tag XAML più diffusi. Scegliere quello che si vuole aggiungere rapidamente al codice.

È possibile riconoscere le selezioni IntelliCode perché vengono visualizzate nella parte superiore dell'elenco e sono contrassegnate da stelle.

![Elenco IntelliCode per l'editor di testo XAML](media/xaml-intellicode-selection.png "Screenshot dell'elenco IntelliCode per l'editor di testo XAML")

Per altre informazioni, vedere la [pagina Panoramica di IntelliCode.](/visualstudio/intellicode/overview/)

### <a name="settings"></a>Impostazioni

Per altre informazioni su *tutte le* impostazioni nell'IDE Visual Studio, vedere la pagina [Funzionalità dell'editor di](../ide/writing-code-in-the-code-and-text-editor.md) codice.

## <a name="xaml-optional-settings"></a>Impostazioni facoltative XAML

È possibile usare la [finestra di](../ide/reference/options-dialog-box-visual-studio.md) dialogo Opzioni per modificare le impostazioni predefinite per l'editor di codice XAML. Per visualizzare le impostazioni, scegliere **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **XAML.**

![Elenco Opzioni per l'editor di testo XAML](media/xaml-tools-options.png "Screenshot dell'elenco Opzioni per l'editor di testo XAML")

> [!NOTE]
> È anche possibile usare i tasti di scelta rapida per accedere alla finestra di dialogo Opzioni. Ecco come: Premere **CTRL** + **Q** per cercare nell'IDE, digitare **Opzioni** e quindi premere **INVIO.** Premere quindi **CTRL** E per cercare nella finestra di dialogo Opzioni, digitare Editor di +  testo, premere **INVIO,** digitare **XAML** e quindi **premere INVIO.** 
>
> Per altre informazioni sui tasti di scelta rapida, vedere la [pagina Suggerimenti per](../ide/productivity-shortcuts.md#code-editor) i Visual Studio.

### <a name="universal-text-editor-options"></a>Opzioni dell'editor di testo universale

Nella finestra [di dialogo](../ide/reference/options-text-editor-xaml-formatting.md) Opzioni per XAML i primi tre elementi seguenti sono universali per tutti i linguaggi di programmazione supportati dall Visual Studio IDE. Per altre informazioni su queste opzioni e su come usarle, vedere le informazioni collegate nella tabella seguente.

|Nome  |Altre informazioni  |
|---------|---------|
|Generale  | [Finestra di dialogo Opzioni: Editor di testo > tutti i linguaggi](../ide/reference/options-text-editor-all-languages.md) |
|Barre di scorrimento | [Opzioni, Editor di testo, Tutti i linguaggi, Barre di scorrimento](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Schede  |  [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Opzioni dell'editor di testo specifiche di XAML

La tabella seguente elenca le impostazioni nella finestra [di](../ide/reference/options-text-editor-xaml-formatting.md) dialogo Opzioni che possono migliorare l'esperienza di modifica quando si sviluppano app basate su XAML. Per altre informazioni su queste opzioni e su come usarle, vedere le informazioni collegate.

|Nome  |Altre informazioni  |
|---------|---------|
|Formattazione | [Opzioni, Editor di testo, XAML, Formattazione](../ide/reference/options-text-editor-xaml-formatting.md) |
|Varie |  [Opzioni, Editor di testo, XAML, Varie](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> L'impostazione Imposta il nome  del metodo del gestore **eventi** in maiuscolo nella sezione Varie è particolarmente utile per gli sviluppatori XAML. Questa impostazione è *disattivata* per impostazione predefinita perché è nuova, ma è consigliabile impostarla su per supportare la corretta distinzione tra maiuscole e minuscole nel codice. 

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come modificare il codice in tempo reale mentre si esegue l'app in modalità di debug, vedere la pagina [Ricaricamento rapido XAML.](xaml-hot-reload.md)

## <a name="see-also"></a>Vedi anche

- [Visual Studio dell'editor di codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML in all UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML in app Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
- [Sviluppo di app per dispositivi mobili Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 per Mac - Presentazione dell'IDE (Mac)](/visualstudio/mac/ide-tour/)
