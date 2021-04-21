---
title: 'Procedura: Aprire documenti di Visio a livello di codice'
description: Informazioni su come usare Visual Studio per aprire un documento di Visio a livello di codice con i metodi Open o OpenEx.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f96efd41eb91551fe3cf7c03b55a44b7a9e1bf1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824744"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procedura: Aprire documenti di Visio a livello di codice
  Esistono due metodi per l'apertura di Microsoft Office documenti di Visio: Open e OpenEx. Il metodo OpenEx è identico al metodo Open, ad eccezione del fatto che fornisce argomenti in cui il chiamante può specificare la modalità di apertura del documento.

 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) e [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Aprire un documento di Visio

### <a name="to-open-a-visio-document"></a>Per aprire un documento di Visio

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Open` e fornire il percorso completo del documento di Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>Aprire un documento di Visio con gli argomenti specificati

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Per aprire un documento di Visio di sola lettura e come ancorato

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.OpenEx`, fornire il percorso completo del documento di Visio e includere gli argomenti che si vogliono usare, ovvero in questo caso, Docked (ancorato) e Read-only (di sola lettura).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Un documento di Visio denominato deve trovarsi in una directory denominata nella cartella Documenti (per Windows XP e versioni precedenti) o nella cartella Documenti `myDrawing.vsd` `Test` (per Windows Vista).  

## <a name="see-also"></a>Vedi anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)
- [Procedura: Creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: Chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: Salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)
