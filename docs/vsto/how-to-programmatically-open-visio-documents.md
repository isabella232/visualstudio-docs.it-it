---
title: 'Procedura: A livello di codice aprire documenti di Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b87d3b1659d46a69e5a2e950997d3c0474e84d11
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598388"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procedura: A livello di codice aprire documenti di Visio
  Esistono due metodi per l'apertura di documenti di Microsoft Office Visio esistenti: Aprire e OpenEx. Il metodo OpenEx è identico al metodo Open, ad eccezione del fatto che fornisca gli argomenti in cui il chiamante può specificare la modalità di apertura del documento.

 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) e [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Aprire un documento di Visio

### <a name="to-open-a-visio-document"></a>Per aprire un documento di Visio

-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Open` e fornire il percorso completo del documento di Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Aprire un documento di Visio con gli argomenti specificati

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Per aprire un documento di Visio di sola lettura e come ancorato

-   Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.OpenEx`, fornire il percorso completo del documento di Visio e includere gli argomenti che si vogliono usare, ovvero in questo caso, Docked (ancorato) e Read-only (di sola lettura).

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

-   Un documento di Visio denominato `myDrawing.vsd` deve trovarsi in una directory denominata `Test` nel *documenti* cartella (per Windows XP e versioni precedenti) o nella *documenti* cartella (per Windows Vista).

## <a name="see-also"></a>Vedere anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)
- [Procedura: Creazione di nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: A livello di programmazione chiudere documenti di Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: A livello di programmazione salvare documenti di Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: A livello di programmazione stampare documenti di Visio](../vsto/how-to-programmatically-print-visio-documents.md)
