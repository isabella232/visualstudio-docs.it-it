---
title: Recupero delle informazioni sul servizio dall'archivio impostazioni | Microsoft Docs
description: Informazioni su come usare l'archivio impostazioni per trovare tutti i servizi disponibili o per determinare se un particolare servizio è installato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15efb14d2cee36e5f2a8559c3ffa3844251aa982
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994433"
---
# <a name="get-service-information-from-the-settings-store"></a>Ottenere informazioni sul servizio dall'archivio impostazioni
È possibile utilizzare l'archivio impostazioni per trovare tutti i servizi disponibili o per determinare se un particolare servizio è installato. È necessario essere a conoscenza del tipo di classe del servizio.

## <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili

1. Creare un progetto VSIX denominato `FindServicesExtension` e quindi aggiungere un comando personalizzato denominato `FindServicesCommand` . Per altre informazioni su come creare un comando personalizzato, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. In *FindServicesCommand.cs* aggiungere le direttive using seguenti:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Ottenere l'archivio delle impostazioni di configurazione, quindi trovare la sottoraccolta denominata Services. Questa raccolta include tutti i servizi disponibili. Nel `MenuItemCommand` Metodo rimuovere il codice esistente e sostituirlo con quanto segue:

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

5. Nell'istanza sperimentale, scegliere **richiama FindServicesCommand** dal menu **strumenti** .

     Verrà visualizzata una finestra di messaggio in cui sono elencati tutti i servizi.

     Per verificare queste impostazioni, è possibile usare l'editor del registro di sistema.

## <a name="find-a-specific-service"></a>Trovare un servizio specifico
 È anche possibile usare il <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodo per determinare se un particolare servizio è installato. È necessario essere a conoscenza del tipo di classe del servizio.

1. Nella MenuItemCallback del progetto creato nella procedura precedente, eseguire una ricerca nell'archivio delle impostazioni di configurazione per la `Services` raccolta che contiene la sottoraccolta denominata dal GUID del servizio. In questo caso verrà cercato il servizio della guida.

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

3. Nell'istanza sperimentale, scegliere **richiama FindServicesCommand** dal menu **strumenti** .

     Verrà visualizzato un messaggio con il servizio di **Guida del testo disponibile:**  seguito da **true** o **false**. Per verificare questa impostazione, è possibile utilizzare un editor del registro di sistema, come illustrato nei passaggi precedenti.
