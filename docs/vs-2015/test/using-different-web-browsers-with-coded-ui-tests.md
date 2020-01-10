---
title: Uso di Web browser diversi con test codificati dell'interfaccia utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a5034a13771c0ea1f7b6dcd2e073ad02e838e07
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851222"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Uso di Web browser diversi con test codificati dell'interfaccia utente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I test codificati dell'interfaccia utente possono automatizzare il test delle applicazioni Web registrando i test tramite Internet Explorer. È quindi possibile personalizzare il test e riprodurlo usando Internet Explorer o un altro tipo di browser per queste applicazioni Web.

 **Requirements**

- Visual Studio Enterprise

- Sistemi operativi:

  - Microsoft Windows 7

  - Microsoft Windows 8

  - Microsoft Windows Server 2008 R2 SP1

- Versioni del Web browser:

  - Windows Internet Explorer 9

  - Windows Internet Explorer 10

  - Per le versioni supportate di Mozilla Firefox e Google Chrome, fare clic [qui](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

- Installare i [componenti Selenium per il test codificato dell'interfaccia utente tra più browser](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

  **Quali sono i Web browser supportati?**

- [Aggiungere il codice personalizzato per le funzionalità di controllo](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/), ad esempio waiter di riproduzione, ricerca e proprietà.

- Popup e finestre di dialogo

- [Eseguire JavaScript di base senza tipo restituito](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Resilienza di ricerca (tramite la corrispondenza intelligente) e [miglioramenti delle prestazioni](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Perché usare i test codificati dell'interfaccia utente per più tipi di Web browser?
 Testando l'applicazione Web con vari tipi di Web browser si emula meglio l'esperienza dell'interfaccia utente degli utenti che possono eseguire diversi browser. Ad esempio, l'applicazione potrebbe includere un controllo o un codice in Internet Explorer non compatibile con altri Web browser. L'esecuzione dei test codificati dell'interfaccia utente in altri browser consente di individuare e risolvere i problemi prima dell'impatto sui clienti.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Come registrare e riprodurre i test codificati dell'interfaccia utente nelle applicazioni web usando i Web browser supportati
 **Registrazione**: è necessario usare il Generatore di test codificati dell'interfaccia utente per registrare il test di un'applicazione Web usando Internet Explorer. È possibile aggiungere la convalida e il codice personalizzato per i controlli testati usando un set predefinito di proprietà come generalmente accade per i test codificati dell'interfaccia utente. Per altre informazioni, vedere [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md).

> [!NOTE]
> Non è possibile registrare i test codificati dell'interfaccia utente usando i browser Mozilla Firefox o Google Chrome.

 **Riproduzione con Internet Explorer**: quando non è specificato alcun browser in modo esplicito, i test vengono eseguiti in Internet Explorer per impostazione predefinita. È possibile dichiarare in modo esplicito il browser da usare impostando la proprietà **BrowserWindow.CurrentBrowser** nel codice del test. Per Internet Explorer questa proprietà deve essere impostata su **IE** o **Internet Explorer**.

 **Riproduzione con Web browser diversi da Internet Explorer**: per riprodurre in Web browser diversi da Internet Explorer, modificare le proprietà BrowserWindow.CurrentBrowser nel codice del test su **Firefox** o **Chrome**.

 Per riprodurre i test su Web browser diversi da IE, è necessario installare i **componenti Selenium per il test codificato dell'interfaccia utente tra più browser**.

#### <a name="installing-selenium-components"></a>Installazione di Selenium Components

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Nella finestra di dialogo dell'estensione e degli aggiornamenti cercare `Selenium components for Cross Browser Testing`.

3. Evidenziare l'estensione e scegliere **Scarica**.

   > [!TIP]
   > È anche possibile scaricare i componenti Selenium per il test codificato dell'interfaccia utente tra più browser facendo clic [qui](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

   Per altre informazioni sulla creazione e l'uso di test codificati dell'interfaccia utente, vedere [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

### <a name="enable-debugging"></a>Abilita debug
 Per abilitare il debug dell'applicazione Web è necessario completare le opzioni di configurazione seguenti:

1. Abilitare Just My Code:

    1. Nel menu **Strumenti** scegliere **Opzioni** e quindi **Debug**.

    2. Selezionare **Abilita Just My Code**.

2. Disabilitare le eccezioni CLR:

    1. Nel menu **Debug** scegliere **Eccezioni**.

    2. Per **Eccezioni Common Language Runtime** deselezionare **Non gestita dall'utente**.

## <a name="generate"></a>*Non viene visualizzata l'opzione per modificare BrowserWindow. CurrentBrowser nel test codificato dell'interfaccia utente.*
 È possibile che si usi una versione di [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] che non supporta i test codificati dell'interfaccia utente tramite Web browser differenti. Per usare questi test codificati dell'interfaccia utente, è necessario usare Visual Studio Enterprise.

 *Altre informazioni*
 **Note**

- ![Prerequisito](../test/media/prereq.png "Prereq") Il Web browser Apple Safari non è supportato.

- ![Prerequisito](../test/media/prereq.png "Prereq") L'azione di avvio del Web browser deve far parte del test codificato dell'interfaccia utente.

   Se il Web browser è già aperto e si desidera eseguire i passaggi, la riproduzione avrà esito negativo a meno che non si usi Internet Explorer. Pertanto è consigliabile includere l'avvio del Web browser come parte dei test codificati dell'interfaccia utente.

- ![Prerequisito](../test/media/prereq.png "Prereq") L'automazione di azioni dell'interfaccia utente basate su browser specifiche come ingrandire, ridurre a icona e ripristinare non è supportata.

  **Suggerimenti**

- ![Suggerimento](../test/media/tip.png "Suggerimento") È possibile configurare l'output per includere le schermate nei log codificati dell'interfaccia utente. A tale scopo, è necessario impostare alcune impostazioni di configurazione nel file QTAgent32.exe.config. Per impostazione predefinita, questo file è installato nel percorso seguente:

   **C:\Programmi (x86)\Microsoft Visual Studio 11.0\Common7\IDE**

   Impostare i seguenti valori:

  - `EqtTraceLevel` nella sezione `system.diagnostics`.

  - `<add name="EqtTraceLevel" value="4" />`

     Impostando 3 o un valore superiore verrà catturata una schermata per ogni azione. Quando il valore è impostato su 1 o 2, le schermate vengono catturate solo per azioni che causano errore.

    Per altre informazioni, vedere [Analisi dei test codificati dell'interfaccia utente usando i log dei test codificati dell'interfaccia utente](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="external-resources"></a>Risorse esterne

### <a name="videos"></a>Videos
 [Record on IE and Playback everywhere](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU) (Registrazione in IE e riproduzione ovunque)

 [Author cross browser tests with Coded UI Test Builder](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8) (Creazione di test eseguibili in più browser con il generatore di test codificati dell'interfaccia utente)

 [Author cross browser tests using plain hand coding without UI Map](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4) (Creazione di test eseguibili in più browser con la normale codifica manuale senza mappa dell'interfaccia utente)

 [Run cross browser tests sequentially on multiple browsers](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8) (Esecuzione di test in sequenza in più browser)

 [Troubleshoot cross browser test failures](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI) (Risoluzione degli errori dei test eseguibili in più browser)

### <a name="guidance"></a>Informazioni aggiuntive
 [Test per la distribuzione continua con Visual Studio 2012 – Capitolo 2: Unit Testing: Test interni](https://msdn.microsoft.com/library/jj159340.aspx)

 [Test per il recapito continuo con Visual Studio 2012 - Capitolo 5: automazione dei test di sistema](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="faq"></a>Domande frequenti
 [Domande frequenti sui test codificati dell'interfaccia utente - 1](https://blogs.msdn.com/b/mathew_aniyan/archive/tags/faq/)

 [Domande frequenti sui test codificati dell'interfaccia utente - 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Test di automazione dell'interfaccia utente di Visual Studio (include test codificati dell'interfaccia utente)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Vedere anche
 [Usare automazione interfaccia utente per testare le](../test/use-ui-automation-to-test-your-code.md) [configurazioni e le piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni analisi dei](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [test codificati dell'interfaccia utente usando i log dei test codificati dell'interfaccia utente](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
