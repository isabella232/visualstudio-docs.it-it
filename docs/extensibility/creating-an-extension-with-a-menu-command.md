---
title: Creazione di un'estensione con un comando di menu | Microsoft Docs
description: Informazioni su come creare un'estensione con un comando di menu che avvia Blocco note. Creare un comando di menu e quindi modificare il gestore dei comandi di menu.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d6fe7776e331fc9918035cb9c9edc7e8cf4c8ae9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627689"
---
# <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu

Questa procedura dettagliata illustra come creare un'estensione con un comando di menu che avvia Blocco note.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nell'Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-command"></a>Creare un comando di menu

1. Creare un progetto VSIX denominato **FirstMenuCommand.** È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Project** nuovo progetto cercando "vsix".

::: moniker range="vs-2017"

2. All'apertura del progetto, aggiungere un modello di elemento di comando personalizzato **denominato FirstCommand.** Nella finestra **di Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a **Estendibilità di Visual C#**  >   e selezionare **Comando personalizzato.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *FirstCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. All'apertura del progetto, aggiungere un modello di elemento di comando personalizzato **denominato FirstCommand.** Nella finestra **di Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a **Estendibilità** di Visual C# e selezionare  >   **Comando**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *FirstCommand.cs*.

::: moniker-end

3. Compilare il progetto e avviare il debug.

    Viene visualizzata l'istanza Visual Studio sperimentale. Per altre informazioni sull'istanza sperimentale, vedere [Istanza sperimentale.](../extensibility/the-experimental-instance.md)

::: moniker range="vs-2017"

4. Nell'istanza sperimentale aprire la **finestra Tools** Extensions and  >  **Updates (Estensioni e** aggiornamenti degli strumenti). L'estensione **FirstMenuCommand** dovrebbe essere visualizzata qui. Se si apre **Estensioni e aggiornamenti nell'istanza** di Visual Studio, non verrà visualizzato **FirstMenuCommand**.

::: moniker-end

::: moniker range=">=vs-2019"

4. Nell'istanza sperimentale aprire la **finestra**  >  **Estensioni Gestisci** estensioni. L'estensione **FirstMenuCommand** dovrebbe essere visualizzata qui. Se si apre **Gestisci estensioni nell'istanza** di Visual Studio, non verrà visualizzato **FirstMenuCommand**.

::: moniker-end

Passare ora al menu **Strumenti nell'istanza** sperimentale. Dovrebbe essere visualizzato **il comando Invoke FirstCommand.** A questo punto, il comando visualizza una finestra di messaggio che indica **FirstCommand Inside FirstMenuCommand.FirstCommand.MenuItemCallback()**. Nella sezione successiva verrà illustrato come avviare Blocco note da questo comando.

## <a name="change-the-menu-command-handler"></a>Modificare il gestore dei comandi di menu

A questo punto si aggiornerà il gestore comandi per avviare Blocco note.

1. Arrestare il debug e tornare all'istanza funzionante di Visual Studio. Aprire il file *FirstCommand.cs* e aggiungere l'istruzione using seguente:

    ```csharp
    using System.Diagnostics;
    ```

2. Trovare il costruttore FirstCommand privato. In questa posizione il comando viene collegato al servizio di comando e viene specificato il gestore comandi. Modificare il nome del gestore comandi in StartNotepad, come indicato di seguito:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Rimuovere il `Execute` metodo e aggiungere un metodo , che `StartNotepad` inizierà Blocco note:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. A questo punto provare. Quando si avvia il debug del progetto e si **fa** clic su Strumenti Richiama FirstCommand , verrà visualizzata un'istanza  >  di Blocco note visualizzata.

    È possibile usare un'istanza della <xref:System.Diagnostics.Process> classe per eseguire qualsiasi eseguibile, non solo Blocco note. Provare ad esempio `calc.exe` con .

## <a name="clean-up-the-experimental-environment"></a>Pulire l'ambiente sperimentale

Se si sviluppano più estensioni o si esplorano semplicemente i risultati con versioni diverse del codice dell'estensione, l'ambiente sperimentale potrebbe smettere di funzionare nel modo previsto. In questo caso, è necessario eseguire lo script di reimpostazione. Si chiama Reset **the Visual Studio Experimental Instance** e viene fornito come parte di Visual Studio SDK. Questo script rimuove tutti i riferimenti alle estensioni dall'ambiente sperimentale, quindi è possibile iniziare da zero.

È possibile accedere a questo script in uno dei due modi seguenti:

1. Dal desktop trovare Reset the Visual Studio Experimental Instance (Reimposta **istanza sperimentale).**

2. Eseguire il comando seguente dalla riga di comando:

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Distribuire l'estensione

Ora che l'estensione dello strumento è in esecuzione nel modo desiderato, è possibile condividerla con amici e colleghi. Questo è semplice, purché sia installato Visual Studio 2015. È necessario solo inviare loro il file *con estensione vsix* creato. Assicurarsi di compilarlo in modalità di rilascio.

È possibile trovare il file *con estensione vsix* per questa estensione nella directory bin *FirstMenuCommand.* In particolare, supponendo che sia stata compilata la configurazione release, sarà in:

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\FirstMenuCommand.vsix*

Per installare l'estensione, è necessario chiudere tutte le istanze aperte di Visual Studio, quindi fare doppio clic sul file con estensione *vsix* per visualizzare il programma di **installazione VSIX.** I file vengono copiati nella directory *%LocalAppData%\Microsoft\VisualStudio \<version> \Extensions.*

Quando il tuo amico Visual Studio di nuovo, troverà l'estensione FirstMenuCommand in **Strumenti**  >  **Estensioni e aggiornamenti.** Possono anche passare a **Estensioni e aggiornamenti** per disinstallare o disabilitare l'estensione.

## <a name="next-steps"></a>Passaggi successivi

Questa procedura dettagliata ha illustrato solo una piccola parte delle attività che è possibile eseguire con un'Visual Studio predefinita. Ecco un breve elenco di altre operazioni (ragionevolmente semplici) che è possibile eseguire con Visual Studio seguenti:

1. È possibile eseguire molte altre operazioni con un semplice comando di menu:

   1. Aggiungere un'icona personalizzata: [aggiungere icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Modificare il testo del comando di menu: [modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Aggiungere un tasto di scelta rapida a un comando: [Associare i tasti di scelta rapida alle voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Aggiungere diversi tipi di comandi, menu e barre degli strumenti: [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)

3. Aggiungere finestre degli strumenti ed estendere le finestre degli strumenti Visual Studio: [Estendere e personalizzare le finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)

4. Aggiungere IntelliSense, suggerimenti di codice e altre funzionalità agli editor di codice esistenti: [estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)

5. Aggiungere le pagine delle opzioni e delle proprietà e le impostazioni utente all'estensione: Estendere le proprietà e [la finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md) ed Estendere le impostazioni utente e le [opzioni](../extensibility/extending-user-settings-and-options.md)

   Altri tipi di estensioni richiedono un po' più di lavoro, ad esempio la creazione di un nuovo tipo di progetto (progetti[Extend),](../extensibility/extending-projects.md)la creazione di un nuovo tipo di editor (creazione di[editor](../extensibility/creating-custom-editors-and-designers.md)e finestre di progettazione personalizzati) o l'implementazione dell'estensione in una shell isolata: [Visual Studio shell isolata](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
