---
title: Abilitare il debug per ASP.NET app | Microsoft Docs
description: Informazioni su come abilitare il debug per ASP.NET e ASP.NET Core app in Visual Studio. È possibile eseguire il processo in un server IIS Express o in un server IIS locale.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 55b2ef029c4cf8fa502ae73fe5afadbfda136c6f9e5b55d1e451daa71df81fc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453723"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Eseguire il debug di app ASP.NET o ASP.NET Core in Visual Studio

È possibile eseguire il debug ASP.NET e ASP.NET Core app in Visual Studio. Il processo differisce tra ASP.NET e ASP.NET Core e se viene eseguito in IIS Express o in un server IIS locale.

>[!NOTE]
>I passaggi e le impostazioni seguenti si applicano solo al debug delle app in un server locale. Il debug delle app in un server IIS remoto usa **Associa a** processo e ignora queste impostazioni. Per altre informazioni e istruzioni per il debug remoto di app ASP.NET in IIS, vedere Remote debug ASP.NET on an IIS computer (Debug remoto in un [computer IIS)](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o Remote debug ASP.NET Core on a remote IIS computer (Debug remoto in un [computer IIS remoto).](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)

Il server di IIS Express è incluso in Visual Studio. IIS Express è il server di debug predefinito per ASP.NET e ASP.NET Core ed è preconfigurato. È il modo più semplice per eseguire il debug ed è ideale per il debug e il test iniziali.

È anche possibile eseguire il debug di un'app ASP.NET o ASP.NET Core in un server IIS locale (versione 8.0 o successiva) configurato per l'esecuzione dell'app. Per eseguire il debug in IIS locale, è necessario soddisfare i requisiti seguenti:

<a name="iis"></a>
- Se non è installato, installare il carico di lavoro **sviluppo web ASP.NET web**. Eseguire di nuovo il Programma di installazione di Visual Studio, selezionare **Modifica** e aggiungere questo carico di lavoro.

   ::: moniker range="vs-2017"
   In Visual Studio 2017 cercare il componente di supporto **IIS in** fase di sviluppo. Assicurarsi che sia selezionato quando si aggiunge il carico di lavoro.
   ::: moniker-end
- Eseguire Visual Studio come amministratore.
- Installare e configurare correttamente IIS con le versioni appropriate di ASP.NET e/o ASP.NET Core. Per altre informazioni sull'uso di IIS ASP.NET Core, vedere [Host ASP.NET Core on Windows with IIS (Host ASP.NET Core su Windows con IIS).](/aspnet/core/host-and-deploy/iis/index) Per ASP.NET, vedere [Install IIS and ASP.NET Modules](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Assicurarsi che l'app venga eseguita in IIS senza errori.

## <a name="debug-aspnet-apps"></a>Eseguire il debug ASP.NET app

IIS Express è l'impostazione predefinita ed è preconfigurata. Se si esegue il debug in IIS locale, assicurarsi di soddisfare i [requisiti per il debug iis locale.](#iis)

1. Selezionare il progetto ASP.NET in Visual Studio **Esplora soluzioni** fare clic  sull'icona Proprietà oppure premere **ALT** INVIO oppure fare clic con il pulsante destro del mouse e +  **scegliere Proprietà.**

1. Selezionare la **scheda Web.**

1. Nel riquadro **Proprietà,** in **Server**,
   - Per IIS Express, **selezionare** IIS Express dall'elenco a discesa.
   - Per IIS locale,
     1. Selezionare **IIS locale nell'elenco** a discesa.
     1. Accanto al campo **PROJECT URL** selezionare **Crea directory** virtuale, se l'app non è ancora stata impostata in IIS.

1. In **Debugger** selezionare **ASP.NET**.

   ![ASP.NET del debugger](media/dbg-aspnet-enable-debugging2.png "ASP.NET del debugger")

1. Scegliere **File**  >  **Save Selected Items (Salva elementi** selezionati) o premere **CTRL** + **S** per salvare le modifiche.

1. Per eseguire il debug dell'app, nel progetto impostare punti di interruzione su codice. Nella barra degli strumenti Visual Studio verificare che la configurazione sia impostata su **Debug** e che il browser desiderato venga visualizzato in **IIS Express ( \<Browser name> )** o IIS locale **( \<Browser name> )** nel campo dell'emulatore.

1. Per avviare il debug, **selezionare IIS Express ( \<Browser name> )** o IIS  locale **( \<Browser name> )** sulla barra degli strumenti, scegliere Avvia debug dal menu **Debug** o premere **F5.** Il debugger viene sospeso in corrispondenza dei punti di interruzione. Se il debugger non è in grado di individuare i punti di interruzione, vedere [Risolvere i problemi di debug.](#troubleshoot-debugging)

## <a name="debug-aspnet-core-apps"></a>Eseguire il debug ASP.NET Core app

IIS Express è l'impostazione predefinita ed è preconfigurata. Se si esegue il debug in IIS locale, assicurarsi di soddisfare i [requisiti per il debug iis locale.](#iis)

1. Selezionare il progetto ASP.NET Core in Visual Studio **Esplora soluzioni** fare clic  sull'icona Proprietà oppure premere **ALT** INVIO oppure fare clic con il pulsante destro del mouse e +  **scegliere Proprietà.**

1. Selezionare la scheda **Debug**.

1. Nel riquadro **Proprietà,** accanto a **Profilo**,
   - Per IIS Express, **selezionare** IIS Express dall'elenco a discesa.
   - Per IIS locale, selezionare il nome dell'app dall'elenco a discesa oppure selezionare **Nuovo**, creare un nuovo nome di profilo e selezionare **OK.**

1. Accanto ad **Avvia** selezionare IIS Express **o** **IIS** dall'elenco a discesa.

1. Assicurarsi che **l'opzione Launch browser (Avvia browser)** sia selezionata.

1. In **Variabili di** ambiente assicurarsi che ASPNETCORE_ENVIRONMENT sia presente con il valore **Sviluppo**.  In caso contrario, **selezionare Aggiungi** e aggiungerlo.

   ![ASP.NET Core del debugger](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core del debugger")

1. Usare **File**  >  **Save Selected Items (Salva elementi** selezionati) o **CTRL** + **S** per salvare le modifiche.

1. Per eseguire il debug dell'app, nel progetto impostare punti di interruzione su codice. Nella barra degli strumenti Visual Studio verificare che la configurazione sia impostata su **Debug** e che nel campo dell'emulatore sia visualizzato **IIS Express** o il nuovo nome del profilo IIS.

1. Per avviare il debug, **IIS Express** o sulla barra degli strumenti, scegliere Avvia debug dal **\<IIS profile name>** menu **Debug** o premere **F5.**  Il debugger viene sospeso in corrispondenza dei punti di interruzione. Se il debugger non è in grado di individuare i punti di interruzione, vedere [Risolvere i problemi di debug.](#troubleshoot-debugging)

## <a name="troubleshoot-debugging"></a>Risolvere i problemi di debug

Se il debug IIS locale non può essere eseguito fino al punto di interruzione, seguire questa procedura per risolvere i problemi.

1. Avviare l'app Web da IIS e assicurarsi che venga eseguita correttamente. Lasciare l'app Web in esecuzione.

2. Da Visual Studio selezionare Debug **>** Connetti a processo o premere **CTRL** ALT P e connettersi al processo ASP.NET o +  + ASP.NET Core (in  generew3wp.exeo **dotnet.exe**). Per altre informazioni, vedere [Connettersi al processo](attach-to-running-processes-with-the-visual-studio-debugger.md) [e Come trovare il nome del ASP.NET processo.](how-to-find-the-name-of-the-aspnet-process.md)

Se è possibile connettersi e premere il punto di interruzione usando Connetti a processo **,** ma non tramite Debug Avvia debug o  >   **F5,** è probabile che un'impostazione non sia corretta nelle proprietà del progetto. Se si usa un file HOSTS, assicurarsi che sia configurato correttamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurare il debug nel file web.config

ASP.NET progetti includono file *web.config* per impostazione predefinita, che contengono sia le informazioni di configurazione dell'app che quelle di avvio, incluse le impostazioni di debug. I *web.config* devono essere configurati correttamente per il debug. Le **impostazioni** proprietà nelle sezioni precedenti aggiornano *iweb.config,* ma è anche possibile configurarli manualmente.

> [!NOTE]
> ASP.NET Core progetti non hanno inizialmente fileweb.config, ma  usanoappsettings.jssu  elaunchSettings.jsfile per la configurazione dell'app e le informazioni di avvio.  La distribuzione dell'app crea *web.config* file o file nel progetto, ma in genere non contengono informazioni di debug.

> [!TIP]
> Il processo di distribuzione può aggiornare le *impostazioniweb.config,* quindi prima di provare a eseguire il debug, assicurarsi che ilweb.config *sia* configurato per il debug.

**Per configurare manualmente un file *web.config* per il debug:**

1. In Visual Studio aprire il file ASP.NET del *progettoweb.config* progetto.

2. *Web.config* è un file XML, pertanto contiene sezioni annidate contrassegnate da tag. Individuare la sezione `configuration/system.web/compilation`. Se `compilation` l'elemento non esiste, crearlo.

3. Assicurarsi che `debug` l'attributo `compilation` nell'elemento sia impostato su `true` . Se `compilation` l'elemento non contiene un `debug` attributo, aggiungerlo e impostarlo su `true` .

   Se si usa IIS locale anziché il server IIS Express predefinito, assicurarsi che il valore dell'attributo nell'elemento corrisponda al `targetFramework` `compilation` framework nel server IIS.

   `compilation`L'elemento del file *web.config* dovrebbe essere simile all'esempio seguente:

   > [!NOTE]
   > Questo esempio è un file *web.config* parziale. In genere sono presenti sezioni XML aggiuntive negli `configuration` elementi `system.web` e e `compilation` l'elemento potrebbe contenere anche altri attributi ed elementi.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] rileva automaticamente eventuali modifiche ai *fileweb.config* e applica le nuove impostazioni di configurazione. Non è necessario riavviare il computer o il server IIS per l'applicazione delle modifiche.

Un sito Web può contenere diverse directory virtuali e sottodirectory, con *web.config* file in ognuna. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Le app ereditano le impostazioni *web.config* file di configurazione a livelli superiori nel percorso URL. Le impostazioni *web.config* file gerarchico si applicano a tutte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le app sottostanti nella gerarchia. L'impostazione di una configurazione diversa in un file *web.config* inferiore nella gerarchia sostituisce le impostazioni nel file superiore.

Ad esempio, se si specifica in www.microsoft.com/aaa/web.config, qualsiasi app nella cartella aaa o in qualsiasi sottocartella di `debug="true"` *aaa* <em></em>eredita tale impostazione, tranne se una di queste app esegue l'override dell'impostazione con il proprio file *web.config.* 

## <a name="publish-in-debug-mode-using-the-file-system"></a>Pubblicare in modalità di debug usando il file system

Esistono diversi modi per pubblicare le app in IIS. Questi passaggi illustrano come creare e distribuire un profilo di pubblicazione di debug usando il file system. A tale scopo, è necessario eseguire Visual Studio come amministratore.

> [!IMPORTANT]
> Se si modifica il codice o si ricompila, è necessario ripetere questi passaggi per ripubblicare.

1. In Visual Studio fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica.**

3. Scegliere **IIS, FTP e così via e fare** clic su **Pubblica.**

    ![Screenshot della finestra di dialogo Seleziona una destinazione di pubblicazione in Visual Studio. Viene selezionato un Distribuzione Web IIS, FTP e il pulsante Pubblica.](media/dbg-aspnet-local-iis.png)

4. Nella finestra **di dialogo CustomProfile,** per **Metodo di pubblicazione,** scegliere **File system**.

5. Per **Percorso di destinazione** selezionare **Sfoglia** (**...**).

   - Per ASP.NET, selezionare **IIS locale,** selezionare il sito Web creato per l'app e quindi **selezionare Apri**.

     ![Pubblicare in ASP.NET in IIS](media/dbg-aspnet-local-iis1.png "Pubblicare ASP.NET in IIS")

   - Per ASP.NET Core selezionare **File system,** selezionare la cartella impostata per l'app e quindi **selezionare Apri**.

1. Selezionare **Avanti**.

1. In **Configurazione** selezionare **Debug nell'elenco** a discesa.

1. Selezionare **Salva**.

1. Nella finestra **di** dialogo Pubblica verificare che sia visualizzato **CustomProfile** (o il nome del profilo appena creato) e **che LastUsedBuildConfiguration sia** impostato su **Debug**.

1. Selezionare **Pubblica**.

    ![Screenshot della finestra di dialogo Pubblica con l'app CustomProfile selezionata, il pulsante Pubblica evidenziato e LastBuildConfiguration impostato su Debug.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> La modalità di debug riduce notevolmente le prestazioni dell'app. Per ottenere prestazioni ottimali, impostare nelweb.confige specificare una build di versione quando si distribuisce un'app di produzione o si `debug="false"` eservino misurazioni delle prestazioni. 

## <a name="see-also"></a>Vedi anche
- [Debug di ASP.NET: requisiti di sistema](aspnet-debugging-system-requirements.md)
- [Procedura: Eseguire il processo di lavoro con un account utente](how-to-run-the-worker-process-under-a-user-account.md)
- [Procedura: Trovare il nome del processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Eseguire il debug di applicazioni Web distribuite](debugging-deployed-web-applications.md)
- [Procedura dettagliata: Debug di un Web Form](walkthrough-debugging-a-web-form.md)
- [Procedura: Eseguire il debug di eccezioni ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Eseguire il debug di applicazioni Web: errori e risoluzione dei problemi](debugging-web-applications-errors-and-troubleshooting.md)
