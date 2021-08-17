---
title: Recupero Project proprietà | Microsoft Docs
description: Informazioni su come visualizzare le proprietà del progetto in una finestra degli strumenti. Questo esempio mostra il controllo struttura ad albero nella finestra degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3244fde5689bc81431f4e14bd6322fd61f9594e01e088156c6781225b0c7b2b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376612"
---
# <a name="get-project-properties"></a>Ottenere le proprietà del progetto

Questa procedura dettagliata illustra come visualizzare le proprietà del progetto in una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Per creare un Project VSIX e aggiungere una finestra degli strumenti

1. Ogni Visual Studio'estensione inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `ProjectPropertiesExtension` . È possibile trovare il modello di progetto VSIX nella **finestra di dialogo Nuovo Project** ricerca di "vsix".

2. Aggiungere una finestra degli strumenti aggiungendo un modello di elemento Finestra degli strumenti personalizzata denominato `ProjectPropertiesToolWindow` . Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Nella finestra **di dialogo Aggiungi nuovo elemento** passare a Estendibilità elementi di Visual **C#**  >   e selezionare Finestra degli **strumenti personalizzata**. Nel campo **Nome** nella parte inferiore della finestra di dialogo modificare il nome del file in `ProjectPropertiesToolWindow.cs` . Per altre informazioni su come creare una finestra degli strumenti personalizzata, vedere [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Compilare la soluzione e verificare che l'operazione avvenga senza errori.

### <a name="to-display-project-properties-in-a-tool-window"></a>Per visualizzare le proprietà del progetto in una finestra degli strumenti

1. Nel file ProjectPropertiesToolWindowCommand.cs aggiungere le direttive using seguenti.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. In *ProjectPropertiesToolWindowControl.xaml* rimuovere il pulsante esistente e aggiungere un controllo TreeView dalla casella degli strumenti. È anche possibile rimuovere il gestore dell'evento Click dal file *ProjectPropertiesToolWindowControl.xaml.cs.*

3. In *ProjectPropertiesToolWindowCommand.cs* usare il metodo per aprire il progetto e leggerne le proprietà, quindi aggiungere le `ShowToolWindow()` proprietà a TreeView. Il codice per ShowToolWindow dovrebbe essere simile al seguente:

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

6. Nella finestra **Visualizza**  >  **altro Windows** fare clic su **ProjectPropertiesToolWindow**.

  Il controllo albero dovrebbe essere visualizzato nella finestra degli strumenti insieme al nome del primo progetto e a tutte le relative proprietà del progetto.
