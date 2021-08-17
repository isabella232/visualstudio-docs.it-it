---
title: Panoramica delle funzionalità di diagnostica della | Microsoft Docs
description: Visual Studio Diagnostica della grafica è un set di strumenti per registrare l'attività Direct3D e analizzare i log per risolvere i problemi di rendering e prestazioni.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8c9ebb8ae3a0aba5a4059a01b5f2ba31359963eea058b519effbc28c40479630
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391318"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Panoramica di Diagnostica grafica di Visual Studio
*Diagnostica della grafica* di Visual Studio è un set di strumenti per la registrazione e l'analisi dei problemi di prestazioni e di rendering nelle app Direct3D. Diagnostica della grafica può essere usato nelle app in esecuzione in locale nel PC Windows o in un PC o un dispositivo remoto.

## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Uso della diagnostica grafica per eseguire il debug dei problemi di rendering
 Il debug dei problemi di rendering in un'app graficamente ricca non è semplice come l'avvio di un debugger e l'esecuzione di codice un'istruzione alla pagina. In ogni frame vengono prodotte centinaia di migliaia di pixel univoci, ciascuno in base a un set complesso di stati, dati, parametri e codice. Di questi, probabilmente solo pochi presenteranno il problema che si tenta di diagnosticare. Come se non bastasse, il codice che genera ciascun pixel viene eseguito in hardware specializzato che elabora centinaia di pixel in parallelo. Gli strumenti e le tecniche tradizionali di debug, difficili da sfruttare anche in codice con pochi thread, sono inefficaci di fronte a una quantità eccessiva di dati.

 Gli strumenti di diagnostica grafica in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sono progettati per individuare i problemi di rendering a partire dagli artefatti visivi che indicano il problema e quindi risalendo all'origine concentrandosi solo sul codice di shader pertinente, le fasi della pipeline, le chiamate di disegno, le risorse e lo stato del dispositivo nel codice sorgente dell'app.

## <a name="directx-version-compatibility"></a>Compatibilità tra versioni DirectX
 Diagnostica della grafica supporta le app che usano Direct3D 10 o versione successiva e offre supporto limitato per le app che usano Direct2D. Non supporta le app che usano versioni precedenti di Direct3D, DirectDraw o altre API grafiche.

### <a name="windows-10-and-direct3d-12"></a>Windows 10 e Direct3D 12
> [!NOTE]
> Visual Studio consiglia PIX su Windows per i giochi DirectX 12. [PIX in Windows](https://aka.ms/PIXonWindows) è uno strumento di ottimizzazione e debug delle prestazioni che supporta completamente DirectX 12. [Altre informazioni o](visual-studio-graphics-diagnostics-directx-12.md) download [sono disponibili qui.](https://aka.ms/downloadPIX)


 Windows 10 ha *introdotto Direct3D 12,* che è sostanzialmente diverso da Direct3D 10 e Direct3D 11. Queste differenze riportano DirectX in allineamento con l'hardware grafico moderno, consentendo di sfruttarne appieno il potenziale. Introducono inoltre notevoli modifiche alle API e comportano maggiori responsabilità per i programmatori in merito alla gestione dei conflitti e della durata delle risorse. Nonostante le differenze, Diagnostica della grafica direct3D 12 mantiene la parità delle funzionalità con Diagnostica della grafica con Direct3D 11.2.

 Windows 10 mantiene inoltre il supporto per le versioni precedenti di Direct3D, oltre che per i giochi e le applicazioni che si basano su di esse. Diagnostica della grafica in Visual Studio continua a supportare Direct3D 10 e Direct3D 11 in Windows 10.

### <a name="limited-direct2d-support"></a>Supporto Direct2D limitato
 Poiché Direct2D è un'API modalità utente basata su Direct3D, è possibile usare Diagnostica della grafica per agevolare il debug dei problemi di rendering nelle app che usano Direct2D. Tuttavia, poiché vengono registrati solo gli eventi Direct3D, anziché gli eventi Direct2D di livello superiore, gli eventi Direct2D non verranno visualizzati nell'elenco eventi grafici. Inoltre, poiché la relazione tra gli eventi Direct2D e gli eventi Direct3D risultanti non è sempre chiara, usare la diagnostica grafica per eseguire il debug dei problemi di rendering nelle app che usano Direct2D non è semplice. È comunque possibile usare la diagnostica della grafica per ottenere informazioni sui problemi di rendering di livello inferiore nelle app che usano Direct2D.

## <a name="graphics-diagnostics-features-in-visual-studio"></a>Funzionalità di diagnostica della grafica in Visual Studio
 Diagnostica della grafica offre un'interfaccia dedicata per la diagnosi dei problemi di rendering, ovvero la finestra Analizzatore grafica. Aggiunge anche alcuni strumenti all'interfaccia di Visual Studio.

### <a name="the-graphics-toolbar-visual-studio"></a>Barra degli strumenti di grafica (Visual Studio)
 La barra degli strumenti di grafica consente di accedere rapidamente ai comandi di diagnostica.

 Il pulsante **Avvia diagnostica** permette di eseguire l'app in Diagnostica della grafica. Quando un'app è in esecuzione in Diagnostica della grafica, il pulsante **Acquisisci il frame successivo di cui è stato eseguito il rendering** è abilitato.

### <a name="diagnostics-capture-interface"></a>Interfaccia di acquisizione della diagnostica
 Quando si esegue l'app in Diagnostica della grafica, Visual Studio visualizza un'interfaccia della sessione di diagnostica che è possibile usare per acquisire i frame e visualizzare il carico corrente della CPU e della GPU. Il carico della CPU e GPU viene mostrato per facilitare l'identificazione dei frame che può essere opportuno acquisire in base alle caratteristiche prestazionali anziché gli errori di rendering.

 Questo, tuttavia, non è l'unico modo per acquisire i frame. Si possono acquisire i frame anche tramite l'interfaccia programmatica di acquisizione oppure usando il programma di acquisizione da riga di comando, dxcap.exe.

 Per altre informazioni, vedere [Acquisizione di informazioni grafiche](capturing-graphics-information.md).

### <a name="gpu-usage"></a>Utilizzo GPU
 Diagnostica della grafica può anche profilare le prestazioni dell'app Direct3D. Poiché i dati di profilatura sarebbero falsati dalla registrazione di dettagli sugli eventi di grafica, questa funzione è distinta dall'acquisizione dei frame da esaminare con Analizzatore grafica.

 Per altre informazioni, vedere [Utilizzo GPU](../../profiling/gpu-usage.md).

### <a name="directx-control-panel"></a>Pannello di controllo DirectX
 Il pannello di controllo DirectX è un componente che consente di modificare il comportamento di DirectX. È ad esempio possibile abilitare la versione di debug dei componenti di runtime di DirectX, selezionare il tipo di messaggi di debug segnalati e impedire l'uso di determinate funzionalità dell'hardware grafico per emulare hardware meno potente. Questo livello di controllo su DirectX può facilitare il debug e il test dell'app DirectX. È possibile accedere al pannello di controllo DirectX da Visual Studio.

#### <a name="to-open-the-directx-control-panel"></a>Per aprire il pannello di controllo DirectX

- Nella barra dei menu scegliere **Debug**, **Grafica**, **Pannello di controllo DirectX**.

## <a name="graphics-analyzer"></a>Analizzatore grafica
 Analizzatore grafica di Visual Studio è un'interfaccia dedicata per l'esame dei problemi di prestazioni e di rendering in frame già acquisiti. All'interno di Analizzatore grafica sono disponibili diversi strumenti che semplificano la visualizzazione e la comprensione del comportamento di rendering dell'app. Ogni strumento espone informazioni di tipo diverso sul frame in esame. Gli strumenti sono progettati per un uso sinergico e consentono di isolare in modo intuitivo l'origine di un problema di rendering, a partire dalla sua comparsa nel buffer frame.

 Questa figura mostra un layout tipico di strumenti in Analizzatore grafica.

 ![Tutte le finestre debugger grafica](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")

### <a name="the-graphics-toolbar-graphics-analyzer"></a>Barra degli strumenti di grafica (Analizzatore grafica)
 La barra degli strumenti di grafica consente di accedere rapidamente alle finestre dello strumento Analizzatore grafica.

 ![Barra degli strumenti grafica in modalità diagnostica della grafica](media/vsg_toolbar.png "vsg_toolbar")

### <a name="graphics-log-document"></a>Documento di log della grafica
 Il documento di log della grafica è la finestra degli strumenti più importante di Analizzatore grafica. Questa finestra rappresenta tutti i frame acquisiti eseguendo l'app in Diagnostica grafica. Da qui è possibile selezionare un altro frame da esaminare o selezionare uno specifico pixel da esaminare con lo strumento Cronologia pixel. L'immagine del buffer frame mostrata in questo documento cambia in modo da riflettere l'evento attualmente selezionato, consentendo di visualizzarne l'effetto nel tempo sul buffer frame.

 Il [documento di log della grafica](graphics-log-document.md) rappresenta anche il punto di ingresso nello strumento Analisi dei frame, che aiuta a comprendere le prestazioni di un frame modificando la configurazione di alcuni aspetti del rendering e offrendo risultati benchmark da confrontare con l'originale.

### <a name="event-list"></a>Elenco eventi
 Gli eventi di grafica contrassegnano ogni chiamata API Direct3D e ogni evento definito dall'utente.

 [L'Elenco](graphics-event-list.md) eventi mostra tutti gli eventi grafici registrati durante il frame che si sta esaminando. Per individuare più facilmente gli elementi più importanti, è possibile visualizzare l'elenco eventi in due modi: in ordine gerarchico, con le modifiche dello stato recenti sotto la chiamata di disegno successiva, oppure come sequenza temporale. Inoltre, gli eventi sono contraddistinti da colori diversi in base alla coda di appartenenza ed è possibile filtrare l'elenco per includere solo gli eventi a cui si è interessati.

 Quando si seleziona un evento nell'elenco, gli altri strumenti di Analisi grafica riflettono lo stato del frame al momento dell'evento. In questo modo è possibile vedere l'effetto di qualsiasi evento nella GPU. Ad esempio, si può vedere l'effetto immediato di qualsiasi chiamata di disegno sul buffer frame, anche se viene nascosto dalle chiamate di disegno successive. Alcuni eventi dispongono anche di collegamenti ipertestuali, che è possibile seguire per accedere a maggiori dettagli sui parametri o sugli oggetti risorsa correlati.

### <a name="pipeline-stages"></a>Fasi pipeline
 Ogni chiamata di disegno dell'app passa attraverso la pipeline grafica fornita da Direct3D. In ogni fase della pipeline, l'output della fase precedente viene trasformato da un piccolo programma denominato shader e passato alla fase successiva fino al rendering finale sullo schermo. Molti errori di rendering si verificano al confine tra una fase della pipeline e l'altra, quando il formato di output è diverso rispetto a quanto previsto dalla fase successiva o semplicemente quando una qualsiasi fase genera risultati non corretti. In genere si ottengono solo i risultati finali così come verrebbero visualizzati sullo schermo e non è facile individuare il punto della pipeline in cui si è verificato l'errore.

 La [finestra Fasi pipeline](graphics-pipeline-stages.md) visualizza il risultato di ogni fase in modo indipendente, in modo da poter determinare più facilmente in quale fase viene visualizzato un problema di rendering per la prima volta. Dopo aver individuato la fase, si può possibile avviare il debug del relativo shader direttamente dalla finestra Fasi pipeline.

### <a name="graphics-state"></a>Stato grafica
 Le operazioni di rendering dipendono da una serie di stati, in genere condivisi tra più oggetti. Molti tipi di problemi di rendering sono causati da uno stato non configurato correttamente.

 La finestra [Stato](graphics-state.md) raccoglie in un'unica posizione le informazioni di stato relative a ogni chiamata di disegno, rendendole più semplici da trovare. Inoltre, evidenzia le modifiche dello stato che si sono verificate dopo la chiamata di disegno precedente.

### <a name="pixel-history"></a>Cronologia pixel
 Nelle scene complesse, non è raro che un pixel venga ombreggiato più volte in un singolo frame. A volte il colore precedente viene semplicemente sovrascritto, ma in alcuni casi i colori vengono combinati per ottenere effetti, come la trasparenza. Quando il risultato della combinazione dei colori non è quello desiderato, non è facile stabilire se il motivo è che uno dei colori è sbagliato o se il problema è dovuto al modo in cui sono stati combinati. In altri casi, un oggetto può sembrare mancante perché per qualche motivo il suo contributo al pixel è stato rifiutato.

 La [finestra Cronologia](graphics-pixel-history.md) pixel visualizza la cronologia shader completa di ogni pixel nel frame, inclusi i contributi rifiutati. Per i contributi non rifiutati, mostra i risultati dello shader non elaborati e le modalità di combinazione di ogni nuovo colore con il precedente. Con queste informazioni, è molto più semplice individuare l'origine degli errori nei pixel che fondono risultati degli shader o determinare quando un oggetto di cui è stato eseguito il rendering manca perché il relativo contributo al pixel è stato erroneamente rifiutato.

### <a name="event-call-stack"></a>Stack di chiamate eventi
 Il codice dello shader non è l'unica fonte dei problemi di rendering in un'app Direct3D. A volte il codice sorgente dell'app passa un parametro errato o non configura Direct3D in modo corretto. Un tipo di errore che la funzionalità descritta in precedenza, Cronologia pixel, consente di individuare facilmente, è rappresentato dai casi in cui un oggetto sottoposto a rendering risulta mancante in quanto tutti i suoi pixel sono stati rifiutati. Questo tipo di errore si verifica in genere quando un'impostazione è configurata in modo non corretto, ad esempio quella che controlla la modalità di esecuzione del test di profondità. Normalmente, è possibile trovare l'errore nello stack di chiamate della chiamata di disegno dell'oggetto mancante.

 La [finestra Stack di chiamate](graphics-event-call-stack.md) eventi visualizza lo stack di chiamate completo di ogni evento grafico nell'elenco eventi e consente anche di passare al codice sorgente dell'app se sono disponibili informazioni di debug. Si tratta di uno strumento potente per seguire un errore dal punto in cui viene visualizzato per la prima volta, nella GPU, al punto in cui ha avuto origine nel codice sorgente dell'applicazione.

### <a name="object-table"></a>Tabella oggetti
 Ogni frame di cui l'app esegue il rendering è probabilmente supportato da centinaia o persino migliaia di oggetti risorsa. Questo include buffer e destinazioni di rendering, trame, buffer dei vertici, buffer degli indici, buffer generali e quasi tutto ciò che Direct3D considera un oggetto.

 La [tabella oggetti](graphics-object-table.md) visualizza tutti gli oggetti esistenti al momento dell'evento grafico selezionato nell'elenco eventi. Poiché in un'app tipica gli oggetti sono per lo più trame, l'elenco eventi è ottimizzato per visualizzare immediatamente i dettagli pertinenti alle immagini. La colonna Tipo indica il tipo di oggetto presente in ogni riga, mentre la colonna Formato mostra il sottotipo o la versione dell'oggetto. Sono disponibili anche altri dettagli. Alcuni oggetti dispongono anche di collegamenti ipertestuali, che è possibile seguire per esaminare l'oggetto con un visualizzatore più specializzato, ad esempio di trame (si può visualizzare la trama come immagine) o di buffer (si può scegliere come il visualizzatore buffer analizza e mostra i byte non elaborati definendo il formato del buffer).

### <a name="frame-analysis"></a>Analisi dei frame
 La grafica dell'app deve essere corretta e veloce, anche in dispositivi meno potenti come computer portatili con grafica integrata o telefoni cellulari. In più, deve essere di qualità elevata.

 Lo strumento [Analisi dei frame](graphics-frame-analysis.md) esplora le potenziali ottimizzazioni delle prestazioni modificando automaticamente il modo in cui l'app usa Direct3D e offrendo risultati benchmark per il confronto. Ad esempio, Analisi dei frame può abilitare il mapping MIP in ogni trama, evidenziando le trame che possono trarre vantaggio dal mapping MIP e in cui non è attualmente abilitato. Sull'hardware supportato, Analisi dei frame presenta anche informazioni raccolte dai contatori delle prestazioni della GPU. Questo livello di informazioni consente di identificare i problemi di prestazioni a livello di hardware, ad esempio un numero elevato di blocchi nel recupero delle trame o mancati riscontri nella cache.

 Analisi dei frame, tuttavia, non è utile solo per la velocità: consente anche di ottenere il massimo delle prestazioni e allo stesso tempo della qualità visiva. A volte un effetto costoso che sembra eccezionale su un display di grandi dimensioni non ha lo stesso impatto sul piccolo schermo di un telefono cellulare, dove un effetto più semplice potrebbe produrre risultati altrettanto buoni senza scaricare la batteria. Le modifiche automatiche e i benchmark offerti da Analisi grafica consentono di trovare il giusto equilibrio per ogni app in un'ampia gamma di dispositivi.

## <a name="see-also"></a>Vedi anche
- [Strumento di acquisizione da riga di comando](command-line-capture-tool.md)
- [Debugger HLSL](hlsl-shader-debugger.md)
