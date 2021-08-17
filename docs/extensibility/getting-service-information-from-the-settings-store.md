---
title: Recupero di informazioni sul servizio dal Impostazioni Store | Microsoft Docs
description: Informazioni su come usare l'archivio impostazioni per trovare tutti i servizi disponibili o per determinare se è installato un particolare servizio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3765859ed2ae3896ef6659d3df4dcbfe65b35963e8058bc8011c94f43324b467
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401752"
---
# <a name="get-service-information-from-the-settings-store"></a>Ottenere informazioni sul servizio dall'archivio impostazioni
È possibile usare l'archivio impostazioni per trovare tutti i servizi disponibili o per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.

## <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili

1. Creare un progetto VSIX denominato `FindServicesExtension` e quindi aggiungere un comando personalizzato denominato `FindServicesCommand` . Per altre informazioni su come creare un comando personalizzato, vedere [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. In *FindServicesCommand.cs* aggiungere le direttive using seguenti:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Ottenere l'archivio delle impostazioni di configurazione, quindi trovare l'insieme secondario denominato Services. Questa raccolta include tutti i servizi disponibili. Nel metodo `MenuItemCommand` rimuovere il codice esistente e sostituirlo con il codice seguente:

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

5. Nell'istanza sperimentale scegliere **Richiama** **FindServicesCommand** dal menu Strumenti .

     Verrà visualizzata una finestra di messaggio che elenca tutti i servizi.

     Per verificare queste impostazioni, è possibile usare l'editor del Registro di sistema.

## <a name="find-a-specific-service"></a>Trovare un servizio specifico
 È anche possibile usare il <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodo per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.

1. In MenuItemCallback del progetto creato nella procedura precedente cercare nell'archivio delle impostazioni di configurazione la raccolta con l'insieme secondario denominato dal `Services` GUID del servizio. In questo caso si cerca il servizio Guida.

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

3. Nell'istanza sperimentale scegliere **Richiama** **FindServicesCommand** dal menu Strumenti .

     Verrà visualizzato un messaggio con il testo **Help Service Available(Servizio guida disponibile):** seguito da **True** o **False.** Per verificare questa impostazione, è possibile usare un editor del Registro di sistema, come illustrato nei passaggi precedenti.
