---
title: Analisi dei test codificati dell'interfaccia utente utilizzando i log dei test codificati dell'interfaccia utente
description: Informazioni sui log di test codificati dell'interfaccia utente, che filtrano e registrano informazioni importanti sulle esecuzioni di test codificati dell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ed58771c45061c180e5ff506babb78bac92416c41362eb8f9a873084df03444c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395531"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analisi dei test codificati dell'interfaccia utente usando i log dei test codificati dell'interfaccia utente

I log dei test codificati dell'interfaccia utente filtrano e registrano informazioni importanti sulle esecuzioni dei test codificati dell'interfaccia utente. I log sono presentati in un formato che consente il debug rapido degli errori.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>Passaggio 1: Abilitare la registrazione

A seconda dello scenario in uso, abilitare la registrazione usando uno dei metodi seguenti:

- Se non è presente alcun file *App.config* nel progetto di test:

   1. Determinare quale processo *QTAgent\*.exe* viene avviato quando si esegue il test. Un modo per farlo è osservare la scheda **Dettagli** in **Gestione attività** di Windows.

   2. Aprire il file *.config* corrispondente dalla cartella *%ProgramFiles(x86)%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE.* Ad esempio, se il processo eseguito è *QTAgent_40.exe* aprire *QTAgent_40.exe.config*.

   2. Modificare il valore di **EqtTraceLevel** e impostarlo sul livello di log desiderato.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. Salvare il file.

- Se è presente un file *App.config* nel progetto di test:

  - Aprire il file *App.config* nel progetto e aggiungere il codice seguente nel nodo di configurazione:

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- La registrazione viene abilitata dal codice di test stesso:

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Passaggio 2: eseguire il test codificato dell'interfaccia utente e visualizzare il log

Quando si esegue un test codificato dell'interfaccia utente dopo avere apportato le modifiche appropriate al file *QTAgent\*.exe.config*, viene visualizzato un collegamento di output nei risultati di **Esplora test**. I file di log vengono generati sia per i test con esito negativo, sia per quelli con esito positivo quando il livello di traccia è impostato su **verbose**.

1. Dal menu **Test** scegliere **Finestre** e selezionare **Esplora test**.

2. Scegliere **Compila soluzione** dal menu **Compila**.

3. In **Esplora test** selezionare il test codificato dell'interfaccia utente che si vuole eseguire, aprire il relativo menu di scelta rapida e quindi scegliere **Esegui test selezionati**.

     I test automatizzati vengono eseguiti e segnalano se sono stati superati o se hanno avuto esito negativo.

    > [!TIP]
    > Per visualizzare **Esplora test,** scegliere **Test**  >  **Windows** e quindi Scegliere **Esplora test**.

4. Scegliere il collegamento **Output** nei risultati di **Esplora test**.

     ![Collegamento di output in Esplora test](../test/media/cuit_htmlactionlog1.png)

     Viene visualizzato l'output del test in cui è incluso un collegamento al log delle azioni.

     ![Risultati e collegamenti di output del test codificato dell'interfaccia utente](../test/media/cuit_htmlactionlog2.png)

5. Scegliere il collegamento *UITestActionLog.html*.

     Il log verrà visualizzato nel browser Web.

     ![File di log del test codificato dell'interfaccia utente](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>Vedi anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Procedura: Eseguire test da Microsoft Visual Studio](/previous-versions/ms182470(v=vs.140))