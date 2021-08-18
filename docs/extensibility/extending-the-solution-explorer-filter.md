---
title: Estensione del Esplora soluzioni filtro | Microsoft Docs
description: Informazioni su come estendere Esplora soluzioni di filtro per visualizzare o nascondere file diversi nell'SDK Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e2c41830892b6199a5cd844b365898efa83c83fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125075"
---
# <a name="extend-the-solution-explorer-filter"></a>Estendere il filtro Esplora soluzioni
È possibile estendere **Esplora soluzioni** filtro per visualizzare o nascondere file diversi. Ad esempio, è possibile creare un filtro che mostra solo i class factory C# nel Esplora soluzioni **,** come illustrato in questa procedura dettagliata.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-visual-studio-package-project"></a>Creare un progetto Visual Studio pacchetto

1. Creare un progetto VSIX denominato `FileFilter` . Aggiungere un modello di elemento di comando personalizzato **denominato FileFilter**. Per altre informazioni, vedere [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Aggiungere un riferimento a `System.ComponentModel.Composition` e `Microsoft.VisualStudio.Utilities` .

3. Fare in modo che il comando di menu venga visualizzato Esplora soluzioni barra **degli** strumenti. Aprire il *file FileFilterPackage.vsct.*

4. Modificare il `<Button>` blocco nel modo seguente:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Aggiornare il file manifesto

1. Nel file *source.extension.vsixmanifest* aggiungere un asset che sia un componente MEF.

2. Nella scheda **Asset** scegliere il **pulsante** Nuovo.

3. Nel campo **Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

4. Nel campo **Origine** scegliere **Un progetto nella soluzione corrente.**

5. Nel campo **Project** scegliere **FileFilter** e quindi fare clic sul **pulsante OK.**

### <a name="add-the-filter-code"></a>Aggiungere il codice di filtro

1. Aggiungere alcuni GUID al *file FileFilterPackageGuids.cs:*

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Aggiungere un file di classe al progetto FileFilter denominato *FileNameFilter.cs.*

3. Sostituire lo spazio dei nomi vuoto e la classe vuota con il codice seguente.

     Il metodo accetta la raccolta che contiene la radice della soluzione ( ) e restituisce la raccolta di elementi `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` `rootItems` da includere nel filtro.

     Il `ShouldIncludeInFilter` metodo filtra gli elementi nella **Esplora soluzioni** gerarchia in base alla condizione specificata.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. In *FileFilter.cs* rimuovere il posizionamento del comando e il codice di gestione dal costruttore FileFilter. Il risultato dovrebbe essere simile al seguente:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Rimuovere anche `ShowMessageBox()` il metodo .

5. In *FileFilterPackage.cs* sostituire il codice nel `Initialize()` metodo con il codice seguente:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Testare il codice

1. Compilare ed eseguire il progetto. Verrà visualizzata una seconda istanza di Visual Studio. Si tratta dell'istanza sperimentale.

2. Nell'istanza sperimentale di Visual Studio aprire un progetto C#.

3. Cercare il pulsante aggiunto sulla barra degli **strumenti Esplora soluzioni** comandi. Deve essere il quarto pulsante da sinistra.

4. Quando si fa clic sul pulsante, tutti i file devono essere filtrati e tutti gli elementi sono stati filtrati **dalla visualizzazione.** **nell'Esplora soluzioni**.
