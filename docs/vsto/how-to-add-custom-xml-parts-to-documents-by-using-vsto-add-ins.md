---
title: Aggiungere parti XML personalizzate ai documenti usando VSTO componenti aggiuntivi
description: Informazioni su come archiviare i dati XML nei tipi di documenti seguenti creando una parte XML personalizzata in un VSTO componente aggiuntivo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 84e769cd1d841a5116750963dcee4c0cb1186bf4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046958"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Procedura: Aggiungere parti XML personalizzate ai documenti usando VSTO componenti aggiuntivi
  È possibile archiviare dati XML nei tipi seguenti di documenti creando una parte XML personalizzata in un componente aggiuntivo VSTO:

- Cartella di lavoro di Microsoft Office Excel.

- Documento di Microsoft Office Word.

- Presentazione di Microsoft Office PowerPoint.

  Per altre informazioni, vedere [Panoramica delle parti XML personalizzate.](../vsto/custom-xml-parts-overview.md)

  **Si applica a:** le informazioni contenute in questo argomento si applicano ai progetti a livello di applicazione per Excel, PowerPoint e Word. Per altre informazioni, vedere [Funzionalità disponibili per l'applicazione Office tipo di progetto](../vsto/features-available-by-office-application-and-project-type.md)e .

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel

1. Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> della cartella di lavoro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella cartella di lavoro.

     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a una cartella di lavoro specificata.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Aggiungere il `AddCustomXmlPartToWorkbook` metodo alla classe in un progetto VSTO componente aggiuntivo per `ThisAddIn` Excel.

3. Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre una cartella di lavoro, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> .

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Per aggiungere una parte XML personalizzata a un documento di Word

1. Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> del documento. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nel documento.

     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a un documento specificato.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Aggiungere il `AddCustomXmlPartToDocument` metodo alla classe in un progetto VSTO componente aggiuntivo per `ThisAddIn` Word.

3. Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre un documento, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Per aggiungere una parte XML personalizzata a una presentazione di PowerPoint

1. Aggiungere un nuovo <xref:Microsoft.Office.Core.CustomXMLPart> oggetto al [file Microsoft.Office. Interoperabilità. PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) nella presentazione. L'oggetto <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella presentazione.

     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a una presentazione specificata.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb" id="Snippet1":::

2. Aggiungere il `AddCustomXmlPartToPresentation` metodo alla classe in un progetto VSTO componente aggiuntivo per `ThisAddIn` PowerPoint.

3. Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre una presentazione, chiamare il metodo da un gestore eventi per [Microsoft.Office. Interoperabilità. PowerPoint. EApplication_Event.AfterPresentationOpen.](/previous-versions/office/developer/office-2010/ff762843(v=office.14))

## <a name="robust-programming"></a>Programmazione efficiente
 Per semplicità, in questo esempio viene usata una stringa XML definita come variabile locale nel metodo. In genere, è necessario ottenere l'XML da un'origine esterna, ad esempio un file o un database.

## <a name="see-also"></a>Vedi anche
- [Panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md)
- [Procedura: Aggiungere parti XML personalizzate alle personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
