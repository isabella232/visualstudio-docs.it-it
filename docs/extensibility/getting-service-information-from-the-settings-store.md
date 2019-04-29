---
title: Recupero di informazioni sul servizio da Store le impostazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe38bf84510ea247c737477e421db8dbb15f63c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863142"
---
# <a name="get-service-information-from-the-settings-store"></a>Ottenere informazioni sul servizio dall'archivio delle impostazioni
È possibile usare l'archivio delle impostazioni per trovare tutti i servizi disponibili o per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.

## <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili

1. Creare un progetto VSIX denominato `FindServicesExtension` e quindi aggiungere un comando personalizzato denominato `FindServicesCommand`. Per altre informazioni su come creare un comando personalizzato, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Nelle *FindServicesCommand.cs*, aggiungere quanto segue usando istruzioni:

    ```vb
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Ottenere l'archivio delle impostazioni di configurazione, quindi trovare la Sottoraccolta servizi denominato. Questa raccolta include tutti i servizi disponibili. Nel `MenuItemCommand` (metodo), rimuovere il codice esistente e sostituirlo con quanto segue:

    ```
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

5. Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **FindServicesCommand richiamare**.

     Dovrebbe elencare tutti i servizi di una finestra di messaggio.

     Per verificare queste impostazioni, è possibile usare l'editor del Registro di sistema.

## <a name="find-a-specific-service"></a>Trovare un servizio specifico
 È anche possibile usare il <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodo per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.

1. In MenuItemCallback del progetto è stato creato nella procedura precedente, eseguire la ricerca dell'archivio delle impostazioni di configurazione per il `Services` raccolta che include la Sottoraccolta denominato dal GUID del servizio. In questo caso verrà cercato il servizio della Guida.

    ```
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

3. Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **FindServicesCommand richiamare**.

     Verrà visualizzato un messaggio con il testo **della Guida servizio disponibili:** seguito da **True** oppure **False**. Per verificare questa impostazione, è possibile usare un editor del Registro di sistema, come illustrato nei passaggi precedenti.