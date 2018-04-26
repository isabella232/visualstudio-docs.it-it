---
title: Finestra di progettazione del flusso di lavoro - individuare e selezionare una finestra di dialogo tipo .NET (Legacy)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 23e311aa8e87fe799bc8ea22a22ffd8e789b3dcd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Finestra di dialogo Cerca e seleziona un tipo .NET (legacy)

Questo argomento viene descritto come utilizzare il **Cerca e seleziona un tipo .NET** nella finestra di dialogo di progettazione del flusso di lavoro Windows legacy. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

 Nel **proprietà** finestra, quando si selezionano le proprietà che accettano un tipo .NET Framework in un assembly di riferimento, i puntini di sospensione **[…]**  visualizzata alla fine della casella di testo della proprietà. Fare clic su di **[…]**  apre il **Cerca e seleziona un tipo .NET** la finestra di dialogo. In questa finestra di dialogo, è possibile scegliere un tipo dalla visualizzazione albero degli assembly a cui si fa riferimento. Ad esempio, quando si utilizza la finestra di progettazione di attività, nel **proprietà** finestra, fare clic sul **di una classe Base** i puntini di sospensione **[…]**  per selezionare un'altra classe di base per un'attività dall'albero assembly a cui fa riferimento.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Cerca e seleziona un tipo .NET** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Nome tipo:**|Nome del tipo correntemente selezionato.|
|**Type**|Nel riquadro sinistro è presente una visualizzazione albero degli Assembly a cui si fa riferimento. Nel riquadro di destra vengono visualizzati i tipi disponibili per la selezione dall’Assembly cui si fa riferimento selezionato nel riquadro sinistro.|

## <a name="see-also"></a>Vedere anche

- [Uso dell'Activity Designer legacy](../workflow-designer/using-the-legacy-activity-designer.md)