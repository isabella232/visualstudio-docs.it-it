---
title: Personalizzare il layout delle finestre
ms.date: 01/23/2017
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1963c76b67eaedea4cdf013739c112275ecffb2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596710"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Personalizzare il layout delle finestre in Visual Studio

In Visual Studio è possibile personalizzare la posizione, la dimensione e il comportamento delle finestre per creare layout di finestra ottimali per i vari flussi di lavoro relativi allo sviluppo. Quando si personalizza il layout, l'IDE memorizza le modifiche apportate. Se, ad esempio, si cambia la posizione di ancoraggio di **Esplora soluzioni** e quindi si chiude Visual Studio, al successivo avvio di quest'ultimo, anche da un altro computer, la finestra di **Esplora soluzioni** risulterà ancorata nella stessa posizione.

È anche possibile assegnare un nome a un layout personalizzato e salvarlo, e quindi passare da un layout all'altro con un unico comando. È ad esempio possibile creare un layout per la modifica e un altro per il debug e passare dall'uno all'altro usando il comando di menu **Finestra** > **Applica layout finestra**.

## <a name="kinds-of-windows"></a>Tipi di finestre

### <a name="tool-and-document-windows"></a>Finestre dei documenti e degli strumenti

L'IDE presenta due tipi di finestre di base: *finestre degli strumenti* e *finestre dei documenti*. Le finestre degli strumenti includono **Esplora soluzioni**, **Esplora server**, **Finestra di output**, **Elenco errori**, le finestre di progettazione, le finestre del debugger e così via. Le finestre dei documenti contengono i file del codice sorgente, file di testo arbitrario, file config e così via. Le finestre degli strumenti possono essere ridimensionate e trascinate dalla barra del titolo. Le finestre di documento possono essere trascinate dalla relativa scheda. fare clic con il pulsante destro del mouse sulla scheda o sulla barra del titolo per impostare altre opzioni nella finestra.

Nel menu **Finestra** vengono visualizzate le opzioni disponibili per ancorare, rendere mobili e nascondere le finestre nell'IDE. Fare clic con il pulsante destro del mouse sulla barra del titolo o sulla scheda di una finestra per visualizzare opzioni aggiuntive per tale specifica finestra. È possibile visualizzare più istanze di determinate finestre degli strumenti per volta. Ad esempio, è possibile visualizzare più finestre di un browser Web, nonché creare ulteriori istanze di alcune finestre degli strumenti selezionando **Nuova finestra** nel menu **Finestra** .

### <a name="preview-tab-document-windows"></a>Scheda Anteprima (finestre dei documenti)

Nella scheda **Anteprima** è possibile visualizzare i file nell'editor senza aprirli. È possibile visualizzare i file di anteprima selezionandoli in **Esplora soluzioni**, durante il debug quando si esegue l'istruzione nei file, con **Vai a definizione** e quando si esplorano i risultati di una ricerca. I file di anteprima vengono visualizzati in una scheda a destra della scheda del documento. Il file viene aperto per la modifica se viene modificato o se si sceglie **Apri**.

### <a name="tab-groups"></a>Gruppi di schede

I gruppi di schede estendono la possibilità di gestire l'area di lavoro limitata mentre si lavora con due o più documenti aperti nell'IDE. È possibile organizzare più finestre dei documenti e finestre degli strumenti in gruppi di schede orizzontali o verticali, nonché spostare i documenti in ordine casuale da un gruppo di schede a un altro.

### <a name="split-windows"></a>Finestre divise

Quando è necessario visualizzare o modificare due percorsi contemporaneamente in un documento, è possibile dividere le finestre. Per dividere il documento in due sezioni che scorrono in modo indipendente, fare clic su **Dividi** nel menu **Finestra** . Fare clic su **Rimuovi divisione** nel menu **Finestra** per ripristinare la visualizzazione singola.

### <a name="toolbars"></a>Toolbars

Le barre degli strumenti possono essere disposte trascinandole o utilizzando la finestra di dialogo **Personalizza** . Per altre informazioni su come posizionare e personalizzare le barre degli strumenti, vedere [Procedura: personalizzare menu e barre degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Disporre e ancorare le finestre

Una finestra del documento o una finestra degli strumenti può essere *ancorata*in modo che abbia una posizione e una dimensione all'interno della cornice della finestra dell'IDE. È anche possibile renderla mobile come finestra separata indipendente dell'IDE. Le finestre degli strumenti possono essere ancorate in qualsiasi area all'interno della cornice dell'IDE; alcune di esse possono essere ancorate come finestre a schede nella cornice dell'editor. Le finestre dei documenti possono essere ancorate all'interno della cornice dell'editor e bloccate nella posizione corrente nell'ordine di tabulazione. È possibile ancorare più finestre per renderle mobili in un *raggruppamento* sopra o all'esterno dell'IDE. Le finestre degli strumenti possono anche essere nascoste o ridotte a icona.

È possibile disporre le finestre nei modi seguenti:

- Bloccare le finestre dei documenti a sinistra della scheda.

- Ancorare le schede delle finestre alla cornice per la modifica.

- Ancorare le finestre degli strumenti al bordo di una cornice nell'IDE.

- Rendere mobili le finestre dei documenti o degli strumenti sopra o all'esterno dell'IDE.

- Nascondere le finestre degli strumenti lungo il bordo dell'IDE.

- Visualizzare le finestre su monitor diversi.

- Reimpostare la posizione delle finestre sul layout predefinito o su un layout personalizzato salvato.

Disporre le finestre degli strumenti e dei documenti trascinandole, usando comandi del menu **Finestra** o facendo clic con il pulsante destro del mouse sulla barra del titolo della finestra da disporre.

### <a name="dock-windows"></a>Ancorare le finestre

Quando si seleziona e si trascina la barra del titolo di una finestra degli strumenti oppure la scheda della finestra del documento, viene visualizzata una guida a forma di rombo. Durante l'operazione di trascinamento, quando il cursore si trova sopra una delle frecce nel rombo, viene visualizzata un'area ombreggiata che mostra la posizione in cui verrà ancorata la finestra se viene rilasciato il mouse in quel preciso momento.

Per spostare una finestra ancorabile senza ancorarla nella posizione di destinazione, tenere premuto **CTRL** mentre si trascina la finestra.

Per ricollocare una finestra degli strumenti o una finestra del documento nella posizione di ancoraggio più recente, premere **CTRL** e fare doppio clic sulla scheda o sulla barra del titolo della finestra.

Nella figura seguente viene illustrata la guida a forma di rombo per le finestre dei documenti, che è possibile ancorare solo all'interno della cornice per la modifica:

![Guida a forma di rombo finestra del documento](../ide/media/documentwindowguidediamonds.png)

Le finestre degli strumenti possono essere bloccate su un lato di una cornice nell'IDE o all'interno della cornice per la modifica. Per consentire all'utente di ancorare di nuovo la finestra con facilità, viene visualizzata una guida a forma di rombo quando si trascina una finestra degli strumenti in un'altra posizione.

![Guide a forma di rombo finestra degli strumenti](../ide/media/vs10guidediamond.png)

La figura seguente illustra la finestra **Esplora soluzioni** mentre viene ancorata in una nuova posizione, delineata dall'area ombreggiata in blu:

![Ancoraggio di Esplora soluzioni in una nuova posizione](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Chiudere e nascondere automaticamente le finestre degli strumenti

È possibile chiudere una finestra degli strumenti facendo clic sulla **X** in alto a destra della barra del titolo. Per riaprire la finestra, usare i tasti di scelta rapida o il comando di menu corrispondente. Le finestre degli strumenti supportano una funzionalità denominata *Nascondi automaticamente*, che fa in modo che una finestra scompaia dallo schermo quando si usa un'altra finestra. Quando una finestra viene nascosta automaticamente, il suo nome viene visualizzato in una scheda sul bordo dell'IDE. Per utilizzare nuovamente la finestra, posizionare il mouse sulla scheda affinché sia possibile visualizzare di nuovo la finestra.

![Nascondi automaticamente](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Per specificare se l'opzione Nascondi automaticamente debba essere applicata alle finestre degli strumenti singolarmente o in gruppi ancorati, selezionare o deselezionare **Nascondi automaticamente ha effetto solo sulla finestra degli strumenti attiva** nella finestra di dialogo **Opzioni**. Per altre informazioni, vedere [General, Environment, Options Dialog Box](../ide/reference/general-environment-options-dialog-box.md) (Finestra di dialogo Generale, Ambiente, Opzioni).

> [!NOTE]
> Le finestre degli strumenti con l'opzione Nascondi automaticamente abilitata potrebbero essere temporaneamente visualizzate quando la finestra ha lo stato attivo. Per nascondere di nuovo la finestra, selezionare un elemento all'esterno della finestra corrente. Quando la finestra non è nello stato attivo, non viene più visualizzata.

### <a name="specifying-a-second-monitor"></a>Indicazione di un secondo monitor

Se si dispone di un secondo monitor, supportato dal sistema operativo, è possibile scegliere in quale monitor visualizzare una finestra. È possibile anche raggruppare più finestre in *raggruppamenti* su altri monitor.

> [!TIP]
> È possibile creare più istanze di **Esplora soluzioni** e spostarle in un altro monitor. Fare clic con il pulsante destro del mouse sulla finestra e scegliere **Nuova visualizzazione Esplora soluzioni**. È possibile ricollocare tutte le finestre nel monitor originale facendo doppio clic e premendo il tasto **CTRL**.

### <a name="reset-name-and-switch-between-window-layouts"></a>Reimpostare, nominare e passare da un layout di finestra all'altro

È possibile ripristinare il layout di finestra originale dell'IDE per la raccolta delle impostazioni utilizzando il comando **Reimposta layout finestra** . Quando si esegue questo comando, si verificano le seguenti azioni:

- Tutte le finestre vengono spostate nelle rispettive posizioni predefinite.

- Le finestre chiuse nel layout di finestra predefinito vengono chiuse.

- Le finestre aperte nel layout di finestra predefinito vengono aperte.

### <a name="create-and-save-custom-layouts"></a>Creare e salvare layout personalizzati

Visual Studio consente di salvare fino a 10 layout di finestra personalizzati e di spostarsi rapidamente da un layout all'altro. La seguente procedura illustra come creare, salvare, richiamare e gestire layout personalizzati con cui vengono usati più monitor grazie a finestre degli strumenti ancorate e mobili.

Creare prima di tutto una soluzione di test che include due progetti, ognuno con un layout ottimale diverso.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Creare un progetto per interfaccia utente e personalizzare il layout

1. Creare un nuovo oggetto progetto **App WPF** C#. Si immagini di sviluppare un'interfaccia utente in questo progetto. Si vuole aumentare al massimo lo spazio per la finestra di progettazione e spostare le altre finestra degli strumenti in modo che non diano fastidio.

2. Se sono disponibili più monitor, spostare le finestre **Esplora soluzioni** e **Proprietà** sul secondo monitor. In un sistema con un solo monitor provare a chiudere tutte le finestre eccetto quella di progettazione.

3. Premere **CTRL**+**ALT**+**X** per visualizzare la finestra **Casella degli strumenti**. Se la finestra è ancorata, trascinarla in modo da spostarla nel punto in cui si vuole posizionarla.

4. Premere **F5** per attivare la modalità di debug in Visual Studio. Regolare la posizione delle finestre di debug **Auto**, **Stack di chiamate** e **Output** nel modo voluto. Il layout che si sta per creare verrà applicato sia alla modalità di modifica che a quella di debug.

5. Quando si ottengono i layout voluti sia in modalità di modifica che di debug, scegliere **Finestra** > **Salva layout finestra**. Assegnare a questo layout il nome "Finestra di progettazione".

     Notare che al nuovo layout viene assegnato il tasto di scelta rapida successivo dell'elenco riservato **CTRL**+**ALT**+**1...0**.

#### <a name="create-a-database-project-and-layout"></a>Creare un layout e un progetto di database

1. Aggiungere un nuovo progetto **Database SQL Server** alla soluzione.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nuovo progetto e scegliere **Visualizza in Esplora oggetti**. Verrà visualizzata la finestra **Esplora oggetti di SQL Server** che consente di accedere a tabelle, viste e altri oggetti nel database. È possibile impostare la finestra come mobile o lasciarla ancorata. Regolare le altre finestre degli strumenti nel modo desiderato. Per maggior realismo è possibile aggiungere un database effettivo, ma questa operazione non è necessaria ai fini di questa procedura dettagliata.

3. Quando il layout è quello desiderato, dal menu principale scegliere **Finestra** > **Salva layout finestra**. Assegnare a questo layout il nome "Progetto di database". Per questo progetto non è necessario creare anche un layout per la modalità di debug.

#### <a name="switch-between-the-layouts"></a>Passare da un layout a un altro

Per passare da un layout a un altro, usare i tasti di scelta rapida oppure nel menu principale scegliere **Finestra** > **Applica layout finestra**.

![Applicare menu layout di finestra](../ide/media/vs2015_applywindowlayout.png)

Dopo l'applicazione del layout dell'interfaccia utente, notare che questo viene mantenuto sia modalità di modifica che in modalità di debug.

Se in ufficio si usa una configurazione a più monitor e a casa una laptop con un solo monitor, è possibile creare layout ottimizzati per ogni computer.

> [!NOTE]
> Se si applica un layout a più monitor in un sistema a monitor singolo, le finestre mobili posizionate sul secondo monitor risulteranno nascoste dietro la finestra di Visual Studio. È possibile portare le finestre in primo piano premendo **ALT + TAB**. Se in seguito si apre Visual Studio con più monitoraggi, è possibile ripristinare le posizioni specificate applicando nuovamente il layout.

#### <a name="manage-and-roam-your-layouts"></a>Gestire o effettuare il roaming dei layout

Per rimuovere, rinominare o riordinare il layout personalizzato, scegliere **Finestra** > **Gestisci layout finestra**. Se si sposta un layout, l'associazione principale viene adattata automaticamente alla nuova posizione nell'elenco. Le associazioni non possono essere modificate diversamente, di conseguenza è possibile archiviare un massimo di 10 layout alla volta.

![Gestire i layout delle finestre](../ide/media/managewindowlayouts.png)

Per ricordare i tasti di scelta rapida associati ai vari layout, scegliere **Finestra** > **Applica layout finestra**.

Il roaming di questi layout verrà effettuato automaticamente tra le edizioni di Visual Studio, oltre che tra le istanze di Blend in computer diversi e da una qualsiasi edizione Express a una qualsiasi altra organizzazione Express. Non viene invece effettuato il roaming dei layout tra Visual Studio, Blend ed Express.

## <a name="see-also"></a>Vedere anche

- [How to: Move around in the IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md) (Procedura: Spostarsi all'interno dell'IDE)
