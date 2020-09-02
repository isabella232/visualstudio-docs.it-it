---
title: 'Procedura: aprire cartelle di lavoro a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 10a849d8545565e450cd099b32a9e3e8f7f11b56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537904"
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedura: aprire cartelle di lavoro a livello di codice
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Nella raccolta Microsoft Office Excel è possibile utilizzare tutte le cartelle di lavoro aperte e aprire le cartelle di lavoro di.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Per aprire una cartella di lavoro esistente

1. Utilizzare il <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodo della <xref:Microsoft.Office.Interop.Excel.Workbooks> raccolta passando il percorso alla cartella di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Una cartella di lavoro denominata `YourWorkbook.xls` deve esistere in una directory denominata nell' `Test` unità C.

## <a name="see-also"></a>Vedere anche
- [Utilizzare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: aprire file di testo come cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Procedura: creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Procedura: salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
