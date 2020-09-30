---
title: 'Procedura: usare finestre di dialogo predefinite in Word a livello di codice'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6edba0b1fe9f06dbf7dba8dd1a3d01c4041ba8fe
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585654"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procedura: usare finestre di dialogo predefinite in Word a livello di codice
  Quando si lavora con Microsoft Office Word, in alcuni casi è necessario visualizzare le finestre di dialogo per l'input dell'utente. Sebbene sia possibile crearne di personalizzati, è anche possibile adottare l'approccio di utilizzo delle finestre di dialogo predefinite in Word, che vengono esposte nella <xref:Microsoft.Office.Interop.Word.Dialogs> raccolta dell' <xref:Microsoft.Office.Interop.Word.Application> oggetto. In questo modo è possibile accedere a oltre 200 delle finestre di dialogo predefinite, rappresentate come enumerazioni.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Finestre di dialogo di visualizzazione
 Per visualizzare una finestra di dialogo, utilizzare uno dei valori dell' <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumerazione per creare un <xref:Microsoft.Office.Interop.Word.Dialog> oggetto che rappresenti la finestra di dialogo che si desidera visualizzare. Quindi, chiamare il <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodo dell' <xref:Microsoft.Office.Interop.Word.Dialog> oggetto.

 Nell'esempio di codice riportato di seguito viene illustrato come visualizzare la finestra di dialogo **Apri file** . Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o `ThisAddIn` nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Accedere ai membri della finestra di dialogo disponibili tramite associazione tardiva
 Alcune proprietà e metodi delle finestre di dialogo in Word sono disponibili solo tramite associazione tardiva. Nei progetti Visual Basic in cui **Option Strict** è impostata su on, è necessario utilizzare la reflection per accedere a questi membri. Per altre informazioni, vedere [associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md).

 Nell'esempio di codice seguente viene illustrato come utilizzare la proprietà **Name** della finestra di dialogo **apri file** in Visual Basic progetti in cui **Option Strict** è disattivato o in progetti Visual C# destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o `ThisAddIn` nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare la reflection per accedere alla proprietà **Name** della finestra di dialogo **apri file** in Visual Basic progetti in cui **Option Strict** è on. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o `ThisAddIn` nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Vedi anche
- [Procedura: usare le finestre di dialogo di Word in modalità nascosta a livello di codice](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Istruzione Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
