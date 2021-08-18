---
title: 'Esercitazione: Creare app UWP con Visual Studio & C #'
description: Creare un'app UWP in Visual Studio con XAML e C#
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/20/2019
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
ms.openlocfilehash: aa0dda71a18b20f5b503aeb4c09c083a76bd664d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157826"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Esercitazione: Creare la prima applicazione universal Windows Platform in Visual Studio con XAML e C&#35;

In questa introduzione all'ambiente di sviluppo integrato (IDE) di Visual Studio verrà creata una semplice app "Hello World" eseguibile in qualsiasi dispositivo Windows 10. A tale scopo, verranno usati un modello di progetto della piattaforma UWP (Universal Windows Platform), Extensible Application Markup Language (XAML) e il linguaggio di programmazione C#.

::: moniker range="vs-2017"
Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.
::: moniker-end
::: moniker range="vs-2019"
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

   ![Modello di progetto universale di Windows nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Se non viene visualizzato il modello di progetto **App vuota (Windows universale)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**.<br><br>![Fare clic sul collegamento Apri il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** e scegliere **Modifica**.<br><br>![Carico di lavoro Sviluppo di app per la piattaforma UWP (Universal Windows Platform) nel programma di installazione di Visual Studio](media/uwp-dev-workload.png)

1. Nella finestra di dialogo **Nuovo progetto della piattaforma UWP (Universal Windows Platform)** accettare le impostazioni predefinite per **Versione di destinazione** e **Versione minima**.

   ![Nella finestra di dialogo Nuovo progetto della piattaforma UWP (Universal Windows Platform) accettare le impostazioni predefinite per Versione di destinazione e Versione minima](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Aprire Visual Studio e nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella schermata **Crea un nuovo progetto** immettere *Windows universale* nella casella di ricerca, scegliere il modello C# per **App vuota (Windows universale)** e quindi scegliere **Avanti**.

   ![Screenshot della schermata Crea un nuovo progetto](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Se il modello di progetto **App vuota (Windows universale)** non viene visualizzato, fare clic sul collegamento **Installa altri strumenti e funzionalità**.<br><br>![Fare clic sul collegamento Installa altri strumenti e funzionalità](media/vs-2019/uwp-not-finding.png)<br><br>Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo di app per la piattaforma UWP (Universal Windows Platform)** e scegliere **Modifica**.<br><br>![Carico di lavoro Sviluppo di app per la piattaforma UWP (Universal Windows Platform) nel programma di installazione di Visual Studio](media/uwp-dev-workload.png)

1. Assegnare al progetto un nome, _HelloWorld,_ e scegliere **Crea**.

   ![Configurare la schermata del progetto](media/vs-2019/uwp-configure-your-project.png)

1. Nella finestra di dialogo **Nuovo progetto della piattaforma UWP (Universal Windows Platform)** accettare le impostazioni predefinite per **Versione di destinazione** e **Versione minima**.

   ![Accettare le impostazioni predefinite Versione di destinazione e Versione minima nella finestra di dialogo Nuova Windows piattaforma Project predefinita](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Se è la prima volta che si usa Visual Studio per creare app UWP, è possibile che venga visualizzata la finestra di dialogo **Impostazioni**. Scegliere **Modalità sviluppatore** e **Sì**.<br><br>
   > ![Abilitare la modalità sviluppatore nella finestra di dialogo Impostazioni della piattaforma UWP](media/enable-developer-mode.png)<br><br>Visual Studio installa un pacchetto aggiuntivo di modalità sviluppatore per l'utente. Una volta completata l'installazione del pacchetto, chiudere la finestra di dialogo **Impostazioni**.

## <a name="create-the-application"></a>Creare l'applicazione

A questo punto è possibile iniziare a sviluppare l'app. Verrà aggiunto un pulsante, verrà aggiunta un'azione al pulsante e l'app "Hello World" verrà avviata per visualizzarne l'aspetto.

### <a name="add-a-button-to-the-design-canvas"></a>Aggiungere un pulsante all'area di progettazione

1. In **Esplora soluzioni** fare doppio clic su *MainPage.xaml* per aprire una doppia visualizzazione.

   ::: moniker range="vs-2017"
   ![Aprire MainPage.xaml da Esplora soluzioni ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Aprire MainPage.xaml da Esplora soluzioni](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Sono disponibili due riquadri: **Finestra di progettazione XAML**, che include un'area di progettazione, ed **Editor XAML**, dove è possibile aggiungere o modificare il codice.

   ![Il riquadro Finestra di progettazione XAML dell'Editor XAML](media/uwp-xaml-editor.png)

1. Scegliere **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

   ![Fare clic su Casella degli strumenti per aprire la relativa finestra a comparsa](media/uwp-toolbox.png)

   Se l'opzione **Casella degli strumenti** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, scegliere **Visualizza barra degli**  >  **strumenti**. In caso contrario, **premere** + **CTRL** + **ALT+X.**

1. Fare clic sull'icona **Blocca** per ancorare la Casella degli strumenti.

   ![Fare clic sull'icona Blocca per ancorare la finestra Casella degli strumenti](media/uwp-toolbox-autohide.png)

1. Fare clic sul controllo **Pulsante** e trascinarlo nell'area di progettazione.

   ![Fare clic sul controllo Pulsante e trascinarlo nell'area di progettazione](media/uwp-toolbox-add-button-control.png)

   Se si osserva il codice **nell'editor XAML,** si nota che il pulsante è stato aggiunto anche in questo caso:

   ![Pulsante Mostra nell'editor XAML](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Aggiungere un'etichetta al pulsante

1. **Nell'editor XAML** modificare il valore di Contenuto pulsante da "Button" a "Hello World!"

   ![Modificare il valore di Button Content in Hello World](media/uwp-change-button-text-in-xaml-code-window.png)

1. Si noti che anche il pulsante **nel finestra di progettazione XAML** cambia.

   ![Il pulsante diventa Hello World nell'area di progettazione](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Aggiungere un gestore eventi

Il termine "gestore dell'evento" sembra qualcosa di complesso, ma in realtà è solo un altro modo di indicare il codice che viene chiamato quando si verifica un evento. In questo caso, aggiunge un'azione a "Hello World!" .

1. Fare doppio clic sul pulsante nell'area di progettazione.

1. Modifica il codice del gestore eventi in *MainPage.xaml.cs*, la pagina code-behind.

   Qui le cose si fanno interessanti. Il gestore eventi predefinito ha un aspetto simile a questo:

   ![Gestore dell'evento Button_Click predefinito ](media/uwp-button-click-code.png)

   Lo modifichiamo, perché diventi simile a questo:

   ![Nuovo gestore dell'evento Button_Click asincrono ](media/uwp-add-hello-world-async-code.png)

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

#### <a name="what-did-we-just-do"></a>Che cosa abbiamo appena fatto?

Il codice usa alcune API Windows per creare un oggetto di sintesi vocale e assegnare un testo da pronunciare a tale oggetto. Per altre informazioni sull'uso di `SpeechSynthesis`, vedere <xref:System.Speech.Synthesis>.

## <a name="run-the-application"></a>Eseguire l'applicazione

::: moniker range="vs-2017"
A questo punto è possibile compilare, distribuire e avviare l'app UWP "Hello World" per verificarne l'aspetto e l'audio. Ecco come.

1. Usare il pulsante di riproduzione (include il testo **Computer locale**) per avviare l'applicazione nel computer locale.

   ![Fare clic su Computer locale per avviare ed eseguire il debug dell'app UWP](media/uwp-start-or-debug.png)

   In alternativa, è possibile scegliere **Debug** > **Avviare debug** dalla barra dei menu o premere F5 per avviare l'app.

1. Visualizzare l'app, che viene visualizzata subito dopo una schermata iniziale. L'app dovrebbe avere un aspetto simile al seguente:

   ![App UWP "Hello World"](media/uwp-hello-world-app.png)

1. Fare clic sul pulsante **Hello World**.

   Il dispositivo Windows 10 pronuncerà le parole "Hello, World!"

1. Per chiudere l'app, fare clic sul pulsante **Arresta debug** sulla barra degli strumenti. In alternativa, scegliere **Debug**  >  **Arrestare** il debug dalla barra dei menu o premere MAIUSC+F5.

::: moniker-end
::: moniker range=">=vs-2019"
A questo punto è possibile compilare, distribuire e avviare l'app UWP "Hello World" per verificarne l'aspetto e l'audio. Ecco come.

1. Usare il pulsante di riproduzione (include il testo **Computer locale**) per avviare l'applicazione nel computer locale.

   ![Fare clic su Computer locale per avviare ed eseguire il debug dell'app UWP](media/uwp-start-or-debug.png)

   In alternativa, è possibile scegliere **Debug** > **Avviare debug** dalla barra dei menu o premere F5 per avviare l'app.

1. Visualizzare l'app, che viene visualizzata subito dopo una schermata iniziale. L'app dovrebbe avere un aspetto simile al seguente:

   ![App "Hello World" UWP](media/vs-2019/uwp-hello-world-app.png)

1. Fare clic sul pulsante **Hello World**.

   Il dispositivo Windows 10 pronuncerà le parole "Hello, World!"

1. Per chiudere l'app, fare clic sul pulsante **Arresta debug** sulla barra degli strumenti. In alternativa, scegliere **Debug**  >  **Arrestare** il debug dalla barra dei menu o premere MAIUSC+F5.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Ci auguriamo che l'articolo sia stato utile per apprendere le nozioni di base su UWP e sull'IDE di Visual Studio. Per altre informazioni, passare all'esercitazione successiva:

> [!div class="nextstepaction"]
> [Creare un'interfaccia utente](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Vedi anche

- [Panoramica di UWP](/windows/uwp/get-started/universal-application-platform-guide)
- [Ottenere esempi di app UWP](/windows/uwp/get-started/get-uwp-app-samples)
