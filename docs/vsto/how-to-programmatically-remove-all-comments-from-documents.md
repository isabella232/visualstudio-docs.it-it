---
title: 'Procedura: rimuovere tutti i commenti dai documenti a livello di codice'
description: Informazioni su come usare Visual Studio per rimuovere a livello di codice tutti i commenti da un documento di Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdb2d7b61efc1e40bf08b6b38ea6564892a04a33
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526653"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Procedura: rimuovere tutti i commenti dai documenti a livello di codice
  Usare il metodo `DeleteAllComments` per rimuovere tutti i commenti da un documento di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Per rimuovere tutti i commenti da un documento che fa parte di una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> della classe `ThisDocument` nel progetto. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Per rimuovere tutti i commenti da un documento usando un componente aggiuntivo VSTO

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> da cui si vogliono rimuovere i commenti.

     Il codice di esempio seguente rimuove tutti i commenti dal documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>Vedere anche
- [Procedura: aggiungere commenti al testo nei documenti a livello di codice](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Elemento host Document](../vsto/document-host-item.md)
