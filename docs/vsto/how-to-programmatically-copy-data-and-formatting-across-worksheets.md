---
title: Copiare dati e formattazione tra fogli di lavoro a livello di codice
description: Informazioni su come copiare dati da un intervallo di un foglio a tutti gli altri fogli di una cartella di lavoro usando il metodo FillAcrossSheets.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fb87be6aefda46033c13911be0d1781ceaa8999bf26d7111204cb4a9dd7fa0d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268092"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Procedura: Copiare dati e formattazione tra fogli di lavoro a livello di codice
  È possibile copiare dati da un intervallo di un foglio in tutti gli altri fogli di una cartella di lavoro usando il <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metodo . Specificare un intervallo e se copiare i dati, la formattazione o entrambi.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet44":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet44":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un intervallo denominato `rangeData` in un foglio di lavoro.

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Procedura: Modificare la formattazione a livello di codice nelle righe del foglio di lavoro contenenti celle selezionate](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
