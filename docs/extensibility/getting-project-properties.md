---
title: Recupero delle proprietà di progetto | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6708759796639886d84a46003fbb894b988a714
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194995"
---
# <a name="get-project-properties"></a>Ottenere le proprietà del progetto

Questa procedura dettagliata mostra come proprietà del progetto consente di visualizzare in una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Per creare un progetto VSIX e aggiungere una finestra degli strumenti

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `ProjectPropertiesExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** dialogo eseguendo una ricerca per "vsix".

2. Aggiungere una finestra degli strumenti tramite l'aggiunta di un modello di elemento di finestra degli strumenti personalizzata denominato `ProjectPropertiesToolWindow`. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, passare a **elementi di Visual C#** > **Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **Name** campo nella parte inferiore della finestra di dialogo, modificare il nome del file per `ProjectPropertiesToolWindow.cs`. Per altre informazioni su come creare una finestra degli strumenti personalizzata, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Compilare la soluzione e verificare che l'operazione avvenga senza errori.

### <a name="to-display-project-properties-in-a-tool-window"></a>Per visualizzare le proprietà del progetto in una finestra degli strumenti

1. Nel file ProjectPropertiesToolWindowCommand.cs, aggiungere le seguenti istruzioni using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. Nelle *ProjectPropertiesToolWindowControl.xaml*, rimuovere al pulsante esistente e aggiungere un controllo TreeView dalla casella degli strumenti. È anche possibile rimuovere il gestore dell'evento click dal *ProjectPropertiesToolWindowControl.xaml.cs* file.

3. Nelle *ProjectPropertiesToolWindowCommand.cs*, usare il `ShowToolWindow()` metodo per aprire il progetto e leggere le relative proprietà, quindi aggiungere le proprietà di visualizzazione albero. Il codice per ShowToolWindow dovrebbe essere simile al seguente:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.

5. Aprire un progetto nell'istanza sperimentale.

6. Nel **View** > **Other Windows** fare clic su **ProjectPropertiesToolWindow**.

  Verrà visualizzato il controllo struttura ad albero nella finestra degli strumenti insieme al nome del primo progetto e di tutte le relative proprietà di progetto.