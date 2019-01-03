---
title: 'Procedura: Copiare e incollare forme in un documento di Visio a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7994d605d22b38b64219a384e5afb0b002ff755
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856488"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Procedura: Copiare e incollare forme in un documento di Visio a livello di codice
  È possibile copiare a livello di codice forme contenute in una pagina di un documento e quindi incollarle in una nuova pagina dello stesso documento. Le forme possono essere incollate nella posizione predefinita (ovvero il centro della finestra attiva) o nelle stesse coordinate occupate nella pagina originale.  
  
## <a name="copy-and-paste-shapes"></a>Copiare e incollare le forme  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)e [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Per copiare forme nel centro di un'altra pagina  
  
-   L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nel centro della seconda pagina.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiare e incollare forme le stesse coordinate  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)e [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .  
  
 Se è necessario controllare il formato delle informazioni incollate ed eventualmente stabilire un collegamento a un file di origine (ad esempio, un documento di Microsoft Office Word), usare il metodo PasteSpecial.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Per copiare le forme nella stessa posizione di un'altra pagina  
  
-   L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nella seconda pagina mantenendo le coordinate originali.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Lavorare con le forme di Visio](../vsto/working-with-visio-shapes.md)   
 [Procedura: A livello di codice aggiungere forme a un documento di Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
