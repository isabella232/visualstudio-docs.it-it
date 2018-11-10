---
title: Debug di un report pubblicato con Visual Studio e IntelliTrace servizio cloud di Azure | Microsoft Docs
description: Informazioni su come eseguire il debug di un servizio cloud con Visual Studio e IntelliTrace
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 865642bb7c8e41f81ff4b44ce628082e19b63a56
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002950"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Debug di un servizio cloud di Azure pubblicato con Visual Studio e IntelliTrace
Con IntelliTrace, è possibile registrare informazioni di debug approfondite per un'istanza del ruolo quando è in esecuzione in Azure. Se è necessario individuare la causa di un problema, è possibile utilizzare i log di IntelliTrace per esaminare il codice da Visual Studio come se fosse in esecuzione in Azure. In effetti, IntelliTrace ha raccolto chiave l'esecuzione di codice e i dati di ambiente quando l'applicazione Azure è in esecuzione come un servizio cloud in Azure e consente di riprodurre i dati registrati da Visual Studio. 

È possibile usare IntelliTrace se hai installato Visual Studio Enterprise e l'applicazione Azure è destinata a .NET Framework 4 o versione successiva. IntelliTrace raccoglie informazioni per i ruoli Azure. Le macchine virtuali per questi ruoli eseguono sempre sistemi operativi a 64 bit.

In alternativa, è possibile usare [debug remoto](http://go.microsoft.com/fwlink/p/?LinkId=623041) per connettersi direttamente a un servizio cloud è in esecuzione in Azure.

> [!IMPORTANT]
> IntelliTrace è destinato esclusivamente a scenari di debug e non deve essere utilizzato per una distribuzione di produzione.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Configurare un'applicazione di Azure per IntelliTrace
Per abilitare IntelliTrace per un'applicazione Azure, è necessario creare e pubblicare l'applicazione da un progetto Azure in Visual Studio. È necessario configurare IntelliTrace per l'applicazione Azure prima di pubblicarlo in Azure. Se si pubblica l'applicazione senza configurare IntelliTrace, è necessario ripubblicare il progetto. Per altre informazioni, vedere [pubblicazione di un cloud di Azure services i progetti che usano Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Quando si è pronti per distribuire l'applicazione Azure, verificare che le destinazioni di compilazione progetto siano impostate su **Debug**.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e, dal menu di scelta rapida, selezionare **Publish**.
   
1. Nel **pubblica applicazione Azure** finestra di dialogo, selezionare la sottoscrizione di Azure e scegliere **successivo**.

1. Nel **le impostazioni** pagina, selezionare la **impostazioni avanzate** scheda.

1. Attivare i **Abilita IntelliTrace** opzione per raccogliere i log di IntelliTrace per l'applicazione quando viene pubblicato nel cloud.
   
1. Per personalizzare la configurazione di IntelliTrace di base, selezionare **le impostazioni** accanto a **Abilita IntelliTrace**.

    ![Collegamento alle impostazioni di IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. Nel **impostazioni di IntelliTrace** finestra di dialogo è possibile specificare gli eventi di log, se si desidera raccogliere informazioni sulle chiamate, quali moduli e i processi per raccogliere i log e quanto spazio allocare per la registrazione. Per altre informazioni su IntelliTrace, vedere [debug con IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![Impostazioni di IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Il log IntelliTrace è un file di log circolare delle dimensioni massime specificate nelle impostazioni di IntelliTrace (le dimensioni predefinite sono 250 MB). I log di IntelliTrace vengono raccolti in un file nel file system della macchina virtuale. Quando si richiedono i log, uno snapshot viene portato a questo punto nel tempo e scaricato nel computer locale.

Dopo aver pubblicato il servizio cloud di Azure in Azure, è possibile determinare se IntelliTrace è stato abilitato dal nodo di Azure in **Esplora Server**, come illustrato nell'immagine seguente:

![Esplora server - IntelliTrace abilitato](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Scaricare i log di IntelliTrace per un'istanza del ruolo
Usa Visual Studio, è possibile scaricare i log IntelliTrace per un'istanza del ruolo attenendosi alla procedura seguente:

1. Nella **Esplora Server**, espandere il **servizi Cloud** nodo, quindi individuare l'istanza del ruolo cui si vuole scaricare i registri. 

1. L'istanza del ruolo e dal menu di scelta rapida, scegliere **Visualizza log IntelliTrace**. 

    ![Visualizza log IntelliTrace l'opzione di menu](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. I log di IntelliTrace vengono scaricati in un file in una directory nel computer locale. Registra ogni volta che si richiede di IntelliTrace, viene creato un nuovo snapshot. Mentre i log vengono scaricati, Visual Studio visualizza lo stato di avanzamento dell'operazione nella **Log attività di Azure** finestra. Come illustrato nella figura seguente, è possibile espandere la voce per l'operazione visualizzare altri dettagli.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

È possibile continuare a lavorare in Visual Studio durante il download dei log IntelliTrace. Quando il log è terminato il download, viene aperto in Visual Studio.

> [!NOTE]
> I log di IntelliTrace possono contenere eccezioni che il framework genera e gestisce in un secondo momento. Codice interno del framework genera queste eccezioni come parte normale di avvio di un ruolo, in modo che si può essere ignorato.
> 
> 

## <a name="next-steps"></a>Passaggi successivi
- [Opzioni per il debug di servizi cloud di Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Pubblicazione di un servizio cloud di Azure con Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)