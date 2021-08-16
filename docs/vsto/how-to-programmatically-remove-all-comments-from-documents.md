---
title: 'Procedura: Rimuovere tutti i commenti dai documenti a livello di codice'
description: Informazioni su come usare Visual Studio per rimuovere a livello di codice tutti i commenti da un Microsoft Word documento.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3ba39c17b5c00ec78af0b4ba89aedb528cb6a322ca22aaa8b44bab2d21f732ef
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366199"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Procedura: Rimuovere tutti i commenti dai documenti a livello di codice
  Usare il metodo `DeleteAllComments` per rimuovere tutti i commenti da un documento di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Per rimuovere tutti i commenti da un documento che fa parte di una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> della classe `ThisDocument` nel progetto. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet119":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet119":::

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Per rimuovere tutti i commenti da un documento usando un VSTO componente aggiuntivo

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> da cui si vogliono rimuovere i commenti.

     Il codice di esempio seguente rimuove tutti i commenti dal documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet119":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet119":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere commenti al testo nei documenti a livello di codice](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Elemento host del documento](../vsto/document-host-item.md)
