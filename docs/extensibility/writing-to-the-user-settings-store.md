---
title: Scrittura nell'archivio impostazioni utente | Microsoft Docs
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec4d9cdda975d0f80e9d8523ec18a19c24c9418a
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906212"
---
# <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente
Le impostazioni utente sono impostazioni scrivibili come quelle nella finestra di dialogo **Strumenti/Opzioni** , finestre proprietà e alcune altre finestre di dialogo. Le estensioni di Visual Studio possono usarle per archiviare piccole quantità di dati. Questa procedura dettagliata illustra come aggiungere il blocco note a Visual Studio come strumento esterno leggendo e scrivendo nell'archivio impostazioni utente.

## <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente

1. Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. In UserSettingsStoreCommand.cs aggiungere le direttive using seguenti:

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

4. Verificare ora se il blocco note è già impostato come strumento esterno. È necessario scorrere tutti gli strumenti esterni per determinare se l'impostazione ToolCmd è "blocco note", come indicato di seguito:

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

5. Se il blocco note non è stato impostato come strumento esterno, impostarlo come segue:

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

6. Testare il codice. Tenere presente che aggiunge il blocco note come strumento esterno, quindi è necessario eseguire il rollback del registro di sistema prima di eseguirlo una seconda volta.

7. Compilare il codice e avviare il debug.

8. Scegliere **richiama UserSettingsStoreCommand**dal menu **strumenti** . Il blocco note verrà aggiunto al menu **strumenti** .

9. A questo punto, il blocco note verrà visualizzato nel menu Strumenti/Opzioni e facendo clic su **blocco note** verrà visualizzata un'istanza del blocco note.
