---
title: Finestra metrica codice
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126360a5cbc39653405d83362ae150edba401fb8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448687"
---
# <a name="use-the-code-metrics-results-window"></a>Usare la finestra Risultati metrica codice

Nella finestra dei **Risultati della metrica del codice** vengono visualizzati i dati generati dall'analisi della metrica del codice. Per altre informazioni sui valori dei dati della metrica del codice, vedere [valori della metrica](../code-quality/code-metrics-values.md)del codice.

## <a name="display-code-metrics-results"></a>Visualizzare i risultati della metrica del codice

La finestra **Risultati metrica codice** viene visualizzata automaticamente quando si generano risultati della metrica del codice. È anche possibile visualizzare la finestra in qualsiasi momento.

È possibile visualizzare la finestra Risultati metrica codice utilizzando una delle seguenti sequenze di menu:

- Dal menu **analizza** scegliere **Windows** >  risultati della**metrica del codice**.

- Scegliere altri**Risultati della metrica del codice**di **Windows** >  dal menu **Visualizza** .

Viene visualizzata la finestra **Risultati metrica codice** , anche se non contiene alcun risultato.

### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli della metrica del codice

Se sono stati generati risultati della metrica del codice, espandere l'albero nella colonna **gerarchia** .

## <a name="filter-code-metrics-results"></a>Filtrare i risultati della metrica del codice

È possibile filtrare i risultati visualizzati nella finestra **Risultati metrica codice** usando la barra degli strumenti nella parte superiore. Ad esempio, potrebbe essere necessario visualizzare solo i risultati che hanno un indice di gestibilità inferiore a 65.

Nella casella di riepilogo a discesa **filtro** sono contenuti i nomi delle colonne dei risultati. Quando viene definito un filtro, questo viene aggiunto alla fine dell'elenco insieme a un rientro. L'elenco può contenere gli ultimi 10 filtri definiti.

### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati della metrica del codice

1. Selezionare il nome della colonna dall'elenco **filtro** .

2. In **min**Digitare il valore minimo da visualizzare.

3. In **Max**Digitare il valore massimo da visualizzare.

4. Fare clic sul pulsante **Applica filtro** .

5. Per visualizzare i dettagli del risultato, espandere l'albero gerarchia.

## <a name="add-remove-and-rearrange-data-columns"></a>Aggiungere, rimuovere e ridisporre le colonne di dati

È possibile aggiungere o rimuovere colonne di risultati dalla finestra **dei risultati della metrica del codice** . Inoltre, è possibile ridisporre le colonne dei risultati in modo che vengano visualizzate nell'ordine desiderato.

### <a name="add-or-remove-a-column"></a>Aggiungere o rimuovere una colonna

1. Fare clic sul pulsante **Aggiungi/Rimuovi colonne** oppure fare clic con il pulsante destro del mouse su un'intestazione di colonna, quindi scegliere **Aggiungi/Rimuovi colonne**.

1. Nella finestra di dialogo **Aggiungi/Rimuovi colonne** selezionare o deselezionare la casella di controllo relativa alla colonna che si desidera aggiungere o rimuovere, quindi scegliere **OK**.

### <a name="rearrange-columns"></a>Ridisponi colonne

1. Fare clic sul pulsante **Aggiungi/Rimuovi colonne** .

1. Nella finestra di dialogo **Aggiungi/Rimuovi colonne** selezionare la colonna che si desidera spostare e quindi fare clic sulla freccia su o sulla freccia in giù.

1. Quando la colonna viene posizionata nel punto desiderato, scegliere **OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copiare dati negli Appunti o in Excel

È possibile selezionare e copiare una riga selezionata di dati di metrica del codice negli Appunti come una stringa di testo contenente una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic su **Apri selezione in Microsoft Excel** per esportare tutti i risultati della metrica del codice in un foglio di calcolo di Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Creare un elemento di lavoro in base ai risultati della metrica del codice

È possibile creare un elemento di lavoro [Azure Boards](/azure/devops/boards/index?view=vsts) basato sui risultati nella finestra **dei risultati della metrica del codice** . Quando viene creato l'elemento di lavoro, Visual Studio immette automaticamente un titolo nel campo del **titolo** e i dati di metrica del codice nella scheda **cronologia** .

Per altre informazioni sugli elementi di lavoro Azure Boards, vedere [elementi di lavoro](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro basato su un risultato

1. Fare clic con il pulsante destro del mouse sul risultato.

2. Scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare (**bug**, **attività**e così via).

3. Completare il form dell'elemento di lavoro compilando tutti i campi obbligatori.

4. Scegliere **Salva tutto** dal menu **file** per salvare l'elemento di lavoro.

### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug basato su un risultato

1. Fare clic sul risultato per selezionarlo.

2. Fare clic sul pulsante **Crea elemento di lavoro** .

3. Completare il form dell'elemento di lavoro compilando tutti i campi obbligatori.

4. Scegliere **Salva tutto** dal menu **file** per salvare l'elemento di lavoro.

## <a name="see-also"></a>Vedere anche

- [Valori della metrica del codice](../code-quality/code-metrics-values.md)
- [Procedura: generare dati di metrica del codice](../code-quality/how-to-generate-code-metrics-data.md)
