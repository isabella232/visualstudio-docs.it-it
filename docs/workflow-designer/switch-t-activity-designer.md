---
title: Progettazione flussi di lavoro - Passare &lt; a T &gt; ActivityDesigner
description: Informazioni su come usare l'ActivityDesigner Switch <T> per creare e configurare un'attività Switch nel <T> Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1fc06eaaa7bd54ff42a087016dae30e674de4023
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963668"
---
# <a name="switcht-activity-designer"></a>Activity Designer\<T> Switch

L'attività <xref:System.Activities.Statements.Switch%601> valuta un'espressione specificata e viene eseguita da una raccolta di attività la cui chiave associata corrisponde al valore ottenuto dalla valutazione.

Switch **<ActivityDesigner \> T** viene usato per creare e configurare un'attività <xref:System.Activities.Statements.Switch%601> nel Progettazione flussi di lavoro.

## <a name="the-switchtactivity"></a>Attività \<T> Switch

Un'attività <xref:System.Activities.Statements.Switch%601> contiene un oggetto <xref:System.Activities.Statements.Switch%601.Expression%2A> e un dizionario di <xref:System.Activities.Statements.Switch%601.Cases%2A>. Ogni case nel dizionario è costituito da una coppia che contiene una chiave *e* da un'attività che funge da valore *corrispondente.* L'attività <xref:System.Activities.Statements.Switch%601> valuta <xref:System.Activities.Statements.Switch%601.Expression%2A> e lo confronta con ogni chiave. Se viene rilevata una corrispondenza, viene eseguita l'attività corrispondente. È consentita una sola corrispondenza in quanto le chiavi del dizionario devono essere univoche in base al tipo di uguaglianza definito dall'operatore di confronto di uguaglianza del dizionario. Se non vengono rilevate corrispondenze, viene eseguita l'attività <xref:System.Activities.Statements.Switch%601.Default%2A>.

## <a name="how-to-use-the-switcht-activity-designer"></a>Come usare \<T> l'ActivityDesigner Switch

Accedere **\<T> all'ActivityDesigner** Switch nella **categoria Controllo Flow** della Casella degli **strumenti**. Dopo l'eliminazione nel Progettazione flussi di lavoro, viene  visualizzata la finestra di dialogo Seleziona tipi per consentire all'utente di specificare il tipo generico *T* usato <xref:System.Activities.Statements.Switch%601> nell'attività. Il valore predefinito è **Int32**. Dopo aver selezionato il tipo *generico T,* nella finestra di progettazione del flusso di<viene aggiunta una finestra di progettazione **Switch<T. \>**

Di seguito sono riportate le proprietà di **Switch<T \>** Designer. Tutte le proprietà possono essere modificate nella griglia delle proprietà. Alcune di esse possono anche essere modificate nell'area della finestra di progettazione.

La tabella seguente mostra le proprietà <xref:System.Activities.Statements.Switch%601> più utili e viene illustrato come usarle nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Switch%601>. Il valore predefinito è Switch<Int32 \> . Il valore può essere modificato nella **finestra** Proprietà o direttamente nell'intestazione della finestra di progettazione.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Vero|Specifica l'espressione usata per confrontare le chiavi presenti nella raccolta di case al fine da identificare il case da eseguire.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Se non vengono rilevate corrispondenze, specifica l'attività eseguita. Fare clic **sul pulsante Aggiungi un'attività** nella finestra di progettazione per aprire la **casella Predefinita** in cui è possibile eliminare l'attività.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Specifica i case da valutare. Per aggiungere un caso, fare clic **sul pulsante Aggiungi nuovo caso** nella parte inferiore di **Progettazione \<T>** switch. Il pulsante viene modificato in una casella di testo (casella combinata se il tipo generico selezionato durante l'aggiunta dell'opzione è \<T> String o Enum). Dopo aver aggiunto una chiave nella casella **Valore** case, l'area del case si espande e un'attività può essere eliminata in cui il testo del suggerimento "Drop activity here" (Rilascia attività qui) per definire la logica di esecuzione per il case.|

È possibile aggiungere più case, purché le relative chiavi non siano duplicate. In caso contrario, viene visualizzata una finestra di dialogo di errore in cui viene segnalato che la chiave del case specificata esiste già e che è necessario sceglierne un'altra. Nella finestra **di \<T>** progettazione switch è possibile visualizzare una sola area del case alla volta. Se l'area di un case si trova in modalità compressa, fare clic su di essa per espanderla. Si noti che, per un case compresso, nella finestra di progettazione viene mostrato l'eventuale nome visualizzato dell'attività a destra all'interno del case. In caso contrario, viene visualizzato **il pulsante Aggiungi** un'attività che espande il caso se si fa clic su di esso e consente di aggiungere un'attività.

Fare clic sulla chiave del case esistente per trasformarla da etichetta in casella di testo in modo che sia possibile modificarla.

È possibile eliminare un case in due modi.

- Selezionare il case ed eliminarlo.

- Selezionare il case, fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere **Elimina**.

Si noti che è necessario selezionare il case per eliminarlo. La selezione e la deselezione dell'attività in un case riguardano la sola attività e non il case.

## <a name="see-also"></a>Vedi anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
