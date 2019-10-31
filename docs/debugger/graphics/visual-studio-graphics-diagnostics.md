---
title: Diagnostica della grafica | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e69d88bb5764836d82232cec26606009eaf694d7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187742"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostica della grafica di Visual Studio
Visual Studio*diagnostica della grafica* è un set di strumenti per la registrazione e l'analisi dei problemi di prestazioni e di rendering nelle app Direct3D. Può essere usato su app eseguite localmente in un computer Windows, in un emulatore di dispositivo Windows oppure in un computer o un dispositivo remoto.

 Il flusso di lavoro di Diagnostica grafica inizia con l'acquisizione di informazioni sul modo in cui l'app usa Direct3D durante l'esecuzione, in modo che il comportamento possa essere analizzato immediatamente, condiviso o salvato per un momento successivo. Le sessioni di acquisizione possono essere avviate e controllate manualmente da Visual Studio o con lo strumento di acquisizione da riga di comando **dxcap. exe**. Le sessioni di acquisizione possono anche essere avviate e controllate a livello di codice usando le API di acquisizione Diagnostica della grafica.

 Dopo la registrazione di una sessione di acquisizione, è possibile riprodurne il contenuto in qualsiasi momento con *Analizzatore grafica* di Visual Studio, ricreando i frame acquisiti mediante le stesse risorse e gli stessi comandi di rendering usati dall'app. Quindi, usando gli strumenti forniti nella finestra analizzatore grafica, i frame acquisiti possono essere analizzati in dettaglio. Questi strumenti consentono di esaminare qualsiasi chiamata alle API Direct3D, risorsa, oggetto di stato della pipeline, fase della pipeline o anche la cronologia completa di qualsiasi pixel in un frame acquisito. Usando questi strumenti insieme si può esplorare un problema di rendering in modo intuitivo, a partire dal modo in cui si manifesta in un frame acquisito ed eseguendo il drill-down alla causa radice nel codice sorgente dell'app, negli shader o nelle risorse grafiche.

 Per diagnosticare i problemi di prestazioni, è possibile analizzare un frame acquisito usando lo strumento *Analisi dei frame*. Questo strumento esplora le potenziali ottimizzazioni delle prestazioni modificando automaticamente il modo in cui l'app usa Direct3D ed effettuando un benchmark di tutte le variazioni. In passato questi benchmark e queste modifiche venivano eseguiti manualmente, semplicemente per verificare quali modifiche creassero effettivamente una differenza. Grazie ad Analisi dei frame, è possibile apportare solo modifiche di cui si conosce già il valore.

 Diagnostica grafica aiuta a ottimizzare l'esecuzione e l'aspetto delle app Direct3D con contenuti grafici avanzati.

 Per ulteriori informazioni sulle funzionalità offerte da Visual Studio Diagnostica della grafica, continuare con la [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) .

## <a name="in-this-section"></a>Contenuto della sezione
 [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) di Vengono introdotti il flusso di lavoro e gli strumenti Diagnostica della grafica.

 [Introduzione](getting-started-with-visual-studio-graphics-diagnostics.md) Questa sezione illustra come installare Visual Studio Diagnostica della grafica e come iniziare a usare Diagnostica della grafica con l'app Direct3D.

 [Acquisizione delle informazioni grafiche](capturing-graphics-information.md) Per usare Diagnostica della grafica per esaminare un problema di rendering nell'app, è prima di tutto necessario registrare le informazioni sul modo in cui l'app usa DirectX. Durante la sessione di registrazione, nel corso della normale esecuzione dell'app, *acquisire* (ossia selezionare) i frame che interessano. Le acquisizioni contengono informazioni dettagliate sulla modalità di rendering dei frame. È possibile salvare le informazioni acquisite come documento di log della grafica da esaminare in un secondo momento o da condividere con gli altri membri del team.

 [Utilizzo GPU](../../profiling/gpu-usage.md) Per usare Diagnostica della grafica per profilare l'app, usare lo strumento utilizzo GPU. Utilizzo GPU può essere usato insieme ad altri strumenti di profilatura, ad esempio Utilizzo CPU, per correlare le attività della CPU e GPU che potrebbero contribuire a problemi di prestazioni nell'app.

 [Documento di log di grafica](graphics-log-document.md) Per avviare l'analisi di un log di grafica registrato, usare la finestra del documento del log di grafica per selezionare un frame acquisito, o anche un pixel specifico, in modo che sia possibile esaminare in dettaglio gli *eventi* , ovvero le chiamate all'API DirectX, che lo influiscono.

 [Analisi di frame](graphics-frame-analysis.md) Dopo aver selezionato un frame, utilizzare analisi dei frame di grafica per esaminare e ottimizzare le prestazioni di rendering.

 [Elenco eventi](graphics-event-list.md) Dopo aver selezionato un frame, è possibile usare l' **elenco eventi di grafica** per esaminare gli eventi per determinare se sono correlati al problema di rendering.

 [Stato](graphics-state.md) di La finestra stato consente di comprendere lo stato di grafica attivo al momento dell'evento corrente.

 [Fasi della pipeline](graphics-pipeline-stages.md) Nella finestra **fasi pipeline grafica** è possibile esaminare il modo in cui l'evento attualmente selezionato viene elaborato da ogni fase della pipeline grafica, in modo che sia possibile identificare la posizione in cui viene prima visualizzato il problema di rendering. L'esame delle fasi della pipeline è particolarmente utile quando un oggetto non viene visualizzato a causa di una trasformazione non corretta o quando una delle fasi produce output non corrispondente a quanto atteso dalla fase successiva.

 [Stack di chiamate eventi](graphics-event-call-stack.md) Usare lo **stack di chiamate eventi di grafica** per esaminare lo stack di chiamate dell'evento attualmente selezionato in modo che sia possibile passare al codice dell'app correlato al problema di rendering.

 [Cronologia pixel](graphics-pixel-history.md) Utilizzando la finestra **Cronologia pixel grafica** per analizzare il modo in cui il pixel attualmente selezionato è influenzato dagli eventi che lo hanno influenzato, è possibile identificare l'evento o la combinazione di eventi che provocano determinati tipi di problemi di rendering. La cronologia del pixel è particolarmente utile quando il rendering di un oggetto viene eseguito in modo errato, perché l'output del pixel shader è a sua volta errato o è combinato in modo errato con il buffer del frame, o quando un oggetto non viene nemmeno visualizzato in quanto i pixel vengono rimossi prima ancora di raggiungere il buffer frame.

 [Tabella oggetti](graphics-object-table.md) Usare la **tabella oggetti grafici** per esaminare le proprietà e il contenuto di oggetti e risorse Direct3D specifici che sono attivi per l'evento attualmente selezionato. La tabella degli oggetti può aiutare a determinare il contesto dei dispositivi grafici attivi durante un evento nonché a esaminare i contenuti di risorse grafiche come i buffer costanti, i buffer vertici e le trame.

 [Debugger HLSL](hlsl-shader-debugger.md) Per esaminare il comportamento del codice dello shader per l'evento e la fase della pipeline grafica attualmente selezionati, è possibile usare il **debugger HLSL** per eseguire il codice un'istruzione alla volta, esaminare il contenuto delle variabili ed eseguire altre attività di debug tipiche. È anche possibile usare il debugger HLSL per esaminare il codice del compute shader, indipendentemente dal fatto che i risultati vengano ulteriormente elaborati dalla pipeline grafica o siano stati appena letti dall'app.

 [Strumento di acquisizione da riga di comando](command-line-capture-tool.md) Usare lo strumento di acquisizione da riga di comando per acquisire e riprodurre rapidamente le informazioni grafiche senza usare Visual Studio o l'acquisizione a livello di codice. In particolare, è possibile usare lo strumento di acquisizione da riga di comando per l'automazione o in un ambiente di test.

 [Esempi](graphics-diagnostics-examples.md) di Molti esempi illustrano come usare insieme gli strumenti Diagnostica della grafica per diagnosticare diversi tipi di problemi di rendering.

## <a name="related-sections"></a>Sezioni correlate

| Titolo | Descrizione |
| - | - |
| [Tour delle funzionalità del debugger](../debugger-feature-tour.md) | Introduce le funzionalità di debug in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Grafica e giochi DirectX](/windows/win32/directx) | Include articoli che illustrano le tecnologie grafiche DirectX. |
