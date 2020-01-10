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
ms.openlocfilehash: f88d7ebe714fcdc9bf404e1cf58c4c86cf37047d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851459"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Finestra di dialogo associa&#39;a una proprietà dell'attività (legacy)
In questo argomento viene descritto come utilizzare la finestra di dialogo **associa a proprietà di un'attività** nella [!INCLUDE[wfd1](../includes/wfd1-md.md)]legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un tipo di istanza di proprietà di dipendenza può essere associato alla proprietà pubblica di un'altra attività o evento. Per ulteriori informazioni sull'associazione di attività, vedere [utilizzo delle proprietà di dipendenza](https://msdn2.microsoft.com/library/bb675255.aspx).

 È possibile selezionare una proprietà da associare utilizzando la finestra di dialogo **associa a una proprietà dell'attività** . Per aprire questa finestra di dialogo, fare clic sui puntini di sospensione **[...]** alla fine della casella di testo della proprietà selezionata nella finestra **Proprietà** oppure fare clic sull'icona del punto esclamativo blu visualizzato accanto al nome della proprietà nel Visualizzatore proprietà.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **associa alla proprietà di un'attività** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Associa a un membro esistente**|Selezionare un membro che si desidera associare nel riquadro di visualizzazione albero. Il riquadro al di sotto della visualizzazione albero visualizza un messaggio che indica se il membro è un tipo valido per l'associazione o no. Fare clic su **OK** per eseguire il binding al membro valido selezionato.|
|**Associa a un nuovo membro**|Creare un campo o una proprietà per il membro nuovo da associare. Immettere un **nuovo nome di membro**. Scegliere se si desidera creare una proprietà di dipendenza o un campo pubblico selezionando **Crea campo** o **Crea proprietà**. Fare clic su **OK** per creare il nuovo membro.|

## <a name="see-also"></a>Vedere anche
 [Uso](https://msdn2.microsoft.com/library/bb628510.aspx) delle proprietà delle attività [con le proprietà di dipendenza](https://msdn2.microsoft.com/library/bb675255.aspx) [progettazione legacy per Windows Workflow Foundation Guida dell'interfaccia utente](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
