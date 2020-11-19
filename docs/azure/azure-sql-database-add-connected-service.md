---
title: Aggiungere una connessione al database SQL di Azure | Microsoft Docs
description: Aggiungere la connessione al database SQL di Azure all'app usando Visual Studio Servizi connessi
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4d720c51d7245d60d40c286c71976132a119a56f
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902870"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Aggiungere una connessione al database SQL di Azure

Con Visual Studio, è possibile connettere uno dei seguenti al database SQL di Azure usando la funzionalità **servizi connessi** :

- App console .NET Framework
- MVC ASP.NET (.NET Framework) 
- ASP.NET Core
- .NET Core (incluse app console, WPF, Windows Forms, libreria di classi)
- Ruolo di lavoro .NET Core
- Funzioni di Azure
- App piattaforma UWP (Universal Windows Platform)
- Xamarin
- Cordova

La funzionalità servizio connesso aggiunge al progetto tutti i riferimenti richiesti e il codice di connessione e modifica i file di configurazione in modo appropriato.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Servizi connessi in Visual Studio per Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro di Azure installato.
- Progetto di uno dei tipi supportati

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Connettersi al database SQL di Azure usando Servizi connessi

1. Aprire il progetto in Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **servizi connessi** e scegliere **Aggiungi servizio connesso** dal menu di scelta rapida.

1. Nella scheda **servizi connessi** selezionare l'icona + per le **dipendenze del servizio**.

    ![Aggiungi dipendenza del servizio](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Nella pagina **Aggiungi dipendenza** selezionare **database SQL di Azure**.

    ![Aggiungere il servizio database SQL di Azure](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Se non è già stato effettuato l'accesso, accedere al proprio account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://azure.microsoft.com/account/free).

1. Nella schermata **Configura database SQL di Azure** selezionare un database SQL di Azure esistente e fare clic su **Avanti**.

    Se è necessario creare un nuovo componente, andare al passaggio successivo. In caso contrario, andare al passaggio 7.

    ![Connettersi a un componente del database SQL di Azure esistente](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Per creare un database SQL di Azure:

   1. Selezionare **Crea un database SQL** nella parte inferiore della schermata.

   1. Compilare il **database SQL di Azure: Crea nuova** schermata e selezionare **Crea**.

       ![Nuovo database SQL di Azure](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Quando viene visualizzata la schermata **Configura database SQL di Azure** , il nuovo database viene visualizzato nell'elenco. Selezionare il nuovo database nell'elenco e fare clic su **Avanti**.

1. Immettere un nome per la stringa di connessione o scegliere l'impostazione predefinita e scegliere se si desidera che la stringa di connessione venga archiviata in un file dei segreti locali o in [Azure Key Vault](/azure/key-vault).

   ![Specificare la stringa di connessione](./media/azure-sql-database-add-connected-service/connection-string.png)

1. La schermata **Riepilogo modifiche** Mostra tutte le modifiche che verranno apportate al progetto se si completa il processo. Se le modifiche sembrano OK, scegliere **fine**.

   ![Riepilogo delle modifiche](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Se viene richiesto di impostare le regole del firewall, scegliere **Sì**.

   ![Regole del firewall](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. La connessione viene visualizzata nella sezione **dipendenze del servizio** della scheda **servizi connessi** .

   ![Dipendenze dei servizi](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Vedere anche

- [Pagina del prodotto del database SQL di Azure](https://azure.microsoft.com/services/sql-database/)
- [Documentazione sul database SQL di Azure](/azure/azure-sql/database/)
- [Servizi connessi (Visual Studio per Mac)](/visualstudio/mac/connected-services)
