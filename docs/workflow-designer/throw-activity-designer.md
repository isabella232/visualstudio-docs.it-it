---
title: Progettazione flussi di lavoro - ActivityDesigner Throw
description: Informazioni sull'attività Throw e su come usare l'ActivityDesigner Throw per creare e configurare un'attività Throw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 8517ac1cfc2a1a4ba0c3a1c28e17970bea6e1598
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098970"
---
# <a name="throw-activity-designer"></a>ActivityDesigner Throw

L'ActivityDesigner **Throw** viene usato per creare e configurare <xref:System.Activities.Statements.Throw> un'attività.

## <a name="the-throw-activity"></a>Attività Throw

L'attività <xref:System.Activities.Statements.Throw> genera un'eccezione.

### <a name="using-the-throw-activity-designer"></a>Utilizzo dell'ActivityDesigner Throw

Accedere **all'ActivityDesigner Throw** nella **categoria Gestione errori** della Casella degli **strumenti**.

L'ActivityDesigner **Throw** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Verrà creata <xref:System.Activities.Statements.Throw> un'attività con **displayName predefinito** throw. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Throw** o nella **casella DisplayName** della griglia delle proprietà. La proprietà <xref:System.Activities.Statements.Throw.Exception%2A> deve essere modificata nella griglia delle proprietà.

### <a name="the-throw-properties"></a>Proprietà di Throw

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Throw> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Throw>. Il valore predefinito è Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Vero|Eccezione da generare. Questa eccezione deve derivare da <xref:System.Exception>. Per specificare l'eccezione, digitare un'espressione Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Activity Designer Throw](../workflow-designer/throw-activity-designer.md)
- [Trycatch](../workflow-designer/trycatch-activity-designer.md)
