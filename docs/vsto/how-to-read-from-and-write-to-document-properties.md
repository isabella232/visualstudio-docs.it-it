---
title: 'Procedura: Leggere e scrivere nelle proprietà del documento'
description: Informazioni su come usare le Visual Studio per ottenere o impostare le proprietà dei documenti in Microsoft Excel e Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 981f9da1138034dd108a438a69683f4107358ee4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032719"
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Procedura: Leggere e scrivere nelle proprietà del documento
  È possibile archiviare le proprietà del documento insieme a un documento. Le applicazioni di Office offrono svariate proprietà predefinite, ad esempio autore, titolo e oggetto. Questo argomento illustra come impostare le proprietà dei documenti in Microsoft Office Excel e Microsoft Office Word.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

## <a name="set-document-properties-in-excel"></a>Impostare le proprietà del documento in Excel
 Per usare le proprietà predefinite in Excel, configurare le proprietà seguenti:

- In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> della classe `ThisWorkbook` .

- In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> .

  Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.

  L'esempio di codice seguente illustra come modificare la proprietà predefinita **Revision Number** in un progetto a livello di documento.

### <a name="to-change-the-revision-number-property-in-excel"></a>Per modificare la proprietà Numero revisione in Excel

1. Assegnare le proprietà predefinite del documento a una variabile.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet7":::

2. Incrementare di uno la proprietà `Revision Number` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet8":::

## <a name="set-document-properties-in-word"></a>Impostare le proprietà del documento in Word
 Per usare le proprietà predefinite in Word, configurare le proprietà seguenti:

- In un progetto a livello di documento usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> della classe `ThisDocument` .

- In un progetto a livello di componente aggiuntivo VSTO, usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Document> .

  Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.

  L'esempio di codice seguente illustra come modificare la proprietà predefinita **Subject** in un progetto a livello di documento.

### <a name="to-change-the-subject-property"></a>Per modificare la proprietà Oggetto

1. Assegnare le proprietà predefinite del documento a una variabile.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet1":::

2. Modificare la proprietà `Subject` in "White paper".

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb" id="Snippet2":::

## <a name="robust-programming"></a>Programmazione efficiente
 Questo esempio presuppone che il codice della classe `ThisWorkbook` sia stato scritto in un progetto a livello di documento per Excel e quello della classe `ThisDocument` in un progetto a livello di documento per Word.

 Anche se si usano Word ed Excel e i rispettivi oggetti, Microsoft Office fornisce l'elenco di proprietà predefinite disponibili per i documenti. Il tentativo di accesso a una proprietà non definita provocherà un'eccezione.

## <a name="see-also"></a>Vedi anche
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Procedura: Creare e modificare proprietà di documenti personalizzati](../vsto/how-to-create-and-modify-custom-document-properties.md)
