---
title: Proteggere documenti e parti di documenti a livello di codice
description: Informazioni su come aggiungere protezione ai Microsoft Word documenti per impedire agli utenti di apportare modifiche al documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 65d869fa7ff797e0144f08e7f15e822ba1c7f25d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046451"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Procedura: Proteggere documenti e parti di documenti a livello di codice
  È possibile aggiungere protezione ai documenti di Microsoft Office Word per impedire agli utenti di apportare modifiche al documento.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 È anche possibile contrassegnare determinate aree del documento come eccezioni in modo che gli utenti possano modificare solo quelle aree del documento. Ad esempio, si potrebbe voler proteggere un intero documento ad eccezione di un segnalibro particolare. È possibile aggiungere facoltativamente una password in modo che gli utenti non possano rimuovere la protezione del documento a meno che non si conosca la password.

> [!NOTE]
> Nell'esempio seguente non viene usata la protezione con password; tuttavia, si consiglia di usare una password quando si aggiunge la protezione di documenti. Per altre informazioni, vedere l'esempio di protezione dei documenti [Office esempi di sviluppo e procedure dettagliate.](../vsto/office-development-samples-and-walkthroughs.md)

 È possibile anche usare i controlli contenuto per proteggere parti di un documento. Per altre informazioni, vedere [Procedura: Proteggere parti di documenti usando i controlli contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Proteggere un documento che fa parte di una personalizzazione a livello di documento

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Per proteggere un documento che fa parte di una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> della classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Per escludere un controllo Bookmark dalla protezione di documenti

1. Proteggere l'intero documento usando il metodo <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

2. Escludere `Bookmark1` dalla protezione di documenti.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet112":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet112":::

### <a name="compile-the-code"></a>Compilare il codice
 Per usare questi esempi di codice, eseguirli dalla classe `ThisDocument` nel progetto. Questi esempi di codice presuppongono che nel documento in cui appare questo codice sia disponibile il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> esistente denominato `Bookmark1` .

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Proteggere un documento usando un VSTO componente aggiuntivo

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Per proteggere un documento usando un componente aggiuntivo VSTO a livello di applicazione

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole proteggere.

     L'esempio di codice seguente protegge il documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet111":::

## <a name="see-also"></a>Vedi anche
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protezione con password per Office documenti](../vsto/password-protection-on-office-documents.md)
- [Procedura: Consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Procedura: Aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
