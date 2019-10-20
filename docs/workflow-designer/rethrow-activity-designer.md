---
title: ActivityDesigner Progettazione flussi di lavoro-Rethrow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d015ad500537a17cfc2c48c8076df43a38534ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650010"
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow

L'ActivityDesigner **Rethrow** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>Attività Rethrow

L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Usare l'ActivityDesigner Rethrow

Accedere all'ActivityDesigner **Rethrow** nella categoria **Gestione errori** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **Rethrow** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Se si elimina l'ActivityDesigner, viene creata un'attività <xref:System.Activities.Statements.Rethrow> con un valore **DisplayName** predefinito Throw. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **Rethrow** oppure nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà di Rethrow

Nella tabella seguente vengono illustrate le proprietà <xref:System.Activities.Statements.Rethrow> e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione:

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)