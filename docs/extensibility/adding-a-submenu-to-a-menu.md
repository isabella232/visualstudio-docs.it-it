---
title: Aggiunta di un sottomenu a un menu | Microsoft Docs
description: Informazioni su come creare un sottomenu, aggiungerlo alla barra Visual Studio e aggiungere un nuovo comando al sottomenu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ebd3a4d97d19977b8a97ff7fcb2a545654f4165
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065189"
---
# <a name="add-a-submenu-to-a-menu"></a>Aggiungere un sottomenu a un menu
Questa procedura dettagliata si basa sulla dimostrazione in Aggiungere un menu alla barra [dei menu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) illustrando come aggiungere un sottomenu al menu **TestMenu.**

 Un sottomenu è un menu secondario visualizzato in un altro menu. Un sottomenu può essere identificato dalla freccia che segue il nome. Se si fa clic sul nome, vengono visualizzati il sottomenu e i relativi comandi.

 Questa procedura dettagliata crea un sottomenu in un menu Visual Studio barra dei menu e inserisce un nuovo comando nel sottomenu. La procedura dettagliata implementa anche il nuovo comando .

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="add-a-submenu-to-a-menu"></a>Aggiungere un sottomenu a un menu

1. Seguire la procedura descritta in [Aggiungere un menu alla barra Visual Studio menu per](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) creare il progetto e la voce di menu. I passaggi di questa procedura dettagliata presuppongono che il nome del progetto VSIX sia `TopLevelMenu` .

2. Aprire *TestCommandPackage.vsct.* Nella sezione aggiungere un elemento per il sottomenu, uno per il gruppo di sottomenu e uno per il comando, il tutto nel nodo `<Symbols>` `<IDSymbol>` denominato `<GuidSymbol>` "guidTopLevelMenuCmdSet". Si tratta dello stesso nodo che contiene `<IDSymbol>` l'elemento per il menu di primo livello.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Aggiungere il sottomenu appena creato alla `<Menus>` sezione .

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     La coppia GUID/ID dell'elemento padre specifica il gruppo di menu generato in Aggiungi un menu alla barra dei menu di [Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)ed è un elemento figlio del menu di primo livello.

4. Aggiungere il gruppo di menu definito nel passaggio 2 alla sezione e renderlo `<Groups>` figlio del sottomenu.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Aggiungere un `<Button>` nuovo elemento alla sezione per definire il comando creato nel passaggio `<Buttons>` 2 come elemento nel sottomenu.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Compilare la soluzione e avviare il debug. Verrà visualizzata l'istanza sperimentale.

7. Fare **clic su TestMenu** per visualizzare un nuovo sottomenu denominato **Sottomenu.** Fare **clic su Sottomenu** per aprire il sottomenu e visualizzare un nuovo comando, **Test Sub Command**. Si noti che facendo clic **su Test Sub Command** non viene eseguito alcun comando.

## <a name="add-a-command"></a>Aggiungere un comando

1. Aprire *TestCommand.cs e* aggiungere l'ID comando seguente dopo l'ID comando esistente.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Aggiungere il sotto-comando. Trovare il costruttore del comando. Aggiungere le righe seguenti subito dopo la chiamata al `AddCommand` metodo .

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Il `SubItemCallback` gestore comandi verrà definito in un secondo momento. Il costruttore dovrebbe ora essere simile al seguente:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Aggiungere `SubItemCallback()`. Si tratta del metodo chiamato quando si fa clic sul nuovo comando nel sottomenu.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

5. Scegliere **Sottomenu** dal menu **TestMenu** e quindi fare clic **su Comando secondario di test.** Dovrebbe essere visualizzata una finestra di messaggio con il testo "Test Command Inside TestCommand.SubItemCallback()".

## <a name="see-also"></a>Vedi anche

- [Aggiungere un menu alla barra Visual Studio menu](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
