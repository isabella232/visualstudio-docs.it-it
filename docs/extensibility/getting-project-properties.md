---
title: Recupero delle proprietà del progetto Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711417"
---
# <a name="get-project-properties"></a>Ottenere le proprietà del progettoGet project properties

In questa procedura dettagliata viene illustrato come visualizzare le proprietà del progetto in una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Per creare un progetto VSIX e aggiungere una finestra degli strumentiTo create a VSIX Project and add a tool window

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un progetto `ProjectPropertiesExtension`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Aggiungere una finestra degli strumenti aggiungendo un `ProjectPropertiesToolWindow`modello di elemento Finestra degli strumenti personalizzata denominato . In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di **dialogo Aggiungi nuovo elemento**, passare a**Estensibilità** degli elementi > di **Visual C,** quindi selezionare **Finestra degli strumenti personalizzata**. Nel campo **Nome** nella parte inferiore della finestra `ProjectPropertiesToolWindow.cs`di dialogo, modificare il nome del file in . Per ulteriori informazioni su come creare una finestra degli strumenti personalizzata, vedere [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Compilare la soluzione e verificare che l'operazione avvenga senza errori.

### <a name="to-display-project-properties-in-a-tool-window"></a>Per visualizzare le proprietà del progetto in una finestra degli strumentiTo display project properties in a tool window

1. Nel file ProjectPropertiesToolWindowCommand.cs aggiungere le direttive using seguenti.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. In *ProjectPropertiesToolWindowControl.xaml*rimuovere il pulsante esistente e aggiungere un controllo TreeView dalla casella degli strumenti. È inoltre possibile rimuovere il gestore dell'evento click dal file *di ProjectPropertiesToolWindowControl.xaml.cs.*

3. In *ProjectPropertiesToolWindowCommand.cs*, `ShowToolWindow()` utilizzare il metodo per aprire il progetto e leggerne le proprietà, quindi aggiungere le proprietà a TreeView. Il codice per ShowToolWindow dovrebbe essere simile al seguente:The code for ShowToolWindow should look like the following:

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

4. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

5. Aprire un progetto nell'istanza sperimentale.

6. Nella **finestra Visualizza** > **altre finestre** fare clic su **ProjectPropertiesToolWindow**.

  Il controllo struttura ad albero dovrebbe essere visualizzato nella finestra degli strumenti insieme al nome del primo progetto e a tutte le relative proprietà del progetto.
