---
title: Copiare e incollare forme nel Visio a livello di codice
description: Informazioni su come copiare forme in una pagina di un documento a livello di codice e incollarle in una nuova pagina nello stesso documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fb913dc14437f9593a656a5ae4eb02368b82493b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046607"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Procedura: Copiare e incollare forme in un documento Visio codice
  È possibile copiare a livello di codice forme contenute in una pagina di un documento e quindi incollarle in una nuova pagina dello stesso documento. Le forme possono essere incollate nella posizione predefinita (ovvero il centro della finestra attiva) o nelle stesse coordinate occupate nella pagina originale.

## <a name="copy-and-paste-shapes"></a>Copiare e incollare forme
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)e [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Per copiare forme nel centro di un'altra pagina

- L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nel centro della seconda pagina.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet14":::

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiare e incollare forme con le stesse posizioni
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)e [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Se è necessario controllare il formato delle informazioni incollate e(facoltativamente) stabilire un collegamento a un file di origine (ad esempio, un documento di Microsoft Office Word), usare il metodo PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Per copiare le forme nella stessa posizione di un'altra pagina

- L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nella seconda pagina mantenendo le coordinate originali.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Vedi anche
- [Visio soluzioni](../vsto/visio-solutions.md)
- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)
- [Usare le Visio personalizzate](../vsto/working-with-visio-shapes.md)
- [Procedura: Aggiungere forme a un documento Visio codice](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
