---
title: 'Procedura: aprire documenti di Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257852"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procedura: aprire documenti di Visio
  Esistono due metodi per l'apertura di documenti di Microsoft Office Visio esistenti: OpenEx e Open. Il metodo OpenEx è identico al metodo Open, ad eccezione del fatto che fornisca gli argomenti in cui il chiamante può specificare la modalità di apertura del documento.  
  
 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) e [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) .  
  
## <a name="open-a-visio-document"></a>Aprire un documento di Visio  
  
### <a name="to-open-a-visio-document"></a>Per aprire un documento di Visio  
  
-   Chiamare il `Microsoft.Office.Interop.Visio.Documents.Open` (metodo) e specificare il percorso completo del documento di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Aprire un documento di Visio con gli argomenti specificati  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Per aprire un documento di Visio di sola lettura e come ancorato  
  
-   Chiamare il `Microsoft.Office.Interop.Visio.Documents.OpenEx` (metodo), specificare il percorso completo del documento di Visio e includere gli argomenti da usare, in questo caso, ancorati e sola lettura.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Un documento di Visio denominato `myDrawing.vsd` deve trovarsi in una directory denominata `Test` nel *documenti* cartella (per Windows XP e versioni precedenti) o nella *documenti* cartella (per Windows Vista).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: chiudere a livello di programmazione di documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: a livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Procedura: stampa di documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  