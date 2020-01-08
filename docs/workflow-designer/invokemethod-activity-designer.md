---
title: ActivityDesigner Progettazione flussi di lavoro-InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8660cd82f9d671da3b535ac228e8ce62c875dc07
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593200"
---
# <a name="invokemethod-activity-designer"></a>ActivityDesigner InvokeMethod

La finestra di progettazione **InvokeMethod** viene utilizzata per creare e configurare un'attività <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>Attività InvokeMethod

L'attività <xref:System.Activities.Statements.InvokeMethod> chiama un metodo pubblico di un oggetto o tipo specificato.

### <a name="use-the-invokemethod-activity-designer"></a>Usare l'ActivityDesigner InvokeMethod

Accedere all'ActivityDesigner **InvokeMethod** nella categoria **primitive** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **InvokeMethod** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro in cui vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. L'eliminazione dell'ActivityDesigner crea un'attività di <xref:System.Activities.Statements.InvokeMethod> con un <xref:System.Activities.Activity.DisplayName%2A> predefinito di InvokeMethod. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InvokeMethod** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-invokemethod-properties"></a>Proprietà InvokeMethod

Nella tabella seguente vengono illustrate le proprietà <xref:System.Activities.Statements.InvokeMethod> e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate in Progettazione flussi di lavoro area.

|Nome proprietà:|Richiesto|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeMethod>. Il valore predefinito è InvokeMethod.<br /><br /> Sebbene il <xref:System.Activities.Activity.DisplayName%2A> non sia strettamente necessario, è preferibile utilizzarne uno.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nome del metodo da richiamare quando viene eseguita l'attività. Il metodo chiamato deve essere dichiarato come **public**. Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Falso|Raccolta di parametri del metodo chiamato. I parametri devono essere aggiunti alla raccolta nello stesso ordine in cui vengono visualizzati nella firma del metodo. Per visualizzare la finestra di dialogo **parametri** in cui è possibile impostare questa proprietà, fare clic sul pulsante con i puntini di sospensione nel campo **parametri** della griglia delle proprietà. Fare clic sul pulsante **Crea argomento** per aggiungere i parametri.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Falso|Valore restituito dalla chiamata del metodo.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Specifica se il metodo viene chiamato in modo asincrono. Il valore predefinito è **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Falso|Oggetto contenente il metodo da chiamare. È possibile modificare questa proprietà nell'area della finestra di progettazione.<br /><br /> È necessario impostare <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Falso|Tipo di <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. È possibile modificare questa proprietà nell'area della finestra di progettazione. È necessario impostare questa proprietà solo se il metodo chiamato è statico.|

Per passare parametri C# come parametro **out** , ad esempio `Method1(out myParam))`, usare **OutArgument anziché InArgument**

Non è possibile richiamare metodi con argomenti denominati **TargetObject** o **result** usando l'attività <xref:System.Activities.Statements.InvokeMethod>. Il motivo di ciò è che l'attività <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A>.

L'algoritmo per la registrazione dei parametri in <xref:System.Activities.Activity.CacheMetadata%2A> viene mostrato nell'elenco seguente:

1. Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Scorrere la raccolta <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrare ogni argomento.

L'eccezione risultante è di tipo <xref:System.Activities.InvalidWorkflowException> e presenta il messaggio seguente: 'InvokeMethod': Esiste già una variabile, RuntimeArgument o DelegateArgument con il nome 'TargetObject'. I nomi devono essere univoci in un ambito di ambiente.

Questa restrizione non si applica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Non sono argomenti del flusso di lavoro e pertanto non sono registrati nella raccolta <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> dell'attività <xref:System.Activities.Statements.InvokeMethod> nel metodo <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
