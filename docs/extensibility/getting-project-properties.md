---
title: Recupero delle proprietà di un progetto | Microsoft Docs
description: Informazioni su come visualizzare le proprietà del progetto in una finestra degli strumenti. Questo esempio mostra il controllo albero nella finestra degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e89a19ee51a62e8d92c0ec8984e912703e2b92b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968190"
---
# <a name="get-project-properties"></a>Ottenere le proprietà del progetto

In questa procedura dettagliata viene illustrato come visualizzare le proprietà del progetto in una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Per creare un progetto VSIX e aggiungere una finestra degli strumenti

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `ProjectPropertiesExtension` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Aggiungere una finestra degli strumenti aggiungendo un modello di elemento della finestra degli strumenti personalizzato denominato `ProjectPropertiesToolWindow` . Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di **dialogo Aggiungi nuovo elemento** passare a **Visual C# elementi**  >  **estensibilità** e selezionare **finestra degli strumenti personalizzata**. Nel campo **nome** nella parte inferiore della finestra di dialogo modificare il nome del file in `ProjectPropertiesToolWindow.cs` . Per ulteriori informazioni sulla creazione di una finestra degli strumenti personalizzata, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Compilare la soluzione e verificare che l'operazione avvenga senza errori.

### <a name="to-display-project-properties-in-a-tool-window"></a>Per visualizzare le proprietà del progetto in una finestra degli strumenti

1. Nel file ProjectPropertiesToolWindowCommand.cs aggiungere le direttive using seguenti.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. In *ProjectPropertiesToolWindowControl. XAML* rimuovere il pulsante esistente e aggiungere un controllo TreeView dalla casella degli strumenti. È anche possibile rimuovere il gestore dell'evento click dal file *ProjectPropertiesToolWindowControl.XAML.cs* .

3. In *ProjectPropertiesToolWindowCommand.cs* utilizzare il `ShowToolWindow()` metodo per aprire il progetto e leggere le relative proprietà, quindi aggiungere le proprietà al controllo TreeView. Il codice per ShowToolWindow dovrebbe essere simile al seguente:

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

6. In **Visualizza**  >  **altre finestre** fare clic su **ProjectPropertiesToolWindow**.

  Il controllo albero verrà visualizzato nella finestra degli strumenti insieme al nome del primo progetto e di tutte le relative proprietà del progetto.
