---
title: Aggiunta dinamica di voci di menu Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712062"
---
# <a name="dynamically-add-menu-items"></a>Aggiungere dinamicamente voci di menu
È possibile aggiungere voci di menu `DynamicItemStart` in fase di esecuzione specificando il flag di comando in una definizione di pulsante segnaposto nel file della tabella dei comandi di Visual Studio (*.vsct*), quindi definendo (nel codice) il numero di voci di menu da visualizzare e gestendo i comandi. Quando il pacchetto VSPackage viene caricato, il segnaposto viene sostituito con le voci di menu dinamico.

 Visual Studio usa gli elenchi dinamici nell'elenco Degli ultimi elementi usati (MRU, **Most Recently Used),** che visualizza i nomi dei documenti aperti di recente, e l'elenco **finestre,** che visualizza i nomi delle finestre attualmente aperte.   Il `DynamicItemStart` flag in una definizione di comando specifica che il comando è un segnaposto fino a quando il pacchetto VSPackage viene aperto. Quando il pacchetto VSPackage viene aperto, il segnaposto viene sostituito con 0 o più comandi che vengono creati in fase di esecuzione e aggiunti all'elenco dinamico. Potrebbe non essere possibile visualizzare la posizione nel menu in cui viene visualizzato l'elenco dinamico fino a quando il pacchetto VSPackage viene aperto.  Per popolare l'elenco dinamico, Visual Studio chiede al pacchetto VSPackage per cercare un comando con un ID i cui primi caratteri sono gli stessi dell'ID del segnaposto. Quando Visual Studio trova un comando corrispondente, aggiunge il nome del comando all'elenco dinamico. Quindi incrementa l'ID e cerca un altro comando corrispondente da aggiungere all'elenco dinamico fino a quando non sono presenti comandi più dinamici.

 Questa procedura dettagliata viene illustrato come impostare il progetto di avvio in una soluzione di Visual Studio con un comando sulla barra degli strumenti **di Esplora soluzioni.** Utilizza un controller di menu che dispone di un elenco a discesa dinamico dei progetti nella soluzione attiva. Per evitare che questo comando venga visualizzato quando non è aperta alcuna soluzione o quando la soluzione aperta dispone di un solo progetto, il pacchetto VSPackage viene caricato solo quando una soluzione dispone di più progetti.

 Per ulteriori informazioni sui file *vsct,* vedere File della tabella dei comandi di [Visual Studio (con estensione vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menuCreate an extension with a menu command

1. Creare un progetto `DynamicMenuItems`VSIX denominato .

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato e denominarlo **DynamicMenu**. Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Impostazione degli elementi nel file *vsct*
 Per creare un controller di menu con voci di menu dinamico su una barra degli strumenti, specificare i seguenti elementi:

- Due gruppi di comandi, uno che contiene il controller di menu e un altro che contiene le voci di menu nell'elenco a discesa

- Un elemento menu di tipo`MenuController`

- Due pulsanti, uno che funge da segnaposto per le voci di menu e un altro che fornisce l'icona e la descrizione comando sulla barra degli strumenti.

1. In *DynamicMenuPackage.vsct*, definire gli ID di comando. Passare alla sezione Simboli e sostituire gli elementi IDSymbol nel blocco **GUIDDynamicMenuPackageCmdSet** GuidSymbol. È necessario definire gli elementi IDSymbol per i due gruppi, il controller di menu, il comando segnaposto e il comando di ancoraggio.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. Nella sezione Gruppi eliminare i gruppi esistenti e aggiungere i due gruppi appena definiti:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Aggiungere il MenuController.Add the MenuController. Impostare il flag del comando DynamicVisibility, poiché non è sempre visibile. Il ButtonText non viene visualizzato.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Aggiungere due pulsanti, uno come segnaposto per le voci di menu dinamico e uno come ancoraggio per il MenuController.Add two buttons, one as a placeholder for the dynamic menu items and one as ananchor for the MenuController.

     L'elemento padre del pulsante segnaposto è **MyMenuControllerGroup**. Aggiungere i flag di comando DynamicItemStart, DynamicVisibility e TextChanges al pulsante segnaposto. Il ButtonText non viene visualizzato.

     Il pulsante di ancoraggio contiene l'icona e il testo della descrizione comando. L'elemento padre del pulsante di ancoraggio è anche **MyMenuControllerGroup**. Aggiungere il flag di comando NoShowOnMenuController per assicurarsi che il pulsante non venga effettivamente visualizzato nell'elenco a discesa del controller di menu e il flag di comando FixMenuController per renderlo l'ancoraggio permanente.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Aggiungere un'icona al progetto (nella cartella *Risorse)* e quindi aggiungervi il riferimento nel file *vsct.* In questa procedura dettagliata viene usata l'icona Frecce inclusa nel modello di progetto.

5. Aggiungere una sezione VisibilityConstraints all'esterno della sezione Commands appena prima della sezione Symbols. Se lo si aggiunge dopo i simboli, è possibile che venga visualizzato un avviso. Questa sezione assicura che il controller di menu venga visualizzato solo quando viene caricata una soluzione con più progetti.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementare il comando di menu dinamico
 Creare una classe di comando di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>menu dinamico che eredita da . In questa implementazione, il costruttore specifica un predicato da utilizzare per i comandi corrispondenti. È necessario <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> eseguire l'override del metodo <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> per utilizzare questo predicato per impostare la proprietà , che identifica il comando da richiamare.

1. Creare un nuovo file di classe di C, denominato *DynamicItemMenuCommand.cs*, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>quindi aggiungere una classe denominata **DynamicItemMenuCommand** che eredita da :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Aggiungere le seguenti direttive using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Aggiungere un campo privato per archiviare il predicato di corrispondenza:Add a private field to store the match predicate:

    ```csharp
    private Predicate<int> matches;

    ```

4. Aggiungere un costruttore che <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> eredita dal costruttore e <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> specifica un gestore di comando e un gestore. Aggiungere un predicato per la corrispondenza con il comando:Add a predicate for matching the command:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Eseguire <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> l'override del metodo in modo che <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> chiami il predicato matches e imposta la proprietà:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Aggiungere il comando
 Il DynamicMenu costruttore è dove è possibile impostare i comandi di menu, inclusi i menu dinamici e le voci di menu.

1. In *DynamicMenuPackage.cs*aggiungere il GUID del set di comandi e l'ID di comando:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Nel file *DynamicMenu.cs* aggiungere le direttive using seguenti:In the DynamicMenu.cs file, add the following using directives:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Nella `DynamicMenu` classe aggiungere un campo privato **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Aggiungere un campo rootItemId privato:Add a private rootItemId field:

    ```csharp
    private int rootItemId = 0;
    ```

5. Nel costruttore DynamicMenu aggiungere il comando di menu. Nella sezione successiva definiremo il gestore `BeforeQueryStatus` del comando, il gestore eventi e il predicato di corrispondenza.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Implementare i gestoriImplement the handlers
 Per implementare voci di menu dinamico in un controller di menu, è necessario gestire il comando quando si fa clic su un elemento dinamico. È inoltre necessario implementare la logica che imposta lo stato della voce di menu. Aggiungere i gestori `DynamicMenu` alla classe.

1. Per implementare il comando Imposta progetto di **avvio,** aggiungere il gestore eventi **OnInvokedDynamicItem.** Cerca il progetto il cui nome è uguale al testo del comando che è stato richiamato e <xref:EnvDTE.SolutionBuild.StartupProjects%2A> lo imposta come progetto di avvio impostando il relativo percorso assoluto nella proprietà.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Aggiungere `OnBeforeQueryStatusDynamicItem` il gestore eventi. Questo è il gestore chiamato prima di un `QueryStatus` evento. Determina se la voce di menu è una voce "reale", ovvero non la voce segnaposto e se l'elemento è già selezionato (ovvero il progetto è già impostato come progetto di avvio).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Implementare il predicato di corrispondenza dell'ID di comandoImplement the command ID match predicate

Implementare ora il predicato di corrispondenza. È necessario determinare due cose: in primo luogo, se l'ID di comando è valido (è maggiore o uguale all'ID di comando dichiarato) e in secondo luogo, se specifica un progetto possibile (è inferiore al numero di progetti nella soluzione).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Impostare il pacchetto VSPackage per il caricamento solo quando una soluzione ha più progettiSet the VSPackage to load only when a solution has multiple projects
 Poiché il comando Imposta progetto di **avvio** non ha senso a meno che la soluzione attiva non disponga di più di un progetto, è possibile impostare il pacchetto VSPackage per il caricamento automatico solo in questo caso. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> con il contesto <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>dell'interfaccia utente . Nel *file DynamicMenuPackage.cs* aggiungere i seguenti attributi alla classe DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Testare il comando set startup project
 A questo punto è possibile testare il codice.

1. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

2. Nell'istanza sperimentale, aprire una soluzione che dispone di più di un progetto.

     Verrà visualizzata l'icona della freccia sulla barra degli strumenti **di Esplora soluzioni.** Quando lo si espande, dovrebbero essere visualizzate le voci di menu che rappresentano i diversi progetti nella soluzione.

3. Quando si seleziona uno dei progetti, diventa il progetto di avvio.

4. Quando si chiude la soluzione o si apre una soluzione con un solo progetto, l'icona della barra degli strumenti dovrebbe scomparire.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
