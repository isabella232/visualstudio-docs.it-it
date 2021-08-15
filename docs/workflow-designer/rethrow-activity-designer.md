---
title: Progettazione flussi di lavoro - ActivityDesigner Rethrow
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
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d758f754a7c8e57b913bd7f1211cc70355f62ca20b93c973cbd3709a60684b00
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243354"
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow

L'ActivityDesigner **Rethrow** viene usato per creare e configurare un'attività. <xref:System.Activities.Statements.Rethrow>

## <a name="the-rethrow-activity"></a>Attività Rethrow

L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Usare l'ActivityDesigner ReThrow

Accedere **all'ActivityDesigner Rethrow** nella **categoria Gestione errori** della Casella degli **strumenti**. L'ActivityDesigner **Rethrow** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione dell'ActivityDesigner crea <xref:System.Activities.Statements.Rethrow> un'attività con **displayName predefinito** throw. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Rethrow** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà di Rethrow

La tabella seguente illustra le <xref:System.Activities.Statements.Rethrow> proprietà e ne descrive l'uso nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Gettare](../workflow-designer/throw-activity-designer.md)
- [Trycatch](../workflow-designer/trycatch-activity-designer.md)
