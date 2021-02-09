---
title: ActivityDesigner Progettazione flussi di lavoro-Rethrow
description: Informazioni sull'attività Rethrow e su come usare l'ActivityDesigner Rethrow per creare e configurare un'attività Rethrow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e3615c73583e8c5c313d23fd5f9aa6d9fcd5ff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847323"
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow

L'ActivityDesigner **Rethrow** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Rethrow> attività.

## <a name="the-rethrow-activity"></a>Attività Rethrow

L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Usare l'ActivityDesigner Rethrow

Accedere all'ActivityDesigner **Rethrow** nella categoria **Gestione errori** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **Rethrow** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.Rethrow> attività con il valore **DisplayName** predefinito Throw. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Rethrow** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà di Rethrow

Nella tabella seguente sono illustrate le <xref:System.Activities.Statements.Rethrow> proprietà e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Generare](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
