---
title: App Hello World con WPF in C#
description: Creare una semplice app Windows Desktop .NET in C# con Visual Studio usando il framework di interfaccia utente Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 26beadbe6963a685f10aef1db7bd8779434927d2
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419276"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Esercitazione: creare un'applicazione semplice con C\#

Completando questa esercitazione, si acquisirà familiarità con molti strumenti, finestre di dialogo e finestre di progettazione che è possibile usare quando si sviluppano applicazioni con Visual Studio. Si creerà un' applicazione "Hello, World", si progetterà l'interfaccia utente, si aggiungerà il codice e si eseguirà il debug degli errori, apprendendo l'uso dell'ambiente di sviluppo integrato ([IDE](visual-studio-ide.md)).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range="vs-2017"
Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?) per installarlo gratuitamente.
::: moniker-end
::: moniker range=">=vs-2019"

- Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
- Per questa esercitazione è possibile usare .NET Framework o .NET Core. .NET Core è il Framework più recente e moderno. .NET Core richiede Visual Studio 2019 versione 16,3 o successiva.
::: moniker-end

## <a name="configure-the-ide"></a>Configurare IDE

::: moniker range="vs-2017"

Quando si apre per la prima volta, Visual Studio richiede di eseguire l'accesso. Questo passaggio è facoltativo per questa esercitazione. È possibile che venga visualizzata una finestra di dialogo in cui viene chiesto di scegliere le impostazioni di sviluppo e il tema colori. Mantenere i valori predefiniti e scegliere **Avvia Visual Studio**.

![Finestra di dialogo Selezionare le impostazioni](../media/exploreide-settings.png)

Dopo aver avviato Visual Studio, saranno visualizzati le finestre degli strumenti, i menu, le barre degli strumenti e l'area della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con **Avvio veloce**, la barra dei menu e la barra degli strumenti standard nella parte superiore. Al centro della finestra dell'applicazione si trova **Pagina iniziale**. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nello spazio in cui si trova la **pagina iniziale** . Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

![Visual Studio 2017 IDE con impostazioni generali applicate](../media/exploreide-idewithgeneralsettings.png "Screenshot dell'IDE di Visual Studio 2017 con impostazioni generali applicate")

::: moniker-end

::: moniker range=">=vs-2019"

Quando si avvia Visual Studio, si apre la finestra iniziale. Selezionare **Continua senza codice** per aprire l'ambiente di sviluppo. Saranno visualizzate le finestre degli strumenti, i menu, barre degli strumenti e lo spazio della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con una casella di ricerca, la barra dei menu e la barra degli strumenti standard nella parte superiore. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nell'area al centro della finestra dell'applicazione. Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

::: moniker-end

## <a name="create-the-project"></a>Creare il progetto

Quando si crea un'applicazione in Visual Studio, è innanzitutto necessario creare un progetto e una soluzione. In questo esempio verrà creato un progetto Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Creare un nuovo progetto. Nella barra dei menu selezionare **file**  >  **nuovo**  >  **progetto**.

     ![Sulla barra dei menu scegliere file, nuovo, progetto](../media/exploreide-filenewproject.png "Screenshot della barra dei menu in cui è possibile scegliere file, nuovo, progetto")

1. Nella finestra di dialogo **Nuovo progetto** selezionare la categoria **Installati** > **Visual C#** > **Windows Desktop** e quindi selezionare il modello **App WPF (.NET Framework)**. Assegnare al progetto il nome **HelloWPFApp** e scegliere **OK**.

     ![Modello App WPF nella finestra di dialogo Nuovo progetto di Visual Studio](media/exploreide-newprojectcsharp.png "Screenshot del modello di applicazione WPF nella finestra di dialogo nuovo progetto")

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Crea nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../../get-started/media/vs-2019/start-window-create-new-project.png "Screenshot della finestra ' Crea nuovo progetto '")

1. Nella schermata **Crea un nuovo progetto** cercare "WPF", scegliere **app WPF (.NET Core)**, quindi fare clic su **Avanti**.

   ![Modello App WPF nella finestra di dialogo "Crea nuovo progetto"](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "Screenshot del modello di applicazione WPF nella finestra di dialogo "Crea nuovo progetto"")

   > [!NOTE]
   > È possibile trovare due modelli desktop WPF, uno per .NET Framework e un altro per .NET Core. Il modello di .NET Core è disponibile in Visual Studio 2019 versione 16,3 e successive. È possibile usarli per questa esercitazione, ma è consigliabile usare .NET Core per il nuovo sviluppo.

1. Nella schermata successiva assegnare al progetto il nome **HelloWPFApp** e scegliere **Crea**.

   ![Denominare il progetto ' HelloWPFApp '](./media/vs-2019/exploreide-nameproject.png "Screenshot della finestra in cui si rinomina il progetto")

::: moniker-end

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML.

![Progetto e soluzione WPF nell'IDE](media/exploreide-wpfproject-cs.png "Screenshot del progetto e della soluzione WPF nell'IDE")

> [!NOTE]
> Per altre informazioni su XAML (eXtensible Application Markup Language), vedere la [panoramica di XAML per WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Dopo aver creato il progetto, sarà possibile personalizzarlo. A tale scopo, scegliere **Finestra Proprietà** dal menu **Visualizza** o premere **F4**. È quindi possibile visualizzare e modificare le opzioni per elementi di progetto, controlli e altri elementi in un'applicazione.

   ![Finestra Proprietà](../media/exploreide-hellowpfappfiles.png "Screenshot della Finestra Proprietà con i nomi delle app file WPF")   

### <a name="change-the-name-of-mainwindowxaml"></a>Cambiare il nome di MainWindow.xaml

Assegnare a MainWindow un nome più specifico. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su *MainWindow. XAML* e scegliere **Rinomina**. Rinominare il file in *Greetings. XAML*.

## <a name="design-the-user-interface-ui"></a>Progettare l'interfaccia utente

Se la finestra di progettazione non è aperta, selezionare *Greetings. XAML* e premere **MAIUSC** + **F7** per aprire la finestra di progettazione.

Verranno aggiunti tre tipi di controlli all'applicazione: un controllo <xref:System.Windows.Controls.TextBlock>, due controlli <xref:System.Windows.Controls.RadioButton> e un controllo <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Aggiungere un controllo TextBlock

1. Premere **CTRL** + **Q** per attivare la casella di ricerca e digitare **casella degli strumenti**. Scegliere **Visualizza > Casella degli strumenti** dall'elenco dei risultati.

1. Nella **casella degli strumenti** espandere il nodo **Controlli WPF comuni** per visualizzare il controllo TextBlock.

     ![Casella degli strumenti con il controllo TextBlock evidenziato](../media/exploreide-textblocktoolbox.png "Screenshot della finestra casella degli strumenti con il controllo TextBlock evidenziato")

1. Aggiungere un controllo TextBlock all'area di progettazione scegliendo l'elemento **TextBlock** e trascinandolo nell'area di progettazione nella finestra. Centrare il controllo nella parte superiore della finestra. In Visual Studio 2019 e versioni successive è possibile usare le linee guida rosse per centrare il controllo.

    La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

    ![Controllo TextBlock nel modulo di messaggi di apertura](../media/exploreide-greetingswithtextblockonly.png "Screenshot del controllo TextBlock nel modulo Greetings")

   Il markup XAML sarà simile all'esempio seguente:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Personalizzare il testo nel blocco di testo

1. Nella visualizzazione XAML individuare il markup di **TextBlock** e modificare l'attributo **Text** da `TextBox` a `Select a message option and then choose the Display button.`

   Il markup XAML sarà simile all'esempio seguente:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Se si vuole, riallineare al centro il controllo TextBlock e quindi salvare le modifiche premendo **CTRL+S** o usando la voce di menu **File**.

Successivamente, verranno aggiunti due controlli [RadioButton](/dotnet/framework/wpf/controls/radiobutton) al form.

### <a name="add-radio-buttons"></a>Aggiungere pulsanti di opzione

1. Nella **casella degli strumenti** cercare il controllo **RadioButton**.

     ![Finestra Casella degli strumenti con il controllo RadioButton selezionato](../media/exploreide-radiobuttontoolbox.png "Screenshot della finestra casella degli strumenti con il controllo RadioButton selezionato")

1. Aggiungere due controlli RadioButton all'area di progettazione scegliendo l'elemento **RadioButton** e trascinandolo nell'area di progettazione nella finestra. Selezionare i pulsanti e usare i tasti di direzione per spostare i pulsanti in modo che vengano visualizzati affiancati sotto il controllo TextBlock. Usare le linee guida rosse per allineare i controlli.

   La finestra dovrebbe risultare simile alla seguente:

   ![Modulo di messaggi di apertura con TextBlock e due pulsanti di opzione](../media/exploreide-greetingswithradiobuttons.png "Screenshot del modulo Greetings con TextBlock e due pulsanti di opzione")

1. Nella finestra **Proprietà** per il controllo RadioButton sinistro modificare la proprietà **Nome** (la proprietà nella parte superiore della finestra **Proprietà** ) in `HelloButton`.

    ![Finestra delle proprietà di RadioButton](../media/exploreide-buttonproperties.png "Screenshot della finestra delle proprietà di RadioButton")

1. Nella finestra **Proprietà** per il controllo RadioButton destro modificare la proprietà **Nome** in `GoodbyeButton`, quindi salvare le modifiche.

È ora possibile aggiungere il testo visualizzato per ogni controllo RadioButton. Nella procedura seguente verrà aggiornata la proprietà **Contenuto** per un controllo RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Aggiungere testo visualizzato per ogni pulsante di opzione

1. Aggiornare l'attributo **Content** per `HelloButton` e `GoodbyeButton` a `"Hello"` e `"Goodbye"` in XAML. Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Impostare un pulsante di opzione che deve essere selezionato per impostazione predefinita

In questo passaggio il pulsante di opzione HelloButton viene impostato in modo che sia selezionato per impostazione predefinita, così che uno dei due pulsanti di opzione sia sempre selezionato.

1. Nella visualizzazione XAML individuare il markup per HelloButton.

1. Aggiungere un attributo **IsChecked** e impostarlo su **True**. In particolare, aggiungere `IsChecked="True"`.

   Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

L'elemento finale dell'interfaccia utente da aggiungere è un controllo [Button](/dotnet/framework/wpf/controls/button) .

### <a name="add-the-button-control"></a>Aggiungere il controllo del pulsante

1. Nella **casella degli strumenti** cercare il controllo **Button** e aggiungerlo all'area di progettazione sotto i controlli RadioButton trascinandolo nel modulo nella visualizzazione Progettazione. Se si usa Visual Studio 2019 o versione successiva, una linea rossa consente di centrare il controllo.

1. Nella visualizzazione XAML modificare il valore di **Contenuto** per il controllo Button da `Content="Button"` a `Content="Display"`, e salvare le modifiche.

     La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

     ![Modulo Greetings con etichette del controllo](media/exploreide-greetingswithcontrollabels-cs.png "Screenshot del modulo Greetings con le etichette dei controlli")

   Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Aggiungere codice al pulsante Visualizza

Quando l'applicazione è in esecuzione, si apre una finestra di messaggio se si sceglie un pulsante di opzione e si seleziona il pulsante **Visualizza**. Verranno visualizzate una finestra di messaggio per Hello e una per Goodbye. Per creare questo comportamento, è necessario aggiungere codice all'evento `Button_Click` in *Greetings.xaml.cs*.

1. Nell'area di progettazione fare doppio clic sul pulsante **Visualizza** .

     Viene visualizzato il file *Greetings.xaml.cs* con il cursore nell'evento `Button_Click`.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Immettere il codice seguente:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Salvare l'applicazione.

## <a name="debug-and-test-the-application"></a>Eseguire il debug e il test dell'applicazione

Verrà quindi eseguito il debug dell'applicazione per rilevare eventuali errori e verificare che entrambe le finestre di messaggio vengano visualizzate correttamente. Le istruzioni seguenti indicano come compilare e avviare il debugger, ma in un secondo momento può essere utile leggere [Compilare un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) e [Debug WPF](../../debugger/debugging-wpf.md) per altre informazioni.

### <a name="find-and-fix-errors"></a>Trovare e correggere errori

In questo passaggio si noterà l'errore che è stato causato in precedenza cambiando il nome del file *MainWindow. XAML* .

#### <a name="start-debugging-and-find-the-error"></a>Avviare il debug e trovare l'errore

1. Avviare il debugger premendo **F5** o selezionando **Debug**, quindi **Avvia debug**.

   Si apre la finestra **Modalità interruzione**. La finestra **Output** indica che si è verificata un'eccezione IOException: Impossibile individuare la risorsa 'mainwindow.xaml'.

   ![Messaggio IOException](../media/exploreide-ioexception.png "Screenshot del messaggio IOException")

1. Arrestare il debugger scegliendo **debug**  >  **Interrompi debug**.

Il file *MainWindow.xaml* è stato rinominato come *Greetings.xaml* all'inizio di questa esercitazione, ma il codice fa ancora riferimento a *MainWindow.xaml* come URI di avvio per l'applicazione. Di conseguenza il progetto non può essere avviato.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Specificare Greetings.xaml come URI di avvio

1. In **Esplora soluzioni** aprire il file *App.xaml*.

1. Modificare `StartupUri="MainWindow.xaml"` in `StartupUri="Greetings.xaml"`, quindi salvare le modifiche.

Avviare nuovamente il debugger premendo **F5**. Viene visualizzata la finestra **Greetings** dell'applicazione.

::: moniker range="vs-2017"
![Screenshot dell'app in esecuzione](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Screenshot dell'app in esecuzione](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Chiudere la finestra dell'applicazione per arrestare il debug.

### <a name="debug-with-breakpoints"></a>Eseguire il debug con punti di interruzione

Aggiungendo alcuni punti di interruzione, è possibile testare il codice durante il debug. È possibile aggiungere punti di interruzione scegliendo **debug**imposta  >  **/Rimuovi**punto di interruzione facendo clic sul margine sinistro dell'editor accanto alla riga di codice in cui si desidera che si verifichi l'interruzione oppure premendo **F9**.

#### <a name="add-breakpoints"></a>Aggiungere punti di interruzione

1. Aprire *Greetings.XAML.cs*e selezionare la riga seguente:`MessageBox.Show("Hello.")`

1. Aggiungere un punto di interruzione dal menu selezionando **Debug**, quindi **Imposta/Rimuovi punto di interruzione**.

     Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

1. Selezionare la riga seguente: `MessageBox.Show("Goodbye.")`.

1. Premere **F9** per aggiungere un punto di interruzione e poi premere **F5** per avviare il debug.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Hello** , quindi il pulsante **Visualizza** .

    La riga `MessageBox.Show("Hello.")` viene evidenziata in giallo. Nella parte inferiore dell'IDE, le finestre Auto, Variabili locali ed Espressioni di controllo sono ancorate insieme sul lato sinistro e le finestre Stack di chiamate, Punti di interruzione, Impostazioni eccezione, Comando, Controllo immediato e Output sono ancorate insieme sul lato destro.

    ![Punto di interruzione nel debugger](media/exploreide-debugbreakpoint.png "Screenshot del punto di interruzione nel debugger")

1. Nella barra dei menu scegliere **debug**Esci  >  **da istruzione/uscita**.

     L'applicazione riprende l'esecuzione e verrà visualizzata una finestra di messaggio con la parola "Hello".

1. Scegliere il pulsante **OK** per chiudere la finestra di messaggio.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Goodbye** , quindi il pulsante **Visualizza** .

     La riga `MessageBox.Show("Goodbye.")` viene evidenziata in giallo.

1. Scegliere **F5** per proseguire con il debug. Quando verrà visualizzata la finestra del messaggio, scegliere il pulsante **OK** per chiuderla.

1. Chiudere la finestra dell'applicazione per arrestare il debug.

1. Sulla barra dei menu scegliere **debug**  >  **Disabilita tutti i**punti di interruzione.

### <a name="view-a-representation-of-the-ui-elements"></a>Visualizzazione di una rappresentazione degli elementi dell'interfaccia utente

Nell'app in esecuzione verrà visualizzato un widget visualizzato nella parte superiore della finestra. Si tratta di un helper di runtime che consente di accedere rapidamente ad alcune utili funzionalità di debug. Fare clic sul primo pulsante, **passare a albero elementi visivi attivi**. Verrà visualizzata una finestra con un albero che contiene tutti gli elementi visivi della pagina. Espandere i nodi per trovare i pulsanti aggiunti.

![Screenshot della finestra albero elementi visivi attivi](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Compilare una versione di rilascio dell'applicazione

Dopo aver verificato che tutto funzioni, sarà possibile preparare una build di versione dell'applicazione.

1. Nel menu principale selezionare **Compila**  >  **soluzione pulita** per eliminare i file intermedi e i file di output creati durante le compilazioni precedenti. Questa operazione non è necessaria, ma elimina l'output di compilazione di debug.

1. Modificare la configurazione di compilazione per HelloWPFApp da **debug** a **rilascio** usando il controllo a discesa sulla barra degli strumenti (viene visualizzato attualmente "debug").

1. Compilare la soluzione scegliendo **Compila**  >  **Compila soluzione**.

L'esercitazione è stata completata. È possibile trovare il file con *estensione exe* compilato nella directory della soluzione e del progetto (*. ..\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Continuare con altre esercitazioni su WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Vedi anche

- [Suggerimenti per la produttività](../../ide/productivity-features.md)
