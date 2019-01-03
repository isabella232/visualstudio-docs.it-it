---
title: 'Procedura: A livello di programmazione stampare documenti di Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f5e8ff7f7577c779349b49fc291f91d02c90094
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845525"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Procedura: A livello di programmazione stampare documenti di Visio
  È possibile stampare l'intero contenuto o solo una pagina specifica di un documento di Microsoft Office Visio.  
  
 Per informazioni dettagliate sui metodi di stampa, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) e [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) .  
  
## <a name="print-a-visio-document"></a>Stampare un documento di Visio  
  
### <a name="to-print-a-complete-document"></a>Per stampare un documento completo  
  
-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Print` dell'oggetto `Microsoft.Office.Interop.Visio.Document` da stampare.  
  
     L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Stampare una pagina di un documento di Visio  
  
### <a name="to-print-a-page-of-a-document"></a>Per stampare una pagina di un documento  
  
-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Pages.Print` dell'oggetto `Microsoft.Office.Interop.Visio.Pages` da stampare.  
  
     L'esempio di codice seguente stampa la prima pagina del documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: Creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: A livello di codice aprire documenti di Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: A livello di programmazione chiudere documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: A livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)  
