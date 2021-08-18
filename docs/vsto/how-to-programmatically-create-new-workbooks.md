---
title: 'Procedura: Creare nuove cartelle di lavoro a livello di codice'
description: Informazioni su come creare una nuova cartella di lavoro di Microsoft Excel a livello di codice usando Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dded73f4af9221b096adc7c0cfda8c70fb91a348
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046592"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Procedura: Creare nuove cartelle di lavoro a livello di codice
  Una cartella di lavoro creata a livello di codice costituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> nativo e non un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Workbook> per un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> in un progetto a livello di componente aggiuntivo VSTO. Per altre informazioni, vedere Estendere documenti di Word Excel cartelle di lavoro [in VSTO componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="to-create-a-new-workbook"></a>Per creare una nuova cartella di lavoro

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet1":::

    > [!NOTE]
    > È possibile creare una cartella di lavoro basata su un modello diverso da quello predefinito. Passare il modello da usare come parametro al metodo <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word Excel cartelle di lavoro VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: Aprire cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-workbooks.md)
- [Procedura: Salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
