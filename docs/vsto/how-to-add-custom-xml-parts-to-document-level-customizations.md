---
title: 'Procedura: Aggiungere parti XML personalizzate a personalizzazioni a livello di documento'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4de0471dcc94a709156f5dc9fcce57dca8fb82bd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427597"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Procedura: Aggiungere parti XML personalizzate a personalizzazioni a livello di documento
  È possibile archiviare dati XML in una cartella di lavoro di Microsoft Office Excel o in un documento di Microsoft Office Word creando una parte XML personalizzata in una personalizzazione a livello di documento. Per altre informazioni, vedere [panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio non offre progetti a livello di documento per Microsoft Office PowerPoint. Per informazioni sull'aggiunta di una parte XML personalizzata a una presentazione di PowerPoint usando un componente aggiuntivo VSTO, vedere [come: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel

1. Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> della cartella di lavoro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella cartella di lavoro.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2. Aggiungere il metodo `AddCustomXmlPartToWorkbook` alla classe `ThisWorkbook` in un progetto a livello di documento per Excel.

3. Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre la cartella di lavoro, chiamare il metodo dal gestore eventi `ThisWorkbook_Startup` .

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Per aggiungere una parte XML personalizzata a un documento di Word

1. Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> del documento. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nel documento.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2. Aggiungere il metodo `AddCustomXmlPartToDocument` alla classe `ThisDocument` in un progetto a livello di documento per Word.

3. Chiamare il metodo da altro codice nel progetto. Per creare, ad esempio, la parte XML personalizzata quando l'utente apre il documento, chiamare il metodo dal gestore eventi `ThisDocument_Startup` .

## <a name="robust-programming"></a>Programmazione efficiente
 Per semplicità, in questo esempio viene usata una stringa XML definita come variabile locale nel metodo. In genere, è necessario ottenere l'XML da un'origine esterna, ad esempio un file o un database.

## <a name="see-also"></a>Vedere anche
- [Panoramica delle parti XML personalizzata](../vsto/custom-xml-parts-overview.md)
- [Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
