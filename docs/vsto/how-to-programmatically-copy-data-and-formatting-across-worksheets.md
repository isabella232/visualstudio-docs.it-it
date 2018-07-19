---
title: 'Procedura: copiare a livello di programmazione dei dati e formattazione nei fogli di lavoro'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4a4cce083bee8b57ff37276ae909799a9a6791d7
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256682"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Procedura: copiare a livello di programmazione dei dati e formattazione nei fogli di lavoro
  È possibile copiare dati da un intervallo di un foglio in tutti gli altri fogli in una cartella di lavoro utilizzando il <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> (metodo). Specificare un intervallo, e se si desidera copiare i dati, formattare o entrambi.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio richiede un intervallo denominato `rangeData` in un foglio di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: a livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Procedura: modificare a livello di codice la formattazione nelle righe del foglio di lavoro contenenti celle selezionate](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  