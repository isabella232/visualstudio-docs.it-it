---
title: 'Procedura: aprire documenti di Visio a livello di codice'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ec46f4fd7be136d16e15e9fa366b7a4cb921b62e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523846"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Procedura: aprire documenti di Visio a livello di codice
  Esistono due metodi per aprire i documenti Microsoft Office Visio esistenti: Open e OpenEx. Il metodo OpenEx è identico al metodo Open, ad eccezione del fatto che fornisce argomenti in cui il chiamante può specificare la modalità di apertura del documento.

 Per informazioni dettagliate sul modello a oggetti, vedere la documentazione di riferimento di VBA relativa ai metodi [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) e [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Aprire un documento di Visio

### <a name="to-open-a-visio-document"></a>Per aprire un documento di Visio

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.Open` e fornire il percorso completo del documento di Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Apre un documento di Visio con gli argomenti specificati

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Per aprire un documento di Visio di sola lettura e come ancorato

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Documents.OpenEx`, fornire il percorso completo del documento di Visio e includere gli argomenti che si vogliono usare, ovvero in questo caso, Docked (ancorato) e Read-only (di sola lettura).

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Un documento di Visio denominato `myDrawing.vsd` deve trovarsi in una directory denominata `Test` nella cartella *documenti* (per Windows XP e versioni precedenti) oppure nella cartella *documenti* (per Windows Vista).

## <a name="see-also"></a>Vedere anche
- [Soluzioni Visio](../vsto/visio-solutions.md)
- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)
- [Procedura: creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: salvare documenti di Visio a livello di codice](../vsto/how-to-programmatically-save-visio-documents.md)
- [Procedura: stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)
