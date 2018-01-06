---
title: 'Procedura: a livello di programmazione applicare stili agli intervalli nelle cartelle di lavoro | Documenti Microsoft'
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
- ranges, styles
- styles, workbook ranges
- workbooks, styles
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f2700b7a8a2a07c77bfbd6961443fdf57cd3cc07
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Procedura: Applicare stili agli intervalli nei fogli di lavoro a livello di codice
  È possibile applicare stili denominati alle aree nelle cartelle di lavoro. Excel fornisce alcuni stili predefiniti:  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 La finestra di dialogo **Formato celle** mostra tutte le opzioni che è possibile usare per formattare le celle e ognuna di queste opzioni è disponibile dal codice. Per visualizzare questa finestra di dialogo in Excel, scegliere **Celle** dal menu **Formato** .  
  
### <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Per applicare uno stile a un intervallo denominato in una personalizzazione a livello di documento  
  
1.  Creare un nuovo stile e impostare i relativi attributi.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]  
  
2.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>, assegnargli un testo e quindi applicare il nuovo stile. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]  
  
### <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Per cancellare uno stile da un intervallo denominato in una personalizzazione a livello di documento  
  
1.  Applicare lo stile Normale all'intervallo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]  
  
### <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Per applicare uno stile a un intervallo denominato in un componente aggiuntivo VSTO  
  
1.  Creare un nuovo stile e impostare i relativi attributi.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]  
  
2.  Creare un oggetto <xref:Microsoft.Office.Interop.Excel.Range>, assegnargli un testo e quindi applicare il nuovo stile.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]  
  
### <a name="to-clear-a-style-from-a-named-range-in-an-vsto-add-in"></a>Per cancellare uno stile da un intervallo denominato in un componente aggiuntivo VSTO  
  
1.  Applicare lo stile Normale all'intervallo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  