---
title: Modifica del testo di un comando di Menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71169b711695ee1997d5ed3b2cd95b79aff359aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965495"
---
# <a name="change-the-text-of-a-menu-command"></a>Modificare il testo di un comando di menu
La procedura seguente illustra come modificare l'etichetta di testo di un comando di menu usando la <xref:System.ComponentModel.Design.IMenuCommandService> servizio.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Modificare un'etichetta di comando di menu con l'oggetto IMenuCommandService  
  
1.  Creare un progetto VSIX denominato `MenuText` con un comando di menu denominato **ChangeMenuText**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Nel *vsct* , aggiungere il `TextChanges` flag per il comando di menu, come illustrato nell'esempio seguente.  
  
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
  
3.  Nel *ChangeMenuText.cs* file, creare un gestore eventi che verrà chiamato prima che venga visualizzato il comando di menu.  
  
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
  
     È anche possibile aggiornare lo stato del comando di menu all'interno del metodo modificando la <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, e <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> delle proprietà nel <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> oggetto.  
  
4.  Nel costruttore ChangeMenuText, sostituire il codice di inizializzazione e posizionamento del comando originale con il codice che crea una <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anziché da un `MenuCommand`) che rappresenta il comando di menu, aggiunge il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore eventi e fornisce il menu di scelta comando per il servizio di comando di menu.  
  
     Ecco cosa sarà simile:  
  
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
  
5.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.  
  
6.  Nel **Tools** menu dovrebbe essere un comando denominato **richiamare ChangeMenuText**.  
  
7.  Fare clic sul comando. Si dovrebbe vedere la finestra di messaggio che annuncia **MenuItemCallback** è stato chiamato. Appena si chiude la finestra di messaggio, si noterà che il nome del comando del menu Strumenti è ora **nuovo testo**.
