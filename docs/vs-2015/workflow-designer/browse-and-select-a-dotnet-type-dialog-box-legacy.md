---
title: Finestra di dialogo Cerca e seleziona un tipo .NET (legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668981"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Finestra di dialogo Cerca e seleziona un tipo .NET (legacy)
In questo argomento viene descritto come utilizzare la finestra di dialogo **Cerca e seleziona un tipo .NET** in legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Quando si selezionano proprietà che accettano un .NET Framework tipo in un assembly a cui si fa riferimento, nella finestra **Proprietà** vengono visualizzati i puntini di sospensione **[...]** alla fine della casella di testo della proprietà. Fare clic su **[...]** per aprire la finestra di dialogo **Cerca e seleziona un tipo .NET** . In questa finestra di dialogo, è possibile scegliere un tipo dalla visualizzazione albero degli assembly a cui si fa riferimento. Ad esempio, quando si utilizza l'ActivityDesigner, nella finestra **Proprietà** fare clic sui puntini di sospensione **[...]** della **classe** di base per selezionare un'altra classe di base per un'attività nell'albero degli assembly a cui si fa riferimento.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Cerca e seleziona un tipo .NET** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Nome tipo:**|Nome del tipo correntemente selezionato.|
|**Tipo**|Nel riquadro sinistro viene visualizzata una visualizzazione struttura degli Assembly a cui si fa riferimento. Nel riquadro di destra vengono visualizzati i tipi disponibili per la selezione dall’Assembly cui si fa riferimento selezionato nel riquadro sinistro.|

## <a name="see-also"></a>Vedere anche
 [Utilizzo dell'ActivityDesigner legacy](../workflow-designer/using-the-legacy-activity-designer.md)