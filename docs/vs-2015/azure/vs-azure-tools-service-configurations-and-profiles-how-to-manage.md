---
title: Come gestire i profili e configurazioni del servizio | Microsoft Docs
description: Informazioni su come lavorare con i file di configurazione profili e configurazioni del servizio | quale archiviare le impostazioni per gli ambienti di distribuzione e pubblicare le impostazioni per i servizi cloud.
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002920"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Come gestire le configurazioni e i profili dei servizi
## <a name="overview"></a>Panoramica
Quando si pubblica un servizio cloud, Visual Studio archivia le informazioni di configurazione in due tipi di file di configurazione: profili e configurazioni del servizio. Le configurazioni del servizio (file con estensione cscfg) archiviano le impostazioni per gli ambienti di distribuzione per un servizio cloud di Azure. Azure Usa questi file di configurazione quando gestisce i servizi cloud. D'altra parte, archivio di profili (file con estensione azurepubxml) pubblicare le impostazioni per i servizi cloud. Queste impostazioni sono un record delle opzioni selezionate quando si usa la pubblicazione guidata e sono utilizzate localmente da Visual Studio. In questo argomento viene illustrato come usare entrambi i tipi di file di configurazione.

## <a name="service-configurations"></a>Configurazioni del servizio
È possibile creare più configurazioni del servizio da utilizzare per ogni ambiente di distribuzione. Ad esempio, si potrebbe creare una configurazione del servizio per l'ambiente locale che consente di eseguire e testare un'applicazione Azure e un'altra configurazione del servizio per l'ambiente di produzione.

È possibile aggiungere, eliminare, rinominare e modificare queste configurazioni del servizio in base alle esigenze. È possibile gestire queste configurazioni del servizio da Visual Studio, come illustrato nella figura seguente.

![Gestisci configurazioni servizio](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

È anche possibile aprire il **Gestisci configurazioni** finestra di dialogo Pagine delle proprietà del ruolo. Per aprire le proprietà per un ruolo nel progetto Azure, aprire il menu di scelta rapida per il ruolo e quindi scegliere **proprietà**. Nel **le impostazioni** scheda, espandere il **configurazione del servizio** elenco e quindi selezionare **Gestisci** per aprire il **Gestisci configurazioni** finestra di dialogo.

### <a name="to-add-a-service-configuration"></a>Per aggiungere una configurazione del servizio
1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **Gestisci configurazioni**.
   
    Il **Gestisci configurazioni del servizio** verrà visualizzata la finestra di dialogo.
2. Per aggiungere una configurazione del servizio, è necessario creare una copia di una configurazione esistente. A tale scopo, scegliere la configurazione che si desidera copiare dall'elenco dei nomi e quindi selezionare **Crea copia**.
3. (Facoltativo) Per assegnare la configurazione del servizio un nome diverso, scegliere la nuova configurazione del servizio dall'elenco dei nomi e quindi selezionare **Rinomina**. Nel **Name** testo, digitare il nome che si desidera usare per questa configurazione del servizio e quindi selezionare **OK**.
   
    Un nuovo file di configurazione servizio denominato ServiceConfiguration. [New Name]. cscfg viene aggiunto al progetto Azure in Esplora soluzioni.

### <a name="to-delete-a-service-configuration"></a>Per eliminare una configurazione del servizio
1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **Gestisci configurazioni**.
   
    Il **Gestisci configurazioni del servizio** verrà visualizzata la finestra di dialogo.
2. Per eliminare una configurazione del servizio, scegliere la configurazione che si desidera eliminare dal **Name** elenco e quindi selezionare **rimuovere**. Per verificare che si desidera eliminare questa configurazione viene visualizzata una finestra di dialogo.
3. Selezionare **Elimina**.
   
     File di configurazione del servizio viene rimosso dal progetto Azure in Esplora soluzioni.

### <a name="to-rename-a-service-configuration"></a>Per rinominare una configurazione del servizio
1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **Gestisci configurazioni**.
   
    Il **Gestisci configurazioni del servizio** verrà visualizzata la finestra di dialogo.
2. Per rinominare una configurazione del servizio, scegliere la nuova configurazione del servizio dal **Name** elenco e quindi selezionare **rinominare**. Nel **Name** testo, digitare il nome che si desidera usare per questa configurazione del servizio e quindi selezionare **OK**.
   
    Il nome del file di configurazione del servizio viene modificato nel progetto Azure in Esplora soluzioni.

### <a name="to-change-a-service-configuration"></a>Per modificare una configurazione del servizio
* Se si desidera modificare una configurazione del servizio, aprire il menu di scelta rapida per il ruolo specifico da modificare nel progetto Azure e quindi selezionare **proprietà**. Visualizzare [procedura: configurare i ruoli per un servizio Cloud di Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) per altre informazioni.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Apportare diverse combinazioni di impostazioni con i profili
Usando un profilo, è possibile popolare automaticamente **pubblicazione guidata** con diverse combinazioni di impostazioni per scopi diversi. Ad esempio, è possibile definire un profilo per il debug e un altro per la versione di build. In tal caso, il **eseguire il Debug** profilo avrebbe **IntelliTrace** abilitata e il **Debug** configurazione selezionata e il **versione** profilo avrebbe **IntelliTrace** disabilitata e il **rilascio** configurazione selezionata. È anche possibile utilizzare profili diversi per distribuire un servizio usando un account di archiviazione diverso.

Quando si esegue la procedura guidata per la prima volta, viene creato un profilo predefinito. Visual Studio archivia il profilo in un file con estensione azurepubxml, aggiunto al progetto Azure con il **profili** cartella. Se si specificano manualmente opzioni diverse quando si esegue la procedura guidata in un secondo momento, il file viene aggiornato automaticamente. Prima di eseguire la procedura seguente, è necessario avere già pubblicato il servizio cloud almeno una volta.

### <a name="to-add-a-profile"></a>Per aggiungere un profilo
1. Aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **pubblica**.
2. Accanto al **profilo di destinazione** elenco, selezionare la **Salva profilo** pulsante, come mostrato nella figura seguente. Verrà creato un profilo per l'utente.
   
    ![Creare un nuovo profilo](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Dopo aver creato il profilo, selezionare **< Gestisci... >** nel **profilo di destinazione** elenco.
   
    Il **gestire i profili** verrà visualizzata la finestra di dialogo, come mostrato nella figura seguente.
   
    ![Finestra di dialogo profili Gestisci](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. Nel **Name** elenco, scegliere un profilo e quindi selezionare **Crea copia**.
5. Scegliere il **Chiudi** pulsante.
   
    Il nuovo profilo compare nell'elenco profilo di destinazione.
6. Nel **profilo di destinazione** elencare, selezionare il profilo appena creato. Le impostazioni di pubblicazione guidata vengono popolate in base alle opzioni relative al profilo selezionato.
7. Selezionare il **Previous** e **successivo** pulsanti da visualizzare ogni pagina della procedura guidata di pubblicazione e quindi personalizzare le impostazioni per questo profilo. Visualizzare [pubblicazione guidata applicazione di Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) per informazioni.
8. Dopo aver completato la personalizzazione delle impostazioni, selezionare **successivo** per tornare alla pagina delle impostazioni. Il profilo viene salvato quando si pubblica il servizio utilizzando queste impostazioni o se si seleziona **salvare** accanto all'elenco dei profili.

### <a name="to-rename-or-delete-a-profile"></a>Per rinominare o eliminare un profilo
1. Aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **pubblica**.
2. Nel **profilo di destinazione** elenco, selezionare **Gestisci**.
3. Nel **gestire i profili** finestra di dialogo, selezionare il profilo che si desidera eliminare e quindi selezionare **rimuovere**.
4. Nella finestra di dialogo di conferma visualizzata, selezionare **OK**.
5. Selezionare **Chiudi**.

### <a name="to-change-a-profile"></a>Per modificare un profilo
1. Aprire il menu di scelta rapida per il progetto Azure e quindi selezionare **pubblica**.
2. Nel **profilo di destinazione** elencare, selezionare il profilo che si desidera modificare.
3. Selezionare il **Previous** e **successivo** pulsanti da visualizzare ogni pagina della procedura guidata di pubblicazione e quindi modificare le impostazioni desiderate. Visualizzare [pubblicazione guidata applicazione di Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) per informazioni.
4. Dopo avere modificato le impostazioni, selezionare **successivo** per tornare alle **impostazioni** pagina.
5. (Facoltativo) selezionare **pubblica** per pubblicare il servizio cloud usando le nuove impostazioni. Se non si vuole pubblicare il servizio cloud in questo momento, e si chiude la pubblicazione guidata, Visual Studio chiede all'utente se si desidera salvare le modifiche al profilo.

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sulla configurazione di altre parti del progetto Azure da Visual Studio, vedere [configurazione di un progetto di Azure](http://go.microsoft.com/fwlink/p/?LinkID=623075)

