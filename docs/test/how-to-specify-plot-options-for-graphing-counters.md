---
title: Opzioni di tracciato per i contatori dei grafici per i test di carico in Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 00860a262573491a358c0f992577f48fc3480d93
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Procedura: specificare le opzioni del tracciato per i contatori grafici

La finestra di dialogo **Opzioni tracciato** consente di modificare il colore e lo stile della linea di un contatore tracciato in un grafico. È possibile correggere anche l'intervallo a un valore specifico o impostare l'intervallo affinché venga regolato automaticamente in base ai dati campionati.

![Finestra di dialogo Opzioni tracciato](../test/media/ltest_plotoptions.png "LTest_PlotOptions")

## <a name="to-specify-plotting-options-for-graphs"></a>Per specificare le opzioni relative ai tracciati per i grafici

1.  Nell'Analizzatore test di carico scegliere **Grafici** sulla barra degli strumenti del test di carico.

     I risultati del test di carico verranno visualizzati nella visualizzazione Grafici.

2.  Nella Legenda o nel grafico fare clic con il pulsante destro del mouse sulla riga o sulla linea del tracciato corrente del contatore delle prestazioni per il quale si vuole modificare l'opzione del tracciato, quindi selezionare **Opzioni tracciato**.

     Viene visualizzata la finestra di dialogo **Opzioni tracciato**.

3.  Usare l'elenco a discesa **Colore** per selezionare il colore che si vuole usare per il tracciato del contatore delle prestazioni.

4.  Usare l'elenco a discesa **Stile** per selezionare lo stile che si vuole usare per il tracciato del contatore delle prestazioni.

5.  Eseguire una delle operazioni seguenti:

     Selezionare **Regola automaticamente intervallo** (impostazione predefinita)

     \- oppure -

     Deselezionare **Regola automaticamente intervallo** e usare l'elenco a discesa **Intervallo** per specificare l'intervallo che si vuole usare per il tracciato del contatore delle prestazioni.

6.  Scegliere **OK**.

     Il contatore delle prestazioni per il quale sono state modificate le opzioni viene visualizzato nel grafico con le modifiche specificate.

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Procedura: Creare grafici personalizzati](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)