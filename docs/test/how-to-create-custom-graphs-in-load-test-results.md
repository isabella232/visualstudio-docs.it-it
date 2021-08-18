---
title: 'Procedura: creare grafici personalizzati nei risultati del test di carico'
description: Informazioni su come progettare grafici che visualizzano informazioni specifiche sui risultati del test di carico durante l'esecuzione di un test di carico o al termine dell'esecuzione.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: a9eb8ef1df65ceb20968ff9887d4750d3b629a84
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139998"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Procedura: Creare grafici personalizzati nei risultati del test di carico

È possibile progettare grafici che visualizzano specifiche informazioni sui risultati dei test di carico. Per progettare un grafico personalizzato, specificare i contatori del test di carico che verranno visualizzati sul grafico.

È possibile eseguire la procedura descritta di seguito durante l'esecuzione di un test di carico o al termine dell'esecuzione.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Per creare un grafico personalizzato dei risultati del test di carico

1. Sulla barra **degli strumenti del test** di carico scegliere Aggiungi nuovo **Graph**.

     \- - oppure -

     **Nell'Analizzatore test di** carico  fare clic con il pulsante destro del mouse nel pannello Contatori o in un grafico e quindi **scegliere Graph**.

     Viene visualizzata la finestra di dialogo **Nome grafico**.

2. In **Nome grafico** digitare un nome per il grafico e scegliere **OK**.

     Il nuovo grafico viene visualizzato nell'**Analizzatore test di carico**. nel pannello del grafico attualmente selezionato, sostituendo il grafico presente precedentemente nel pannello.

3. Personalizzare il nuovo grafico aggiungendo i contatori. Per altre informazioni, [vedere Procedura: Aggiungere ed eliminare contatori nei grafici.](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)

## <a name="see-also"></a>Vedi anche

- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
