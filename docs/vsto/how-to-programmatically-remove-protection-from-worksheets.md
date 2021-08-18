---
title: 'Procedura: Rimuovere la protezione dai fogli di lavoro a livello di codice'
description: Informazioni su come usare Visual Studio per rimuovere la protezione a livello di codice da un Microsoft Excel foglio di lavoro.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: af5fb0cab5501b6a5bbe19025be6f963728ee477
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092176"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Procedura: Rimuovere la protezione dai fogli di lavoro a livello di codice
  È possibile rimuovere la protezione a livello di codice da un foglio di lavoro di Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 L'esempio seguente usa la variabile `getPasswordFromUser`, che contiene una password ottenuta dall'utente.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Per rimuovere la protezione da un foglio di lavoro in una personalizzazione a livello di documento

1. Chiamare il <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> metodo del foglio di lavoro e passare la password, se necessario. Questo esempio presuppone l'utilizzo di un foglio di lavoro denominato `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Per rimuovere la protezione di un foglio di lavoro in VSTO componente aggiuntivo

1. Chiamare il <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> metodo del foglio di lavoro attivo e passare la password, se necessario.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Procedura: Proteggere le cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-protect-workbooks.md)
- [Procedura: Nascondere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Accesso globale agli oggetti nei progetti Office globali](../vsto/global-access-to-objects-in-office-projects.md)
