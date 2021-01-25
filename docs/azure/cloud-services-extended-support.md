---
title: Usare i servizi cloud (supporto esteso) (anteprima)
description: Informazioni su come creare e distribuire un servizio cloud (supporto esteso) usando Azure Resource Manager con Visual Studio
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: ff45cf05a6811c02881c26f76193d4c1f5a5e735
ms.sourcegitcommit: 7d34ab111614ae6bde5fb3c2bb91dd79e29a0a78
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2021
ms.locfileid: "98750305"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>Creare e distribuire in servizi cloud (supporto esteso) in Visual Studio (anteprima)

A partire da [Visual Studio 2019 versione 16,9](https://visualstudio.microsoft.com/vs/preview) (attualmente in anteprima), è possibile lavorare con i servizi cloud usando Azure Resource Manager, che semplifica e modernizza notevolmente la manutenzione e la gestione delle risorse di Azure. Questa funzionalità è abilitata da un nuovo servizio di Azure denominato *servizi cloud (supporto esteso)*. È possibile pubblicare un servizio cloud esistente in servizi cloud (supporto esteso). Per informazioni su questo servizio di Azure, vedere la [documentazione relativa ai servizi cloud (supporto esteso)](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>Pubblica nei servizi cloud (supporto esteso)

Quando si pubblica il progetto del servizio cloud di Azure esistente in servizi cloud (supporto esteso), si mantiene comunque la funzionalità di pubblicazione in un servizio cloud di Azure classico. In Visual Studio 2019 versione 16,9 Preview 3 e versioni successive, i progetti di servizi cloud classici hanno una versione speciale del comando **Publish** , **Publish (Extended Support)**. Questo comando viene visualizzato nel menu di scelta rapida in **Esplora soluzioni**.

Esistono alcune differenze durante la pubblicazione nei servizi cloud (supporto esteso). Ad esempio, non viene richiesto se si esegue la pubblicazione in **gestione temporanea** o in **produzione**, perché questi slot di distribuzione non fanno parte del modello di pubblicazione del supporto esteso. Con i servizi cloud (supporto esteso), è invece possibile configurare più distribuzioni e scambiare le distribuzioni nel portale di Azure. Sebbene gli strumenti di Visual Studio consentano di impostare questo valore in 16,9 Preview 3, la funzionalità di scambio non verrà abilitata fino a una versione successiva dei servizi cloud (supporto esteso) e potrebbe verificarsi un errore in fase di distribuzione durante l'anteprima.

Prima di pubblicare un servizio cloud di Azure classico in servizi cloud (supporto esteso), controllare gli account di archiviazione usati dal progetto e verificare che siano account di archiviazione V1 o storage V2. I tipi di account di archiviazione classico avranno esito negativo con un messaggio di errore in fase di distribuzione. Assicurarsi di controllare l'account di archiviazione usato dalla diagnostica. Per verificare l'account di archiviazione di diagnostica, vedere [configurare la diagnostica per i servizi cloud e le macchine virtuali di Azure](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Se il servizio usa un account di archiviazione classico, è possibile aggiornarlo; vedere [eseguire l'aggiornamento a un account di archiviazione per utilizzo generico V2](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Per informazioni generali sui tipi di account di archiviazione, vedere [Panoramica dell'account di archiviazione](/azure/storage/common/storage-account-overview).

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Per pubblicare un progetto di servizio cloud di Azure classico in servizi cloud (supporto esteso)

1. Servizi cloud (supporto esteso) è attualmente in versione di anteprima. Registrare la funzionalità per la propria sottoscrizione come indicato di seguito:

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. Fare clic con il pulsante destro del mouse sul nodo del progetto nel progetto servizio cloud di Azure (versione classica) e scegliere **pubblica (supporto esteso)...**. Nella prima schermata verrà visualizzata la **pubblicazione guidata** .

   ![Scegliere pubblica (supporto esteso) dal menu](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   Verrà visualizzata la **pubblicazione** guidata.

   ![Pagina di accesso](./media/cloud-services-extended-support/publish-step1.png)

1. **Account** - Selezionare un account o fare clic su **Aggiungi un account** nell'elenco a discesa degli account.

1. **Scegliere la sottoscrizione** - Scegliere la sottoscrizione da usare per la distribuzione.

1. Scegliere **Avanti** per passare alla pagina **Impostazioni** .

   ![Impostazioni comuni](./media/cloud-services-extended-support/publish-settings.png)

1. **Servizio cloud (supporto esteso)** : usando l'elenco a discesa, selezionare un servizio cloud esistente (supporto esteso) oppure selezionare **Crea nuovo** e crearne uno. Il data center viene visualizzato tra parentesi per ogni servizio cloud (supporto esteso). È consigliabile che la posizione del data center per il servizio cloud (supporto esteso) corrisponda a quella del data center per l'account di archiviazione.

   Se si sceglie di creare un nuovo servizio, verrà visualizzata la finestra di dialogo **Crea servizio cloud (supporto esteso)** . Specificare il percorso e il gruppo di risorse che si vuole usare per il servizio cloud (supporto esteso).

   ![Creazione di un servizio cloud (supporto esteso)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Configurazione compilazione** - Selezionare **Debug** o **Rilascio**.

1. **Configurazione servizio** - Selezionare **Cloud** o **Locale**.

1. **Account di archiviazione** : selezionare l'account di archiviazione da usare per la distribuzione oppure **crearne uno nuovo** per creare un account di archiviazione. L'area viene visualizzata tra parentesi per ogni account di archiviazione. È consigliabile che la posizione del data center per l'account di archiviazione corrisponda a quella del data center per il servizio cloud (Impostazioni comuni).

   L'account di archiviazione di Azure archivia il pacchetto per la distribuzione dell'applicazione.

1. **Key Vault** : specificare l'insieme di credenziali delle chiavi che contiene i segreti per questo servizio cloud (supporto esteso). Questa funzionalità è abilitata se desktop remoto è abilitato o se i certificati vengono aggiunti alla configurazione.

1. **Abilita Desktop remoto per tutti i ruoli** - Selezionare questa opzione per consentire la connessione remota al servizio. Verrà richiesto di specificare le credenziali.

   ![Impostazioni desktop remoto](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Scegliere **Avanti** per passare alla pagina **impostazioni di diagnostica** .

   ![Impostazioni di diagnostica](./media/cloud-services-extended-support/diagnostics-settings.png)

   La diagnostica consente di risolvere i problemi relativi a un servizio cloud di Azure (supporto esteso). Per informazioni sulla diagnostica, vedere [Configurazione della diagnostica per i servizi cloud e le macchine virtuali di Azure](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Per informazioni su Application Insights, vedere [Informazioni su Azure Application Insights](/azure/application-insights/app-insights-overview).

1. Scegliere **Avanti** per passare alla pagina **Riepilogo** .

   ![Riepilogo](./media/cloud-services-extended-support/publish-summary.png)

1. **Profilo di destinazione** - È possibile scegliere di creare un profilo di pubblicazione dalle impostazioni scelte. È ad esempio possibile creare un profilo per un ambiente di test e un altro per l'ambiente di produzione. Per salvare questo profilo, scegliere l'icona **Salva**. La procedura guidata crea e salva il profilo nel progetto Visual Studio. Per modificare il nome del profilo, aprire l'elenco **Profilo di destinazione**, quindi scegliere **Gestisci**.

   > [!Note]
   > Il profilo di pubblicazione viene visualizzato in Esplora soluzioni in Visual Studio e le impostazioni del profilo vengono scritte in un file con estensione *azurePubxml* . Le impostazioni vengono salvate come attributi dei tag XML.

1. Dopo avere configurato tutte le impostazioni per la distribuzione del progetto, selezionare **Pubblica** nella parte inferiore della finestra di dialogo. È possibile monitorare lo stato del processo nella finestra di output del **log attività di Azure** in Visual Studio. Scegliere il collegamento **Apri nel portale** per 

Congratulazioni! Il progetto del servizio cloud (supporto esteso) è stato pubblicato in Azure. Per eseguire di nuovo la pubblicazione con le stesse impostazioni, è possibile riutilizzare il profilo di pubblicazione oppure ripetere questi passaggi per crearne uno nuovo. Il modello di Azure Resource Manager (ARM) e i parametri usati per la distribuzione vengono salvati nella cartella *bin/ \<configuration\> /Publish* .

## <a name="clean-up-azure-resources"></a>Pulire le risorse di Azure

Per pulire le risorse di Azure create seguendo questa esercitazione, passare alla [portale di Azure](https://portal.azure.com), scegliere **gruppi di risorse**, trovare e aprire il gruppo di risorse usato per creare il servizio cloud (supporto esteso) e scegliere **Elimina gruppo di risorse**.

## <a name="next-steps"></a>Passaggi successivi

Configurare l'integrazione continua (CI) usando il pulsante **Configura** della schermata di **pubblicazione** . Per ulteriori informazioni, vedere [Azure Pipelines documentazione](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
