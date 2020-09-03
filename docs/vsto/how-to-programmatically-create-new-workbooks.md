---
title: 'Procedura: creare nuove cartelle di lavoro a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a23f4b089d580d482193d278f22e4990d343097
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545977"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Procedura: creare nuove cartelle di lavoro a livello di codice
  Una cartella di lavoro creata a livello di codice costituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> nativo e non un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> per un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> in un progetto a livello di componente aggiuntivo VSTO. Per altre informazioni, vedere [estensione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)in fase di esecuzione.

## <a name="to-create-a-new-workbook"></a>Per creare una nuova cartella di lavoro

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > È possibile creare una cartella di lavoro basata su un modello diverso da quello predefinito. Passare il modello da usare come parametro al metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Vedere anche
- [Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Utilizzare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: aprire cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-workbooks.md)
- [Procedura: salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
