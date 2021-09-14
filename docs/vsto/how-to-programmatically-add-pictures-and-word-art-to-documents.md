---
title: Aggiungere immagini e Word Art ai documenti a livello di codice
description: Informazioni su come aggiungere immagini e oggetti di disegno ai documenti in fase di progettazione o in fase di esecuzione.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3f0e284b8307aa60f15f55d2ac5fc5cb5aed5e9c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634004"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Procedura: Aggiungere immagini e Word Art ai documenti a livello di codice
  È possibile aggiungere immagini e oggetti disegno ai documenti in fase di progettazione o in fase di esecuzione. WordArt consente di aggiungere testo decorativo ai documenti di Microsoft Office Word. Questi effetti di testo speciali sono oggetti disegno che è possibile personalizzare e inserire nel documento.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Aggiungere un'immagine in fase di progettazione
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un'immagine al documento in fase di progettazione.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Per aggiungere un'immagine a un documento di Word in fase di progettazione

1. Posizionare il cursore nel punto in cui si vuole inserire l'immagine nel documento.

2. Fare clic **sulla scheda** Inserisci della barra multifunzione.

3. Nel gruppo **Illustrazioni** fare clic su **Immagine**.

4. Nella finestra **di dialogo** Inserisci immagine passare all'immagine da inserire e fare clic su **Inserisci**.

     L'immagine verrà aggiunta al documento in corrispondenza della posizione corrente del cursore.

## <a name="add-a-picture-at-run-time"></a>Aggiungere un'immagine in fase di esecuzione
 È possibile inserire un'immagine in un documento in corrispondenza della posizione corrente del cursore.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Per aggiungere un'immagine in corrispondenza della posizione del cursore

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> della raccolta <xref:Microsoft.Office.Interop.Word.InlineShapes> e passare il nome del file.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Aggiungere WordArt in fase di progettazione
 Se si sviluppa una personalizzazione a livello di documento, è possibile aggiungere un oggetto WordArt al documento in fase di progettazione.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Per aggiungere un oggetto WordArt a un documento di Word in fase di progettazione

1. Posizionare il cursore nel punto in cui si vuole inserire l'oggetto WordArt nel documento.

2. Fare clic **sulla scheda** Inserisci della barra multifunzione.

3. Nel gruppo **Testo** fare clic su **WordArt** e quindi selezionare uno stile WordArt.

4. Aggiungere il testo da visualizzare nel documento alla finestra di dialogo Modifica testo **WordArt** e fare clic su **OK.**

     Il testo verrà aggiunto al documento con lo stile WordArt selezionato applicato.

## <a name="add-wordart-at-run-time"></a>Aggiungere WordArt in fase di esecuzione
 È possibile inserire un oggetto WordArt in un documento in corrispondenza della posizione corrente del cursore. La procedura è diversa per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in una personalizzazione a livello di documento

1. Ottenere la posizione corrente superiore e sinistra del cursore.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> nel documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Per aggiungere un oggetto WordArt in corrispondenza della posizione del cursore in un componente aggiuntivo VSTO

1. Ottenere la posizione corrente superiore e sinistra del cursore.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Shapes> del documento attivo (o un documento diverso specificato).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Compilare il codice

- Un'immagine denominata *SamplePicture.jpg* deve esistere nell'unità C.

## <a name="see-also"></a>Vedi anche
- [Procedura: Aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)
- [Procedura: Inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Procedura: Salvare documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
