---
title: 'Procedura: creare e modificare proprietà personalizzate di un documento'
description: Informazioni su come creare e modificare le proprietà personalizzate del documento se sono presenti informazioni aggiuntive da archiviare con il documento.
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
ms.workload:
- office
ms.openlocfilehash: 0080c9b0ddd7ffba4730a8cfb305bc34b6ba1690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964316"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Procedura: creare e modificare proprietà personalizzate di un documento
  Le applicazioni di Microsoft Office elencate in precedenza forniscono proprietà incorporate che vengono archiviate con i documenti. Inoltre, è possibile creare e modificare le proprietà personalizzate del documento se si vuole archiviare informazioni aggiuntive con il documento.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Usare la proprietà CustomDocumentProperties di un documento per lavorare con proprietà personalizzate. Ad esempio, in un progetto a livello di documento per Microsoft Office Excel, usare la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> della classe `ThisWorkbook` . In un progetto di componente aggiuntivo VSTO per Excel, usare la proprietà <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> di un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> . Queste proprietà restituiscono un oggetto <xref:Microsoft.Office.Core.DocumentProperties> , che rappresenta una raccolta di oggetti <xref:Microsoft.Office.Core.DocumentProperty> . È possibile usare la proprietà `Item` della raccolta per recuperare una proprietà specifica, in base al nome o in base all'indice nella raccolta.

 Nell'esempio seguente viene illustrato come aggiungere una proprietà personalizzata in una personalizzazione a livello di documento per Excel e come assegnare un valore a tale proprietà.

## <a name="example"></a>Esempio
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Programmazione efficiente
 Il tentativo di accesso alla proprietà `Value` per proprietà non definite genera un'eccezione.

## <a name="see-also"></a>Vedi anche
- [Componenti aggiuntivi VSTO di programma](../vsto/programming-vsto-add-ins.md)
- [Programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Procedura: leggere e scrivere nelle proprietà dei documenti](../vsto/how-to-read-from-and-write-to-document-properties.md)
