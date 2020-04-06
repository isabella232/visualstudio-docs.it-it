---
title: Recupero delle informazioni sul servizio dall'archivio impostazioni . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711378"
---
# <a name="get-service-information-from-the-settings-store"></a>Ottenere informazioni sul servizio dall'archivio impostazioniGet service information from the settings store
È possibile utilizzare l'archivio impostazioni per trovare tutti i servizi disponibili o per determinare se un determinato servizio è installato. È necessario conoscere il tipo della classe di servizio.

## <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili

1. Creare un progetto `FindServicesExtension` VSIX denominato e `FindServicesCommand`quindi aggiungere un comando personalizzato denominato . Per altre informazioni su come creare un comando personalizzato, vedere [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) di menuFor more information about how to create a custom command, see Create an extension with a menu command

2. In *FindServicesCommand.cs*aggiungere le seguenti direttive using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Ottenere l'archivio delle impostazioni di configurazione, quindi trovare la raccolta secondaria denominata Servizi.Get the configuration settings store, then find the subcollection named Services. Questa raccolta include tutti i servizi disponibili. Nel `MenuItemCommand` metodo, rimuovere il codice esistente e sostituirlo con quanto segue:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

5. Nell'istanza sperimentale scegliere Richiama **FindServicesCommand**dal menu **Strumenti** .

     Verrà visualizzata una finestra di messaggio in cui sono elencati tutti i servizi.

     Per verificare queste impostazioni, è possibile utilizzare l'editor del Registro di sistema.

## <a name="find-a-specific-service"></a>Trovare un servizio specifico
 È inoltre possibile <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> utilizzare il metodo per determinare se un determinato servizio è installato. È necessario conoscere il tipo della classe di servizio.

1. Nel MenuItemCallback del progetto creato nella procedura precedente, cercare nell'archivio delle impostazioni di configurazione la `Services` raccolta con la sottoraccolta denominata dal GUID del servizio. In questo caso cercheremo il servizio di assistenza.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Compilare il progetto e avviare il debug.

3. Nell'istanza sperimentale scegliere Richiama **FindServicesCommand**dal menu **Strumenti** .

     Verrà visualizzato un messaggio con il testo **Guida al servizio disponibile:** seguito da **True** o **False**. Per verificare questa impostazione, è possibile utilizzare un editor del Registro di sistema, come illustrato nei passaggi precedenti.
