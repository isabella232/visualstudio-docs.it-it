---
title: 'Procedura: Stampare documenti di Visio a livello di codice'
description: Informazioni su come stampare un documento completo di Microsoft Visio o stampare solo una pagina specifica in tale documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f38f6afb5aa6d1735207a851de80bd57d6c4fa811c6d96abbea9ab78b14a0ebd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351811"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Procedura: Stampare documenti di Visio a livello di codice
  È possibile stampare l'intero contenuto o solo una pagina specifica di un documento di Microsoft Office Visio.

 Per informazioni dettagliate sui metodi di stampa, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) e [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Stampare un documento Visio

### <a name="to-print-a-complete-document"></a>Per stampare un documento completo

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Print` dell'oggetto `Microsoft.Office.Interop.Visio.Document` da stampare.

     L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet8":::

## <a name="print-a-page-of-a-visio-document"></a>Stampare una pagina di un documento Visio

### <a name="to-print-a-page-of-a-document"></a>Per stampare una pagina di un documento

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Pages.Print` dell'oggetto `Microsoft.Office.Interop.Visio.Pages` da stampare.

     L'esempio di codice seguente stampa la prima pagina del documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Vedi anche
- [Visio soluzioni](../vsto/visio-solutions.md)
- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)
- [Procedura: Creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: Aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: Chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
