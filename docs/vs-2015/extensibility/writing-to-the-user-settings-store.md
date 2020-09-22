---
title: Scrittura nell'archivio impostazioni utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839979"
---
# <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le impostazioni utente sono impostazioni scrivibili come quelle nella finestra di dialogo **Strumenti/Opzioni** , finestre proprietà e alcune altre finestre di dialogo. Le estensioni di Visual Studio possono usarle per archiviare piccole quantità di dati. Questa procedura dettagliata illustra come aggiungere il blocco note a Visual Studio come strumento esterno leggendo e scrivendo nell'archivio impostazioni utente.  
  
### <a name="backing-up-your-user-settings"></a>Backup delle impostazioni utente  
  
1. È necessario essere in grado di reimpostare le impostazioni degli strumenti esterni in modo che sia possibile eseguire il debug e ripetere la procedura. A tale scopo, è necessario salvare le impostazioni originali in modo che sia possibile ripristinarle come richiesto.  
  
2. Aprire Regedit.exe.  
  
3. Passare a HKEY_CURRENT_USER strumenti \Software\Microsoft\VisualStudio\14.0Exp\External \\ .  
  
    > [!NOTE]
    > Assicurarsi di esaminare la chiave che contiene \14.0Exp\ e non \ 14,0 \\ . Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni utente si trovano nell'hive del registro di sistema "14.0 Exp".  
  
4. Fare clic con il pulsante destro del mouse sulla sottochiave \External Tools \, quindi scegliere **Esporta**. Assicurarsi che sia selezionato **Branch selezionato** .  
  
5. Salvare il file External Tools. reg risultante.  
  
6. In seguito, quando si desidera reimpostare le impostazioni degli strumenti esterni, selezionare la chiave del registro di sistema HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \ e scegliere **Elimina** dal menu di scelta rapida.  
  
7. Quando viene visualizzata la finestra di dialogo **Conferma eliminazione chiave** , fare clic su **Sì**.  
  
8. Fare clic con il pulsante destro del mouse sul file External Tools. reg salvato in precedenza, scegliere **Apri con**, quindi fare clic su **Editor del registro di sistema**.  
  
## <a name="writing-to-the-user-settings-store"></a>Scrittura nell'archivio delle impostazioni utente  
  
1. Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. In UserSettingsStoreCommand.cs aggiungere le istruzioni using seguenti:  
  
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
