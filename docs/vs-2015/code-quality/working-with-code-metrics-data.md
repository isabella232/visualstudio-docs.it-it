---
title: Uso dei dati di metrica del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645699"
---
# <a name="working-with-code-metrics-data"></a>Uso di dati di metrica del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra dei **Risultati della metrica del codice** vengono visualizzati i dati generati dall'analisi della metrica del codice. Per altre informazioni sui valori dei dati della metrica del codice, vedere [valori della metrica](../code-quality/code-metrics-values.md)del codice.

 In questo argomento sono incluse le sezioni seguenti:

- [Finestra Risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Visualizzazione dei risultati della metrica del codice](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtro dei risultati della metrica del codice](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Aggiunta, rimozione e ridisposizione di colonne di dati](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Copia di dati negli Appunti o in Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Creazione di un elemento di lavoro in base ai risultati della metrica del codice](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="code-metrics-results-window"></a><a name="BKMK_CodeMetricsResultsWindow"></a> Finestra Risultati metrica codice
 Nella finestra dei **Risultati della metrica del codice** è presente una barra degli strumenti nella parte superiore e le colonne per visualizzare i risultati calcolati.

|Colonna|Descrizione|
|------------|-----------------|
|**Gerarchia**|La colonna **gerarchia** contiene una visualizzazione struttura ad albero della gerarchia del codice che è possibile espandere o comprimere per visualizzare il livello di dettaglio desiderato. Le colonne rimanenti mostrano i risultati calcolati. È possibile nascondere o disporre le colonne dei risultati nel modo desiderato.|
|**Facilità di gestione**|La colonna di **gestibilità** contiene un'icona oltre al risultato numerico. Un'icona verde indica un grado relativamente elevato di gestibilità. Un'icona gialla indica un grado di gestibilità moderato. Un'icona rossa indica una bassa gestibilità e un potenziale problema. Questi indicatori di colore corrispondono alle categorie di gravità utilizzate dalla regola FxCop AvoidUnmaintainableCode. Questa regola genera un errore se l'indice di gestibilità è inferiore a 10, un avviso se l'indice è compreso tra 10 e 20, né un errore né un avviso se l'indice è maggiore di 20. L'indice di gestibilità è una sintesi di tre metriche: complessità ciclomatica, righe di codice e complessità computazionale. I valori non sono espressi in unità.|

## <a name="displaying-code-metrics-results"></a><a name="BKMK_DisplayingCodeMetricsResults"></a> Visualizzazione dei risultati della metrica del codice
 La finestra Risultati metrica codice viene visualizzata automaticamente quando si generano risultati della metrica del codice. È anche possibile visualizzare la finestra in qualsiasi momento.

#### <a name="to-display-the-code-metrics-results-window"></a>Per visualizzare la finestra dei risultati della metrica del codice

- Scegliere **finestre** dal menu **analizza** e quindi fare clic su **Risultati metrica codice**.

     \- - oppure -

- Scegliere **altre finestre** dal menu **Visualizza** , quindi fare clic su **Risultati metrica codice**.

     La finestra Risultati metrica codice viene visualizzata anche quando non contiene risultati.

#### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli della metrica del codice

- Se sono stati generati risultati della metrica del codice, espandere l'albero nella colonna **gerarchia** .

## <a name="filtering-code-metrics-results"></a><a name="BKMK_FilteringCodeMetricsResults"></a> Filtro dei risultati della metrica del codice
 È possibile filtrare i risultati visualizzati nella finestra **Risultati metrica codice** usando la barra degli strumenti nella parte superiore. Ad esempio, potrebbe essere necessario visualizzare solo i risultati che hanno un indice di gestibilità inferiore a 65.

 Nella casella di riepilogo a discesa **filtro** sono contenuti i nomi delle colonne dei risultati. Quando viene definito un filtro, questo viene aggiunto alla fine dell'elenco insieme a un rientro. L'elenco può contenere gli ultimi dieci filtri definiti.

#### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati della metrica del codice

1. Selezionare il nome della colonna dall'elenco **filtro** .

2. In **min**Digitare il valore minimo da visualizzare.

3. In **Max**Digitare il valore massimo da visualizzare.

4. Fare clic sul pulsante **Applica filtro** .

5. Per visualizzare i dettagli del risultato, espandere l'albero gerarchia.

## <a name="adding-removing-and-rearranging-data-columns"></a><a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Aggiunta, rimozione e ridisposizione di colonne di dati
 È possibile aggiungere o rimuovere colonne di risultati dalla finestra **dei risultati della metrica del codice** . Inoltre, è possibile ridisporre le colonne dei risultati in modo che vengano visualizzate nell'ordine desiderato.

#### <a name="to-remove-a-column"></a>Per rimuovere una colonna

1. Fare clic sul pulsante **Aggiungi/Rimuovi colonne** .

     \- - oppure -

     Fare clic con il pulsante destro del mouse su un'intestazione di colonna e quindi scegliere **Aggiungi/Rimuovi colonne**.

2. Nella finestra di dialogo **Aggiungi/Rimuovi colonne** deselezionare la casella di controllo relativa alla colonna che si desidera rimuovere e quindi fare clic su **OK**.

#### <a name="to-add-a-previously-removed-column"></a>Per aggiungere una colonna precedentemente rimossa

1. Fare clic sul pulsante **Aggiungi/Rimuovi colonne** .

     \- - oppure -

     Fare clic con il pulsante destro del mouse su un'intestazione di colonna e quindi scegliere **Aggiungi/Rimuovi colonne**.

2. Nella finestra di dialogo **Aggiungi/Rimuovi colonne** selezionare la casella di controllo relativa alla colonna che si desidera aggiungere, quindi fare clic su **OK**.

#### <a name="to-rearrange-columns"></a>Per ridisporre le colonne

1. Fare clic sul pulsante **Aggiungi/Rimuovi colonne** .

     \- - oppure -

     Fare clic con il pulsante destro del mouse su un'intestazione di colonna e quindi scegliere **Aggiungi/Rimuovi colonne**.

2. Nella finestra di dialogo **Aggiungi/Rimuovi colonne** selezionare la colonna che si desidera spostare e quindi fare clic sulla freccia su o sulla freccia in giù.

3. Quando la colonna viene posizionata in corrispondenza della posizione desiderata, fare clic su **OK**.

## <a name="copying-data-to-the-clipboard-or-excel"></a><a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copia di dati negli Appunti o in Excel
 È possibile selezionare e copiare una riga selezionata di dati di metrica del codice negli Appunti come una stringa di testo contenente una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic su **Apri elenco in Microsoft Excel** per esportare tutti i risultati della metrica del codice in un foglio di calcolo di Excel

## <a name="creating-a-work-item-based-on-code-metric-results"></a><a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Creazione di un elemento di lavoro in base ai risultati della metrica del codice
 È possibile creare un [!INCLUDE[esprfound](../includes/esprfound-md.md)] elemento di lavoro basato sui risultati nella finestra **dei risultati della metrica del codice** . Quando viene creato l'elemento di lavoro, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] immette automaticamente un titolo nel campo del **titolo** e i dati di metrica del codice nella scheda **cronologia** .

 Per altre informazioni su come creare elementi di lavoro, vedere [creare un elemento di lavoro &#91;reindirizzato&#93;](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro basato su un risultato

1. Fare clic con il pulsante destro del mouse sul risultato.

2. Scegliere **Crea elemento di lavoro**, quindi fare clic sul tipo di elemento di lavoro che si desidera creare (**bug**, **attività**e così via).

3. Completare il form dell'elemento di lavoro compilando tutti i campi obbligatori.

4. Scegliere **Salva tutto** dal menu **file** per salvare l'elemento di lavoro.

#### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug basato su un risultato

1. Fare clic sul risultato per selezionarlo.

2. Fare clic sul pulsante **Crea elemento di lavoro** .

3. Completare il form dell'elemento di lavoro compilando tutti i campi obbligatori.

4. Scegliere **Salva tutto** dal menu **file** per salvare l'elemento di lavoro.

## <a name="see-also"></a>Vedere anche
 [Misurazione della complessità e della gestibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [procedura: generare dati di metrica del codice](../code-quality/how-to-generate-code-metrics-data.md)
