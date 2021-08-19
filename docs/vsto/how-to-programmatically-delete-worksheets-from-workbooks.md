---
title: 'Procedura: Eliminare fogli di lavoro da cartelle di lavoro a livello di codice'
description: Informazioni su come eliminare a livello di codice qualsiasi foglio di lavoro in Microsoft Excel cartella di lavoro usando l'elemento host del foglio di lavoro, ad esempio .
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 783ee376cda1ca5a4e293f1e3f8ef7a5805b6edc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148103"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Procedura: Eliminare fogli di lavoro da cartelle di lavoro a livello di codice
  È possibile eliminare qualsiasi foglio di lavoro da una cartella di lavoro. Per eliminare un foglio di lavoro, usare l'elemento host del foglio di lavoro o accedere al foglio di lavoro tramite la raccolta Sheets della cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host del foglio di lavoro
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per eliminarlo usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento direttamente all'elemento host del foglio di lavoro.

> [!IMPORTANT]
> Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:
>
> - Cartella di lavoro di Excel 2013
> - Modello di Excel 2013
> - Cartella di lavoro di Excel 2010
> - Modello di Excel 2010
>
>   Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento a **Microsoft.Office. Interoperabilità. Excel** assembly ed è quindi necessario usare le classi di tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per altre informazioni, vedere [Procedura:](how-to-target-office-applications-through-primary-interop-assemblies.md) Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari e informazioni di riferimento sugli assembly di interoperabilità primari [Excel 2010.](office-primary-interop-assemblies.md)

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Per eliminare un foglio di lavoro mediante un elemento host del foglio di lavoro

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> di `Sheet1`.

     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet17":::
     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet17":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta Sheets della cartella di lavoro Excel lavoro
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:

- Se si intende eliminare un foglio di lavoro in un componente aggiuntivo VSTO.

- Se il foglio di lavoro che si vuole eliminare è stato creato in fase di esecuzione in una personalizzazione a livello di documento.

  Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento al foglio tramite il numero di indice della **raccolta Sheets.** Per questo codice si presume che sia già stato creato un nuovo foglio di lavoro a livello di codice.

> [!IMPORTANT]
> Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento a **Microsoft.Office. Interoperabilità. Excel** assembly ed è quindi necessario usare le classi di tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro. Per altre informazioni, vedere [Procedura:](how-to-target-office-applications-through-primary-interop-assemblies.md) Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari e informazioni di riferimento sugli assembly di interoperabilità primari [Excel 2010.](office-primary-interop-assemblies.md)

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Per eliminare un foglio di lavoro mediante la raccolta Sheets della cartella di lavoro di Excel

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.

     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet18":::
     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet18":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](working-with-worksheets.md)
- [Procedura: Nascondere fogli di lavoro a livello di codice](how-to-programmatically-hide-worksheets.md)
- [Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Procedura: Selezionare fogli di lavoro a livello di codice](how-to-programmatically-select-worksheets.md)
- [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Elemento host foglio di lavoro](worksheet-host-item.md)
- [Accesso globale agli oggetti nei progetti Office globali](global-access-to-objects-in-office-projects.md)
- [Limitazioni a livello di codice di elementi host e controlli host](programmatic-limitations-of-host-items-and-host-controls.md)
