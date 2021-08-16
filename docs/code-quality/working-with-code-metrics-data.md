---
title: Finestra Metriche codice
ms.date: 12/12/2017
description: Informazioni su come visualizzare, filtrare, ridisporre ed esportare Visual Studio dati di analisi delle metriche del codice. Vedere come creare elementi di lavoro in base ai risultati della metrica del codice.
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d68f8b43e675aa3e07b392ca8e0dfa77232245b0d8e652ee6570cd3869350e5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121405383"
---
# <a name="use-the-code-metrics-results-window"></a>Usare la finestra Risultati metriche codice

Nella **finestra Risultati metriche codice** vengono visualizzati i dati generati dall'analisi delle metriche del codice. Per altre informazioni sui valori dei dati delle metriche del codice, vedere [Valori delle metriche del codice.](../code-quality/code-metrics-values.md)

## <a name="display-code-metrics-results"></a>Visualizzare i risultati delle metriche del codice

La **finestra Risultati metriche codice** viene visualizzata automaticamente quando si generano i risultati delle metriche del codice. È anche possibile visualizzare la finestra in qualsiasi momento.

È possibile visualizzare la finestra Risultati metriche codice usando una delle sequenze di menu seguenti:

- Nel menu **Analizza** scegliere Windows  >  **risultati delle metriche del codice.**

- Scegliere **Altro** dal menu Visualizza **per** Windows  >  **risultati delle metriche del codice.**

Viene **visualizzata la finestra Risultati** metriche codice, anche se non contiene risultati.

### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli delle metriche del codice

Se sono stati generati risultati delle metriche del codice, espandere l'albero nella **colonna Gerarchia** .

## <a name="filter-code-metrics-results"></a>Filtrare i risultati delle metriche del codice

È possibile filtrare i risultati visualizzati nella **finestra** Risultati metriche codice usando la barra degli strumenti nella parte superiore. Ad esempio, potrebbe essere necessario visualizzare solo i risultati con un indice di manutenibilità inferiore a 65.

La **casella** di riepilogo a discesa Filtro contiene i nomi delle colonne dei risultati. Quando un filtro viene definito, viene aggiunto alla fine dell'elenco insieme a un rientro. L'elenco può contenere gli ultimi 10 filtri definiti.

### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati delle metriche del codice

1. **Nell'elenco Filtro** selezionare il nome della colonna.

2. In **Min** digitare il valore minimo da visualizzare.

3. In **Max**(Massimo) digitare il valore massimo da visualizzare.

4. Fare clic **sul pulsante Applica** filtro.

5. Per visualizzare i dettagli del risultato, espandere l'albero della gerarchia.

## <a name="add-remove-and-rearrange-data-columns"></a>Aggiungere, rimuovere e ridisporre le colonne di dati

È possibile aggiungere o rimuovere colonne dei risultati dalla **finestra Risultati metriche** codice. Inoltre, è possibile ridisporre le colonne dei risultati in modo che vengano visualizzate nell'ordine desiderato.

### <a name="add-or-remove-a-column"></a>Aggiungere o rimuovere una colonna

1. Fare clic **sul pulsante Aggiungi/Rimuovi** colonne oppure fare clic con il pulsante destro del mouse su qualsiasi intestazione di colonna e quindi scegliere **Aggiungi/Rimuovi colonne**.

1. Nella finestra **di dialogo Aggiungi/Rimuovi** colonne selezionare o deselezionare la casella di controllo per la colonna da aggiungere o rimuovere e quindi scegliere **OK.**

### <a name="rearrange-columns"></a>Ridisporre le colonne

1. Fare clic **sul pulsante Aggiungi/Rimuovi** colonne.

1. Nella finestra **di dialogo Aggiungi/Rimuovi** colonne selezionare la colonna che si vuole spostare e quindi scegliere la freccia SU o freccia GIÙ.

1. Quando la colonna è posizionata nel punto desiderato, scegliere **OK.**

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copiare dati negli Appunti o Excel

È possibile selezionare e copiare negli Appunti una riga selezionata di dati delle metriche del codice come stringa di testo contenente una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic **su Apri selezione Microsoft Excel** per esportare tutti i risultati delle metriche del codice in un foglio Excel foglio di calcolo.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Creare un elemento di lavoro in base ai risultati della metrica del codice

È possibile creare un [Azure Boards](/azure/devops/boards/index?view=vsts&preserve-view=true) di lavoro basato sui risultati nella **finestra Risultati metrica codice.** Quando viene creato l'elemento di lavoro, Visual Studio immette automaticamente un titolo nel campo **Titolo** e i dati delle metriche del codice nella **scheda** Cronologia.

Per altre informazioni sui Azure Boards di lavoro, vedere [Elementi di lavoro](/azure/devops/boards/work-items/index?view=vsts&preserve-view=true).

### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro in base a un risultato

1. Fare clic con il pulsante destro del mouse sul risultato.

2. Scegliere Crea **elemento di lavoro** e quindi fare clic sul tipo di elemento di lavoro che si vuole creare (**Bug,** **Attività** e così via).

3. Completare il form dell'elemento di lavoro compilando tutti i campi obbligatori.

4. Scegliere **Salva** tutto dal menu File **per** salvare l'elemento di lavoro.

### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug in base a un risultato

1. Fare clic sul risultato per selezionarlo.

2. Fare clic **sul pulsante Crea elemento di** lavoro .

3. Completare il form dell'elemento di lavoro compilando tutti i campi obbligatori.

4. Scegliere **Salva** tutto dal menu File **per** salvare l'elemento di lavoro.

## <a name="see-also"></a>Vedi anche

- [Valori delle metriche del codice](../code-quality/code-metrics-values.md)
- [Procedura: Generare dati delle metriche del codice](../code-quality/how-to-generate-code-metrics-data.md)
