---
title: Creazione di un'estensione con un comando di menu Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739554"
---
# <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menuCreate an extension with a menu command

In questa procedura dettagliata viene illustrato come creare un'estensione con un comando di menu che avvia il Blocco note.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-command"></a>Creare un comando di menu

1. Creare un progetto VSIX denominato **FirstMenuCommand**. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **FirstCommand**. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Comando personalizzato**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando *in FirstCommand.cs*.

3. Compilare il progetto e avviare il debug.

    Viene visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio appears. Per ulteriori informazioni sull'istanza sperimentale, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Nell'istanza sperimentale aprire la finestra**Estensioni e aggiornamenti** degli **strumenti.** >  Si dovrebbe vedere il **FirstMenuCommand** estensione qui. Se si **aprono estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, **FirstMenuCommand**non verrà visualizzato .

::: moniker-end

::: moniker range=">=vs-2019"

4. Nell'istanza sperimentale aprire la finestra**Gestione estensioni.** **Extensions** >  Si dovrebbe vedere il **FirstMenuCommand** estensione qui. Se si apre **Gestisci estensioni** nell'istanza di lavoro di Visual Studio, **FirstMenuCommand**non verrà visualizzato .

::: moniker-end

Ora vai al menu **Strumenti** nell'istanza sperimentale. Verrà visualizzato il comando **Invoke FirstCommand.You** should see Invoke FirstCommand command. A questo punto, il comando visualizza una finestra di messaggio che indica **FirstCommandPackage Inside FirstMenuCommand.FirstCommand.MenuItemCallback()**. Vedremo come avviare effettivamente Blocco note da questo comando nella sezione successiva.

## <a name="change-the-menu-command-handler"></a>Modificare il gestore dei comandi di menu

Ora aggiorniamo il gestore dei comandi per avviare blocco note.

1. Interrompere il debug e tornare all'istanza di lavoro di Visual Studio. Aprire il *file FirstCommand.cs* e aggiungere l'istruzione using seguente:

    ```csharp
    using System.Diagnostics;
    ```

2. Trovare il costruttore predefinito FirstCommand. Questo è dove il comando è collegato al servizio di comando e il gestore del comando è specificato. Modificare il nome del gestore comandi in StartNotepad, come indicato di seguito:

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

3. Rimuovere `MenuItemCallback` il metodo `StartNotepad` e aggiungere un metodo, che avvierà solo il Blocco note:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Ora provalo. Quando si avvia il debug del progetto e si fa clic su **Strumenti** > **Richiama FirstCommand**, verrà visualizzata un'istanza del Blocco note.

    È possibile utilizzare un'istanza della <xref:System.Diagnostics.Process> classe per eseguire qualsiasi eseguibile, non solo il Blocco note. Provalo `calc.exe`con , per esempio.

## <a name="clean-up-the-experimental-environment"></a>Pulire l'ambiente sperimentale

Se si sviluppano più estensioni o semplicemente si esplorano i risultati con versioni diverse del codice di estensione, l'ambiente sperimentale potrebbe smettere di funzionare come dovrebbe. In questo caso, è necessario eseguire lo script di reimpostazione. Si chiama **Reimpostare l'istanza sperimentale**di Visual Studio e viene fornito come parte di Visual Studio SDK. Questo script rimuove tutti i riferimenti alle estensioni dall'ambiente sperimentale, in modo da poter iniziare da zero.

È possibile accedere a questo script in uno dei due modi seguenti:

1. Dal desktop, trovare **Reimposta l'istanza sperimentale**di Visual Studio .

2. Eseguire il comando seguente dalla riga di comando:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Distribuire l'estensioneDeploy your extension

Ora che hai l'estensione dello strumento in esecuzione nel modo desiderato, è il momento di pensare a condividerlo con i tuoi amici e colleghi. Questo è facile, purché abbiano installato Visual Studio 2015. Tutto quello che devi fare è inviare loro il file *.vsix* che hai creato. (Assicurarsi di compilarlo in modalità di rilascio.)

È possibile trovare il file *VSIX* per questa estensione nella directory bin *FirstMenuCommand.* In particolare, supponendo che sia stata compilata la configurazione di rilascio, sarà in:Specifically, assuming you have built the Release configuration, it will be in:

*\<directory di codice> , FirstMenuCommand , FirstMenuCommand , bin , Release , FirstMenuCommand.vsix*

Per installare l'estensione, l'amico deve chiudere tutte le istanze aperte di Visual Studio, quindi fare doppio clic sul file *VSIX,* che visualizza il **programma di installazione VSIX**. I file vengono copiati nella directory *%LocalAppData>%\<*

Quando il tuo amico visualizza nuovamente Visual Studio, troverà l'estensione FirstMenuCommand in**Estensioni e aggiornamenti** **degli strumenti** > . Possono andare a **estensioni e aggiornamenti** per disinstallare o disabilitare l'estensione, troppo.

## <a name="next-steps"></a>Passaggi successivi

Questa procedura dettagliata ha illustrato solo una piccola parte di ciò che è possibile fare con un'estensione di Visual Studio.This walkthrough has shown you only a small part of what you can do with a Visual Studio extension. Ecco un breve elenco di altre operazioni (ragionevolmente semplici) che è possibile eseguire con le estensioni di Visual Studio:Here's a short list of other (reasonably easy) things you can do with Visual Studio extensions:

1. Puoi fare molte altre cose con un semplice comando di menu:

   1. Aggiungere un'icona personalizzata: [Aggiungere icone ai comandi](../extensibility/adding-icons-to-menu-commands.md) di menu

   2. Modificare il testo del comando di [menu: modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Aggiungere una scelta rapida da menu a un comando: [Associare i tasti di scelta rapida alle voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Aggiungere diversi tipi di comandi, menu e barre degli strumenti: [Estendere menu e comandi](../extensibility/extending-menus-and-commands.md)

3. Aggiungere finestre degli strumenti ed estendere le finestre degli strumenti di Visual Studio predefinite: [Estendere e personalizzare le finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)

4. Aggiungere IntelliSense, suggerimenti di codice e altre funzionalità agli editor di codice esistenti: [estendere l'editor e i servizi di linguaggioAdd](../extensibility/extending-the-editor-and-language-services.md) IntelliSense, code suggestions, and other features to existing code editors: Extend the editor and language services

5. Aggiungere opzioni e pagine delle proprietà e impostazioni utente all'estensione: [Estendere le proprietà e la finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md) e estendere le impostazioni e le opzioni [utente](../extensibility/extending-user-settings-and-options.md)

   Altri tipi di estensioni richiedono un po' più di lavoro, ad esempio la creazione di un nuovo tipo di progetto ([Estendi progetti](../extensibility/extending-projects.md)), la creazione di un nuovo tipo di editor ( Crea editor e finestre di[progettazione personalizzati](../extensibility/creating-custom-editors-and-designers.md)) o l'implementazione dell'estensione in una shell isolata: [Shell isolata di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
