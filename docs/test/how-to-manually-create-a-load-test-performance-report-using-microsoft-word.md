---
title: Creare un report di prestazioni del test di carico con MS Word
description: Informazioni su come creare manualmente Microsoft Word report di test di carico copiando e incollando i dati dalla visualizzazione Riepilogo Risultati test caricamento e dalla visualizzazione grafici.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 45844370a3a43c0d2a8f580e43bb5fd685f4d45b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122982"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Procedura: Creare manualmente un report di prestazioni di un test di carico usando Microsoft Word

È possibile creare manualmente report di test di carico di Microsoft Word copiando e incollando dati dalla visualizzazione Riepilogo dei risultati test di carico e dalla visualizzazione Grafici. I dati presenti nelle visualizzazioni Riepilogo e Grafici vengono applicati in formato HTML quando vengono copiati.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> È possibile copiare testo normale dalla visualizzazione Tabelle e schermate dalla visualizzazione Dettagli in Microsoft Word, ma non verrà applicato in formato HTML e richiederà formattazione e modifiche aggiuntive.

> [!TIP]
> È possibile generare automaticamente anche report di Microsoft Excel organizzati. Per altre informazioni, vedere [Procedura: Creare report di prestazioni dei test di carico usando Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Copiare i dati della visualizzazione Riepilogo

1. In **Carica Risultati test**, se la visualizzazione riepilogo non è attualmente visualizzata, fare clic **su Riepilogo** sulla barra degli strumenti.

2. Nella visualizzazione Riepilogo fare clic con il pulsante destro del mouse e scegliere **Seleziona tutto**.

3. Nella visualizzazione Riepilogo fare clic con il pulsante destro del mouse e scegliere **Copia**. Il rendering dei dati della visualizzazione Riepilogo verrà eseguito in formato HTML negli Appunti.

4. In Microsoft Word incollare i dati della visualizzazione Riepilogo nella posizione desiderata.

5. A questo punto è possibile modificare, formattare ed eliminare aspetti del contenuto copiato per soddisfare le esigenze riguardanti il rapporto.

## <a name="copy-graph-view-data"></a>Copiare i dati della visualizzazione Grafici

1. In **Carica Risultati test**, se la visualizzazione grafici non è attualmente visualizzata, scegliere **Grafici sulla** barra degli strumenti.

2. (Facoltativo) Ingrandire il grafico specifico che si vuole copiare nel documento di Microsoft Word, come illustrato nella figura seguente. Per altre informazioni, vedere [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Controllo zoom della visualizzazione grafico](../test/media/ltest_zoomcontrol.png)

3. Nel grafico che si vuole copiare nel documento di Microsoft Word fare clic con il pulsante destro del mouse e scegliere **Copia**.

4. In Microsoft Word incollare il grafico e i dati della tabella associati nella posizione desiderata.

    > [!WARNING]
    > Non è possibile copiare il grafico da un desktop remoto e incollarlo in un altro computer, perché verranno copiate solo le informazioni della tabella associata al grafico e non l'immagine del grafico. L'immagine del grafico viene archiviata nella directory temporanea del computer dal quale è stata copiata e il secondo computer non è in grado di dereferenziare tale directory.

## <a name="see-also"></a>Vedi anche

- [Creare report sui risultati dei test di carico per confronti tra test o analisi delle tendenze](../test/compare-load-test-results.md)
- [Procedura: Creare report di prestazioni dei test di carico usando Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
