---
title: 'Procedura: Aggiungere parti XML personalizzate alle personalizzazioni a livello di documento'
description: Informazioni su come archiviare dati XML in una cartella di lavoro di Microsoft Office Excel o Microsoft Office documento di Word creando una parte XML personalizzata in una personalizzazione a livello di documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 217bb0178a09822a7f44af91ed475fd9364dc09d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083505"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Procedura: Aggiungere parti XML personalizzate alle personalizzazioni a livello di documento
  È possibile archiviare dati XML in una cartella di lavoro di Microsoft Office Excel o in un documento di Microsoft Office Word creando una parte XML personalizzata in una personalizzazione a livello di documento. Per altre informazioni, vedere [Cenni preliminari sulle parti XML personalizzate.](../vsto/custom-xml-parts-overview.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio non offre progetti a livello di documento per Microsoft Office PowerPoint. Per informazioni sull'aggiunta di una parte XML personalizzata a una presentazione di PowerPoint tramite un componente aggiuntivo VSTO, vedere [Procedura:](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)Aggiungere parti XML personalizzate ai documenti usando componenti aggiuntivi VSTO .

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel

1. Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> della cartella di lavoro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella cartella di lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Aggiungere il metodo `AddCustomXmlPartToWorkbook` alla classe `ThisWorkbook` in un progetto a livello di documento per Excel.

3. Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre la cartella di lavoro, chiamare il metodo dal gestore eventi `ThisWorkbook_Startup` .

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Per aggiungere una parte XML personalizzata a un documento di Word

1. Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> del documento. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nel documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. Aggiungere il metodo `AddCustomXmlPartToDocument` alla classe `ThisDocument` in un progetto a livello di documento per Word.

3. Chiamare il metodo da altro codice nel progetto. Per creare, ad esempio, la parte XML personalizzata quando l'utente apre il documento, chiamare il metodo dal gestore eventi `ThisDocument_Startup` .

## <a name="robust-programming"></a>Programmazione efficiente
 Per semplicità, in questo esempio viene usata una stringa XML definita come variabile locale nel metodo. In genere, è necessario ottenere l'XML da un'origine esterna, ad esempio un file o un database.

## <a name="see-also"></a>Vedi anche
- [Panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md)
- [Procedura: Aggiungere parti XML personalizzate ai documenti usando VSTO componenti aggiuntivi](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
