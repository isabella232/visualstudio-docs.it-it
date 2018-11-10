---
title: Come mantenere un indirizzo IP virtuale costante per un servizio cloud di Azure | Microsoft Docs
description: Informazioni su come assicurare che l'indirizzo IP virtuale (VIP) del servizio cloud di Azure non subisca modifiche.
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002900"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Mantenere un indirizzo IP virtuale costante per un servizio cloud di Azure
Quando si aggiorna un servizio cloud che è ospitato in Azure, è necessario assicurare che l'indirizzo IP virtuale (VIP) del servizio non subisca modifiche. Molti servizi di gestione di dominio usano il sistema DNS (Domain Name) per la registrazione dei nomi di dominio. DNS funziona solo se l'indirizzo VIP rimane invariato. È possibile usare la **pubblicazione guidata** negli strumenti di Azure per garantire che l'indirizzo VIP del servizio cloud non cambi quando si aggiorna. Per altre informazioni su come usare Gestione dei domini DNS per i servizi cloud, vedere [configurazione di un nome di dominio personalizzato per un servizio cloud Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Pubblicare un servizio cloud senza modifica dell'indirizzo VIP
L'indirizzo VIP di un servizio cloud viene allocato alla prima distribuzione in Azure in un ambiente specifico, ad esempio l'ambiente di produzione. L'indirizzo VIP viene modificato solo se si elimina la distribuzione in modo esplicito o la distribuzione viene eliminata in modo implicito mediante il processo di aggiornamento della distribuzione. Per mantenere l'indirizzo VIP, è necessario non eliminare la distribuzione e assicurarsi che Visual Studio non elimini automaticamente la distribuzione. 

È possibile specificare le impostazioni di distribuzione nel **pubblicazione guidata**, che supporta alcune opzioni di distribuzione. È possibile specificare una nuova distribuzione o una distribuzione degli aggiornamenti, che può essere incrementale o simultanea. Entrambi i tipi di distribuzione di aggiornamento mantengono l'indirizzo VIP. Per le definizioni di questi diversi tipi di distribuzione, vedere [pubblicazione guidata applicazione di Azure](vs-azure-tools-publish-azure-application-wizard.md). Inoltre, è possibile controllare se la distribuzione precedente di un servizio cloud viene eliminata se si verifica un errore. Se si non imposta tale opzione in modo corretto, l'indirizzo VIP cambi in modo imprevisto.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Aggiornare un servizio cloud senza modifica dell'indirizzo VIP
1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio. 

2. Nelle **Esplora soluzioni**, fare clic sul progetto. Menu di scelta rapida, selezionare **pubblica**.

    ![Menu Pubblica](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. Nel **pubblica applicazione Azure** finestra di dialogo, selezionare la sottoscrizione di Azure a cui si desidera distribuire. L'accesso se necessario, quindi selezionare **successivo**.

    ![Pubblicazione di Azure dell'applicazione nella pagina di accesso](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Nel **impostazioni comuni** scheda, verificare che il nome del cloud di servizio in cui esegue la distribuzione, il **ambiente**, il **configurazione della Build**e il **Configurazione del servizio** siano tutti corretti.

    ![Scheda Impostazioni comuni di applicazione di Azure pubblica](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Nel **impostazioni avanzate** scheda, verificare che il **etichetta distribuzione** e il **account di archiviazione** siano corretti. Verificare che il **Elimina la distribuzione in caso di errore** casella di controllo è deselezionata e verificare che il **aggiornamento distribuzione** casella di controllo è selezionata. Cancellando il **Elimina la distribuzione in caso di errore** casella di controllo, assicurarsi che l'indirizzo VIP non andrà perso se si verifica un errore durante la distribuzione. Selezionando il **aggiornamento distribuzione** casella di controllo, si assicura che non viene eliminata la distribuzione e l'indirizzo VIP non andrà perso quando si ripubblica l'applicazione. 

    ![Scheda Impostazioni avanzate dell'applicazione di Azure pubblica](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Per specificare ulteriormente come aggiornare i ruoli, selezionare **le impostazioni** accanto a **aggiornamento distribuzione**. Selezionare uno **aggiornamento incrementale** oppure **aggiornamento simultaneo**e selezionare **OK**. Scegli **aggiornamento incrementale** aggiornare ogni istanza dell'applicazione, uno dopo l'altro, in modo che l'applicazione sia sempre disponibile. Scegli **aggiornamento simultaneo** per aggiornare tutte le istanze dell'applicazione nello stesso momento. L'aggiornamento simultaneo è più veloce, ma il servizio potrebbe non essere disponibile durante il processo di aggiornamento. Al termine, selezionare **successivo**.

    ![Pagina Impostazioni di distribuzione dell'applicazione di Azure pubblica](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. Nel **pubblica applicazione Azure** finestra di dialogo **successiva** fino a quando non la **riepilogo** verrà visualizzata la pagina. Verificare le impostazioni e quindi selezionare **pubblica**.
   
    ![Pagina di riepilogo dell'applicazione di Azure pubblica](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Passaggi successivi
- [Con Visual Studio pubblicazione guidata applicazione di Azure](vs-azure-tools-publish-azure-application-wizard.md)

