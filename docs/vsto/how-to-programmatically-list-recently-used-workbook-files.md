---
title: 'Procedura: A livello di codice vengono usati i file della cartella di lavoro di elenco'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 954a106b87d0ee941aa9c3a6c9c35579d1cb3d54
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812534"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedura: A livello di codice vengono usati i file della cartella di lavoro di elenco
  Il <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> proprietà restituisce una raccolta che contiene i nomi di tutti i file che vengono visualizzati nell'elenco dei file usati di recente di Microsoft Office Excel. La lunghezza dell'elenco varia a seconda del numero di file selezionato dall'utente da conservare. È possibile visualizzare i risultati in un intervallo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Per le cartelle di lavoro elenco usato di recente in un oggetto range

1. Scorrere l'elenco dei file recenti e i nomi visualizzati nelle celle relative a un <xref:Microsoft.Office.Interop.Excel.Range> oggetto.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Vedere anche
- [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
