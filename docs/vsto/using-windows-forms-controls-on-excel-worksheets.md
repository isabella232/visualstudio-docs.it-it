---
title: Usare Windows Forms controlli nei fogli di lavoro di Excel
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982311"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Usare Windows Forms controlli nei fogli di lavoro di Excel
  È possibile aggiungere controlli Windows Forms alle cartelle di lavoro di Microsoft Office Excel nello stesso modo in cui si aggiungono controlli a Windows Forms. Per informazioni generali sull'uso dei controlli sui documenti, vedere [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Considerazioni sui controlli per Excel
 Esistono alcune considerazioni specifiche di Excel.

### <a name="match-control-size-to-cell-size"></a>Corrisponde alle dimensioni del controllo alle dimensioni della cella
 È possibile impostare il ridimensionamento automatico del controllo quando vengono modificate le dimensioni della cella padre. Per altre informazioni, vedere [procedura: ridimensionare i controlli all'interno di celle del foglio di comando](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Aggiungere componenti condivisi da tutti i fogli di foglio
 I componenti da condividere in tutti i fogli di lavoro, ad esempio un oggetto <xref:System.Data.DataSet>, possono essere aggiunti alla finestra di progettazione delle cartelle di lavoro anziché ai fogli di lavoro. Il componente verrà visualizzato nella barra dei componenti.

### <a name="formula-for-embedding-controls"></a>Formula per l'incorporamento di controlli
 Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

## <a name="see-also"></a>Vedere anche
- [Procedura: ridimensionare i controlli all'interno di celle del foglio di comando](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Procedura: nascondere i controlli nei fogli di foglio durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Procedura dettagliata: modificare la formattazione del foglio di controllo tramite i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Procedura dettagliata: visualizzare il testo in una casella di testo di un foglio di testo utilizzando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Procedura dettagliata: aggiornare un grafico in un foglio di comando utilizzando pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
