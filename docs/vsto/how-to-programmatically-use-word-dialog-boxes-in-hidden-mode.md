---
title: 'Procedura: Usare le finestre di dialogo di Word in modalità nascosta a livello di codice'
description: Informazioni su come usare le Visual Studio a livello di codice per Microsoft Word finestre di dialogo in modalità nascosta.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ca6d7f1e14904497ecb756936b996b64311a8423
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710049"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procedura: Usare le finestre di dialogo di Word in modalità nascosta a livello di codice
  È possibile eseguire operazioni complesse con una chiamata al metodo richiamando le finestre di dialogo incorporate in Microsoft Office Word senza visualizzarle all'utente. A tale scopo, è possibile usare <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> il metodo <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto senza chiamare il metodo <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Esempio
 Gli esempi di codice seguenti  illustrano come usare la finestra di dialogo Imposta pagina in modalità nascosta per impostare più proprietà di impostazione della pagina senza input dell'utente. Negli esempi viene utilizzato un <xref:Microsoft.Office.Interop.Word.Dialog> oggetto per configurare dimensioni di pagina personalizzate. Le impostazioni specifiche per l'impostazione della pagina, ad esempio il margine superiore, il margine inferiore e così via, sono disponibili come proprietà ad associazione tardiva <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto . Queste proprietà vengono create dinamicamente da Word in fase di esecuzione.

 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** è disattivato e nei progetti Visual C# che hanno come destinazione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In questi progetti è possibile usare le funzionalità di associazione tardiva nei compilatori Visual Basic e Visual C#. Per usare questo esempio, eseguirlo dalla `ThisDocument` `ThisAddIn` classe o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 Nell'esempio seguente viene illustrato come eseguire questa attività in Visual Basic in **cui Option Strict** è attivata. In questi progetti è necessario usare la reflection per accedere alle proprietà ad associazione tardiva. Per usare questo esempio, eseguirlo dalla `ThisDocument` `ThisAddIn` classe o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare finestre di dialogo incorporate in Word a livello di codice](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Associazione tardiva in Office soluzioni](../vsto/late-binding-in-office-solutions.md)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
