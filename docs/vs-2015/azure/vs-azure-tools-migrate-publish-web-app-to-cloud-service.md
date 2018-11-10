---
title: Come eseguire la migrazione e pubblicare un'applicazione Web a un servizio Cloud di Azure da Visual Studio | Microsoft Docs
description: Informazioni su come eseguire la migrazione e pubblicare l'applicazione web a un servizio cloud di Azure con Visual Studio
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c122b54a4e22285678d13213cc73d6492baba629
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003041"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Procedura: eseguire la migrazione e pubblicare un'applicazione Web a un servizio Cloud di Azure da Visual Studio

Per sfruttare i vantaggi dei servizi di hosting e scalabilità di Azure, si potrebbe voler eseguire la migrazione e distribuire l'applicazione web a un servizio cloud di Azure. Sono necessarie solo modifiche minime. Questo articolo illustra la distribuzione in servizi cloud di sola lettura. per il servizio App, vedere [distribuire un'app web nel servizio App di Azure](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Questa migrazione è supportata solo per i progetti ASP.NET, Silverlight, WCF e flusso di lavoro WCF specifici. Non è supportata per i progetti ASP.NET Core. Visualizzare [modelli di progetto supportati](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Eseguire la migrazione di un progetto di servizi cloud

1. Il progetto di applicazione web e scegliere **Converti > Converti in progetto servizio Cloud di Microsoft Azure**. Si noti che questo comando non viene visualizzato se si dispone già di un progetto di ruolo web nella soluzione.
1. Visual Studio crea un progetto servizio cloud nella soluzione che contiene il ruolo web richiesto. Il nome di questo progetto corrisponde al progetto dell'applicazione con più il suffisso `.Azure`.
1. Visual Studio imposta anche il **Copia localmente** proprietà su true per qualsiasi assembly necessario per MVC 2, MVC 3, MVC 4 e applicazioni aziendali di Silverlight. Questa proprietà consente di aggiungere questi assembly al pacchetto del servizio che viene usato per la distribuzione.

   > [!Important]
   > Se si dispone di altri assembly o i file necessari per l'applicazione web, è necessario impostare manualmente le proprietà per questi file. Per informazioni su come impostare queste proprietà, vedere [includere file nel pacchetto del servizio](#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Errori e avvisi

Eventuali avvisi o errori che si verificano indicano problemi da risolvere prima di distribuire in Azure, ad esempio assembly mancanti.

Se si compila la tua applicazione, eseguirla localmente utilizzando l'emulatore di calcolo o pubblicarla in Azure, si potrebbe essere visualizzato l'errore: "il percorso specificato, nome del file o entrambi sono troppo lunghi." Questo errore indica che lunghezza del nome completo del progetto Azure superiore a 146 caratteri. Per correggere il problema, spostare la soluzione in una cartella diversa con un percorso più breve.

Per altre informazioni su come trattare tutti gli avvisi come errori, vedere [configurare un progetto servizio Cloud di Azure con Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Testare la migrazione in locale

1. In Visual Studio **Esplora soluzioni**, fare clic sul progetto servizio cloud aggiunto e selezionare **imposta come progetto di avvio**.
1. Selezionare **Debug > Avvia debug** (F5) per avviare l'ambiente di debug di Azure. Questo ambiente, in particolare, fornisce emulazione di vari servizi di Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Usare un Database SQL di Azure per l'applicazione

Se si dispone di una stringa di connessione per l'applicazione web che usa un database di SQL Server in locale, è necessario eseguire la migrazione del database SQL di Azure invece e aggiornare la stringa di connessione. Per istruzioni su questo processo, vedere gli argomenti seguenti:

- [Migrazione di database di SQL Server al Database SQL nel cloud](/azure/sql-database/sql-database-cloud-migrate)
- [Usare .NET (C#) con Visual Studio per connettersi ed eseguire query e database SQL di Azure](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Pubblicare l'applicazione di servizio Cloud di Azure

1. Creare i cloud necessari account di archiviazione e del servizio nella sottoscrizione di Azure come descritto in [preparare la pubblicazione o distribuzione di un'applicazione Azure da Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. In Visual Studio, fare doppio clic sul progetto di applicazione e selezionare **pubblica in Microsoft Azure...**  (che è diverso dal comando "Pubblica in corso".).
1. Nel **pubblica applicazione Azure** che viene visualizzata, accedere usando l'account nella sottoscrizione di Azure e selezionare **successiva >**.
1. Nel **Impostazioni > Impostazioni comuni** scheda, selezionare il servizio cloud di destinazione dalle **servizio Cloud** elenco a discesa, insieme all'ambiente selezionato e alle configurazioni. 
1. Nelle **Impostazioni > Impostazioni avanzate**, selezionare l'account di archiviazione da usare, quindi selezionare **successiva >**.
1. Nelle **diagnostica**, decidere se inviare informazioni ad Application Insights.
1. Selezionare **Avanti >** per visualizzare un riepilogo, quindi selezionare **Publish** per avviare la distribuzione.
1. Visual Studio apre una finestra log attività in cui è possibile tenere traccia dello stato:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Facoltativo) Per annullare il processo di distribuzione, fare doppio clic la voce nel log attività e scegliere **Annulla e Rimuovi**. Questo comando Arresta il processo di distribuzione ed elimina l'ambiente di distribuzione da Azure. Nota: per rimuovere questo ambiente di distribuzione dopo che è stato distribuito, è necessario usare il [portale di Azure](https://portal.azure.com).
1. (Facoltativo) Una volta avviate le istanze del ruolo, Visual Studio Mostra automaticamente l'ambiente di distribuzione nel **Esplora Server > servizi Cloud** nodo. Da qui è possibile visualizzare lo stato di singole istanze del ruolo.
1. Per accedere all'applicazione dopo la distribuzione, scegliere la freccia accanto alla distribuzione quando lo stato **Completed** viene visualizzato nei **log attività di Azure** insieme all'URL. Vedere la tabella seguente per informazioni dettagliate su come avviare un tipo specifico di applicazione web di Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Usando l'emulatore di calcolo e avvio dell'applicazione in Azure

Tutti i tipi di applicazioni possono essere avviati in un browser connesso al debugger di Visual Studio selezionando **Debug > Avvia debug** (F5). Con un progetto di applicazione Web ASP.NET vuota, è innanzitutto necessario aggiungere un `.aspx` pagina nell'applicazione e impostarla come pagina iniziale per il progetto web.

Nella tabella seguente fornisce informazioni dettagliate sull'avvio dell'applicazione in Azure:

   | Tipo di applicazione Web | In esecuzione in Azure |
   | --- | --- | --- |
   | Applicazione Web ASP.NET<br/>(inclusi MVC 2, MVC 3, MVC 4) | Selezionare l'URL nel **distribuzione** scheda per il **log attività di Azure**. |
   | Applicazione Web ASP.NET vuota | Se si dispone di un valore predefinito `.aspx` pagina nell'applicazione, selezionare l'URL nel **distribuzione** scheda per il **log attività di Azure**. Per passare a una pagina diversa, immettere un URL nel formato seguente in un browser: `<deployment_url>/<page_name>.aspx` |
   | Applicazione Silverlight<br/>Applicazione aziendale di Silverlight<br/>Applicazione di navigazione Silverlight | Passare alla pagina specifica per l'applicazione usando il formato di URL seguente: `<deployment_url>/<page_name>.aspx` |
    Applicazione del servizio WCF<br/>Applicazione servizi flusso di lavoro WCF | Impostare il `.svc` file come pagina iniziale per il progetto di servizio WCF. Quindi passare a `<deployment_url>/<service_file>.svc` |
   | Entità dinamiche ASP.NET<br/>Linq to SQL ASP.NET Dynamic Data | Aggiornare la stringa di connessione come descritto nella sezione successiva. Passare quindi a `<deployment_url>/<page_name>.aspx`. Per Linq to SQL, è necessario usare un database SQL di Azure. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aggiornare una stringa di connessione per entità dinamiche ASP.NET

1. Creare un database di SQL Azure per un'applicazione web entità dinamiche ASP.NET, come descritto in precedenza (#use-an-azuresql-database-for-your-application).
1. Aggiungere le tabelle e i campi necessari per il database dal portale di Azure.
1. Specificare una stringa di connessione nel `web.config` file con il formato seguente e salvare il file:

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    Aggiorna il *connectionString* valore con la stringa di connessione ADO.NET per il database di SQL Azure come indicato di seguito:

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Modelli di progetto supportati

Le applicazioni che possono essere migrate e pubblicate in servizi cloud devono usare uno dei modelli nella tabella seguente. ASP.NET Core non è supportato.

| Gruppo di modelli | Modello di progetto |
| --- | --- |
| Web | Applicazione Web ASP.NET (.NET Framework) |
| Web | Applicazione Web ASP.NET MVC 2 |
| Web | Applicazione Web ASP.NET MVC 3 |
| Web | Applicazione Web ASP.NET MVC4 |
| Web | Applicazione Web ASP.NET vuota (o un sito) |
| Web | Applicazione Web vuota ASP.NET MVC 2 |
| Web | Applicazione Web entità ASP.NET Dynamic Data |
| Web | Linq ASP.NET Dynamic Data per l'applicazione Web SQL |
| Silverlight | Applicazione Silverlight |
| Silverlight | Applicazione aziendale di Silverlight |
| Silverlight | Applicazione di navigazione Silverlight |
| WCF | Applicazione del servizio WCF |
| WCF | Applicazione servizi flusso di lavoro WCF |
| Flusso di lavoro | Applicazione servizi flusso di lavoro WCF |

## <a name="next-steps"></a>Passaggi successivi

- [Preparare la pubblicazione o distribuzione di un'applicazione Azure da Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Configurazione delle credenziali di autenticazione denominate](vs-azure-tools-setting-up-named-authentication-credentials.md).
