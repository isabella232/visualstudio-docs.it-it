---
title: Configurare il profiler ASP.NET per i test di carico
description: Informazioni su come usare l'adattatore ASP.NET dati di diagnostica del profiler per raccogliere ASP.NET del profiler.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 23973a9ac44cdfcf58df57eed54c070fdb9388dcf3ff257add9e418588f9bf12
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384925"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Procedura: Configurare il profiler ASP.NET per i test di carico usando le impostazioni test in Visual Studio

È possibile usare l'adattatore dati di diagnostica del profiler ASP.NET per raccogliere le informazioni sul profiler ASP.NET. Questo adattatore dati di diagnostica consente di raccogliere dati relativi alle prestazioni per le applicazioni ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Questo adattatore dati di diagnostica non può essere usato per i test eseguiti Microsoft Test Manager (deprecato in Visual Studio 2017). È possibile usare l'adattatore di diagnostica del profiler ASP.NET con test di carico usando solo siti Web, che richiedono Visual Studio Enterprise.

L'adattatore dati di diagnostica del profiler ASP.NET consente di raccogliere i dati del profiler ASP.NET dal livello applicazione quando si esegue un test di carico. Non è consigliabile eseguire il profiler per test di carico lunghi, ad esempio test di carico eseguiti per più di un'ora, in quanto le dimensioni del file del profiler possono aumentare anche fino a raggiungere centinaia di megabyte. Eseguire, al contrario, i test di carico più brevi tramite il profiler ASP.NET che offrirà comunque il vantaggio di ottenere una diagnosi approfondita dei problemi di prestazioni.

> [!NOTE]
> L'adattatore dati di diagnostica del profiler ASP.NET profila il processo Internet Information Services (IIS), pertanto non funzionerà con un server Web di sviluppo. Per profilare il sito Web nel test di carico, è necessario installare un agente di test nel computer sul quale IIS è in esecuzione. L'agente di test non genererà carico, ma sarà un agente di sola raccolta. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).

Per altre informazioni, vedere [Procedura: Creare un'impostazione test per un test di carico distribuito](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Configurare il profiler ASP.NET per le impostazioni di test

Prima di eseguire i passaggi di questa procedura, è necessario aprire le impostazioni test da Visual Studio e selezionare la pagina **Dati e diagnostica**.

1. Selezionare il ruolo da usare per raccogliere i dati del profiler ASP.NET.

    > [!WARNING]
    > Questo ruolo deve essere un server Web.

2. Selezionare **Profiler ASP.NET** per attivare la raccolta dei dati di profilatura ASP.NET, quindi scegliere **Configura**.

     Viene visualizzata la finestra di dialogo per configurare la raccolta dei dati di profilatura ASP.NET.

3. In **Intervallo di campionamento** del profiler digitare il numero di cicli di clock della CPU non interrotti che devono verificarsi tra ogni campione di profilatura ASP.NET.

4. Per abilitare la profilatura delle interazioni tra livelli, selezionare **Abilita profilatura interazione tra livelli**.

     La profilatura interazione tra livelli consente di contare il numero di richieste inviate al server Web per ciascun artefatto, ad esempio, *MyPage.aspx* o *CompanyLogo.gif*, e il tempo richiesto per soddisfare ogni richiesta. La profilatura interazione tra livelli consente di raccogliere inoltre le connessioni ADO.NET utilizzate come parte della richiesta di pagina e il numero di chiamate a query e stored procedure eseguite come parte della risposta a tale richiesta.

     Vengono raccolti due set diversi di informazioni di intervallo:

    - Le informazioni di intervallo (Min, Max, Media e Totale) per soddisfare ogni richiesta Web.

    - Le informazioni di intervallo (Min, Max, Media e Totale) per l'esecuzione di ogni query.

Con l'adattatore dati di diagnostica del profiler ASP.NET configurato nell'impostazione test, è ora possibile raccogliere dati di profilatura ASP.NET nell'applicazione Web ASP.NET.

## <a name="see-also"></a>Vedi anche

- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)
- [Procedura: Creare un'impostazione test per un test di carico distribuito](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)