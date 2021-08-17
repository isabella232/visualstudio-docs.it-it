---
title: Usare Servizi cloud (supporto esteso)
description: Informazioni su come creare e distribuire servizi cloud (supporto esteso) usando Azure Resource Manager con Visual Studio
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 547c3b6e81ad1df0f0beffec54a25ad7c0b32ed7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082439"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio"></a>Creare e distribuire in Servizi cloud (supporto esteso) in Visual Studio

A partire [da Visual Studio 2019 versione 16.9,](https://visualstudio.microsoft.com/vs/)è possibile usare i servizi cloud usando Azure Resource Manager, che semplifica notevolmente e modernizza la manutenzione e la gestione delle risorse di Azure. Questa funzionalità è abilitata da un nuovo servizio di Azure denominato *Servizi cloud (supporto esteso).* È possibile pubblicare un servizio cloud esistente in Servizi cloud (supporto esteso). Per informazioni su questo servizio di Azure, vedere [la documentazione di Servizi cloud (supporto esteso).](/azure/cloud-services-extended-support/overview)

## <a name="publish-to-cloud-services-extended-support"></a>Pubblicare in Servizi cloud (supporto esteso)

Quando si pubblica il progetto di Servizio cloud di Azure esistente in Servizi cloud (supporto esteso), si mantiene comunque la possibilità di pubblicare in un servizio cloud di Azure classico. In Visual Studio 2019 versione 16.9 e successive, i progetti di  servizi cloud classici hanno una versione speciale del comando Pubblica, **Pubblica (supporto esteso).** Questo comando viene visualizzato nel menu di scelta rapida in **Esplora soluzioni**.

Esistono alcune differenze quando si esegue la pubblicazione in Servizi cloud (supporto esteso). Ad esempio, non viene chiesto se si sta pubblicando in **Gestione** temporanea o **Produzione,** perché questi slot di distribuzione non fanno parte del modello di pubblicazione del supporto esteso. Con Servizi cloud (supporto esteso) è invece possibile configurare più distribuzioni e scambiare le distribuzioni nel portale di Azure. Anche se gli strumenti Visual Studio consentono di impostare questa opzione nella versione 16.9, la funzionalità di scambio non verrà abilitata fino a una versione successiva di Servizi cloud (supporto esteso) e potrebbe causare un errore in fase di distribuzione durante l'anteprima.

Prima di pubblicare un servizio cloud di Azure classico in Servizi cloud (supporto esteso), controllare gli account di archiviazione utilizzati dal progetto e assicurarsi che siano account Archiviazione V1 o Archiviazione V2. I tipi di account di archiviazione classici avranno esito negativo con un messaggio di errore in fase di distribuzione. Assicurarsi di controllare l'account di archiviazione usato dalla diagnostica. Per controllare l'account di archiviazione di diagnostica, vedere Configurare la diagnostica per Servizi cloud di Azure [e le macchine virtuali.](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) Se il servizio usa un account di archiviazione classico, è possibile aggiornarlo. Vedere [Eseguire l'aggiornamento a un account di archiviazione per utilizzo generico v2.](/azure/storage/common/storage-account-upgrade?tabs=azure-portal)  Per informazioni generali sui tipi di account di archiviazione, vedere panoramica [Archiviazione account di archiviazione.](/azure/storage/common/storage-account-overview)

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Per pubblicare un progetto di servizio cloud di Azure classico in Servizi cloud (supporto esteso)

1. Fare clic con il pulsante destro del mouse sul nodo del progetto nel progetto servizio cloud di Azure (versione classica) e scegliere **Pubblica (supporto esteso)...**. La **pubblicazione guidata** si apre nella prima schermata.

   ![Scegliere Pubblica (supporto esteso) dal menu](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   Verrà **visualizzata la pubblicazione** guidata.

   ![Pagina di accesso](./media/cloud-services-extended-support/publish-step1.png)

1. **Account** - Selezionare un account o fare clic su **Aggiungi un account** nell'elenco a discesa degli account.

1. **Scegliere la sottoscrizione** - Scegliere la sottoscrizione da usare per la distribuzione.

1. Scegliere **Avanti** per passare alla **Impostazioni** pagina.

   ![Impostazioni comuni](./media/cloud-services-extended-support/publish-settings.png)

1. **Servizio cloud (supporto esteso):** nell'elenco a discesa selezionare un servizio cloud esistente (supporto esteso) oppure selezionare **Crea nuovo** e crearne uno. Il data center viene visualizzato tra parentesi per ogni servizio cloud (supporto esteso). È consigliabile che la data center locale per il servizio cloud (supporto esteso) sia uguale alla posizione data center per l'account di archiviazione.

   Se si sceglie di creare un nuovo servizio, verrà visualizzata la finestra **di dialogo Crea servizio cloud (supporto esteso).** Specificare la località e il gruppo di risorse da usare per il servizio cloud (supporto esteso).

   ![Creare un servizio cloud (supporto esteso)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Configurazione compilazione** - Selezionare **Debug** o **Rilascio**.

1. **Configurazione servizio** - Selezionare **Cloud** o **Locale**.

1. **Archiviazione account:** selezionare l'account di archiviazione da usare per questa distribuzione oppure **Crea nuovo** per creare un account di archiviazione. L'area viene visualizzata tra parentesi per ogni account di archiviazione. È consigliabile che la posizione del data center per l'account di archiviazione corrisponda a quella del data center per il servizio cloud (Impostazioni comuni).

   L'account di archiviazione di Azure archivia il pacchetto per la distribuzione dell'applicazione.

1. **Insieme di credenziali** delle chiavi: specificare l'insieme di credenziali delle chiavi che contiene i segreti per questo servizio cloud (supporto esteso). Questa opzione è abilitata se desktop remoto è abilitato o se vengono aggiunti certificati alla configurazione.

1. **Abilita Desktop remoto per tutti i ruoli** - Selezionare questa opzione per consentire la connessione remota al servizio. Verrà richiesto di specificare le credenziali.

   ![Impostazioni di Desktop remoto](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Scegliere **Avanti** per passare alla **pagina Impostazioni di** diagnostica.

   ![Impostazioni di diagnostica](./media/cloud-services-extended-support/diagnostics-settings.png)

   La diagnostica consente di risolvere i problemi di un servizio cloud di Azure (supporto esteso). Per informazioni sulla diagnostica, vedere [Configurazione della diagnostica per i servizi cloud e le macchine virtuali di Azure](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Per informazioni su Application Insights, vedere [Informazioni su Azure Application Insights](/azure/application-insights/app-insights-overview).

1. Scegliere **Avanti** per passare alla **pagina** Riepilogo.

   ![Riepilogo](./media/cloud-services-extended-support/publish-summary.png)

1. **Profilo di destinazione** - È possibile scegliere di creare un profilo di pubblicazione dalle impostazioni scelte. È ad esempio possibile creare un profilo per un ambiente di test e un altro per l'ambiente di produzione. Per salvare questo profilo, scegliere l'icona **Salva**. La procedura guidata crea e salva il profilo nel progetto Visual Studio. Per modificare il nome del profilo, aprire l'elenco **Profilo di destinazione**, quindi scegliere **Gestisci**.

   > [!Note]
   > Il profilo di pubblicazione viene visualizzato Esplora soluzioni in Visual Studio e le impostazioni del profilo vengono scritte in un file con estensione *azurePubxml.* Le impostazioni vengono salvate come attributi dei tag XML.

1. Dopo avere configurato tutte le impostazioni per la distribuzione del progetto, selezionare **Pubblica** nella parte inferiore della finestra di dialogo. È possibile monitorare lo stato del processo nella finestra di output **del log attività** di Azure Visual Studio. Scegliere il **collegamento Apri nel** portale per 

Congratulazioni! Il progetto di servizio cloud (supporto esteso) è stato pubblicato in Azure. Per pubblicare di nuovo con le stesse impostazioni, è possibile riutilizzare il profilo di pubblicazione o ripetere questi passaggi per crearne uno nuovo. Il Azure Resource Manager (ARM) e i parametri usati per la distribuzione vengono salvati nella *cartella bin/ \<configuration\> /Publish.*

## <a name="clean-up-azure-resources"></a>Pulire le risorse di Azure

Per pulire le risorse di Azure create seguendo questa esercitazione, passare al [portale di Azure](https://portal.azure.com), scegliere Gruppi di risorse **,** trovare e aprire il gruppo di risorse usato per creare il servizio cloud (supporto esteso) e scegliere Elimina gruppo di **risorse**.

## <a name="next-steps"></a>Passaggi successivi

Configurare l'integrazione continua (CI) usando **il pulsante Configura** nella **schermata** Pubblica. Per altre informazioni, vedere la [Azure Pipelines .](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)
