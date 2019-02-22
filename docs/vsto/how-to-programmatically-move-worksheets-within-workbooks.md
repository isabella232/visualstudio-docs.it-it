---
title: "Procedura: A livello di programmazione spostare fogli di lavoro all'interno di cartelle di lavoro"
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 20ca03e8d7a3c574501d879cf9949d26fd7ba3a3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56595737"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Procedura: A livello di programmazione spostare fogli di lavoro all'interno di cartelle di lavoro
  A livello di codice è possibile modificare la posizione dei fogli di lavoro rispetto ad altri fogli in una cartella di lavoro. Se non si specifica una posizione per il foglio spostato, Excel crea una nuova cartella di lavoro per contenerlo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Per spostare un foglio di lavoro in una personalizzazione a livello di documento

1.  Assegnare il numero totale di fogli della cartella di lavoro a una variabile e quindi spostare il primo foglio di lavoro in modo che diventi l'ultimo.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Per spostare un foglio di lavoro in un componente aggiuntivo VSTO

1.  Assegnare il numero totale di fogli della cartella di lavoro a una variabile e quindi spostare il primo foglio di lavoro in modo che diventi l'ultimo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Procedura: A livello di codice eliminare fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: Proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
