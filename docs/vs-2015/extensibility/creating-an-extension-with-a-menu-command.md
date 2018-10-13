---
title: Creazione di un'estensione con un comando di Menu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111b20eb427f1e1e2b4d00d1d2ced33c4bd677f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174629"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Creazione di un'estensione con un comando di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare un'estensione con un comando di menu che consente di avviare Blocco note.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Creazione di un comando di Menu  
  
1.  Creare un progetto VSIX denominato **FirstMenuCommand**. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **FirstCommand**. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da **FirstCommand.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per altre informazioni sull'istanza sperimentale, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, aprire il **strumenti / estensioni e aggiornamenti** finestra. Dovrebbero vedere le **FirstMenuCommand** estensione qui. (Se si apre **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstMenuCommand**).  
  
     Procedere quindi con il **strumenti** menu nell'istanza sperimentale. Si noterà **richiamare FirstCommand** comando. A questo punto, solo apparirà una finestra di messaggio con la dicitura "FirstCommandPackage all'interno di FirstMenuCommand.FirstCommand.MenuItemCallback()". Si vedrà come effettivamente avviare Blocco note di questo comando nella sezione successiva.  
  
## <a name="changing-the-menu-command-handler"></a>Modificare il gestore di comando di Menu  
 A questo punto è possibile aggiornare il gestore del comando per avviare il blocco note.  
  
1.  Arrestare il debug e tornare all'istanza di lavoro di Visual Studio. Aprire il file FirstCommand.cs e aggiungere la seguente istruzione using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Trovare il costruttore FirstCommand privato. Si tratta in cui il comando è collegato al servizio di comando e viene specificato il gestore del comando. Modificare il nome del gestore comando in StartNotepad, come indicato di seguito:  
  
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
  
3.  Rimuovere il metodo MenuItemCallback e aggiungere un metodo StartNotepad semplicemente avviare Blocco note:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Provare ora a eseguire l'operazione. Quando si avvia il debug del progetto e fare clic su **strumenti / richiamare FirstCommand**, dovrebbe essere un'istanza del blocco note venire in mente.  
  
     È possibile usare un'istanza di <xref:System.Diagnostics.Process> classe per eseguire qualsiasi eseguibile, non appena il blocco note. È possibile provarlo con calc.exe, ad esempio.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Pulizia ambiente di sperimentazione  
 Se si siano sviluppando più estensioni o semplicemente esplorando i risultati con diverse versioni del codice dell'estensione, l'ambiente sperimentale potrebbe smettere di funzionare nel modo desiderato. In questo caso, è necessario eseguire lo script di reimpostazione. Viene chiamato **reimpostare l'istanza sperimentale di Visual Studio 2015**, e fornito come parte di Visual Studio SDK. Questo script rimuove tutti i riferimenti a estensioni dall'ambiente sperimentale, ed è possibile iniziare da zero.  
  
 È possibile ottenere per questo script in uno dei due modi:  
  
1.  Dal desktop, individuare **reimpostare l'istanza sperimentale di Visual Studio 2015**.  
  
2.  Eseguire il comando seguente dalla riga di comando:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Distribuzione dell'estensione  
 Dopo aver creato l'estensione degli strumenti in esecuzione nel modo desiderato, è necessario pensare di condividerla con gli amici e colleghi. Che è molto semplice, in quanto dispongono di Visual Studio 2015 è installato. Tutto è necessario eseguire è inviare loro il file con estensione VSIX è stata compilata. (Assicurarsi di compilare la soluzione in modalità di rilascio.)  
  
 È possibile trovare il file VSIX per questa estensione nella directory bin FirstMenuCommand. In particolare, se che è stata compilata la configurazione di rilascio, sarà:  
  
 **\<directory del codice > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Per installare l'estensione, l'amico deve chiudere tutte le istanze aperte di Visual Studio, quindi fare doppio clic sul file con estensione VSIX, che consente di visualizzare il **programma di installazione VSIX**. I file vengono copiati i **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** directory.  
  
 Quando l'amico visualizzata nuovamente Visual Studio, egli sarà disponibile l'estensione FirstMenuCommand nel **strumenti / estensioni e aggiornamenti**. È possibile passare al **estensioni e aggiornamenti** per disinstallare o disabilitare l'estensione, troppo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata è stato illustrato solo una piccola parte delle operazioni che è possibile eseguire con un'estensione di Visual Studio. Ecco un breve elenco di operazioni (relativamente facile) è possibile eseguire con le estensioni di Visual Studio:  
  
1.  È possibile eseguire molte altre operazioni con un comando di menu semplice:  
  
    1.  Aggiungere un'icona personalizzata: [aggiunta di icone ai comandi di Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Modificare il testo del comando di menu: [la modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Aggiungere un menu di scelta rapida a un comando: [associazione scelte rapide da tastiera a voci di Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Aggiungere diversi tipi di comandi, menu e barre degli strumenti: [estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)  
  
3.  Aggiungere finestre degli strumenti ed estendere le finestre degli strumenti di Visual Studio incorporate: [estensione e personalizzazione di Windows degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Aggiungere i suggerimenti di codice, IntelliSense e altre funzionalità esistente di editor di codice: [estensione dell'Editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Aggiungere pagine delle proprietà e le opzioni e impostazioni utente per l'estensione: [estensione di proprietà e la finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md) e [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md)  
  
 Altri tipi di estensioni richiedono un po' più operazioni, ad esempio creare un nuovo tipo di progetto ([estensione di progetti](../extensibility/extending-projects.md)), creare un nuovo tipo di editor ([finestre di progettazione e creazione di editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)), o implementazione dell'estensione in una shell isolata: [Shell isolata di Visual Studio](../extensibility/visual-studio-isolated-shell.md)

