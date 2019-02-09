---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32e595247b147d9a775fcea0299c291d9027aea9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942986"
---
# <a name="invokemethod-activity-designer"></a>ActivityDesigner InvokeMethod

**InvokeMethod** designer viene utilizzato per creare e configurare un <xref:System.Activities.Statements.InvokeMethod> attività.

## <a name="the-invokemethod-activity"></a>L'attività InvokeMethod

L'attività <xref:System.Activities.Statements.InvokeMethod> chiama un metodo pubblico di un oggetto o tipo specificato.

### <a name="use-the-invokemethod-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeMethod

Accesso di **InvokeMethod** ActivityDesigner nel **primitive** categoria del **della casella degli strumenti**. Il **InvokeMethod** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro in cui sin posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. La finestra di progettazione di attività di rilascio crea un <xref:System.Activities.Statements.InvokeMethod> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InvokeMethod** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-invokemethod-properties"></a>Le proprietà di InvokeMethod

La tabella seguente illustra il <xref:System.Activities.Statements.InvokeMethod> proprietà e viene descritto l'utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeMethod>. Il valore predefinito è InvokeMethod.<br /><br /> Sebbene il <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, si consiglia di usarne uno.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nome del metodo da richiamare quando viene eseguita l'attività. Il metodo chiamato deve essere dichiarato come **pubblica**. Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Raccolta di parametri del metodo chiamato. I parametri devono essere aggiunti alla raccolta nello stesso ordine in cui vengono visualizzati nella firma del metodo. Per visualizzare il **parametri** finestra di dialogo in cui è possibile impostare questa proprietà, fare clic sul pulsante con puntini di sospensione il **parametri** campo della griglia delle proprietà. Scegliere il **Crea argomento** pulsante per aggiungere i parametri.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Valore restituito dalla chiamata del metodo.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Specifica se il metodo viene chiamato in modo asincrono. Il valore predefinito è **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Oggetto contenente il metodo da chiamare. È possibile modificare questa proprietà nell'area della finestra di progettazione.<br /><br /> È necessario impostare <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Tipo di <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. È possibile modificare questa proprietà nell'area della finestra di progettazione. È necessario impostare questa proprietà solo se il metodo chiamato è statico.|

Passare i parametri come c# **out** parametro (ad esempio `Method1(out myParam))`, usare **OutArgument** anziché **InOutArgument**

Metodi con gli argomenti chiamati **TargetObject** oppure **risultato** non può essere richiamata usando la <xref:System.Activities.Statements.InvokeMethod> attività. Il motivo di ciò è che l'attività <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A>.

L'algoritmo per la registrazione dei parametri in <xref:System.Activities.Activity.CacheMetadata%2A> viene mostrato nell'elenco seguente:

1.  Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2.  Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3.  Scorrere la raccolta <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrare ogni argomento.

L'eccezione risultante è di tipo <xref:System.Activities.InvalidWorkflowException> con messaggio analogo al seguente: 'InvokeMethod': Una variabile, RuntimeArgument o DelegateArgument già esiste con il nome 'TargetObject'. I nomi devono essere univoci in un ambito di ambiente.

Questa restrizione non si applica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Che non si è gli argomenti del flusso di lavoro e pertanto non sono registrati nel <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> raccolta del <xref:System.Activities.Statements.InvokeMethod> attività nel <xref:System.Activities.Activity.CacheMetadata%2A> (metodo).

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)