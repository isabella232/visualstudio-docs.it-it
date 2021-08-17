---
title: 'Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice'
description: Informazioni su come usare Visual Studio per fare riferimento a livello di codice al contenuto di un controllo NamedRange o di un oggetto intervallo Excel nativo in un foglio Microsoft Excel dati.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: be0052005ecc7af763aa1f4f934ef529afa4d4c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032771"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice
  Si usa un processo simile per fare riferimento al contenuto di un controllo o di un oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel intervallo nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Nell'esempio seguente viene aggiunto un oggetto a un foglio di lavoro e quindi <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto testo alla cella nell'intervallo.

### <a name="to-refer-to-a-namedrange-control"></a>Per fare riferimento a un controllo NamedRange

1. Assegnare una stringa <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> alla proprietà del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> . Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet46":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet46":::

## <a name="use-native-excel-ranges"></a>Usare intervalli Excel nativi
 L'esempio seguente aggiunge un intervallo Excel nativo a un foglio di lavoro e quindi aggiunge testo alla cella dell'intervallo.

### <a name="to-refer-to-a-native-range-object"></a>Per fare riferimento a un oggetto intervallo nativo

1. Assegnare una stringa alla <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> proprietà dell'intervallo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet47":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet47":::

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Riempire automaticamente gli intervalli con dati che cambiano in modo incrementale](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Procedura: Cercare testo negli intervalli di fogli di lavoro a livello di codice](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
