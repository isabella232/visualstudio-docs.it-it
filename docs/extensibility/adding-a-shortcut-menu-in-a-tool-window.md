---
title: Aggiunta di un menu di scelta rapida in una finestra degli strumenti | Microsoft Docs
description: Informazioni su come aggiungere un menu di scelta rapida a una finestra degli strumenti Visual Studio visualizzata quando si fa clic con il pulsante destro del mouse su un pulsante, una casella di testo o uno sfondo della finestra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d698b0e3ee5e2c629e7d9cc1c1415b40bfbe176208cb87e1f5ee14a2e9a8c3ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435114"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Aggiungere un menu di scelta rapida in una finestra degli strumenti
Questa procedura dettagliata inserisce un menu di scelta rapida in una finestra degli strumenti. Un menu di scelta rapida è un menu che viene visualizzato quando un utente fa clic con il pulsante destro del mouse su un pulsante, una casella di testo o uno sfondo della finestra. I comandi in un menu di scelta rapida si comportano come i comandi in altri menu o barre degli strumenti. Per supportare un menu di scelta rapida, specificarlo nel file con estensione *vsct* e visualizzarlo in risposta al clic con il pulsante destro del mouse.

Una finestra degli strumenti è costituita da un controllo utente WPF in una classe della finestra degli strumenti personalizzata che eredita da <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

Questa procedura dettagliata illustra come creare un menu di scelta rapida come menu Visual Studio, dichiarando le voci di menu nel file con estensione *vsct* e quindi usando Managed Package Framework per implementarle nella classe che definisce la finestra degli strumenti. Questo approccio facilita l'accesso a Visual Studio comandi, elementi dell'interfaccia utente e al modello a oggetti di Automazione.

In alternativa, se il menu di scelta rapida non accede Visual Studio funzionalità, è possibile usare la proprietà di un elemento <xref:System.Windows.FrameworkElement.ContextMenu%2A> XAML nel controllo utente. Per altre informazioni, vedere [ContextMenu.](/dotnet/framework/wpf/controls/contextmenu)

## <a name="prerequisites"></a>Prerequisiti
A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Creare il pacchetto del menu di scelta rapida della finestra degli strumenti

1. Creare un progetto VSIX denominato e aggiungerne un modello di finestra degli strumenti `TWShortcutMenu` denominato **ShortcutMenu.** Per altre informazioni sulla creazione di una finestra degli strumenti, vedere [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Specifica del menu di scelta rapida
Un menu di scelta rapida come quello illustrato in questa procedura dettagliata consente all'utente di selezionare da un elenco di colori usati per riempire lo sfondo della finestra degli strumenti.

1. In *ShortcutMenuPackage.vsct* trovare nell'elemento GuidSymbol denominato guidShortcutMenuPackageCmdSet e dichiarare il menu di scelta rapida, il gruppo di menu di scelta rapida e le opzioni di menu. L'elemento GuidSymbol dovrebbe ora essere simile al seguente:

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

2. Subito prima dell'elemento Buttons, creare un elemento Menus e quindi definirne il menu di scelta rapida.

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

    Un menu di scelta rapida non ha un elemento padre perché non fa parte di un menu o di una barra degli strumenti.

3. Creare un elemento Groups con un elemento Group contenente le voci del menu di scelta rapida e associare il gruppo al menu di scelta rapida.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Nell'elemento Pulsanti definire i singoli comandi che verranno visualizzati nel menu di scelta rapida. L'elemento Buttons dovrebbe essere simile al seguente:

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

5. In *ShortcutMenuCommand.cs* aggiungere le definizioni per il GUID del set di comandi, il menu di scelta rapida e le voci di menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Si tratta degli stessi ID di comando definiti nella sezione Simboli del file *ShortcutMenuPackage.vsct.* Il gruppo di contesto non è incluso qui perché è necessario solo nel file *con estensione vsct.*

## <a name="implementing-the-shortcut-menu"></a>Implementazione del menu di scelta rapida
 Questa sezione implementa il menu di scelta rapida e i relativi comandi.

1. In *ShortcutMenu.cs* la finestra degli strumenti può ottenere il servizio di comando di menu, ma il controllo che contiene non può. La procedura seguente illustra come rendere il servizio di comando di menu disponibile per il controllo utente.

2. In *ShortcutMenu.cs* aggiungere le direttive using seguenti:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Eseguire l'override del metodo Initialize() della finestra degli strumenti per ottenere il servizio di comando di menu e aggiungere il controllo, passando il servizio di comando di menu al costruttore:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Nel costruttore della finestra degli strumenti ShortcutMenu rimuovere la riga che aggiunge il controllo. Il costruttore dovrebbe ora essere simile al seguente:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. In *ShortcutMenuControl.xaml.cs* aggiungere un campo privato per il servizio di comando di menu e modificare il costruttore del controllo per eseguire il servizio di comando di menu. Usare quindi il servizio di comando di menu per aggiungere i comandi del menu di scelta rapida. Il costruttore ShortcutMenuControl dovrebbe ora essere simile al codice seguente. Il gestore dei comandi verrà definito in un secondo momento.

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

6. In *ShortcutMenuControl.xaml* aggiungere un <xref:System.Windows.UIElement.MouseRightButtonDown> evento all'elemento di primo <xref:System.Windows.Controls.UserControl> livello. Il file XAML dovrebbe ora essere simile al seguente:

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

7. In *ShortcutMenuControl.xaml.cs* aggiungere uno stub per il gestore eventi.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Aggiungere le direttive using seguenti allo stesso file:

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

    Viene creato un oggetto per il menu di scelta rapida, viene identificata la posizione del clic del mouse e viene aperto il menu di scelta rapida in tale posizione <xref:System.ComponentModel.Design.CommandID> usando il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metodo .

10. Implementare il gestore dei comandi.

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

    In questo caso, un solo metodo gestisce gli eventi per tutte le voci di menu identificando e impostando il colore <xref:System.ComponentModel.Design.CommandID> di sfondo di conseguenza. Se le voci di menu contenevano comandi non correlati, sarebbe stato creato un gestore eventi separato per ogni comando.

## <a name="test-the-tool-window-features"></a>Testare le funzionalità della finestra degli strumenti

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Nell'istanza sperimentale fare **clic su Visualizza/Windows** e quindi su **ShortcutMenu**. In questo modo verrà visualizzata la finestra degli strumenti.

3. Fare clic con il pulsante destro del mouse nel corpo della finestra degli strumenti. Verrà visualizzato un menu di scelta rapida con un elenco di colori.

4. Fare clic su un colore nel menu di scelta rapida. Il colore di sfondo della finestra degli strumenti deve essere modificato nel colore selezionato.

## <a name="see-also"></a>Vedi anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)
