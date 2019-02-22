---
title: 'Procedura: A livello di codice aprire cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9d8ab4be67ffd84406869c956f9046a53d6ec79
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611893"
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedura: A livello di codice aprire cartelle di lavoro
  Il <xref:Microsoft.Office.Interop.Excel.Workbooks> insieme in Microsoft Office Excel consente di lavorare con tutte le cartelle di lavoro e di aprire le cartelle di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Per aprire una cartella di lavoro esistente

1.  Usare la <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodo del <xref:Microsoft.Office.Interop.Excel.Workbooks> insieme, passando il percorso alla cartella di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

-   Una cartella di lavoro denominato `YourWorkbook.xls` deve essere presente in una directory denominata `Test` nell'unità C.

## <a name="see-also"></a>Vedere anche
- [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: A livello di codice aprire i file di testo come cartelle di lavoro](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Procedura: A livello di codice crea nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Procedura: A livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: A livello di programmazione chiudere cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
