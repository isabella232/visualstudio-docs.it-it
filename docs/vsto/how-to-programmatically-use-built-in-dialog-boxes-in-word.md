---
title: 'Procedura: A livello di codice usare finestre di dialogo predefinite in Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f8037e4d91aa7706c7ffd7b9f32778dfeac79488
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961641"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procedura: A livello di codice usare finestre di dialogo predefinite in Word
  Quando si lavora con Microsoft Office Word, esistono casi è necessario per visualizzare le finestre di dialogo per l'input utente. È possibile crearne uno, è opportuno anche di adottare l'approccio dell'uso di finestre di dialogo predefinite in Word, esposti nel <xref:Microsoft.Office.Interop.Word.Dialogs> raccolta del <xref:Microsoft.Office.Interop.Word.Application> oggetto. In questo modo è possibile accedere a oltre 200 delle finestre di dialogo predefinite, rappresentati come enumerazioni.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Visualizzare le finestre di dialogo
 Per visualizzare una finestra di dialogo, usare uno dei valori del <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumerazione per creare un <xref:Microsoft.Office.Interop.Word.Dialog> oggetto che rappresenta la finestra di dialogo da visualizzare. Chiamare quindi il <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodo di <xref:Microsoft.Office.Interop.Word.Dialog> oggetto.

 Esempio di codice seguente viene illustrato come visualizzare le **Apri File** nella finestra di dialogo. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Accedere ai membri di finestra di dialogo disponibili tramite l'associazione tardiva
 Alcune proprietà e metodi delle finestre di dialogo di Word sono disponibili solo tramite l'associazione tardiva. Nei progetti Visual Basic dove **Option Strict** è on, è necessario usare la reflection per accedere a questi membri. Per altre informazioni, vedere [associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md).

 Esempio di codice seguente viene illustrato come utilizzare il **nome** proprietà delle **Apri File** finestra di dialogo in Visual Basic progetti dove **Option Strict** è disattivato o in Visual c# i progetti che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o il [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Esempio di codice seguente viene illustrato come usare la reflection per accedere la **nome** proprietà del **Apri File** finestra di dialogo in Visual Basic progetti dove **Option Strict** è in. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Vedere anche
- [Procedura: A livello di codice usare le finestre di dialogo di Word in modalità nascosta](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Istruzione Option strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
