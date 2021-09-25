---
title: App Hello World con WPF in C#
description: Creare una semplice app Windows Desktop .NET in C# con Visual Studio usando il framework di interfaccia utente Windows Presentation Foundation (WPF).
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7627c96851133ba14f5fd3a2b59e3ca3f4e7e567
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428563"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Esercitazione: Creare un'applicazione semplice con C\#

Completando questa esercitazione, si acquisirà familiarità con molti strumenti, finestre di dialogo e finestre di progettazione che è possibile usare quando si sviluppano applicazioni con Visual Studio. Si creerà un' applicazione "Hello, World", si progetterà l'interfaccia utente, si aggiungerà il codice e si eseguirà il debug degli errori, apprendendo l'uso dell'ambiente di sviluppo integrato ([IDE](visual-studio-ide.md)).

## <a name="prerequisites"></a>Prerequisiti

::: moniker range="vs-2017"
Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?) per installarlo gratuitamente.
::: moniker-end
::: moniker range=">=vs-2019"

- Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
- Per questa esercitazione è possibile .NET Framework o .NET Core. .NET Core è il framework più recente e moderno. .NET Core richiede Visual Studio 2019 versione 16.3 o successiva.
::: moniker-end

## <a name="configure-the-ide"></a>Configurare IDE

::: moniker range="vs-2017"

Quando si apre per la prima volta, Visual Studio richiede di eseguire l'accesso. Questo passaggio è facoltativo per questa esercitazione. È possibile che venga visualizzata una finestra di dialogo in cui viene chiesto di scegliere le impostazioni di sviluppo e il tema colori. Mantenere i valori predefiniti e scegliere **Avvia Visual Studio**.

![Finestra di dialogo Selezionare le impostazioni](../media/exploreide-settings.png)

Dopo aver avviato Visual Studio, saranno visualizzati le finestre degli strumenti, i menu, le barre degli strumenti e l'area della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con **Avvio veloce**, la barra dei menu e la barra degli strumenti standard nella parte superiore. Al centro della finestra dell'applicazione si trova **Pagina iniziale**. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nello spazio in cui si trova la **pagina iniziale** . Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

![Visual Studio 2017 IDE con l'Impostazioni generale applicata](../media/exploreide-idewithgeneralsettings.png "Screenshot dell'IDE Visual Studio 2017 con l'Impostazioni generale applicata")

::: moniker-end

::: moniker range=">=vs-2019"

Quando si avvia Visual Studio, si apre la finestra iniziale. Selezionare **Continua senza codice** per aprire l'ambiente di sviluppo. Saranno visualizzate le finestre degli strumenti, i menu, barre degli strumenti e lo spazio della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione. La casella di ricerca, la barra dei menu e la barra degli strumenti standard si trovano nella parte superiore. Quando si carica una soluzione o un progetto, gli editor e le finestre di progettazione vengono visualizzati nell'area al centro della finestra dell'applicazione. Quando si sviluppa un'applicazione, per la maggior parte del tempo si usa quest'area centrale.

::: moniker-end

## <a name="create-the-project"></a>Creare il progetto

Quando si crea un'applicazione in Visual Studio, è innanzitutto necessario creare un progetto e una soluzione. In questo esempio verrà creato un progetto Windows Presentation Foundation (WPF).

::: moniker range="vs-2017"

1. Creare un nuovo progetto. Sulla barra dei menu selezionare **File**  >  **Nuovo**  >  **Project**.

     ![Nella barra dei menu scegliere File, Nuovo, Project](../media/exploreide-filenewproject.png "Screenshot che mostra la Visual Studio dei menu in cui si sceglie File, Nuovo Project.")

1. Nella finestra di dialogo **Nuovo progetto** selezionare la categoria **Installati** > **Visual C#** > **Windows Desktop** e quindi selezionare il modello **App WPF (.NET Framework)**. Assegnare al progetto il nome **HelloWPFApp** e scegliere **OK**.

     ![Modello App WPF nella finestra di dialogo Nuovo progetto di Visual Studio](media/exploreide-newprojectcsharp.png "Screenshot del modello App WPF nella finestra di dialogo Project wpf.")

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../../get-started/media/vs-2019/start-window-create-new-project.png "Screenshot della finestra iniziale in Visual Studio 2022 con l'opzione &quot;Crea un nuovo progetto&quot; evidenziata.")

1. Nella schermata **Crea un nuovo progetto** cercare "WPF", scegliere Applicazione **WPF** e quindi **scegliere Avanti.**

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="Screenshot della finestra di dialogo &quot;Crea un nuovo progetto&quot; con &quot;WPF&quot; immesso nella casella di ricerca e il modello di progetto &quot;Applicazione WPF&quot; evidenziato.":::

1. Nella schermata successiva assegnare al progetto il nome **HelloWPFApp** e scegliere **Avanti.**

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Screenshot della finestra di dialogo &quot;Configura il nuovo progetto&quot; con &quot;HelloWPFApp&quot; immesso nel Project nome.":::

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già **selezionato .NET Core 3.1** per il framework di destinazione. In caso contrario, **selezionare .NET Core 3.1.** Scegliere quindi **Crea.**

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="Nella finestra &quot;Informazioni aggiuntive&quot; assicurarsi che sia selezionato .NET Core 3.1":::

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML.

![Progetto e soluzione WPF nell'IDE](media/exploreide-wpfproject-cs.png "Screenshot del progetto e della soluzione HelloWPFApp nell'IDE di Visual Studio con il Esplora soluzioni aperto e le visualizzazioni XAML e della finestra di progettazione di 'MainWindow.xaml' aperte in WPF Designer.")

> [!NOTE]
> Per altre informazioni su XAML (eXtensible Application Markup Language), vedere la [panoramica di XAML per WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Dopo aver creato il progetto, sarà possibile personalizzarlo. A tale scopo, scegliere **Finestra Proprietà** dal menu **Visualizza** o premere **F4**. È quindi possibile visualizzare e modificare le opzioni per elementi di progetto, controlli e altri elementi in un'applicazione.

![Finestra Proprietà](../media/exploreide-hellowpfappfiles.png "Screenshot della finestra Esplora soluzioni che mostra proprietà, riferimenti e file nell'app HelloWPF.")

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Screenshot della finestra iniziale in Visual Studio 2022 con l'opzione &quot;Crea un nuovo progetto&quot; evidenziata.":::

1. Nella schermata **Crea un nuovo progetto** cercare "WPF", scegliere Applicazione **WPF** e quindi **scegliere Avanti.**

   :::image type="content" source="media/vs-2022/explore-ide-new-project-csharp-wpf-vs-2022.png" alt-text="Screenshot della finestra di dialogo &quot;Crea un nuovo progetto&quot; con &quot;WPF&quot; immesso nella casella di ricerca e il modello di progetto &quot;Applicazione WPF&quot; evidenziato.":::

1. Nella schermata successiva assegnare al progetto il nome **HelloWPFApp** e scegliere **Avanti.**

   :::image type="content" source="media/vs-2022/explore-ide-name-project.png" alt-text="Screenshot della finestra di dialogo &quot;Configura il nuovo progetto&quot; con &quot;HelloWPFApp&quot; immesso nel Project nome.":::

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già selezionato **.NET 6.0** per il framework di destinazione. In caso contrario, selezionare **.NET 6.0.** Scegliere quindi **Crea.**

   :::image type="content" source="media/vs-2022/wpf-target-framework.png" alt-text="Nello screenshot della finestra Informazioni aggiuntive con l'opzione '.NET 6.0' selezionata nel campo Framework.":::

Visual Studio crea il progetto e la soluzione HelloWPFApp e in **Esplora soluzioni** vengono visualizzati i vari file. **WPF Designer** include una doppia visualizzazione con una visualizzazione Progettazione e una visualizzazione XAML di *MainWindow.xaml*. È possibile far scorrere la barra di divisione in modo da mostrare più o meno elementi in ciascuna visualizzazione. È possibile scegliere di visualizzare solo la visualizzazione degli elementi visivi o solo la visualizzazione XAML.

:::image type="content" source="media/vs-2022/explore-ide-wpf-project-cs.png" alt-text="Screenshot del progetto e della soluzione HelloWPFApp nell'IDE di Visual Studio con il Esplora soluzioni aperto e le visualizzazioni XAML e della finestra di progettazione di 'MainWindow.xaml' aperte in WPF Designer.":::

> [!NOTE]
> Per altre informazioni su XAML (eXtensible Application Markup Language), vedere la [panoramica di XAML per WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Dopo aver creato il progetto, sarà possibile personalizzarlo. A tale scopo, scegliere **Finestra Proprietà** dal menu **Visualizza** o premere **F4**. È quindi possibile visualizzare e modificare le opzioni per elementi di progetto, controlli e altri elementi in un'applicazione.

:::image type="content" source="media/vs-2022/explore-ide-hello-wpf-properties.png" alt-text="Screenshot del Finestra Proprietà che mostra la sezione Varie delle proprietà della soluzione per il progetto HelloWPFApp.":::

::: moniker-end

### <a name="change-the-name-of-mainwindowxaml"></a>Cambiare il nome di MainWindow.xaml

Assegnare a MainWindow un nome più specifico. In **Esplora soluzioni** fare clic con il pulsante destro del mouse *su MainWindow.xaml* e **scegliere Rinomina.** Rinominare il file in *Greetings.xaml.*

## <a name="design-the-user-interface-ui"></a>Progettare l'interfaccia utente

Se la finestra di progettazione non è aperta, *selezionare Greetings.xaml* e premere  + **MAIUSC F7** per aprire la finestra di progettazione.

Verranno aggiunti tre tipi di controlli all'applicazione: un controllo <xref:System.Windows.Controls.TextBlock>, due controlli <xref:System.Windows.Controls.RadioButton> e un controllo <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Aggiungere un controllo TextBlock

::: moniker range="vs-2019"

1. Premere **CTRL** + **Q per** attivare la casella di ricerca e digitare Casella degli **strumenti**. Scegliere **Visualizza > Casella degli strumenti** dall'elenco dei risultati.

1. Nella **casella degli strumenti** espandere il nodo **Controlli WPF comuni** per visualizzare il controllo TextBlock.

     ![Casella degli strumenti con il controllo TextBlock evidenziato](../media/exploreide-textblocktoolbox.png "Screenshot della finestra Casella degli strumenti con il controllo TextBlock selezionato nell'elenco di controlli WPF comuni.")

1. Aggiungere un controllo TextBlock all'area di progettazione scegliendo l'elemento **TextBlock** e trascinandolo nell'area di progettazione nella finestra. Centrare il controllo nella parte superiore della finestra. In Visual Studio 2019 e versioni successive è possibile usare le linee guida rosse per centrare il controllo.

    La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

    ![Controllo TextBlock nel modulo di messaggi di apertura](../media/exploreide-greetingswithtextblockonly.png "Screenshot del controllo TextBlock nell'area di progettazione del form Greetings.")

   Il markup XAML sarà simile all'esempio seguente:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **CTRL** + **Q per** attivare la casella di ricerca e digitare Casella degli **strumenti**. Scegliere **Visualizza > Casella degli strumenti** dall'elenco dei risultati.

1. Nella **casella degli strumenti** espandere il nodo **Controlli WPF comuni** per visualizzare il controllo TextBlock.

    :::image type="content" source="media/vs-2022/explore-ide-textblock-toolbox.png" alt-text="Screenshot della finestra Casella degli strumenti con il controllo TextBlock selezionato nell'elenco di controlli WPF comuni.":::

1. Aggiungere un controllo TextBlock all'area di progettazione scegliendo l'elemento **TextBlock** e trascinandolo nell'area di progettazione nella finestra. Centrare il controllo nella parte superiore della finestra. È possibile usare le linee guida per centrare il controllo.

    La finestra dovrebbe essere simile all'immagine seguente:

    :::image type="content" source="media/vs-2022/explore-ide-greetings-with-textblock-only.png" alt-text="Screenshot del controllo TextBlock nell'area di progettazione. Vengono visualizzate linee guida per il posizionamento e il ridimensionamento del controllo.":::

   Il markup XAML sarà simile all'esempio seguente:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

::: moniker-end

### <a name="customize-the-text-in-the-text-block"></a>Personalizzare il testo nel blocco di testo

1. Nella visualizzazione XAML individuare il markup di **TextBlock** e modificare l'attributo **Text** da `TextBox` a `Select a message option and then choose the Display button.`

   Il markup XAML sarà simile all'esempio seguente:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Se si vuole, riallineare al centro il controllo TextBlock e quindi salvare le modifiche premendo **CTRL+S** o usando la voce di menu **File**.

Si aggiungeranno quindi due [controlli RadioButton](/dotnet/framework/wpf/controls/radiobutton) al form.

### <a name="add-radio-buttons"></a>Aggiungere pulsanti di opzione

::: moniker range="vs-2019"

1. Nella **casella degli strumenti** cercare il controllo **RadioButton**.

     ![Finestra Casella degli strumenti con il controllo RadioButton selezionato](../media/exploreide-radiobuttontoolbox.png "Screenshot della finestra Casella degli strumenti con il controllo RadioButton selezionato nell'elenco dei controlli WPF comuni.")

1. Aggiungere due controlli RadioButton all'area di progettazione scegliendo l'elemento **RadioButton** e trascinandolo nell'area di progettazione nella finestra. Selezionare i pulsanti e usare i tasti di direzione per spostare i pulsanti in modo che vengano visualizzati affiancati sotto il controllo TextBlock. Usare le linee guida rosse per allineare i controlli.

   La finestra dovrebbe risultare simile alla seguente:

   ![Modulo di messaggi di apertura con TextBlock e due pulsanti di opzione](../media/exploreide-greetingswithradiobuttons.png "Screenshot della finestra di progettazione per Greetings.xaml, che mostra un controllo TextBlock e due controlli RadioButton posizionati nell'area di progettazione.")

1. Nella finestra **Proprietà** per il controllo RadioButton sinistro modificare la proprietà **Nome** (la proprietà nella parte superiore della finestra **Proprietà** ) in `HelloButton`.

    ![Finestra delle proprietà di RadioButton](../media/exploreide-buttonproperties.png "Screenshot dell'Finestra Proprietà per un controllo RadioButton. Il valore della proprietà Name è stato modificato in 'HelloButton'.")

1. Nella finestra **Proprietà** per il controllo RadioButton destro modificare la proprietà **Nome** in `GoodbyeButton`, quindi salvare le modifiche.

È ora possibile aggiungere il testo visualizzato per ogni controllo RadioButton. Nella procedura seguente verrà aggiornata la proprietà **Contenuto** per un controllo RadioButton.

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella **casella degli strumenti** cercare il controllo **RadioButton**.

   :::image type="content" source="media/vs-2022/explore-ide-radiobutton-toolbox.png" alt-text="Screenshot della finestra Casella degli strumenti con il controllo RadioButton selezionato nell'elenco dei controlli WPF comuni.":::

1. Aggiungere due controlli RadioButton all'area di progettazione scegliendo l'elemento **RadioButton** e trascinandolo nell'area di progettazione nella finestra. Selezionare i pulsanti e usare i tasti di direzione per spostare i pulsanti in modo che vengano visualizzati affiancati sotto il controllo TextBlock. È possibile usare le linee guida per allineare i controlli.

   La finestra dovrebbe risultare simile alla seguente:

   :::image type="content" source="media/vs-2022/explore-ide-greetings-with-radiobuttons.png" alt-text="Screenshot della finestra di progettazione per Greetings.xaml, che mostra un controllo TextBlock e due controlli RadioButton posizionati nell'area di progettazione.":::

1. Nella finestra **Proprietà** per il controllo RadioButton sinistro modificare la proprietà **Nome** (la proprietà nella parte superiore della finestra **Proprietà** ) in `HelloButton`.

   :::image type="content" source="media/vs-2022/explore-ide-button-properties.png" alt-text="Screenshot dell'Finestra Proprietà per un controllo RadioButton. Il valore della proprietà Name è stato modificato in 'HelloButton'.":::

1. Nella finestra **Proprietà** per il controllo RadioButton destro modificare la proprietà **Nome** in `GoodbyeButton`, quindi salvare le modifiche.

È ora possibile aggiungere il testo visualizzato per ogni controllo RadioButton. Nella procedura seguente verrà aggiornata la proprietà **Contenuto** per un controllo RadioButton.

::: moniker-end

### <a name="add-display-text-for-each-radio-button"></a>Aggiungere testo visualizzato per ogni pulsante di opzione

1. Aggiornare **l'attributo Content** per `HelloButton` e in e in `GoodbyeButton` `"Hello"` `"Goodbye"` XAML. Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

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

L'ultimo elemento dell'interfaccia utente che verrà aggiunto è un [controllo](/dotnet/framework/wpf/controls/button) Button.

### <a name="add-the-button-control"></a>Aggiungere il controllo del pulsante

::: moniker range="vs-2019"

1. Nella **casella degli strumenti** cercare il controllo **Button** e aggiungerlo all'area di progettazione sotto i controlli RadioButton trascinandolo nel modulo nella visualizzazione Progettazione. Se si usa il Visual Studio 2019 o versione successiva, una linea rossa consente di centrare il controllo.

1. Nella visualizzazione XAML modificare il valore di **Contenuto** per il controllo Button da `Content="Button"` a `Content="Display"`, e salvare le modifiche.

     La finestra dovrebbe essere simile a quella illustrata nella figura di seguito.

     ![Modulo Greetings con etichette del controllo](media/exploreide-greetingswithcontrollabels-cs.png "Screenshot della finestra di progettazione per Greetings.xaml che mostra un controllo TextBlock, due controlli RadioButton con etichetta &quot;Hello&quot; e &quot;Goodbye&quot; e un pulsante con etichetta &quot;Display&quot;.")

   Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella **casella degli strumenti** cercare il controllo **Button** e aggiungerlo all'area di progettazione sotto i controlli RadioButton trascinandolo nel modulo nella visualizzazione Progettazione. Le linee guida consentono di centrare il controllo.

1. Nella visualizzazione XAML modificare il valore di **Contenuto** per il controllo Button da `Content="Button"` a `Content="Display"`, e salvare le modifiche.

     La finestra dovrebbe essere simile alla schermata seguente.

     :::image type="content" source="media/vs-2022/explore-ide-greetings-with-control-labels-cs.png" alt-text="Screenshot della finestra di progettazione per Greetings.xaml che mostra un controllo TextBlock, due controlli RadioButton con etichetta &quot;Hello&quot; e &quot;Goodbye&quot; e un pulsante con etichetta &quot;Display&quot;.":::

   Il markup XAML dovrebbe avere un aspetto simile all'esempio seguente:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

::: moniker-end

### <a name="add-code-to-the-display-button"></a>Aggiungere codice al pulsante Visualizza

::: moniker range="vs-2019"

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

::: moniker-end

::: moniker range=">=vs-2022"

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

::: moniker-end

## <a name="debug-and-test-the-application"></a>Eseguire il debug e il test dell'applicazione

Verrà quindi eseguito il debug dell'applicazione per rilevare eventuali errori e verificare che entrambe le finestre di messaggio vengano visualizzate correttamente. Le istruzioni seguenti indicano come compilare e avviare il debugger, ma in un secondo momento può essere utile leggere [Compilare un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) e [Debug WPF](../../debugger/debugging-wpf.md) per altre informazioni.

### <a name="find-and-fix-errors"></a>Trovare e correggere errori

In questo passaggio si troverà l'errore causato in precedenza modificando il nome del file *MainWindow.xaml.*

#### <a name="start-debugging-and-find-the-error"></a>Avviare il debug e trovare l'errore

::: moniker range="vs-2019"

1. Avviare il debugger premendo **F5** o selezionando **Debug**, quindi **Avvia debug**.

   Si apre la finestra **Modalità interruzione**. La finestra **Output** indica che si è verificata un'eccezione IOException: Impossibile individuare la risorsa 'mainwindow.xaml'.

   ![Messaggio IOException](../media/exploreide-ioexception.png "Screenshot della finestra Output che mostra un'eccezione System.IO.IOException con il messaggio &quot;Impossibile individuare la risorsa mainwindow.xaml&quot;.")

1. Arrestare il  debugger scegliendo Debug > **Arresta debug**.

Il file *MainWindow.xaml* è stato rinominato come *Greetings.xaml* all'inizio di questa esercitazione, ma il codice fa ancora riferimento a *MainWindow.xaml* come URI di avvio per l'applicazione. Di conseguenza il progetto non può essere avviato.

::: moniker-end

::: moniker range=">=vs-2022"

1. Avviare il debugger premendo **F5** o selezionando **Debug**, quindi **Avvia debug**.

   Si apre la finestra **Modalità interruzione**. La finestra **Output** indica che si è verificata un'eccezione IOException: Impossibile individuare la risorsa 'mainwindow.xaml'.

   :::image type="content" source="media/vs-2022/explore-ide-ioexception.png" alt-text="Screenshot della finestra Output che mostra un'eccezione System.IO.IOException con il messaggio &quot;Impossibile individuare la risorsa mainwindow.xaml&quot;.":::

1. Arrestare il  debugger scegliendo Debug > **Arresta debug**.

Il file *MainWindow.xaml* è stato rinominato come *Greetings.xaml* all'inizio di questa esercitazione, ma il codice fa ancora riferimento a *MainWindow.xaml* come URI di avvio per l'applicazione. Di conseguenza il progetto non può essere avviato.

::: moniker-end
#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Specificare Greetings.xaml come URI di avvio

1. In **Esplora soluzioni** aprire il file *App.xaml*.

1. Modificare `StartupUri="MainWindow.xaml"` in e salvare le `StartupUri="Greetings.xaml"` modifiche.

Come passaggio facoltativo, si eviterà confusione nel modificare il titolo della finestra dell'applicazione in modo che corrisponda al nuovo nome.

1. In **Esplora soluzioni** aprire il file *Greetings.xaml* appena rinominato.

1. Modificare il valore della  **proprietà Window.Title** da `Title="MainWindow"` a e salvare le `Title="Greetings"` modifiche.

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

1. Aprire *Greetings.xaml.cs* e selezionare la riga seguente: `MessageBox.Show("Hello.")`

1. Aggiungere un punto di interruzione dal menu selezionando **Debug**, quindi **Imposta/Rimuovi punto di interruzione**.

     Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

1. Selezionare la riga seguente: `MessageBox.Show("Goodbye.")`.

1. Premere **F9** per aggiungere un punto di interruzione e poi premere **F5** per avviare il debug.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Hello** , quindi il pulsante **Visualizza** .

    La riga `MessageBox.Show("Hello.")` viene evidenziata in giallo. Nella parte inferiore dell'IDE, le finestre Auto, Variabili locali ed Espressioni di controllo sono ancorate insieme sul lato sinistro e le finestre Stack di chiamate, Punti di interruzione, Impostazioni eccezione, Comando, Controllo immediato e Output sono ancorate insieme sul lato destro.

    ![Punto di interruzione nel debugger](media/exploreide-debugbreakpoint.png "Screenshot di una sessione di debug in Visual Studio. La finestra del codice per Greetings.xaml.cs mostra l'esecuzione interrotta in corrispondenza di un punto di interruzione con una riga evidenziata in giallo.")

1. Sulla barra dei menu scegliere **Esegui debug** > **istruzione/uscita.**

     L'applicazione riprende l'esecuzione e verrà visualizzata una finestra di messaggio con la parola "Hello".

1. Scegliere il pulsante **OK** per chiudere la finestra di messaggio.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Goodbye** , quindi il pulsante **Visualizza** .

     La riga `MessageBox.Show("Goodbye.")` viene evidenziata in giallo.

1. Scegliere **F5** per proseguire con il debug. Quando verrà visualizzata la finestra del messaggio, scegliere il pulsante **OK** per chiuderla.

1. Chiudere la finestra dell'applicazione per arrestare il debug.

1. Sulla barra dei menu scegliere Debug **Disabilita** > **tutti i punti di interruzione**.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire *Greetings.xaml.cs* e selezionare la riga seguente: `MessageBox.Show("Hello.")`

1. Aggiungere un punto di interruzione dal menu selezionando **Debug**, quindi **Imposta/Rimuovi punto di interruzione**.

     Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

1. Selezionare la riga seguente: `MessageBox.Show("Goodbye.")`.

1. Premere **F9** per aggiungere un punto di interruzione e poi premere **F5** per avviare il debug.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Hello** , quindi il pulsante **Visualizza** .
    
    La riga `MessageBox.Show("Hello.")` viene evidenziata in giallo. Nella parte inferiore dell'IDE, le finestre Auto, Variabili locali ed Espressioni di controllo sono ancorate insieme sul lato sinistro e le finestre Stack di chiamate, Punti di interruzione, Impostazioni eccezione, Comando, Controllo immediato e Output sono ancorate insieme sul lato destro.

    :::image type="content" source="media/vs-2022/explore-ide-debug-breakpoint.png" alt-text="Screenshot di una sessione di debug in Visual Studio. La finestra del codice per Greetings.xaml.cs mostra l'esecuzione interrotta in corrispondenza di un punto di interruzione con una riga evidenziata in giallo.":::

1. Sulla barra dei menu scegliere **Esegui debug** > **istruzione/uscita.**

     L'applicazione riprende l'esecuzione e verrà visualizzata una finestra di messaggio con la parola "Hello".

1. Scegliere il pulsante **OK** per chiudere la finestra di messaggio.

1. Nella finestra **Greetings** scegliere il pulsante di opzione **Goodbye** , quindi il pulsante **Visualizza** .

     La riga `MessageBox.Show("Goodbye.")` viene evidenziata in giallo.

1. Scegliere **F5** per proseguire con il debug. Quando verrà visualizzata la finestra del messaggio, scegliere il pulsante **OK** per chiuderla.

1. Chiudere la finestra dell'applicazione per arrestare il debug.

1. Sulla barra dei menu scegliere Debug **Disabilita** > **tutti i punti di interruzione**.

::: moniker-end

### <a name="view-a-representation-of-the-ui-elements"></a>Visualizzare una rappresentazione degli elementi dell'interfaccia utente

Nell'app in esecuzione dovrebbe essere visualizzato un widget nella parte superiore della finestra. Il widget è un helper di runtime che consente di accedere rapidamente ad alcune utili funzionalità di debug. Selezionare il primo pulsante, **Vai alla struttura ad albero visuale in tempo reale.** Verrà visualizzata una finestra con una struttura ad albero che contiene tutti gli elementi visivi della pagina. Espandere i nodi per trovare i pulsanti aggiunti.

::: moniker range="vs-2019"
![Screenshot della finestra Struttura ad albero visuale attiva](media/vs-2019/exploreide-live-visual-tree.png "Screenshot della finestra Struttura ad albero visuale attiva, che mostra la struttura ad albero degli elementi visivi nella pagina mentre è in esecuzione.")
::: moniker-end
::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-live-visual-tree.png" alt-text="Screenshot della finestra Struttura ad albero visuale attiva, che mostra la struttura ad albero degli elementi visivi in HelloWPFApp.exe mentre è in esecuzione.":::

::: moniker-end
### <a name="build-a-release-version-of-the-application"></a>Compilare una versione di rilascio dell'applicazione

Dopo aver verificato che tutto funzioni, sarà possibile preparare una build di versione dell'applicazione.

1. Nel menu principale selezionare **Compila** soluzione pulita per eliminare i file intermedi e i file di output creati durante le  >   compilazioni precedenti. Questo passaggio non è obbligatorio, ma elimina gli output di compilazione di debug.

1. Modificare la configurazione della build per HelloWPFApp da **Debug** a **Release** usando il controllo a discesa sulla barra degli strumenti (attualmente è "Debug").

1. Compilare la soluzione scegliendo **Compila**  >  **compila soluzione**.

L'esercitazione è stata completata. È possibile trovare il *.exe* creato nella directory della soluzione e del progetto (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Continuare con altre esercitazioni su WPF](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Vedi anche

- [Suggerimenti per la produttività](../../ide/productivity-features.md)
