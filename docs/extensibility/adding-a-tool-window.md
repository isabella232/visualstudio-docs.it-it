---
title: Aggiunta di una finestra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ee669d2acd5bc69c7268b19ad04e9fa7b506e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633411"
---
# <a name="add-a-tool-window"></a>Aggiungere una finestra degli strumenti

In questa procedura dettagliata viene illustrato come creare una finestra degli strumenti e integrarla in Visual Studio nei modi seguenti:

- Aggiungere un controllo alla finestra degli strumenti.

- Aggiungere una barra degli strumenti a una finestra degli strumenti.

- Aggiungere un comando alla barra degli strumenti.

- Implementare i comandi.

- Imposta la posizione predefinita per la finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisites

Visual Studio SDK è incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Crea una finestra degli strumenti

1. Creare un progetto denominato **FirstToolWin** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **FirstToolWindow**.

    > [!NOTE]
    > Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Aggiungere un controllo alla finestra degli strumenti

1. Rimuovere il controllo predefinito. Aprire *FirstToolWindowControl. XAML* ed eliminare il **clic su me** . immagini (...).

2. Nella **casella degli strumenti**espandere la **sezione tutti i controlli WPF** e trascinare il controllo **elemento multimediale** sul form **FirstToolWindowControl** . Selezionare il controllo e nella finestra **Proprietà** assegnare un nome a questo elemento **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Aggiungere una barra degli strumenti alla finestra degli strumenti
Con l'aggiunta di una barra degli strumenti nel modo seguente si garantisce che le sfumature e i colori siano coerenti con il resto dell'IDE.

1. In **Esplora soluzioni**aprire *FirstToolWindowPackage. vsct*. Il file con *estensione vsct* definisce gli elementi dell'interfaccia utente grafica (GUI) nella finestra degli strumenti usando XML.

2. Nella sezione `<Symbols>` trovare il nodo `<GuidSymbol>` il cui attributo `name` è `guidFirstToolWindowPackageCmdSet`. Aggiungere i due elementi `<IDSymbol>` seguenti all'elenco di elementi `<IDSymbol>` in questo nodo per definire una barra degli strumenti e un gruppo di barre degli strumenti.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Appena sopra la sezione `<Buttons>` creare una sezione `<Menus>` simile alla seguente:

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

    Sono disponibili diversi tipi di menu. Questo menu è una barra degli strumenti in una finestra degli strumenti, definita dall'attributo `type`. Le impostazioni `guid` e `id` costituiscono l'ID completo della barra degli strumenti. In genere, il `<Parent>` di un menu è il gruppo che lo contiene. Tuttavia, una barra degli strumenti è definita come padre. Lo stesso identificatore viene pertanto usato per gli elementi `<Menu>` e `<Parent>`. L'attributo `priority` è solo ' 0'.

4. Le barre degli strumenti sono simili ai menu in molti modi. Ad esempio, come un menu può avere gruppi di comandi, le barre degli strumenti possono anche avere gruppi. Nei menu i gruppi di comandi sono separati da linee orizzontali. Sulle barre degli strumenti, i gruppi non sono separati dai divisori visivi.

    Aggiungere una sezione di `<Groups>` contenente un elemento di `<Group>`. Definisce il gruppo il cui ID è stato dichiarato nella sezione `<Symbols>`. Aggiungere la sezione `<Groups>` subito dopo la sezione `<Menus>`.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Impostando il GUID e l'ID padre sul GUID e sull'ID della barra degli strumenti, il gruppo viene aggiunto alla barra degli strumenti.

## <a name="add-a-command-to-the-toolbar"></a>Aggiungere un comando alla barra degli strumenti

Aggiungere un comando alla barra degli strumenti, che viene visualizzato come pulsante.

1. Nella sezione `<Symbols>` dichiarare gli elementi IDSymbol seguenti immediatamente dopo la barra degli strumenti e le dichiarazioni di gruppo della barra degli strumenti.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Aggiungere un elemento Button nella sezione `<Buttons>`. Questo elemento verrà visualizzato sulla barra degli strumenti della finestra degli strumenti, con un'icona di **ricerca** (lente di ingrandimento).

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

    Questa operazione rende disponibili i comandi nel codice.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Aggiungere una proprietà MediaPlayer a FirstToolWindowControl
Dai gestori eventi per i controlli della barra degli strumenti, il codice deve essere in grado di accedere al controllo Media Player, che è figlio della classe FirstToolWindowControl.

In **Esplora soluzioni**fare clic con il pulsante destro del mouse su *FirstToolWindowControl. XAML*, scegliere **Visualizza codice**e aggiungere il codice seguente alla classe FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Creare un'istanza della finestra degli strumenti e della barra degli strumenti
Aggiungere una barra degli strumenti e un comando di menu che richiama la finestra di dialogo **Apri file** e riproduce il file multimediale selezionato.

1. Aprire *FirstToolWindow.cs* e aggiungere le direttive `using` seguenti:

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

7. Nella classe FirstToolWindowCommand aggiungere il codice seguente alla fine del Metodo ShowToolWindow (). Il comando ButtonHandler verrà implementato nella sezione successiva.

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

1. Nella classe FirstToolWindowCommand aggiungere un metodo ButtonHandler che richiama la finestra di dialogo **Apri file** . Quando è stato selezionato un file, il file multimediale viene riprodotto.

2. Nella classe FirstToolWindowCommand aggiungere un riferimento privato alla finestra FirstToolWindow che viene creata nel Metodo FindToolWindow ().

    ```csharp
    private FirstToolWindow window;
    ```

3. Modificare il metodo ShowToolWindow () per impostare la finestra definita in precedenza, in modo che il gestore di comandi ButtonHandler possa accedere al controllo finestra. Ecco il metodo ShowToolWindow () completo.

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

4. Aggiungere il metodo ButtonHandler. Viene creato un oggetto OpenFileDialog che consente all'utente di specificare il file multimediale da riprodurre, quindi riproduce il file selezionato.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Imposta la posizione predefinita per la finestra degli strumenti

Specificare quindi un percorso predefinito nell'IDE per la finestra degli strumenti. Le informazioni di configurazione per la finestra degli strumenti si trova nel file *FirstToolWindowPackage.cs* .

1. In *FirstToolWindowPackage.cs*trovare l'attributo <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> nella classe `FirstToolWindowPackage`, che passa il tipo FirstToolWindow al costruttore. Per specificare una posizione predefinita, è necessario aggiungere altri parametri al costruttore che segue l'esempio.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Il primo parametro denominato è `Style` e il relativo valore è `Tabbed`, il che significa che la finestra sarà una scheda in una finestra esistente. La posizione di ancoraggio viene specificata dal parametro `Window`, n questo caso, il GUID della **Esplora soluzioni**.

    > [!NOTE]
    > Per ulteriori informazioni sui tipi di finestre nell'IDE, vedere <xref:EnvDTE.vsWindowType>.

## <a name="test-the-tool-window"></a>Testare la finestra degli strumenti

1. Premere **F5** per aprire una nuova istanza della compilazione sperimentale di Visual Studio.

2. Scegliere **altre finestre** dal menu **Visualizza** , quindi fare clic su **prima finestra degli strumenti**.

    La finestra degli strumenti Media Player dovrebbe aprirsi nella stessa posizione del **Esplora soluzioni**. Se ancora viene visualizzato nella stessa posizione di prima, reimpostare il layout della finestra (**finestra/Reimposta layout finestra**).

3. Fare clic sul pulsante con l'icona di **ricerca** nella finestra degli strumenti. Selezionare un file audio o video supportato, ad esempio *C:\Windows\Media\chimes.wav*, quindi fare clic su **Apri**.

    Si dovrebbe sentire il suono del campanello.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
