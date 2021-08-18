---
title: Aggiungere una connessione a database SQL di Azure | Microsoft Docs
description: Aggiungere database SQL di Azure connessione all'app usando il Visual Studio Servizi connessi
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: f44eeb9017936dd28157a35ad7c911698400f00b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091799"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Aggiungere una connessione a database SQL di Azure

Con Visual Studio, è possibile connettere uno degli elementi seguenti a database SQL di Azure usando **la** Servizi connessi funzionalità:

- .NET Framework app console
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (tra cui app console, WPF, Windows Form, libreria di classi)
- Ruolo di lavoro .NET Core
- Funzioni di Azure
- App Windows universali
- Xamarin
- Cordova

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Progetto di uno dei tipi supportati

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Connessione da database SQL di Azure usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro **del** mouse sul nodo Servizi connessi e scegliere Aggiungi servizio connesso dal menu di **scelta rapida.**

1. Nella scheda **Servizi connessi** selezionare l'icona + per **Dipendenze servizio**.

    ![Aggiungere una dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **database SQL di Azure**.

    ![Aggiungere database SQL di Azure servizio](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Se non è già stato eseguito l'accesso, accedere all'account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita.](https://azure.microsoft.com/account/free)

1. Nella schermata **Configura database SQL di Azure** selezionare un database SQL di Azure esistente e selezionare **Avanti.**

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connessione al componente database SQL di Azure esistente](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Per creare un database SQL di Azure:

   1. Selezionare **Crea un database SQL** nella parte inferiore della schermata.

   1. Compilare la **database SQL di Azure: Crea nuova** schermata e selezionare **Crea**.

       ![Nuovo database SQL di Azure](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Quando viene **visualizzata la schermata Configura** database SQL di Azure database, il nuovo database viene visualizzato nell'elenco. Selezionare il nuovo database nell'elenco e selezionare **Avanti.**

1. Immettere un nome di stringa di connessione o scegliere l'impostazione predefinita e scegliere se archiviare la stringa di connessione in un file di segreti locale [o](/azure/key-vault)in Azure Key Vault .

   ![Specificare la stringa di connessione](./media/azure-sql-database-add-connected-service/connection-string.png)

1. La **schermata Riepilogo delle** modifiche mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sono ok, scegliere **Fine.**

   ![Riepilogo delle modifiche](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Se viene richiesto di impostare le regole del firewall, scegliere **Sì.**

   ![Regole del firewall](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. La connessione viene visualizzata nella **sezione Dipendenze** servizio della **scheda** Servizi connessi connessione.

   ![Dipendenze dei servizi](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedi anche

- [database SQL di Azure prodotto](https://azure.microsoft.com/services/sql-database/)
- [Documentazione sul database SQL di Azure](/azure/azure-sql/database/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
