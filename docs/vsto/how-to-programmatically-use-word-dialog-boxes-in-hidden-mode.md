---
title: 'Procedura: Usare le finestre di dialogo di Word a livello di codice in modalità nascosta'
description: Informazioni su come usare le Visual Studio a livello di codice per usare le finestre di dialogo di Microsoft Word in modalità nascosta.
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
ms.workload:
- office
ms.openlocfilehash: 39a81ccec284541d93d3a5901211d8a46ea6b61a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826187"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procedura: Usare le finestre di dialogo di Word a livello di codice in modalità nascosta
  È possibile eseguire operazioni complesse con una sola chiamata al metodo richiamando le finestre di dialogo incorporate in Microsoft Office Word senza visualizzarle all'utente. È possibile eseguire questa operazione usando il <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metodo <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto senza chiamare il metodo <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Esempio
 Gli esempi di codice seguenti  illustrano come usare la finestra di dialogo Imposta pagina in modalità nascosta per impostare più proprietà di impostazione della pagina senza input dell'utente. Negli esempi viene utilizzato <xref:Microsoft.Office.Interop.Word.Dialog> un oggetto per configurare dimensioni di pagina personalizzate. Le impostazioni specifiche per l'impostazione della pagina, ad esempio il margine superiore, il margine inferiore e così via, sono disponibili come proprietà ad associazione tardiva <xref:Microsoft.Office.Interop.Word.Dialog> dell'oggetto . Queste proprietà vengono create dinamicamente da Word in fase di esecuzione.

 L'esempio seguente illustra come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** è disattivato e nei progetti Visual C# che hanno come destinazione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . In questi progetti è possibile usare le funzionalità di associazione tardiva nei compilatori Visual Basic e Visual C#. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe `ThisAddIn` o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 L'esempio seguente illustra come eseguire questa attività nei progetti Visual Basic in **cui Option Strict** è attivata. In questi progetti è necessario usare la reflection per accedere alle proprietà ad associazione tardiva. Per usare questo esempio, eseguirlo dalla `ThisDocument` classe `ThisAddIn` o nel progetto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Usare finestre di dialogo incorporate in Word a livello di codice](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)
- [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
