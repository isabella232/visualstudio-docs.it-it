---
title: Modifica dell'aspetto di un comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4741059410e052c571d77088b9cbe109fb651642
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184499"
---
# <a name="changing-the-appearance-of-a-command"></a>Modifica dell'aspetto di un comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire commenti e suggerimenti all'utente modificando l'aspetto di un comando. Ad esempio, è possibile che un comando abbia un aspetto diverso quando non è disponibile. È possibile rendere i comandi disponibili o non disponibili, nasconderli o visualizzarli oppure selezionarli o deselezionarli nel menu.  
  
 Per modificare l'aspetto di un comando, eseguire una delle operazioni seguenti:  
  
- Specificare i flag appropriati nella definizione del comando nel file della tabella dei comandi.  
  
- Usare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> servizio.  
  
- Implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia e modificare gli oggetti comando non elaborati.  
  
  Nei passaggi seguenti viene illustrato come trovare e aggiornare l'aspetto di un comando tramite il Framework di pacchetto gestito (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Per modificare l'aspetto di un comando di menu  
  
1. Seguire le istruzioni riportate in [modifica del testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md) per creare una voce di menu denominata `New Text` .  
  
2. Nel file ChangeMenuText.cs aggiungere l'istruzione using seguente:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3. Nel file ChangeMenuTextPackageGuids.cs aggiungere la riga seguente:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4. Nel file ChangeMenuText.cs sostituire il codice nel metodo Metodo ShowMessageBox con il codice seguente:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5. Ottenere il comando che si desidera aggiornare dall' <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> oggetto, quindi impostare le proprietà appropriate sull'oggetto Command. Il metodo seguente, ad esempio, rende disponibile o non disponibile il comando specificato da un set di comandi VSPackage. Il codice seguente rende la voce di menu denominata `New Text` non disponibile dopo che è stato selezionato.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.  
  
7. Scegliere il comando **richiama ChangeMenuText** dal menu **strumenti** . A questo punto il nome del comando è **Invoke ChangeMenuText**, quindi il gestore di comando non chiama ChangeMyCommand ().  
  
8. Nel menu **strumenti** dovrebbe ora essere visualizzato **nuovo testo**. Fare clic su **nuovo testo**. Il comando dovrebbe ora essere disattivato.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
