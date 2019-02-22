---
title: 'Procedura: A livello di codice aggiungere commenti al testo nei documenti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b2f043cba192ed3ff1f4e0ec995b0ee51a48432
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624646"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Procedura: A livello di codice aggiungere commenti al testo nei documenti
  La proprietà commenti della classe documento aggiunge un commento a un intervallo di testo in un documento di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L'esempio seguente aggiunge un commento al primo paragrafo nel documento.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Per aggiungere un nuovo commento al testo in una personalizzazione a livello di documento

1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> della proprietà <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> e fornire un intervallo e il testo del commento. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Per aggiungere un nuovo commento al testo in un componente aggiuntivo VSTO

1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> della proprietà <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> e fornire un intervallo e il testo del commento.

     L'esempio di codice seguente aggiunge un commento al documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Programmazione efficiente
 Per modificare le iniziali dell'utente che Word aggiunge ai commenti, usare la proprietà <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .

## <a name="see-also"></a>Vedere anche
- [Procedura: A livello di codice rimuovere tutti i commenti dai documenti](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Elemento host Document](../vsto/document-host-item.md)
