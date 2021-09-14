---
title: Mantenere l'indirizzo IP virtuale costante per il servizio cloud di Azure
description: Informazioni su come assicurare che l'indirizzo IP virtuale (indirizzo VIP) del servizio cloud di Azure non subisca modifiche.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: b29f7b4380233a510fb34c3e72cf2aac9b948ba1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633212"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Mantenere un indirizzo IP virtuale costante per un servizio cloud di Azure
Quando si aggiorna un servizio cloud ospitato in Azure, potrebbe essere necessario assicurare che l'indirizzo IP virtuale (indirizzo VIP) del servizio non subisca modifiche. Molti servizi di gestione di dominio usano DNS (Domain Name System) per la registrazione dei nomi di dominio. DNS funziona solo se l'indirizzo VIP rimane invariato. È possibile usare la **Pubblicazione guidata** in Strumenti di Azure per assicurare che l'indirizzo VIP del servizio cloud non cambi in caso di aggiornamento. Per altre informazioni su come usare la gestione dei domini DNS per i servizi cloud, vedere [Configurazione di un nome di dominio personalizzato per un servizio cloud di Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Pubblicare un servizio cloud senza modifica dell'indirizzo VIP
L'indirizzo VIP di un servizio cloud viene allocato alla prima distribuzione in Azure in un ambiente specifico, ad esempio l'ambiente di produzione. L'indirizzo VIP viene modificato solo se si elimina esplicitamente la distribuzione o se la si elimina implicitamente mediante il processo di aggiornamento della distribuzione. Per mantenere l'indirizzo VIP, è necessario non eliminare la distribuzione e assicurare che Visual Studio non la elimini automaticamente.

È possibile specificare le impostazioni di distribuzione nella **Pubblicazione guidata**, che supporta alcune opzioni di distribuzione. È possibile specificare una nuova distribuzione o una distribuzione di aggiornamento, che può essere incrementale o simultanea. Entrambi i tipi di distribuzione di aggiornamento mantengono l'indirizzo VIP. Per definizioni di questi diversi tipi di distribuzione, vedere [Procedura guidata Pubblica l'applicazione Azure](vs-azure-tools-publish-azure-application-wizard.md). È anche possibile controllare se la distribuzione precedente di un servizio cloud viene eliminata in caso di errore. Se l'opzione non viene impostata correttamente, è possibile che l'indirizzo VIP cambi in modo imprevisto.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Aggiornare un servizio cloud senza modifica dell'indirizzo VIP
1. Creare o aprire un progetto del servizio cloud di Azure in Visual Studio.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto. Dal menu di scelta rapida selezionare **Pubblicare**.

    ![Menu Pubblica](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. Nella finestra di dialogo **Pubblica applicazione Azure**, selezionare la sottoscrizione di Azure in cui si desidera distribuire. Effettuare l'accesso se necessario, quindi selezionare **Avanti**.

    ![Pagina di accesso Pubblica applicazione Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Nella **scheda Impostazioni** comuni verificare che il nome del servizio cloud in cui si esegue la distribuzione, l'ambiente **,** la configurazione della compilazione e la configurazione del servizio **siano** tutti corretti.

    ![Scheda delle impostazioni comuni di Pubblica applicazione Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Nella scheda **Impostazioni avanzate** verificare che il **Etichetta distribuzione** e **Account di archiviazione** siano corretti. Verificare che la casella di controllo **Elimina distribuzione in caso di errore** sia deselezionata e che sia selezionata la casella di controllo **Aggiornamento distribuzione**. Deselezionando la casella **di controllo** Elimina distribuzione in caso di errore, si garantisce che l'indirizzo VIP non sia perso se si verifica un errore durante la distribuzione. Se si seleziona la casella di controllo **Aggiornamento distribuzione**, si assicura che la distribuzione non verrà eliminata e che l'indirizzo VIP non andrà perso quando si ripubblica l'applicazione.

    ![Scheda delle impostazioni avanzate di Pubblica applicazione Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Per specificare ulteriormente come aggiornare i ruoli, selezionare **Impostazioni** accanto ad **Aggiornamento distribuzione**. Selezionare **Aggiornamento incrementale** o **Simultaneous update** (Aggiornamento simultaneo) e scegliere **OK**. Se si sceglie **Aggiornamento incrementale**, le istanze dell'applicazione vengono aggiornate una dopo l'altra, in modo che l'applicazione sia sempre disponibile. Se si sceglie **Simultaneous update** (Aggiornamento simultaneo), tutte le istanze dell'applicazione vengono aggiornate contemporaneamente. L'aggiornamento simultaneo è più veloce, ma è possibile che il servizio non sia disponibile durante il processo di aggiornamento. Al termine dell'operazione, scegliere **Avanti**.

    ![Pagina delle impostazioni di distribuzione di Pubblica applicazione Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. Quando si ritorna alla finestra di dialogo **Pubblica applicazione Azure**, selezionare **Avanti** fino a quando non viene visualizzata la pagina **Riepilogo**. Verificare le impostazioni e quindi selezionare **Pubblica**.

    ![Pagina di riepilogo di Pubblica applicazione Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Passaggi successivi
- [Uso della procedura guidata Pubblica l'applicazione Azure di Visual Studio](vs-azure-tools-publish-azure-application-wizard.md)
