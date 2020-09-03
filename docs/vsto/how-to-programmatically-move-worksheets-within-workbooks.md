---
title: "Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice"
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4594395eb887a950c9ff0ba41cd8d3c625d35dc3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519824"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice
  A livello di codice è possibile modificare la posizione dei fogli di lavoro rispetto ad altri fogli in una cartella di lavoro. Se non si specifica una posizione per il foglio spostato, Excel crea una nuova cartella di lavoro per contenerlo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Per spostare un foglio di lavoro in una personalizzazione a livello di documento

1. Assegnare il numero totale di fogli della cartella di lavoro a una variabile e quindi spostare il primo foglio di lavoro in modo che diventi l'ultimo.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Per spostare un foglio di un foglio di un componente aggiuntivo VSTO

1. Assegnare il numero totale di fogli della cartella di lavoro a una variabile e quindi spostare il primo foglio di lavoro in modo che diventi l'ultimo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: nascondere i fogli di programmazione a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Procedura: eliminare fogli di lavoro dalle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: proteggere i fogli di fogli di un foglio di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
