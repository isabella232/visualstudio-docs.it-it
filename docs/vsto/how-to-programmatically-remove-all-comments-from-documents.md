---
title: 'Procedura: A livello di codice rimuovere tutti i commenti dai documenti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 368779aa5c0edbfcaba3aff2abdf3eba09375f9f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833410"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Procedura: A livello di codice rimuovere tutti i commenti dai documenti
  Usare il metodo `DeleteAllComments` per rimuovere tutti i commenti da un documento di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Per rimuovere tutti i commenti da un documento che fa parte di una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> della classe `ThisDocument` nel progetto. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Per rimuovere tutti i commenti da un documento usando un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> da cui si vogliono rimuovere i commenti.  
  
     Il codice di esempio seguente rimuove tutti i commenti dal documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: A livello di codice aggiungere commenti al testo nei documenti](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
