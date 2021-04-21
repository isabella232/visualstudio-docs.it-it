---
title: 'Procedura: Applicare il colore agli intervalli di Excel a livello di codice'
description: Informazioni su come applicare un colore al testo all'interno di un intervallo di celle, usare un controllo NamedRange o un oggetto intervallo di Excel nativo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 081985dbd4b235fe5dd8d3472d0ab574603abe1b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828319"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procedura: Applicare il colore agli intervalli di Excel a livello di codice
  Per applicare un colore al testo all'interno di un intervallo di celle, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo nativo di Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Questo esempio è per le personalizzazioni a livello di documento.

### <a name="to-apply-color-to-a-namedrange-control"></a>Per applicare il colore a un controllo NamedRange

1. Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella A1.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet65":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet65":::

2. Impostare il colore del testo nel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet66":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet66":::

## <a name="use-native-excel-ranges"></a>Usare intervalli nativi di Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Per applicare il colore a un oggetto intervallo di Excel nativo

1. Creare un intervallo nella cella A1 e quindi impostare il colore del testo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatizzare Excel tramite oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
