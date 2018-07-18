---
title: Finestra di progettazione del flusso di lavoro - commutatore<T> ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afa5932ebfaea1e0a7f61997c26e95226ed51b1d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758016"
---
# <a name="switcht-activity-designer"></a>Commutatore\<T > ActivityDesigner

L'attività <xref:System.Activities.Statements.Switch%601> valuta un'espressione specificata e viene eseguita da una raccolta di attività la cui chiave associata corrisponde al valore ottenuto dalla valutazione.

Il **Switch < T\>**  ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Switch%601> attività nella finestra di progettazione del flusso di lavoro.

## <a name="the-switchtactivity"></a>Il commutatore\<T > attività

Un'attività <xref:System.Activities.Statements.Switch%601> contiene un oggetto <xref:System.Activities.Statements.Switch%601.Expression%2A> e un dizionario di <xref:System.Activities.Statements.Switch%601.Cases%2A>. Ogni caso nel dizionario è costituito da una coppia che contiene un *key* e un'attività che viene usato come relativo valore corrispondente *valore*. L'attività <xref:System.Activities.Statements.Switch%601> valuta <xref:System.Activities.Statements.Switch%601.Expression%2A> e lo confronta con ogni chiave. Se viene rilevata una corrispondenza, viene eseguita l'attività corrispondente. È consentita una sola corrispondenza in quanto le chiavi del dizionario devono essere univoche in base al tipo di uguaglianza definito dall'operatore di confronto di uguaglianza del dizionario. Se non vengono rilevate corrispondenze, viene eseguita l'attività <xref:System.Activities.Statements.Switch%601.Default%2A>.

## <a name="how-to-use-the-switcht-activity-designer"></a>Come usare l'opzione\<T > Activity Designer

Accesso di **commutatore\<T >** ActivityDesigner nel **flusso di controllo** categoria del **casella degli strumenti**. Dopo averlo rilasciato in Progettazione flussi di lavoro, viene visualizzato il **Seleziona tipi** finestra di dialogo per consentire all'utente di specificare il tipo generico *T* utilizzata in <xref:System.Activities.Statements.Switch%601> attività. Il valore predefinito è **Int32**. Una volta il tipo generico *T* è stata selezionata, un **Switch < T\>**  progettazione viene aggiunto nella finestra di progettazione del flusso di lavoro.

Di seguito sono le proprietà del **Switch < T\>**  finestra di progettazione. Tutte le proprietà possono essere modificate nella griglia delle proprietà. Alcune di esse possono anche essere modificate nell'area della finestra di progettazione.

La tabella seguente mostra le proprietà <xref:System.Activities.Statements.Switch%601> più utili e viene illustrato come usarle nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Switch%601>. Il valore predefinito è Switch < Int32\>. Il valore può essere modificato nel **proprietà** finestra o direttamente nell'intestazione della finestra di progettazione.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Specifica l'espressione usata per confrontare le chiavi presenti nella raccolta di case al fine da identificare il case da eseguire.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Se non vengono rilevate corrispondenze, specifica l'attività eseguita. Fare clic sui **aggiungere un'attività** pulsante nella finestra di progettazione per aprire il **predefinito** casella in cui è possibile rilasciare l'attività.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Specifica i case da valutare. Per aggiungere un case, fare clic sul **Aggiungi nuovo case** pulsante in fondo **commutatore\<T >** finestra di progettazione. Il pulsante diventa una casella di testo (casella combinata se il tipo generico selezionato durante l'aggiunta di Switch\<T > è String o Enum). Dopo l'aggiunta di una chiave nel **valore Case** finestra si espande l'area del case ed è possibile rilasciare un'attività in cui il testo di suggerimento "Rilasciare l'attività" per definire la logica di esecuzione per il case.|

È possibile aggiungere più case, purché le relative chiavi non siano duplicate. In caso contrario, viene visualizzata una finestra di dialogo di errore in cui viene segnalato che la chiave del case specificata esiste già e che è necessario sceglierne un'altra. Nel **commutatore\<T >** della finestra di progettazione, può essere solo un area case nella visualizzazione espansa alla volta. Se l'area di un case si trova in modalità compressa, fare clic su di essa per espanderla. Si noti che, per un case compresso, nella finestra di progettazione viene mostrato l'eventuale nome visualizzato dell'attività a destra all'interno del case. In caso contrario, viene illustrato il **aggiungere un'attività** pulsante che si espande il caso se viene selezionata e consente di aggiungere un'attività.

Fare clic sulla chiave del case esistente per trasformarla da etichetta in casella di testo in modo che sia possibile modificarla.

È possibile eliminare un case in due modi.

- Selezionare il case ed eliminarlo.

- Selezionare il pulsante destro del mouse case, per visualizzare il menu di scelta rapida e selezionare **Elimina**.

Si noti che è necessario selezionare il case per eliminarlo. La selezione e la deselezione dell'attività in un case riguardano la sola attività e non il case.

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)