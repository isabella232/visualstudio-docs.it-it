---
title: 'Procedura: Chiudere documenti a livello di codice'
description: Informazioni su come chiudere il documento attivo o specificare un Microsoft Office documento di Word da chiudere.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 795629796c0b72368e9bf0bc4fa0e36bdbdcda414b0d5c3af97875f6326171b7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394498"
---
# <a name="how-to-programmatically-close-documents"></a>Procedura: Chiudere documenti a livello di codice
  È possibile chiudere il documento attivo oppure specificare un documento da chiudere.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Chiudere il documento attivo
 Esistono due procedure per chiudere il documento attivo: una per le personalizzazioni a livello di documento e una per i componenti aggiuntivi VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Per chiudere il documento attivo in una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Close%2A> della classe `ThisDocument` nel progetto per chiudere il documento associato alla personalizzazione. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` .

    > [!NOTE]
    > Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet3":::

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Per chiudere il documento attivo in un componente aggiuntivo VSTO

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Close%2A> della proprietà <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> per chiudere il documento attivo. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisAddIn` nel progetto.

    > [!NOTE]
    > Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet3":::

## <a name="close-a-document-that-you-specify-by-name"></a>Chiudere un documento specificato in base al nome
 Il modo in cui viene chiuso un documento specificato in base al nome è identico per i componenti aggiuntivi VSTO e le personalizzazioni a livello di documento.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Per chiudere un documento specificato in base al nome

1. Specificare il nome del documento come argomento per la raccolta <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> e quindi chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . L'esempio di codice seguente presuppone l'apertura in Word di un documento il cui nome è **NewDocument** .

    > [!NOTE]
    > Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet4":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Procedura: Salvare documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
