---
title: 'Procedura: Copiare fogli di lavoro a livello di codice'
description: Informazioni su come creare una copia di un foglio di lavoro e inserirlo prima o dopo un foglio di lavoro esistente nella cartella di lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7aed53b3579e656d3b00e200b38075859174b8cf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106204"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Procedura: Copiare fogli di lavoro a livello di codice
  È possibile creare una copia di un foglio di lavoro e inserirla prima o dopo un foglio di lavoro esistente nella cartella di lavoro. e non si specifica dove inserire il foglio di lavoro, Excel crea una nuova cartella di lavoro per il nuovo foglio di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Indipendentemente dal fatto che il foglio di lavoro venga copiato a livello di codice o manualmente dall'utente finale, non è presente codice nel nuovo foglio di lavoro e i controlli presenti sul nuovo foglio non funzionano perché il foglio di lavoro appena copiato è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> e non un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>. I controlli Windows Form e i controlli host possono essere aggiunti solo agli elementi host. Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi host e dei controlli host.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Per aggiungere una copia di un foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> per copiare il primo foglio nella cartella di lavoro corrente e inserire la copia dopo il terzo foglio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet16":::

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Per aggiungere una copia di un foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> per copiare il primo foglio nella cartella di lavoro corrente e inserire la copia dopo il terzo foglio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Procedura: Eliminare fogli di lavoro da cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: Selezionare fogli di lavoro a livello di codice](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Accesso globale agli oggetti nei Office progetto](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
