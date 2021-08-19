---
title: 'Procedura: Chiudere cartelle di lavoro a livello di codice'
description: Informazioni su come chiudere la cartella di lavoro attiva o specificare una cartella di lavoro da chiudere a livello di codice.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 21b789a2a722e78d0a89f7db9b1eaeaf28d9db58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099893"
---
# <a name="how-to-programmatically-close-workbooks"></a>Procedura: Chiudere cartelle di lavoro a livello di codice
  È possibile chiudere la cartella di lavoro attiva o specificare una cartella di lavoro da chiudere.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Chiudere la cartella di lavoro attiva
 Esistono due procedure per chiudere la cartella di lavoro attiva: una per le personalizzazioni a livello di documento e una per i componenti aggiuntivi VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Per chiudere la cartella di lavoro attiva in una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> per chiudere la cartella di lavoro associata alla personalizzazione. Per usare l'esempio di codice seguente, eseguirlo nella classe `Sheet1` in un progetto a livello di documento per Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Per chiudere la cartella di lavoro attiva in un componente aggiuntivo VSTO

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> per chiudere la cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Chiudere una cartella di lavoro specificata in base al nome
 Il modo in cui viene chiusa una cartella di lavoro specificata in base al nome è identico per i componenti aggiuntivi VSTO e per le personalizzazioni a livello di documento.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Per chiudere una cartella di lavoro attiva specificata in base al nome

1. Specificare il nome della cartella di lavoro come argomento per la raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> . L'esempio di codice seguente presuppone l'apertura in Excel di una cartella di lavoro il cui nome è **NewWorkbook** .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: Salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: Aprire cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-workbooks.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
