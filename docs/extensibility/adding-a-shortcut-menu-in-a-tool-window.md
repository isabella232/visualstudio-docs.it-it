---
title: Aggiunta di un Menu di scelta rapida in una finestra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36df685197acbac4372daa8f8c813acf22357678
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309942"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Aggiungere un menu di scelta rapida in una finestra degli strumenti
Questa procedura dettagliata inserisce un menu di scelta rapida in una finestra degli strumenti. Un menu di scelta rapida è un menu che viene visualizzato quando l'utente fa clic sul pulsante, casella di testo un sfondo della finestra. I comandi in un menu di scelta rapida si comportano come i comandi su altri menu o barre degli strumenti. Per supportare un menu di scelta rapida, specificarlo nella *vsct* file e visualizzarli in risposta al pulsante destro del mouse del mouse.

Una finestra degli strumenti è costituito da un controllo utente WPF in una classe della finestra degli strumenti personalizzata che eredita da <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.

Questa procedura dettagliata illustra come creare un menu di scelta rapida come un menu di Visual Studio, con la dichiarazione di voci di menu la *vsct* file e quindi usando il Framework di pacchetto gestito per la relativa implementazione nella classe che definisce la finestra degli strumenti. Questo approccio semplifica l'accesso a comandi di Visual Studio, gli elementi dell'interfaccia utente e il modello oggetto di automazione.

In alternativa, se il menu di scelta rapida non accederanno funzionalità di Visual Studio, è possibile usare il <xref:System.Windows.FrameworkElement.ContextMenu%2A> proprietà di un elemento XAML nel controllo utente. Per altre informazioni, vedere [sull'oggetto ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Prerequisiti
A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Creare il pacchetto di menu scelta rapida finestra degli strumenti

1. Creare un progetto VSIX denominato `TWShortcutMenu` e aggiungere un modello di finestra degli strumenti denominato **menu scelta rapida** ad esso. Per altre informazioni sulla creazione di una finestra degli strumenti, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Specifica il menu di scelta rapida
Un menu di scelta rapida, ad esempio quella illustrata in questa procedura dettagliata consente all'utente di selezionare da un elenco di colori utilizzati per riempire lo sfondo della finestra degli strumenti.

1. Nelle *ShortcutMenuPackage.vsct*, trovare nell'elemento GuidSymbol denominato guidShortcutMenuPackageCmdSet e dichiarare il menu di scelta rapida, il gruppo di menu di scelta rapida e le opzioni di menu. L'elemento GuidSymbol dovrebbe ora essere simile al seguente:

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

2. Appena prima dell'elemento di pulsanti, creare un elemento del menu di scelta e quindi definire il menu di scelta rapida in esso.

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

    Un menu di scelta rapida non è un elemento padre perché non fa parte di un menu o sulla barra degli strumenti.

3. Creare un elemento di gruppi con un elemento di gruppo che contiene le voci di menu di scelta rapida e associare il gruppo di menu di scelta rapida.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Nell'elemento pulsanti, definire i singoli comandi che verranno visualizzato il menu di scelta rapida. L'elemento pulsanti dovrebbe essere simile al seguente:

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

5. Nelle *ShortcutMenuCommand.cs*, aggiungere le definizioni per il comando del set di GUID, il menu di scelta rapida e le voci di menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Questi sono gli stessi ID di comando che sono definiti nella sezione Symbols del *ShortcutMenuPackage.vsct* file. Il gruppo di contesto non è incluso qui perché è necessaria solo il *vsct* file.

## <a name="implementing-the-shortcut-menu"></a>Implementazione di menu di scelta rapida
 In questa sezione implementa il menu di scelta rapida e i relativi comandi.

1. Nelle *ShortcutMenu.cs*, la finestra degli strumenti è possibile ottenere il servizio di comando di menu, ma non è il controllo che contiene. La procedura seguente illustra come rendere disponibili per il controllo utente servizio dei comandi di menu.

2. Nelle *ShortcutMenu.cs*, aggiungere quanto segue usando istruzioni:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Eseguire l'override di metodo Initialize () della finestra degli strumenti per ottenere il servizio di comando di menu e aggiungere il controllo, passando il servizio di comando di menu al costruttore:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Nel costruttore di finestra degli strumenti del menu scelta rapida, rimuovere la riga che aggiunge il controllo. Il costruttore a questo punto dovrebbe essere simile al seguente:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. Nelle *ShortcutMenuControl.xaml.cs*, aggiungere un campo privato per il servizio di comando di menu e modificare il costruttore di controllo per sfruttare il servizio di comando di menu. Usare quindi il servizio di comando di menu per aggiungere i comandi di menu di scelta rapida. Il costruttore ShortcutMenuControl deve ora apparire simile al codice seguente. Il gestore del comando verrà definito in un secondo momento.

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

6. Nelle *ShortcutMenuControl.xaml*, aggiungere un <xref:System.Windows.UIElement.MouseRightButtonDown> evento nel livello superiore <xref:System.Windows.Controls.UserControl> elemento. Il file XAML dovrebbe ora essere simile al seguente:

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

7. Nelle *ShortcutMenuControl.xaml.cs*, aggiungere uno stub per il gestore dell'evento.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Aggiungere quanto segue usando istruzioni nello stesso file:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implementare il `MyToolWindowMouseRightButtonDown` evento come indicato di seguito.

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

    Ciò consente di creare un <xref:System.ComponentModel.Design.CommandID> oggetto per il menu di scelta rapida, identifica la posizione di clic del mouse e consente di aprire il menu di scelta rapida in tale percorso usando il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> (metodo).

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

    In questo caso, un solo metodo gestisce gli eventi per tutte le voci di menu identificando il <xref:System.ComponentModel.Design.CommandID> e impostando il colore di sfondo di conseguenza. Se le voci di menu conteneva comandi non correlati, si sarebbe stato creato un gestore di evento separato per ogni comando.

## <a name="test-the-tool-window-features"></a>Testare la funzionalità della finestra degli strumenti

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Nell'istanza sperimentale, fare clic su **Vista / Windows Other**, quindi fare clic su **menu scelta rapida**. In questo modo, dovrebbe essere visualizzata la finestra degli strumenti.

3. Pulsante destro del mouse all'interno della finestra degli strumenti. Deve essere visualizzato un menu di scelta rapida che include un elenco di colori.

4. Fare clic su un colore menu di scelta rapida. Il colore di sfondo finestra degli strumenti deve essere modificato in colore selezionato.

## <a name="see-also"></a>Vedere anche
- [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)
