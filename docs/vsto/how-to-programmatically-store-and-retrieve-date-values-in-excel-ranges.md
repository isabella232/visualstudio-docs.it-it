---
title: 'Procedura: archiviare e recuperare valori di data in intervalli di Excel a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f1abe0e797a65886f595913f8e6495ec084b7e2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672850"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Procedura: archiviare e recuperare valori di data in intervalli di Excel a livello di codice
  È possibile archiviare e recuperare i valori in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se si archivia un valore di data che cade il o dopo il 1/1/1900 in un intervallo usando gli strumenti di sviluppo per Office in Visual Studio, questo viene archiviato in formato di automazione OLE (OA). È necessario usare il <xref:System.DateTime.FromOADate%2A> metodo per recuperare il valore di date di automazione OLE (OA). Se la data è precedente a 1/1/1900, sono archiviati come una stringa.  
  
> [!NOTE]  
>  Le date di Excel sono diversi dalle date di automazione OLE per i primi due mesi di 1900. Esistono anche differenze se il **sistema data 1904** opzione è selezionata. Gli esempi di codice riportato di seguito non consente di risolvere queste differenze.  
  
## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange  
  
-   Questo esempio è per le personalizzazioni a livello di documento. Il codice seguente deve essere inserito in una classe foglio, non nel `ThisWorkbook` classe.  
  
### <a name="to-store-a-date-value-in-a-named-range"></a>Per archiviare un valore date in un intervallo denominato  
  
1.  Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Impostare la data odierna come valore per `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Per recuperare un valore di data da un intervallo denominato  
  
1.  Recuperare il valore della data da `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="use-native-excel-ranges"></a>Usare gli intervalli di Excel nativi  
  
### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Per archiviare un valore date in un oggetto intervallo di Excel nativo  
  
1.  Creare un <xref:Microsoft.Office.Interop.Excel.Range> che rappresenta una cella **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Impostare la data odierna come valore per `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Per recuperare un valore di data da un oggetto intervallo di Excel nativo  
  
1.  Recuperare il valore della data da `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con intervalli](../vsto/working-with-ranges.md)   
 [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: fare riferimento a livello di programmazione agli intervalli di foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  