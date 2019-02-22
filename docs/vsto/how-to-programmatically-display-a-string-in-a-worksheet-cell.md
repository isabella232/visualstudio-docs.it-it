---
title: 'Procedura: A livello di programmazione visualizzare una stringa in una cella di foglio di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d391022e9ce86b2866d941d8c0b56e2e35e3776
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629443"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Procedura: A livello di programmazione visualizzare una stringa in una cella di foglio di lavoro
  In questo esempio viene illustrato come visualizzare il testo in una cella a livello di codice. Per visualizzare il testo nella cella, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Questo esempio Usa un' <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `message`. Il controllo deve essere aggiunto a una personalizzazione a livello di documento in fase di progettazione. Il codice seguente deve essere inserito in una classe foglio, non nel `ThisWorkbook` classe.

### <a name="to-display-text-in-a-namedrange-control"></a>Per visualizzare il testo in un controllo NamedRange

1.  Impostare il valore della <xref:Microsoft.Office.Tools.Excel.NamedRange> il controllo a **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Usare un intervallo di Excel nativo
 Il codice seguente crea un nuovo intervallo a livello di codice e quindi assegna un valore.

### <a name="to-display-text-in-an-excel-range"></a>Per visualizzare il testo in un intervallo di Excel

1.  Recuperare l'intervallo in corrispondenza della cella **A1** sul `Sheet1` e impostare il valore **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Raccogliere i dati di utilizzo di un modulo di Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Risolvere i problemi di soluzioni Office](../vsto/troubleshooting-office-solutions.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
