---
title: Scrittura nell'archivio delle impostazioni utente Documenti Microsoft
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740357"
---
# <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente
Le impostazioni utente sono impostazioni scrivibili come quelle nella finestra di dialogo **Strumenti / Opzioni,** nelle finestre delle proprietà e in alcune altre finestre di dialogo. Le estensioni di Visual Studio possono usarle per archiviare piccole quantità di dati. In questa procedura dettagliata viene illustrato come aggiungere Blocco note a Visual Studio come strumento esterno leggendo e scrivendo nell'archivio delle impostazioni utente.

## <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente

1. Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand.Create a VSIX project named UserSettingsStoreExtension and then add a custom command named UserSettingsStoreCommand. Per altre informazioni su come creare un comando personalizzato, vedere [Creazione di un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) di menuFor more information about how to create a custom command, see Creating an Extension with a Menu Command

2. In UserSettingsStoreCommand.cs, aggiungere le direttive using seguenti:In UserSettingsStoreCommand.cs, add the following using directives:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. In MenuItemCallback eliminare il corpo del metodo e ottenere l'archivio delle impostazioni utente, come indicato di seguito:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Ora scoprire se Blocco note è già impostato come strumento esterno. È necessario scorrere tutti gli strumenti esterni per determinare se l'impostazione ToolCmd è "Notepad", come indicato di seguito:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Se Blocco note non è stato impostato come strumento esterno, impostarlo come segue:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Testare il codice. Tenere presente che aggiunge il Blocco note come strumento esterno, pertanto è necessario eseguire il rollback del Registro di sistema prima di eseguirlo una seconda volta.

7. Compilare il codice e avviare il debug.

8. Scegliere **Richiama UserSettingsStoreCommand**dal menu **Strumenti** . Verrà aggiunto Blocco note al menu **Strumenti.**

9. Ora dovresti vedere Blocco note dal menu Strumenti / Opzioni e facendo clic su **Blocco note** dovrebbe visualizzare un'istanza del Blocco note.
