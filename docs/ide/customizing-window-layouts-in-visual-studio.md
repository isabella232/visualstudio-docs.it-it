---
title: Personalizzare il layout delle finestre
description: Informazioni su come personalizzare le caratteristiche di Windows per creare layout più adatti per diversi flussi di lavoro di sviluppo.
ms.custom: SEO-VS-2020
ms.date: 07/31/2020
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
ms.openlocfilehash: c433a6faf3eab9dd959cc25f26033c74852c0899
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006666"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Personalizzare il layout delle finestre in Visual Studio

In Visual Studio è possibile personalizzare la posizione, la dimensione e il comportamento delle finestre per creare layout di finestra ottimali per i vari flussi di lavoro relativi allo sviluppo. Quando si personalizza il layout, l'IDE memorizza le modifiche apportate. Se, ad esempio, si cambia la posizione di ancoraggio di **Esplora soluzioni** e quindi si chiude Visual Studio, al successivo avvio di quest'ultimo, anche da un altro computer, la finestra di **Esplora soluzioni** risulterà ancorata nella stessa posizione.

È anche possibile assegnare un nome a un layout personalizzato e salvarlo, e quindi passare da un layout all'altro con un unico comando. Ad esempio, è possibile creare un layout per la modifica e un layout per il debug e passare da un layout all'altra usando il comando di menu **finestra**  >  **applica layout finestra** .

## <a name="tool-and-document-windows"></a>Finestre dei documenti e degli strumenti

L'IDE presenta due tipi di finestre di base: *finestre degli strumenti* e *finestre dei documenti*. Le finestre degli strumenti includono **Esplora soluzioni**, **Esplora server**, **finestra di output**, **Elenco errori**, le finestre di progettazione, le finestre del debugger e così via. Le finestre dei documenti contengono i file del codice sorgente, file di testo arbitrario, file config e così via. Le finestre degli strumenti possono essere ridimensionate e trascinate dalla barra del titolo. Le finestre di documento possono essere trascinate in base alla relativa scheda. Fare clic con il pulsante destro del mouse sulla scheda o sulla barra del titolo per impostare altre opzioni nella finestra.

Nel menu **finestra** vengono visualizzate le opzioni per l'ancoraggio, la virgola mobile e il nascondere le finestre nell'IDE. Fare clic con il pulsante destro del mouse sulla barra del titolo o sulla scheda di una finestra per visualizzare opzioni aggiuntive per tale specifica finestra. È possibile visualizzare più istanze di determinate finestre degli strumenti per volta. Ad esempio, è possibile visualizzare più finestre di un browser Web, nonché creare ulteriori istanze di alcune finestre degli strumenti selezionando **Nuova finestra** nel menu **Finestra** .

### <a name="split-windows"></a>Finestre divise

Quando è necessario visualizzare o modificare due percorsi contemporaneamente in un documento, è possibile dividere le finestre. Per dividere il documento in due sezioni che scorrono in modo indipendente, fare clic su **Dividi** nel menu **Finestra** . Fare clic su **Rimuovi divisione** nel menu **Finestra** per ripristinare la visualizzazione singola.

### <a name="tabs"></a>Schede

È possibile utilizzare le schede per disporre il layout in diversi modi. Ad esempio, è possibile visualizzare un'anteprima di un file nell'editor senza aprire il file, è possibile raggruppare le schede e altro ancora.

#### <a name="preview-tab-document-windows"></a>Scheda Anteprima (finestre dei documenti)

Nella scheda **Anteprima** è possibile visualizzare i file nell'editor senza aprirli. È possibile visualizzare in anteprima i file scegliendo i file in **Esplora soluzioni**, durante il debug quando si esegue l'istruzione nei file, con **Vai a definizione** e quando si esplorano i risultati di una ricerca. I file di anteprima vengono visualizzati in una scheda a destra della scheda del documento. Il file viene aperto per la modifica se viene modificato o se si sceglie **Apri**.

::: moniker range="vs-2019"

#### <a name="vertical-document-tabs"></a>Schede verticali del documento

**[Novità della versione 16,4](/visualstudio/releases/2019/release-notes-v16.4/)**: è stata aggiunta una delle principali richieste di funzionalità, le [schede verticali dei documenti](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html), nella versione di Visual Studio 2019 versione 16,4. A questo punto, è possibile gestire le schede dei documenti in un elenco verticale sul lato sinistro o destro dell'editor.

È possibile applicare le schede verticali dei documenti nei modi seguenti:

- Scegliere **strumenti**  >  **Opzioni**  >  **ambiente**  >  **schede e finestre** dalla barra dei menu. Quindi, dal controllo **Layout scheda Set** , scegliere **Top**, **Left** o **right** dall'elenco a discesa.

- Fare clic con il pulsante destro del mouse su una scheda, scegliere **Imposta layout scheda**, quindi scegliere a **sinistra** o a **destra**. Per ripristinare la posizione predefinita delle schede, scegliere **superiore**.

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Animazione che mostra le schede verticali del documento in azione":::

::: moniker-end

#### <a name="tab-groups"></a>Gruppi di schede

I gruppi di schede estendono la possibilità di gestire l'area di lavoro limitata mentre si lavora con due o più documenti aperti nell'IDE. È possibile organizzare più finestre dei documenti e finestre degli strumenti in gruppi di schede orizzontali o verticali, nonché spostare i documenti in ordine casuale da un gruppo di schede a un altro.

### <a name="toolbars"></a>Barre degli strumenti

È possibile disporre le barre degli strumenti trascinandoli nella posizione desiderata o utilizzando la finestra di dialogo **Personalizza** . Per altre informazioni su come posizionare e personalizzare le barre degli strumenti, vedere [procedura: personalizzare menu e barre degli](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)strumenti.

## <a name="arrange-and-dock-windows"></a>Disporre e ancorare le finestre

Una finestra del documento o una finestra degli strumenti può essere *ancorata*, in modo che abbia una posizione e una dimensione all'interno della cornice della finestra IDE. È anche possibile posizionarlo come una finestra mobile separata esterna all'IDE.

È possibile ancorare una finestra degli strumenti in un punto qualsiasi all'interno del frame IDE. È anche possibile ancorare alcune finestre degli strumenti come finestre a schede nella cornice dell'editor. È possibile ancorare le finestre dei documenti all'interno del frame dell'editor ed è possibile aggiungerle alla posizione corrente nell'ordine di tabulazione.

È anche possibile ancorare più finestre per renderle mobili in una *zattera* sopra o all'esterno dell'IDE. Le finestre degli strumenti possono anche essere nascoste o ridotte a icona.

È possibile disporre le finestre nei modi seguenti:

- Bloccare le finestre dei documenti a sinistra della scheda.

- Ancorare le schede delle finestre alla cornice per la modifica.

- Ancorare le finestre degli strumenti al bordo di una cornice nell'IDE.

- Rendere mobili le finestre dei documenti o degli strumenti sopra o all'esterno dell'IDE.

- Nascondere le finestre degli strumenti lungo il bordo dell'IDE.

- Visualizzare le finestre su monitor diversi.

- Reimpostare la posizione delle finestre sul layout predefinito o su un layout personalizzato salvato.

Per disporre le finestre degli strumenti e dei documenti, è possibile posizionare il cursore sulla barra del titolo di una finestra e trascinarlo nella posizione desiderata. In alternativa, è possibile fare clic con il pulsante destro del mouse sulla barra del titolo della finestra per utilizzare il menu di scelta rapida oppure è possibile utilizzare i comandi disponibili nel menu **finestra** .

### <a name="dock-windows"></a>Ancorare le finestre

Quando si seleziona e si trascina la barra del titolo di una finestra degli strumenti oppure la scheda della finestra del documento, viene visualizzata una guida a forma di rombo. Durante l'operazione di trascinamento, quando il cursore si trova sopra una delle frecce nel rombo, viene visualizzata un'area ombreggiata che mostra la posizione in cui verrà ancorata la finestra se viene rilasciato il mouse in quel preciso momento.

Per spostare una finestra ancorabile senza ancorarla nella posizione di destinazione, tenere premuto **CTRL** mentre si trascina la finestra.

Per restituire una finestra degli strumenti o una finestra del documento nella posizione ancora più recente, premere **CTRL** mentre si fa doppio clic sulla barra del titolo o sulla scheda della finestra.

Nella figura seguente viene illustrata la guida a forma di rombo per le finestre dei documenti, che è possibile ancorare solo all'interno della cornice per la modifica:

![Guida a forma di rombo finestra del documento](../ide/media/documentwindowguidediamonds.png)

Le finestre degli strumenti possono essere bloccate su un lato di una cornice nell'IDE o all'interno della cornice per la modifica. Per consentire all'utente di ancorare di nuovo la finestra con facilità, viene visualizzata una guida a forma di rombo quando si trascina una finestra degli strumenti in un'altra posizione.

![Guide a forma di rombo finestra degli strumenti](../ide/media/vs10guidediamond.png)

La figura seguente illustra la finestra **Esplora soluzioni** mentre viene ancorata in una nuova posizione, delineata dall'area ombreggiata in blu:

![Ancoraggio di Esplora soluzioni in una nuova posizione](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Chiudere e nascondere automaticamente le finestre degli strumenti

È possibile chiudere una finestra degli strumenti facendo clic sulla **X** in alto a destra della barra del titolo. Per riaprire la finestra, usare i tasti di scelta rapida o il comando di menu corrispondente. Le finestre degli strumenti supportano una funzionalità denominata *Nascondi automaticamente*, che causa la disattivazione della finestra quando si usa una finestra diversa. Quando una finestra viene nascosta automaticamente, il suo nome viene visualizzato in una scheda sul bordo dell'IDE. Per utilizzare nuovamente la finestra, posizionare il mouse sulla scheda affinché sia possibile visualizzare di nuovo la finestra.

![Nascondi automaticamente](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Per impostare l'opzione Nascondi automaticamente sulle finestre degli strumenti singolarmente o in gruppi ancorati, selezionare o deselezionare **Nascondi automaticamente pulsante influisca sulle finestre degli strumenti attive solo** nella finestra di dialogo **Opzioni** . Per ulteriori informazioni, vedere [generale, ambiente, finestra di dialogo Opzioni](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Le finestre degli strumenti con l'opzione Nascondi automaticamente abilitata potrebbero essere temporaneamente visualizzate quando la finestra ha lo stato attivo. Per nascondere di nuovo la finestra, selezionare un elemento all'esterno della finestra corrente. Quando la finestra non è nello stato attivo, non viene più visualizzata.

### <a name="use-a-second-monitor"></a>Usa un secondo monitoraggio

Se si dispone di un secondo monitor, supportato dal sistema operativo, è possibile scegliere in quale monitor visualizzare una finestra. È anche possibile raggruppare più finestre tra le *Zattere* su altri monitoraggi.

> [!TIP]
> È possibile creare più istanze di **Esplora soluzioni** e spostarle in un altro monitor. Fare clic con il pulsante destro del mouse sulla finestra e scegliere **Nuova visualizzazione Esplora soluzioni**. È possibile riportare tutte le finestre al monitor originale facendo doppio clic quando si sceglie il tasto **CTRL** .

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

2. Se sono presenti più monitoraggi, effettuare il pull della finestra **Esplora soluzioni** e della finestra **Proprietà** sul secondo monitor. In un sistema con un solo monitor provare a chiudere tutte le finestre eccetto quella di progettazione.

3. Premere **CTRL** + **ALT** + **X** per visualizzare la finestra **casella degli strumenti** . Se la finestra è ancorata, trascinarla in modo da spostarla nel punto in cui si vuole posizionarla.

4. Premere **F5** per attivare la modalità di debug di Visual Studio. Modificare la posizione delle finestre di debug **auto**, **stack di chiamate** e **output** nel modo desiderato. Il layout che si sta per creare verrà applicato sia alla modalità di modifica che a quella di debug.

5. Quando i layout in modalità di debug e di modifica sono quelli desiderati, scegliere **finestra**  >  **Salva layout finestra**. Assegnare a questo layout il nome "Finestra di progettazione".

     Si noti che al nuovo layout viene assegnato il tasto di scelta rapida successivo nell'elenco riservato di **CTRL** + **ALT** + **1... 0**.

#### <a name="create-a-database-project-and-layout"></a>Creare un layout e un progetto di database

1. Aggiungere un nuovo progetto **Database SQL Server** alla soluzione.

2. Fare clic con il pulsante destro del mouse sul nuovo progetto in **Esplora soluzioni** e scegliere **Visualizza in Esplora oggetti**. Verrà visualizzata la finestra **Esplora oggetti di SQL Server** che consente di accedere a tabelle, viste e altri oggetti nel database. È possibile impostare la finestra come mobile o lasciarla ancorata. Regolare le altre finestre degli strumenti nel modo desiderato. Per maggior realismo è possibile aggiungere un database effettivo, ma questa operazione non è necessaria ai fini di questa procedura dettagliata.

3. Quando il layout è quello desiderato, dal menu principale scegliere **finestra**  >  **Salva layout finestra**. Assegnare a questo layout il nome "Progetto di database". Per questo progetto non è necessario creare anche un layout per la modalità di debug.

#### <a name="switch-between-the-layouts"></a>Passare da un layout a un altro

Per passare da un layout all'altra, usare i tasti di scelta rapida oppure dal menu principale scegliere **finestra**  >  **applica layout finestra**.

![Applicare menu layout di finestra](../ide/media/vs2015_applywindowlayout.png)

Dopo l'applicazione del layout dell'interfaccia utente, notare che questo viene mantenuto sia modalità di modifica che in modalità di debug.

Se in ufficio si usa una configurazione a più monitor e a casa una laptop con un solo monitor, è possibile creare layout ottimizzati per ogni computer.

> [!NOTE]
> Se si applica un layout a più monitor in un sistema a monitor singolo, le finestre mobili posizionate sul secondo monitor risulteranno nascoste dietro la finestra di Visual Studio. È possibile portare le finestre in primo piano premendo **ALT + TAB**. Se in seguito si apre Visual Studio con più monitoraggi, è possibile ripristinare le posizioni specificate applicando nuovamente il layout.

#### <a name="manage-and-roam-your-layouts"></a>Gestire o effettuare il roaming dei layout

È possibile rimuovere, rinominare o riordinare il layout personalizzato scegliendo **finestra**  >  **Gestisci layout finestra**. Se si sposta un layout, l'associazione principale viene adattata automaticamente alla nuova posizione nell'elenco. Le associazioni non possono essere modificate altrimenti, quindi è possibile archiviare un massimo di 10 layout alla volta.

![Gestire i layout delle finestre](../ide/media/managewindowlayouts.png)

Per ricordare i tasti di scelta rapida assegnati al layout, scegliere **finestra**  >  **applica layout finestra**.

Il roaming di questi layout verrà effettuato automaticamente tra le edizioni di Visual Studio, oltre che tra le istanze di Blend in computer diversi e da una qualsiasi edizione Express a una qualsiasi altra organizzazione Express. Tuttavia, i layout non vengono spostati tra Visual Studio, Blend ed Express.

## <a name="see-also"></a>Vedi anche

- [Procedura: spostarsi nell'IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)
