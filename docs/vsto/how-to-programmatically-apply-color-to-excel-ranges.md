---
title: 'Procedura: applicare il colore a intervalli di Excel a livello di codice | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 141186d6c37fdbb2023650d9b43dfef57176ddda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procedura: applicare il colore a intervalli di Excel a livello di codice
  Per applicare un colore al testo all'interno di un intervallo di celle, utilizzare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Utilizzo di un controllo NamedRange  
 Questo esempio è per le personalizzazioni a livello di documento.  
  
#### <a name="to-apply-color-to-a-namedrange-control"></a>Per applicare un colore per un controllo NamedRange  
  
1.  Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Impostare il colore del testo di <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="using-native-excel-ranges"></a>Utilizzo di intervalli di Excel nativo  
  
#### <a name="to-apply-color-to-a-native-excel-range-object"></a>Per applicare un colore per un oggetto intervallo di Excel nativo  
  
1.  Creare un intervallo nella cella A1 e quindi impostare il colore del testo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: a livello di programmazione applicare stili agli intervalli nelle cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: fare riferimento a livello di programmazione agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  