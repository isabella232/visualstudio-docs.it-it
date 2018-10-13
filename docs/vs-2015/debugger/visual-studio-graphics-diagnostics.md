---
title: Diagnostica della grafica di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1ada0fb0379846d7c0a0af5a6ab28906b29f619
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294203"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostica della grafica di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*diagnostica della grafica* è un set di strumenti per la registrazione e quindi eseguire l'analisi dei problemi di prestazioni e di rendering nelle App Direct3D. Può essere usato su app eseguite localmente in un computer Windows, in un emulatore di dispositivo Windows oppure in un computer o un dispositivo remoto.  
  
 Il flusso di lavoro di Diagnostica della grafica inizia con l'acquisizione di informazioni sul modo in cui l'app usa Direct3D durante l'esecuzione, in modo che il comportamento possa essere analizzato immediatamente, condiviso o salvato per un momento successivo. Sessioni di acquisizione possono essere avviate e controllate manualmente da Visual Studio o con lo strumento di acquisizione da riga di comando **dxcap.exe**. Possono anche essere avviate e controllate a livello di programmazione usando le API di acquisizione di Diagnostica della grafica.  
  
 Dopo una sessione di acquisizione è stata registrata il suo contenuto può essere riprodotti da Visual Studio *analizzatore grafica* in qualsiasi momento, ricreando i frame acquisiti usando le stesse risorse esatte e comandi di rendering dell'app usati. Quindi, usando gli strumenti forniti nella finestra Analizzatore grafica, è possibile analizzare in dettaglio tutti i frame acquisiti. Questi strumenti consentono di esaminare qualsiasi chiamata alle API Direct3D, risorsa, oggetto di stato della pipeline, fase della pipeline o anche la cronologia completa di qualsiasi pixel in un frame acquisito. Usando questi strumenti insieme si può esplorare un problema di rendering in modo intuitivo, a partire dal modo in cui si manifesta in un frame acquisito ed eseguendo il drill-down alla causa radice nel codice sorgente dell'app, negli shader o nelle risorse grafiche.  
  
 Per diagnosticare i problemi di prestazioni, è possibile analizzare un frame acquisito tramite il *analisi dei Frame* dello strumento. Questo strumento esplora le potenziali ottimizzazioni delle prestazioni modificando automaticamente il modo in cui l'app usa Direct3D ed effettuando un benchmark di tutte le variazioni. In passato questi benchmark e queste modifiche venivano eseguiti manualmente, semplicemente per verificare quali modifiche creassero effettivamente una differenza. Grazie ad Analisi dei frame, è possibile apportare solo modifiche di cui si conosce già il valore.  
  
 Diagnostica della grafica aiuta a ottimizzare l'esecuzione e l'aspetto delle app Direct3D con contenuti grafici avanzati.  
  
 Continuare a [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md) per altre informazioni sulle funzionalità offerte di Visual Studio Graphics Diagnostics.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Viene fornita un'introduzione agli strumenti di diagnostica della grafica e al relativo flusso di lavoro.  
  
 [Introduzione](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Questa sezione illustra come installare Diagnostica della grafica di Visual Studio e come iniziare a usare Diagnostica della grafica con le app Direct3D.  
  
 [Capturing Graphics Information](../debugger/capturing-graphics-information.md)  
 Per usare la diagnostica della grafica al fine di esaminare un problema di rendering nell'app, è necessario prima registrare informazioni su come l'app stessa usa DirectX. Durante la sessione di registrazione, come l'app viene eseguita in genere, si *acquisire* (ossia selezionare) i frame che si sono interessati. Le acquisizioni contengono informazioni dettagliate sulla modalità di rendering dei frame. È possibile salvare le informazioni acquisite come documento di log della grafica da esaminare in un secondo momento o da condividere con gli altri membri del team.  
  
 [Utilizzo GPU](../debugger/gpu-usage.md)  
 Per usare Diagnostica della grafica per profilare un'app, usare lo strumento Utilizzo GPU. Utilizzo GPU può essere usato insieme ad altri strumenti di profilatura, ad esempio Utilizzo CPU, per correlare le attività della CPU e GPU che potrebbero contribuire a problemi di prestazioni nell'app.  
  
 [Documento di log della grafica](../debugger/graphics-log-document.md)  
 Per avviare l'esame di un log di grafica registrato, utilizzare la finestra del documento Log grafica per selezionare un frame acquisito, o anche un pixel specifico, in modo da poter esaminare in dettaglio le *eventi* (vale a dire, chiamate API di DirectX) vi influiscono .  
  
 [Analisi dei frame](../debugger/graphics-frame-analysis.md)  
 Dopo aver selezionato un frame, usare l'analisi dei frame di grafica per esaminare e ottimizzare le prestazioni di rendering.  
  
 [Elenco eventi](../debugger/graphics-event-list.md)  
 Dopo aver selezionato un frame, usare il **elenco eventi grafici** per esaminarne gli eventi per determinare se sono correlati al problema di rendering.  
  
 [Stato](../debugger/graphics-state.md)  
 La finestra Stato consente di comprendere lo stato di grafica attivo al momento dell'evento corrente.  
  
 [Fasi della pipeline](../debugger/graphics-pipeline-stages.md)  
 Nel **fasi Pipeline grafica** finestra, si esamina la modalità di elaborazione in ogni fase della pipeline grafica dell'evento attualmente selezionato in modo che sia possibile identificare in cui viene visualizzato innanzitutto il problema di rendering. L'esame delle fasi della pipeline è particolarmente utile quando un oggetto non viene visualizzato a causa di una trasformazione non corretta o quando una delle fasi produce output non corrispondente a quanto atteso dalla fase successiva.  
  
 [Stack di chiamate a eventi](../debugger/graphics-event-call-stack.md)  
 Si utilizza il **Stack di chiamate eventi di grafica** per esaminare lo stack di chiamate dell'evento attualmente selezionato in modo che possa passare al codice dell'app che è correlato al problema di rendering.  
  
 [Cronologia Pixel](../debugger/graphics-pixel-history.md)  
 Tramite il **cronologia Pixel grafica** finestra da analizzare come il pixel attualmente selezionato è interessato dagli eventi che lo influenzano, è possibile identificare l'evento o una combinazione di eventi che causano determinati tipi di problemi di rendering. La cronologia del pixel è particolarmente utile quando il rendering di un oggetto viene eseguito in modo errato, perché l'output del pixel shader è a sua volta errato o è combinato in modo errato con il buffer del frame, o quando un oggetto non viene nemmeno visualizzato in quanto i pixel vengono rimossi prima ancora di raggiungere il buffer frame.  
  
 [Tabella oggetti](../debugger/graphics-object-table.md)  
 Si utilizza il **tabella oggetti grafici** per esaminare le proprietà e il contenuto di oggetti specifici Direct3D e risorse che sono attivi per l'evento attualmente selezionato. La tabella degli oggetti può aiutare a determinare il contesto dei dispositivi grafici attivi durante un evento nonché a esaminare i contenuti di risorse grafiche come i buffer costanti, i buffer vertici e le trame.  
  
 [Debugger HLSL](../debugger/hlsl-shader-debugger.md)  
 Per esaminare il codice dello shader per l'evento attualmente selezionato e la grafica fase della pipeline comportamento, si utilizza il **Debugger HLSL** per avanzare nel codice, esaminare il contenuto delle variabili ed eseguire altre attività di debug comuni. È anche possibile usare il debugger HLSL per esaminare il codice del compute shader, indipendentemente dal fatto che i risultati vengano ulteriormente elaborati dalla pipeline grafica o siano stati appena letti dall'app.  
  
 [Strumento di acquisizione da riga di comando](../debugger/command-line-capture-tool.md)  
 Usare lo strumento di acquisizione da riga di comando per acquisire e riprodurre rapidamente le informazioni grafiche senza usare Visual Studio o l'acquisizione a livello di codice. In particolare, è possibile usare lo strumento di acquisizione da riga di comando per l'automazione o in un ambiente di test.  
  
 [Esempi](../debugger/graphics-diagnostics-examples.md)  
 Vari esempi mostrano come usare gli strumenti di diagnostica della grafica per diagnosticare diversi tipi di problemi di rendering.  
  
## <a name="related-sections"></a>Sezioni correlate  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)|Introduce le funzionalità di debug in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Grafica e giochi DirectX](http://go.microsoft.com/fwlink/?LinkId=256498)|Include articoli che illustrano le tecnologie grafiche DirectX.|



