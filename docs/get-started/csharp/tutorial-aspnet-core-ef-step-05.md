---
title: "Passaggio 5: Distribuzione dell'app ASP.NET Core in Azure"
description: Distribuire l'App Web di ASP.NET Core in Azure con questo video di esercitazione e per istruzioni dettagliate.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 2d995818ec5b8ac01c9776bbf2290da39d2cc40b
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018103"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Passaggio 5: Distribuire l'app ASP.NET Core in Azure

Seguire questi passaggi per distribuire l'app ASP.NET Core e il relativo database in Azure.

_Guardare questo video e seguire le indicazioni per distribuire la prima app ASP.NET Core in Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Aprire il progetto

Aprire l'app ASP.NET Core in Visual Studio 2019. L'app deve essere già configurata con EF Core e un'API Web funzionante, come descritto nel [passaggio 4 di questa serie di esercitazioni](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

Fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Pubblica**. Lasciare le impostazioni predefinite **Servizio app** e **Crea nuovo**, quindi fare clic sul pulsante **Pubblica**. Se non si ha già un account Azure, fare clic su **Crea un account Azure gratuito** e completare il breve processo di registrazione.

Aggiungere un'istanza di SQL Server. Specificare nome utente e password di un amministratore.

![Visual Studio 2019 - Creare il server di Azure SQL](media/vs-2019/vs2019-azure-sql-server.png)

Aggiungere Application Insights.

Fare clic sul pulsante **Crea** per continuare.

![Visual Studio 2019 - Creare un nuovo servizio app di Azure](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Esplorare il portale di Azure e l'app ospitata

Dopo aver creato il servizio app, il sito verrà avviato in un browser. Durante il caricamento è anche possibile trovare il servizio app nel portale di Azure. Esplorando le opzioni disponibili per il servizio app si troverà una sezione **Panoramica** da cui è possibile avviare e arrestare l'app.

![Opzioni del servizio app di Azure](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Scalabilità

È possibile esaminare le opzioni per la scalabilità dell'app. È possibile aumentare le risorse assegnate a ogni istanza che ospita l'app oppure aumentare il numero di istanze che ospitano l'app. Si può anche configurare la scalabilità automatica per l'app, in modo da aumentare automaticamente il numero di istanze usate per ospitare l'app in risposta al carico, per poi ridurle quando il carico diminuisce.

### <a name="security-and-compliance"></a>Sicurezza e conformità

Altri vantaggi dell'hosting di app con Azure sono la sicurezza e la conformità. Servizio app di Azure offre la conformità ISO, SOC e PCI. È possibile scegliere di autenticare gli utenti con Azure Active Directory o account di accesso per social network quali Twitter, Facebook, Google o Microsoft. Si possono creare restrizioni IP, gestire le identità del servizio, aggiungere domini personalizzati e supportare SSL per l'app, oltre a configurare i backup con copie di archiviazione ripristinabili del contenuto, della configurazione e del database dell'app. Queste funzionalità sono accessibili tramite le opzioni di menu Autenticazione/Autorizzazione, Identità, Backup e Impostazioni SSL.

### <a name="deployment-slots"></a>Slot di distribuzione

Spesso, quando si distribuisce un'app, è presente un breve periodo di inattività mentre l'app viene riavviata. Gli slot di distribuzione evitano questo problema, consentendo di distribuire in un'istanza o un set di istanze di gestione temporanea separati e di riscaldarli prima di metterli in produzione. Lo scambio è semplicemente un reindirizzamento del traffico facile e immediato. Se si verificano problemi nell'ambiente di produzione dopo lo scambio, è possibile tornare sempre all'ultimo stato di produzione valido.

## <a name="update-connection-string"></a>Aggiornare la stringa di connessione

Per impostazione predefinita, Azure prevede che la connessione di una nuova app al nuovo database di SQL Server usi una stringa di connessione denominata `DefaultConnection`. L'app creata in precedenza in questa serie di esercitazioni usa attualmente una stringa di connessione denominata `AppDbContext`. È necessario modificare questo valore in *appsettings.json* e *Startup.cs*, quindi ridistribuire l'app.

## <a name="test-the-app-running-in-azure"></a>Testare l'app in esecuzione in Azure

Passare al percorso */Games*. Dovrebbe essere possibile aggiungere un nuovo gioco e visualizzarlo nell'elenco. Passare quindi al percorso */swagger*. Dovrebbe essere possibile usare gli endpoint dell'API Web da questa posizione per verificare che anche l'API dell'app funzioni correttamente.

La procedura è stata completata. Questa serie di esercitazioni video è ora completa.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni su come progettare applicazioni ASP.NET Core con queste risorse gratuite.

[Architettura delle applicazioni ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Vedere anche

- [Pubblicare un'app ASP.NET Core in Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)