---
title: Estensione del Finestra di output | Microsoft Docs
description: Informazioni su come estendere la finestra Output in Visual Studio SDK e su come creare e gestire riquadri personalizzati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 402c53691525530171edafd6a0751dfc72c9798d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900226"
---
# <a name="extend-the-output-window"></a>Estendere la finestra Output
La **finestra Output** è un set di riquadri di testo di lettura/scrittura. Visual Studio include questi riquadri **predefiniti:** Compilazione , in cui i progetti comunicano messaggi sulle compilazioni e **Generale**, in cui comunicano messaggi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sull'IDE. I progetti ottengono  automaticamente un riferimento al riquadro Compilazione tramite i metodi di interfaccia e Visual Studio offre l'accesso diretto al <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> **riquadro** Generale tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servizio. Oltre ai riquadri predefiniti, è possibile creare e gestire riquadri personalizzati.

 È possibile controllare la **finestra Output** direttamente tramite le interfacce <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . L'interfaccia , offerta dal servizio, definisce i metodi per la creazione, il recupero e l'eliminazione dei riquadri della finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> di output.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>L'interfaccia definisce i metodi per visualizzare i riquadri, nascondere i riquadri e modificarne il testo. Un modo alternativo per controllare la finestra **Output** è tramite gli oggetti e nel modello a oggetti <xref:EnvDTE.OutputWindow> Visual Studio <xref:EnvDTE.OutputWindowPane> automazione di . Questi oggetti incapsulano quasi tutte le funzionalità delle <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfacce e . Inoltre, gli oggetti e aggiungono alcune funzionalità di livello superiore per semplificare l'enumerazione dei riquadri della finestra di output e il recupero di <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> testo dai riquadri. 

## <a name="create-an-extension-that-uses-the-output-pane"></a>Creare un'estensione che usa il riquadro Output
 È possibile creare un'estensione che esercita aspetti diversi del riquadro Output.

1. Creare un progetto VSIX `TestOutput` denominato con un comando di menu denominato **TestOutput**. Per altre informazioni, vedere [Creare un'estensione con un comando di menu.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Aggiungere i riferimenti seguenti:

    1. EnvDTE

    2. EnvDTE80

3. In *TestOutput.cs* aggiungere l'istruzione using seguente:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. In *TestOutput.cs* eliminare il `ShowMessageBox` metodo . Aggiungere lo stub del metodo seguente:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. Nel costruttore TestOutput modificare il gestore comandi in OutputCommandHandler. Ecco la parte che aggiunge i comandi:

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

6. Le sezioni seguenti hanno metodi diversi che illustrano diversi modi di gestire il riquadro di output. È possibile chiamare questi metodi nel corpo del `OutputCommandHandler()` metodo. Ad esempio, il codice seguente aggiunge `CreatePane()` il metodo specificato nella sezione successiva.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Creare una finestra output con IVsOutputWindow
 In questo esempio viene illustrato come creare un nuovo **riquadro della** finestra di output usando l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> .

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

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** viene visualizzata la finestra **Output** con un'intestazione che indica **Mostra output da: CreatedPane** e le parole This **is the Created Pane** nel riquadro stesso.

## <a name="create-an-output-window-with-outputwindow"></a>Creare una finestra di output con OutputWindow
 In questo esempio viene illustrato come creare un **riquadro della** finestra di output usando l'oggetto <xref:EnvDTE.OutputWindow> .

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

 Anche se la raccolta consente di recuperare un riquadro della finestra di output in base al titolo, non è garantito che i titoli dei riquadri <xref:EnvDTE.OutputWindowPanes> siano univoci.  In caso di dubbi sull'univocità di un titolo, usare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> per recuperare il riquadro corretto in base al RELATIVO GUID.

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando Invoke **TestOutput** viene visualizzata la finestra Output con un'intestazione che indica Mostra **output da: DTEPane** e le parole **Riquadro DTE** aggiunto nel riquadro stesso.

## <a name="delete-an-output-window"></a>Eliminare una finestra di output
 Questo esempio illustra come eliminare un riquadro **della finestra** di output.

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

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** viene visualizzata la finestra Output con un'intestazione che indica Mostra **output da:** Nuovo riquadro e le parole **Aggiunta** riquadro creato nel riquadro stesso. Se si fa di **nuovo clic sul comando Invoke TestOutput** , il riquadro viene eliminato.

## <a name="get-the-general-pane-of-the-output-window"></a>Ottenere il riquadro Generale della finestra Output
 Questo esempio illustra come ottenere il riquadro **Generale** incorporato della finestra **Output.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Se si aggiunge questo metodo all'estensione specificata nella sezione precedente, quando si fa clic sul comando **Invoke TestOutput** si dovrebbe vedere che nella finestra **Output** vengono visualizzate le parole Found **General** nel riquadro.

## <a name="get-the-build-pane-of-the-output-window"></a>Ottenere il riquadro Compilazione della finestra Output
 Questo esempio illustra come trovare il **riquadro** Compilazione e scriverlo. Poiché il **riquadro** Compilazione non è attivato per impostazione predefinita, lo attiva anche.

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
