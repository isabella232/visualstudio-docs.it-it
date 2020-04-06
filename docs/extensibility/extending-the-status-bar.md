---
title: Estensione della barra di stato Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711546"
---
# <a name="extend-the-status-bar"></a>Estendere la barra di stato
È possibile utilizzare la barra di stato di Visual Studio nella parte inferiore dell'IDE per visualizzare informazioni.

 Quando si estende la barra di stato, è possibile visualizzare informazioni e interfaccia utente in quattro aree: l'area commenti e suggerimenti, la barra di stato, l'area di animazione e l'area della finestra di progettazione. L'area commenti e suggerimenti consente di visualizzare il testo ed evidenziare il testo visualizzato. La barra di avanzamento mostra lo stato di avanzamento incrementale per le operazioni a esecuzione breve, ad esempio il salvataggio di un file. L'area di animazione visualizza un'animazione a ciclo continuo per operazioni a esecuzione prolungata o operazioni di lunghezza indeterminata, ad esempio la compilazione di più progetti in una soluzione. E l'area di progettazione mostra il numero di riga e colonna della posizione del cursore.

 È possibile ottenere la barra <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> di stato <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> utilizzando l'interfaccia (dal servizio). Inoltre, qualsiasi oggetto si trova su una cornice di finestra può <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> registrarsi come oggetto client della barra di stato implementando l'interfaccia. Ogni volta che viene attivata una finestra, Visual `IVsStatusbarUser` Studio esegue una query sull'oggetto individuato in tale finestra per l'interfaccia. Se viene trovato, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> chiama il metodo sull'interfaccia restituita e l'oggetto può aggiornare la barra di stato dall'interno di tale metodo. Le finestre di documento, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> ad esempio, possono utilizzare il metodo per aggiornare le informazioni nell'area della finestra di progettazione quando diventano attive.

 Le procedure seguenti presuppongono che si comprende come creare un progetto VSIX e aggiungere un comando di menu personalizzato. Per informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

## <a name="modify-the-status-bar"></a>Modificare la barra di stato
 In questa procedura viene illustrato come impostare e ottenere testo, visualizzare testo statico ed evidenziare il testo visualizzato nell'area commenti e suggerimenti della barra di stato.

### <a name="read-and-write-to-the-status-bar"></a>Lettura e scrittura nella barra di stato

1. Creare un progetto VSIX denominato **TestStatusBarExtension** e aggiungere un comando di menu denominato **TestStatusBarCommand**.

2. In *TestStatusBarCommand.cs*sostituire il codice`MenuItemCallback`del metodo del gestore di comando ( ) con quanto segue:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Compilare il codice e avviare il debug.Compile the code and start debugging.

4. Aprire il menu **Strumenti** nell'istanza sperimentale di Visual Studio. Fare clic sul pulsante **Richiama TestStatusBarCommand.**

     Si dovrebbe vedere che il testo nella barra di stato ora legge **Abbiamo appena scritto alla barra di stato.** e la finestra di messaggio visualizzata ha lo stesso testo.

### <a name="update-the-progress-bar"></a>Aggiornare la barra di avanzamento

1. In questa procedura verrà illustrato come inizializzare e aggiornare l'indicatore di stato.

2. Aprire il file di `MenuItemCallback` *TestStatusBarCommand.cs* e sostituire il metodo con il codice seguente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Compilare il codice e avviare il debug.Compile the code and start debugging.

4. Aprire il menu **Strumenti** nell'istanza sperimentale di Visual Studio. Fare clic sul pulsante **Richiama TestStatusBarCommand.**

     Si dovrebbe vedere che il testo nella barra di stato ora legge Scrittura sulla barra di **stato.** Dovresti anche vedere la barra di avanzamento essere aggiornata ogni secondo per 20 secondi. Dopo di che la barra di stato e la barra di avanzamento vengono cancellati.

### <a name="display-an-animation"></a>Visualizzare un'animazione

1. La barra di stato visualizza un'animazione ciglio continuo che indica un'operazione a esecuzione prolungata (ad esempio, la compilazione di più progetti in una soluzione). Se questa animazione non viene visualizzata, assicurarsi di disporre delle**impostazioni** corrette per Le opzioni **degli strumenti:** > 

     Passare alla scheda**Generale** **opzioni** >  **degli strumenti** > e deselezionare **Regola automaticamente l'esperienza visiva in base alle prestazioni del client.** Selezionare quindi l'opzione secondaria **Abilita esperienza visiva rich client**. You should now be able to see the animation when you build the project in your experimental instance of Visual Studio.

     In questa procedura viene visualizzata l'animazione standard di Visual Studio che rappresenta la compilazione di un progetto o di una soluzione.

2. Aprire il file di `MenuItemCallback` *TestStatusBarCommand.cs* e sostituire il metodo con il codice seguente:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Compilare il codice e avviare il debug.Compile the code and start debugging.

4. Aprire il menu **Strumenti** nell'istanza sperimentale di Visual Studio e fare clic su **Richiama TestStatusBarCommand**.

     Quando viene visualizzata la finestra di messaggio, si dovrebbe vedere anche l'animazione nella barra di stato all'estrema destra. Quando si chiude la finestra di messaggio, l'animazione scompare.
