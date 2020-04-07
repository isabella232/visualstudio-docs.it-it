---
title: Modifica del testo di un comando di menu Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739837"
---
# <a name="change-the-text-of-a-menu-command"></a>Modificare il testo di un comando di menu
La procedura seguente illustra come modificare l'etichetta di <xref:System.ComponentModel.Design.IMenuCommandService> testo di un comando di menu utilizzando il servizio.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Modifica dell'etichetta di un comando di menu con IMenuCommandService

1. Creare un progetto `MenuText` VSIX denominato con un comando di menu denominato **ChangeMenuText**. Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

2. Nel file *vsct* aggiungere `TextChanges` il flag al comando di menu, come illustrato nell'esempio seguente.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. Nel file *ChangeMenuText.cs* creare un gestore eventi che verrà chiamato prima che venga visualizzato il comando di menu.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    È inoltre possibile aggiornare lo stato del comando <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>di <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> menu in <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> questo metodo modificando le proprietà , e sull'oggetto .

4. Nel ChangeMenuText costruttore, sostituire il codice di inizializzazione <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e posizionamento del comando originale con il codice che crea un (anziché un `MenuCommand`) che rappresenta il comando di menu, aggiunge il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore eventi e dà il comando di menu al servizio di comando di menu.

    Ecco come dovrebbe apparire:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio appears.

6. Nel menu **Strumenti** verrà visualizzato un comando denominato **Richiama ChangeMenuText**.

7. Fare clic sul comando. Verrà visualizzata la finestra di messaggio che annuncia che **MenuItemCallback** è stato chiamato. Quando si chiude la finestra di messaggio, si note che il nome del comando del menu Strumenti è ora **Nuovo testo**.
