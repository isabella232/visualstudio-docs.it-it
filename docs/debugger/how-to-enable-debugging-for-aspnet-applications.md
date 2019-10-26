---
title: Abilitare il debug per le app ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911346"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Eseguire il debug di app ASP.NET o ASP.NET Core in Visual Studio

È possibile eseguire il debug di app ASP.NET e ASP.NET Core in Visual Studio. Il processo è diverso tra ASP.NET e ASP.NET Core e se viene eseguito in IIS Express o in un server IIS locale.

>[!NOTE]
>I passaggi e le impostazioni seguenti si applicano solo alle app di debug in un server locale. Il debug di app in un server IIS remoto usa **Connetti a processo**e ignora queste impostazioni. Per ulteriori informazioni e istruzioni per il debug remoto di app ASP.NET in IIS, vedere [Remote debug ASP.NET in un computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o [Remote Debug ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Il server IIS Express incorporato è incluso in Visual Studio. IIS Express è il server di debug predefinito per i progetti ASP.NET e ASP.NET Core ed è preconfigurato. È il modo più semplice per eseguire il debug e la soluzione ideale per il debug e il test iniziali.

È anche possibile eseguire il debug di un'app ASP.NET o ASP.NET Core in un server IIS locale (versione 8,0 o successiva) configurata per l'esecuzione dell'app. Per eseguire il debug in IIS locale, è necessario soddisfare i requisiti seguenti:

<a name="iis"></a>
- Selezionare il **supporto IIS in fase di sviluppo** durante l'installazione di Visual Studio. Se necessario, eseguire nuovamente il Programma di installazione di Visual Studio, selezionare **modifica**e aggiungere il componente.
- Eseguire Visual Studio come amministratore.
- Installare e configurare correttamente IIS con le versioni appropriate di ASP.NET e/o ASP.NET Core. Per ulteriori informazioni e istruzioni, vedere [iis 8,0 con ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o [host ASP.NET Core in Windows con IIS](/aspnet/core/host-and-deploy/iis/index).
- Assicurarsi che l'app venga eseguita in IIS senza errori.

## <a name="debug-aspnet-apps"></a>Eseguire il debug di app ASP.NET

IIS Express è l'impostazione predefinita ed è preconfigurata. Se si esegue il debug in IIS locale, verificare che siano soddisfatti i [requisiti per il debug locale di IIS](#iis).

1. Selezionare il progetto ASP.NET in Visual Studio **Esplora soluzioni** e fare clic sull'icona delle **Proprietà** , premere **ALT**+**invio**oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Selezionare la scheda **Web** .

1. Nel riquadro **Proprietà** , in **Server**,
   - Per IIS Express selezionare **IIS Express** nell'elenco a discesa.
   - Per IIS locale,
     1. Selezionare **IIS locale** dall'elenco a discesa.
     1. Accanto al campo **URL progetto** selezionare **Crea directory virtuale**, se l'app non è ancora stata configurata in IIS.

1. In **debugger**selezionare **ASP.NET**.

   ![Impostazioni del debugger ASP.NET](media/dbg-aspnet-enable-debugging2.png "Impostazioni del debugger ASP.NET")

1. Usare **File** > **salvare gli elementi selezionati** o **CTRL**+**S** per salvare le modifiche.

1. Per eseguire il debug dell'app, nel progetto impostare i punti di interruzione su un codice. Nella barra degli strumenti di Visual Studio verificare che la configurazione sia impostata su **debug**e che il browser desiderato venga visualizzato in **IIS Express (\<nome del browser >)** o **IIS locale (\<nome del browser >)** nel campo dell'emulatore.

1. Per avviare il debug, selezionare **IIS Express (\<nome del browser >)** o **IIS locale (\<nome del browser >)** sulla barra degli strumenti, selezionare **Avvia debug** dal menu **debug** oppure premere **F5**. Il debugger viene sospeso in corrispondenza dei punti di interruzione. Se il debugger non riesce a raggiungere i punti di interruzione, vedere [risolvere i problemi di debug](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Eseguire il debug di app ASP.NET Core

IIS Express è l'impostazione predefinita ed è preconfigurata. Se si esegue il debug in IIS locale, verificare che siano soddisfatti i [requisiti per il debug locale di IIS](#iis).

1. Selezionare il progetto ASP.NET Core in Visual Studio **Esplora soluzioni** e fare clic sull'icona delle **Proprietà** , premere **ALT**+**invio**oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Selezionare la scheda **Debug**.

1. Nel riquadro **Proprietà** , accanto a **profilo**,
   - Per IIS Express selezionare **IIS Express** nell'elenco a discesa.
   - Per IIS locale selezionare il nome dell'app nell'elenco a discesa oppure selezionare **nuovo**, creare un nuovo nome del profilo e fare clic su **OK**.

1. Accanto a **Avvia**selezionare **IIS Express** o **IIS** nell'elenco a discesa.

1. Assicurarsi che **Launch browser** sia selezionato.

1. In **variabili di ambiente**verificare che **ASPNETCORE_ENVIRONMENT** sia presente con il valore **Development**. In caso contrario, selezionare **Aggiungi** e Aggiungi.

   ![Impostazioni del debugger ASP.NET Core](../debugger/media/dbg-aspnet-enable-debugging3.png "Impostazioni del debugger ASP.NET Core")

1. Usare **File** > **salvare gli elementi selezionati** o **CTRL**+**S** per salvare le modifiche.

1. Per eseguire il debug dell'app, nel progetto impostare i punti di interruzione su un codice. Nella barra degli strumenti di Visual Studio verificare che la configurazione sia impostata su **debug**e che **IIS Express**o il nuovo nome del profilo IIS sia visualizzato nel campo emulatore.

1. Per avviare il debug, selezionare **IIS Express** o **\<nome del profilo IIS >** sulla barra degli strumenti, scegliere **Avvia debug** dal menu **debug** oppure premere **F5**. Il debugger viene sospeso in corrispondenza dei punti di interruzione. Se il debugger non riesce a raggiungere i punti di interruzione, vedere [risolvere i problemi di debug](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Risoluzione dei problemi di debug

Se il debug IIS locale non può avanzare al punto di interruzione, attenersi alla procedura seguente per risolvere i problemi.

1. Avviare l'app Web da IIS e assicurarsi che venga eseguita correttamente. Lasciare l'app Web in esecuzione.

2. In Visual Studio selezionare **Debug > Connetti a processo** oppure premere **Ctrl**+**ALT**+**P**e connettersi al processo ASP.NET o ASP.NET Core (in genere **w3wp. exe** o **dotnet. exe**). Per ulteriori informazioni, vedere [Connetti a processo](attach-to-running-processes-with-the-visual-studio-debugger.md) e [come individuare il nome del processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Se è possibile connettersi e raggiungere il punto di interruzione utilizzando **Connetti a processo**, ma non usando **debug** > **avviare il debug** o **F5**, un'impostazione è probabilmente errata nelle proprietà del progetto. Se si usa un file HOSTs, assicurarsi che sia configurato correttamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurare il debug nel file Web. config

I progetti ASP.NET hanno file *Web. config* per impostazione predefinita, che contengono sia la configurazione dell'app che le informazioni di avvio, incluse le impostazioni di debug. Per eseguire il debug, è necessario configurare correttamente i file *Web. config* . Le impostazioni delle **Proprietà** nelle sezioni precedenti aggiornano i file *Web. config* , ma è possibile configurarle anche manualmente.

> [!NOTE]
> I progetti di ASP.NET Core non hanno inizialmente file *Web. config* , ma usano i file *appSettings. JSON* e *launchSettings. JSON* per la configurazione delle app e le informazioni di avvio. La distribuzione dell'app crea un file *Web. config* o i file nel progetto, ma in genere non contengono informazioni di debug.

> [!TIP]
> Il processo di distribuzione può aggiornare le impostazioni di *Web. config* . prima di provare a eseguire il debug, assicurarsi che il *file Web. config* sia configurato per il debug.

**Per configurare manualmente un file *Web. config* per il debug:**

1. In Visual Studio aprire il file *Web. config* del progetto ASP.NET.

2. *Web. config* è un file XML, quindi contiene sezioni annidate contrassegnate da tag. Individuare la sezione `configuration/system.web/compilation`. Se l'elemento `compilation` non esiste, crearlo.

3. Verificare che l'attributo `debug` nell'elemento `compilation` sia impostato su `true`. Se l'elemento `compilation` non contiene un attributo `debug`, aggiungerlo e impostarlo su `true`.)

   Se si utilizza IIS locale anziché il server IIS Express predefinito, assicurarsi che il valore dell'attributo `targetFramework` nell'elemento `compilation` corrisponda al Framework nel server IIS.

   L'elemento `compilation` del file *Web. config* dovrebbe essere simile all'esempio seguente:

   > [!NOTE]
   > Questo esempio è un file *Web. config* parziale. Negli elementi `configuration` e `system.web` sono in genere presenti sezioni XML aggiuntive e l'elemento `compilation` potrebbe contenere anche altri attributi ed elementi.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] rileva automaticamente qualsiasi modifica apportata ai file *web.config* e applica le nuove impostazioni di configurazione. Non è necessario riavviare il computer o il server IIS per rendere effettive le modifiche.

Un sito Web può contenere diverse directory virtuali e sottodirectory, con i file *Web. config* in ognuno di essi. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] app ereditano le impostazioni di configurazione dai file *Web. config* a livelli superiori nel percorso URL. Le impostazioni del file *Web. config* gerarchico si applicano a tutte le app [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sottostanti nella gerarchia. L'impostazione di una configurazione diversa in un file *Web. config* di livello inferiore nella gerarchia sostituisce le impostazioni nel file di livello superiore.

Se ad esempio si specifica `debug="true"` in <em>www.Microsoft.com/aaa/Web.config</em>, qualsiasi app nella cartella *AAA* o in qualsiasi sottocartella di *AAA* eredita tale impostazione, tranne nel caso in cui una di queste app esegua l'override dell'impostazione con il proprio *file Web. config* file.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Pubblicare in modalità di debug usando il file system

Esistono diversi modi per pubblicare le app in IIS. Questi passaggi illustrano come creare e distribuire un profilo di pubblicazione di debug usando il file system. A tale scopo, è necessario eseguire Visual Studio come amministratore.

> [!IMPORTANT]
> Se si modifica il codice o la ricompilazione, è necessario ripetere questi passaggi per la ripubblicazione.

1. In Visual Studio fare clic con il pulsante destro del mouse sul progetto e scegliere **pubblica**.

3. Scegliere **IIS, FTP e così via** , quindi fare clic su **pubblica**.

    ![Pubblica in IIS](media/dbg-aspnet-local-iis.png "Eseguire la pubblicazione in IIS")

4. Nella finestra di dialogo **CustomProfile** fare clic su **file System**per **metodo di pubblicazione**.

5. In **percorso di destinazione**selezionare **Sfoglia** ( **...** ).

   - Per ASP.NET selezionare **IIS locale**, selezionare il sito Web creato per l'app e quindi selezionare **Apri**.

     ![Pubblicare in ASP.NET in IIS](media/dbg-aspnet-local-iis1.png "Pubblicare ASP.NET in IIS")

   - Per ASP.NET Core selezionare **file System**, selezionare la cartella configurata per l'app e quindi selezionare **Apri**.

1. Scegliere **Avanti**.

1. In **configurazione**selezionare **debug** nell'elenco a discesa.

1. Selezionare **Salva**.

1. Nella finestra di dialogo **pubblica** verificare che sia visualizzato **CustomProfile** (o il nome del profilo appena creato) e che **LastUsedBuildConfiguration** sia impostato su **debug**.

1. Selezionare **Pubblica**.

    ![Pubblica in IIS](media/dbg-aspnet-local-iis-select-site.png "Eseguire la pubblicazione in IIS")

> [!IMPORTANT]
> La modalità di debug riduce notevolmente le prestazioni dell'app. Per ottenere prestazioni ottimali, impostare `debug="false"` nel *file Web. config* e specificare una build di rilascio quando si distribuisce un'app di produzione o si eseguono misurazioni delle prestazioni.

## <a name="see-also"></a>Vedere anche
- [Debug di ASP.NET: requisiti di sistema](aspnet-debugging-system-requirements.md)
- [Procedura: Eseguire il processo di lavoro con un account utente](how-to-run-the-worker-process-under-a-user-account.md)
- [Procedura: Trovare il nome del processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Eseguire il debug di applicazioni Web distribuite](debugging-deployed-web-applications.md)
- [Procedura dettagliata: Debug di un Web Form](walkthrough-debugging-a-web-form.md)
- [Procedura: Eseguire il debug di eccezioni ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Eseguire il debug di applicazioni Web: errori e risoluzione dei problemi](debugging-web-applications-errors-and-troubleshooting.md)
