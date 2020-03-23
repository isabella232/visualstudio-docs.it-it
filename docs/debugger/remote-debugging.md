---
title: Debug remoto - Documenti Microsoft
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302077"
---
# <a name="remote-debugging"></a>Debug remoto
È possibile eseguire il debug di un'applicazione Visual Studio che è stata distribuita in un computer diverso. A questo scopo si usa Visual Studio Remote Debugger.

Per istruzioni approfondite sul debug remoto, vedere questi argomenti.

|Scenario|Collegamento|
|-|-|-|
|Servizio app di Azure|Debugger snapshot o ASP.NET di debug remoto in [AzureSnapshot Debugger](../debugger/debug-live-azure-applications.md) [or Remote debug ASP.NET on Azure](../debugger/remote-debugging-azure.md)|
|Macchina virtuale di Azure|[Eseguire il debug remoto di ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Eseguire il debug di un'applicazione Azure Service FabricDebug an Azure Service Fabric application](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Debug remoto ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) o [ASP.NET di debug remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# o Visual Basic|[Eseguire il debug remoto di un progetto C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Debug remoto di un progetto in C](../debugger/remote-debugging-cpp.md)|
|App Windows universali (UWP)|[Eseguire app UWP in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) o Eseguire il debug di un pacchetto [dell'app installatoRun](../debugger/debug-installed-app-package.md) UWP apps on a remote machine or Debug an installed app package|

Se si desidera solo scaricare e installare il debugger remoto e non sono necessarie istruzioni aggiuntive per lo scenario, attenersi alla procedura descritta in questo articolo.

## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Requisiti

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Facoltativo) Per eseguire il debugger remoto da una condivisione fileTo run the remote debugger from a file share

Il debugger remoto (*msvsmon.exe*) è in un computer in cui è già installato Visual Studio Community, Professional o Enterprise. Per alcuni scenari, il modo più semplice per configurare il debug remoto consiste nell'eseguire il debugger remoto (msvsmon.exe) da una condivisione file. Per le limitazioni di utilizzo, vedere la pagina della Guida del debugger remoto **(Guida > utilizzo** nel debugger remoto).

1. Individuare *msvsmon.exe* nella directory corrispondente alla versione di Visual Studio:

   ::: moniker range=">=vs-2019"

   *File di programma (x86) Microsoft Visual Studio 2019, Enterprise, Common7, IDE, Debugger remoto, x86, msvsmon.exe*

   *File di programma (x86) Microsoft Visual Studio 2019, Enterprise, Common7, IDE, Debugger remoto, x64, msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *File di programma (x86) Microsoft Visual Studio 2017 Enterprise Common7 IDE , Debugger remoto , x86 , msvsmon.exe*

   *File di programma (x86) Microsoft Visual Studio 2017 Enterprise Common7 IDE , Debugger remoto , x64 msvsmon.exe*

   ::: moniker-end

2. Condividere la cartella **Debugger remoto** nel computer Visual Studio.

3. Nel computer remoto eseguire *msvsmon.exe* dalla cartella condivisa. Seguire le istruzioni di [configurazione](#bkmk_setup).

> [!TIP]
> Per informazioni di riferimento sull'installazione dalla riga di comando e ``msvsmon.exe /?`` sulla riga di comando, vedere la pagina della Guida di *msvsmon.exe* digitando nella riga di comando del computer in cui è installato Visual Studio oppure passare alla **Guida > utilizzo** nel debugger remoto.

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Configurare il debugger remoto
È possibile modificare alcuni aspetti della configurazione del debugger remoto dopo che è stata avviata per la prima volta.

- Se è necessario aggiungere autorizzazioni per consentire ad altri utenti di connettersi al debugger remoto, scegliere **Strumenti > Autorizzazioni**. È necessario disporre dei privilegi di amministratore per concedere o negare autorizzazioni.

     > [!IMPORTANT]
     > È possibile eseguire il debugger remoto con un account utente diverso da quello utilizzato nel computer Visual Studio, ma è necessario aggiungere l'account utente diverso alle autorizzazioni del debugger remoto.

     In alternativa, è possibile avviare il debugger remoto dalla riga di comando con il parametro ** \</allow nomeutente>:** **msvsmon \< username@computer /allow>**.

- Se è necessario modificare la modalità di autenticazione o il numero di porta oppure specificare un valore di timeout per gli strumenti remoti: scegliere **Strumenti > Opzioni**.

     Per un elenco dei numeri di porta utilizzati per impostazione predefinita, vedere [Assegnazioni di porte](../debugger/remote-debugger-port-assignments.md)del debugger remoto .

     > [!WARNING]
     > È possibile scegliere di eseguire Remote Tools in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Facoltativo) Configurare il debugger remoto come servizioConfigure the remote debugger as a service
Per il debug in ASP.NET e in altri ambienti server, è necessario eseguire il debugger remoto come amministratore oppure, se si desidera che venga sempre eseguito, eseguire il debugger remoto come servizio.

 Se si desidera configurare il debugger remoto come servizio, attenersi alla seguente procedura.

1. Trovare la **Configurazione guidata del debugger remoto** (rdbgwiz.exe). Si tratta di un'applicazione separata dal debugger remoto. È disponibile solo quando si installano gli strumenti remoti. e non è inclusa nell'installazione di Visual Studio.

2. Avviare la configurazione guidata. Quando viene visualizzata la prima pagina, fare clic su **Avanti**.

3. Selezionare la casella di controllo **Esegui Visual Studio 2015 Remote Debugger come servizio** .

4. Aggiungere il nome dell'account utente e la password.

    Potrebbe essere necessario aggiungere il diritto utente **Accedi come servizio** a questo account (Trova criteri di protezione **locali** (secpol.msc) nella pagina o nella finestra **iniziale** (oppure **digitare secpol** al prompt dei comandi). Quando viene visualizzata la finestra, fare doppio clic su **Assegnazione diritti utente**e trovare **Accedi come servizio** nel riquadro di destra. Fare doppio clic. Aggiungere l'account utente alla finestra **Proprietà** e fare clic su **OK**. Fare clic su **Avanti**.

5. Selezionare il tipo di rete con cui si vuole che Remote Tools comunichi. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento. Fare clic su **Avanti**.

6. Se è possibile avviare il servizio, viene visualizzato il messaggio **Configurazione guidata di Visual Studio Remote Debugger completata**. Se non è possibile avviare il servizio, viene visualizzato il messaggio **Impossibile completare la Configurazione guidata di Visual Studio Remote Debugger**. La pagina offre anche alcuni suggerimenti da seguire per l'avvio del servizio.

7. Fare clic su **Fine**.

   A questo punto il debugger remoto è in esecuzione come servizio. È possibile verificarlo accedendo al **Pannello di controllo > Servizi** e cercando Visual Studio **2015 Remote Debugger**.

   È possibile arrestare e avviare il servizio debugger remoto dal **Pannello di controllo > Services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedere anche

- [Primo sguardo al debugger](../debugger/debugger-feature-tour.md)
- [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni di porta del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Debug remoto ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)