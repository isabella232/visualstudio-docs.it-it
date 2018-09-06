---
title: 'Procedura: utilizzare a livello di programmazione le finestre di dialogo di Word in modalità nascosta'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5b123f1b58e61dffc64b5df912092edfd3fbf53
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672810"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procedura: utilizzare a livello di programmazione le finestre di dialogo di Word in modalità nascosta
  È possibile eseguire operazioni complesse con una chiamata al metodo richiamando le finestre di dialogo predefinite in Microsoft Office Word senza che vengano visualizzate all'utente. Tale scopo, è possibile utilizzare il <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metodo per il <xref:Microsoft.Office.Interop.Word.Dialog> oggetti senza chiamare il <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> (metodo).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Esempi  
 Gli esempi di codice seguenti illustrano come usare il **Imposta pagina** finestra di dialogo in modalità nascosta a set di proprietà di installazione di più pagine senza input dell'utente. Gli esempi usano un <xref:Microsoft.Office.Interop.Word.Dialog> oggetto per configurare una dimensione di pagina personalizzato. Le impostazioni specifiche per l'installazione di pagina, ad esempio il margine superiore, il margine inferiore e così via, sono disponibili come proprietà di associazione tardiva del <xref:Microsoft.Office.Interop.Word.Dialog> oggetto. Queste proprietà vengono create dinamicamente dal Word in fase di esecuzione.  
  
 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** è disattivata e nei progetti Visual c# che hanno come destinazione il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In questi progetti, è possibile usare funzionalità di associazione tardiva nei compilatori Visual Basic e Visual c#. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 Nell'esempio seguente viene illustrato come eseguire questa attività nei progetti Visual Basic in cui **Option Strict** si trova in. In questi progetti, è necessario usare la reflection per accedere alle proprietà con associazione tardiva. Per usare questo esempio, eseguirlo dal `ThisDocument` o `ThisAddIn` classe nel progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare a livello di programmazione le finestre di dialogo predefinite in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  