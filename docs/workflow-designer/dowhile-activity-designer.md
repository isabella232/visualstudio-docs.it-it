---
title: Progettazione flussi di lavoro - ActivityDesigner DoWhile
description: Informazioni su come l'attività DoWhile esegue l'attività contenuta nel corpo almeno una volta, fino a quando una condizione specificata non restituisce false.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 13434292f4b053dffae2775e71387e6f6ce4ba110956d4e7b64436b8aae604d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383820"
---
# <a name="dowhile-activity-designer"></a>ActivityDesigner DoWhile

<xref:System.Activities.Statements.DoWhile>L'attività esegue l'attività contenuta in almeno una volta, fino <xref:System.Activities.Statements.DoWhile.Body%2A> a quando una condizione specificata non restituisce **false.** Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, usare l'attività alternativa <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Proprietà di DoWhile in Progettazione flussi di lavoro

La tabella seguente illustra le proprietà di attività più utili e descrive come <xref:System.Activities.Statements.DoWhile> usarle nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Falso|Attività da eseguire mentre la condizione è **true.** Per aggiungere l'attività, rilasciare un'attività dalla casella degli strumenti nella casella <xref:System.Activities.Statements.DoWhile.Body%2A> **Corpo** dell'ActivityDesigner **DoWhile** con il testo del suggerimento "Drop Activity Here".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Vero|Condizione da valutare prima di ogni iterazione del ciclo. Per impostare , digitare un'Visual Basic nella casella <xref:System.Activities.Statements.DoWhile.Condition%2A> **Condizione** dell'ActivityDesigner **DoWhile** o nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [While](../workflow-designer/while-activity-designer.md)
- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)