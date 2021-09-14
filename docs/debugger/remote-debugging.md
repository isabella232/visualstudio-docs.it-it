---
title: Debug remoto | Microsoft Docs
description: Eseguire il Visual Studio un'applicazione distribuita in un computer diverso usando il debugger Visual Studio remoto.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
ms.date: 7/26/2021
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5e10ac45c0aee1a7298e06efe36e3334295257b7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627900"
---
# <a name="remote-debugging"></a>Remote Debugging
È possibile eseguire il debug di un'applicazione Visual Studio che è stata distribuita in un computer diverso. A questo scopo si usa Visual Studio Remote Debugger.

Per istruzioni approfondite sul debug remoto, vedere questi argomenti.

|Scenario|Collegamento|
|-|-|-|
|Servizio app di Azure|[Eseguire il debug ASP.NET remoto in Azure](../debugger/remote-debugging-azure.md) o, Visual Studio Enterprise, il [Snapshot Debugger](../debugger/debug-live-azure-applications.md)|
|Macchina virtuale di Azure|[Eseguire il debug remoto di ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Eseguire il debug di un'applicazione Service Fabric Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Debug remoto ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) [o debug remoto ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# o Visual Basic|[Eseguire il debug remoto di un progetto C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Eseguire il debug remoto di un progetto C++](../debugger/remote-debugging-cpp.md)|
|App Windows universali (UWP)|[Eseguire app UWP in un computer remoto o](../debugger/run-windows-store-apps-on-a-remote-machine.md) eseguire il debug di un pacchetto di app [installato](../debugger/debug-installed-app-package.md)|

Se si vuole semplicemente scaricare e installare il debugger remoto e non sono necessarie istruzioni aggiuntive per lo scenario, seguire la procedura descritta in questo articolo.

## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Requisiti

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (Facoltativo) Per eseguire il debugger remoto da una condivisione file

È possibile trovare il debugger remoto (*msvsmon.exe*) in un computer con Visual Studio Community, Professional o Enterprise già installato. Per alcuni scenari, il modo più semplice per configurare il debug remoto è eseguire il debugger remoto (msvsmon.exe) da una condivisione file. Per le limitazioni di utilizzo, vedere la pagina della Guida del debugger remoto (**Guida >'utilizzo** nel debugger remoto).

1. Trovare *msvsmon.exe* nella directory corrispondente alla versione di Visual Studio:

   ::: moniker range=">=vs-2019"

   *Programmi (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programmi (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Programmi (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programmi (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Condividere la **cartella Debugger** remoto nel computer Visual Studio remoto.

3. Nel computer remoto eseguire *msvsmon.exe* dalla cartella condivisa. Seguire le istruzioni [di installazione](#bkmk_setup).

> [!TIP]
> Per informazioni di riferimento sull'installazione dalla riga di comando e sulla riga di comando, vedere la pagina della Guida per *msvsmon.exe* digitando nella riga di comando nel computer in cui è installato Visual Studio oppure passare alla Guida ``msvsmon.exe /?`` di > **Usage** nel debugger remoto.

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Configurare il debugger remoto
È possibile modificare alcuni aspetti della configurazione del debugger remoto dopo che è stata avviata per la prima volta.

- Se è necessario aggiungere autorizzazioni per consentire ad altri utenti di connettersi al debugger remoto, scegliere **Strumenti > autorizzazioni**. È necessario disporre dei privilegi di amministratore per concedere o negare autorizzazioni.

     > [!IMPORTANT]
     > È possibile eseguire il debugger remoto con un account utente diverso dall'account utente in uso nel computer Visual Studio, ma è necessario aggiungere il diverso account utente alle autorizzazioni del debugger remoto.

     In alternativa, è possibile avviare il debugger remoto dalla riga di comando con il **parametro /allow: \<username>** **msvsmon /allow \<username@computer>**.

- Se è necessario modificare la modalità di autenticazione o il numero di porta o specificare un valore di timeout per gli strumenti remoti: scegliere Strumenti > **Opzioni**.

     Per un elenco dei numeri di porta usati per impostazione predefinita, vedere [Assegnazioni di porte del debugger remoto](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > È possibile scegliere di eseguire Remote Tools in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (Facoltativo) Configurare il debugger remoto come servizio
Per il debug in ASP.NET e in altri ambienti server, è necessario eseguire il debugger remoto come amministratore o, se si vuole che sia sempre in esecuzione, eseguire il debugger remoto come servizio.

 Se si vuole configurare il debugger remoto come servizio, seguire questa procedura.

1. Trovare la **Configurazione guidata del debugger remoto** (rdbgwiz.exe). Si tratta di un'applicazione separata dal debugger remoto. È disponibile solo quando si installano gli strumenti remoti. e non è inclusa nell'installazione di Visual Studio.

2. Avviare la configurazione guidata. Quando viene visualizzata la prima pagina, fare clic su **Avanti**.

3. Selezionare la casella di controllo **Esegui Visual Studio 2015 Remote Debugger come servizio** .

4. Aggiungere il nome dell'account utente e la password.

    Potrebbe essere necessario aggiungere il diritto utente Accesso come servizio **a** questo account (Trova criteri di sicurezza locali (secpol.msc) nella pagina **iniziale** o nella finestra (o digitare **secpol** al prompt dei comandi).  Quando viene visualizzata la finestra, fare doppio clic su **Assegnazione diritti utente** e trovare **Accedi come servizio** nel riquadro di destra. Fare doppio clic. Aggiungere l'account utente alla finestra **Proprietà** e fare clic su **OK**. Fare clic su **Avanti**.

5. Selezionare il tipo di rete con cui si vuole che Remote Tools comunichi. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento. Fare clic su **Avanti**.

6. Se è possibile avviare il servizio, viene visualizzato il messaggio **Configurazione guidata di Visual Studio Remote Debugger completata**. Se non è possibile avviare il servizio, viene visualizzato il messaggio **Impossibile completare la Configurazione guidata di Visual Studio Remote Debugger**. La pagina offre anche alcuni suggerimenti da seguire per l'avvio del servizio.

7. Fare clic su **Fine**.

   A questo punto il debugger remoto è in esecuzione come servizio. È possibile verificarlo andando a Pannello di controllo > **Services** e cercando **Visual Studio 2015 Remote Debugger**.

   È possibile arrestare e avviare il servizio debugger remoto **da Pannello di controllo > Services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedi anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Configurare il firewall Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni di porta del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Debug remoto ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori di debug remoto e risoluzione dei problemi](../debugger/remote-debugging-errors-and-troubleshooting.md)