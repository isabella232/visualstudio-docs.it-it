---
title: ActivityDesigner InvokeMethod | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658996"
---
# <a name="invokemethod-activity-designer"></a>ActivityDesigner InvokeMethod
La finestra di progettazione **InvokeMethod** viene utilizzata per creare e configurare un' <xref:System.Activities.Statements.InvokeMethod> attività.

## <a name="the-invokemethod-activity"></a>Attività InvokeMethod
 L'attività <xref:System.Activities.Statements.InvokeMethod> chiama un metodo pubblico di un oggetto o tipo specificato.

### <a name="using-the-invokemethod-activity-designer"></a>Utilizzo dell'ActivityDesigner InvokeMethod
 L'ActivityDesigner **InvokeMethod** è disponibile nella categoria **primitive** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** . [!INCLUDE[wfd2](../includes/wfd2-md.md)] in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **InvokeMethod** dalla **casella degli strumenti** e rilasciarlo nell' [!INCLUDE[wfd2](../includes/wfd2-md.md)] area in cui vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.InvokeMethod> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InvokeMethod. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **InvokeMethod** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-invokemethod-properties"></a>Proprietà di InvokeMethod
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.InvokeMethod> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.InvokeMethod>. Il valore predefinito è InvokeMethod.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Vero|Nome del metodo da richiamare quando viene eseguita l'attività. Il metodo chiamato deve essere dichiarato come **public**. È possibile modificare questa proprietà nell'area della finestra di progettazione. Si tratta di una proprietà obbligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Falso|Raccolta di parametri del metodo chiamato. I parametri devono essere aggiunti alla raccolta nello stesso ordine in cui vengono visualizzati nella firma del metodo. Nella griglia delle proprietà fare clic sul pulsante con i puntini di sospensione nel campo **parametri** per visualizzare la finestra di dialogo **parametri** che consente di impostare questa proprietà. Fare clic sul pulsante **Crea argomento** per aggiungere i parametri.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Falso|Valore restituito dalla chiamata del metodo.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Vero|Specifica se il metodo viene chiamato in modo asincrono. Il valore predefinito è **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Falso|Oggetto contenente il metodo da chiamare. È possibile modificare questa proprietà nell'area della finestra di progettazione.<br /><br /> È necessario impostare <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Falso|Tipo di <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. È possibile modificare questa proprietà nell'area della finestra di progettazione. È necessario impostare questa proprietà solo se il metodo chiamato è statico.|

 Per passare i parametri come parametro **out** C# (ad esempio, `Method1(out myParam)),` è necessario usare **OutArgument** **OutArgument anziché InArgument**

 Non è possibile richiamare metodi con argomenti denominati **TargetObject** o **result** usando l' <xref:System.Activities.Statements.InvokeMethod> attività. Il motivo di ciò è che l'attività <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> in <xref:System.Activities.Activity.CacheMetadata%2A>.

 L'algoritmo per la registrazione dei parametri in <xref:System.Activities.Activity.CacheMetadata%2A> viene mostrato nell'elenco seguente:

1. Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Registrare l'argomento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Scorrere la raccolta <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrare ogni argomento.

   L'eccezione risultante è di tipo <xref:System.Activities.InvalidWorkflowException> e presenta il messaggio seguente: 'InvokeMethod': Esiste già una variabile, RuntimeArgument o DelegateArgument con il nome 'TargetObject'. I nomi devono essere univoci in un ambito di ambiente.

   Questa restrizione non si applica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> perché non sono argomenti del flusso di lavoro e pertanto non sono registrati nella raccolta <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> dell'attività <xref:System.Activities.Statements.InvokeMethod> nel metodo <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Vedere anche
 Le [primitive](../workflow-designer/primitives-activity-designers.md) [assegnano](../workflow-designer/assign-activity-designer.md) il [ritardo](../workflow-designer/delay-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)