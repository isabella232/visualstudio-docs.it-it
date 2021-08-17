---
title: 'Procedura: Creare tabelle di Word a livello di codice'
description: Informazioni su come usare il metodo Add della raccolta Tables per aggiungere una tabella in corrispondenza dell'intervallo specificato in un Microsoft Word documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 721828123734b82797fa27f720a9e5e0b7d4126f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122748"
---
# <a name="how-to-programmatically-create-word-tables"></a>Procedura: Creare tabelle di Word a livello di codice
  La raccolta <xref:Microsoft.Office.Interop.Word.Tables> è un membro delle classi <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> e <xref:Microsoft.Office.Interop.Word.Range>, pertanto è possibile creare una tabella in ognuno di questi contenuti. Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Tables> per aggiungere una tabella nell'intervallo specificato.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Creare tabelle nelle personalizzazioni a livello di documento

### <a name="to-add-a-table-to-a-document"></a>Per aggiungere una tabella a un documento

- Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> per aggiungere una tabella costituita da tre righe e quattro colonne all'inizio del documento.

   Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet86":::

  Quando si crea una tabella, viene aggiunta automaticamente alla raccolta <xref:Microsoft.Office.Interop.Word.Tables> dell'elemento host <xref:Microsoft.Office.Tools.Word.Document>. È quindi possibile fare riferimento alla tabella in base al numero dell'elemento usando la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, come illustrato nel codice seguente.

### <a name="to-refer-to-a-table-by-item-number"></a>Per fare riferimento a una tabella in base al numero dell'elemento

1. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> e fornire il numero di elemento a cui si vuole fare riferimento.

    Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet87":::

   Ogni oggetto <xref:Microsoft.Office.Interop.Word.Table> dispone anche di una proprietà <xref:Microsoft.Office.Interop.Word.Table.Range%2A> che consente di impostare gli attributi di formattazione.

### <a name="to-apply-a-style-to-a-table"></a>Per applicare uno stile a una tabella

1. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Table.Style%2A> per applicare uno degli stili incorporati di Word a una tabella.

     Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet88":::

## <a name="create-tables-in-vsto-add-ins"></a>Creare tabelle in VSTO componenti aggiuntivi

### <a name="to-add-a-table-to-a-document"></a>Per aggiungere una tabella a un documento

- Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> per aggiungere una tabella costituita da tre righe e quattro colonne all'inizio del documento.

   L'esempio di codice seguente aggiunge una tabella al documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet86":::

  Quando si crea una tabella, viene aggiunta automaticamente alla raccolta <xref:Microsoft.Office.Interop.Word.Tables> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document>. È quindi possibile fare riferimento alla tabella in base al numero dell'elemento usando la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, come illustrato nel codice seguente.

### <a name="to-refer-to-a-table-by-item-number"></a>Per fare riferimento a una tabella in base al numero dell'elemento

1. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> e fornire il numero di elemento a cui si vuole fare riferimento.

    L'esempio di codice seguente usa il documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet87":::

   Ogni oggetto <xref:Microsoft.Office.Interop.Word.Table> dispone anche di una proprietà <xref:Microsoft.Office.Interop.Word.Table.Range%2A> che consente di impostare gli attributi di formattazione.

### <a name="to-apply-a-style-to-a-table"></a>Per applicare uno stile a una tabella

1. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Table.Style%2A> per applicare uno degli stili incorporati di Word a una tabella.

     L'esempio di codice seguente usa il documento attivo. Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet88":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere testo e formattazione alle celle nelle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Procedura: Aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Procedura: Popolare tabelle di Word con proprietà di documento a livello di codice](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
