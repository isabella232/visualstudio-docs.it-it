---
title: Progettazione flussi di lavoro - Rigenera ActivityDesigner
description: Informazioni sull'attività Rethrow e su come usare l'ActivityDesigner di Rethrow per creare e configurare un'attività Rethrow.
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
ms.openlocfilehash: 5508555d2e4347a96e1eaf7319270cf3f95f3177
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963633"
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow

**L'ActivityDesigner Rethrow** viene usato per creare e configurare <xref:System.Activities.Statements.Rethrow> un'attività.

## <a name="the-rethrow-activity"></a>Attività Rethrow

L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Usare l'ActivityDesigner ReThrow

Accedere **all'ActivityDesigner di Rigenera** nella **categoria Gestione** errori della Casella degli **strumenti**. L'ActivityDesigner **Di rigenerazione** può  essere trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere posizionate attività, ad esempio all'interno di <xref:System.Activities.Statements.Sequence> un oggetto . L'eliminazione dell'ActivityDesigner crea <xref:System.Activities.Statements.Rethrow> un'attività con **displayName predefinito** di Throw. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Rethrow** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà Rethrow

La tabella seguente illustra le proprietà e descrive come <xref:System.Activities.Statements.Rethrow> vengono usate nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Gettare](../workflow-designer/throw-activity-designer.md)
- [Trycatch](../workflow-designer/trycatch-activity-designer.md)
