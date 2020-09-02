---
title: Creazione di un'estensione con un comando di menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572887"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Creazione di un'estensione con un comando di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come creare un'estensione con un comando di menu che avvia il blocco note.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Creazione di un comando di menu  
  
1. Creare un progetto VSIX denominato **FirstMenuCommand**. Il modello di progetto VSIX è reperibile nella finestra di dialogo **nuovo progetto** in **Visual C#/extensibility**.  
  
2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **FirstCommand**. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi/nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in **FirstCommand.cs**.  
  
3. Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4. Nell'istanza sperimentale aprire la finestra  **strumenti/estensioni e aggiornamenti** . L'estensione **FirstMenuCommand** dovrebbe essere visualizzata qui. (Se si aprono **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstMenuCommand**).  
  
     Passare ora al menu **strumenti** nell'istanza sperimentale. Dovrebbe essere visualizzato il comando **Invoke FirstCommand** . A questo punto viene visualizzata solo una finestra di messaggio con la dicitura "FirstCommandPackage all'interno di FirstMenuCommand. FirstCommand. MenuItemCallback ()". Si vedrà come avviare effettivamente il blocco note da questo comando nella sezione successiva.  
  
## <a name="changing-the-menu-command-handler"></a>Modifica del gestore dei comandi di menu  
 A questo punto, è possibile aggiornare il gestore dei comandi per avviare il blocco note.  
  
1. Arrestare il debug e tornare all'istanza di lavoro di Visual Studio. Aprire il file FirstCommand.cs e aggiungere l'istruzione using seguente:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. Trovare il costruttore FirstCommand privato. Questo è il punto in cui il comando viene collegato al servizio di comando e viene specificato il gestore di comandi. Modificare il nome del gestore del comando in StartNotepad, come indicato di seguito:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3. Rimuovere il metodo MenuItemCallback e aggiungere un metodo StartNotepad che avvierà semplicemente il blocco note:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. È ora possibile provarlo. Quando si avvia il debug del progetto e si fa clic su **strumenti/richiama FirstCommand**, viene visualizzata un'istanza del blocco note.  
  
     È possibile utilizzare un'istanza della <xref:System.Diagnostics.Process> classe per eseguire qualsiasi eseguibile, non solo blocco note. Provare con calc.exe, ad esempio.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Pulizia dell'ambiente sperimentale  
 Se si sviluppano più estensioni o si esplorano i risultati con versioni diverse del codice dell'estensione, l'ambiente sperimentale potrebbe smettere di funzionare come dovrebbe. In questo caso, è necessario eseguire lo script di reimpostazione. Viene chiamato **Reimposta l'istanza sperimentale di Visual studio 2015**e viene fornito come parte di Visual Studio SDK. Questo script rimuove tutti i riferimenti alle estensioni dall'ambiente sperimentale, quindi è possibile iniziare da zero.  
  
 È possibile ottenere questo script in uno dei due modi seguenti:  
  
1. Dal desktop, trovare **Reimposta l'istanza sperimentale di Visual Studio 2015**.  
  
2. Eseguire il comando seguente dalla riga di comando:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Distribuzione dell'estensione  
 Ora che l'estensione dello strumento è in esecuzione nel modo desiderato, è necessario condividerla con gli amici e i colleghi. Questa operazione è facile, purché Visual Studio 2015 sia installato. È sufficiente inviare il file con estensione VSIX compilato. Assicurarsi di compilarlo in modalità di rilascio.  
  
 È possibile trovare il file VSIX per questa estensione nella directory bin FirstMenuCommand. In particolare, supponendo che sia stata compilata la configurazione di rilascio, sarà in:  
  
 **\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand. vsix**  
  
 Per installare l'estensione, l'amico deve chiudere tutte le istanze aperte di Visual Studio, quindi fare doppio clic sul file VSIX, che Visualizza il programma di **installazione VSIX**. I file vengono copiati nella directory **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions**  
  
 Quando il tuo amico Visualizza di nuovo Visual Studio, troverà l'estensione FirstMenuCommand in **strumenti/estensioni e aggiornamenti**. Può anche passare a **estensioni e aggiornamenti** per disinstallare o disabilitare l'estensione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 In questa procedura dettagliata è stata illustrata solo una piccola parte delle operazioni che è possibile eseguire con un'estensione di Visual Studio. Di seguito è riportato un breve elenco di altre (ragionevolmente semplici) operazioni che è possibile eseguire con le estensioni di Visual Studio:  
  
1. È possibile eseguire molte altre operazioni con un semplice comando di menu:  
  
   1. Aggiungere un'icona personalizzata: [aggiunta di icone ai comandi di menu](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. Modificare il testo del comando di menu: [modifica del testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. Aggiungere un menu di scelta rapida a un comando: [associazione di tasti di scelta rapida alle voci di menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Aggiungere diversi tipi di comandi, menu e barre degli strumenti: [estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)  
  
3. Aggiungere finestre degli strumenti ed estendere le finestre degli strumenti di Visual Studio predefinite: [estensione e personalizzazione delle finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Aggiungere IntelliSense, suggerimenti del codice e altre funzionalità agli editor del codice esistenti: [estensione dell'editor e dei servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Aggiungere le opzioni e le pagine delle proprietà e le impostazioni utente all'estensione: [estensione delle proprietà e della finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md) ed [estensione delle impostazioni utente e delle opzioni](../extensibility/extending-user-settings-and-options.md)  
  
   Altri tipi di estensioni richiedono un minor numero di operazioni, ad esempio la creazione di un nuovo tipo di progetto ([estensione dei progetti](../extensibility/extending-projects.md)), la creazione di un nuovo tipo di Editor ([creazione di editor e finestre di progettazione personalizzati](../extensibility/creating-custom-editors-and-designers.md)) o l'implementazione dell'estensione in una shell isolata: [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)
