---
title: Finestra di dialogo associa&#39;a una proprietà dell'attività (legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 451544a84237bc6fa4e069df9dd1e17feccf86f7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301012"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Finestra di dialogo associa&#39;a una proprietà dell'attività (legacy)
In questo argomento viene descritto come usare la finestra di dialogo **Associazione alla proprietà dell'attività** in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un tipo di istanza di proprietà di dipendenza può essere associato alla proprietà pubblica di un'altra attività o evento. Per ulteriori informazioni sull'associazione di attività, vedere [utilizzo delle proprietà di dipendenza](https://go.microsoft.com/fwlink?LinkID=65007).

 Si seleziona una proprietà da associare usando la finestra di dialogo **Associazione alla proprietà dell’attività**. Per aprire questa finestra di dialogo fare clic sui puntini di sospensione **[.]** alla fine della casella di testo della proprietà selezionata nella finestra **Proprietà** oppure fare clic sull'icona del punto esclamativo blu visualizzata accanto al nome della proprietà nel visualizzatore proprietà.

 La tabella seguente descrive gli elementi dell'interfaccia utente (Interfaccia utente) della finestra di dialogo **Associa ad una proprietà dell’attività**.

|Elemento dell'interfaccia utente|description|
|----------------|-----------------|
|**Associa a un membro esistente**|Selezionare un membro che si desidera associare nel riquadro di visualizzazione albero. Il riquadro al di sotto della visualizzazione albero visualizza un messaggio che indica se il membro è un tipo valido per l'associazione o no. Scegliere **OK** per creare un’associazione al membro valido selezionato.|
|**Associa a un nuovo membro**|Creare un campo o una proprietà per il membro nuovo da associare. Immettere un **Nuovo nome membro**. Scegliere se si desidera creare una proprietà di dipendenza o un campo pubblico selezionando **Crea campo** o **Crea proprietà**. Scegliere **OK** per creare il nuovo membro.|

## <a name="see-also"></a>Vedere anche
 [Uso](https://go.microsoft.com/fwlink?LinkID=65013) delle proprietà delle attività [con le proprietà di dipendenza](https://go.microsoft.com/fwlink?LinkID=65007) [progettazione legacy per Windows Workflow Foundation Guida dell'interfaccia utente](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)