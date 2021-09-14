---
title: 'Procedura: Selezionare fogli di lavoro a livello di codice'
description: Usare Visual Studio per selezionare a livello Microsoft Excel fogli di lavoro con l'elemento host del foglio di lavoro o la raccolta di fogli della cartella Excel lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 82d74fff713741208981278474b295c17975a639
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711323"
---
# <a name="how-to-programmatically-select-worksheets"></a>Procedura: Selezionare fogli di lavoro a livello di codice
  Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> seleziona l'oggetto specificato e questa operazione sposta la selezione dell'utente al nuovo oggetto. Usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> se si vuole applicare lo stato attivo all'oggetto senza modificare la selezione dell'utente.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Se si desidera selezionare un foglio di lavoro esistente in un componente aggiuntivo VSTO o se il foglio di lavoro è stato creato in fase di esecuzione in una personalizzazione a livello di documento, è necessario accedervi tramite la raccolta Excel della cartella di lavoro di Excel; in caso contrario, è possibile accedere direttamente all'elemento <xref:Microsoft.Office.Interop.Excel.Sheets> <xref:Microsoft.Office.Tools.Excel.Worksheet> host.

## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host del foglio di lavoro
 In una personalizzazione a livello di documento aggiungere il codice seguente a *Sheet1.vb* *o Sheet1.cs.*

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Per selezionare il primo foglio di lavoro in una cartella di lavoro usando un elemento host

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> di `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet19":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta sheets della cartella di lavoro Excel lavoro
 Accedere al foglio di lavoro usando la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Per selezionare il primo foglio di lavoro in una cartella di lavoro usando la raccolta Sheets della cartella di lavoro di Excel

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> della Collection <xref:Microsoft.Office.Interop.Excel.Sheets> per selezionare il primo foglio di lavoro della cartella di lavoro attiva.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet20":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Stampare fogli di lavoro a livello di codice](../vsto/how-to-programmatically-print-worksheets.md)
- [Procedura: Eliminare fogli di lavoro da cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: Nascondere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Procedura: Proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Elemento host Foglio di lavoro](../vsto/worksheet-host-item.md)
- [Accesso globale agli oggetti nei Office progetto](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
