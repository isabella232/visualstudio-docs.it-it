---
title: Copiare dati e formattazione tra fogli di dati a livello di codice
description: Informazioni su come copiare i dati da un intervallo in un foglio a tutti gli altri fogli in una cartella di lavoro usando il metodo FillAcrossSheets.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d768eb086707af2eeddeb18a77bad1ef1f101839
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964238"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Procedura: copiare dati e formattazione nei fogli di dati a livello di codice
  È possibile copiare i dati da un intervallo in un foglio a tutti gli altri fogli in una cartella di lavoro usando il <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metodo. Specificare un intervallo e se si desidera copiare i dati, la formattazione o entrambi.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un intervallo denominato `rangeData` in un foglio di foglio.

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Procedura: modificare la formattazione nelle righe di un foglio di un foglio di codice contenente celle selezionate](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
