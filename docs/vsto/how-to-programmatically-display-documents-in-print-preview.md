---
title: "Procedura: Visualizzare documenti nell'anteprima di stampa a livello di codice"
description: Informazioni su come visualizzare documenti in Anteprima di stampa a livello di codice in Microsoft Word documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 855aea5fefede1e454a8f273ad1cdf402cae4b9aea6159f0ac6f86fb93d64818
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366238"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Procedura: Visualizzare documenti nell'anteprima di stampa a livello di codice
  Se la soluzione genera un report, è possibile che si voglia far visualizzare il report all'utente in modalità Anteprima di stampa.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Procedure per le personalizzazioni a livello di documento

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> della classe <xref:Microsoft.Office.Tools.Word.Document> . Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview

1. Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="procedures-for-vsto-add-ins"></a>Procedure per i componenti aggiuntivi VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole visualizzare in anteprima. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet13":::

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview

1. Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet14":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Stampare documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md)
- [Procedura: Aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Procedura: Creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)
