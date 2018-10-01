---
title: Utilizzo di dati di metrica codice | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: 954b81dfe738ebd0de1f8aa38cb4975a05333feb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529064"
---
# <a name="working-with-code-metrics-data"></a>Uso di dati di metrica del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funziona con dati di metrica codice](https://docs.microsoft.com/visualstudio/code-quality/working-with-code-metrics-data).  
  
Il **risultati metrica codice** finestra Visualizza i dati generati dall'analisi delle metriche del codice. Per altre informazioni sui valori dei dati di metrica codice, vedere [valori della metrica del codice](../code-quality/code-metrics-values.md).  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Visualizzazione risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtro risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Aggiungendo, rimuovendo e ridisponendo le colonne di dati](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Copia dei dati negli Appunti o Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Creazione di un elemento di lavoro basato sui risultati metrica codice](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 Il **risultati metrica codice** finestra dispone di una barra degli strumenti nella parte superiore e le colonne da visualizzare i risultati calcolati.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Gerarchia**|Il **gerarchia** colonna contiene una visualizzazione albero della gerarchia di codice che è possibile espandere o comprimere per visualizzare il livello di dettaglio desiderato. Le colonne rimanenti mostrano i risultati calcolati. È possibile nascondere o ordinare le colonne di risultati desiderato.|  
|**facilità di gestione**|Il **manutenibilità** colonna contiene un'icona oltre al risultato numerico. Un'icona verde indica un livello elevato di manutenibilità. Un'icona gialla indica un livello moderato di manutenibilità. Un'icona rossa indica una manutenibilità insufficiente e un potenziale punto problematico. Questi indicatori di colore corrispondono alle categorie di livello di gravità che vengono usate dalla regola FxCop AvoidUnmaintainableCode. Questa regola genera un errore se l'indice di manutenibilità è inferiore a 10, un avviso se l'indice è compreso tra 10 e 20 e né un errore né un avviso se l'indice è superiore a 20. L'indice di manutenibilità è una sintesi delle tre metriche: complessità ciclomatica, le righe di codice e le complessità del calcolo. I relativi valori non sono espresse in unità di misura.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> Visualizzazione risultati metrica codice  
 La finestra Risultati metrica codice viene visualizzata automaticamente quando si generano risultati metrica codice. È anche possibile visualizzare la finestra in qualsiasi momento.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Per visualizzare la finestra Risultati metrica codice  
  
-   Nel **Analyze** menu, fare clic su **Windows** e quindi fare clic su **risultati metrica codice**.  
  
     \- oppure -  
  
-   Nel **View** dal menu **Other Windows** e quindi fare clic su **risultati metrica codice**.  
  
     Anche quando non contiene risultati, verrà visualizzata la finestra Risultati metrica codice.  
  
#### <a name="to-view-code-metrics-details"></a>Per visualizzare i dettagli di metrica codice  
  
-   Se sono stati generati risultati metrica codice, espandere l'albero nel **gerarchia** colonna.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> Filtro risultati metrica codice  
 È possibile filtrare i risultati vengono visualizzati nei **risultati metrica codice** finestra usando la barra degli strumenti nella parte superiore. Potrebbe ad esempio, si desidera visualizzare solo i risultati che includono un indice di manutenibilità seguito 65.  
  
 Il **filtro** casella di riepilogo a discesa contiene i nomi delle colonne di risultati. Quando viene definito un filtro, aggiungerlo alla fine dell'elenco con un rientro. L'elenco può contenere gli ultimi dieci filtri che sono stati definiti.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Per filtrare i risultati di metrica codice  
  
1.  Dal **filtro** elencare, selezionare il nome della colonna.  
  
2.  Nelle **Min**, digitare il valore minimo da visualizzare.  
  
3.  Nelle **Max**, digitare il valore massimo deve essere visualizzato.  
  
4.  Scegliere il **Applica filtro** pulsante.  
  
5.  Per visualizzare i dettagli dei risultati, espandere l'albero gerarchico.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Aggiungendo, rimuovendo e ridisponendo le colonne di dati  
 È possibile aggiungere o rimuovere risultati le colonne dai **risultati metrica codice** finestra. Inoltre, è possibile ridisporre le colonne dei risultati in modo che vengano visualizzati nell'ordine in cui si desidera.  
  
#### <a name="to-remove-a-column"></a>Per rimuovere una colonna  
  
1.  Scegliere il **Aggiungi/Rimuovi colonne** pulsante.  
  
     \- oppure -  
  
     Fare doppio clic su un'intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.  
  
2.  Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, deselezionare il casella di controllo per la colonna che si desidera rimuovere e quindi fare clic su **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Per aggiungere una colonna rimossa in precedenza  
  
1.  Scegliere il **Aggiungi/Rimuovi colonne** pulsante.  
  
     \- oppure -  
  
     Fare doppio clic su un'intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.  
  
2.  Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la casella di controllo per la colonna che si desidera aggiungere e quindi fare clic su **OK**.  
  
#### <a name="to-rearrange-columns"></a>Per riordinare le colonne  
  
1.  Scegliere il **Aggiungi/Rimuovi colonne** pulsante.  
  
     \- oppure -  
  
     Fare doppio clic su un'intestazione di colonna e quindi fare clic su **Aggiungi/Rimuovi colonne**.  
  
2.  Nel **Aggiungi/Rimuovi colonne** finestra di dialogo, selezionare la colonna che si desidera spostare e quindi fare clic sulla freccia in su o freccia in giù.  
  
3.  Quando la colonna si trova dove opportuno, fare clic su **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copia dei dati negli Appunti o Excel  
 È possibile selezionare e copiare una riga selezionata di dati di metrica codice negli Appunti come stringa di testo che contiene una riga per il nome e il valore di ogni colonna di dati. È anche possibile fare clic su **aprire l'elenco in Microsoft Excel** per esportare tutti i risultati metrica codice in un foglio di calcolo di Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Creazione di un elemento di lavoro basato sui risultati metrica codice  
 È possibile creare un [!INCLUDE[esprfound](../includes/esprfound-md.md)] elemento di lavoro basato su comporta il **risultati metrica codice** finestra. Quando viene creato l'elemento di lavoro, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] immette automaticamente un titolo nel **Title** dati di metrica del campo e il codice sotto il **cronologia** scheda.  
  
 Per altre informazioni su come creare elementi di lavoro, vedere [creare un elemento di lavoro &#91;reindirizzamento&#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Per creare un elemento di lavoro basato su un risultato  
  
1.  Fare clic sul risultato.  
  
2.  Puntare **Crea elemento di lavoro**, quindi scegliere il tipo di elemento di lavoro da creare (**Bug**, **attività**e così via).  
  
3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.  
  
4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Per creare un bug basato su un risultato  
  
1.  Fare clic sul risultato per selezionarlo.  
  
2.  Scegliere il **Crea elemento di lavoro** pulsante.  
  
3.  Completare il form elemento di lavoro con l'inserimento di tutti i campi obbligatori.  
  
4.  Nel **File** menu, fare clic su **Salva tutto** per salvare l'elemento di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Procedura: Generare dati di metrica codice](../code-quality/how-to-generate-code-metrics-data.md)



