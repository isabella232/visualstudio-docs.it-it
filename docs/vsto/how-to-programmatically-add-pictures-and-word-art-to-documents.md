---
title: 'Procedura: aggiungere a livello di codice le immagini e WordArt ai documenti'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 61399df32ef0f22d1d0aacf23dea45c1357c7579
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255106"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Procedura: aggiungere a livello di codice le immagini e WordArt ai documenti
  È possibile aggiungere immagini e oggetti disegno ai documenti in fase di progettazione o in fase di esecuzione. WordArt consente di aggiungere testo decorativo ai documenti di Microsoft Office Word. Questi effetti di testo speciali sono oggetti disegno che è possibile personalizzare e inserire nel documento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="add-a-picture-at-design-time"></a>Aggiungere un'immagine in fase di progettazione  
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un'immagine al documento in fase di progettazione.  
  
### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Per aggiungere un'immagine a un documento di Word in fase di progettazione  
  
1.  Posizionare il cursore nel punto in cui si vuole inserire l'immagine nel documento.  
  
2.  Scegliere il **Inserisci** della barra multifunzione.  
  
3.  Nel **illustrazioni** gruppo, fare clic su **immagine**.  
  
4.  Nel **Inserisci immagine** passare all'immagine da inserire nella finestra di dialogo e fare clic su **Inserisci**.  
  
     L'immagine verrà aggiunta al documento in corrispondenza della posizione corrente del cursore.  
  
## <a name="add-a-picture-at-runtime"></a>Aggiungere un'immagine in fase di esecuzione  
 È possibile inserire un'immagine in un documento in corrispondenza della posizione corrente del cursore.  
  
### <a name="to-add-a-picture-at-the-cursor-location"></a>Per aggiungere un'immagine in corrispondenza della posizione del cursore  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> della raccolta <xref:Microsoft.Office.Interop.Word.InlineShapes> e passare il nome del file.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="add-wordart-at-design-time"></a>Aggiungere un oggetto WordArt in fase di progettazione  
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un oggetto WordArt al documento in fase di progettazione.  
  
### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Per aggiungere un oggetto WordArt a un documento di Word in fase di progettazione  
  
1.  Posizionare il cursore nel punto in cui si vuole inserire l'oggetto WordArt nel documento.  
  
2.  Scegliere il **Inserisci** della barra multifunzione.  
  
3.  Nel **testo** gruppo, fare clic su **WordArt**e quindi selezionare uno stile WordArt.  
  
4.  Aggiungere il testo che si desidera visualizzare nel documento per il **Modifica testo WordArt** finestra di dialogo e fare clic su **OK**.  
  
     Il testo verrà aggiunto al documento con lo stile WordArt selezionato applicato.  
  
## <a name="add-wordart-at-runtime"></a>Aggiungere un oggetto WordArt in fase di esecuzione  
 È possibile inserire un oggetto WordArt in un documento in corrispondenza della posizione corrente del cursore. La procedura è diversa per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in una personalizzazione a livello di documento  
  
1.  Ottenere la posizione corrente superiore e sinistra del cursore.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> nel documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in un componente aggiuntivo VSTO  
  
1.  Ottenere la posizione corrente superiore e sinistra del cursore.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> del documento attivo (o un documento diverso specificato).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
  
-   Un'immagine denominata *SamplePicture. jpg* deve esistere nell'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: a livello di programmazione inserire testo nei documenti di Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: ripristino a livello di codice le selezioni dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Procedura: salvare i documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  