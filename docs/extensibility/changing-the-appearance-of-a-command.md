---
title: Modifica dell'aspetto di un comando | Microsoft Docs
description: Informazioni su come fornire commenti e suggerimenti per modificare l'aspetto di un comando, ad esempio rendere i comandi disponibili/non disponibili, nascosti/visualizzati o selezionati/deselezionati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddeed08d7bc33b9a9ae5405876f3b28459d4eaf2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905033"
---
# <a name="change-the-appearance-of-a-command"></a>Modificare l'aspetto di un comando
È possibile inviare commenti e suggerimenti all'utente modificando l'aspetto di un comando. Ad esempio, è possibile che un comando sia diverso quando non è disponibile. È possibile rendere i comandi disponibili o non disponibili, nasconderli o mostrarli oppure selezionare o deselezionarli nel menu.

Per modificare l'aspetto di un comando, eseguire una di queste azioni:

- Specificare i flag appropriati nella definizione del comando nel file della tabella dei comandi.

- Usare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> servizio .

- Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e modificare gli oggetti comando non elaborati.

  La procedura seguente illustra come trovare e aggiornare l'aspetto di un comando usando Managed Package Framework (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Per modificare l'aspetto di un comando di menu

1. Seguire le istruzioni in [Modificare il testo di un comando di menu per](../extensibility/changing-the-text-of-a-menu-command.md) creare una voce di menu denominata `New Text` .

2. Nel file *ChangeMenuText.cs* aggiungere l'istruzione using seguente:

    ```csharp
    using System.Security.Permissions;
    ```

3. Nel file *ChangeMenuTextPackageGuids.cs* aggiungere la riga seguente:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. Nel file *ChangeMenuText.cs* sostituire il codice nel metodo ShowMessageBox con il codice seguente:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Ottenere il comando che si vuole aggiornare <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> dall'oggetto e quindi impostare le proprietà appropriate sull'oggetto comando. Ad esempio, il metodo seguente rende disponibile o non disponibile il comando specificato da un set di comandi VSPackage. Il codice seguente rende la voce di menu denominata `New Text` non disponibile dopo che è stata selezionata.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
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

6. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza Visual Studio sperimentale.

7. Scegliere **Richiama** **ChangeMenuText** dal menu Strumenti. A questo punto il nome del comando **è Invoke ChangeMenuText**, quindi il gestore del comando non chiama **ChangeMyCommand().**

8. Nel menu **Strumenti** dovrebbe essere visualizzato Nuovo **testo.** Fare clic **su Nuovo testo**. Il comando dovrebbe ora essere disattivato.

## <a name="see-also"></a>Vedere anche
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)
- [Visual Studio tabella dei comandi (. Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
