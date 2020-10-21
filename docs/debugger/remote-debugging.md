---
title: Debug remoto | Microsoft Docs
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
ms.openlocfilehash: e8051b83e0022361e4cb1cb61602dfcf8991062e
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "92298692"
---
# <a name="remote-debugging"></a>Remote Debugging
È possibile eseguire il debug di un'applicazione Visual Studio che è stata distribuita in un computer diverso. A questo scopo si usa Visual Studio Remote Debugger.

Per istruzioni dettagliate sul debug remoto, vedere questi argomenti.

|Scenario|Collegamento|
|-|-|-|
|Servizio app di Azure|[ASP.NET di debug remoto in Azure](../debugger/remote-debugging-azure.md) o, per Visual Studio Enterprise, il [snapshot debugger](../debugger/debug-live-azure-applications.md)|
|Macchina virtuale di Azure|[Eseguire il debug remoto di ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Eseguire il debug di un'applicazione Service Fabric di Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Remote debug ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) o [Remote Debug ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# o Visual Basic|[Eseguire il debug remoto di un progetto C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Eseguire il debug remoto di un progetto C++](../debugger/remote-debugging-cpp.md)|
|App di Windows universale (UWP)|[Eseguire app UWP in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) o eseguire il [debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md)|

Se si vuole semplicemente scaricare e installare il debugger remoto e non sono necessarie istruzioni aggiuntive per lo scenario, seguire la procedura descritta in questo articolo.

## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Requisiti

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> Opzionale Per eseguire il debugger remoto da una condivisione file

È possibile trovare il debugger remoto (*msvsmon.exe*) in un computer in cui è già installato Visual Studio Community, Professional o Enterprise. Per alcuni scenari, il modo più semplice per configurare il debug remoto consiste nell'eseguire il debugger remoto (msvsmon.exe) da una condivisione file. Per informazioni sulle limitazioni di utilizzo, vedere la pagina della guida del debugger remoto (per **> utilizzo** nel debugger remoto).

1. Trovare *msvsmon.exe* nella directory che corrisponde alla versione di Visual Studio:

   ::: moniker range=">=vs-2019"

   *Programmi (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programmi (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Programmi (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programmi (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Condividere la cartella del **debugger remoto** nel computer che esegue Visual Studio.

3. Nel computer remoto eseguire *msvsmon.exe* dalla cartella condivisa. Seguire le [istruzioni di installazione](#bkmk_setup).

> [!TIP]
> Per informazioni di riferimento sulla riga di comando e sull'installazione della riga di comando, vedere la pagina della Guida per *msvsmon.exe* digitando nella riga di comando nel computer in cui è ``msvsmon.exe /?`` installato Visual Studio (o passare a **Help > Usage** in Remote Debugger).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Configurare il debugger remoto
È possibile modificare alcuni aspetti della configurazione del debugger remoto dopo che è stata avviata per la prima volta.

- Se è necessario aggiungere autorizzazioni per consentire ad altri utenti di connettersi al debugger remoto, scegliere **strumenti > autorizzazioni**. È necessario disporre dei privilegi di amministratore per concedere o negare autorizzazioni.

     > [!IMPORTANT]
     > È possibile eseguire il debugger remoto con un account utente diverso dall'account utente in uso nel computer di Visual Studio, ma è necessario aggiungere l'account utente diverso alle autorizzazioni del debugger remoto.

     In alternativa, è possibile avviare il debugger remoto dalla riga di comando con il **parametro \<username> /Allow** : **msvsmon/allow \<username@computer> **.

- Se è necessario modificare la modalità di autenticazione o il numero di porta oppure specificare un valore di timeout per Remote Tools: scegliere **strumenti > opzioni**.

     Per un elenco dei numeri di porta usati per impostazione predefinita, vedere [assegnazioni di porte del debugger remoto](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > È possibile scegliere di eseguire Remote Tools in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Opzionale Configurare il debugger remoto come servizio
Per il debug in ASP.NET e in altri ambienti server, è necessario eseguire il debugger remoto come amministratore o, se si vuole che sia sempre in esecuzione, eseguire il debugger remoto come servizio.

 Se si desidera configurare il debugger remoto come servizio, attenersi alla seguente procedura.

1. Trovare la **Configurazione guidata del debugger remoto** (rdbgwiz.exe). Si tratta di un'applicazione separata dal debugger remoto. È disponibile solo quando si installa Remote Tools. e non è inclusa nell'installazione di Visual Studio.

2. Avviare la configurazione guidata. Quando viene visualizzata la prima pagina, fare clic su **Avanti**.

3. Selezionare la casella di controllo **Esegui Visual Studio 2015 Remote Debugger come servizio** .

4. Aggiungere il nome dell'account utente e la password.

    Potrebbe essere necessario aggiungere il diritto utente **Accedi come servizio** a questo account (trovare i criteri di **sicurezza locali** (secpol. msc) nella pagina o nella finestra **iniziale** (oppure digitare **secpol** al prompt dei comandi). Quando viene visualizzata la finestra, fare doppio clic su **Assegnazione diritti utente**e trovare **Accedi come servizio** nel riquadro di destra. Fare doppio clic. Aggiungere l'account utente alla finestra **Proprietà** e fare clic su **OK**. Fare clic su **Avanti**.

5. Selezionare il tipo di rete con cui si vuole che Remote Tools comunichi. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento. Fare clic su **Avanti**.

6. Se è possibile avviare il servizio, viene visualizzato il messaggio **Configurazione guidata di Visual Studio Remote Debugger completata**. Se non è possibile avviare il servizio, viene visualizzato il messaggio **Impossibile completare la Configurazione guidata di Visual Studio Remote Debugger**. La pagina offre anche alcuni suggerimenti da seguire per l'avvio del servizio.

7. Fare clic su **Fine**.

   A questo punto il debugger remoto è in esecuzione come servizio. Per verificarlo, passare a **Pannello di controllo > Servizi** e cercare **Visual Studio 2015 remote debugger**.

   È possibile arrestare e avviare il servizio debugger remoto dal **Pannello di controllo > Servizi**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedere anche

- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [ASP.NET Core di debug remoto in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)