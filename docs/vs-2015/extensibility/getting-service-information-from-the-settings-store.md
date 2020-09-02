---
title: Recupero delle informazioni sul servizio dall'archivio impostazioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204307"
---
# <a name="getting-service-information-from-the-settings-store"></a>Recupero delle informazioni sui servizi dall'archivio delle impostazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare l'archivio impostazioni per trovare tutti i servizi disponibili o per determinare se un particolare servizio è installato. È necessario essere a conoscenza del tipo di classe del servizio.  
  
### <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili  
  
1. Creare un progetto VSIX denominato FindServicesExtension e quindi aggiungere un comando personalizzato denominato FindServicesCommand. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. In FindServicesCommand.cs aggiungere le istruzioni using seguenti:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Ottenere l'archivio delle impostazioni di configurazione, quindi trovare la sottoraccolta denominata Services. Questa raccolta include tutti i servizi disponibili. Nel metodo MenuItemCommand rimuovere il codice esistente e sostituirlo con quanto segue:  
  
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
  
5. Nell'istanza sperimentale, scegliere **richiama FindServicesCommand**dal menu **strumenti** .  
  
     Verrà visualizzata una finestra di messaggio in cui sono elencati tutti i servizi.  
  
     Per verificare queste impostazioni, è possibile usare l'editor del registro di sistema.  
  
## <a name="finding-a-specific-service"></a>Ricerca di un servizio specifico  
 È anche possibile usare il <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodo per determinare se un particolare servizio è installato. È necessario essere a conoscenza del tipo di classe del servizio.  
  
1. Nella MenuItemCallback del progetto creato nella procedura precedente, eseguire una ricerca nell'archivio delle impostazioni di configurazione per la `Services` raccolta che contiene la sottoraccolta denominata dal GUID del servizio. In questo caso verrà cercato il servizio della guida.  
  
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
  
3. Nell'istanza sperimentale, scegliere **richiama FindServicesCommand**dal menu **strumenti** .  
  
     Verrà visualizzato un messaggio con il servizio di **Guida del testo disponibile:**  seguito da **true** o **false**. Per verificare questa impostazione, è possibile utilizzare un editor del registro di sistema, come illustrato nei passaggi precedenti.
