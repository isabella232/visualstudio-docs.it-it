---
title: Progettazione flussi di lavoro - ActivityDesigner While
description: Informazioni su come l'attività While esegue l'attività contenuta nel corpo mentre la condizione specificata restituisce true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: f7d5859ae9841eff105b7a18f5f4730d440df94f
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963427"
---
# <a name="while-activity-designer"></a>ActivityDesigner While

<xref:System.Activities.Statements.While>L'attività esegue l'attività contenuta in <xref:System.Activities.Statements.While.Body%2A> mentre l'oggetto <xref:System.Activities.Statements.While.Condition%2A> specificato restituisce **true.** L'attività contenuta potrebbe non essere mai eseguita. Se si desidera eseguirla almeno una volta, usare l'attività <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Proprietà di While in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.While> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.While> nell'intestazione. Il valore predefinito è While. Il valore può essere modificato nella finestra Proprietà o **direttamente** nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.While.Body%2A>|Falso|Contiene l'attività da eseguire mentre <xref:System.Activities.Statements.While.Condition%2A> restituisce **true.**|
|<xref:System.Activities.Statements.While.Condition%2A>|Vero|Contiene Visual Basic'espressione che viene valutata per determinare se l'attività in <xref:System.Activities.Statements.While.Body%2A> deve essere eseguita.|

## <a name="see-also"></a>Vedi anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [Dowhile](../workflow-designer/dowhile-activity-designer.md)
