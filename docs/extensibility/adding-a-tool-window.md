---
title: Aggiunta di una finestra degli strumenti | Microsoft Docs
description: Informazioni su come creare una finestra degli strumenti e integrarla in Visual Studio aggiungendo un controllo e una barra degli strumenti contenente un comando alla finestra degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3bf82de2fd491f786ed3a882ee44adb20b38d442
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035287"
---
# <a name="add-a-tool-window"></a>Aggiungere una finestra degli strumenti

In questa procedura dettagliata si apprenderà come creare una finestra degli strumenti e integrarla in Visual Studio nei modi seguenti:

- Aggiungere un controllo alla finestra degli strumenti.

- Aggiungere una barra degli strumenti a una finestra degli strumenti.

- Aggiungere un comando alla barra degli strumenti.

- Implementare i comandi .

- Impostare la posizione predefinita per la finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

L Visual Studio SDK è incluso come funzionalità facoltativa nella Visual Studio configurazione. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tool-window"></a>Creare una finestra degli strumenti

1. Creare un progetto denominato **FirstToolWin usando** il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato **denominato FirstToolWindow.**

    > [!NOTE]
    > Per altre informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="add-a-control-to-the-tool-window"></a>Aggiungere un controllo alla finestra degli strumenti

1. Rimuovere il controllo predefinito. Aprire *FirstToolWindowControl.xaml* ed eliminare il file **Click Me!** .

2. Nella casella **degli strumenti** espandere la sezione Tutti i **controlli WPF** e trascinare il controllo **Elemento** multimediale nel form **FirstToolWindowControl.** Selezionare il controllo e nella finestra **Proprietà assegnare all'elemento** il nome **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Aggiungere una barra degli strumenti alla finestra degli strumenti
Aggiungendo una barra degli strumenti nel modo seguente, si garantisce che le sfumature e i colori siano coerenti con il resto dell'IDE.

1. In **Esplora soluzioni** aprire *FirstToolWindowPackage.vsct.* Il file *con estensione vsct* definisce gli elementi dell'interfaccia utente grafica (GUI) nella finestra degli strumenti tramite XML.

2. Nella sezione `<Symbols>` trovare il nodo il cui attributo è `<GuidSymbol>` `name` `guidFirstToolWindowPackageCmdSet` . Aggiungere i due elementi seguenti all'elenco di elementi in questo nodo per definire una barra degli strumenti `<IDSymbol>` e un gruppo di barre degli `<IDSymbol>` strumenti.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Appena sopra `<Buttons>` la sezione creare una sezione simile alla `<Menus>` seguente:

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

    Esistono diversi tipi di menu. Questo menu è una barra degli strumenti in una finestra degli strumenti, definita dal relativo `type` attributo . Le `guid` impostazioni e costituiscono `id` l'ID completo della barra degli strumenti. In genere, `<Parent>` di un menu è il gruppo contenitore. Tuttavia, una barra degli strumenti è definita come padre. Pertanto, lo stesso identificatore viene usato per gli `<Menu>` elementi `<Parent>` e . `priority`L'attributo è semplicemente "0".

4. Le barre degli strumenti sono simili ai menu in molti modi. Ad esempio, proprio come un menu può avere gruppi di comandi, anche le barre degli strumenti possono avere gruppi. Nei menu i gruppi di comandi sono separati da linee orizzontali. Sulle barre degli strumenti i gruppi non sono separati da divisori visivi.

    Aggiungere una `<Groups>` sezione che contiene un elemento `<Group>` . Definisce il gruppo di cui è stato dichiarato l'ID nella `<Symbols>` sezione . Aggiungere la `<Groups>` sezione subito dopo la sezione `<Menus>` .

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Impostando il GUID e l'ID padre sul GUID e sull'ID della barra degli strumenti, si aggiunge il gruppo alla barra degli strumenti.

## <a name="add-a-command-to-the-toolbar"></a>Aggiungere un comando alla barra degli strumenti

Aggiungere un comando alla barra degli strumenti, che viene visualizzata come pulsante.

1. Nella sezione dichiarare gli elementi IDSymbol seguenti subito dopo le dichiarazioni della barra degli strumenti e del gruppo `<Symbols>` di barre degli strumenti.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Aggiungere un elemento Button all'interno della `<Buttons>` sezione . Questo elemento verrà visualizzato sulla barra degli strumenti nella finestra degli strumenti, con **l'icona** Cerca (lente di ingrandimento).

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

    In questo modo i comandi saranno disponibili nel codice.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Aggiungere una proprietà MediaPlayer a FirstToolWindowControl
Dai gestori eventi per i controlli della barra degli strumenti, il codice deve essere in grado di accedere al controllo Media Player, che è figlio della classe FirstToolWindowControl.

In Esplora soluzioni fare clic con il pulsante destro del mouse su *FirstToolWindowControl.xaml,* scegliere Visualizza **codice** e aggiungere il codice seguente alla classe FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Creare un'istanza della finestra degli strumenti e della barra degli strumenti
Aggiungere una barra degli strumenti e un comando di menu che richiama la **finestra di dialogo Apri file** e riproduce il file multimediale selezionato.

1. Aprire *FirstToolWindow.cs* e aggiungere le `using` direttive seguenti:

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

5. A questo punto, il costruttore FirstToolWindow dovrebbe essere simile al seguente:

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

6. Aggiungere il comando di menu alla barra degli strumenti. Nella classe FirstToolWindowCommand.cs aggiungere la direttiva using seguente:

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

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Per implementare un comando di menu nella finestra degli strumenti

1. Nella classe FirstToolWindowCommand aggiungi un metodo ButtonHandler che richiama la finestra **di dialogo Apri** file. Quando un file è stato selezionato, riproduce il file multimediale.

2. Nella classe FirstToolWindowCommand aggiungi un riferimento privato alla finestra FirstToolWindow che viene creata nel metodo FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Modificare il metodo ShowToolWindow() per impostare la finestra definita in precedenza ,in modo che il gestore di comando ButtonHandler possa accedere al controllo finestra. Ecco il metodo ShowToolWindow() completo.

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

4. Aggiungere il metodo ButtonHandler. Crea un oggetto OpenFileDialog per l'utente per specificare il file multimediale da riprodurre e quindi riproduce il file selezionato.

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

Specificare quindi un percorso predefinito nell'IDE per la finestra degli strumenti. Le informazioni di configurazione per la finestra degli strumenti si trova nel file *FirstToolWindowPackage.cs.*

1. In *FirstToolWindowPackage.cs* trovare l'attributo nella classe , che passa il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> tipo `FirstToolWindowPackage` FirstToolWindow al costruttore. Per specificare una posizione predefinita, è necessario aggiungere altri parametri al costruttore nell'esempio seguente.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Il primo parametro denominato è e il relativo valore è , il che significa che la finestra `Style` sarà una scheda in una finestra `Tabbed` esistente. La posizione di ancoraggio viene specificata dal `Window` parametro , in questo caso il GUID del **Esplora soluzioni**.

    > [!NOTE]
    > Per altre informazioni sui tipi di finestre nell'IDE, vedere <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Testare la finestra degli strumenti

1. Premere **F5** per aprire una nuova istanza del Visual Studio compilazione sperimentale.

2. Scegliere **Altro** dal menu Visualizza Windows **quindi** fare clic su Prima finestra **degli strumenti.**

    La finestra degli strumenti del lettore multimediale deve essere aperta nella stessa **posizione Esplora soluzioni**. Se viene ancora visualizzato nella stessa posizione di prima, reimpostare il layout della finestra **(Finestra/Reimposta layout finestra).**

3. Fare clic sul pulsante (con **l'icona** Cerca) nella finestra degli strumenti. Selezionare un file audio o video supportato, ad esempio *C:\windows\media\chimes.wav,* quindi premere **Apri**.

    Si dovrebbe ascoltare il suono del segnale acustico.

## <a name="see-also"></a>Vedi anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
