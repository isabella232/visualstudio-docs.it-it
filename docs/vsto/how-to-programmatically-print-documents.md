---
title: 'Procedura: Stampare documenti a livello di codice'
description: Informazioni su come stampare un intero documento di Microsoft Word, o parte di un documento, sulla stampante predefinita.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47f295a6259b8d722c9c3c714b62fe648bdea1c6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827201"
---
# <a name="how-to-programmatically-print-documents"></a>Procedura: Stampare documenti a livello di codice
  È possibile stampare un intero documento di Microsoft Office Word o parte di un documento sulla stampante predefinita.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Stampare un documento che fa parte di una personalizzazione a livello di documento

### <a name="to-print-the-entire-document"></a>Per stampare l'intero documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> della classe `ThisDocument` nel progetto per stampare l'intero documento. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-the-document"></a>Per stampare la pagina corrente del documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> della classe `ThisDocument` nel progetto e specificare che una copia della pagina corrente deve essere stampata. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet12":::

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Stampare un documento usando un componente aggiuntivo VSTO

### <a name="to-print-an-entire-document"></a>Per stampare un intero documento

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> da stampare. L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet11":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet11":::

### <a name="to-print-the-current-page-of-a-document"></a>Per stampare la pagina corrente di un documento

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole stampare e specificare che una copia della pagina corrente deve essere stampata. L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet12":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet12":::

## <a name="see-also"></a>Vedi anche
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
