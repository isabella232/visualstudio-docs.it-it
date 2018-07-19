---
title: 'Procedura: copiare e incollare forme in un documento di Visio a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 29dada62bb1e51c9cafb41d4eae08ce10e9a930c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257085"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Procedura: copiare e incollare forme in un documento di Visio a livello di codice
  È possibile copiare a livello di codice forme contenute in una pagina di un documento e quindi incollarle in una nuova pagina dello stesso documento. Le forme possono essere incollate nella posizione predefinita (ovvero il centro della finestra attiva) o nelle stesse coordinate occupate nella pagina originale.  
  
## <a name="copy-and-paste-shapes"></a>Copiare e incollare le forme  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)e [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Per copiare forme nel centro di un'altra pagina  
  
-   L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nel centro della seconda pagina.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiare e incollare forme le stesse coordinate  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA sui metodi [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)e [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) e sul flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Se è necessario controllare il formato delle informazioni incollate ed eventualmente stabilire un collegamento a un file di origine (ad esempio, un documento di Microsoft Office Word), usare il metodo PasteSpecial.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Per copiare le forme nella stessa posizione di un'altra pagina  
  
-   L'esempio seguente illustra come copiare le forme dalla prima pagina e quindi incollarle nella seconda pagina mantenendo le coordinate originali.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Lavorare con le forme di Visio](../vsto/working-with-visio-shapes.md)   
 [Procedura: a livello di codice aggiungere forme a un documento di Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  