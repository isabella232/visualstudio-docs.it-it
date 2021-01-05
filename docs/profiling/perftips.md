---
title: PerfTips | Microsoft Docs
description: Informazioni su come usare il debugger di Visual Studio PerfTips e Strumenti di diagnostica integrato per monitorare e analizzare le prestazioni dell'app durante il debug.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 481113e9f5e2f5b66aec5f4dad29f581462165ca
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815828"
---
# <a name="perftips"></a>PerfTips

Il debugger di Visual Studio *PerfTips* e il debugger integrato **Strumenti di diagnostica** consentono di monitorare e analizzare le prestazioni dell'app durante il debug.

Anche se gli strumenti di diagnostica integrati debugger sono un ottimo modo per acquisire consapevolezza dei problemi di prestazioni durante lo sviluppo, il debugger può avere un impatto significativo sulle prestazioni dell'applicazione. Per raccogliere dati più accurati sulle prestazioni, è consigliabile usare gli strumenti nel profiler delle prestazioni come parte aggiuntiva delle analisi delle prestazioni. Vedere [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>PerfTips

Quando il debugger interrompe l'esecuzione in un punto di interruzione o un'operazione passo a passo, il tempo trascorso tra l'interruzione e il precedente punto di interruzione viene visualizzato come un suggerimento nella finestra dell'editor. Per altre informazioni, vedere [PerfTips, informazioni immediate sulle prestazioni durante il debug in Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Finestra Strumenti di diagnostica

I punti di interruzione e i dati di intervallo associati vengono registrati nella finestra **strumenti di diagnostica** .

Nella figura seguente viene illustrata la finestra di **strumenti di diagnostica** .

![Screenshot della finestra di Strumenti di diagnostica nel debugger di Visual Studio, che mostra la sequenza temporale degli eventi e i grafici per l'utilizzo della memoria e della CPU.](../profiling/media/diagnostictools-update1.png)

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
