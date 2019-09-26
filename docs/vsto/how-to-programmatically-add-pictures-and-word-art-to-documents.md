---
title: Aggiungere immagini e Word Art ai documenti a livello di codice
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45b3030875539035f93bd340354e7041028200d2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253814"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Procedura: Aggiungere a livello di codice immagini e Word Art ai documenti
  È possibile aggiungere immagini e oggetti disegno ai documenti in fase di progettazione o in fase di esecuzione. WordArt consente di aggiungere testo decorativo ai documenti di Microsoft Office Word. Questi effetti di testo speciali sono oggetti disegno che è possibile personalizzare e inserire nel documento.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Aggiungere un'immagine in fase di progettazione
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un'immagine al documento in fase di progettazione.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Per aggiungere un'immagine a un documento di Word in fase di progettazione

1. Posizionare il cursore nel punto in cui si vuole inserire l'immagine nel documento.

2. Fare clic sulla scheda **Inserisci** della barra multifunzione.

3. Nel gruppo **illustrazioni** fare clic su **immagine**.

4. Nella finestra di dialogo **Inserisci immagine** passare all'immagine che si desidera inserire, quindi fare clic su **Inserisci**.

     L'immagine verrà aggiunta al documento in corrispondenza della posizione corrente del cursore.

## <a name="add-a-picture-at-run-time"></a>Aggiungere un'immagine in fase di esecuzione
 È possibile inserire un'immagine in un documento in corrispondenza della posizione corrente del cursore.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Per aggiungere un'immagine in corrispondenza della posizione del cursore

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> della raccolta <xref:Microsoft.Office.Interop.Word.InlineShapes> e passare il nome del file.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Aggiungi WordArt in fase di progettazione
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un oggetto WordArt al documento in fase di progettazione.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Per aggiungere un oggetto WordArt a un documento di Word in fase di progettazione

1. Posizionare il cursore nel punto in cui si vuole inserire l'oggetto WordArt nel documento.

2. Fare clic sulla scheda **Inserisci** della barra multifunzione.

3. Nel gruppo **testo** fare clic su **WordArt**, quindi selezionare uno stile WordArt.

4. Aggiungere il testo che si desidera visualizzare nel documento alla finestra di dialogo **modifica testo WordArt** e fare clic su **OK**.

     Il testo verrà aggiunto al documento con lo stile WordArt selezionato applicato.

## <a name="add-wordart-at-run-time"></a>Aggiungi WordArt in fase di esecuzione
 È possibile inserire un oggetto WordArt in un documento in corrispondenza della posizione corrente del cursore. La procedura è diversa per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in una personalizzazione a livello di documento

1. Ottenere la posizione corrente superiore e sinistra del cursore.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> nel documento.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in un componente aggiuntivo VSTO

1. Ottenere la posizione corrente superiore e sinistra del cursore.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> del documento attivo (o un documento diverso specificato).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Compilare il codice

- Un'immagine denominata *SamplePicture. jpg* deve esistere nell'unità C.

## <a name="see-also"></a>Vedere anche
- [Procedura: Aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Procedura: Inserire testo in documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: Ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Procedura: Salvare documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
