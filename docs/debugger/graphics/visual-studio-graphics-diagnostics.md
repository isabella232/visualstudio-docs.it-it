---
title: Diagnostica della grafica | Microsoft Docs
description: Visual Studio Diagnostica della grafica è un set di strumenti per la registrazione e l'analisi dell'attività Direct3D. Usarli per risolvere i problemi di rendering e prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 04cc77650572f5e3539d4b53e4602e4c16259b61
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090837"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostica della grafica di Visual Studio
>[!NOTE]
> Visual Studio consiglia PIX su Windows per i giochi DirectX 12. [PIX in Windows](https://aka.ms/PIXonWindows) è uno strumento di ottimizzazione e debug delle prestazioni che supporta completamente DirectX 12. [Altre informazioni o](visual-studio-graphics-diagnostics-directx-12.md) download [sono disponibili qui.](https://aka.ms/downloadPIX)

*Diagnostica della grafica* di Visual Studio è un set di strumenti per la registrazione e l'analisi dei problemi di prestazioni e di rendering nelle app Direct3D. Può essere usato su app eseguite localmente in un computer Windows, in un emulatore di dispositivo Windows oppure in un computer o un dispositivo remoto.

 Il flusso di lavoro di Diagnostica grafica inizia con l'acquisizione di informazioni sul modo in cui l'app usa Direct3D durante l'esecuzione, in modo che il comportamento possa essere analizzato immediatamente, condiviso o salvato per un momento successivo. Le sessioni di acquisizione possono essere avviate e controllate manualmente da Visual Studio o con lo strumento di acquisizione da riga di **comandodxcap.exe**. Le sessioni di acquisizione possono anche essere avviate e controllate a livello di codice usando le API di Diagnostica della grafica di acquisizione.

 Dopo la registrazione di una sessione di acquisizione, è possibile riprodurne il contenuto in qualsiasi momento con *Analizzatore grafica* di Visual Studio, ricreando i frame acquisiti mediante le stesse risorse e gli stessi comandi di rendering usati dall'app. Usando quindi gli strumenti disponibili nella finestra Analizzatore grafica, è possibile analizzare in dettaglio i frame acquisiti. Questi strumenti consentono di esaminare qualsiasi chiamata alle API Direct3D, risorsa, oggetto di stato della pipeline, fase della pipeline o anche la cronologia completa di qualsiasi pixel in un frame acquisito. Usando questi strumenti insieme si può esplorare un problema di rendering in modo intuitivo, a partire dal modo in cui si manifesta in un frame acquisito ed eseguendo il drill-down alla causa radice nel codice sorgente dell'app, negli shader o nelle risorse grafiche.

 Per diagnosticare i problemi di prestazioni, è possibile analizzare un frame acquisito usando lo strumento *Analisi dei frame*. Questo strumento esplora le potenziali ottimizzazioni delle prestazioni modificando automaticamente il modo in cui l'app usa Direct3D ed effettuando un benchmark di tutte le variazioni. In passato questi benchmark e queste modifiche venivano eseguiti manualmente, semplicemente per verificare quali modifiche creassero effettivamente una differenza. Grazie ad Analisi dei frame, è possibile apportare solo modifiche di cui si conosce già il valore.

 Diagnostica grafica aiuta a ottimizzare l'esecuzione e l'aspetto delle app Direct3D con contenuti grafici avanzati.

 Passare a [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) per altre informazioni sulle Visual Studio Diagnostica della grafica offerte.

## <a name="in-this-section"></a>Contenuto della sezione
 [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) Vengono presentati il flusso Diagnostica della grafica e gli strumenti.

 [Attività iniziali](getting-started-with-visual-studio-graphics-diagnostics.md) In questa sezione si apprenderà come installare Visual Studio Diagnostica della grafica e come iniziare a usare Diagnostica della grafica con l'app Direct3D.

 [Acquisizione di informazioni grafiche](capturing-graphics-information.md) Per usare Diagnostica della grafica esaminare un problema di rendering nell'app, registrare prima di tutto le informazioni sul modo in cui l'app usa DirectX. Durante la sessione di registrazione, nel corso della normale esecuzione dell'app, *acquisire* (ossia selezionare) i frame che interessano. Le acquisizioni contengono informazioni dettagliate sulla modalità di rendering dei frame. È possibile salvare le informazioni acquisite come documento di log della grafica da esaminare in un secondo momento o da condividere con gli altri membri del team.

 [Utilizzo GPU](../../profiling/gpu-usage.md) Per usare Diagnostica della grafica profilare l'app, usare lo strumento Utilizzo GPU. Utilizzo GPU può essere usato insieme ad altri strumenti di profilatura, ad esempio Utilizzo CPU, per correlare le attività della CPU e GPU che potrebbero contribuire a problemi di prestazioni nell'app.

 [Documento di log di grafica](graphics-log-document.md) Per iniziare l'esame di un log di grafica registrato, usare la finestra del documento Log di grafica per selezionare un frame acquisito, o anche un pixel specifico, in modo da poter esaminare in dettaglio gli eventi *(ovvero* le chiamate api DirectX) che lo interessano.

 [Analisi dei frame](graphics-frame-analysis.md) Dopo aver selezionato un frame, è possibile usare analisi dei frame di grafica per esaminare e ottimizzare le prestazioni di rendering.

 [Elenco eventi](graphics-event-list.md) Dopo aver selezionato un frame, usare l'Elenco **eventi di grafica** per esaminarne gli eventi per determinare se sono correlati al problema di rendering.

 [Stato](graphics-state.md) La finestra Stato consente di comprendere lo stato grafico attivo al momento dell'evento corrente.

 [Fasi della pipeline](graphics-pipeline-stages.md) Nella finestra **Fasi pipeline** grafica si esamina il modo in cui l'evento attualmente selezionato viene elaborato da ogni fase della pipeline grafica in modo da poter identificare la prima posizione in cui viene visualizzato il problema di rendering. L'esame delle fasi della pipeline è particolarmente utile quando un oggetto non viene visualizzato a causa di una trasformazione non corretta o quando una delle fasi produce output non corrispondente a quanto atteso dalla fase successiva.

 [Stack di chiamate eventi](graphics-event-call-stack.md) Lo stack **di chiamate degli eventi** di grafica viene utilizzato per esaminare lo stack di chiamate dell'evento attualmente selezionato, in modo da poter passare al codice dell'app correlato al problema di rendering.

 [Cronologia pixel](graphics-pixel-history.md) Usando la finestra Cronologia **pixel** grafica per analizzare il modo in cui il pixel attualmente selezionato è interessato dagli eventi che lo hanno influenzato, è possibile identificare l'evento o la combinazione di eventi che causano determinati tipi di problemi di rendering. La cronologia del pixel è particolarmente utile quando il rendering di un oggetto viene eseguito in modo errato, perché l'output del pixel shader è a sua volta errato o è combinato in modo errato con il buffer del frame, o quando un oggetto non viene nemmeno visualizzato in quanto i pixel vengono rimossi prima ancora di raggiungere il buffer frame.

 [Tabella oggetti](graphics-object-table.md) La tabella **oggetti grafici viene utilizzata** per esaminare le proprietà e il contenuto di risorse e oggetti Direct3D specifici in uso per l'evento attualmente selezionato. La tabella degli oggetti può aiutare a determinare il contesto dei dispositivi grafici attivi durante un evento nonché a esaminare i contenuti di risorse grafiche come i buffer costanti, i buffer vertici e le trame.

 [Debugger HLSL](hlsl-shader-debugger.md) Per esaminare il comportamento del codice shader per la fase della pipeline grafica e dell'evento attualmente selezionato, usare il **debugger HLSL** per esaminare il codice, esaminare il contenuto delle variabili ed eseguire altre attività di debug tipiche. È anche possibile usare il debugger HLSL per esaminare il codice del compute shader, indipendentemente dal fatto che i risultati vengano ulteriormente elaborati dalla pipeline grafica o siano stati appena letti dall'app.

 [Strumento di acquisizione da riga di comando](command-line-capture-tool.md) Usare lo strumento di acquisizione da riga di comando per acquisire e riprodurre rapidamente le informazioni grafiche senza Visual Studio o a livello di codice. In particolare, è possibile usare lo strumento di acquisizione da riga di comando per l'automazione o in un ambiente di test.

 [Esempi](graphics-diagnostics-examples.md) Alcuni esempi illustrano come usare gli strumenti Diagnostica della grafica per diagnosticare diversi tipi di problemi di rendering.

## <a name="related-sections"></a>Sezioni correlate

| Titolo | Descrizione |
| - | - |
| [Presentazione delle funzionalità del debugger](../debugger-feature-tour.md) | Introduce le funzionalità di debug in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Grafica e giochi DirectX](/windows/win32/directx) | Include articoli che illustrano le tecnologie grafiche DirectX. |
| [Supporto di DirectX 12 in Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | Informazioni sul supporto di DirectX 12 in Visual Studio |
