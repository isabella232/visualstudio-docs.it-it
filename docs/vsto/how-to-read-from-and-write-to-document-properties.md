---
title: 'Procedura: Leggere e scrivere le proprietà del documento'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51add739e6303a62eb3333c4a173fa0d2e58f2f1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862629"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Procedura: Leggere e scrivere le proprietà del documento
  È possibile archiviare le proprietà del documento insieme a un documento. Le applicazioni di Office offrono svariate proprietà predefinite, ad esempio autore, titolo e oggetto. Questo argomento illustra come impostare le proprietà dei documenti in Microsoft Office Excel e Microsoft Office Word.  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Accedere e modificare le proprietà personalizzate dei documenti in Microsoft Word? ](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="set-document-properties-in-excel"></a>Impostare le proprietà di documento di Excel  
 Per usare le proprietà predefinite in Excel, configurare le proprietà seguenti:  
  
- In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> della classe `ThisWorkbook` .  
  
- In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> .  
  
  Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
  L'esempio di codice seguente illustra come modificare la proprietà predefinita **Revision Number** in un progetto a livello di documento.  
  
### <a name="to-change-the-revision-number-property-in-excel"></a>Per modificare la proprietà Numero revisione in Excel  
  
1.  Assegnare le proprietà predefinite del documento a una variabile.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Incrementare di uno la proprietà `Revision Number` .  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="set-document-properties-in-word"></a>Impostare le proprietà di documento di Word  
 Per usare le proprietà predefinite in Word, configurare le proprietà seguenti:  
  
- In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> della classe `ThisDocument` .  
  
- In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Document> .  
  
  Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.  
  
  L'esempio di codice seguente illustra come modificare la proprietà predefinita **Subject** in un progetto a livello di documento.  
  
### <a name="to-change-the-subject-property"></a>Per modificare la proprietà Oggetto  
  
1.  Assegnare le proprietà predefinite del documento a una variabile.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Modificare la proprietà `Subject` in "White paper".  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Questo esempio presuppone che il codice della classe `ThisWorkbook` sia stato scritto in un progetto a livello di documento per Excel e quello della classe `ThisDocument` in un progetto a livello di documento per Word.  
  
 Anche se si usano Word ed Excel e i rispettivi oggetti, Microsoft Office fornisce l'elenco di proprietà predefinite disponibili per i documenti. Il tentativo di accesso a una proprietà non definita provocherà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedura: Creare e modificare le proprietà personalizzate dei documenti](../vsto/how-to-create-and-modify-custom-document-properties.md)  
