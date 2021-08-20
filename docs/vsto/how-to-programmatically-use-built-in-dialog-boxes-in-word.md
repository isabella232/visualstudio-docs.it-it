---
title: 'Procedura: Usare finestre di dialogo incorporate in Word a livello di codice'
description: Informazioni su come usare Visual Studio per usare a livello di codice le finestre di dialogo incorporate in Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 66b35e6a46ba42f64dddf54427d43bba74f10ae0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147986"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procedura: Usare finestre di dialogo incorporate in Word a livello di codice
  Quando si lavora con Microsoft Office Word, in alcuni casi è necessario visualizzare finestre di dialogo per l'input dell'utente. Anche se è possibile crearne di personalizzate, è anche possibile adottare l'approccio basato sull'uso delle finestre di dialogo incorporate in Word, esposte nella raccolta <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> dell'oggetto . In questo modo è possibile accedere a più di 200 finestre di dialogo incorporate, rappresentate come enumerazioni.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Visualizzare le finestre di dialogo
 Per visualizzare una finestra di dialogo, utilizzare uno dei valori dell'enumerazione per creare un oggetto che rappresenta la finestra di dialogo <xref:Microsoft.Office.Interop.Word.WdWordDialog> <xref:Microsoft.Office.Interop.Word.Dialog> da visualizzare. Chiamare quindi il <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodo <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto .

 Nell'esempio di codice seguente viene illustrato come visualizzare la **finestra di dialogo Apri** file . Per usare questo esempio, eseguirlo dalla `ThisDocument` classe `ThisAddIn` o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Accedere ai membri della finestra di dialogo disponibili tramite l'associazione tardiva
 Alcune proprietà e metodi delle finestre di dialogo in Word sono disponibili solo tramite l'associazione tardiva. Nei Visual Basic in cui **Option Strict è** attivata, è necessario usare la reflection per accedere a questi membri. Per altre informazioni, vedere [Associazione tardiva in Office soluzioni](../vsto/late-binding-in-office-solutions.md).

 Nell'esempio di codice seguente viene illustrato come usare la proprietà **Name** della finestra di dialogo **Apri** file nei progetti Visual Basic in cui **Option Strict** è disattivato o nei progetti Visual C# che hanno come destinazione o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Per usare questo esempio, eseguirlo dalla `ThisDocument` classe `ThisAddIn` o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 Nell'esempio di codice seguente viene illustrato come usare la reflection per accedere alla proprietà **Name** della finestra di dialogo **Apri** file nei Visual Basic in cui **Option Strict** è attivata. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe `ThisAddIn` o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare le finestre di dialogo di Word a livello di codice in modalità nascosta](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
