---
title: Aggiunta di servizi mobili tramite Servizi connessi
description: Aggiungere servizi mobili tramite la finestra di dialogo Aggiungi Servizi connessi di Visual Studio
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300188"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Aggiunta di servizi mobili con Visual Studio Servizi connessi
Con Visual Studio 2015 è possibile connettersi a servizi mobili di Azure usando la finestra di dialogo **Aggiungi servizio connesso** . È possibile connettersi da qualsiasi C# app client, qualsiasi app JavaScript o app Cordova multipiattaforma. Una volta stabilita la connessione, è possibile creare e accedere ai dati, creare API personalizzate e processi pianificati o aggiungere il supporto per le notifiche push.  L'operazione relativa ai servizi connessi aggiunge tutti i riferimenti appropriati e il codice di connessione. Puoi anche sfruttare il supporto integrato per l'autenticazione con diversi schemi di identità comuni, come Azure AD, Facebook, Twitter e account Microsoft.

## <a name="supported-project-types"></a>Tipi di progetto supportati
> [!NOTE]
> In Visual Studio 2015, l'aggiunta di servizi mobili di Azure a un progetto di Windows universale (Windows 10) tramite la finestra di dialogo Aggiungi Servizi connessi non è supportata. È possibile aggiungere servizi mobili di Azure installando i pacchetti appropriati usando Gestione pacchetti NuGet per il progetto.
>
>

È possibile usare la finestra di dialogo Servizi connessi per connettersi a servizi mobili di Azure nei tipi di progetto seguenti.

* Progetti .NET Windows 8.1 Store, Phone e Universal app
* Progetti di Windows 8.1 JavaScript Store, Phone e Universal app
* Progetti creati con Strumenti di Visual Studio per Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Connettersi a servizi mobili di Azure usando la finestra di dialogo Aggiungi Servizi connessi
1. Assicurarsi di avere un account Azure. Se non si ha un account Azure, è possibile iscriversi per ottenere una [versione di valutazione gratuita](https://go.microsoft.com/fwlink/?LinkId=518146).
2. Aprire la finestra di dialogo **aggiungi servizi connessi** .

   * Per le app .NET, aprire il progetto in Visual Studio, aprire il menu di scelta rapida per il nodo **riferimenti** in Esplora soluzioni, quindi scegliere **Aggiungi servizio connesso** .

        ![Connessione al servizio mobile di Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Per Apache Cordova progetti di app, aprire il progetto in Visual Studio, aprire il menu di scelta rapida per il nodo del progetto in Esplora soluzioni, quindi scegliere **Aggiungi servizio connesso**.
3. Nella finestra di dialogo **Aggiungi servizio connesso** scegliere **servizi mobili di Azure**, quindi fare clic sul pulsante **Configura** . È possibile che venga richiesto di accedere ad Azure, se non è già stato fatto.

    ![Aggiunta di un servizio mobile di Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Nella finestra di dialogo **servizi mobili di Azure** scegliere un servizio mobile esistente, se presente. Se è necessario creare un nuovo servizio mobile di Azure, seguire la procedura riportata di seguito. In caso contrario, andare al passaggio successivo.

    Per creare un nuovo account di servizio mobile:

   1. Scegliere il collegamento **Crea servizio** nella parte inferiore della finestra di dialogo.
       ![aggiungere un nuovo servizio mobile connesso](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Nella finestra di dialogo **Crea servizio mobile** è possibile scegliere un servizio mobile back-end JavaScript o un servizio mobile back-end .NET dall'elenco a discesa **Runtime** .

       ![Creazione di un servizio mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Un servizio back-end JavaScript è semplice e potente. Se si crea un servizio mobile back-end JavaScript, il codice JavaScript sul lato server viene archiviato nel cloud, ma è possibile modificare gli script del server usando Esplora server o il portale di gestione di Azure.

       Un servizio mobile back-end .NET offre tutta la potenza e la flessibilità dell'API Web e Entity Framework. Se si crea un servizio mobile back-end .NET, viene creato un progetto e viene aggiunto alla soluzione.
   3. Scegliere l' **area** in cui si desidera il servizio mobile e quindi immettere un nome utente e una password per il server.
   4. Dopo aver immesso tutte le informazioni necessarie, scegliere il pulsante **Crea** per creare il servizio mobile.
   5. Il nuovo servizio mobile dovrebbe essere visualizzato nell'elenco dei servizi nella finestra di dialogo **servizi mobili di Azure** . Scegliere il nuovo servizio mobile nell'elenco, quindi scegliere il pulsante **Aggiungi** per aggiungere il servizio al progetto.
5. Esaminare la pagina introduttiva visualizzata e scoprire come è stato modificato il progetto. Quando si aggiunge un servizio connesso, viene visualizzata una pagina Introduzione nel browser. È possibile esaminare i passaggi successivi suggeriti e gli esempi di codice oppure passare alla pagina cosa è accaduto per vedere quali riferimenti sono stati aggiunti al progetto e come sono stati modificati i file di codice e di configurazione.
6. Usando gli esempi di codice come guida, iniziare a scrivere il codice per accedere al servizio mobile.

## <a name="how-your-project-is-modified"></a>Come viene modificato il progetto
Il modo in cui Visual Studio modifica il progetto dipende dal tipo di progetto. Per C# le app client, vedere [cosa è C# successo – progetti](https://go.microsoft.com/fwlink/p/?LinkId=513119). Per le app client JavaScript, vedere [cosa è successo – progetti JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=513120). Per le app Cordova, vedere [cosa è successo – progetti Cordova](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Passaggi successivi
Porre domande e ottenere assistenza:

* [Forum MSDN: Servizi mobili di Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Servizi mobili di Azure nel Blog del team di Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Servizi mobili di Azure in azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentazione di servizi mobili di Azure in azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
