---
title: 'Procedura: Aggiungere ed eliminare commenti del foglio di lavoro a livello di codice'
description: Informazioni su come aggiungere ed eliminare commenti a livello di codice in Microsoft Office Excel di lavoro. È possibile aggiungere commenti solo a singole celle, non a intervalli di più celle.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 04259cdb6f21254dba6c7769347403fbb6410f26
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148155"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Procedura: Aggiungere ed eliminare commenti del foglio di lavoro a livello di codice
  È possibile aggiungere ed eliminare commenti a livello di codice nei fogli di lavoro di Microsoft Office Excel. I commenti possono essere aggiunti solo a singole celle, non a intervalli con più celle.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Aggiungere ed eliminare un commento in un progetto a livello di documento
 Gli esempi seguenti presuppongono la presenza di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a cella singola denominato `dateComment` in un foglio di lavoro denominato `Sheet1`.

### <a name="to-add-a-new-comment-to-a-named-range"></a>Per aggiungere un nuovo commento a un intervallo denominato

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e fornire il testo del commento. Questo codice deve essere inserito nella classe `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet30":::

#### <a name="to-delete-a-comment-from-a-named-range"></a>Per eliminare un commento da un intervallo denominato

1. Verificare l'esistenza di un commento nell'intervallo ed eliminarlo. Questo codice deve essere inserito nella classe `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet29":::

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Aggiungere ed eliminare un commento in un VSTO progetto di componente aggiuntivo
 Gli esempi seguenti presuppongono la presenza di un oggetto <xref:Microsoft.Office.Interop.Excel.Range> a cella singola denominato `dateComment` nel foglio di lavoro attivo.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Per aggiungere un nuovo commento a un intervallo di Excel

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Range> e fornire il testo del commento.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet20":::

### <a name="to-delete-a-comment-from-an-excel-range"></a>Per eliminare un commento da un intervallo di Excel

1. Verificare l'esistenza di un commento nell'intervallo ed eliminarlo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet19":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Visualizzare commenti del foglio di lavoro a livello di codice](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
