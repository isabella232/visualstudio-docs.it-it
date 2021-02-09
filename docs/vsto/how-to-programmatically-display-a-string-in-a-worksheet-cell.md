---
title: 'Procedura: visualizzare una stringa in una cella di un foglio di codice a livello di codice'
description: Informazioni su come è possibile visualizzare una stringa a livello di codice in una cella del foglio di lavoro di Microsoft Excel usando un controllo NamedRange o un oggetto intervallo Excel nativo.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5a89716797ec460b461f79c94df8cea475532a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885560"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Procedura: visualizzare una stringa in una cella di un foglio di codice a livello di codice
  In questo esempio viene illustrato come visualizzare il testo in una cella a livello di codice. Per visualizzare il testo nella cella, utilizzare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 In questo esempio viene usato un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `message` . Il controllo deve essere aggiunto a una personalizzazione a livello di documento in fase di progettazione. Il codice seguente deve essere inserito in una classe foglio, non nella `ThisWorkbook` classe.

### <a name="to-display-text-in-a-namedrange-control"></a>Per visualizzare il testo in un controllo NamedRange

1. Impostare il valore del <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo su **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Usa un intervallo di Excel nativo
 Il codice seguente consente di creare un nuovo intervallo a livello di codice e di assegnarvi un valore.

### <a name="to-display-text-in-an-excel-range"></a>Per visualizzare il testo in un intervallo di Excel

1. Recuperare l'intervallo sulla cella **a1** in `Sheet1` e impostare il valore su **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: raccolta di dati tramite Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Risolvere i problemi relativi alle soluzioni Office](../vsto/troubleshooting-office-solutions.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
