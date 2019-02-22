---
title: Usare i controlli Windows Form nei fogli di lavoro di Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032ee551ff04590ccdb8744c1274b137dec0b756
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599506"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Usare i controlli Windows Form nei fogli di lavoro di Excel
  È possibile aggiungere controlli Windows Form per le cartelle di lavoro di Microsoft Office Excel allo stesso modo aggiungere controlli a un Windows Form. Per informazioni generali sull'uso dei controlli nei documenti, vedere [controlli Windows Form nella panoramica di documenti Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Considerazioni sui controlli per Excel
 Esistono alcune considerazioni specifiche di Excel.

### <a name="match-control-size-to-cell-size"></a>Dimensione del controllo corrispondono alle dimensioni di cella
 È possibile impostare il ridimensionamento automatico del controllo quando vengono modificate le dimensioni della cella padre. Per altre informazioni, vedere [Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Aggiungere i componenti condivisi da tutti i fogli di lavoro
 I componenti da condividere in tutti i fogli di lavoro, ad esempio un oggetto <xref:System.Data.DataSet>, possono essere aggiunti alla finestra di progettazione delle cartelle di lavoro anziché ai fogli di lavoro. Il componente verrà visualizzato nella barra dei componenti.

### <a name="formula-for-embedding-controls"></a>Formula per l'incorporamento di controlli
 Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

## <a name="see-also"></a>Vedere anche
- [Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Procedura: Nascondere controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Procedura dettagliata: La modifica del foglio di lavoro della formattazione mediante controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Procedura dettagliata: Testo visualizzato in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Procedura dettagliata: Aggiornare un grafico in un foglio di lavoro mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
