---
title: ActivityDesigner Progettazione flussi di lavoro-TryCatch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a7600cdab94499e13592924efabba2fb4c2faf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649798"
---
# <a name="trycatch-activity-designer"></a>ActivityDesigner TryCatch

L'ActivityDesigner **TryCatch** viene usato per creare e configurare un'attività <xref:System.Activities.Statements.TryCatch>.

## <a name="the-trycatch-activity"></a>Attività TryCatch
 L'attività <xref:System.Activities.Statements.TryCatch> contiene un'attività <xref:System.Activities.Statements.TryCatch.Try%2A>, una raccolta di **> \<TException catch** e un'attività <xref:System.Activities.Statements.TryCatch.Finally%2A>. Un <xref:System.Activities.Statements.Catch%601> di tipo **TException** contiene una <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e un <xref:System.Activities.Statements.Catch%601.Action%2A>. che vengono usate insieme per implementare un meccanismo tipico di gestione degli errori basato sulle eccezioni. Un'attività <xref:System.Activities.Statements.TryCatch> tenta di eseguire la relativa attività <xref:System.Activities.Statements.TryCatch.Try%2A>. Se l'attività <xref:System.Activities.Statements.TryCatch.Try%2A> genera un'eccezione, l'attività <xref:System.Activities.Statements.TryCatch> usa la raccolta di **\> Catch < TException** per trovare la corrispondenza con l'eccezione. Se viene rilevata una corrispondenza, viene eseguita la <xref:System.Activities.Statements.Catch%601.Action%2A> del **\<TException catch corrispondente >** , che funge da logica di gestione degli errori per l'eccezione. Se le attività nella sezione di <xref:System.Activities.Statements.TryCatch.Try%2A> o le attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> terminano in modo corretto, l'attività di <xref:System.Activities.Statements.TryCatch> esegue la relativa attività di <xref:System.Activities.Statements.TryCatch.Finally%2A>. Per ulteriori informazioni, vedere [eccezioni del flusso di lavoro di Windows](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Utilizzo dell'ActivityDesigner TryCatch

Accedere all'ActivityDesigner **TryCatch** nella categoria **Gestione errori** della **casella degli strumenti**.

È possibile trascinare l'ActivityDesigner **TryCatch** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TryCatch> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito TryCatch. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **TryCatch** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate sulla superficie dell'ActivityDesigner **TryCatch** .

Fare clic sul pulsante Espandi nell'angolo superiore destro di **TryCatch** designer per visualizzare le caselle **try**, **catch**e **finally** nella visualizzazione espansa. Per aggiungere un catch, fare clic sul pulsante **Aggiungi nuova cattura** in **TryCatch** designer. Il pulsante diventa una casella combinata del tipo. Selezionare un tipo di eccezione e premere INVIO per aggiungere il catch. Dopo l'aggiunta di un **catch**, l'area catch viene espansa e un'attività può essere rilasciata nell'intercetta per definire la logica di esecuzione per l'istruzione catch. Si noti la presenza di una casella di testo a destra dell'area dei catch espansa. Questa casella consente di assegnare un nome alla variabile dell'eccezione. La variabile di eccezione può essere utilizzata solo per le attività all'interno dello stesso **catch**.

**TryCatch** designer non supporta la modifica di **catch**. Se si desidera modificare il tipo di eccezione, è necessario eliminare il **catch** e aggiungerne uno nuovo. Per eliminare un **catch** , selezionarlo ed eliminarlo o selezionando **Elimina** dal menu di scelta rapida a cui si accede facendo clic con il pulsante destro del mouse.

### <a name="the-trycatch-properties"></a>Proprietà di TryCatch

Nella tabella seguente viene illustrato il <xref:System.Activities.Statements.TryCatch>properties e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TryCatch>. Il percorso predefinito è TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|L'attività è stata eseguita per prima quando viene eseguito <xref:System.Activities.Statements.TryCatch>.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Raccolta di elementi **catch** da verificare quando l'attività <xref:System.Activities.Statements.TryCatch.Try%2A> genera un'eccezione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|L'attività da eseguire quando <xref:System.Activities.Statements.TryCatch.Try%2A> e qualsiasi attività necessaria nella raccolta <xref:System.Activities.Statements.TryCatch.Catches%2A> completano l'esecuzione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)