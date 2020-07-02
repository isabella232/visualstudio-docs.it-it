---
title: 'Procedura: stampare documenti di Visio a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e31a55e49d42311b5ec5fff82769584cc55ce09
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537800"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Procedura: stampare documenti di Visio a livello di codice
  È possibile stampare l'intero contenuto o solo una pagina specifica di un documento di Microsoft Office Visio.

 Per informazioni dettagliate sui metodi di stampa, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) e [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Stampare un documento di Visio

### <a name="to-print-a-complete-document"></a>Per stampare un documento completo

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Print` dell'oggetto `Microsoft.Office.Interop.Visio.Document` da stampare.

     L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Stampare una pagina di un documento di Visio

### <a name="to-print-a-page-of-a-document"></a>Per stampare una pagina di un documento

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Pages.Print` dell'oggetto `Microsoft.Office.Interop.Visio.Pages` da stampare.

     L'esempio di codice seguente stampa la prima pagina del documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Vedere anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)
- [Procedura: creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
