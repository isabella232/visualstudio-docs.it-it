---
title: 'Procedura: A livello di codice eliminare fogli di lavoro dalle cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a70e6b7c8126b2e9d2fc3274d5ecf905dce960d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644510"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Procedura: A livello di codice eliminare fogli di lavoro dalle cartelle di lavoro
  È possibile eliminare qualsiasi foglio di lavoro da una cartella di lavoro. Per eliminare un foglio di lavoro, usare l'elemento host del foglio di lavoro o accedere al foglio di lavoro tramite la raccolta Sheets della cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host foglio di lavoro
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per eliminarlo usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento direttamente all'elemento host del foglio di lavoro.

> [!IMPORTANT]
>  Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:
>
> - Cartella di lavoro di Excel 2013
> - Modello di Excel 2013
> - Cartella di lavoro di Excel 2010
> - Modello di Excel 2010
>
>   Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento per la **Interop** assembly, quindi è necessario usare le classi da tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per altre informazioni, vedere [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Per eliminare un foglio di lavoro mediante un elemento host del foglio di lavoro

1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> di `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta Sheets della cartella di lavoro di Excel
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:

- Se si intende eliminare un foglio di lavoro in un componente aggiuntivo VSTO.

- Se il foglio di lavoro che si vuole eliminare è stato creato in fase di esecuzione in una personalizzazione a livello di documento.

  Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento alla pagina tramite il numero di indice il **fogli** raccolta. Per questo codice si presume che sia già stato creato un nuovo foglio di lavoro a livello di codice.

> [!IMPORTANT]
>  Se si desidera eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento per la **Interop** assembly, quindi è necessario usare le classi da tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per altre informazioni, vedere [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Per eliminare un foglio di lavoro mediante la raccolta Sheets della cartella di lavoro di Excel

1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Procedura: A livello di programmazione spostare fogli di lavoro all'interno di cartelle di lavoro](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Procedura: A livello di codice selezionare fogli di lavoro](../vsto/how-to-programmatically-select-worksheets.md)
- [Procedura: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Elemento host Worksheet](../vsto/worksheet-host-item.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
