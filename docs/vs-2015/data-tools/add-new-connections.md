---
title: Aggiungere nuove connessioni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13398a1b0aebc921c9600518c87888bd2b5cdea7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519999"
---
# <a name="add-new-connections"></a>Aggiungere nuove connessioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiungere le nuove connessioni](https://docs.microsoft.com/visualstudio/data-tools/add-new-connections).  
  
  
È possibile testare la connessione a un database o un servizio ed esplorare i contenuti del database e schemi, utilizzando **Esplora Server**, **Cloud Explorer**, o **Esplora oggetti di SQL Server**. La funzionalità di queste finestre si sovrappone a una certa misura. Le differenze di base sono:  
  
 Esplora server  
 Installato per impostazione predefinita in Visual Studio. Utilizzabile per testare le connessioni e visualizzare i database di SQL Server, ad altri database che hanno installato un provider ADO.NET e alcuni servizi di Azure. Mostra anche gli oggetti di basso livello, ad esempio i contatori delle prestazioni di sistema, registri eventi e le code di messaggi. Se un'origine dati non dispone di alcun provider ADO.NET, non verranno visualizzati qui, ma è comunque possibile usarlo da Visual Studio tramite la connessione a livello di codice.  
  
 Cloud Explorer  
 Installare manualmente questa finestra come un'estensione di Visual Studio selezionando **degli strumenti** > **estensioni e aggiornamenti** > **Online**  >  **Visual Studio Gallery**. Fornisce funzionalità specializzate per l'esplorazione e la connessione a servizi di Azure.  
  
 Esplora oggetti di SQL Server  
 Installato con SQL Server Data Tools e visibile sotto il **vista** menu. Se non viene visualizzato non esiste, andare al **programmi e funzionalità** nel Pannello di controllo Cerca Visual Studio e quindi selezionare **modifica** per eseguire nuovamente il programma di installazione dopo aver selezionato la casella di controllo per SQL Server Data Tools. Uso **Esplora oggetti di SQL Server** ai database SQL di visualizzazione (se dispongono di un provider ADO.NET), creare nuovi database, modificare gli schemi, creare stored procedure, recuperare le stringhe di connessione, visualizzare i dati e altro ancora. Database SQL di cui non sono installato alcun provider ADO.NET non verranno visualizzate qui, ma può comunque connettersi a essi a livello di codice.  
  
## <a name="add-a-connection-in-server-explorer"></a>Aggiungere una connessione in Esplora Server  
 Per creare una connessione al database, fare clic sui **Aggiungi connessione** icona nella **Esplora Server**, o fare doppio clic nella **Esplora Server** nel **dati Le connessioni** nodo e selezionare **Aggiungi connessione**. A questo punto, è anche possibile connettersi a un database in un altro server, un servizio di SharePoint o un servizio di Azure.  
  
 ![Icona nuova connessione di Esplora server](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata sull'icona di connessione al nuovo Esplora Server")  
  
 Verrà visualizzata la **Aggiungi connessione** nella finestra di dialogo. In questo caso, è stato immesso il nome dell'istanza di LocalDB di SQL Server.  
  
 ![Aggiungi nuova connessione](../data-tools/media/raddata-add-new-connection-dialog.png "raddata Aggiungi nuova finestra di dialogo di connessione")  
  
## <a name="change-the-provider"></a>Modificare il provider  
 Se l'origine dati non si desidera, fare clic il **modifica** pulsante per selezionare una nuova origine dati e/o un nuovo provider di dati ADO.NET. Il nuovo provider potrebbe chiedere le credenziali, a seconda di come è stato configurato.  
  
 ![Modificare il Provider di dati AD0.NET](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata Provider di dati di modifica AD0.NET")  
  
## <a name="test-the-connection"></a>Testare la connessione  
 Dopo aver scelto l'origine dati, fare clic su **Test connessione**. Se non viene completato, è necessario risolvere i problemi di base la documentazione del fornitore.  
  
 ![Test connessione](../data-tools/media/raddata-test-connection.png "raddata Test connessione")  
  
 Se il test ha esito positivo, si è pronti per creare un *zdroj dat*, che è un termine di Visual Studio che in realtà indica una *modello di dati* basato sul database o del servizio sottostante.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

