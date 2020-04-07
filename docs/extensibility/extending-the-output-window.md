---
title: Estensione della finestra di output Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711649"
---
# <a name="extend-the-output-window"></a>Estendere la finestra Output
La finestra **Output** è un set di riquadri di testo di lettura/scrittura. Visual Studio dispone di questi riquadri predefiniti: **Build**, in cui i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti comunicano messaggi relativi alle compilazioni, e **General**, in cui comunica messaggi sull'IDE. I progetti ottengono **Build** automaticamente un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> riferimento al riquadro Compila tramite i metodi <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> dell'interfaccia e Visual Studio offre accesso diretto al riquadro **Generale** tramite il servizio. Oltre ai riquadri predefiniti, è possibile creare e gestire riquadri personalizzati.

 È possibile controllare la finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> **di output** direttamente tramite le interfacce e . L'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> offerta dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> servizio, definisce i metodi per la creazione, il recupero e l'eliminazione dei riquadri della finestra **di output.** L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> definisce i metodi per visualizzare i riquadri, nascondere i riquadri e modificarne il testo. Un modo alternativo per controllare la <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> finestra output è tramite gli oggetti e nel modello a oggetti di automazione di Visual Studio.An alternative way of controlling the **Output** window is through the and objects in the Visual Studio Automation object model. Questi oggetti incapsulano quasi <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> tutte <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> le funzionalità delle interfacce e . Inoltre, gli <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> oggetti e aggiungono alcune funzionalità di livello superiore per semplificare l'enumerazione dei riquadri della finestra **di output** e recuperare il testo dai riquadri.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Creare un'estensione che usa il riquadro OutputCreate an extension that uses the Output pane
 È possibile creare un'estensione che esercita diversi aspetti del riquadro Output.You can make an extension that exercises different aspects of the Output pane.

1. Creare un progetto `TestOutput` VSIX denominato con un comando di menu denominato **TestOutput**. Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

2. Aggiungere i riferimenti seguenti:

    1. EnvDTE

    2. EnvDTE80

3. In *TestOutput.cs*aggiungere l'istruzione using seguente:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. In *TestOutput.cs*eliminare `ShowMessageBox` il metodo. Aggiungere il seguente stub di metodo:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. In the TestOutput constructor, change the command handler to OutputCommandHandler. Ecco la parte che aggiunge i comandi:

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

6. Le sezioni seguenti hanno diversi metodi che mostrano diversi modi di gestire il riquadro di output. È possibile chiamare questi metodi `OutputCommandHandler()` al corpo del metodo. Ad esempio, il codice `CreatePane()` seguente aggiunge il metodo specificato nella sezione successiva.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Creare una finestra di output con IVsOutputWindowCreate an Output window with IVsOutputWindow
 In questo esempio viene illustrato come creare <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> un nuovo riquadro della finestra di **output** utilizzando l'interfaccia .

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

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Richiama TestOutput** si dovrebbe vedere la finestra **di Output** con un'intestazione che dice Mostra **output da: CreatedPane** e le parole **Questo è il riquadro creato** nel riquadro stesso.

## <a name="create-an-output-window-with-outputwindow"></a>Creare una finestra di output con OutputWindowCreate an Output window with OutputWindow
 In questo esempio viene illustrato come creare <xref:EnvDTE.OutputWindow> **un** Output riquadro della finestra utilizzando l'oggetto.

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
        panes.Add(title);
    }
}
```

 Anche <xref:EnvDTE.OutputWindowPanes> se la raccolta consente di recuperare **un** output riquadro della finestra dal titolo, i titoli del riquadro non è garantito per essere univoco. Quando si dubita dell'univocità <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> di un titolo, utilizzare il metodo per recuperare il riquadro corretto in base al relativo GUID.

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Richiama TestOutput** si dovrebbe vedere la finestra di output con un'intestazione che dice **Mostra output da: DTEPane** e le parole **Aggiunto DEL riquadro DTE** nel riquadro stesso.

## <a name="delete-an-output-window"></a>Eliminare una finestra di outputDelete an Output window
 In questo esempio viene illustrato come eliminare un riquadro della finestra **di output.**

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

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Richiama TestOutput** si dovrebbe vedere la finestra di output con un'intestazione che dice **Mostra output da: Nuovo riquadro** e le parole **Aggiunto riquadro creato** nel riquadro stesso. Se si fa nuovamente clic sul comando **Richiama TestOutput,** il riquadro viene eliminato.

## <a name="get-the-general-pane-of-the-output-window"></a>Ottenere il riquadro Generale della finestra OutputGet the General pane of the Output window
 In questo esempio viene illustrato come ottenere il riquadro **Generale** incorporato della finestra **di output.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Richiama TestOutput** si dovrebbe vedere che la finestra **Output** mostra le parole **Trovato generale riquadro** nel riquadro.

## <a name="get-the-build-pane-of-the-output-window"></a>Ottenere il riquadro Compila della finestra OutputGet the Build pane of the Output window
 In questo esempio viene illustrato come trovare il riquadro **Compila** e scrivervi. Poiché il riquadro **Compila** non è attivato per impostazione predefinita, lo attiva anche.

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
