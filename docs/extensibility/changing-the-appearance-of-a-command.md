---
title: Modifica dell'aspetto di un comando Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739859"
---
# <a name="change-the-appearance-of-a-command"></a>Modificare l'aspetto di un comando
È possibile fornire commenti e suggerimenti all'utente modificando l'aspetto di un comando. Ad esempio, è possibile che si desideri che un comando abbia un aspetto diverso quando non è disponibile. È possibile rendere i comandi disponibili o non disponibili, nasconderli o visualizzarli oppure selezionarli o deselezionarli nel menu.

Per modificare l'aspetto di un comando, effettuare una delle seguenti operazioni:

- Specificare i flag appropriati nella definizione del comando nel file della tabella dei comandi.

- Utilizzare <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> il servizio.

- Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e modificare gli oggetti comando non elaborati.

  La procedura seguente viene illustrato come trovare e aggiornare l'aspetto di un comando utilizzando il Framework di pacchetto gestito (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Per modificare l'aspetto di un comando di menu

1. Seguire le istruzioni in [Modificare il testo di un comando di menu](../extensibility/changing-the-text-of-a-menu-command.md) per creare una voce di menu denominata `New Text`.

2. Nel file *ChangeMenuText.cs* aggiungere l'istruzione using seguente:

    ```csharp
    using System.Security.Permissions;
    ```

3. Nel file *ChangeMenuTextPackageGuids.cs* aggiungere la riga seguente:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. Nel file *ChangeMenuText.cs* sostituire il codice nel metodo ShowMessageBox con quanto segue:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Ottenere il comando che si <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> desidera aggiornare dall'oggetto e quindi impostare le proprietà appropriate sull'oggetto comando. Ad esempio, il metodo seguente rende il comando specificato da un set di comandi VSPackage disponibile o non disponibile. Il codice seguente rende `New Text` non disponibile la voce di menu denominata dopo che è stata fatta clic.

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
        return cmdUpdated;
    }
    ```

6. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio should appear.

7. Scegliere il comando **Richiama ChangeMenuText** dal menu **Strumenti** . A questo punto il nome del comando è **Invoke ChangeMenuText**, pertanto il gestore del comando non chiama **ChangeMyCommand()**.

8. Nel menu **Strumenti** dovrebbe essere visualizzato **Nuovo testo**. Fare clic su **Nuovo testo**. Il comando dovrebbe ora essere disattivato.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Tabella dei comandi di Visual Studio (. Vsct) File](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
