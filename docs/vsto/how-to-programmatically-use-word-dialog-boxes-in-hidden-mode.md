---
title: 'Procedura: Usare le finestre di dialogo di Word in modalità nascosta a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255844"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procedura: Usare le finestre di dialogo di Word in modalità nascosta a livello di codice
  È possibile eseguire operazioni complesse con una chiamata al metodo richiamando le finestre di dialogo predefinite in Microsoft Office parola senza visualizzarle all'utente. A tale scopo, è possibile utilizzare <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> il metodo <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto senza chiamare il <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metodo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Esempi
 Gli esempi di codice seguenti illustrano come usare la finestra di dialogo **Imposta pagina** in modalità nascosta per impostare più proprietà di impostazione della pagina senza input utente. Negli esempi viene utilizzato <xref:Microsoft.Office.Interop.Word.Dialog> un oggetto per configurare una dimensione di pagina personalizzata. Le impostazioni specifiche per la configurazione della pagina, ad esempio il margine superiore, il margine inferiore e così via, sono disponibili come proprietà ad associazione tardiva dell' <xref:Microsoft.Office.Interop.Word.Dialog> oggetto. Queste proprietà vengono create dinamicamente da Word in fase di esecuzione.

 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** è disattivato e nei C# progetti visivi destinati [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]a. In questi progetti è possibile utilizzare le funzionalità di associazione tardiva nel Visual Basic e C# nei compilatori visivi. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o `ThisAddIn` nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** è on. In questi progetti, è necessario utilizzare la reflection per accedere alle proprietà ad associazione tardiva. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe o `ThisAddIn` nel progetto.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare le finestre di dialogo predefinite in Word a livello di codice](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
