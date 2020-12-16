---
title: 'Procedura: elencare i file della cartella di lavoro usati di recente a livello di codice'
description: Informazioni su come è possibile elencare a livello di codice i file della cartella di lavoro di Microsoft Excel usati di recente usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bbcad553ade6234d3a688c8f718a0dd6e6cda509
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525629"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedura: elencare i file della cartella di lavoro usati di recente a livello di codice
  La <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> proprietà restituisce una raccolta che contiene i nomi di tutti i file visualizzati nell'elenco Microsoft Office Excel dei file usati di recente. La lunghezza dell'elenco varia a seconda del numero di file che l'utente ha selezionato per mantenere. È possibile visualizzare i risultati in un intervallo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Per elencare le cartelle di lavoro utilizzate di recente in un oggetto intervallo

1. Scorrere l'elenco dei file recenti e visualizzare i nomi nelle celle relative a un <xref:Microsoft.Office.Interop.Excel.Range> oggetto.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Vedere anche
- [Utilizzare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
