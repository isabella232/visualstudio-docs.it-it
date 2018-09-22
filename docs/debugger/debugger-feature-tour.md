---
title: Introduzione al debug in Visual Studio 2017
description: Iniziare il debug di applicazioni mediante il debugger di Visual Studio
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2339dcfe80e994b8bc9062d137263d3b25d274d
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542416"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Iniziare a esaminare il Debugger di Visual Studio

In questo argomento vengono descritti gli strumenti di debugger disponibili in Visual Studio. Nel contesto di Visual Studio, quando si *il debug dell'app*, in genere significa che si esegue l'applicazione con il debugger collegato (vale a dire, in modalità di debug). Quando si esegue questa operazione, il debugger fornisce diversi modi per ottenere informazioni sulle attività del codice mentre è in esecuzione. È possibile esaminare il codice ed esaminare i valori archiviati nelle variabili, è possibile impostare espressioni di controllo per le variabili per vedere quando vengono modificati i valori, è possibile esaminare il percorso di esecuzione del codice, et al. Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo argomento.

Le funzionalità descritte di seguito sono applicabili a c#, C++, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (se diversamente specificato).

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

Per eseguire il debug, è necessario avviare l'app con il debugger collegato al processo dell'app. **F5** (**Debug > Avvia debug**) è il modo più comune per eseguire questa operazione. Tuttavia, a questo punto si potrebbe non essere stato punti di interruzione per esaminare l'app del codice, quindi si verrà fatto e quindi avviare il debug. I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. 

Se è aperto un file nell'editor del codice, è possibile impostare un punto di interruzione facendo clic sul margine a sinistra di una riga di codice.

![Impostare un punto di interruzione](../debugger/media/dbg-tour-set-a-breakpoint.gif "impostare un punto di interruzione")

Premere **F5** (**Debug > Avvia debug**) o nella **Avvia debug** pulsante ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug ") nella barra degli strumenti Debug e l'esecuzione del debugger per il primo punto di interruzione viene rilevato. Se l'app non è ancora in esecuzione, F5 viene avviato il debugger e si interrompe al primo punto di interruzione.

I punti di interruzione sono una funzionalità molto utile quando si conosce la riga di codice o nella sezione di codice che si desidera esaminare in dettaglio.

## <a name="navigate"></a> Esplorare il codice nel debugger tramite i comandi di passaggio

Offriamo i tasti di scelta rapida per la maggior parte dei comandi poiché rendono più rapida esplorazione del codice dell'app. (Equivalente comandi quali comandi di menu vengono visualizzati tra parentesi).

Per avviare l'app con il debugger collegato, premere **F11** (**Debug > Esegui istruzione**). F11 è il **Esegui istruzione** comando e sposta in avanti l'app esecuzione un'istruzione alla volta. Quando si avvia l'app con F11, il debugger si interrompe la prima istruzione che viene eseguita.

![F11 Eseguire l'istruzione](../debugger/media/dbg-tour-f11.png "F11 eseguire l'istruzione")

La freccia gialla rappresenta l'istruzione in cui il debugger ha sospeso, che anche sospende l'esecuzione di app nella stessa fase (questa istruzione non è ancora eseguito).

F11 è un buon metodo per esaminare il flusso di esecuzione nella maggior parte dei dettagli. (Per spostare più velocemente tramite il codice, mostreremo alcuni anche altre opzioni.) Per impostazione predefinita, il debugger ignora codice non utente (se si desidera visualizzare ulteriori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

>[!NOTE]
> Nel codice gestito, si verrà visualizzato una finestra di dialogo che chiede se si desidera ricevere una notifica quando automaticamente l'istruzione/routine delle proprietà e operatori (comportamento predefinito). Se si desidera modificare l'impostazione in un secondo momento, disabilitare **Esegui istruzione/routine di proprietà e operatori** impostazione nelle **strumenti > Opzioni** menu sotto **debug**.

## <a name="step-over-code-to-skip-functions"></a>Esegui istruzione/routine di codice per ignorare le funzioni

Quando si usa una riga di codice che è una chiamata di funzione o un metodo, è possibile premere **F10** (**Debug > Esegui istruzione/routine**) anziché F11.

F10 fa avanzare il debugger senza eseguire istruzioni di funzioni o metodi nel codice dell'app (il codice viene ancora eseguito). Premendo F10, è possibile ignorare il codice che non si è interessati. In questo modo, è possibile accedere rapidamente a codice che si è più interessati.

## <a name="step-into-a-property"></a>Passaggio in una proprietà

Come accennato in precedenza, per impostazione predefinita il debugger ignora le proprietà gestite e i campi, ma il **Esegui istruzione specifica** comando consente di eseguire l'override di questo comportamento.

Fare clic su una proprietà o campo e scegliere **Esegui istruzione specifica**, quindi scegliere una delle opzioni disponibili.

![Eseguire l'istruzione specifici](../debugger/media/dbg-tour-step-into-specific.png "Esegui istruzione specifica")

In questo esempio **Esegui istruzione specifica** arrivati al codice per `Path.set`.

![Eseguire l'istruzione specifici](../debugger/media/dbg-tour-step-into-specific-2.png "Esegui istruzione specifica")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Esecuzione in un punto nel codice rapidamente utilizzando il mouse

Quando nel debugger, passare il mouse su una riga di codice fino al **Esegui fino al fare clic su** pulsante (esecuzione fino a qui) ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata a sinistra.

![Esegui fino al clic](../debugger/media/dbg-tour-run-to-click-2.png "eseguire fa clic su")

> [!NOTE]
> Il **Esegui fino al clic** pulsante (esecuzione fino a qui) è una novità [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Fare clic sui **Esegui fino al clic** pulsante (esecuzione fino a qui). Il debugger avanza alla riga di codice in cui si fa clic su.

Tramite questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Questo comando è anche utile per ottenere rapidamente all'interno di un'area visibile del codice dell'app. È possibile usare **Esegui fino al clic** in qualsiasi file aperto.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Far avanzare il debugger dalla funzione corrente

In alcuni casi, si potrebbe voler continuare la sessione di debug ma far avanzare il debugger completamente tramite la funzione corrente.

Premere **MAIUSC+F11** (o **Debug > Esci da istruzione**).

Questo comando riprende l'esecuzione di app (e fa avanzare il debugger) fino a quando non restituisce la funzione corrente.

## <a name="run-to-cursor"></a>Esecuzione fino al cursore

Arrestare il debugger premendo il **arresta debug** pulsante rosso ![arresta debug](../debugger/media/dbg-tour-stop-debugging.png "arresta debug") oppure **MAIUSC**  +  **F5**.

Fare doppio clic su una riga di codice nell'app e scegli **Esegui fino al cursore**. Questo comando avvia il debug e imposta un punto di interruzione temporaneo nella riga di codice corrente.

![Esegui fino al cursore](../debugger/media/dbg-tour-run-to-cursor.png "Esegui fino al cursore")

Se sono stati impostati i punti di interruzione, il debugger sospende sul punto di interruzione prima che accede.

Premere **F5** fino a raggiungere la riga di codice in cui è selezionata **Esegui fino al cursore**.

Questo comando è utile quando si modifica del codice e si vuole impostare un punto di interruzione temporanea rapidamente e avviare il debugger nello stesso momento.

> [!NOTE]
> È possibile usare **Esegui fino al cursore** nel **Stack di chiamate** finestra durante il debug.

## <a name="restart-your-app-quickly"></a>Riavviare l'app rapidamente

Fare clic sui **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "riavviare App") pulsante sulla barra degli strumenti Debug (**Ctrl + MAIUSC + F5**).

Quando si preme **riavviare**, consentono di risparmiare tempo e l'arresto dell'app e riavviare il debugger. Il debugger si fermerà in corrispondenza il primo punto di interruzione viene raggiunto mediante l'esecuzione di codice.

Se si desidera arrestare il debugger e tornare nell'editor di codice, è possibile premere l'arresto rossa ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "arresta debug") pulsante anziché **riavviare**.

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Ora che si ha una buona conoscenza un po', hai una buona opportunità per avviare la verifica lo stato dell'app (variabili) con il debugger. Funzionalità che consentono di controllare le variabili sono alcune delle funzionalità più utili del debugger, ed esistono diversi modi per farlo. Spesso, quando si tenta di eseguire il debug di un problema, si sta tentando di scoprire se le variabili archiviano i valori che si prevede possano disporre in uno stato particolare app.

Durante la pausa del debugger, passare il mouse su un oggetto con il puntatore del mouse e viene visualizzato il valore della proprietà predefinita (in questo esempio, il nome del file `market 031.jpg` è il valore della proprietà predefinito).

![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "consente di visualizzare un suggerimento dati")

Espandere l'oggetto per visualizzare tutte le relative proprietà (ad esempio il `FullPath` proprietà in questo esempio).

Spesso, durante il debug, si desidera un modo rapido per verificare i valori delle proprietà sugli oggetti e i suggerimenti dati sono un buon metodo per eseguire questa operazione.

> [!TIP]
> Nei linguaggi più supportati, è possibile modificare codice all'interno di una sessione di debug. Per altre informazioni, vedi [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e variabili locali

Durante il debug, esaminare i **Auto** finestra nella parte inferiore dell'editor del codice.

![Finestra Auto](../debugger/media/dbg-tour-autos-window.png "finestra Auto")

Nel **Auto** è visualizzare variabili lungo con il relativo valore corrente e il loro tipo. Il **Auto** finestra Mostra tutte le variabili usate nella riga corrente o nella riga precedente (In C++, la finestra Mostra le variabili in tre righe di codice precedenti. Vedere la documentazione per il comportamento specifico del linguaggio).

> [!NOTE]
> In JavaScript, il **variabili locali** finestra è supportata ma non le **Auto** finestra.

Esaminare quindi le **variabili locali** finestra. Il **variabili locali** finestra Mostra le variabili che sono attualmente nell'ambito.

![Finestra variabili locali](../debugger/media/dbg-tour-locals-window.png "finestra variabili locali")

In questo esempio, il `this` e l'oggetto `f` rientrano nell'ambito. Per altre informazioni, vedi [esaminare le variabili in auto e variabili locali Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

È possibile usare una **Watch** per specificare una variabile (o un'espressione) che si desidera tenere d'occhio nella finestra.

Durante il debug, fare doppio clic su un oggetto e scegli **Aggiungi espressione di controllo**.

![Finestra Espressioni di controllo](../debugger/media/dbg-tour-watch-window.png "finestra Espressioni di controllo")

In questo esempio, è necessario impostare su un'espressione di controllo di `f` oggetto ed è possibile visualizzarne il valore cambia quando sposta tramite il debugger. A differenza di altre finestre delle variabili, il **Watch** finestre mostrano sempre le variabili che sta controllando (è disattivati quando fuori ambito).

Per altre informazioni, vedere [impostare un'espressione di controllo usando le espressioni di controllo e controllo immediato Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

Scegliere il **Stack di chiamate** finestra durante il debug, per impostazione predefinita è aperto nel riquadro inferiore destro.

![Esaminare lo Stack di chiamate](../debugger/media/dbg-tour-call-stack.png "esaminare lo stack di chiamate")

Il **Stack di chiamate** finestra Mostra l'ordine in cui vengono introduzione chiamate i metodi e le funzioni. La prima riga visualizza la funzione corrente (la `Update` metodo in questo esempio). La seconda riga indica che `Update` è stato chiamato dal `Path.set` proprietà e così via. Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

> [!NOTE]
> Il **Stack di chiamate** finestra è simile alla prospettiva di Debug in alcuni ambienti di sviluppo integrato, ad esempio Eclipse.

È possibile fare doppio clic su una riga di codice per passare osservare che il codice sorgente e che viene modificato anche l'ambito corrente viene controllato dal debugger. Ciò non far avanzare il debugger.

È anche possibile usare i menu di scelta rapida dal **Stack di chiamate** finestra per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione in funzioni specifiche, riavviare l'app usando **Esegui fino al cursore**e per passare a esaminare il codice sorgente. Visualizzare [procedura: esaminare lo Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Esaminare un'eccezione

Quando l'app genera un'eccezione, il debugger passerà alla riga di codice che ha generato l'eccezione.

![Helper eccezioni](../debugger/media/dbg-tour-exception-helper.png "Helper eccezioni")

In questo esempio, il **Helper eccezioni** Mostra un `System.Argument` eccezione e un messaggio di errore indicante che il percorso non è un modulo valido. Pertanto, sappiamo che si è verificato l'errore su un argomento di metodo o funzione.

In questo esempio, il `DirectoryInfo` chiamata è stato assegnato l'errore nella archiviati in una stringa vuota di `value` variabile.

Gestore di eccezioni è un'ottima funzionalità che consentono di eseguire il debug degli errori. È anche possibile eseguire operazioni come visualizzare i dettagli dell'errore e aggiungere un'espressione di controllo dal gestore di eccezioni. In alternativa, se necessario, è possibile modificare le condizioni per l'eccezione specifica.

>  [!NOTE]
> L'Helper eccezioni consente di sostituire le informazioni sulle eccezioni in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Espandere la **impostazioni eccezioni** nodo per visualizzare altre opzioni su come gestire questo tipo di eccezione, ma è necessario modificare alcun valore per questa presentazione.

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Il debug in tempo reale delle App ASP.NET in servizio App di Azure

il **Snapshot Debugger** crea uno snapshot delle App nell'ambiente di produzione quando viene eseguito codice che si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

![Avviare il debugger di snapshot](../debugger/media/snapshot-launch.png "avviare il debugger di snapshot")

Raccolta di snapshot è disponibile per le applicazioni ASP.NET in esecuzione in servizio App di Azure. Le applicazioni ASP.NET devono essere in esecuzione su .NET Framework 4.6.1 o versioni successive, e le applicazioni ASP.NET Core devono essere in esecuzione su .NET Core 2.0 o versioni successive in Windows.

Per altre informazioni, vedere [il Debug in tempo reale delle App ASP.NET usando il Debugger di Snapshot](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>Visualizzare gli snapshot con IntelliTrace (Visual Studio Enterprise) tornare indietro

**Tornare indietro di IntelliTrace** crea automaticamente uno snapshot dell'applicazione in ogni punto di interruzione e il debugger di eventi di passaggio. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

![Passaggio precedente e inoltrare i pulsanti](../debugger/media/intellitrace-step-back-icons-description.png  "pulsanti Vai indietro e Avanti")

Per altre informazioni, vedere la [ispezionare stati precedenti di app con IntelliTrace](../debugger/view-historical-application-state.md) pagina.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione sono state esaminare rapidamente numerose funzionalità di debug. È possibile esaminare informazioni più dettagliate queste funzionalità usando un'applicazione di esempio

> [!div class="nextstepaction"]
> [Informazioni sul debug tramite Visual Studio](../debugger/getting-started-with-the-debugger.md)
