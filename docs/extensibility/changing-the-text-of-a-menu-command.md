---
title: Modifica del testo di un comando di menu | Microsoft Docs
description: Per informazioni su come modificare l'etichetta di testo di un comando di menu usando il servizio IMenuCommandService, vedere questo esempio di codice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47389352e0491c20b7eb6409c36091179bf967d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068063"
---
# <a name="change-the-text-of-a-menu-command"></a>Modificare il testo di un comando di menu
Nei passaggi seguenti viene illustrato come modificare l'etichetta di testo di un comando di menu utilizzando il <xref:System.ComponentModel.Design.IMenuCommandService> servizio.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Modifica di un'etichetta del comando di menu con IMenuCommandService

1. Creare un progetto VSIX denominato `MenuText` con un comando di menu denominato **ChangeMenuText**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Nel file con *estensione vsct* aggiungere il `TextChanges` flag al comando di menu, come illustrato nell'esempio seguente.

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

3. Nel file *ChangeMenuText. cs* creare un gestore eventi che verrà chiamato prima di visualizzare il comando di menu.

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

    È inoltre possibile aggiornare lo stato del comando di menu in questo metodo modificando le <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> proprietà, e <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> per l' <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> oggetto.

4. Nel costruttore ChangeMenuText sostituire il codice di inizializzazione e posizionamento del comando originale con il codice che crea un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anziché un `MenuCommand` ) che rappresenta il comando di menu, aggiunge il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore eventi e assegna il comando di menu al servizio comando di menu.

    Di seguito è riportato un aspetto simile al seguente:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.

6. Nel menu **strumenti** dovrebbe essere visualizzato un comando denominato **Invoke ChangeMenuText**.

7. Fare clic sul comando. Verrà visualizzata la finestra di messaggio che annuncia che è stato chiamato **MenuItemCallback** . Quando si chiude la finestra di messaggio, si noterà che il nome del comando nel menu strumenti è ora **nuovo testo**.
