---
title: 'Procedura: eliminare fogli di lavoro dalle cartelle di lavoro a livello di codice'
description: Informazioni su come è possibile eliminare a livello di codice un foglio di lavoro in una cartella di lavoro di Microsoft Excel usando l'elemento host del foglio di lavoro, ad esempio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e9d1330c454e0b9b9f5ad4624c18e4ed1055343d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527783"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Procedura: eliminare fogli di lavoro dalle cartelle di lavoro a livello di codice
  È possibile eliminare qualsiasi foglio di lavoro da una cartella di lavoro. Per eliminare un foglio di lavoro, usare l'elemento host del foglio di lavoro o accedere al foglio di lavoro tramite la raccolta Sheets della cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host Worksheet
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per eliminarlo usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento direttamente all'elemento host del foglio di lavoro.

> [!IMPORTANT]
> Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:
>
> - Cartella di lavoro di Excel 2013
> - Modello di Excel 2013
> - Cartella di lavoro di Excel 2010
> - Modello di Excel 2010
>
>   Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft. Office. Interop. Excel** , quindi è necessario usare le classi di tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per altre informazioni, vedere [procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari](how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Per eliminare un foglio di lavoro mediante un elemento host del foglio di lavoro

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> di `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta Sheets della cartella di lavoro di Excel
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:

- Se si intende eliminare un foglio di lavoro in un componente aggiuntivo VSTO.

- Se il foglio di lavoro che si vuole eliminare è stato creato in fase di esecuzione in una personalizzazione a livello di documento.

  Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento al foglio tramite il numero di indice della raccolta **Sheets** . Per questo codice si presume che sia già stato creato un nuovo foglio di lavoro a livello di codice.

> [!IMPORTANT]
> Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft. Office. Interop. Excel** , quindi è necessario usare le classi di tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per altre informazioni, vedere [procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari](how-to-target-office-applications-through-primary-interop-assemblies.md) e [riferimento all'assembly di interoperabilità primario di Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Per eliminare un foglio di lavoro mediante la raccolta Sheets della cartella di lavoro di Excel

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](working-with-worksheets.md)
- [Procedura: nascondere i fogli di programmazione a livello di codice](how-to-programmatically-hide-worksheets.md)
- [Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Procedura: selezionare fogli di programmazione a livello di codice](how-to-programmatically-select-worksheets.md)
- [Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Elemento host Worksheet](worksheet-host-item.md)
- [Accesso globale a oggetti nei progetti di Office](global-access-to-objects-in-office-projects.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](programmatic-limitations-of-host-items-and-host-controls.md)
