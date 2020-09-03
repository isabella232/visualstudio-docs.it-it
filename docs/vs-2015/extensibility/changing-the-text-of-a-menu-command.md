---
title: Modifica del testo di un comando di menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184488"
---
# <a name="changing-the-text-of-a-menu-command"></a>Modifica del testo di un comando di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nei passaggi seguenti viene illustrato come modificare l'etichetta di testo di un comando di menu utilizzando il <xref:System.ComponentModel.Design.IMenuCommandService> servizio.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Modifica di un'etichetta del comando di menu con IMenuCommandService  
  
1. Creare un progetto VSIX denominato `MenuText` con un comando di menu denominato **ChangeMenuText**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Nel file con estensione vstc aggiungere il `TextChanges` flag al comando di menu, come illustrato nell'esempio seguente.  
  
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
  
3. Nel file ChangeMenuText.cs creare un gestore eventi che verrà chiamato prima di visualizzare il comando di menu.  
  
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
  
5. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.  
  
6. Nel menu **strumenti** dovrebbe essere visualizzato un comando denominato **Invoke ChangeMenuText**.  
  
7. Fare clic sul comando. Verrà visualizzata la finestra di messaggio che annuncia che è stato chiamato MenuItemCallback. Quando si chiude la finestra di messaggio, si noterà che il nome del comando nel menu strumenti è ora **nuovo testo**.
