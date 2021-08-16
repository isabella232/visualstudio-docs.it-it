---
title: Uso di Web browser diversi con test codificati dell'interfaccia utente
description: Informazioni su come personalizzare il test e riprodurlo usando browser diversi per le applicazioni Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 22821e8dacca86a659d412ae85a04afd3f8b32911dfea59ef2b67ec66da0f264
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384678"
---
# <a name="use-different-web-browsers-with-coded-ui-tests"></a>Usare vari Web browser con test codificati dell'interfaccia utente

I test codificati dell'interfaccia utente possono automatizzare il test delle applicazioni Web registrando i test tramite Internet Explorer. È quindi possibile personalizzare il test e riprodurlo usando Internet Explorer o un altro tipo di browser per queste applicazioni Web.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Prima di tutto, installare i [componenti selenium per il test codificato dell'interfaccia utente tra browser.](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)

## <a name="whats-supported-across-all-web-browsers"></a>Funzionalità supportate in tutti i Web browser

- [Aggiungere il codice personalizzato per le funzionalità di controllo](https://devblogs.microsoft.com/devops/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer/), ad esempio waiter di riproduzione, ricerca e proprietà.

- Popup e finestre di dialogo

- [Eseguire JavaScript di base senza tipo restituito](https://devblogs.microsoft.com/devops/introducing-javascript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test/)

- Resilienza di ricerca (tramite la corrispondenza intelligente) e [miglioramenti delle prestazioni](https://devblogs.microsoft.com/devops/guidelines-on-improving-performance-of-coded-ui-test-playback/)

## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Perché usare i test codificati dell'interfaccia utente per più tipi di Web browser?

Testando l'applicazione Web con vari tipi di Web browser si emula meglio l'esperienza dell'interfaccia utente degli utenti che possono eseguire diversi browser. Ad esempio, l'applicazione potrebbe includere un controllo o un codice in Internet Explorer non compatibile con altri Web browser. L'esecuzione dei test codificati dell'interfaccia utente in altri browser consente di individuare e risolvere i problemi prima dell'impatto sui clienti.

## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Come registrare e riprodurre i test codificati dell'interfaccia utente nelle applicazioni web usando i Web browser supportati

**Registrazione**: è necessario usare il Generatore di test codificati dell'interfaccia utente per registrare il test di un'applicazione Web usando Internet Explorer. È possibile aggiungere la convalida e il codice personalizzato per i controlli testati usando un set predefinito di proprietà come generalmente accade per i test codificati dell'interfaccia utente. Per altre informazioni, vedere Usare [l'automazione interfaccia utente per testare il codice.](../test/use-ui-automation-to-test-your-code.md)

> [!NOTE]
> Non è possibile registrare i test codificati dell'interfaccia utente usando i browser Mozilla Firefox o Google Chrome.

**Riproduzione con Internet Explorer**: quando non è specificato alcun browser in modo esplicito, i test vengono eseguiti in Internet Explorer per impostazione predefinita. È possibile dichiarare in modo esplicito il browser da usare impostando la proprietà **BrowserWindow.CurrentBrowser** nel codice del test. Per Internet Explorer questa proprietà deve essere impostata su **IE** o **Internet Explorer**.

**Riproduzione con Web browser diversi da Internet Explorer**: per riprodurre in Web browser diversi da Internet Explorer, modificare le proprietà BrowserWindow.CurrentBrowser nel codice del test su **Firefox** o **Chrome**.

Per riprodurre i test su Web browser diversi da IE, è necessario installare i **componenti Selenium per il test codificato dell'interfaccia utente tra più browser**.

### <a name="install-selenium-components"></a>Installare i componenti Selenium

::: moniker range="vs-2017"

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Nella finestra di dialogo **Estensioni e aggiornamenti** cercare `Selenium components for Cross Browser Testing`.

::: moniker-end

::: moniker range=">=vs-2019"

1. Scegliere **Gestisci estensioni** dal menu **Estensioni**.

2. Nella finestra di dialogo **Gestisci estensioni** cercare `Selenium components for Cross Browser Testing`.

::: moniker-end

3. Evidenziare l'estensione e scegliere **Scarica**.

    > [!TIP]
    > È anche possibile scaricare i componenti Selenium per il test codificato dell'interfaccia utente tra più browser facendo clic [qui](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting).

Per altre informazioni sulla creazione e l'uso di test codificati dell'interfaccia utente, vedere [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md).

### <a name="enable-debugging"></a>Abilitare il debug

Per abilitare il debug dell'applicazione Web è necessario completare le opzioni di configurazione seguenti:

1. Abilitare Just My Code:

    1. Nel menu **Strumenti** scegliere **Opzioni** e quindi **Debug**.

    2. Selezionare **Abilita Just My Code**.

2. Disabilitare le eccezioni CLR:

    1. Nel menu **Debug** scegliere **Eccezioni**.

    2. Per **Eccezioni Common Language Runtime** deselezionare **Non gestita dall'utente**.

Se l'opzione per modificare `BrowserWindow.CurrentBrowser` nel test codificato dell'interfaccia utente non viene visualizzata, è possibile che si stia usando una versione di Visual Studio che non supporta i test codificati dell'interfaccia utente in vari Web browser. Per usare questi test codificati dell'interfaccia utente, è necessario usare Visual Studio Enterprise Edition.

Altre informazioni da tenere presente:

- Il Web browser Apple Safari non è supportato.

- L'azione di avvio del Web browser deve far parte del test codificato dell'interfaccia utente.

   Se il Web browser è già aperto e si desidera eseguire i passaggi, la riproduzione avrà esito negativo a meno che non si usi Internet Explorer. Pertanto è consigliabile includere l'avvio del Web browser come parte dei test codificati dell'interfaccia utente.

- L'automazione di azioni dell'interfaccia utente specifiche del browser quali l'ingrandimento, la riduzione al minimo e il ripristino non è supportata.

## <a name="tips"></a>Suggerimenti

È possibile configurare l'output in modo da includere le schermate nei log codificati dell'interfaccia utente. A tale scopo, è necessario impostare alcune impostazioni di configurazione nel file *QTAgent32.exe.config* file. Per impostazione predefinita, questo file è installato nel percorso seguente:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*

Impostare i valori seguenti:

- `EqtTraceLevel` nella sezione `system.diagnostics`.

- `<add name="EqtTraceLevel" value="4" />`

   Se si imposta 3 o un valore superiore, viene catturata una schermata per ogni azione. Quando il valore è impostato su 1 o 2, le schermate vengono catturate solo per azioni che causano errore.

Per altre informazioni, vedere [Analisi dei test codificati dell'interfaccia utente usando i log dei test codificati dell'interfaccia utente](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="video-resources"></a>Risorse video

[Registrazione in IE e riproduzione ovunque](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)

[Creare test tra browser con generatore di test codificati dell'interfaccia utente](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)

[Author cross browser tests using plain hand coding without UI Map](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4) (Creazione di test eseguibili in più browser con la normale codifica manuale senza mappa dell'interfaccia utente)

[Run cross browser tests sequentially on multiple browsers](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8) (Esecuzione di test in sequenza in più browser)

[Troubleshoot cross browser test failures](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI) (Risoluzione degli errori dei test eseguibili in più browser)

## <a name="see-also"></a>Vedi anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Analizzare i test codificati dell'interfaccia utente usando i log di test codificati dell'interfaccia utente](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)
