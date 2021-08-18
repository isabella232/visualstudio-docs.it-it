---
title: PerfTips | Microsoft Docs
description: Informazioni su come usare il debugger Visual Studio PerfTips e le funzionalità Strumenti di diagnostica monitorare e analizzare le prestazioni dell'app durante il debug.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8a31872097d34a6ad7c8ce052c635c9b48770b5c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141597"
---
# <a name="perftips"></a>PerfTips

Il debugger di Visual Studio *PerfTips* e il debugger integrato **Strumenti di diagnostica** consentono di monitorare e analizzare le prestazioni dell'app durante il debug.

Anche se gli strumenti di diagnostica integrati debugger sono un ottimo modo per acquisire consapevolezza dei problemi di prestazioni durante lo sviluppo, il debugger può avere un impatto significativo sulle prestazioni dell'applicazione. Per raccogliere dati sulle prestazioni più accurati, è consigliabile usare gli strumenti Profiler prestazioni come parte aggiuntiva delle indagini sulle prestazioni. Vedere [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>PerfTips

Quando il debugger interrompe l'esecuzione in un punto di interruzione o un'operazione passo a passo, il tempo trascorso tra l'interruzione e il precedente punto di interruzione viene visualizzato come un suggerimento nella finestra dell'editor. Per altre informazioni, vedere [PerfTips, informazioni immediate sulle prestazioni durante il debug in Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Finestra Strumenti di diagnostica

I punti di interruzione e i dati di intervallo associati vengono registrati nella **finestra** Strumenti di diagnostica dati.

La figura seguente mostra la **Strumenti di diagnostica** finestra.

![Screenshot della finestra Strumenti di diagnostica nel debugger Visual Studio, che mostra la sequenza temporale eventi e i grafici per l'utilizzo della memoria e della CPU.](../profiling/media/diagnostictools-update1.png)

- La sequenza temporale **Eventi di interruzione** contrassegnano i punti di interruzione che vengono eseguiti nella sessione di debug. Fare clic su un evento per selezionare l’elenco dei dettagli **Debugger** .

- Il grafico **Utilizzo CPU** mostra la modifica di uso della CPU tra tutti i core di processori nella sessione di debug.

- L’elenco **Eventi** del riquadro dettagli **Debugger** include gli elementi per ogni evento di interruzione.

- La colonna **Durata** di un evento di interruzione visualizza il tempo trascorso tra l'evento e il punto di interruzione precedente.

## <a name="turn-perftips-on-or-off"></a>Attivare o disattivare PerfTips

Per abilitare o disabilitare PerfTips:

1. Scegliere **Opzioni** dal menu **Debug**.

2. Selezionare o deselezionare **Mostra il PerfTip relativo al tempo trascorso durante il debug**.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Attivare o disattivare la finestra Strumenti di diagnostica

Per attivare o disattivare la finestra Strumenti di diagnostica:

1. Scegliere **Opzioni** dal menu **Debug**.

2. Selezionare o deselezionare **Abilita Strumenti di diagnostica durante il debug**.

## <a name="see-also"></a>Vedi anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
