---
title: La finestra Risultati metrica codice in Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40e265e5bdc453ec658de16f288e9c184979975f
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44321255"
---
# <a name="using-the-code-metrics-results-window"></a>Uso della finestra Risultati metrica codice

Il **risultati metrica codice** finestra Visualizza i dati generati dall'analisi delle metriche del codice. Per altre informazioni sui valori dei dati di metrica codice, vedere [i valori delle metriche del codice](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Visualizzazione risultati metrica codice

Il **risultati metrica codice** finestra viene visualizzata automaticamente quando si generano risultati metrica codice. È anche possibile visualizzare la finestra in qualsiasi momento.

### <a name="to-display-the-code-metrics-results-window"></a>Per visualizzare la finestra Risultati metrica codice

- Nel **Analyze** menu, scegliere **Windows** > **risultati metrica codice**.

   \- oppure -

- Nel **View** menu, scegliere **Other Windows** > **risultati metrica codice**.

Il **risultati metrica codice** finestra viene visualizzata, anche se non contiene alcun risultato.

### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli di metrica codice

Se sono stati generati risultati metrica codice, espandere l'albero nel **gerarchia** colonna.

## <a name="filtering-code-metrics-results"></a>Filtro risultati metrica codice

È possibile filtrare i risultati vengono visualizzati nei **risultati metrica codice** finestra usando la barra degli strumenti nella parte superiore. Potrebbe ad esempio, si desidera visualizzare solo i risultati che includono un indice di manutenibilità seguito 65.

Il **filtro** casella di riepilogo a discesa contiene i nomi delle colonne di risultati. Quando viene definito un filtro, aggiungerlo alla fine dell'elenco con un rientro. L'elenco può contenere gli ultimi dieci filtri che sono stati definiti.

### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati di metrica codice

1.  Dal **filtro** elencare, selezionare il nome della colonna.

2.  Nelle **Min**, digitare il valore minimo da visualizzare.

3.  Nelle **Max**, digitare il valore massimo deve essere visualizzato.

4.  Scegliere il **Applica filtro** pulsante.

5.  Per visualizzare i dettagli dei risultati, espandere l'albero gerarchico.

## <a name="adding-removing-and-rearranging-data-columns"></a>Aggiungendo, rimuovendo e ridisponendo le colonne di dati

È possibile aggiungere o rimuovere risultati le colonne dai **risultati metrica codice** finestra. Inoltre, è possibile ridisporre le colonne dei risultati in modo che vengano visualizzati nell'ordine in cui si desidera.

### <a name="to-remove-a-column"></a>Per rimuovere una colonna

1. Scegliere il **Aggiungi/Rimuovi colonne** pulsante.

     \- oppure fare doppio clic su un'intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.

1. Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, deselezionare il casella di controllo per la colonna che si desidera rimuovere e quindi fare clic su **OK**.

### <a name="to-add-a-previously-removed-column"></a>Per aggiungere una colonna rimossa in precedenza

1. Scegliere il **Aggiungi/Rimuovi colonne** pulsante.

     \- oppure -

     Fare doppio clic su un'intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.

1. Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la casella di controllo per la colonna che si desidera aggiungere e quindi fare clic su **OK**.

### <a name="to-rearrange-columns"></a>Per riordinare le colonne

1. Scegliere il **Aggiungi/Rimuovi colonne** pulsante.

     \- oppure -

     Fare doppio clic su un'intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.

1. Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la colonna che si desidera spostare e quindi fare clic sulla freccia in su o freccia in giù.

1. Quando la colonna si trova dove opportuno, fare clic su **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Copia dei dati negli Appunti o Excel

È possibile selezionare e copiare una riga selezionata di dati di metrica codice negli Appunti come stringa di testo che contiene una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic su **Apri selezione in Microsoft Excel** per esportare tutti i risultati metrica codice in un foglio di calcolo di Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Creazione di un elemento di lavoro basato sui risultati metrica codice

È possibile creare un [Azure lavagne](/azure/devops/boards/index?view=vsts) genera elemento di lavoro che si basa sul **risultati metrica codice** finestra. Quando viene creato l'elemento di lavoro, Visual Studio avvia automaticamente un titolo nel **Title** dati di metrica del campo e il codice sotto il **cronologia** scheda.

Per altre informazioni sulle aree di Azure gli elementi di lavoro, vedere [elementi di lavoro](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro basato su un risultato

1.  Fare clic sul risultato.

2.  Puntare **Crea elemento di lavoro**, quindi scegliere il tipo di elemento di lavoro da creare (**Bug**, **attività**e così via).

3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.

4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.

### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug basato su un risultato

1.  Fare clic sul risultato per selezionarlo.

2.  Scegliere il **Crea elemento di lavoro** pulsante.

3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.

4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.

## <a name="see-also"></a>Vedere anche

- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
- [Procedura: generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)