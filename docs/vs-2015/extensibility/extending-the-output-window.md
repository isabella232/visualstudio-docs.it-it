---
title: Estensione del Finestra di output | Microsoft Docs
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
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204421"
---
# <a name="extending-the-output-window"></a>Estensione della finestra di output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra **output** è un set di riquadri di testo in lettura/scrittura. Visual Studio include i riquadri predefiniti seguenti: **Build**, in cui i progetti comunicano messaggi sulle compilazioni e **generale**, in cui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comunica i messaggi sull'IDE. I progetti ottengono automaticamente un riferimento al riquadro di **compilazione** tramite i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> metodi di interfaccia e Visual Studio offre accesso diretto al riquadro **generale** tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servizio. Oltre ai riquadri predefiniti, è possibile creare e gestire i riquadri personalizzati.  
  
 È possibile controllare la finestra di **output** direttamente tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> le <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce e. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia, offerta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> servizio, definisce i metodi per la creazione, il recupero e l'eliminazione dei riquadri della finestra di **output** . L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia definisce i metodi per visualizzare i riquadri, nascondere i riquadri e manipolare il testo. Un modo alternativo per controllare la finestra di **output** consiste nell'usare gli <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> oggetti e nel modello a oggetti di automazione di Visual Studio. Questi oggetti incapsulano quasi tutte le funzionalità delle <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfacce e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . Inoltre, gli <xref:EnvDTE.OutputWindow> oggetti e <xref:EnvDTE.OutputWindowPane> aggiungono alcune funzionalità di livello superiore per semplificare l'enumerazione dei riquadri della finestra di **output** e il recupero di testo dai riquadri.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Creazione di un'estensione che utilizza il riquadro di output  
 È possibile creare un'estensione che eserciti diversi aspetti del riquadro di output.  
  
1. Creare un progetto VSIX denominato `TestOutput` con un comando di menu denominato **TestOutput**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Aggiungere i riferimenti seguenti:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. In TestOutput.cs aggiungere l'istruzione using seguente:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. In TestOutput.cs eliminare il metodo Metodo ShowMessageBox. Aggiungere lo stub del metodo seguente:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. Nel costruttore TestOutput modificare il gestore del comando in OutputCommandHandler. Ecco la parte che aggiunge i comandi:  
  
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
  
6. Le sezioni seguenti presentano metodi diversi che mostrano diverse modalità di gestione del riquadro di output. È possibile chiamare questi metodi per il corpo del metodo OutputCommandHandler (). Il codice seguente, ad esempio, aggiunge il metodo CreatePane () specificato nella sezione successiva.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Creazione di un Finestra di output con IVsOutputWindow  
 Questo esempio illustra come creare un nuovo riquadro della finestra di **output** usando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaccia.  
  
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
  
 Se si aggiunge questo metodo all'estensione fornita nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** dovrebbe essere visualizzata la finestra di **output** con un'intestazione che **Mostra l'output di: CreatedPane** e le parole **questo è il riquadro creato** nel riquadro stesso.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Creazione di un Finestra di output con OutputWindow  
 Questo esempio illustra come creare un riquadro della finestra di **output** usando l' <xref:EnvDTE.OutputWindow> oggetto.  
  
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
  
 Sebbene la <xref:EnvDTE.OutputWindowPanes> raccolta consenta di recuperare un riquadro della finestra di **output** in base al titolo, non è garantito che i titoli dei riquadri siano univoci. Quando si dubita dell'univocità di un titolo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> metodo per recuperare il riquadro corretto in base al relativo GUID.  
  
 Se si aggiunge questo metodo all'estensione fornita nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** dovrebbe essere visualizzata la finestra di output con un'intestazione che **Mostra l'output di: DTEPane** e il **riquadro parole aggiunto DTE** nel riquadro stesso.  
  
## <a name="deleting-an-output-window"></a>Eliminazione di un Finestra di output  
 Questo esempio illustra come eliminare un riquadro della finestra di **output** .  
  
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
  
 Se si aggiunge questo metodo all'estensione fornita nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** dovrebbe essere visualizzata la finestra di output con un'intestazione che **Mostra l'output di: nuovo riquadro** e il riquadro di parole **aggiunto creato** nel riquadro stesso. Se si fa nuovamente clic sul comando **Invoke TestOutput** , il riquadro viene eliminato.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Recupero del riquadro generale del Finestra di output  
 Questo esempio illustra come ottenere il riquadro **generale** predefinito della finestra di **output** .  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Se si aggiunge questo metodo all'estensione fornita nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** si noterà che la finestra di **output** Mostra il riquadro parole **trovate** nel riquadro.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Recupero del riquadro di compilazione della Finestra di output  
 Questo esempio illustra come trovare il riquadro di compilazione e scrivere su di esso. Poiché il riquadro di compilazione non è attivato per impostazione predefinita, lo attiva anche.  
  
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
