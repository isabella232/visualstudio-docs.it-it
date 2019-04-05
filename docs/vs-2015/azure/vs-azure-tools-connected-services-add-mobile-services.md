---
title: Aggiunta di servizi mobili tramite servizi connessi
description: Aggiungere servizi mobili usando la finestra di dialogo di Visual Studio aggiungere servizi connessi
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
ms.openlocfilehash: 4bfda342952820b4472a1f826273a7b9075faa9a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954886"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Aggiunta di servizi mobili tramite servizi connessi di Visual Studio
Con Visual Studio 2015, è possibile connettersi a servizi mobili di Azure usando il **Aggiungi servizio connesso** finestra di dialogo. È possibile connettersi da qualsiasi C# app client, qualsiasi app JavaScript o app Cordova multipiattaforma. Dopo essersi connessi, è possibile creare e accedere ai dati, creare API personalizzate e i processi pianificati o aggiungere il supporto per le notifiche push.  L'operazione di servizi connessi aggiunge tutti i riferimenti appropriati e il codice di connessione. È anche possibile sfruttare i vantaggi del supporto incorporato per l'autenticazione con un'ampia gamma di sistemi di identità comuni, ad esempio Azure AD, Facebook, Twitter e Microsoft Accounts.

## <a name="supported-project-types"></a>Tipi di progetto supportati
> [!NOTE]
> In Visual Studio 2015, l'aggiunta di servizi mobili di Azure a un progetto Windows universale (Windows 10) usando la finestra di dialogo Aggiungi servizi connessi non è supportato. È possibile aggiungere servizi mobili di Azure installando i pacchetti appropriati usando Gestione pacchetti NuGet per il progetto.
>
>

È possibile usare la finestra di dialogo servizi connessi per connettersi a servizi mobili di Azure nei seguenti tipi di progetto.

* Progetti .NET Windows 8.1 Store, Phone e Universal App
* Progetti JavaScript Windows 8.1 Store, Phone e Universal App
* Progetti creati con Visual Studio Tools per Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Connettersi a servizi mobili di Azure usando la finestra di dialogo Aggiungi servizi connessi
1. Assicurarsi di avere un account Azure. Se non hai un account Azure, è possibile iscriversi a un [versione di valutazione gratuita](http://go.microsoft.com/fwlink/?LinkId=518146).
2. Aprire il **Aggiungi servizi connessi** nella finestra di dialogo.

   * Per le app .NET, aprire il progetto in Visual Studio, aprire il menu di scelta rapida per il **riferimenti** nodo in Esplora soluzioni, quindi scegliere **Aggiungi servizio connesso**

        ![La connessione al servizio Mobile di Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Per i progetti di app Apache Cordova, aprire il progetto in Visual Studio, aprire il menu di scelta rapida per il nodo del progetto in Esplora soluzioni e quindi scegliere **Aggiungi servizio connesso**.
3. Nel **Aggiungi servizio connesso** finestra di dialogo scegliere **servizi mobili di Azure**, quindi scegliere il **configura** pulsante. Potrebbe essere richiesto di accedere ad Azure se non è già fatto.

    ![Aggiunta di un servizio Mobile di Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Nel **servizi mobili di Azure** finestra di dialogo, scegliere un servizio mobile esistente se ne hai uno. Se è necessario creare un nuovo servizio mobile di Azure, seguire la procedura seguente per eseguire questa operazione. In caso contrario, andare al passaggio successivo.

    Per creare un nuovo account di servizio mobile:

   1. Scegliere il **Create Service** collegamento nella parte inferiore della finestra di dialogo.
       ![Aggiungi nuovo servizio mobile connesso](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Nel **Crea servizio Mobile** della finestra di dialogo è possibile scegliere un servizio mobile back-end JavaScript, o un servizio mobile back-end .NET dalle **Runtime** elenco a discesa.

       ![Creazione di un servizio mobile](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Un servizio back-end JavaScript è semplice e potente. Se si crea un servizio mobile back-end JavaScript, il codice JavaScript lato server viene archiviato nel cloud, ma è possibile modificare gli script del server tramite Esplora Server o il portale di gestione di Azure.

       Un servizio mobile back-end .NET ti offre tutta la potenza e flessibilità dell'API Web ed Entity Framework. Se si crea un servizio mobile back-end .NET, un progetto viene creato e aggiunto alla soluzione.
   3. Scegliere il **regione** in cui si desidera che il servizio mobile e quindi immettere un nome utente e una password per il server.
   4. Dopo aver immesso tutte le informazioni necessarie, scegliere il **Create** pulsante per creare il servizio mobile.
   5. Il nuovo servizio mobile deve essere visualizzato nell'elenco dei servizi nel **servizi mobili di Azure** nella finestra di dialogo. Scegliere il nuovo servizio mobile nell'elenco e quindi scegliere il **Add** pulsante per aggiungere il servizio al progetto.
5. Esaminare la pagina introduttiva visualizzata e Scopri come è stato modificato il progetto. Ogni volta che si aggiunge un servizio connesso, viene visualizzata una pagina Guida introduttiva nel browser. È possibile esaminare i passaggi successivi suggeriti e gli esempi di codice o passare alla pagina che cosa è successo per vedere quali riferimenti sono stati aggiunti al progetto e come sono stati modificati i file di codice e la configurazione.
6. Usando gli esempi di codice come guida, iniziare a scrivere codice per accedere al servizio mobile.

## <a name="how-your-project-is-modified"></a>Come viene modificato il progetto
Modo in cui Visual Studio modifica il progetto dipende dal tipo di progetto. Per C# App client, vedere [informazioni sull'evento – C# progetti](http://go.microsoft.com/fwlink/p/?LinkId=513119). Per le app client JavaScript, vedere [risultati-progetti JavaScript](http://go.microsoft.com/fwlink/p/?LinkId=513120). Per le app Cordova, vedere [risultati-progetti Cordova](http://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Passaggi successivi
Porre domande e ottenere assistenza:

* [Forum MSDN: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Servizi mobili di Azure nel Blog del Team di Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Servizi mobili di Azure in azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentazione di servizi mobili di Azure in azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
