---
title: 'Procedura: Applicare il colore agli intervalli di Excel a livello Excel codice'
description: Per applicare un colore al testo all'interno di un intervallo di celle, si usa un controllo NamedRange o un oggetto Excel intervallo nativo.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2a2a66db404501048a3eeaffafaf4ab0b51ac813
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634003"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procedura: Applicare il colore agli intervalli di Excel a livello Excel codice
  Per applicare un colore al testo all'interno di un intervallo di celle, usare un controllo o un oggetto Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> intervallo nativo.

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

## <a name="use-native-excel-ranges"></a>Usare intervalli Excel nativi

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Per applicare il colore a un oggetto Excel intervallo nativo

1. Creare un intervallo nella cella A1 e quindi impostare il colore del testo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
