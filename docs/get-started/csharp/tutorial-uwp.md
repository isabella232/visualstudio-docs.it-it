---
title: 'Esercitazione: Creare app UWP con Visual Studio & C #'
description: Creare un'app UWP in Visual Studio con XAML e C#
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 97108256dbfbd35e52f22a88eab16cdff9a6b825
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128424880"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Esercitazione: Creare la prima applicazione Universal Windows Platform in Visual Studio con XAML e C&#35;

In questa introduzione all'ambiente di sviluppo integrato (IDE) di Visual Studio verrà creata una semplice app "Hello World" eseguibile in qualsiasi dispositivo Windows 10. A tale scopo, verranno usati un modello di progetto della piattaforma UWP (Universal Windows Platform), Extensible Application Markup Language (XAML) e il linguaggio di programmazione C#.

::: moniker range="vs-2017"
Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.
::: moniker-end
::: moniker range=">=vs-2019"
Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.
::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa è necessario creare un progetto della piattaforma UWP (Universal Windows Platform). Il tipo di progetto include fin dall'inizio tutti i file di modello necessari.

::: moniker range="vs-2017"
1. Aprire Visual Studio.

1. Nella barra dei menu superiore scegliere **File** > **nuovo** > **Project**.

1. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e scegliere **Universale di Windows**. Nel riquadro centrale scegliere **App vuota (Windows universale)**. Assegnare al progetto il nome *HelloWorld* e scegliere **OK**.

   > [!NOTE]
   > Assicurarsi che il percorso del progetto di origine si trova in un'unità formattata **CON NTFS (New Technology File System),** ad esempio l'unità del sistema operativo. In caso contrario, potrebbero verificarsi problemi durante la compilazione e l'esecuzione del progetto. 

   ![Screenshot che mostra il Windows di progetto Universale nella finestra di dialogo Nuovo Project nell'IDE Visual Studio.](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Se non viene visualizzato il modello di progetto **App vuota (Windows universale)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**.<br><br>![Screenshot che mostra il collegamento a "Apri Programma di installazione di Visual Studio" nella finestra di dialogo Project nuova pagina.](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** e scegliere **Modifica**.<br><br>![Screenshot del Programma di installazione di Visual Studio che mostra il carico di lavoro sviluppo della piattaforma Windows universali.](media/uwp-dev-workload.png)

1. Nella finestra di dialogo **Nuovo progetto della piattaforma UWP (Universal Windows Platform)** accettare le impostazioni predefinite per **Versione di destinazione** e **Versione minima**.

   ![Screenshot della finestra di dialogo New Universal Windows Platform Project che mostra le impostazioni predefinite Versione di destinazione e Versione minima.](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range="vs-2019"
1. Aprire Visual Studio e nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella schermata **Crea un nuovo progetto** immettere *Windows universale* nella casella di ricerca, scegliere il modello C# per **App vuota (Windows universale)** e quindi scegliere **Avanti**.

   ![Screenshot della finestra di dialogo "Crea un nuovo progetto" con le "finestre universali" immesse nella casella di ricerca e il modello di progetto "App vuota (universal Windows)" evidenziato.](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Se il modello di progetto **App vuota (Windows universale)** non viene visualizzato, fare clic sul collegamento **Installa altri strumenti e funzionalità**.<br><br>![Screenshot della finestra Crea un nuovo progetto che mostra il collegamento "Installa altri strumenti e funzionalità".](media/vs-2019/uwp-not-finding.png)<br><br>Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** e scegliere **Modifica**.<br><br>![Screenshot del Programma di installazione di Visual Studio che mostra il carico di lavoro sviluppo della piattaforma Windows universali.](media/uwp-dev-workload.png)

1. Assegnare al progetto un nome, _HelloWorld,_ e scegliere **Crea**.

   ![Screenshot della finestra di dialogo "Configura il nuovo progetto" con "HelloWorld" immesso nel campo Project nome.](media/vs-2019/uwp-configure-your-project.png)

1. Nella finestra di dialogo **Nuovo progetto della piattaforma UWP (Universal Windows Platform)** accettare le impostazioni predefinite per **Versione di destinazione** e **Versione minima**.

   ![Screenshot della finestra di dialogo New Universal Windows Platform Project che mostra le impostazioni predefinite Versione di destinazione e Versione minima.](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2022"
1. Aprire Visual Studio e nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella schermata **Crea un nuovo progetto** immettere *Windows universale* nella casella di ricerca, scegliere il modello C# per **App vuota (Windows universale)** e quindi scegliere **Avanti**.

   :::image type="content" source="media/vs-2022/uwp-create-new-project.png" alt-text="Screenshot della finestra di dialogo &quot;Crea un nuovo progetto&quot; con &quot;Universal Windows&quot; immesso nella casella di ricerca e il modello di progetto &quot;Blank App (Universal Windows)&quot; evidenziato.":::

   > [!NOTE]
   > Se il modello di progetto **App vuota (Windows universale)** non viene visualizzato, fare clic sul collegamento **Installa altri strumenti e funzionalità**.<br><br>:::image type="content" source="media/vs-2022/uwp-not-finding.png" alt-text="Screenshot della finestra Crea un nuovo progetto che mostra il collegamento &quot;Installa altri strumenti e funzionalità&quot;.":::<br><br>Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo Windows universali** e quindi selezionare **Modifica**.<br><br>:::image type="content" source="media/vs-2022/uwp-dev-workload.png" alt-text="Screenshot del Programma di installazione di Visual Studio che mostra il carico di lavoro sviluppo della piattaforma Windows universali.":::

1. Assegnare al progetto un nome, *HelloWorld,* e scegliere **Crea**.

   :::image type="content" source="media/vs-2022/uwp-configure-your-project.png" alt-text="Screenshot della finestra di dialogo &quot;Configura il nuovo progetto&quot; con &quot;HelloWorld&quot; immesso nel campo Project nome.":::

1. Nella finestra di dialogo **Nuovo progetto della piattaforma UWP (Universal Windows Platform)** accettare le impostazioni predefinite per **Versione di destinazione** e **Versione minima**.

   :::image type="content" source="media/vs-2022/new-uwp-project-target-minver-dialog.png" alt-text="Screenshot della finestra di dialogo New Universal Windows Platform Project che mostra le impostazioni predefinite Versione di destinazione e Versione minima.":::

::: moniker-end

   > [!NOTE]
   > Se è la prima volta che si usa Visual Studio per creare app UWP, è possibile che venga visualizzata la finestra di dialogo **Impostazioni**. Scegliere **Modalità sviluppatore** e **Sì**.<br><br>
   > ![Screenshot che mostra la finestra di dialogo Impostazioni della pagina UWP con l'opzione per l'abilitazione della modalità sviluppatore.](media/enable-developer-mode.png)<br><br>Visual Studio installa un pacchetto aggiuntivo di modalità sviluppatore per l'utente. Una volta completata l'installazione del pacchetto, chiudere la finestra di dialogo **Impostazioni**.

## <a name="create-the-application"></a>Creare l'applicazione

A questo punto è possibile iniziare a sviluppare l'app. Verrà aggiunto un pulsante, verrà aggiunta un'azione al pulsante e l'app "Hello World" verrà avviata per visualizzarne l'aspetto.

### <a name="add-a-button-to-the-design-canvas"></a>Aggiungere un pulsante all'area di progettazione

::: moniker range="vs-2017"

1. In **Esplora soluzioni** fare doppio clic su *MainPage.xaml* per aprire una doppia visualizzazione.

   ![Screenshot della finestra Esplora soluzioni che mostra le proprietà, i riferimenti, gli asset e i file nel progetto HelloWorld. Il file MainPage.xaml è selezionato.](media/uwp-solution-explorer-MainPage-xaml.png)

   Sono disponibili due riquadri: **Finestra di progettazione XAML**, che include un'area di progettazione, ed **Editor XAML**, dove è possibile aggiungere o modificare il codice.

   ![Screenshot che mostra MainPage.xaml aperto nell'IDE Visual Studio. Il finestra di progettazione XAML mostra un'area di progettazione vuota e il riquadro Editor XAML mostra parte del codice XAML.](media/uwp-xaml-editor.png)

1. Scegliere **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

   ![Screenshot che mostra la scheda per la finestra a comparsa "Casella degli strumenti" evidenziata sul lato sinistro del finestra di progettazione XAML riquadro attività.](media/uwp-toolbox.png)

   Se l'opzione **Casella degli strumenti** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, scegliere **Visualizza barra degli**  >  **strumenti**. In caso contrario, **premere** + **CTRL** + **ALT+X.**

1. Fare clic sull'icona **Blocca** per ancorare la Casella degli strumenti.

   ![Screenshot che mostra l'icona Aggiungi evidenziata nella barra superiore della finestra della casella degli strumenti.](media/uwp-toolbox-autohide.png)

1. Fare clic sul controllo **Pulsante** e trascinarlo nell'area di progettazione.

   ![Screenshot che mostra "Button" evidenziato nella finestra Casella degli strumenti e un controllo Button nell'area di disegno.](media/uwp-toolbox-add-button-control.png)

   Se si osserva il codice **nell'editor XAML,** si nota che il pulsante è stato aggiunto anche in questo caso:

   ![Screenshot che mostra il codice per il pulsante appena aggiunto evidenziato nell'editor XAML.](media/uwp-xaml-control-code-window.png)

::: moniker-end

::: moniker range="vs-2019"

1. In **Esplora soluzioni** fare doppio clic su *MainPage.xaml* per aprire una doppia visualizzazione.

   ![Screenshot della finestra Esplora soluzioni che mostra le proprietà, i riferimenti, gli asset e i file nel progetto HelloWorld. Il file MainPage.xaml è selezionato.](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)

   Sono disponibili due riquadri: **Finestra di progettazione XAML**, che include un'area di progettazione, ed **Editor XAML**, dove è possibile aggiungere o modificare il codice.

   ![Screenshot che mostra MainPage.xaml aperto nell'IDE Visual Studio. Il finestra di progettazione XAML mostra un'area di progettazione vuota e il riquadro Editor XAML mostra parte del codice XAML.](media/uwp-xaml-editor.png)

1. Scegliere **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

   ![Screenshot che mostra la scheda per la finestra a comparsa "Casella degli strumenti" evidenziata sul lato sinistro del finestra di progettazione XAML riquadro attività.](media/uwp-toolbox.png)

   Se l'opzione **Casella degli strumenti** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, scegliere **Visualizza barra degli**  >  **strumenti**. In caso contrario, **premere** + **CTRL** + **ALT+X.**

1. Fare clic sull'icona **Blocca** per ancorare la Casella degli strumenti.

   ![Screenshot che mostra l'icona Aggiungi evidenziata nella barra superiore della finestra della casella degli strumenti.](media/uwp-toolbox-autohide.png)

1. Fare clic sul controllo **Pulsante** e trascinarlo nell'area di progettazione.

   ![Screenshot che mostra "Button" evidenziato nella finestra Casella degli strumenti e un controllo Button nell'area di disegno.](media/uwp-toolbox-add-button-control.png)

   Se si osserva il codice **nell'editor XAML,** si nota che il pulsante è stato aggiunto anche in questo caso:

   ![Screenshot che mostra il codice per il pulsante appena aggiunto evidenziato nell'editor XAML.](media/uwp-xaml-control-code-window.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. In **Esplora soluzioni** fare doppio clic su *MainPage.xaml* per aprire una doppia visualizzazione.

   :::image type="content" source="media/vs-2022/uwp-solution-explorer-mainpage-xaml.png" alt-text="Screenshot della finestra Esplora soluzioni che mostra le proprietà, i riferimenti, gli asset e i file nel progetto HelloWorld. Il file MainPage.xaml è selezionato.":::  

   Sono disponibili due riquadri: **Finestra di progettazione XAML**, che include un'area di progettazione, ed **Editor XAML**, dove è possibile aggiungere o modificare il codice.

   :::image type="content" source="media/vs-2022/uwp-xaml-editor.png" alt-text="Screenshot che mostra MainPage.xaml aperto nell'IDE Visual Studio. Il finestra di progettazione XAML mostra un'area di progettazione vuota e il riquadro Editor XAML mostra parte del codice XAML.":::

1. Scegliere **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

   :::image type="content" source="media/vs-2022/uwp-toolbox.png" alt-text="Screenshot che mostra la scheda per la finestra a comparsa &quot;Casella degli strumenti&quot; evidenziata sul lato sinistro finestra di progettazione XAML riquadro attività.":::

   Se l'opzione **Casella degli strumenti** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, scegliere **Visualizza barra degli**  >  **strumenti**. In caso contrario, **premere** + **CTRL** + **ALT+X.**

1. Selezionare **l'icona Aggiungi** per ancorare la finestra casella degli strumenti.

   :::image type="content" source="media/vs-2022/uwp-toolbox-autohide.png" alt-text="Screenshot che mostra l'icona Aggiungi evidenziata nella barra superiore della finestra della casella degli strumenti.":::

1. Selezionare il **controllo Pulsante** e trascinarlo nell'area di disegno.

   :::image type="content" source="media/vs-2022/uwp-toolbox-add-button-control.png" alt-text="Screenshot che mostra &quot;Button&quot; evidenziato nella finestra Casella degli strumenti e un controllo Button nell'area di disegno.":::

   Se si osserva il codice **nell'editor XAML,** si nota che il pulsante è stato aggiunto anche in questo caso:

   :::image type="content" source="media/vs-2022/uwp-xaml-control-code-window.png" alt-text="Screenshot che mostra il codice per il pulsante appena aggiunto evidenziato nell'editor XAML.":::
 
::: moniker-end

### <a name="add-a-label-to-the-button"></a>Aggiungere un'etichetta al pulsante

::: moniker range="<=vs-2019"

1. **Nell'editor XAML** modificare il valore di Contenuto pulsante da "Button" a "Hello World!".

   ![Screenshot che mostra il codice XAML per Button nell'editor XAML. Il valore della proprietà Content è stato modificato in 'Hello World!'.](media/uwp-change-button-text-in-xaml-code-window.png)

1. Si noti che anche il pulsante **nel finestra di progettazione XAML** cambia.

   ![Screenshot che mostra il controllo Button nell'area di disegno del finestra di progettazione XAML. L'etichetta del pulsante è stata modificata in "Hello World!".](media/uwp-button-text-change-in-design-canvas.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. **Nell'editor XAML** modificare il valore di Contenuto pulsante da "Button" a "Hello World!".

   :::image type="content" source="media/vs-2022/uwp-change-button-text-in-xaml-code-window.png" alt-text="Screenshot che mostra il codice XAML per Button nell'editor XAML. Il valore della proprietà Content è stato modificato in 'Hello World!'.":::

1. Si noti che anche il pulsante **nel finestra di progettazione XAML** cambia.

   :::image type="content" source="media/vs-2022/uwp-button-text-change-in-design-canvas.png" alt-text="Screenshot che mostra il controllo Button nell'area di disegno del finestra di progettazione XAML. L'etichetta del pulsante è stata modificata in &quot;Hello World!&quot;.":::

::: moniker-end

### <a name="add-an-event-handler"></a>Aggiungere un gestore eventi

Il termine "gestore dell'evento" sembra qualcosa di complesso, ma in realtà è solo un altro modo di indicare il codice che viene chiamato quando si verifica un evento. In questo caso, aggiunge un'azione a "Hello World!" .

::: moniker range="vs-2019"

1. Fare doppio clic sul pulsante nell'area di progettazione.

1. Modifica il codice del gestore eventi in *MainPage.xaml.cs*, la pagina code-behind.

   Qui le cose si fanno interessanti. Il gestore eventi predefinito ha un aspetto simile a questo:

   ![Screenshot che mostra il codice C# per il gestore eventi Button_Click predefinito.](media/uwp-button-click-code.png)

   Lo modifichiamo, perché diventi simile a questo:

   ![Screenshot che mostra il codice C# per il nuovo gestore eventi Button_Click asincrono.](media/uwp-add-hello-world-async-code.png)

   Di seguito viene riportato il codice da copiare e incollare:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

::: moniker-end

::: moniker range=">=vs-2022"

1. Fare doppio clic sul pulsante nell'area di progettazione.

1. Modifica il codice del gestore eventi in *MainPage.xaml.cs*, la pagina code-behind.

   Qui le cose si fanno interessanti. Il gestore eventi predefinito ha un aspetto simile a questo:

   :::image type="content" source="media/vs-2022/uwp-button-click-code.png" alt-text="Screenshot che mostra il codice C# per il gestore eventi Button_Click predefinito.":::

   Lo modifichiamo, perché diventi simile a questo:

   :::image type="content" source="media/vs-2022/uwp-add-hello-world-async-code.png" alt-text="Screenshot che mostra il codice C# per il nuovo gestore eventi Button_Click asincrono.":::

   Di seguito viene riportato il codice da copiare e incollare:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

::: moniker-end

#### <a name="what-did-we-just-do"></a>Che cosa abbiamo appena fatto?

Il codice usa alcune API Windows per creare un oggetto di sintesi vocale e assegnare un testo da pronunciare a tale oggetto. Per altre informazioni sull'uso di `SpeechSynthesis`, vedere <xref:System.Speech.Synthesis>.

## <a name="run-the-application"></a>Eseguire l'applicazione

::: moniker range="vs-2017"
A questo punto è possibile compilare, distribuire e avviare l'app UWP "Hello World" per verificarne l'aspetto e l'audio. Ecco come.

1. Usare il pulsante di riproduzione (include il testo **Computer locale**) per avviare l'applicazione nel computer locale.

   ![Screenshot che mostra la casella di riepilogo a discesa aperta accanto al pulsante Riproduci con l'opzione "Computer locale" selezionata.](media/uwp-start-or-debug.png)

   In alternativa, è possibile scegliere **Debug** > **Avviare debug** dalla barra dei menu o premere **F5** per avviare l'app.

1. Visualizzare l'app, che viene visualizzata subito dopo una schermata iniziale. L'app dovrebbe avere un aspetto simile al seguente:

   ![Screenshot che mostra l'applicazione "Hello World" UWP in esecuzione.](media/uwp-hello-world-app.png)

1. Fare clic sul pulsante **Hello World**.

   Il dispositivo Windows 10 pronuncerà le parole "Hello, World!"

1. Per chiudere l'app, fare clic sul pulsante **Arresta debug** sulla barra degli strumenti. In alternativa, scegliere **Debug**  >  **Arrestare** il debug dalla barra dei menu o **premere MAIUSC+F5.**

::: moniker-end
::: moniker range="vs-2019"
A questo punto è possibile compilare, distribuire e avviare l'app UWP "Hello World" per verificarne l'aspetto e l'audio. Ecco come.

1. Usare il pulsante di riproduzione (include il testo **Computer locale**) per avviare l'applicazione nel computer locale.

   ![Screenshot che mostra la casella di riepilogo a discesa aperta accanto al pulsante Riproduci con l'opzione "Computer locale" selezionata.](media/uwp-start-or-debug.png)

   In alternativa, è possibile scegliere **Debug** > **Avviare debug** dalla barra dei menu o premere **F5** per avviare l'app.

1. Visualizzare l'app, che viene visualizzata subito dopo una schermata iniziale. L'app dovrebbe avere un aspetto simile al seguente:

   ![Screenshot che mostra l'applicazione "Hello World" UWP in esecuzione.](media/vs-2019/uwp-hello-world-app.png)

1. Fare clic sul pulsante **Hello World**.

   Il dispositivo Windows 10 pronuncerà le parole "Hello, World!"

1. Per chiudere l'app, fare clic sul pulsante **Arresta debug** sulla barra degli strumenti. In alternativa, scegliere **Debug**  >  **Arrestare** il debug dalla barra dei menu o **premere MAIUSC+F5.**

::: moniker-end

::: moniker range=">=vs-2022"

A questo punto è possibile compilare, distribuire e avviare l'app UWP "Hello World" per verificarne l'aspetto e l'audio. Ecco come.

1. Usare il pulsante di riproduzione (include il testo **Computer locale**) per avviare l'applicazione nel computer locale.

   :::image type="content" source="media/vs-2022/uwp-start-or-debug.png" alt-text="Screenshot che mostra la casella di riepilogo a discesa aperta accanto al pulsante Riproduci con l'opzione &quot;Computer locale&quot; selezionata.":::

   In alternativa, è possibile scegliere **Debug** > **Avviare debug** dalla barra dei menu o premere **F5** per avviare l'app.

1. Visualizzare l'app, che viene visualizzata subito dopo una schermata iniziale. L'app dovrebbe essere simile a questa immagine:

   :::image type="content" source="media/vs-2022/uwp-hello-world-app.png" alt-text="Screenshot che mostra l'applicazione &quot;Hello World&quot; UWP in esecuzione.":::

1. Selezionare il **Hello World** comando.

   Il Windows 10 dispositivo pronuncia letteralmente "Hello, World!".

1. Per chiudere l'app, selezionare il **pulsante Arresta** debug sulla barra degli strumenti. In alternativa, scegliere **Debug**  >  **Arrestare** il debug dalla barra dei menu o **premere MAIUSC+F5.**

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Ci auguriamo che l'articolo sia stato utile per apprendere le nozioni di base su UWP e sull'IDE di Visual Studio. Per altre informazioni, passare all'esercitazione successiva:

> [!div class="nextstepaction"]
> [Creare un'interfaccia utente](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Vedi anche

- [Panoramica di UWP](/windows/uwp/get-started/universal-application-platform-guide)
- [Ottenere esempi di app UWP](/windows/uwp/get-started/get-uwp-app-samples)
