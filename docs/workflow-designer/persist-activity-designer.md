---
title: Progettazione flussi di lavoro - Persist ActivityDesigner
description: Informazioni sull'attività Persist e su come usare Persist ActivityDesigner per creare e configurare un'attività Persist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 2f0040b4c816ee55e6db7c59c3a74c53cedb51d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633668"
---
# <a name="persist-activity-designer"></a>ActivityDesigner Persist

Persist  ActivityDesigner viene usato per creare e configurare <xref:System.Activities.Statements.Persist> un'attività.

## <a name="the-persist-activity"></a>Attività Persist

L'attività <xref:System.Activities.Statements.Persist> salva un flusso di lavoro su disco, se possibile. Non è possibile eseguire l'attività <xref:System.Activities.Statements.Persist> in un'area non permanente come, ad esempio, all'interno di un'attività <xref:System.Activities.Statements.TransactionScope>. Se si usa un'attività in un ambito non di persistenza, viene generata <xref:System.Activities.Statements.Persist> un'eccezione in fase di esecuzione.

### <a name="using-the-persist-activity-designer"></a>Utilizzo dell'ActivityDesigner Persist

L'ActivityDesigner persistente è disponibile nella categoria **Runtime** della Casella  degli strumenti **,**  a cui si accede facendo clic sulla scheda Casella degli strumenti .In alternativa, selezionare Casella degli strumenti dal **menu** Visualizza o CTRL+ALT+X. 

**L'ActivityDesigner** persiste può  essere trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere posizionate attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Verrà creata <xref:System.Activities.Statements.Persist> un'attività con un **valore DisplayName predefinito** di Persist. Può <xref:System.Activities.Activity.DisplayName%2A> essere modificato nell'intestazione di **Persist** ActivityDesigner o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-persist-properties"></a>Proprietà di Persist

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Persist> e ne viene descritta la modalità di uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune di esse possono essere modificate Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Persist>. Il valore predefinito è Persist. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|

## <a name="see-also"></a>Vedi anche

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
