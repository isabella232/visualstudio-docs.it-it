---
title: Scrittura in User Impostazioni Store | Microsoft Docs
description: Informazioni su come aggiungere Blocco note a Visual Studio come strumento esterno leggendo e scrivendo nell'archivio delle impostazioni utente usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b27796000919336e2585d5b3e7c288a88abe261f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028345"
---
# <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente
Le impostazioni utente sono impostazioni scrivibili come quelle nella finestra di **dialogo Strumenti/Opzioni,** nelle finestre delle proprietà e in alcune altre finestre di dialogo. Visual Studio estensioni possono usarle per archiviare piccole quantità di dati. Questa procedura dettagliata illustra come aggiungere Blocco note a Visual Studio come strumento esterno leggendo e scrivendo nell'archivio delle impostazioni utente.

## <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente

1. Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand. Per altre informazioni su come creare un comando personalizzato, vedere [Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

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

4. Verificare ora se Blocco note è già impostato come strumento esterno. È necessario scorrere tutti gli strumenti esterni per determinare se l'impostazione di ToolCmd è "Blocco note", come indicato di seguito:

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

6. Testare il codice. Tenere presente che aggiunge Blocco note come strumento esterno, quindi è necessario eseguire il rollback del Registro di sistema prima di eseguire il registro una seconda volta.

7. Compilare il codice e avviare il debug.

8. Scegliere **Richiama** **UserSettingsStoreCommand** dal menu Strumenti . Questo aggiungerà Blocco note **al** menu Strumenti.

9. A questo punto, Blocco note nel menu Strumenti/Opzioni e facendo clic su Blocco note **verrà** visualizzata un'istanza di Blocco note.
