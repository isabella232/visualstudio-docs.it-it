---
title: Estensione della finestra di Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e4fe3b07a2a076218fd004328ad87e4d5e3bab7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966012"
---
# <a name="extending-the-output-window"></a>Estensione della finestra di output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il **Output** finestra è un set di riquadri di testo di lettura/scrittura. Visual Studio include questi riquadri predefiniti: **Compilare**, nella quale i progetti comunicare i messaggi relativi alle compilazioni, e **generali**, in cui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comunica i messaggi relativi a IDE. Progetti di ottenere un riferimento al **compilare** riquadro automaticamente tramita il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metodi di interfaccia e Visual Studio offre accesso diretto al **generali** riquadro tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servizio. Oltre ai riquadri predefiniti, è possibile creare e gestire i proprio riquadri personalizzati.  
  
 È possibile controllare la **Output** finestra direttamente tramita il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia, che viene offerto dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> del servizio, definisce i metodi per la creazione, recupero ed eliminazione **Output** riquadri della finestra. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia definisce i metodi per la visualizzazione dei riquadri, nascondere riquadri e la modifica del testo. Un modo alternativo di controllare il **Output** finestra è tramite il <xref:EnvDTE.OutputWindow> e <xref:EnvDTE.OutputWindowPane> oggetti nel modello a oggetti di automazione di Visual Studio. Questi oggetti includono quasi tutte le funzionalità dei <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce. Inoltre, il <xref:EnvDTE.OutputWindow> e <xref:EnvDTE.OutputWindowPane> oggetti aggiungono alcune funzionalità di livello superiore per renderne più semplice enumerare le **Output** riquadri della finestra e per recuperare il testo dai riquadri.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Creazione di un'estensione che usa il riquadro di Output  
 È possibile creare un'estensione che esercita diversi aspetti del riquadro di Output.  
  
1.  Creare un progetto VSIX denominato `TestOutput` con un comando di menu denominato **TestOutput**. Per altre informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aggiungere i riferimenti seguenti:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  In TestOutput.cs, aggiungere la seguente istruzione using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  In TestOutput.cs, eliminare il metodo ShowMessageBox. Aggiungere lo stub del metodo seguente:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  Nel costruttore TestOutput, modificare il gestore del comando a OutputCommandHandler. Questa è la parte che aggiunge i comandi:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  Le sezioni seguenti includono diversi metodi che mostrano diverse modalità di gestione con il riquadro di Output. È possibile chiamare questi metodi al corpo del metodo OutputCommandHandler(). Ad esempio, il codice seguente aggiunge il metodo CreatePane() fornito nella sezione successiva.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Creazione di una finestra di Output con IVsOutputWindow  
 Questo esempio viene illustrato come creare una nuova **Output** riquadro della finestra usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando dovrebbe essere il **Output** finestra con un'intestazione con la dicitura **Mostra output Da: CreatedPane** e le parole **questo è il riquadro creazione** nel riquadro stesso.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Creazione di una finestra di Output con OutputWindow  
 In questo esempio viene illustrato come creare un **Output** riquadro della finestra usando il <xref:EnvDTE.OutputWindow> oggetto.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Anche se il <xref:EnvDTE.OutputWindowPanes> raccolta consente di recuperare un' **Output** riquadro della finestra dal relativo titolo, i titoli di riquadro non sono necessariamente essere univoci. Quando si dubito l'univocità di un titolo, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metodo per recuperare il riquadro corretto con il relativo GUID.  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando è verrà visualizzata la finestra di Output con un'intestazione con la dicitura **Mostra output di: DTEPane** e le parole **aggiunto riquadro DTE** nel riquadro stesso.  
  
## <a name="deleting-an-output-window"></a>L'eliminazione di una finestra di Output  
 In questo esempio mostra come eliminare un' **Output** riquadro della finestra.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando è verrà visualizzata la finestra di Output con un'intestazione con la dicitura **Mostra output di: Nuovo riquadro** e le parole **aggiunto riquadro create** nel riquadro stesso. Se si fa clic il **richiamare TestOutput** nuovo il comando, il riquadro viene eliminato.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Ottenere il riquadro Generale della finestra di Output  
 In questo esempio viene illustrato come ottenere l'oggetto incorporato **generali** riquadro della finestra di **Output** finestra.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Se si aggiunge questo metodo per l'estensione fornita nella sezione precedente, quando si fa clic il **richiamare TestOutput** comando si noterà che il **Output** finestra vengono visualizzate le parole **trovato generale riquadro** nel riquadro.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Ottenere il riquadro di compilazione della finestra di Output  
 In questo esempio viene illustrato come individuare il riquadro di compilazione e la scrittura. Poiché il riquadro di compilazione non è attivato per impostazione predefinita, attiva anche.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
