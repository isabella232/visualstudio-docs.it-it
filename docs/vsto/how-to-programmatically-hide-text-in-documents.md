---
title: 'Procedura: Nascondere testo nei documenti a livello di codice'
description: Informazioni su come nascondere il testo in Microsoft Word documento impostando la proprietà Hidden del tipo di carattere per un intervallo di testo specifico.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 72e869d585f2db5163036b4e8f024d4ca4c0c620c8aec829ffcdd6ccea1cf610
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366251"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Procedura: Nascondere testo nei documenti a livello di codice
  È possibile nascondere testo in un documento impostando la proprietà <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> di un controllo <xref:Microsoft.Office.Interop.Word.Range.Font%2A> per un intervallo di testo determinato.

 Ad esempio, è possibile nascondere temporaneamente il testo all'interno di (in una personalizzazione a livello di documento) o (in un componente aggiuntivo VSTO) prima di inviare un documento a una <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> stampante.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Per nascondere testo in un controllo Bookmark mentre si stampa il documento

1. Creare una routine che nasconda tutto il testo che rientra in un intervallo specificato.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet105":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet105":::

2. Creare una routine che scopra tutto il testo che rientra in un intervallo specificato.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet106":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet106":::

3. Passare l'intervallo di un segnalibro al metodo `HideText` , stampare il documento e quindi passare lo stesso intervallo al metodo `UnhideText` .

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento. Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet107":::

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet107":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che il documento contenga un controllo (in una personalizzazione a livello di documento) o un controllo (in un componente aggiuntivo <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> VSTO) denominato `bookmark1` .

## <a name="see-also"></a>Vedi anche
- [Procedura: Stampare documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Reimpostare gli intervalli a livello di codice nei documenti di Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: Aggiornare il testo segnalibro a livello di codice](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
