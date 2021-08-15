---
title: 'Procedura: Usare finestre di dialogo incorporate in Word a livello di codice'
description: Informazioni su come usare le Visual Studio per usare le finestre di dialogo incorporate in Microsoft Word.
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
ms.openlocfilehash: 3581107e77415749f93ea6e6e94edb6f19e49dde89fd0ad5eba705eb23b92462
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267871"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procedura: Usare finestre di dialogo incorporate in Word a livello di codice
  Quando si lavora con Microsoft Office Word, in alcuni casi è necessario visualizzare finestre di dialogo per l'input dell'utente. Sebbene sia possibile creare finestre di dialogo personalizzate, è anche possibile adottare l'approccio basato sull'uso delle finestre di dialogo incorporate in Word, esposte nella raccolta <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> dell'oggetto . In questo modo è possibile accedere a oltre 200 finestre di dialogo incorporate, rappresentate come enumerazioni.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Visualizzare le finestre di dialogo
 Per visualizzare una finestra di dialogo, utilizzare uno dei valori dell'enumerazione per creare un oggetto che rappresenta la finestra <xref:Microsoft.Office.Interop.Word.WdWordDialog> di dialogo che si desidera <xref:Microsoft.Office.Interop.Word.Dialog> visualizzare. Chiamare quindi il <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodo <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto .

 Nell'esempio di codice seguente viene illustrato come visualizzare la **finestra di dialogo** Apri file . Per usare questo esempio, eseguirlo dalla `ThisDocument` `ThisAddIn` classe o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Accedere ai membri della finestra di dialogo disponibili tramite associazione tardiva
 Alcune proprietà e metodi delle finestre di dialogo in Word sono disponibili solo tramite associazione tardiva. Nei Visual Basic in cui **Option Strict è** attiva, è necessario usare la reflection per accedere a questi membri. Per altre informazioni, vedere [Associazione tardiva in Office soluzioni](../vsto/late-binding-in-office-solutions.md).

 L'esempio di codice seguente illustra come  usare la proprietà **Name** della finestra di dialogo Apri file nei progetti Visual Basic in cui **Option Strict** è disattivato o nei progetti Visual C# che hanno come destinazione o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Per usare questo esempio, eseguirlo dalla `ThisDocument` `ThisAddIn` classe o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 Nell'esempio di codice seguente viene illustrato come  usare la reflection per accedere alla proprietà **Name** della finestra di dialogo Apri file nei Visual Basic in cui **Option Strict** è attivata. Per usare questo esempio, eseguirlo dalla `ThisDocument` `ThisAddIn` classe o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare le finestre di dialogo di Word in modalità nascosta a livello di codice](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
- [Istruzione option strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
