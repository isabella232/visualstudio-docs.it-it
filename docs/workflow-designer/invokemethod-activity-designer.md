---
title: Progettazione flussi di lavoro - ActivityDesigner InvokeMethod
description: Informazioni sull'attività InvokeMethod e su come usare l'ActivityDesigner InvokeMethod per creare e configurare un'attività InvokeMethod.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: fa26f068b723c4c67c09017eab5a5a5e7ca210fd
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963354"
---
# <a name="invokemethod-activity-designer"></a>ActivityDesigner InvokeMethod

**La finestra di progettazione InvokeMethod** viene usata per creare e configurare un'attività. <xref:System.Activities.Statements.InvokeMethod>

## <a name="the-invokemethod-activity"></a>Attività InvokeMethod

L'attività <xref:System.Activities.Statements.InvokeMethod> chiama un metodo pubblico di un oggetto o tipo specificato.

### <a name="use-the-invokemethod-activity-designer"></a>Usare l'ActivityDesigner InvokeMethod

Accedere **all'ActivityDesigner InvokeMethod** nella **categoria Primitive** della casella **degli strumenti**. **L'ActivityDesigner InvokeMethod** può essere  trascinato dalla casella degli strumenti e rilasciato nella superficie Progettazione flussi di lavoro in cui vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione dell'ActivityDesigner <xref:System.Activities.Statements.InvokeMethod> crea un'attività con il <xref:System.Activities.Activity.DisplayName%2A> valore predefinito InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione dell'ActivityDesigner **InvokeMethod** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-invokemethod-properties"></a>Proprietà InvokeMethod

La tabella seguente illustra le <xref:System.Activities.Statements.InvokeMethod> proprietà e ne descrive l'uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeMethod>. Il valore predefinito è InvokeMethod.<br /><br /> Anche se <xref:System.Activities.Activity.DisplayName%2A> non è strettamente necessario, è meglio usarne uno.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Vero|Nome del metodo da richiamare quando viene eseguita l'attività. Il metodo chiamato deve essere dichiarato come **pubblico.** Questa proprietà può essere modificata nell'area di progettazione ed è obbligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Falso|Raccolta di parametri del metodo chiamato. I parametri devono essere aggiunti alla raccolta nello stesso ordine in cui vengono visualizzati nella firma del metodo. Per visualizzare la **finestra di** dialogo Parametri in cui è possibile impostare questa proprietà, fare clic sul pulsante con i puntini di sospensione nel **campo** Parametri della griglia delle proprietà. Fare clic **sul pulsante Crea** argomento per aggiungere i parametri.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Falso|Valore restituito dalla chiamata del metodo.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Vero|Specifica se il metodo viene chiamato in modo asincrono. Il valore predefinito è **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Falso|Oggetto contenente il metodo da chiamare. È possibile modificare questa proprietà nell'area della finestra di progettazione.<br /><br /> È necessario impostare <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Falso|Tipo di <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. È possibile modificare questa proprietà nell'area della finestra di progettazione. È necessario impostare questa proprietà solo se il metodo chiamato è statico.|

Per passare i parametri come parametro **out** di C#, ad esempio `Method1(out myParam))` , usare **OutArgument** anziché **InOutArgument**

I metodi con argomenti **denominati TargetObject** o **Result** non possono essere richiamati usando l'attività <xref:System.Activities.Statements.InvokeMethod> . Il motivo di ciò è che l'attività <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A>.

L'algoritmo per la registrazione dei parametri in <xref:System.Activities.Activity.CacheMetadata%2A> viene mostrato nell'elenco seguente:

1. Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Scorrere la raccolta <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrare ogni argomento.

L'eccezione risultante è di tipo <xref:System.Activities.InvalidWorkflowException> e presenta il messaggio seguente: 'InvokeMethod': Esiste già una variabile, RuntimeArgument o DelegateArgument con il nome 'TargetObject'. I nomi devono essere univoci in un ambito di ambiente.

Questa restrizione non si applica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . Non sono argomenti del flusso di lavoro e pertanto non vengono registrati nella <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> raccolta <xref:System.Activities.Statements.InvokeMethod> dell'attività nel metodo <xref:System.Activities.Activity.CacheMetadata%2A> .

## <a name="see-also"></a>Vedi anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Ritardo](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
