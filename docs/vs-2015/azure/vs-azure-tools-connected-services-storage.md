---
title: Aggiungere spazio di archiviazione di Azure tramite servizi connessi in Visual Studio | Microsoft Docs
description: Aggiungere archiviazione di Azure all'App usando la finestra di dialogo di Visual Studio aggiungere servizi connessi
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002340"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Aggiunta dell'archiviazione di Azure tramite servizi connessi di Visual Studio
Con Visual Studio, è possibile connettersi le seguenti operazioni in archiviazione di Azure usando il **Aggiungi servizi connessi** finestra di dialogo:

- C#servizio cloud
- Servizio mobile back-end .NET
- Sito Web ASP.NET o servizio
- Servizio ASP.NET Core
- Servizio processo Web Azure 

La funzionalità servizio connesso aggiunge tutti i riferimenti richiesti e il codice di connessione al progetto e modifica i file di configurazione in modo appropriato. 

Dopo il completamento, il **Aggiungi servizi connessi** finestra di dialogo automaticamente consente di visualizzare la documentazione che illustra in dettaglio i passaggi necessari per iniziare a usare archiviazione blob, code e tabelle.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Connettersi ad archiviazione di Azure usando la finestra di dialogo servizi connessi
1. Aprire il progetto in Visual Studio

1. Nella **Esplora soluzioni**, fare doppio clic il **servizi connessi** nodo, quindi scegliere il menu di scelta rapida e selezionare **Aggiungi servizio connesso**.
   
    ![Aggiungere Azure servizio connesso](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Nel **servizi connessi** pagina, selezionare **archiviazione Cloud con archiviazione di Azure**.
   
    ![Aggiungere archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Nel **archiviazione di Azure** finestra di dialogo, selezionare un account di archiviazione e scegliere **Add**.
   
    Se è necessario creare un account di archiviazione, andare al passaggio successivo. In caso contrario, andare al passaggio 6.
    
    ![Aggiungere account di archiviazione esistente al progetto](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Per creare un account di archiviazione: 
   
   1. Selezionare **creare un nuovo Account di archiviazione** nella parte inferiore della finestra di dialogo.

   1. Compilare il **crea Account di archiviazione** finestra di dialogo e selezionare **crea**.
      
       ![Nuovo account di archiviazione di Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. Quando la **archiviazione di Azure** viene visualizzata una finestra di dialogo, il nuovo account di archiviazione viene visualizzata nell'elenco. Selezionare il nuovo account di archiviazione nell'elenco e selezionare **Add**.

1. Lo spazio di archiviazione servizio connesso viene visualizzato sotto il **riferimenti al servizio** nodo del progetto.
   
## <a name="how-your-project-is-modified"></a>Come viene modificato il progetto
Al termine della finestra di dialogo, Visual Studio aggiunge riferimenti e modifica di alcuni file di configurazione. Le modifiche specifiche dipendono dal tipo di progetto: 

- Progetto ASP.NET - [informazioni sull'evento – progetti ASP.NET](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- Progetto ASP.NET Core - [informazioni sull'evento – progetti ASP.NET 5](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- Progetto servizio cloud (ruoli web e ruoli di lavoro) - [informazioni sull'evento – progetti del servizio Cloud](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- Progetto WebJob - [risultati - progetti processo Web](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Passaggi successivi
- [Forum MSDN: Archiviazione di Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog del Team di archiviazione di Microsoft Azure](http://blogs.msdn.com/b/windowsazurestorage/)
- [Documentazione di archiviazione di Azure](https://docs.microsoft.com/azure/storage/)
