---
title: ActivityDesigner Progettazione flussi di lavoro-Switch &lt; T &gt;
description: Informazioni su come usare l'ActivityDesigner Switch <T> per creare e configurare un'attività Switch <T> nel Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6bdf05878c08b1c175b78ff2205b74c4ea5669b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433934"
---
# <a name="switcht-activity-designer"></a>Activity Designer\<T> Switch

L'attività <xref:System.Activities.Statements.Switch%601> valuta un'espressione specificata e viene eseguita da una raccolta di attività la cui chiave associata corrisponde al valore ottenuto dalla valutazione.

L'ActivityDesigner **Switch<\> T** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Switch%601> attività nel Progettazione flussi di lavoro.

## <a name="the-switchtactivity"></a>Attività Switch \<T>

Un'attività <xref:System.Activities.Statements.Switch%601> contiene un oggetto <xref:System.Activities.Statements.Switch%601.Expression%2A> e un dizionario di <xref:System.Activities.Statements.Switch%601.Cases%2A>. Ogni case del dizionario è costituito da una coppia che contiene una *chiave* e un'attività che funge da *valore* corrispondente. L'attività <xref:System.Activities.Statements.Switch%601> valuta <xref:System.Activities.Statements.Switch%601.Expression%2A> e lo confronta con ogni chiave. Se viene rilevata una corrispondenza, viene eseguita l'attività corrispondente. È consentita una sola corrispondenza in quanto le chiavi del dizionario devono essere univoche in base al tipo di uguaglianza definito dall'operatore di confronto di uguaglianza del dizionario. Se non vengono rilevate corrispondenze, viene eseguita l'attività <xref:System.Activities.Statements.Switch%601.Default%2A>.

## <a name="how-to-use-the-switcht-activity-designer"></a>Come usare l' \<T> ActivityDesigner Switch

Accedere all' **ActivityDesigner \<T> Switch** nella categoria **flusso di controllo** della **casella degli strumenti**. Una volta rilasciata la Progettazione flussi di lavoro, viene visualizzata la finestra di dialogo **Seleziona tipi** per consentire all'utente di specificare il tipo generico *T* utilizzato nell' <xref:System.Activities.Statements.Switch%601> attività. Il valore predefinito è **Int32**. Una volta selezionato il tipo generico *t* , viene aggiunta una finestra di progettazione **Switch<t \>** nella finestra di progettazione del flusso di lavoro.

Di seguito sono riportate le proprietà di **Switch<T \>** designer. Tutte le proprietà possono essere modificate nella griglia delle proprietà. Alcune di esse possono anche essere modificate nell'area della finestra di progettazione.

La tabella seguente mostra le proprietà <xref:System.Activities.Statements.Switch%601> più utili e viene illustrato come usarle nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Switch%601>. Il valore predefinito è switch<Int32 \> . Il valore può essere modificato nella finestra **Proprietà** o direttamente nell'intestazione della finestra di progettazione.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Vero|Specifica l'espressione usata per confrontare le chiavi presenti nella raccolta di case al fine da identificare il case da eseguire.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Se non vengono rilevate corrispondenze, specifica l'attività eseguita. Fare clic sul pulsante **Aggiungi attività** nella finestra di progettazione per aprire la casella **predefinita** in cui è possibile eliminare l'attività.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Specifica i case da valutare. Per aggiungere un case, fare clic sul pulsante **Aggiungi nuovo case** nella parte inferiore di finestra di progettazione **\<T> Switch** . Il pulsante viene modificato in una casella di testo (casella combinata se il tipo generico selezionato quando si aggiunge l'opzione \<T> è String o enum). Dopo aver aggiunto una chiave nella casella **valore case** , l'area del case si espande ed è possibile eliminare un'attività in cui il testo del suggerimento "rilasciare l'attività" per definire la logica di esecuzione del case.|

È possibile aggiungere più case, purché le relative chiavi non siano duplicate. In caso contrario, viene visualizzata una finestra di dialogo di errore in cui viene segnalato che la chiave del case specificata esiste già e che è necessario sceglierne un'altra. Nella finestra di progettazione **Switch \<T>** , una sola area del case può essere in visualizzazione espansa alla volta. Se l'area di un case si trova in modalità compressa, fare clic su di essa per espanderla. Si noti che, per un case compresso, nella finestra di progettazione viene mostrato l'eventuale nome visualizzato dell'attività a destra all'interno del case. In caso contrario, viene visualizzato il pulsante **Aggiungi un'attività** che espande il case facendo clic su di esso e consente di aggiungere un'attività.

Fare clic sulla chiave del case esistente per trasformarla da etichetta in casella di testo in modo che sia possibile modificarla.

È possibile eliminare un case in due modi.

- Selezionare il case ed eliminarlo.

- Selezionare il caso, fare clic con il pulsante destro del mouse per visualizzare il menu di scelta rapida e scegliere **Elimina**.

Si noti che è necessario selezionare il case per eliminarlo. La selezione e la deselezione dell'attività in un case riguardano la sola attività e non il case.

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
