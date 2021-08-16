---
title: 'Procedura: Creare e modificare proprietà di documenti personalizzati'
description: Informazioni su come creare e modificare proprietà personalizzate del documento se sono presenti informazioni aggiuntive da archiviare con il documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d0a289d77ee0b7263d58c9781bc29fa27afcbaea6d395ad39cd85002c635fcec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268287"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Procedura: Creare e modificare proprietà di documenti personalizzati
  Le applicazioni di Microsoft Office elencate in precedenza forniscono proprietà incorporate che vengono archiviate con i documenti. Inoltre, è possibile creare e modificare le proprietà personalizzate del documento se si vuole archiviare informazioni aggiuntive con il documento.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Usare la proprietà CustomDocumentProperties di un documento per usare proprietà personalizzate. Ad esempio, in un progetto a livello di documento per Microsoft Office Excel, usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> della classe `ThisWorkbook` . In un progetto di componente aggiuntivo VSTO per Excel, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> . Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.

 Nell'esempio seguente viene illustrato come aggiungere una proprietà personalizzata in una personalizzazione a livello di documento per Excel e come assegnare un valore a tale proprietà.

## <a name="example"></a>Esempio
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet6":::

## <a name="robust-programming"></a>Programmazione efficiente
 Il tentativo di accesso alla proprietà `Value` per proprietà non definite genera un'eccezione.

## <a name="see-also"></a>Vedi anche
- [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Procedura: Leggere e scrivere nelle proprietà del documento](../vsto/how-to-read-from-and-write-to-document-properties.md)
