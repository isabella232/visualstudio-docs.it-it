---
title: Aggiunta di una finestra degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740262"
---
# <a name="add-a-tool-window"></a>Aggiungere una finestra degli strumenti

In questa procedura dettagliata viene illustrato come creare una finestra degli strumenti e integrarla in Visual Studio nei modi seguenti:In this walkthrough you learn how to create a tool window and integrate it into Visual Studio in the following ways:

- Aggiungere un controllo alla finestra degli strumenti.

- Aggiungere una barra degli strumenti a una finestra degli strumenti.

- Aggiungere un comando alla barra degli strumenti.

- Implementare i comandi.

- Impostare la posizione predefinita per la finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

Visual Studio SDK è incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.The Visual Studio SDK is included as an optional feature in Visual Studio setup. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tool-window"></a>Creare una finestra degli strumenti

1. Creare un progetto denominato **FirstToolWin** utilizzando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **FirstToolWindow**.

    > [!NOTE]
    > Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, consultate [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="add-a-control-to-the-tool-window"></a>Aggiungere un controllo alla finestra degli strumentiAdd a control to the tool window

1. Rimuovere il controllo predefinito. Aprire *FirstToolWindowControl.xaml* ed eliminare il **file Click Me!** .

2. Nella **Casella degli strumenti**espandere la sezione **Tutti i controlli WPF** e trascinare il controllo Elemento **multimediale** nel form **FirstToolWindowControl** . Selezionare il controllo e nella finestra **Proprietà** assegnare a questo elemento il nome **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Aggiungere una barra degli strumenti alla finestra degli strumenti
Aggiungendo una barra degli strumenti nel modo seguente, si garantisce che le sfumature e colori sono coerenti con il resto dell'IDE.

1. In **Esplora soluzioni**aprire *FirstToolWindowPackage.vsct*. Il file *vsct* definisce gli elementi dell'interfaccia utente grafica (GUI) nella finestra degli strumenti utilizzando XML.

2. Nella `<Symbols>` sezione individuare `<GuidSymbol>` il `name` nodo `guidFirstToolWindowPackageCmdSet`il cui attributo è . Aggiungere i `<IDSymbol>` due elementi seguenti `<IDSymbol>` all'elenco di elementi in questo nodo per definire una barra degli strumenti e un gruppo di barre degli strumenti.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Appena sopra `<Buttons>` la sezione, creare una `<Menus>` sezione simile alla seguente:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Ci sono diversi tipi di menu. Questo menu è una barra degli strumenti `type` in una finestra degli strumenti, definita dal relativo attributo. Le `guid` `id` impostazioni e costituiscono l'ID completo della barra degli strumenti. In genere, il `<Parent>` di un menu è il gruppo che lo contiene. Tuttavia, una barra degli strumenti è definita come elemento padre. Pertanto, lo stesso identificatore viene utilizzato per gli `<Menu>` elementi e `<Parent>` . L'attributo `priority` è solo '0'.

4. Le barre degli strumenti sono simili ai menu in molti modi. Ad esempio, proprio come un menu può avere gruppi di comandi, le barre degli strumenti possono anche avere gruppi. Nei menu, i gruppi di comandi sono separati da linee orizzontali. Sulle barre degli strumenti, i gruppi non sono separati da divisori visivi.)

    Aggiungere `<Groups>` una sezione `<Group>` che contiene un elemento. Definisce il gruppo di cui `<Symbols>` è stato dichiarato l'ID nella sezione. Aggiungere `<Groups>` la sezione `<Menus>` subito dopo la sezione.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Impostando il GUID e l'ID padre sul GUID e sull'ID della barra degli strumenti, si aggiunge il gruppo alla barra degli strumenti.

## <a name="add-a-command-to-the-toolbar"></a>Aggiungere un comando alla barra degli strumenti

Aggiungere un comando alla barra degli strumenti, che viene visualizzata come un pulsante.

1. Nella `<Symbols>` sezione dichiarare i seguenti elementi IDSymbol subito dopo le dichiarazioni della barra degli strumenti e del gruppo di barre degli strumenti.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Aggiungere un Button `<Buttons>` elemento all'interno della sezione. Questo elemento verrà visualizzato sulla barra degli strumenti nella finestra degli strumenti, con un'icona **di ricerca** (lente di ingrandimento).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Aprire *FirstToolWindowCommand.cs* e aggiungere le righe seguenti nella classe subito dopo i campi esistenti.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Questa operazione rende i comandi disponibili nel codice.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Aggiungere una proprietà MediaPlayer a FirstToolWindowControl
Dai gestori eventi per i controlli della barra degli strumenti, il codice deve essere in grado di accedere al controllo Media Player, che è un elemento figlio della classe FirstToolWindowControl.

In **Esplora soluzioni**fare clic con il pulsante destro del mouse su *FirstToolWindowControl.xaml*, **scegliere Visualizza codice**e aggiungere il codice seguente alla classe FirstToolWindowControl .

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Creare un'istanza della finestra degli strumenti e della barra degli strumenti
Aggiungere una barra degli strumenti e un comando di menu che richiama la finestra di dialogo **Apri file** e riproduce il file multimediale selezionato.

1. Aprire *FirstToolWindow.cs* e `using` aggiungere le direttive seguenti:Open FirstToolWindow.cs and add the following directives:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. All'interno della classe FirstToolWindow aggiungere un riferimento pubblico al controllo FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Alla fine del costruttore, impostare questa variabile di controllo sul controllo appena creato.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Creare un'istanza della barra degli strumenti all'interno del costruttore.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. A questo punto, il FirstToolWindow costruttore dovrebbe essere simile al seguente:At this point, the FirstToolWindow constructor should look like this:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Aggiungere il comando di menu alla barra degli strumenti. Nella classe FirstToolWindowCommand.cs aggiungere la direttiva using seguente:In the following class, add the following using directive:

    ```csharp
    using System.Windows.Forms;
    ```

7. Nella classe FirstToolWindowCommand aggiungere il codice seguente alla fine del metodo ShowToolWindow(). Il comando ButtonHandler verrà implementato nella sezione successiva.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Per implementare un comando di menu nella finestra degli strumentiTo implement a menu command in the tool window

1. Nella classe FirstToolWindowCommand aggiungere un metodo ButtonHandler che richiama la finestra di dialogo **Apri file.** Quando un file è stato selezionato, viene riprodotto il file multimediale.

2. Nella classe FirstToolWindowCommand aggiungere un riferimento privato alla finestra FirstToolWindow creata nel metodo FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Modificare il metodo ShowToolWindow() per impostare la finestra definita in precedenza (in modo che il gestore di comando ButtonHandler possa accedere al controllo finestra. Ecco il metodo completo ShowToolWindow().

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Aggiungere il metodo ButtonHandler.Add the ButtonHandler method. Crea un OpenFileDialog per l'utente per specificare il file multimediale da riprodurre e quindi riproduce il file selezionato.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Impostare la posizione predefinita per la finestra degli strumenti

Successivamente, specificare un percorso predefinito nell'IDE per la finestra degli strumenti. Le informazioni di configurazione per la finestra degli strumenti si trova nel file *FirstToolWindowPackage.cs.*

1. In *FirstToolWindowPackage.cs*, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> individuare `FirstToolWindowPackage` l'attributo nella classe , che passa il tipo FirstToolWindow al costruttore. Per specificare una posizione predefinita, è necessario aggiungere altri parametri al costruttore nell'esempio seguente.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Il primo parametro denominato `Style` `Tabbed`è e il relativo valore è , il che significa che la finestra sarà una scheda in una finestra esistente. La posizione di ancoraggio `Window` è specificata dal parametro, n questo caso, il GUID di **Esplora soluzioni**.

    > [!NOTE]
    > Per ulteriori informazioni sui tipi di finestre <xref:EnvDTE.vsWindowType>nell'IDE, vedere .

## <a name="test-the-tool-window"></a>Testare la finestra degli strumenti

1. Premere **F5** per aprire una nuova istanza della build sperimentale di Visual Studio.

2. Scegliere **Altre finestre** dal menu **Visualizza** , quindi fare clic su Prima finestra **degli strumenti**.

    La finestra degli strumenti del lettore multimediale dovrebbe essere aperta nella stessa posizione di **Esplora soluzioni.** Se viene ancora visualizzato nella stessa posizione di prima, reimpostare il layout della finestra (**Finestra / Ripristina layout finestra**).

3. Fare clic sul pulsante (ha l'icona **Cerca)** nella finestra degli strumenti. Selezionare un file audio o video supportato, ad *esempio, C:* **Open**

    Dovresti sentire il suono del suono del cicalino.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
