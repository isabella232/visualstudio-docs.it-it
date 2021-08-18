---
title: Progettazione flussi di lavoro - ActivityDesigner Delay
description: Informazioni sulle attività Delay e su come usare l'ActivityDesigner Delay per creare e configurare un'attività Delay.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 71618b2ebbd0abc6f089ad9838942a99d0897e7c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099230"
---
# <a name="delay-activity-designer"></a>ActivityDesigner Delay

L'ActivityDesigner **Delay** viene usato per creare e configurare <xref:System.Activities.Statements.Delay> un'attività.

## <a name="the-delay-activity"></a>Attività Delay

L'attività <xref:System.Activities.Statements.Delay> ritarda l'esecuzione di un flusso di lavoro per una quantità di tempo specificata.

### <a name="use-the-delay-activity-designer"></a>Usare l'ActivityDesigner Delay

L'ActivityDesigner **Delay** è disponibile nella categoria **Primitive** della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

L'ActivityDesigner **Delay** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che in genere vengono inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione dell'ActivityDesigner crea <xref:System.Activities.Statements.Delay> un'attività con <xref:System.Activities.Activity.DisplayName%2A> l'impostazione predefinita Delay. <xref:System.Activities.Activity.DisplayName%2A>L'oggetto può essere modificato nell'intestazione dell'ActivityDesigner **Delay** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-delay-properties"></a>Proprietà Delay

La tabella seguente illustra le <xref:System.Activities.Statements.Delay> proprietà e ne descrive l'uso nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà e alcune possono essere modificate nella Progettazione flussi di lavoro proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Delay>. Il valore predefinito è Delay. Anche se <xref:System.Activities.Activity.DisplayName%2A> il valore non è strettamente necessario, è consigliabile usarne uno.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Vero|Durata del ritardo del flusso di lavoro. Questa proprietà viene impostata nella griglia delle proprietà. Per specificare tale durata, digitare un valore <xref:System.TimeSpan> letterale nel formato 00:00:00 o un'espressione Visual Basic.|

## <a name="see-also"></a>Vedi anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Activity Designer Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)