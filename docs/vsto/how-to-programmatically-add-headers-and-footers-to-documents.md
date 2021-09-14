---
title: 'Procedura: Aggiungere intestazioni e piè di pagina ai documenti a livello di codice'
description: Informazioni su come aggiungere testo a intestazioni e piè di pagina nel documento usando la proprietà Headers e la proprietà Footers della sezione.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b2ddbc24bcd567ce56326a4b96d9c97f1e50061c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710076"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Procedura: Aggiungere intestazioni e piè di pagina ai documenti a livello di codice
  È possibile aggiungere testo alle intestazioni e ai piè di pagina del documento usando la proprietà <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> e la proprietà <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> di <xref:Microsoft.Office.Interop.Word.Section>. Ogni sezione di un documento contiene tre intestazioni e piè di pagina:

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Le procedure sono diverse per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Personalizzazioni a livello di documento
 Per usare gli esempi di codice seguenti, eseguirli dalla classe `ThisDocument` nel progetto.

### <a name="to-add-text-to-footers-in-the-document"></a>Per aggiungere testo ai piè di pagina nel documento

1. L'esempio di codice seguente imposta il tipo di carattere del testo da inserire nel piè di pagina principale di ogni sezione del documento e quindi inserisce il testo nel piè di pagina.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Per aggiungere testo alle intestazioni nel documento

1. L'esempio di codice seguente aggiunge un campo per mostrare il numero di pagina in ogni intestazione del documento e quindi imposta l'allineamento del paragrafo in modo che il testo venga allineato a destra dell'intestazione.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet116":::

## <a name="vsto-add-ins"></a>Componenti aggiuntivi VSTO
 Per usare gli esempi di codice seguenti, eseguirli dalla classe `ThisAddIn` nel progetto.

### <a name="to-add-text-to-footers-in-a-document"></a>Per aggiungere testo ai piè di pagina in un documento

1. L'esempio di codice seguente imposta il tipo di carattere del testo da inserire nel piè di pagina principale di ogni sezione del documento e quindi inserisce il testo nel piè di pagina. L'esempio di codice usa il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet114":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet114":::

### <a name="to-add-text-to-headers-in-the-document"></a>Per aggiungere testo alle intestazioni nel documento

1. L'esempio di codice seguente aggiunge un campo per mostrare il numero di pagina in ogni intestazione del documento e quindi imposta l'allineamento del paragrafo in modo che il testo venga allineato a destra dell'intestazione. L'esempio di codice usa il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet116":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet116":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)
- [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Scorrere a livello di codice gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
