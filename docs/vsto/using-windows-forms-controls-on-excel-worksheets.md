---
title: Usare Windows Form nei fogli Excel lavoro
description: Informazioni su come aggiungere Windows form alle cartelle di lavoro Microsoft Excel nello stesso modo in cui si aggiungono i controlli Windows Form.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 98a48f2c1f67c8758f9d5019e01f711192ab59b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082712"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Usare Windows Form nei fogli Excel lavoro
  È possibile aggiungere Windows form alle cartelle di lavoro Microsoft Office Excel nello stesso modo in cui si aggiungono i controlli Windows Form. Per informazioni generali sull'uso dei controlli nei documenti, vedere [Windows Forms controls on Office documents overview](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Considerazioni sul controllo per Excel
 Esistono alcune considerazioni specifiche per l'Excel.

### <a name="match-control-size-to-cell-size"></a>Adattare le dimensioni del controllo alle dimensioni delle celle
 È possibile impostare il ridimensionamento automatico del controllo quando vengono modificate le dimensioni della cella padre. Per altre informazioni, vedere [Procedura: Ridimensionare i controlli all'interno delle celle del foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Aggiungere componenti condivisi da tutti i fogli di lavoro
 I componenti da condividere in tutti i fogli di lavoro, ad esempio un oggetto <xref:System.Data.DataSet>, possono essere aggiunti alla finestra di progettazione delle cartelle di lavoro anziché ai fogli di lavoro. Il componente verrà visualizzato nella barra dei componenti.

### <a name="formula-for-embedding-controls"></a>Formula per l'incorporamento di controlli
 Quando si seleziona un controllo in Excel, verrà visualizzato **=EMBED("WinForms.Control.Host","")** nella **Barra della formula**. Questo testo è necessario e non deve essere eliminato.

## <a name="see-also"></a>Vedi anche
- [Procedura: Ridimensionare i controlli all'interno delle celle del foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Procedura: Nascondere i controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Procedura dettagliata: Modificare la formattazione del foglio di lavoro usando i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Procedura dettagliata: Visualizzare il testo in una casella di testo in un foglio di lavoro usando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Procedura dettagliata: Aggiornare un grafico in un foglio di lavoro usando i pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
