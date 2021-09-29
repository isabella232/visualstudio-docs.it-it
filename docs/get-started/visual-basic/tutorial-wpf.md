---
title: App Hello World con WPF in Visual Basic
description: Creare una semplice app Windows Desktop .NET in Visual Basic con Visual Studio usando il framework di interfaccia utente Windows Presentation Foundation (WPF).
ms.custom: vs-acquisition, seodec18, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b33078255f2a85bc9067e3c9b7a8b4e0412b8fe6
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431260"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Esercitazione: Creare un'applicazione semplice con Visual Basic

Completando questa esercitazione, si acquisirà familiarità con molti strumenti, finestre di dialogo e finestre di progettazione che è possibile usare quando si sviluppano applicazioni con Visual Studio. Si creerà un' applicazione "Hello, World", si progetterà l'interfaccia utente, si aggiungerà il codice e si eseguirà il debug degli errori, apprendendo l'uso dell'ambiente di sviluppo integrato ([IDE](visual-studio-ide.md)).

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="configure-the-ide"></a>Configurare IDE

::: moniker range="vs-2017"

Quando si apre per la prima volta, Visual Studio richiede di eseguire l'accesso. Questo passaggio è facoltativo per questa esercitazione. È possibile che venga visualizzata una finestra di dialogo in cui viene chiesto di scegliere le impostazioni di sviluppo e il tema colori. Mantenere i valori predefiniti e scegliere **Avvia Visual Studio**.

![Finestra di dialogo Selezionare le impostazioni](../media/exploreide-settings.png)

Dopo aver avviato Visual Studio, saranno visualizzati le finestre degli strumenti, i menu, le barre degli strumenti e l'area della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con **Avvio veloce**, la barra dei menu e la barra degli strumenti standard nella parte superiore. Al centro della finestra dell'applicazione si trova **Pagina iniziale**. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nello spazio in cui si trova la **pagina iniziale** . Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

![Visual Studio 2017 IDE con impostazioni generali applicate](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Quando si avvia Visual Studio, si apre la finestra iniziale. Selezionare **Continua senza codice** per aprire l'ambiente di sviluppo. Saranno visualizzate le finestre degli strumenti, i menu, barre degli strumenti e lo spazio della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione. La casella di ricerca, la barra dei menu e la barra degli strumenti standard si trovano nella parte superiore. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nell'area al centro della finestra dell'applicazione. Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

::: moniker-end

## <a name="create-the-project"></a>Creare il progetto

Quando si crea un'applicazione in Visual Studio, è innanzitutto necessario creare un progetto e una soluzione. In questo esempio verrà creato un progetto Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Creare un nuovo progetto. Sulla barra dei menu selezionare **File**  >  **Nuovo**  >  **Project**.

     ![Nella barra dei menu scegliere File, Nuovo, Progetto](../media/exploreide-filenewproject.png)

1. Nella finestra di dialogo **Nuovo progetto** selezionare la categoria **Installati** > **Visual Basic** > **Windows Desktop** e quindi selezionare il modello **App WPF (.NET Framework)**. Assegnare al progetto il nome **HelloWPFApp** e scegliere **OK**.

     ![Modello App WPF nella finestra di dialogo Nuovo progetto di Visual Studio](media/exploreide-newproject-vb.png)

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML. In **Esplora soluzioni** vengono visualizzati gli elementi indicati di seguito.

![Esplora soluzioni con i file HelloWPFApp caricati](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

1. Nella schermata **Crea un nuovo progetto** cercare "WPF", scegliere **App WPF (.NET Framework)** e quindi scegliere **Avanti**.

   ![Screenshot della finestra di dialogo "Crea un nuovo progetto" con "WPF" immesso nella casella di ricerca e il modello di progetto "App WPF (.NET Framework)" selezionato.](media/vs-2019/exploreide-newprojectvb-vs2019.png)

1. Nella schermata successiva assegnare al progetto il nome **HelloWPFApp** e scegliere **Crea**.

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML. In **Esplora soluzioni** vengono visualizzati gli elementi indicati di seguito.

![Screenshot che mostra i file nel progetto e nella soluzione HelloWPFApp nella Esplora soluzioni.](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.
 
1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Screenshot della finestra iniziale in Visual Studio 2022 con l'opzione &quot;Crea un nuovo progetto&quot; evidenziata.":::

1. Nella schermata **Crea un nuovo progetto** cercare "WPF" e  selezionare Visual Basic **nell'elenco** a discesa Tutti i linguaggi. Scegliere **App WPF (.NET Framework)** e quindi scegliere **Avanti.**

   :::image type="content" source="media/vs-2022/explore-ide-new-wpf-app-project-vb.png" alt-text="Screenshot della finestra di dialogo &quot;Crea un nuovo progetto&quot; con &quot;WPF&quot; immesso nella casella di ricerca, &quot;Visual Basic&quot; selezionato nell'elenco delle lingue e il modello di progetto &quot;App WPF (.NET Framework)&quot; evidenziato.":::

1. Nella schermata successiva assegnare al progetto il nome **HelloWPFApp** e scegliere **Crea**.

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML. In **Esplora soluzioni** vengono visualizzati gli elementi indicati di seguito.

:::image type="content" source="media/vs-2022/explore-ide-hello-wpf-app-files.png" alt-text="Screenshot che mostra i file nel progetto e nella soluzione HelloWPFApp nella Esplora soluzioni.":::

::: moniker-end

> [!NOTE]
> Per altre informazioni su XAML (eXtensible Application Markup Language), vedere la [panoramica di XAML per WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Dopo aver creato il progetto, sarà possibile personalizzarlo. Nella finestra **Proprietà** (disponibile nel menu **Visualizzazione** ) è possibile visualizzare e modificare le opzioni per elementi di progetto, controlli e altri elementi in un'applicazione.

### <a name="change-the-name-of-mainwindowxaml"></a>Cambiare il nome di MainWindow.xaml

Assegnare a MainWindow un nome più specifico. In **Esplora soluzioni** fare clic con il pulsante destro del mouse *su MainWindow.xaml* e **scegliere Rinomina.** Rinominare il file in *Greetings.xaml.*

Come passaggio facoltativo, si eviterà confusione nel modificare il titolo della finestra dell'applicazione in modo che corrisponda al nuovo nome.

1. In **Esplora soluzioni** aprire il file *Greetings.xaml* appena rinominato.

1. Nella visualizzazione XAML modificare il valore della  **proprietà Window.Title** da `Title="MainWindow"` a e salvare le `Title="Greetings"` modifiche.

## <a name="design-the-user-interface-ui"></a>Progettare l'interfaccia utente

Se la finestra di progettazione non è aperta, selezionare *Greetings.xaml* **Esplora soluzioni** e premere **MAIUSC** + **F7** per aprire la finestra di progettazione.

Verranno aggiunti tre tipi di controlli all'applicazione: un controllo <xref:System.Windows.Controls.TextBlock>, due controlli <xref:System.Windows.Controls.RadioButton> e un controllo <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Aggiungere un controllo TextBlock

::: moniker range="vs-2019"

1. Premere **CTRL** + **Q per** attivare la casella di ricerca e digitare Casella degli **strumenti**. Scegliere **Visualizza > Casella degli strumenti** dall'elenco dei risultati.

1. Nella **casella degli strumenti** espandere il nodo **Controlli WPF comuni** per visualizzare il controllo TextBlock.

   ![Screenshot che mostra la finestra Casella degli strumenti con il controllo TextBlock evidenziato nell'elenco dei controlli WPF comuni.](../media/exploreide-textblocktoolbox.png)

1. Aggiungere un controllo TextBlock all'area di progettazione scegliendo l'elemento **TextBlock** e trascinandolo nell'area di progettazione nella finestra. Centrare il controllo nella parte superiore della finestra. In Visual Studio 2019 e versioni successive è possibile usare le linee guida rosse per centrare il controllo.

La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

![Screenshot che mostra il controllo TextBlock posizionato nel modulo Greetings.](../media/exploreide-greetingswithtextblockonly.png)

Il markup XAML sarà simile all'esempio seguente:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **CTRL** + **Q per** attivare la casella di ricerca e digitare Casella degli **strumenti**. Scegliere **Visualizza > Casella degli strumenti** dall'elenco dei risultati.

1. Nella **casella degli strumenti** espandere il nodo **Controlli WPF comuni** per visualizzare il controllo TextBlock.

   :::image type="content" source="media/vs-2022/explore-ide-textblock-toolbox.png" alt-text="Screenshot che mostra la finestra Casella degli strumenti con il controllo TextBlock evidenziato nell'elenco dei controlli WPF comuni.":::

1. Aggiungere un controllo TextBlock all'area di progettazione scegliendo l'elemento **TextBlock** e trascinandolo nell'area di progettazione nella finestra. Centrare il controllo nella parte superiore della finestra. È possibile usare le linee guida per centrare il controllo.

La finestra dovrebbe essere simile all'immagine seguente:

:::image type="content" source="media/vs-2022/explore-ide-greetings-with-textblock-only.png" alt-text="Screenshot che mostra il controllo TextBlock posizionato nel modulo Greetings con le linee guida visibili.":::

Il markup XAML sarà simile all'esempio seguente:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

::: moniker-end

### <a name="customize-the-text-in-the-text-block"></a>Personalizzare il testo nel blocco di testo

1. Nella visualizzazione XAML individuare il markup di TextBlock e modificare l'attributo Text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

1. Se necessario, riallineare al centro il controllo TextBlock e salvare le modifiche premendo CTRL+S o usando la voce di menu **File**.

Si aggiungeranno quindi due [controlli RadioButton](/dotnet/framework/wpf/controls/radiobutton) al form.

### <a name="add-radio-buttons"></a>Aggiungere pulsanti di opzione

::: moniker range="vs-2019"

1. Nella **casella degli strumenti** cercare il controllo **RadioButton**.

     ![Screenshot che mostra la finestra Casella degli strumenti con il controllo RadioButton selezionato nell'elenco di controlli WPF comuni.](../media/exploreide-radiobuttontoolbox.png)

1. Aggiungere due controlli RadioButton all'area di progettazione scegliendo l'elemento **RadioButton** e trascinandolo nell'area di progettazione nella finestra. Selezionare i pulsanti e usare i tasti di direzione per spostare i pulsanti in modo che vengano visualizzati affiancati sotto il controllo TextBlock. Usare le linee guida rosse per allineare i controlli.

     La finestra dovrebbe risultare simile alla seguente:

     ![Screenshot che mostra il modulo Greetings con un controllo TextBlock e due pulsanti di opzione.](../media/exploreide-greetingswithradiobuttons.png)

1. Nella finestra **Proprietà** per il controllo RadioButton sinistro modificare la proprietà **Nome** (la proprietà nella parte superiore della finestra **Proprietà** ) in `HelloButton`.

     ![Screenshot che mostra la Esplora soluzioni Finestra Proprietà per il pulsante di opzione "HelloButton".](../media/exploreide-buttonproperties.png)

1. Nella finestra **Proprietà** per il controllo RadioButton destro modificare la proprietà **Nome** in `GoodbyeButton`, quindi salvare le modifiche.

È ora possibile aggiungere il testo visualizzato per ogni controllo RadioButton. Nella procedura seguente verrà aggiornata la proprietà **Contenuto** per un controllo RadioButton.

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella **casella degli strumenti** cercare il controllo **RadioButton**.

     :::image type="content" source="media/vs-2022/explore-ide-radiobutton-toolbox.png" alt-text="Screenshot che mostra la finestra Casella degli strumenti con il controllo RadioButton selezionato nell'elenco di controlli WPF comuni.":::

1. Aggiungere due controlli RadioButton all'area di progettazione scegliendo l'elemento **RadioButton** e trascinandolo nell'area di progettazione nella finestra. Selezionare i pulsanti e usare i tasti di direzione per spostare i pulsanti in modo che vengano visualizzati affiancati sotto il controllo TextBlock. Usare le linee guida per allineare i controlli.

     La finestra dovrebbe risultare simile alla seguente:

     :::image type="content" source="media/vs-2022/explore-ide-greetings-with-radiobuttons.png" alt-text="Screenshot che mostra il modulo Greetings con un controllo TextBlock e due pulsanti di opzione.":::

1. Nella finestra **Proprietà** per il controllo RadioButton sinistro modificare la proprietà **Nome** (la proprietà nella parte superiore della finestra **Proprietà** ) in `HelloButton`.

     :::image type="content" source="media/vs-2022/explore-ide-button-properties.png" alt-text="Screenshot che mostra la Esplora soluzioni Finestra Proprietà per il pulsante di opzione &quot;HelloButton&quot;.":::

1. Nella finestra **Proprietà** per il controllo RadioButton destro modificare la proprietà **Nome** in `GoodbyeButton`, quindi salvare le modifiche.

È ora possibile aggiungere il testo visualizzato per ogni controllo RadioButton. Nella procedura seguente verrà aggiornata la proprietà **Contenuto** per un controllo RadioButton.

::: moniker-end
### <a name="add-display-text-for-each-radio-button"></a>Aggiungere testo visualizzato per ogni pulsante di opzione

Aggiornare **l'attributo Content** per `HelloButton` e in e in `GoodbyeButton` `"Hello"` `"Goodbye"` XAML. Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Impostare un pulsante di opzione che deve essere selezionato per impostazione predefinita

In questo passaggio il pulsante di opzione HelloButton viene impostato in modo che sia selezionato per impostazione predefinita, così che uno dei due pulsanti di opzione sia sempre selezionato.

Nella visualizzazione XAML individuare il markup per HelloButton e aggiungere un attributo **IsChecked**:

```xaml
IsChecked="True"
```

L'ultimo elemento dell'interfaccia utente che verrà aggiunto è un [controllo](/dotnet/framework/wpf/controls/button) Button.

### <a name="add-the-button-control"></a>Aggiungere il controllo del pulsante

::: moniker range="vs-2019"

1. Nella **casella degli strumenti** cercare il controllo **Button** e aggiungerlo all'area di progettazione sotto i controlli RadioButton trascinandolo nel modulo nella visualizzazione Progettazione. Le linee guida consentono di centrare il controllo.

1. Nella visualizzazione XAML modificare il valore di **Contenuto** per il controllo Button da `Content="Button"` a `Content="Display"`, e salvare le modifiche.

   Il markup dovrebbe essere simile all'esempio seguente: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

   ![Screenshot che mostra il modulo Greetings con TextBlock, i pulsanti di opzione con etichetta 'Hello' e 'Goodbye' e il controllo Button con etichetta 'Display' tutti posizionati nel modulo.](../media/exploreide-greetingswithcontrollabels.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella **casella degli strumenti** cercare il controllo **Button** e aggiungerlo all'area di progettazione sotto i controlli RadioButton trascinandolo nel modulo nella visualizzazione Progettazione. Le linee guida consentono di centrare il controllo.

1. Nella visualizzazione XAML modificare il valore di **Contenuto** per il controllo Button da `Content="Button"` a `Content="Display"`, e salvare le modifiche.

   Il markup dovrebbe essere simile all'esempio seguente:

   ```xaml
   <Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>
   ```

   La finestra dovrebbe essere simile all'immagine seguente.

   :::image type="content" source="media/vs-2022/explore-ide-greetings-with-control-labels.png" alt-text="Screenshot che mostra il modulo Greetings con TextBlock, i pulsanti di opzione con etichetta 'Hello' e 'Goodbye' e il controllo Button con etichetta 'Display' tutti posizionati nel modulo.":::

::: moniker-end
### <a name="add-code-to-the-display-button"></a>Aggiungere codice al pulsante Visualizza

Quando l'applicazione è in esecuzione, si apre una finestra di messaggio se si sceglie un pulsante di opzione e si seleziona il pulsante **Visualizza**. Verranno visualizzate una finestra di messaggio per Hello e una per Goodbye. Per creare questo comportamento, è necessario aggiungere codice all'evento `Button_Click` in *Greetings.xaml.vb* o *Greetings.xaml.cs*.

1. Nell'area di progettazione fare doppio clic sul pulsante **Visualizza** .

     Viene visualizzato il file *Greetings.xaml.vb* con il cursore nell'evento `Button_Click`.

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

1. Immettere il codice seguente:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

1. Salvare l'applicazione.

## <a name="debug-and-test-the-application"></a>Eseguire il debug e il test dell'applicazione

Verrà quindi eseguito il debug dell'applicazione per rilevare eventuali errori e verificare che entrambe le finestre di messaggio vengano visualizzate correttamente. Le istruzioni seguenti indicano come compilare e avviare il debugger, ma in un secondo momento può essere utile leggere [Compilare un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) e [Debug WPF](../../debugger/debugging-wpf.md) per altre informazioni.

### <a name="find-and-fix-errors"></a>Trovare e correggere errori

In questo passaggio si troverà l'errore causato in precedenza modificando il nome del file *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Avviare il debug e trovare l'errore

::: moniker range="vs-2019"

1. Avviare il debugger premendo **F5** o selezionando **Debug**, quindi **Avvia debug**.

   Si apre la finestra **Modalità interruzione**. La finestra **Output** indica che si è verificata un'eccezione IOException: Impossibile individuare la risorsa 'mainwindow.xaml'.

   ![Screenshot che mostra la finestra "Eccezione non gestita" con un messaggio System.IO.Exception che indica che non è possibile individuare la risorsa mainwindow.xaml.](../media/exploreide-ioexception.png)

1. Arrestare il  debugger scegliendo Debug > **Arresta debug**.

Il file *MainWindow.xaml* è stato rinominato come *Greetings.xaml* all'inizio di questa esercitazione, ma il codice fa ancora riferimento a *MainWindow.xaml* come URI di avvio per l'applicazione. Di conseguenza il progetto non può essere avviato.

::: moniker-end

::: moniker range=">=vs-2022"

1. Avviare il debugger premendo **F5** o selezionando **Debug**, quindi **Avvia debug**.

   Si apre la finestra **Modalità interruzione**. La finestra **Output** indica che si è verificata un'eccezione IOException: Impossibile individuare la risorsa 'mainwindow.xaml'.

   :::image type="content" source="media/vs-2022/explore-ide-ioexception.png" alt-text="Screenshot che mostra la finestra &quot;Eccezione non gestita&quot; con un messaggio System.IO.Exception che indica che non è possibile individuare la risorsa mainwindow.xaml.":::

1. Arrestare il  debugger scegliendo Debug > **Arresta debug**.

Il file *MainWindow.xaml* è stato rinominato come *Greetings.xaml* all'inizio di questa esercitazione, ma il codice fa ancora riferimento a *MainWindow.xaml* come URI di avvio per l'applicazione. Di conseguenza il progetto non può essere avviato.

::: moniker-end

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Specificare Greetings.xaml come URI di avvio

1. In **Esplora soluzioni** aprire il file *Application.xaml*.

1. Modificare `StartupUri="MainWindow.xaml"` in e salvare le `StartupUri="Greetings.xaml"` modifiche.

Avviare nuovamente il debugger premendo **F5**. Verrà ora visualizzata la **finestra Greetings (Messaggi di** saluto) dell'applicazione.

::: moniker range="vs-2017"

![Screenshot dell'app in esecuzione](media/exploreide-wpf-running-app.png "Screenshot della finestra Greetings con i controlli TextBlock, RadioButtons e Button visibili. Il pulsante di opzione &quot;Hello&quot; è selezionato.")

::: moniker-end

::: moniker range="vs-2019"

![Screenshot dell'app in esecuzione](media/vs-2019/exploreide-wpf-running-app.png "Screenshot della finestra Greetings con i controlli TextBlock, RadioButtons e Button visibili. Il pulsante di opzione &quot;Hello&quot; è selezionato.")

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-wpf-running-app.png" alt-text="Screenshot della finestra Greetings con i controlli TextBlock, RadioButtons e Button visibili. Il pulsante di opzione &quot;Hello&quot; è selezionato.":::

::: moniker-end

Chiudere la finestra dell'applicazione per arrestare il debug.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

Aggiungendo alcuni punti di interruzione, è possibile testare il codice durante il debug. È possibile aggiungere punti di interruzione scegliendo Debug Attiva/Disattiva punto di interruzione facendo clic sul margine sinistro dell'editor accanto alla riga di codice in cui si vuole inserire l'interruzione oppure premendo  >   **F9.**

#### <a name="add-breakpoints"></a>Aggiungere punti di interruzione

::: moniker range="vs-2019"

1. Aprire *Greetings.xaml.vb* e selezionare la riga seguente: `MessageBox.Show("Hello.")`

1. Aggiungere un punto di interruzione dal menu premendo **F9** o selezionando **Debug**, quindi **Attiva/disattiva punto di interruzione**.

   Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

1. Selezionare la riga seguente: `MessageBox.Show("Goodbye.")`.

1. Premere **F9** per aggiungere un punto di interruzione e poi premere **F5** per avviare il debug.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Hello** , quindi il pulsante **Visualizza** .

   La riga `MessageBox.Show("Hello.")` viene evidenziata in giallo. Nella parte inferiore dell'IDE, le finestre Auto, Variabili locali ed Espressioni di controllo sono ancorate insieme sul lato sinistro e le finestre Stack di chiamate, Punti di interruzione, Impostazioni eccezione, Comando, Controllo immediato e Output sono ancorate insieme sul lato destro.

   ![Screenshot che mostra una sessione di debug in Visual Studio con il codice, la diagnostica. Vengono aperte le finestre Auto e Stack di chiamate. L'esecuzione viene arrestata in corrispondenza di un punto di interruzione in Greetings.xaml.vb.](media/exploreide-debugbreakpoint.png)

1. Sulla barra dei menu scegliere **Esegui debug** > **istruzione/uscita.**

     L'applicazione riprende l'esecuzione e verrà visualizzata una finestra di messaggio con la parola "Hello&quot;.

1. Scegliere il pulsante **OK** per chiudere la finestra di messaggio.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Goodbye** , quindi il pulsante **Visualizza** .

     La riga `MessageBox.Show(&quot;Goodbye.")` viene evidenziata in giallo.

1. Scegliere **F5** per proseguire con il debug. Quando verrà visualizzata la finestra del messaggio, scegliere il pulsante **OK** per chiuderla.

1. Chiudere la finestra dell'applicazione per arrestare il debug.

1. Sulla barra dei menu scegliere **Debug Disabilita** tutti i punti > **di interruzione**.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire *Greetings.xaml.vb* e selezionare la riga seguente: `MessageBox.Show("Hello.")`

1. Aggiungere un punto di interruzione dal menu premendo **F9** o selezionando **Debug**, quindi **Attiva/disattiva punto di interruzione**.

   Accanto alla riga di codice nel margine all'estrema sinistra o nel margine sinistro della finestra dell'editor viene visualizzato un cerchio rosso.

1. Selezionare la riga seguente: `MessageBox.Show("Goodbye.")`.

1. Premere **F9** per aggiungere un punto di interruzione e poi premere **F5** per avviare il debug.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Hello** , quindi il pulsante **Visualizza** .

   La riga `MessageBox.Show("Hello.")` viene evidenziata in giallo. Nella parte inferiore dell'IDE, le finestre Auto, Variabili locali ed Espressioni di controllo sono ancorate insieme sul lato sinistro e le finestre Stack di chiamate, Punti di interruzione, Impostazioni eccezione, Comando, Controllo immediato e Output sono ancorate insieme sul lato destro.

   :::image type="content" source="media/vs-2022/explore-ide-debug-breakpoint.png" alt-text="Screenshot che mostra una sessione di debug Visual Studio codice, diagnostica. Si aprono le finestre Auto e Stack di chiamate. L'esecuzione viene arrestata in corrispondenza di un punto di interruzione in Greetings.xaml.vb.":::

1. Sulla barra dei menu scegliere **Esegui debug** > **istruzione/uscita**.

     L'applicazione riprende l'esecuzione e verrà visualizzata una finestra di messaggio con la parola "Hello".

1. Scegliere il pulsante **OK** per chiudere la finestra di messaggio.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Goodbye** , quindi il pulsante **Visualizza** .

     La riga `MessageBox.Show("Goodbye.")` viene evidenziata in giallo.

1. Scegliere **F5** per proseguire con il debug. Quando verrà visualizzata la finestra del messaggio, scegliere il pulsante **OK** per chiuderla.

1. Chiudere la finestra dell'applicazione per arrestare il debug.

1. Sulla barra dei menu scegliere **Debug Disabilita** tutti i punti > **di interruzione**.

::: moniker-end

### <a name="view-a-representation-of-the-ui-elements"></a>Visualizzare una rappresentazione degli elementi dell'interfaccia utente

Nell'app in esecuzione dovrebbe essere visualizzato un widget nella parte superiore della finestra. Si tratta di un helper di runtime che consente di accedere rapidamente ad alcune utili funzionalità di debug. Fare clic sul primo pulsante, **Vai alla struttura ad albero visuale live.** Verrà visualizzata una finestra con un albero che contiene tutti gli elementi visivi della pagina. Espandere i nodi per trovare i pulsanti aggiunti.

::: moniker range="vs-2019"

![Screenshot che mostra la finestra Albero visuale live che visualizza un albero contenente tutti gli elementi visivi per HelloWPFApp.exe.](media/vs-2019/exploreide-live-visual-tree.png)

::: moniker-end

::: moniker range=">=vs-2022&quot;

:::image type="content" source="media/vs-2022/explore-ide-live-visual-tree.png" alt-text="Screenshot che mostra la finestra Albero visuale live che visualizza un albero contenente tutti gli elementi visivi per HelloWPFApp.exe.":::

::: moniker-end
### <a name=&quot;build-a-release-version-of-the-application&quot;></a>Compilare una versione di rilascio dell'applicazione

Dopo aver verificato che tutto funzioni, sarà possibile preparare una build di versione dell'applicazione.

1. Nel menu principale selezionare **Compila** soluzione pulita per eliminare i file intermedi e i file di  >   output creati durante le compilazioni precedenti. Questa operazione non è necessaria, ma elimina l'output di compilazione di debug.

1. Modificare la configurazione della build per HelloWPFApp da **Debug** a **Release** usando il controllo a discesa sulla barra degli strumenti (attualmente è &quot;Debug").

1. Compilare la soluzione scegliendo **Compila**  >  **soluzione**.

L'esercitazione è stata completata. È possibile trovare la *.exe* creata nella directory della soluzione e del progetto (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Vedi anche

::: moniker range="vs-2017"

- [Novità di Visual Studio 2017](../../ide/whats-new-visual-studio-2017.md)
- [Suggerimenti per la produttività](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Novità di Visual Studio 2019](../../ide/whats-new-visual-studio-2019.md)
- [Suggerimenti per la produttività](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2022"

- [Novità di Visual Studio 2022](../../ide/whats-new-visual-studio-2022.md)
- [Suggerimenti per la produttività](../../ide/productivity-features.md)

::: moniker-end
