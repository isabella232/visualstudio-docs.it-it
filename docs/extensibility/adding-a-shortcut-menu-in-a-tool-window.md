---
title: Aggiunta di un menu di scelta rapida in una finestra degli strumenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740289"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Aggiungere un menu di scelta rapida in una finestra degli strumenti
Questa procedura dettagliata inserisce un menu di scelta rapida in una finestra degli strumenti. Un menu di scelta rapida è un menu che viene visualizzato quando un utente fa clic con il pulsante destro del mouse su un pulsante, una casella di testo o lo sfondo di una finestra. I comandi di un menu di scelta rapida hanno lo stesso modo dei comandi di altri menu o barre degli strumenti. Per supportare un menu di scelta rapida, specificarlo nel file *vsct* e visualizzarlo in risposta al clic con il pulsante destro del mouse.

Una finestra degli strumenti è costituita da un controllo <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>utente WPF in una classe della finestra degli strumenti personalizzata che eredita da .

In questa procedura dettagliata viene illustrato come creare un menu di scelta rapida come menu di Visual Studio, dichiarando le voci di menu nel file *vsct* e quindi utilizzando il Framework di pacchetto gestito per implementarli nella classe che definisce la finestra degli strumenti. Questo approccio facilita l'accesso ai comandi di Visual Studio, agli elementi dell'interfaccia utente e al modello a oggetti di automazione.

In alternativa, se il menu di scelta rapida non <xref:System.Windows.FrameworkElement.ContextMenu%2A> accederà alle funzionalità di Visual Studio, è possibile usare la proprietà di un elemento XAML nel controllo utente. Per ulteriori informazioni, vedere [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Prerequisiti
A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-tool-window-shortcut-menu-package"></a>Creare il pacchetto del menu di scelta rapida della finestra degli strumentiCreate the tool window shortcut menu package

1. Creare un progetto `TWShortcutMenu` VSIX denominato e aggiungervi un modello di finestra degli strumenti denominato **ShortcutMenu.Create** a VSIX project named and add a tool window template named ShortcutMenu to it. Per ulteriori informazioni sulla creazione di una finestra degli strumenti, consultate [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="specifying-the-shortcut-menu"></a>Specifica del menu di scelta rapida
Un menu di scelta rapida come quello illustrato in questa procedura dettagliata consente all'utente di selezionare da un elenco di colori utilizzati per riempire lo sfondo della finestra degli strumenti.

1. In *ShortcutMenuPackage.vsct*individuare l'elemento GuidSymbol denominato guidShortcutMenuPackageCmdSet e dichiarare le opzioni del menu di scelta rapida, del gruppo di menu di scelta rapida e del menu di scelta rapida. L'elemento GuidSymbol dovrebbe essere simile al seguente:The GuidSymbol element should now look like this:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Appena prima di Buttons elemento, creare un Menus elemento e quindi definire il menu di scelta rapida in esso.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Un menu di scelta rapida non dispone di un elemento padre perché non fa parte di un menu o di una barra degli strumenti.

3. Creare un Groups elemento con un Group elemento che contiene le voci di menu di scelta rapida e associare il gruppo con il menu di scelta rapida.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Nell'elemento Buttons definire i singoli comandi che verranno visualizzati nel menu di scelta rapida. L'elemento Buttons dovrebbe essere simile al seguente:The Buttons element should look like this:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. In *ShortcutMenuCommand.cs*, aggiungere le definizioni per il GUID del set di comandi, il menu di scelta rapida e le voci di menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Si tratta degli stessi ID di comando definiti nella sezione Symbols del file *ShortcutMenuPackage.vsct.* Il gruppo di contesto non è incluso qui perché è necessario solo nel file *vsct.*

## <a name="implementing-the-shortcut-menu"></a>Implementazione del menu di scelta rapida
 Questa sezione implementa il menu di scelta rapida e i relativi comandi.

1. In *ShortcutMenu.cs*, la finestra degli strumenti può ottenere il servizio di comando di menu, ma il controllo che contiene non può. I passaggi seguenti illustrano come rendere il servizio di comando di menu disponibile per il controllo utente.

2. In *ShortcutMenu.cs*, aggiungere le direttive using seguenti:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Eseguire l'override del metodo Initialize() della finestra degli strumenti per ottenere il servizio dei comandi di menu e aggiungere il controllo, passando il servizio dei comandi di menu al costruttore:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Nel costruttore della finestra degli strumenti ShortcutMenu, rimuovere la riga che aggiunge il controllo. Il costruttore dovrebbe ora essere simile al seguente:The constructor should now look like this:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. In *ShortcutMenuControl.xaml.cs*, aggiungere un campo privato per il servizio di comando di menu e modificare il costruttore del controllo per eseguire il servizio di comando di menu. Utilizzare quindi il servizio di comando di menu per aggiungere i comandi del menu di scelta rapida. Il ShortcutMenuControl costruttore dovrebbe ora essere simile al codice seguente. Il gestore del comando verrà definito in un secondo momento.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. In *ShortcutMenuControl.xaml*aggiungere <xref:System.Windows.UIElement.MouseRightButtonDown> un evento <xref:System.Windows.Controls.UserControl> all'elemento di primo livello. Il file XAML dovrebbe essere simile al seguente:The XAML file should now look like this:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. In *ShortcutMenuControl.xaml.cs*aggiungere uno stub per il gestore eventi.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Aggiungere le seguenti direttive using allo stesso file:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implementare `MyToolWindowMouseRightButtonDown` l'evento come indicato di seguito.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    In questo <xref:System.ComponentModel.Design.CommandID> modo viene creato un oggetto per il menu di scelta rapida, viene <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> identificata la posizione del clic del mouse e viene aperto il menu di scelta rapida in tale posizione utilizzando il metodo .

10. Implementare il gestore del comando.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    In questo caso, solo un metodo gestisce gli eventi <xref:System.ComponentModel.Design.CommandID> per tutte le voci di menu identificando il e impostando il colore di sfondo di conseguenza. Se le voci di menu fossero contenute comandi non correlati, si sarebbe creato un gestore eventi separato per ogni comando.

## <a name="test-the-tool-window-features"></a>Testare le funzionalità della finestra degli strumenti

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Nell'istanza sperimentale fare clic su **Visualizza/Altre finestre**, quindi su **ShortcutMenu**. In questo modo dovrebbe essere visualizzata la finestra degli strumenti.

3. Fare clic con il pulsante destro del mouse nel corpo della finestra degli strumenti. Deve essere visualizzato un menu di scelta rapida con un elenco di colori.

4. Fare clic su un colore nel menu di scelta rapida. Il colore di sfondo della finestra degli strumenti deve essere modificato nel colore selezionato.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Utilizzo e fornitura di servizi](../extensibility/using-and-providing-services.md)
