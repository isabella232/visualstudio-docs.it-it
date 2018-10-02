---
title: Recupero di informazioni sul servizio da Store le impostazioni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0328842e3698015bceb8e24663d218e4cd3c5dfa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532344"
---
# <a name="getting-service-information-from-the-settings-store"></a>Recupero delle informazioni sui servizi dall'archivio delle impostazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [recupero di informazioni del servizio da Store di impostazioni](https://docs.microsoft.com/visualstudio/extensibility/getting-service-information-from-the-settings-store).  
  
È possibile usare l'archivio delle impostazioni per trovare tutti i servizi disponibili o per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.  
  
### <a name="to-list-the-available-services"></a>Per elencare i servizi disponibili  
  
1.  Creare un progetto VSIX denominato FindServicesExtension e quindi aggiungere un comando personalizzato denominato FindServicesCommand. Per altre informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  In FindServicesCommand.cs, aggiungere quanto segue usando istruzioni:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3.  Ottenere l'archivio delle impostazioni di configurazione, quindi trovare la Sottoraccolta servizi denominato. Questa raccolta include tutti i servizi disponibili. Nel metodo MenuItemCommand, rimuovere il codice esistente e sostituirlo con quanto segue:  
  
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
  
4.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
5.  Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **FindServicesCommand richiamare**.  
  
     Dovrebbe elencare tutti i servizi di una finestra di messaggio.  
  
     Per verificare queste impostazioni, è possibile usare l'editor del Registro di sistema.  
  
## <a name="finding-a-specific-service"></a>Ricerca di un servizio specifico  
 È anche possibile usare il <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodo per determinare se è installato un particolare servizio. È necessario conoscere il tipo della classe del servizio.  
  
1.  In MenuItemCallback del progetto è stato creato nella procedura precedente, eseguire la ricerca dell'archivio delle impostazioni di configurazione per il `Services` raccolta che include la Sottoraccolta denominato dal GUID del servizio. In questo caso verrà cercato il servizio della Guida.  
  
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
  
2.  Compilare il progetto e avviare il debug.  
  
3.  Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **FindServicesCommand richiamare**.  
  
     Verrà visualizzato un messaggio con il testo **della Guida servizio disponibili:** seguito da **True** oppure **False**. Per verificare questa impostazione, è possibile usare un editor del Registro di sistema, come illustrato nei passaggi precedenti.

