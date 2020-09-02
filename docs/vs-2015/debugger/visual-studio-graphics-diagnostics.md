---
title: Diagnostica della grafica di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca0a1613f46f8542a3ede4ce2053b3584824590e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847820"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostica della grafica di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*diagnostica della grafica* è un set di strumenti per la registrazione e l'analisi dei problemi di prestazioni e di rendering nelle app Direct3D. Può essere usato su app eseguite localmente in un computer Windows, in un emulatore di dispositivo Windows oppure in un computer o un dispositivo remoto.  
  
 Il flusso di lavoro di Diagnostica grafica inizia con l'acquisizione di informazioni sul modo in cui l'app usa Direct3D durante l'esecuzione, in modo che il comportamento possa essere analizzato immediatamente, condiviso o salvato per un momento successivo. Le sessioni di acquisizione possono essere avviate e controllate manualmente da Visual Studio o con lo strumento di acquisizione da riga di comando **dxcap.exe**. Le sessioni di acquisizione possono anche essere avviate e controllate a livello di codice usando le API di acquisizione Diagnostica della grafica.  
  
 Dopo la registrazione di una sessione di acquisizione, è possibile riprodurne il contenuto in qualsiasi momento con *Analizzatore grafica* di Visual Studio, ricreando i frame acquisiti mediante le stesse risorse e gli stessi comandi di rendering usati dall'app. Quindi, usando gli strumenti forniti nella finestra analizzatore grafica, i frame acquisiti possono essere analizzati in dettaglio. Questi strumenti consentono di esaminare qualsiasi chiamata alle API Direct3D, risorsa, oggetto di stato della pipeline, fase della pipeline o anche la cronologia completa di qualsiasi pixel in un frame acquisito. Usando questi strumenti insieme si può esplorare un problema di rendering in modo intuitivo, a partire dal modo in cui si manifesta in un frame acquisito ed eseguendo il drill-down alla causa radice nel codice sorgente dell'app, negli shader o nelle risorse grafiche.  
  
 Per diagnosticare i problemi di prestazioni, è possibile analizzare un frame acquisito usando lo strumento *Analisi dei frame*. Questo strumento esplora le potenziali ottimizzazioni delle prestazioni modificando automaticamente il modo in cui l'app usa Direct3D ed effettuando un benchmark di tutte le variazioni. In passato questi benchmark e queste modifiche venivano eseguiti manualmente, semplicemente per verificare quali modifiche creassero effettivamente una differenza. Grazie ad Analisi dei frame, è possibile apportare solo modifiche di cui si conosce già il valore.  
  
 Diagnostica grafica aiuta a ottimizzare l'esecuzione e l'aspetto delle app Direct3D con contenuti grafici avanzati.  
  
 Per ulteriori informazioni sulle funzionalità offerte da Visual Studio Diagnostica della grafica, continuare con la [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md) .  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Viene fornita un'introduzione agli strumenti di diagnostica della grafica e al relativo flusso di lavoro.  
  
 [Per iniziare](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Questa sezione illustra come installare Diagnostica grafica di Visual Studio e come iniziare a usare Diagnostica grafica con le app Direct3D.  
  
 [Acquisizione di informazioni grafiche](../debugger/capturing-graphics-information.md)  
 Per usare la diagnostica della grafica al fine di esaminare un problema di rendering nell'app, è necessario prima registrare informazioni su come l'app stessa usa DirectX. Durante la sessione di registrazione, nel corso della normale esecuzione dell'app, *acquisire* (ossia selezionare) i frame che interessano. Le acquisizioni contengono informazioni dettagliate sulla modalità di rendering dei frame. È possibile salvare le informazioni acquisite come documento di log della grafica da esaminare in un secondo momento o da condividere con gli altri membri del team.  
  
 [Utilizzo GPU](../debugger/gpu-usage.md)  
 Per usare Diagnostica grafica per profilare un'app, usare lo strumento Utilizzo GPU. Utilizzo GPU può essere usato insieme ad altri strumenti di profilatura, ad esempio Utilizzo CPU, per correlare le attività della CPU e GPU che potrebbero contribuire a problemi di prestazioni nell'app.  
  
 [Documento log grafica](../debugger/graphics-log-document.md)  
 Per iniziare l'esame di un log di grafica registrato, usare la finestra dei documenti di log della grafica per selezionare un frame acquisito, o anche un pixel specifico, ed esaminare nel dettaglio gli *eventi* (ovvero le chiamate API di DirectX) che hanno effetto su di esso.  
  
 [Analisi dei frame](../debugger/graphics-frame-analysis.md)  
 Dopo aver selezionato un frame, usare l'analisi dei frame di grafica per esaminare e ottimizzare le prestazioni di rendering.  
  
 [Elenco eventi](../debugger/graphics-event-list.md)  
 Dopo aver selezionato un frame, è possibile usare l'**elenco degli eventi grafici** per esaminarne gli eventi e determinare se sono correlati al problema di rendering.  
  
 [State](../debugger/graphics-state.md)  
 La finestra Stato consente di comprendere lo stato di grafica attivo al momento dell'evento corrente.  
  
 [Fasi della pipeline](../debugger/graphics-pipeline-stages.md)  
 Nella finestra **Fasi pipeline grafica** è possibile analizzare le modalità di elaborazione dell'evento attualmente selezionato in ogni fase della pipeline grafica, per identificare l'origine del problema di rendering. L'esame delle fasi della pipeline è particolarmente utile quando un oggetto non viene visualizzato a causa di una trasformazione non corretta o quando una delle fasi produce output non corrispondente a quanto atteso dalla fase successiva.  
  
 [Stack di chiamate eventi](../debugger/graphics-event-call-stack.md)  
 È possibile usare lo **Stack di chiamate eventi grafici** per esaminare lo stack di chiamate dell'evento attualmente selezionato, in modo da poter raggiungere la porzione di codice dell'app correlata al problema di rendering.  
  
 [Cronologia pixel](../debugger/graphics-pixel-history.md)  
 Usando la finestra **Cronologia pixel grafica** per analizzare il modo in cui il pixel attualmente selezionato è interessato dagli eventi che lo influenzano, è possibile identificare l'evento o la combinazione di eventi che causano determinati tipi di problemi di rendering. La cronologia del pixel è particolarmente utile quando il rendering di un oggetto viene eseguito in modo errato, perché l'output del pixel shader è a sua volta errato o è combinato in modo errato con il buffer del frame, o quando un oggetto non viene nemmeno visualizzato in quanto i pixel vengono rimossi prima ancora di raggiungere il buffer frame.  
  
 [Tabella oggetti](../debugger/graphics-object-table.md)  
 È possibile usare la **Tabella oggetti grafici** per esaminare le proprietà e i contenuti di risorse e oggetti specifici Direct3D che hanno effetto sull'evento attualmente selezionato. La tabella degli oggetti può aiutare a determinare il contesto dei dispositivi grafici attivi durante un evento nonché a esaminare i contenuti di risorse grafiche come i buffer costanti, i buffer vertici e le trame.  
  
 [Debugger HLSL](../debugger/hlsl-shader-debugger.md)  
 Per esaminare come si comporta il codice dello shader per l'evento nonché per la fase della pipeline grafica attualmente selezionati, usare il **debugger HLSL** per avanzare nel codice, esaminare il contenuto delle variabili ed eseguire altre attività di debug comuni. È anche possibile usare il debugger HLSL per esaminare il codice del compute shader, indipendentemente dal fatto che i risultati vengano ulteriormente elaborati dalla pipeline grafica o siano stati appena letti dall'app.  
  
 [Strumento di acquisizione da riga di comando](../debugger/command-line-capture-tool.md)  
 Usare lo strumento di acquisizione da riga di comando per acquisire e riprodurre rapidamente le informazioni grafiche senza usare Visual Studio o l'acquisizione a livello di codice. In particolare, è possibile usare lo strumento di acquisizione da riga di comando per l'automazione o in un ambiente di test.  
  
 [esempi](../debugger/graphics-diagnostics-examples.md)  
 Vari esempi mostrano come usare gli strumenti di diagnostica della grafica per diagnosticare diversi tipi di problemi di rendering.  
  
## <a name="related-sections"></a>Sezioni correlate  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)|Introduce le funzionalità di debug in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Grafica e giochi DirectX](https://msdn.microsoft.com/library/ee663274(v=vs.85).aspx)|Include articoli che illustrano le tecnologie grafiche DirectX.|
