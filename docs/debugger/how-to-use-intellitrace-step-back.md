---
title: Visualizzare uno snapshot usando tornare indietro di IntelliTrace
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0422237855a4332761eb50761e88df26ba639b2
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495758"
---
# <a name="view-snapshots-using-intellitrace-step-back-in-visual-studio"></a>Visualizzare gli snapshot con tornare indietro di IntelliTrace in Visual Studio

Tornare indietro di IntelliTrace crea automaticamente uno snapshot dell'applicazione in ogni punto di interruzione e il debugger di eventi di passaggio. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

Tornare indietro di IntelliTrace è disponibile a partire da Visual Studio Enterprise 2017 versione 15.5 e versioni successive e richiede Windows 10 Anniversary Update o versione successiva. La funzionalità è attualmente supportata per il debug di ASP.NET, WinForms, WPF, App console gestite e librerie di classi gestite. A partire da Visual Studio 2017 Enterprise versione 15.7, la funzionalità è supportata anche per ASP.NET Core e .NET Core. A partire da Visual Studio 2017 Enterprise versione 15.9 Preview 2, la funzionalità è supportata anche per le app native destinate a Windows. Debug di applicazioni UWP non è attualmente supportato.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Abilita gli snapshot e gli eventi di Intellitrace
> * Passare gli eventi usando i comandi per tornare indietro e feedforward passaggio
> * Visualizzare gli snapshot di evento
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Abilitare la modalità di eventi e snapshot IntelliTrace 

1. Aprire il progetto in Visual Studio Enterprise.

1. Aprire **degli strumenti** > **opzioni** > **IntelliTrace** impostazioni, quindi selezionare l'opzione **IntelliTrace snapshot ed eventi** . 

    A partire da Visual Studio 2017 Enterprise versione 15.9 Preview 2, questa opzione viene **istantanee di IntelliTrace (gestite e native)**. 

    ![Abilitare la modalità snapshot ed eventi IntelliTrace](../debugger/media/intellitrace-enable-snapshots.png "modalità abilitare eventi IntelliTrace e snapshot")

1. Se si desidera configurare le opzioni per la visualizzazione snapshot in caso di eccezioni, scegliere **IntelliTrace** > **avanzate** dal **opzioni** nella finestra di dialogo.

    Queste opzioni sono disponibili a partire da Visual Studio 2017 Enterprise versione 15.7.

    ![Configurare il comportamento per gli snapshot in caso di eccezioni](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Quando si abilita snapshot ed eventi, creazione di snapshot in caso di eccezioni viene anche abilitato per impostazione predefinita. È possibile disabilitare gli snapshot in caso di eccezioni deselezionando **Raccogli snapshot in eventi di eccezione**. Quando questa funzionalità è abilitata, vengono creati snapshot per le eccezioni non gestite. Per le eccezioni gestite, vengono creati snapshot solo se viene generata l'eccezione e se non è generare nuovamente un'eccezione generata in precedenza. È possibile impostare un numero massimo di snapshot in caso di eccezioni da selezionando un valore dall'elenco a discesa. Si applica il valore massimo per ogni volta che l'app passa alla modalità di interruzione (ad esempio, quando l'app raggiunge un punto di interruzione).

    > [!NOTE]
    > Gli snapshot vengono creati solo per gli eventi di eccezione registrati da IntelliTrace. Per codice gestito, è possibile specificare gli eventi IntelliTrace ha raccolto selezionando **degli strumenti** > **opzioni** > **eventi IntelliTrace**.

1. Nel progetto, impostare uno o più punti di interruzione e avviare il debug (premere **F5**), o avviare il debug eseguendo istruzioni del codice (**F10** oppure **F11**).

    IntelliTrace crea uno snapshot del processo dell'applicazione in ogni passaggio del debugger, evento punto di interruzione ed eventi di eccezione non gestita. Questi eventi vengono registrati nella **eventi** scheda le **strumenti di diagnostica** finestra, nonché altri eventi di IntelliTrace. Per aprire questa finestra, scegliere **Debug** > **Windows** > **Mostra strumenti di diagnostica**.

    Clicca l'icona viene visualizzata accanto agli eventi per i quali gli snapshot sono disponibili. 

    ![Gli eventi di scheda con gli snapshot](../debugger/media/intellitrace-events-tab-with-snapshots.png "scheda eventi con gli snapshot dei punti di interruzione e passaggi")

    Per motivi di prestazioni gli snapshot non vengono acquisiti quando si eseguono istruzioni molto rapidamente. Se viene visualizzata alcuna icona della telecamera accanto al passaggio, provare a eseguire istruzioni più lentamente.

## <a name="navigate-and-view-snapshots"></a>Esplorare e visualizzare gli snapshot

1. Lo spostamento tra eventi usando il **Vai indietro (Alt + [)** e **passo avanti (Alt +])** pulsanti sulla barra degli strumenti di Debug.

    Questi pulsanti di spostarsi tra gli eventi che vengono visualizzati nei **eventi** scheda il **finestra Strumenti di diagnostica**. Attiva l'esecuzione di istruzioni in avanti o indietro per un evento automaticamente [debug cronologico](../debugger/historical-debugging.md) per l'evento selezionato.

    ![Scorrere in avanti e inoltrare i pulsanti](../debugger/media/intellitrace-step-back-icons-description.png "pulsanti Vai indietro e Vai Avanti")

    Quando si passo indietro o passo avanti, Visual Studio passa alla modalità di debug cronologica. In questa modalità, il contesto del debugger passa all'ora di quando è stato registrato l'evento selezionato. Visual Studio, inoltre, sposta il puntatore alla riga di codice nella finestra di origine corrispondente. 

    Da questa visualizzazione, è possibile esaminare i valori di **Stack di chiamate**, **variabili locali**, **Auto**, e **Watch** windows. È anche possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati ed eseguire la valutazione di espressioni nel **Immediate** finestra. I dati visualizzati sono rispetto allo snapshot del processo dell'applicazione effettuato a questo punto nel tempo.

    In questo caso, ad esempio, se hai raggiunto un punto di interruzione ed eseguito un passaggio (**F10**), il **Vai Indietro** pulsante inserisce Visual Studio in modalità cronologico alla riga di codice corrispondente al punto di interruzione. 

    ![Attivazione in corso la modalità cronologica per un evento con uno snapshot](../debugger/media/intellitrace-historical-mode-with-snapshot.png "modalità cronologico di attivazione in corso per un evento con uno snapshot")

2. Per tornare all'esecuzione in tempo reale, scegliere **(F5) di continuazione** oppure fare clic sui **tornare al debug attivo** collegamento sulla barra informazioni. 

3. È anche possibile visualizzare uno snapshot dal **eventi** scheda. A tale scopo, selezionare un evento con uno snapshot e fare clic su **attivare debug cronologico**.

    ![Attiva debug cronologico per un evento](../debugger/media/intellitrace-activate-historical-debugging.png "attivare debug cronologico per un evento")

    A differenza di **Imposta istruzione successiva** comando, visualizzazione di uno snapshot non esegue di nuovo il codice; offre una vista statica dello stato dell'applicazione in un punto nel tempo che si è verificato in passato.

    ![Panoramica di tornare indietro di IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Panoramica di tornare indietro di IntelliTrace")

    Per altre informazioni su come controllare le variabili in Visual Studio, vedere [Tour delle funzionalità del Debugger](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Domande frequenti

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Come è diversa dalla modalità sola eventi IntelliTrace tornare indietro di IntelliTrace?

In modalità solo eventi IntelliTrace consente di attivare debug cronologico per punti di interruzione e passaggi del debugger. Tuttavia, IntelliTrace acquisisce solo i dati nel **variabili locali** e **Auto** windows, se sono aperte le finestre e acquisisce solo i dati che viene espanso e nella visualizzazione. In modalità solo eventi, spesso non è una panoramica completa delle variabili e oggetti complessi. Inoltre, valutazione e visualizzazione dati dell'espressione nel **Watch** finestra non è supportata. 

In modalità snapshot ed eventi, IntelliTrace consente di acquisire l'intero snapshot del processo dell'applicazione, inclusi gli oggetti complessi. In una riga di codice, è possibile visualizzare le stesse informazioni come se sono stati arrestati in un punto di interruzione (e non è importante se le informazioni espansi in precedenza). Valutazione dell'espressione è supportata anche durante la visualizzazione di uno snapshot.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Che cos'è l'impatto sulle prestazioni di questa funzionalità? 

L'impatto sulle prestazioni di debug passo a passo generale dipende dall'applicazione. L'overhead di acquisire uno snapshot è circa 30 minuti. Quando viene creato uno snapshot, il processo dell'app viene duplicato e la copia con fork viene sospeso. Quando si visualizza un'istantanea, Visual Studio si connette alla copia creata tramite fork del processo. Per ogni snapshot, Visual Studio copia solo la tabella della pagina e imposta le pagine copy-on-write. Se gli oggetti sull'heap di modifica tra i vari passaggi del debugger con gli snapshot associati, la tabella della pagina corrispondente viene quindi copiata, risultante in memoria minimo costo. Se Visual Studio rileva che non vi è memoria sufficiente per creare uno snapshot, non viene preso uno.
 
## <a name="known-issues"></a>Problemi noti  
* Se si utilizza la modalità di eventi e snapshot IntelliTrace nelle versioni di Windows precedenti a Windows 10 Fall Creators Update (RS3) e se la piattaforma di destinazione di debug dell'applicazione è impostata su x86, IntelliTrace non registra snapshot.

    Soluzione alternativa:
    * Installare o eseguire l'aggiornamento a Windows 10 Fall Creators Update (RS3). 
    * In alternativa: 
        1. Installare il componente Set di strumenti VC++ 2015.3 versione 140 per desktop (x86, x64) dal programma di installazione di Visual Studio.
        2. Compilare l'applicazione di destinazione.
        3. Dalla riga di comando, usare lo strumento editbin per impostare il `Largeaddressaware` flag per l'eseguibile di destinazione. Ad esempio, è possibile usare questo comando (dopo aver aggiornato il percorso): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
        4. Premere **F5** per avviare il debug. A questo punto, gli snapshot vengono creati i punti di interruzione e passaggi del debugger.

        > [!Note]
        > Il `Largeaddressaware` flag deve essere impostato ogni volta che il file eseguibile viene ricompilato con modifiche.

* Quando viene creato uno snapshot del processo dell'applicazione in un'applicazione che usa un file mappato alla memoria persistente, il processo con lo snapshot mantiene un blocco esclusivo sul file mappato alla memoria (anche dopo che il processo padre ha rilasciato il blocco). Altri processi sono ancora in grado di leggere, ma non scrive, al file mappato alla memoria.

    Soluzione alternativa:
    * Cancella tutti gli snapshot terminando la sessione di debug. 

* Durante il debug di un'applicazione cui processo dispone di un numero elevato di aree di memoria univoco, ad esempio un'applicazione che carica un numero elevato di DLL, l'esecuzione delle prestazioni con gli snapshot abilitati potrebbero risultare peggiorata. Questo problema verrà risolto in una versione futura di Windows. Se si sta verificando questo problema, contattare Microsoft all'indirizzo stepback@microsoft.com. 

* Quando si salva un file con **Debug > IntelliTrace > sessione IntelliTrace Salva** in modalità snapshot ed eventi, i dati aggiuntivi acquisiti dagli snapshot non sono disponibili nel file. iTrace. In eventi punto di interruzione e passaggio, vedere le stesse informazioni come se è stato salvato il file in modalità solo eventi IntelliTrace. 

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come usare tornare indietro di IntelliTrace. È possibile per altre informazioni sulle altre funzionalità di IntelliTrace.

> [!div class="nextstepaction"]
> [Funzionalità IntelliTrace](../debugger/intellitrace-features.md)
