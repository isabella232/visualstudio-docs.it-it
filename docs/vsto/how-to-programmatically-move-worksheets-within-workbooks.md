---
title: "Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice"
description: Informazioni su come modificare a livello di codice la posizione dei fogli di lavoro rispetto ad altri fogli di lavoro in una cartella di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827292"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice
  A livello di codice è possibile modificare la posizione dei fogli di lavoro rispetto ad altri fogli in una cartella di lavoro. Se non si specifica una posizione per il foglio spostato, Excel crea una nuova cartella di lavoro per contenerlo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Per spostare un foglio di lavoro in una personalizzazione a livello di documento

1. Assegnare il numero totale di fogli della cartella di lavoro a una variabile e quindi spostare il primo foglio di lavoro in modo che diventi l'ultimo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Per spostare un foglio di lavoro in un componente aggiuntivo VSTO

1. Assegnare il numero totale di fogli della cartella di lavoro a una variabile e quindi spostare il primo foglio di lavoro in modo che diventi l'ultimo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Nascondere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Procedura: Eliminare fogli di lavoro da cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: Proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Accesso globale agli oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
