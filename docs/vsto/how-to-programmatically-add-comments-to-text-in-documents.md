---
title: 'Procedura: Aggiungere commenti al testo nei documenti a livello di codice'
description: Aggiungere commenti al testo nei documenti a livello di codice. La proprietà Comments della classe Document aggiunge un commento a un intervallo di testo in un Microsoft Word documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3e8b8d2f89b87d312b0a3868974fa6d9f7d039f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083349"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Procedura: Aggiungere commenti al testo nei documenti a livello di codice
  La proprietà Comments della classe Document aggiunge un commento a un intervallo di testo in un documento Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L'esempio seguente aggiunge un commento al primo paragrafo nel documento.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Per aggiungere un nuovo commento al testo in una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> della proprietà <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> e fornire un intervallo e il testo del commento. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet118":::

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Per aggiungere un nuovo commento al testo in un VSTO componente aggiuntivo

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> della proprietà <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> e fornire un intervallo e il testo del commento.

     L'esempio di codice seguente aggiunge un commento al documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet118":::

## <a name="robust-programming"></a>Programmazione efficiente
 Per modificare le iniziali dell'utente che Word aggiunge ai commenti, usare la proprietà <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .

## <a name="see-also"></a>Vedi anche
- [Procedura: Rimuovere tutti i commenti dai documenti a livello di codice](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Elemento host del documento](../vsto/document-host-item.md)
