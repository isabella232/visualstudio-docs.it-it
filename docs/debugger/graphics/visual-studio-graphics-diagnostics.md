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
ms.openlocfilehash: cbc3edfabe041804a632b919eff4e565be9cc5e3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703032"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostica della grafica di Visual Studio
Visual Studio*diagnostica della grafica* è un set di strumenti per la registrazione e quindi eseguire l'analisi dei problemi di prestazioni e di rendering nelle App Direct3D. Può essere usato su app eseguite localmente in un computer Windows, in un emulatore di dispositivo Windows oppure in un computer o un dispositivo remoto.

 Il flusso di lavoro di Diagnostica grafica inizia con l'acquisizione di informazioni sul modo in cui l'app usa Direct3D durante l'esecuzione, in modo che il comportamento possa essere analizzato immediatamente, condiviso o salvato per un momento successivo. Sessioni di acquisizione possono essere avviate e controllate manualmente da Visual Studio o con lo strumento di acquisizione da riga di comando **dxcap.exe**. Sessioni di acquisizione possono anche essere avviate e controllate a livello di programmazione tramite le API di acquisizione di diagnostica della grafica.

 Dopo la registrazione di una sessione di acquisizione, è possibile riprodurne il contenuto in qualsiasi momento con *Analizzatore grafica* di Visual Studio, ricreando i frame acquisiti mediante le stesse risorse e gli stessi comandi di rendering usati dall'app. Quindi, usando gli strumenti forniti nella finestra analizzatore grafica, uno qualsiasi dei frame acquisiti possono essere analizzato in dettaglio. Questi strumenti consentono di esaminare qualsiasi chiamata alle API Direct3D, risorsa, oggetto di stato della pipeline, fase della pipeline o anche la cronologia completa di qualsiasi pixel in un frame acquisito. Usando questi strumenti insieme si può esplorare un problema di rendering in modo intuitivo, a partire dal modo in cui si manifesta in un frame acquisito ed eseguendo il drill-down alla causa radice nel codice sorgente dell'app, negli shader o nelle risorse grafiche.

 Per diagnosticare i problemi di prestazioni, è possibile analizzare un frame acquisito usando lo strumento *Analisi dei frame*. Questo strumento esplora le potenziali ottimizzazioni delle prestazioni modificando automaticamente il modo in cui l'app usa Direct3D ed effettuando un benchmark di tutte le variazioni. In passato questi benchmark e queste modifiche venivano eseguiti manualmente, semplicemente per verificare quali modifiche creassero effettivamente una differenza. Grazie ad Analisi dei frame, è possibile apportare solo modifiche di cui si conosce già il valore.

 Diagnostica grafica aiuta a ottimizzare l'esecuzione e l'aspetto delle app Direct3D con contenuti grafici avanzati.

 Continuare a [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) per altre informazioni sulle funzionalità offerte di Visual Studio Graphics Diagnostics.

## <a name="in-this-section"></a>In questa sezione
 [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) introduce il flusso di lavoro di diagnostica della grafica e strumenti.

 [Introduzione a](getting-started-with-visual-studio-graphics-diagnostics.md) In questa sezione si apprenderà come installare diagnostica della grafica di Visual Studio e come iniziare a usare diagnostica della grafica con l'app Direct3D.

 [Acquisizione di informazioni grafiche](capturing-graphics-information.md) per usare diagnostica della grafica per esaminare un problema di rendering nell'app, è necessario prima registrare informazioni su come l'app Usa DirectX. Durante la sessione di registrazione, nel corso della normale esecuzione dell'app, *acquisire* (ossia selezionare) i frame che interessano. Le acquisizioni contengono informazioni dettagliate sulla modalità di rendering dei frame. È possibile salvare le informazioni acquisite come documento di log della grafica da esaminare in un secondo momento o da condividere con gli altri membri del team.

 [Utilizzo GPU](gpu-usage.md) per usare diagnostica della grafica per profilare un'app, usare lo strumento utilizzo GPU. Utilizzo GPU può essere usato insieme ad altri strumenti di profilatura, ad esempio Utilizzo CPU, per correlare le attività della CPU e GPU che potrebbero contribuire a problemi di prestazioni nell'app.

 [Documento Log grafica](graphics-log-document.md) per avviare l'esame di un log di grafica registrato, utilizzare la finestra del documento Log grafica per selezionare un frame acquisito, o anche un pixel specifico, in modo da poter esaminare in dettaglio le *eventi* (che è, le chiamate all'API di DirectX) che ha effetto.

 [Analisi dei frame](graphics-frame-analysis.md) dopo aver selezionato un frame, si usa analisi dei Frame di grafica per esaminare e ottimizzare le prestazioni di rendering.

 [Elenco di eventi](graphics-event-list.md) dopo aver selezionato un frame, usare il **elenco eventi grafici** per esaminarne gli eventi per determinare se sono correlati al problema di rendering.

 [Stato](graphics-state.md) finestra stato consente di comprendere lo stato di grafica che è attivo al momento dell'evento corrente.

 [Fasi della pipeline](graphics-pipeline-stages.md) nella **fasi Pipeline grafica** finestra, si esamina la modalità di elaborazione in ogni fase della pipeline grafica dell'evento attualmente selezionato in modo che sia possibile identificare dove il problema di rendering prima viene visualizzata. L'esame delle fasi della pipeline è particolarmente utile quando un oggetto non viene visualizzato a causa di una trasformazione non corretta o quando una delle fasi produce output non corrispondente a quanto atteso dalla fase successiva.

 [Stack di chiamate eventi](graphics-event-call-stack.md) è usare il **Stack di chiamate eventi di grafica** per esaminare lo stack di chiamate dell'evento attualmente selezionato in modo che possa passare al codice dell'app che è correlato al problema di rendering.

 [Cronologia pixel](graphics-pixel-history.md) usando il **cronologia Pixel grafica** finestra da analizzare come il pixel attualmente selezionato è interessato dagli eventi che lo influenzano, è possibile identificare l'evento o una combinazione di eventi che causano determinati tipi di problemi di rendering. La cronologia del pixel è particolarmente utile quando il rendering di un oggetto viene eseguito in modo errato, perché l'output del pixel shader è a sua volta errato o è combinato in modo errato con il buffer del frame, o quando un oggetto non viene nemmeno visualizzato in quanto i pixel vengono rimossi prima ancora di raggiungere il buffer frame.

 [Oggetto tabella](graphics-object-table.md) è usare il **tabella oggetti grafici** per esaminare le proprietà e il contenuto di oggetti specifici Direct3D e risorse che sono attivi per l'evento attualmente selezionato. La tabella degli oggetti può aiutare a determinare il contesto dei dispositivi grafici attivi durante un evento nonché a esaminare i contenuti di risorse grafiche come i buffer costanti, i buffer vertici e le trame.

 [Debugger HLSL](hlsl-shader-debugger.md) per esaminare il codice dello shader per l'evento attualmente selezionato e la grafica fase della pipeline comportamento, usano i **Debugger HLSL** per avanzare nel codice, esaminare il contenuto delle variabili ed eseguire altro attività di debug comuni. È anche possibile usare il debugger HLSL per esaminare il codice del compute shader, indipendentemente dal fatto che i risultati vengano ulteriormente elaborati dalla pipeline grafica o siano stati appena letti dall'app.

 [Strumento di acquisizione da riga di comando](command-line-capture-tool.md) usare lo strumento di acquisizione da riga di comando per acquisire e riprodurre le informazioni grafiche senza usare Visual Studio o l'acquisizione a livello di codice rapidamente. In particolare, è possibile usare lo strumento di acquisizione da riga di comando per l'automazione o in un ambiente di test.

 [Esempi](graphics-diagnostics-examples.md) vari esempi mostrano come usare insieme gli strumenti di diagnostica della grafica per diagnosticare diversi tipi di problemi di rendering.

## <a name="related-sections"></a>Sezioni correlate

| Titolo | Description |
| - | - |
| [Tour delle funzionalità del debugger](/visualstudio/debugger/debugger-feature-tour) | Introduce le funzionalità di debug in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Grafica e giochi DirectX](http://go.microsoft.com/fwlink/?LinkId=256498) | Include articoli che illustrano le tecnologie grafiche DirectX. |
