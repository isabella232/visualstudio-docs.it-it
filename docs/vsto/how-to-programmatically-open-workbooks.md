---
title: 'Procedura: Aprire cartelle di lavoro a livello di codice'
description: Informazioni su come usare Visual Studio per aprire una cartella di lavoro Microsoft Excel a livello di codice o usare una cartella di lavoro esistente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 529b957613ae954d35c2284870d6512c7357ac64
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633916"
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedura: Aprire cartelle di lavoro a livello di codice
  La raccolta in Microsoft Office Excel consente di usare tutte le cartelle di lavoro <xref:Microsoft.Office.Interop.Excel.Workbooks> aperte e di aprire le cartelle di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Per aprire una cartella di lavoro esistente

1. Usare il <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodo della raccolta , passando il percorso della cartella di <xref:Microsoft.Office.Interop.Excel.Workbooks> lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Una cartella di `YourWorkbook.xls` lavoro denominata deve esistere in una directory denominata `Test` nell'unità C.

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: Aprire file di testo come cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Procedura: Creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Procedura: Salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)
- [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
