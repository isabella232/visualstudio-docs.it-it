---
title: Visualizzare lo stato precedente dell'app con IntelliTrace
description: Informazioni su come creare e visualizzare snapshot e visualizzare gli snapshot con la funzionalità per tornare indietro di IntelliTrace
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0cb43e75f626f82a0b47bb76bc8be64615ccc333e40e3f22c94e90ff223e239d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418930"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Controllare gli stati precedenti delle app usando la funzionalità per tornare indietro di IntelliTrace in Visual Studio (Visual Studio Enterprise)

La funzionalità per tornare indietro di IntelliTrace crea automaticamente uno snapshot dell'applicazione in corrispondenza di ogni evento di punto di interruzione ed esecuzione di passaggio del debugger. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

La funzionalità per tornare indietro di IntelliTrace è disponibile a partire da Visual Studio Enterprise 2017 versione 15.5 e versioni successive e richiede l'Aggiornamento dell'anniversario di Windows 10 o versione successiva. La funzionalità è attualmente supportata per il debug di ASP.NET, WinForms, WPF, app console gestite e librerie di classi gestite. A partire da Visual Studio 2017 Enterprise versione 15.7, la funzionalità è supportata anche per ASP.NET Core e .NET Core. A partire da Visual Studio 2017 Enterprise versione 15.9 Preview 2, la funzionalità è supportata anche per le app native con destinazione Windows. Il debug delle applicazioni della piattaforma UWP non è attualmente supportato.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Abilitare eventi e snapshot di IntelliTrace
> * Spostarsi negli eventi usando i comandi per andare avanti e tornare indietro
> * Visualizzare gli snapshot di eventi

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Abilitare la modalità eventi e snapshot di IntelliTrace

1. Aprire il progetto in Visual Studio Enterprise.

1. Aprire **le impostazioni** di IntelliTrace opzioni strumenti e selezionare  >    >   **l'opzione Eventi e snapshot intelliTrace**.

    A partire da Visual Studio 2017 Enterprise versione 15.9 Preview 2 questa opzione è **IntelliTrace snapshots (managed and native)** (Snapshot IntelliTrace (gestiti e nativi)).

    ![Abilitare la modalità Snapshot e eventi di IntelliTrace](../debugger/media/intellitrace-enable-snapshots.png "Abilitare la modalità Snapshot e eventi IntelliTrace")

1. Se si desidera configurare le opzioni per la visualizzazione degli snapshot in caso di eccezioni, scegliere **IntelliTrace**  >  **Avanzato** nella **finestra di dialogo** Opzioni.

    Queste opzioni sono disponibili a partire da Visual Studio 2017 Enterprise versione 15.7.

    ![Configurare il comportamento per gli snapshot in caso di eccezioni](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Quando si abilitano snapshot ed eventi, per impostazione predefinita viene abilitata anche la creazione di snapshot in caso di eccezioni. È possibile disabilitare gli snapshot in caso di eccezioni deselezionando l'opzione che consente di **raccogliere gli snapshot per gli eventi di eccezione**. Quando questa funzionalità è abilitata, vengono creati snapshot per le eccezioni non gestite. Per le eccezioni gestite, vengono creati snapshot solo se viene generata l'eccezione e se non si tratta di una rigenerazione di un'eccezione generata in precedenza. È possibile impostare un numero massimo di snapshot in caso di eccezioni selezionando un valore dall'elenco a discesa. Viene applicato il valore massimo ogni volta che l'app passa alla modalità di interruzione, ad esempio, quando l'app raggiunge un punto di interruzione.

    > [!NOTE]
    > Gli snapshot vengono creati solo per gli eventi di eccezione registrati da IntelliTrace. Per il codice gestito, è possibile specificare gli eventi registrati da IntelliTrace **selezionando** Opzioni strumenti  >    >  **Eventi IntelliTrace**.

1. Impostare nel progetto uno o più punti di interruzione e avviare il debug (premere **F5**) o iniziare il debug eseguendo le istruzioni del codice (**F10** o **F11**).

    IntelliTrace crea uno snapshot del processo dell'applicazione per ogni passaggio del debugger, evento punto di interruzione ed evento di eccezione non gestita. Questi eventi vengono registrati nella scheda **Eventi** nella finestra **Strumenti di diagnostica** insieme ad altri eventi IntelliTrace. Per aprire questa finestra, scegliere **Debug**  >  **Windows**  >  **Mostra Strumenti di diagnostica**.

    Per indicare gli snapshot disponibili, viene visualizzata un'icona a forma di fotocamera accanto ai relativi eventi.

    ![Scheda Eventi con snapshot](../debugger/media/intellitrace-events-tab-with-snapshots.png "Scheda Eventi con snapshot su punti di interruzione e passaggi")

    Per motivi di prestazioni gli snapshot non vengono acquisiti quando le istruzioni vengono eseguite molto rapidamente. Se non appare l'icona della fotocamera accanto al passaggio, provare a eseguire l'istruzione più lentamente.

## <a name="navigate-and-view-snapshots"></a>Esplorare e visualizzare gli snapshot

1. Per spostarsi tra gli eventi, usare i pulsanti **Passo indietro (Alt + [)** e **Passo avanti (Alt + ])** sulla barra degli strumenti di Debug.

    Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella **scheda** Eventi nella **finestra Strumenti di diagnostica .** L'esecuzione di istruzioni indietro o avanti in un evento attiva automaticamente [il debug cronologico](../debugger/historical-debugging.md) sull'evento selezionato.

    ![Pulsanti Indietro e Avanti](../debugger/media/intellitrace-step-back-icons-description.png "Pulsanti Indietro e Avanti")

    Quando si torna indietro o si va avanti, Visual Studio passa alla modalità di debug cronologico. In questa modalità il contesto del debugger passa al momento in cui è stato registrato l'evento selezionato. Visual Studio, inoltre, sposta il puntatore sulla riga di codice corrispondente nella finestra di origine.

    Da questa visualizzazione, è possibile esaminare i valori presenti nelle finestre **Stack di chiamate**, **Variabili locali**, **Auto** ed **Espressioni di controllo**. È anche possibile passare il mouse sulle variabili per visualizzare DataTips ed eseguire la valutazione di espressioni nella finestra **Controllo immediato**. I dati visualizzati provengono dallo snapshot del processo dell'applicazione acquisito in corrispondenza di quel punto nel tempo.

    Quindi, ad esempio, se è stato raggiunto un punto di interruzione ed è stato acquisito un passaggio (**F10**), il pulsante **Passo indietro** mette Visual Studio in modalità cronologica alla riga di codice corrispondente al punto di interruzione.

    ![Attivazione della modalità cronologica in un evento con uno snapshot](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Attivazione della modalità cronologica in un evento con uno snapshot")

2. Per tornare all'esecuzione in diretta, scegliere **Continua (F5)** o fare clic sul collegamento **Torna al debug attivo** nella barra informazioni.

3. È anche possibile visualizzare uno snapshot dalla **scheda** Eventi. A tale scopo, selezionare un evento con uno snapshot e fare clic **su Attiva debug cronologico**.

    ![Attivare il debug cronologico in un evento](../debugger/media/intellitrace-activate-historical-debugging.png "Attivare il debug cronologico per un evento")

    A differenza del comando **Imposta istruzione successiva**, la visualizzazione di uno snapshot non esegue di nuovo il codice, ma offre una vista statica dello stato dell'applicazione in un punto nel tempo che si è verificato in passato.

    ![Panoramica del passaggio indietro di IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Panoramica della funzionalità Per tornare indietro di IntelliTrace")

    Per altre informazioni su come controllare le variabili in Visual Studio, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>Domande frequenti

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>In che cosa differisce la funzionalità per tornare indietro di IntelliTrace dalla modalità con soli eventi di IntelliTrace?

In modalità solo eventi IntelliTrace consente di attivare il debug cronologico per passaggi e punti di interruzione del debugger. Tuttavia IntelliTrace acquisisce i dati nelle finestre **Variabili locali** e **Auto** solo se le finestre sono aperte e acquisisce solo i dati che appaiono espansi nella visualizzazione. In modalità solo eventi spesso non si ha una visione completa delle variabili e degli oggetti complessi. Inoltre, la valutazione delle espressioni e la visualizzazione dei dati nella finestra **Espressioni di controllo** non sono supportate.

Nella modalità eventi e snapshot IntelliTrace acquisisce l'intero snapshot del processo dell'applicazione, inclusi gli oggetti complessi. In corrispondenza di una riga di codice è possibile vedere le stesse informazioni che appaiono se ci si ferma in un punto di interruzione, a prescindere dal fatto che le informazioni siano state espanse in precedenza. Anche la valutazione dell'espressione è supportata durante la visualizzazione di uno snapshot.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Qual è l'impatto sulle prestazioni di questa funzionalità? 

L'impatto sulle prestazioni generali dell'esecuzione delle istruzioni dipende dall'applicazione. Il sovraccarico per l'acquisizione di uno snapshot è circa 30 ms. Quando viene acquisito uno snapshot, viene creata una copia con fork del processo e tale copia viene sospesa. Quando si visualizza uno snapshot, Visual Studio si connette alla copia creata con fork del processo. Per ogni snapshot, Visual Studio copia solo la tabella della pagina e imposta le pagine per la copia su scrittura. Se gli oggetti sull'heap cambiano tra i passaggi del debugger con snapshot associati, viene copiata la tabella della pagina corrispondente e il costo in termini di memoria è minimo. Se Visual Studio rileva che non vi è memoria sufficiente per creare uno snapshot, non ne acquisisce uno.

## <a name="known-issues"></a>Problemi noti
* Se si usa la modalità eventi e snapshot di IntelliTrace nelle versioni di Windows precedenti a Windows 10 Fall Creators Update (RS3) e se la piattaforma di destinazione di debug dell'applicazione è impostata su x86, IntelliTrace non acquisisce snapshot.

    Soluzioni alternative:
  * Se si usa l'Aggiornamento dell'anniversario di Windows 10 (RS1) e versioni precedenti a 10.0.14393.2273, [installare KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Se si usa Windows 10 Creators Update (RS2) e versioni precedenti a 10.0.15063.1112, [installare KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Installare o eseguire l'aggiornamento a Windows 10 Fall Creators Update (RS3).
  * In alternativa:
    1. Installare il componente Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) dal programma di installazione di Visual Studio.
    2. Compilare l'applicazione di destinazione.
    3. Dalla riga di comando usare lo strumento editbin per impostare il flag `Largeaddressaware` per il file eseguibile di destinazione. Ad esempio, si potrebbe usare questo comando (dopo aver aggiornato il percorso): "C:\Programmi (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. Premere **F5** per avviare il debug. Da questo punto in poi gli snapshot vengono creati in corrispondenza di passaggi e punti di interruzione del debugger.

       > [!Note]
       > Il flag `Largeaddressaware` deve essere impostato ogni volta che il file eseguibile viene ricompilato con modifiche.

* Quando uno snapshot del processo dell'applicazione viene creato per un'applicazione che usa un file mappato alla memoria persistente, il processo con lo snapshot mantiene un blocco esclusivo sul file mappato alla memoria (anche dopo che il processo padre ha rilasciato il blocco). Altri processi sono comunque in grado di leggere, ma non di scrivere, nel file mappato alla memoria.

  Soluzione alternativa:
  * Cancellare tutti gli snapshot terminando la sessione di debug.

* Durante il debug di un'applicazione cui processo ha un numero elevato di aree di memoria univoche, ad esempio un'applicazione che carica un numero elevato di DLL, l'esecuzione delle istruzioni con gli snapshot abilitati può risultare peggiorata. Questo problema verrà risolto in una versione futura di Windows. Se si riscontra questo problema, contattare Microsoft all'indirizzo stepback@microsoft.com.

* Quando si salva un file con **Debug > IntelliTrace > Salva la sessione di IntelliTrace** in modalità eventi e snapshot, i dati aggiuntivi acquisiti dagli snapshot non sono disponibili nel file ITRACE. In eventi di punti di interruzione e passaggi, si visualizzano le stesse informazioni come se il file fosse stato salvato nella modalità solo eventi di IntelliTrace.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come usare la funzionalità per tornare indietro di IntelliTrace. Sono disponibili informazioni anche su altre funzionalità di IntelliTrace.

> [!div class="nextstepaction"]
> [Funzionalità IntelliTrace](../debugger/intellitrace-features.md)
