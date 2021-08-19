---
title: Estensione della barra di stato | Microsoft Docs
description: Informazioni su come estendere la Visual Studio di stato nella parte inferiore dell'IDE, che visualizza informazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3b95beaf29f976b621f2b3581376bc6e84f13e46
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144678"
---
# <a name="extend-the-status-bar"></a>Estendere la barra di stato
È possibile usare la Visual Studio di stato nella parte inferiore dell'IDE per visualizzare le informazioni.

 Quando si estende la barra di stato, è possibile visualizzare le informazioni e l'interfaccia utente in quattro aree: l'area di feedback, l'indicatore di stato, l'area di animazione e l'area della finestra di progettazione. L'area di feedback consente di visualizzare il testo ed evidenziare il testo visualizzato. L'indicatore di stato mostra lo stato di avanzamento incrementale per le operazioni a esecuzione breve, ad esempio il salvataggio di un file. L'area di animazione visualizza un'animazione a ciclo continuo per operazioni a esecuzione lunga o operazioni di lunghezza non determinata, ad esempio la compilazione di più progetti in una soluzione. L'area della finestra di progettazione mostra la riga e il numero di colonna della posizione del cursore.

 È possibile ottenere la barra di stato usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> l'interfaccia (dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> servizio ). Inoltre, qualsiasi oggetto presente in una cornice di finestra può essere registrato come oggetto client della barra di stato implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> l'interfaccia . Ogni volta che viene attivata una finestra, Visual Studio esegue una query sull'oggetto in tale finestra per `IVsStatusbarUser` l'interfaccia . Se viene trovato, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodo sull'interfaccia restituita e l'oggetto può aggiornare la barra di stato dall'interno di tale metodo. Le finestre dei documenti, ad esempio, possono usare il metodo per aggiornare le informazioni nell'area della finestra di progettazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> quando diventano attive.

 Le procedure seguenti presuppongono che si comprendi come creare un progetto VSIX e aggiungere un comando di menu personalizzato. Per informazioni, vedere [Creare un'estensione con un comando di menu.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="modify-the-status-bar"></a>Modificare la barra di stato
 Questa procedura illustra come impostare e ottenere testo, visualizzare testo statico ed evidenziare il testo visualizzato nell'area commenti e suggerimenti della barra di stato.

### <a name="read-and-write-to-the-status-bar"></a>Leggere e scrivere nella barra di stato

1. Creare un progetto VSIX denominato **TestStatusBarExtension e** aggiungere un comando di menu **denominato TestStatusBarCommand.**

2. In *TestStatusBarCommand.cs* sostituire il codice del metodo del gestore comandi ( `MenuItemCallback` ) con il codice seguente:

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

3. Compilare il codice e avviare il debug.

4. Aprire il menu **Strumenti** nell'istanza sperimentale di Visual Studio. Fare clic sul pulsante Invoke TestStatusBarCommand ( Richiama **TestStatusBarCommand).**

     Si dovrebbe vedere che il testo nella barra di stato ora è **We just wrote to the status bar (Abbiamo appena scritto sulla barra di stato).** e la finestra di messaggio visualizzata ha lo stesso testo.

### <a name="update-the-progress-bar"></a>Aggiornare l'indicatore di stato

1. In questa procedura verrà illustrato come inizializzare e aggiornare l'indicatore di stato.

2. Aprire il file *TestStatusBarCommand.cs* e sostituire il `MenuItemCallback` metodo con il codice seguente:

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

3. Compilare il codice e avviare il debug.

4. Aprire il menu **Strumenti** nell'istanza sperimentale di Visual Studio. Fare **clic sul pulsante Richiama TestStatusBarCommand.**

     Si dovrebbe vedere che il testo nella barra di stato ora legge **Scrittura nell'indicatore di stato.** Si dovrebbe anche vedere che l'indicatore di stato viene aggiornato ogni secondo per 20 secondi. Successivamente, la barra di stato e l'indicatore di stato vengono cancellati.

### <a name="display-an-animation"></a>Visualizzare un'animazione

1. La barra di stato visualizza un'animazione a ciclo continuo che indica un'operazione a esecuzione lunga ,ad esempio la compilazione di più progetti in una soluzione. Se questa animazione non viene visualizzata, assicurarsi di avere le impostazioni corrette **di**  >  **Opzioni strumenti:**

     Passare alla scheda **Opzioni strumenti** Generale e deselezionare Regola automaticamente  >    >   **l'esperienza visiva in base alle prestazioni del client.** Selezionare quindi l'opzione secondaria Enable rich client visual experience (Abilita **esperienza visiva rich client).** A questo punto dovrebbe essere possibile visualizzare l'animazione quando si compila il progetto nell'istanza sperimentale di Visual Studio.

     In questa procedura viene visualizzata l'animazione Visual Studio standard che rappresenta la compilazione di un progetto o di una soluzione.

2. Aprire il file *TestStatusBarCommand.cs* e sostituire il `MenuItemCallback` metodo con il codice seguente:

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

3. Compilare il codice e avviare il debug.

4. Aprire il menu **Strumenti** nell'istanza sperimentale di Visual Studio fare clic **su Richiama TestStatusBarCommand**.

     Quando viene visualizzata la finestra di messaggio, l'animazione dovrebbe essere visualizzata anche nella barra di stato all'estrema destra. Quando si chiude la finestra di messaggio, l'animazione scompare.
