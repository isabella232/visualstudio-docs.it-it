---
title: 'Procedura: Elencare tutti i fogli di lavoro in una cartella di lavoro a livello di codice'
description: Informazioni su come elencare tutti i fogli di lavoro in una cartella Microsoft Excel a livello di codice usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b62b2bdb5fdff99a42cb0967e005b6c907ffbe76
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633923"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Procedura: Elencare tutti i fogli di lavoro in una cartella di lavoro a livello di codice
  La classe <xref:Microsoft.Office.Interop.Excel.Workbook> fornisce un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheets>. Questo oggetto contiene una raccolta di tutti gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> presenti nella cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Per elencare tutti i fogli di lavoro presenti in una cartella di lavoro in una personalizzazione a livello di documento

1. Scorrere la raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets> e inviare il nome di ciascun foglio a un offset di cella determinato da un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet21":::

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Per elencare tutti i fogli di lavoro presenti in una cartella di lavoro in un componente aggiuntivo VSTO

1. Scorrere la raccolta <xref:Microsoft.Office.Interop.Excel.Worksheets> e inviare il nome di ciascun foglio a un offset di cella determinato da un oggetto <xref:Microsoft.Office.Interop.Excel.Range>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Accesso globale agli oggetti nei Office progetto](../vsto/global-access-to-objects-in-office-projects.md)
