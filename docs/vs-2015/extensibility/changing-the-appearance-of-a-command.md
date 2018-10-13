---
title: Modifica dell'aspetto di un comando | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 832a6732789d8e218a739b03fb5aa6541ec8276f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294723"
---
# <a name="changing-the-appearance-of-a-command"></a>Modifica dell'aspetto di un comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile fornire feedback all'utente modificando l'aspetto di un comando. Ad esempio, è possibile che un comando in modo diverso quando non è disponibile. È possibile rendere i comandi disponibili o non, nascondere o visualizzarli, o selezionare o deselezionare li nel menu.  
  
 Per modificare l'aspetto di un comando, eseguire una di queste azioni:  
  
-   Specifica i flag appropriati nella definizione di comando nel file della tabella comandi.  
  
-   Usare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> servizio.  
  
-   Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e modificare gli oggetti comando non elaborati.  
  
 La procedura seguente illustra come trovare e aggiornare l'aspetto di un comando usando il Framework di pacchetto gestito (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Per modificare l'aspetto di un comando di menu  
  
1.  Seguire le istruzioni in [modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md) per creare una voce di menu denominato `New Text`.  
  
2.  Nel file ChangeMenuText.cs, aggiungere la seguente istruzione using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  Nel file ChangeMenuTextPackageGuids.cs, aggiungere la riga seguente:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Nel file ChangeMenuText.cs, sostituire il codice nel metodo ShowMessageBox con gli elementi seguenti:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Ottenere il comando che si vuole aggiornare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> dell'oggetto e quindi impostare le proprietà appropriate per l'oggetto comando. Ad esempio, il metodo seguente rende il comando specificato da un comando VSPackage set disponibile o non disponibile. Il codice seguente effettua il voce di menu denominata `New Text` disponibile dopo che è stato fatto clic.  
  
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
  
6.  Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato.  
  
7.  Nel **degli strumenti** dal menu fare clic sul **ChangeMenuText richiamare** comando. A questo punto è il nome del comando **richiamare ChangeMenuText**, in modo che il gestore del comando non chiama ChangeMyCommand().  
  
8.  Nel **degli strumenti** menu si noterà ora **nuovo testo**. Fare clic su **nuovo testo**. Il comando dovrebbe ora essere disabilitato.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

