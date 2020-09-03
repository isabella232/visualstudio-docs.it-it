---
title: ActivityDesigner Progettazione flussi di lavoro Throw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650082ab0e4f8576b7028b8011c88bf5d93b2afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593096"
---
# <a name="throw-activity-designer"></a>ActivityDesigner Throw

L'ActivityDesigner **throw** viene usato per creare e configurare un' <xref:System.Activities.Statements.Throw> attività.

## <a name="the-throw-activity"></a>Attività Throw

L'attività <xref:System.Activities.Statements.Throw> genera un'eccezione.

### <a name="using-the-throw-activity-designer"></a>Utilizzo dell'ActivityDesigner Throw

Accedere all'ActivityDesigner **throw** nella categoria **Gestione errori** della **casella degli strumenti**.

È possibile trascinare l'ActivityDesigner **throw** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Viene creata un' <xref:System.Activities.Statements.Throw> attività con il valore **DisplayName** predefinito Throw. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **throw** o nella casella **DisplayName** della griglia delle proprietà. La proprietà <xref:System.Activities.Statements.Throw.Exception%2A> deve essere modificata nella griglia delle proprietà.

### <a name="the-throw-properties"></a>Proprietà di Throw

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Throw> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Throw>. Il valore predefinito è Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Vero|Eccezione da generare. Questa eccezione deve derivare da <xref:System.Exception>. Per specificare l'eccezione, digitare un'espressione Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Activity Designer Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
